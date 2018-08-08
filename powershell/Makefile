# $FreeBSD$

PORTNAME=	powershell
DISTVERSIONPREFIX=	v
DISTVERSION=	6.1.0-preview.4
CATEGORIES=	shells

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

MAINTAINER=	mateus@mateus.tech
COMMENT=	PowerShell is a task automation and configuration management framework from Microsoft, consisting of a command-line shell and associated scripting language.

USE_GITHUB=	yes
GH_ACCOUNT=	PowerShell
GH_PROJECT=	PowerShell
GH_TUPLE=	PowerShell:PowerShell-Native:98599da:1/external/powershell-native \
		google:googletest:4e4df22:2/external/powershell-native/src/libpsl-native/test/googletest

USES=		mono:nuget
NUGET_FEEDS=	NUGET POWERSHELL_CORE
POWERSHELL_CORE_URL=	https://powershell.myget.org/F/powershell-core/api/v2/
POWERSHELL_CORE_DEPENDS=	libpsl=6.0.0-rc \
				PowerShell.Core.Instrumentation=6.0.0-beta.10 \
				PowerShellHelpFiles=1.0.0-alpha02 \
				PSDesiredStateConfiguration=6.0.0-beta.8 \
				psrp=1.4.2 \
				Microsoft.PowerShell.Commands.Management=6.1.0-preview.4 \
				Microsoft.PowerShell.Commands.Utility=6.1.0-preview.4 \
				Microsoft.PowerShell.ConsoleHost=6.1.0-preview.4 \
				Microsoft.PowerShell.CoreCLR.Eventing=6.1.0-preview.4 \
				Microsoft.PowerShell.MarkdownRender=6.1.0-preview.4 \
				Microsoft.PowerShell.SDK=6.1.0-preview.4 \
				Microsoft.PowerShell.Security=6.1.0-preview.4 \
				System.Management.Automation=6.1.0-preview.4


SUB_FILES=	patch-PowerShell.Common.props
SUB_LIST=	WRKSRC=${WRKSRC}
MAKE_JOBS_UNSAFE=	yes

BUILD_CONFIGURATION=	Release

# .NET related
export COMPlus_ZapDisable=1
export COMPlus_ReadyToRun=0
export DOTNET_SKIP_FIRST_TIME_EXPERIENCE=1
export DOTNET_CLI_TELEMETRY_OPTOUT=1
export SSL_CERT_FILE=/usr/local/share/certs/ca-root-nss.crt
export DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER=0

pre-patch:
	# copy git describe file
	${CP} files/git-describe.txt ${WRKSRC}/git-describe.txt

post-patch:
	@${REINPLACE_CMD} -e 's|%%WRKSRC%%|${WRKSRC}|g' ${WRKSRC}/PowerShell.Common.props

build:
	# copy shared framework version
	dotnet --list-runtimes | awk '{print $$2}' > ${WRKSRC}/shared-framework-version.txt
	# generate ResGen files
	(cd ${WRKSRC}/src/ResGen && \
	       dotnet build -c ${BUILD_CONFIGURATION} --no-restore && \
	       dotnet --fx-version $$(cat ${WRKSRC}/shared-framework-version.txt) bin/${BUILD_CONFIGURATION}/netcoreapp2.0/resgen.dll)
	# generate type catalog
	cat files/typecatalog.txt > ${WRKSRC}/src/Microsoft.PowerShell.SDK/obj/Microsoft.PowerShell.SDK.csproj.TypeCatalog.targets
	dotnet msbuild ${WRKSRC}/src/Microsoft.PowerShell.SDK/Microsoft.PowerShell.SDK.csproj /t:_GetDependencies "/property:DesignTimeBuild=true;_DependencyFile=${WRKSRC}/src/TypeCatalogGen/powershell.inc" /nologo
	(cd ${WRKSRC}/src/TypeCatalogGen && \
	       dotnet run --no-restore ../System.Management.Automation/CoreCLR/CorePsTypeCatalog.cs powershell.inc)
	# build powershell
	(cd ${WRKSRC}/src/powershell-unix && \
		dotnet build -c ${BUILD_CONFIGURATION} --no-restore)
	# build powershell-native
	(cd ${WRKSRC}/external/powershell-native/src/libpsl-native && \
	       make)
	# copy native build results
	${CP} ${WRKSRC}/external/powershell-native/src/powershell-unix/libpsl-native.so ${WRKSRC}/src/powershell-unix/bin/${BUILD_CONFIGURATION}/netcoreapp2.1/libpsl-native.so

.include <bsd.port.mk>
