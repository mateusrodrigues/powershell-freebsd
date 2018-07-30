# $FreeBSD$

PORTNAME=	powershell
DISTVERSIONPREFIX=	v
DISTVERSION=	6.1.0-preview.4
CATEGORIES=	shells

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

MAINTAINER=	mateus@mateus.tech
COMMENT=	Microsoft PowerShell

USE_GITHUB=	yes
GH_ACCOUNT=	PowerShell
GH_PROJECT=	PowerShell

MAKE_JOBS_UNSAFE=	yes

# .NET related
export COMPlus_ZapDisable=1
export COMPlus_ReadyToRun=0
export DOTNET_SKIP_FIRST_TIME_EXPERIENCE=1
export DOTNET_CLI_TELEMETRY_OPTOUT=1
export SSL_CERT_FILE=/usr/local/share/certs/ca-root-nss.crt
export DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER=0

post-extract:
	# clone powershell-native
	git clone --recurse-submodules https://github.com/PowerShell/PowerShell-Native ${WRKDIR}/pwshnative

pre-patch:
	# copy git describe file
	cp files/git-describe.txt ${WRKSRC}/git-describe.txt

build:
	# copy shared framework version
	dotnet --list-runtimes | awk '{print $$2}' > ${WRKSRC}/shared-framework-version.txt
	# generate ResGen files
	sh -c "cd ${WRKSRC}/src/ResGen && dotnet build && dotnet --fx-version $$(cat ${WRKSRC}/shared-framework-version.txt) bin/Debug/netcoreapp2.0/resgen.dll"
	# generate type catalog
	cat files/typecatalog.txt > ${WRKSRC}/src/Microsoft.PowerShell.SDK/obj/Microsoft.PowerShell.SDK.csproj.TypeCatalog.targets
	dotnet msbuild ${WRKSRC}/src/Microsoft.PowerShell.SDK/Microsoft.PowerShell.SDK.csproj /t:_GetDependencies "/property:DesignTimeBuild=true;_DependencyFile=${WRKSRC}/src/TypeCatalogGen/powershell.inc" /nologo
	sh -c "cd ${WRKSRC}/src/TypeCatalogGen && dotnet run ../System.Management.Automation/CoreCLR/CorePsTypeCatalog.cs powershell.inc"
	# build powershell
	sh -c "cd ${WRKSRC}/src/powershell-unix && dotnet build"
	build powershell-native
	sh -c "cd ${WRKDIR}/pwshnative/src/libpsl-native && make"
.include <bsd.port.mk>
