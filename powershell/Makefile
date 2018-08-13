# $FreeBSD$

PORTNAME=	powershell
DISTVERSIONPREFIX=	v
DISTVERSION=	6.1.0-preview.4
CATEGORIES=	shells

MAINTAINER=	mateus@mateus.tech
COMMENT=	PowerShell is a task automation and configuration management framework

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

ONLY_FOR_ARCHS=	amd64 i386

BUILD_DEPENDS=	${LOCALBASE}/share/dotnet/sdk:devel/dotnet-sdk
RUN_DEPENDS=	dotnet:devel/dotnet

USES=		mono:nuget
USE_GITHUB=	yes
GH_ACCOUNT=	PowerShell
GH_PROJECT=	PowerShell
GH_TUPLE=	PowerShell:PowerShell-Native:98599da:1/external/powershell-native \
		google:googletest:4e4df22:2/external/powershell-native/src/libpsl-native/test/googletest
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

MAKE_JOBS_UNSAFE=	yes
BUILD_CONFIGURATION=	Release
DOTNET_ENV=	COMPlus_ZapDisable=1 \
		COMPlus_ReadyToRun=0 \
		DOTNET_SKIP_FIRST_TIME_EXPERIENCE=1 \
		DOTNET_CLI_TELEMETRY_OPTOUT=1 \
		SSL_CERT_FILE=/usr/local/share/certs/ca-root-nss.crt \
		DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER=0

post-patch:
	@${CP} files/git-describe.txt ${WRKSRC}/git-describe.txt
	@${REINPLACE_CMD} -e 's|%%WRKSRC%%|${WRKSRC}|g' ${WRKSRC}/PowerShell.Common.props

do-build:
	# copy shared framework version
	${SETENV} ${DOTNET_ENV} dotnet --list-runtimes | ${AWK} '{print $$2}' > ${WRKSRC}/shared-framework-version.txt
	# generate ResGen files
	(cd ${WRKSRC}/src/ResGen && \
	       ${SETENV} ${DOTNET_ENV} dotnet build -c ${BUILD_CONFIGURATION} --no-restore && \
	       ${SETENV} ${DOTNET_ENV} dotnet --fx-version $$(cat ${WRKSRC}/shared-framework-version.txt) bin/${BUILD_CONFIGURATION}/netcoreapp2.0/resgen.dll)
	# generate type catalog
	${CAT} files/typecatalog.txt > ${WRKSRC}/src/Microsoft.PowerShell.SDK/obj/Microsoft.PowerShell.SDK.csproj.TypeCatalog.targets
	${SETENV} ${DOTNET_ENV} dotnet msbuild ${WRKSRC}/src/Microsoft.PowerShell.SDK/Microsoft.PowerShell.SDK.csproj /t:_GetDependencies "/property:DesignTimeBuild=true;_DependencyFile=${WRKSRC}/src/TypeCatalogGen/powershell.inc" /nologo
	(cd ${WRKSRC}/src/TypeCatalogGen && \
	       ${SETENV} ${DOTNET_ENV} dotnet run --no-restore ../System.Management.Automation/CoreCLR/CorePsTypeCatalog.cs powershell.inc)
	# build powershell
	(cd ${WRKSRC}/src/powershell-unix && \
		${SETENV} ${DOTNET_ENV} dotnet build -c ${BUILD_CONFIGURATION} --no-restore)
	# build powershell-native
	(cd ${WRKSRC}/external/powershell-native/src/libpsl-native && \
		make)

do-install:
	${MKDIR} ${STATEDIR}${PREFIX}/lib/powershell
	(cd ${WRKSRC}/src/powershell-unix/bin/Release/netcoreapp2.1 && \
		${COPYTREE_SHARE} . ${STAGEDIR}${PREFIX}/lib/powershell)
	${INSTALL_LIB} ${WRKSRC}/external/powershell-native/src/powershell-unix/libpsl-native.so ${STAGEDIR}${PREFIX}/lib/powershell
	${INSTALL_SCRIPT} files/pwsh ${STAGEDIR}${PREFIX}/bin
	${REINPLACE_CMD} -e 's|%%PREFIX%%|${PREFIX}|g' ${STAGEDIR}${PREFIX}/bin/pwsh

.include <bsd.port.mk>
