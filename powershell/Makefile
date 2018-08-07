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
NUGET_DEPENDS=	Markdig.Signed=0.15.1 \
		Microsoft.ApplicationInsights=2.6.4 \
		Microsoft.CodeAnalysis.Analyzers=1.1.0 \
		Microsoft.CodeAnalysis.Common=2.8.2 \
		Microsoft.CodeAnalysis.CSharp=2.8.2 \
		Microsoft.Management.Infrastructure=1.0.0-alpha08 \
		Microsoft.NETCore.App=2.0.0 \
		Microsoft.NETCore.App=2.1.2 \
		Microsoft.NETCore.DotNetAppHost=2.1.2 \
		Microsoft.NETCore.DotNetHostPolicy=2.0.0 \
		Microsoft.NETCore.DotNetHostPolicy=2.1.2 \
		Microsoft.NETCore.DotNetHostResolver=2.1.2 \
		Microsoft.NETCore.Platforms=1.0.1 \
		Microsoft.NETCore.Platforms=1.1.0 \
		Microsoft.NETCore.Platforms=2.0.0 \
		Microsoft.NETCore.Platforms=2.1.0 \
		Microsoft.NETCore.Targets=1.0.1 \
		Microsoft.NETCore.Targets=1.1.0 \
		Microsoft.NETCore.Targets=2.0.0 \
		Microsoft.NETCore.Windows.ApiSets=1.0.1 \
		Microsoft.Win32.Registry=4.5.0 \
		Microsoft.Win32.Registry.AccessControl=4.5.0 \
		Microsoft.Win32.SystemEvents=4.5.0 \
		Microsoft.Windows.Compatibility=2.0.0 \
		Microsoft.Windows.Compatibility.Shims=2.0.0 \
		NETStandard.Library=1.6.1 \
		NETStandard.Library=2.0.0 \
		NETStandard.Library=2.0.3 \
		Newtonsoft.Json=9.0.1 \
		Newtonsoft.Json=11.0.2 \
		NJsonSchema=9.10.63 \
		runtime.debian.8-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.fedora.23-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.fedora.24-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.linux-x64.Microsoft.NETCore.App=2.0.0 \
		runtime.linux-x64.Microsoft.NETCore.App=2.1.2 \
		runtime.linux-x64.Microsoft.NETCore.DotNetAppHost=2.1.2 \
		runtime.linux-x64.Microsoft.NETCore.DotNetHostPolicy=2.1.2 \
		runtime.linux-x64.Microsoft.NETCore.DotNetHostResolver=2.1.2 \
		runtime.native.System=4.3.0 \
		runtime.native.System.Data.SqlClient.sni=4.4.0 \
		runtime.native.System.IO.Compression=4.3.0 \
		runtime.native.System.Net.Http=4.3.0 \
		runtime.native.System.Security.Cryptography.Apple=4.3.0 \
		runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.opensuse.13.2-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.opensuse.42.1-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.osx-x64.Microsoft.NETCore.App=2.0.0 \
		runtime.osx-x64.Microsoft.NETCore.App=2.1.2 \
		runtime.osx-x64.Microsoft.NETCore.DotNetAppHost=2.1.2 \
		runtime.osx-x64.Microsoft.NETCore.DotNetHostPolicy=2.1.2 \
		runtime.osx-x64.Microsoft.NETCore.DotNetHostResolver=2.1.2 \
		runtime.osx.10.10-x64.runtime.native.System.Security.Cryptography.Apple=4.3.0 \
		runtime.osx.10.10-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.rhel.7-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.ubuntu.14.04-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.ubuntu.16.04-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.ubuntu.16.10-x64.runtime.native.System.Security.Cryptography.OpenSsl=4.3.0 \
		runtime.win-x64.Microsoft.NETCore.App=2.0.0 \
		runtime.win-x64.Microsoft.NETCore.App=2.1.2 \
		runtime.win-x64.Microsoft.NETCore.DotNetAppHost=2.0.0 \
		runtime.win-x64.Microsoft.NETCore.DotNetAppHost=2.1.2 \
		runtime.win-x64.Microsoft.NETCore.DotNetHostPolicy=2.0.0 \
		runtime.win-x64.Microsoft.NETCore.DotNetHostPolicy=2.1.2 \
		runtime.win-x64.Microsoft.NETCore.DotNetHostResolver=2.0.0 \
		runtime.win-x64.Microsoft.NETCore.DotNetHostResolver=2.1.2 \
		runtime.win-x86.Microsoft.NETCore.App=2.0.0 \
		runtime.win-x86.Microsoft.NETCore.App=2.1.2 \
		runtime.win-x86.Microsoft.NETCore.DotNetAppHost=2.0.0 \
		runtime.win-x86.Microsoft.NETCore.DotNetAppHost=2.1.2 \
		runtime.win-x86.Microsoft.NETCore.DotNetHostPolicy=2.0.0 \
		runtime.win-x86.Microsoft.NETCore.DotNetHostPolicy=2.1.2 \
		runtime.win-x86.Microsoft.NETCore.DotNetHostResolver=2.0.0 \
		runtime.win-x86.Microsoft.NETCore.DotNetHostResolver=2.1.2 \
		runtime.win-arm64.runtime.native.System.Data.SqlClient.sni=4.4.0 \
		runtime.win-x64.runtime.native.System.Data.SqlClient.sni=4.4.0 \
		runtime.win-x86.runtime.native.System.Data.SqlClient.sni=4.4.0 \
		System.AppContext=4.3.0 \
		System.Buffers=4.3.0 \
		System.CodeDom=4.5.0 \
		System.Collections=4.0.11 \
		System.Collections=4.3.0 \
		System.Collections.Concurrent=4.3.0 \
		System.Collections.Immutable=1.3.0 \
		System.Collections.Immutable=1.3.1 \
		System.ComponentModel.Composition=4.5.0 \
		System.Configuration.ConfigurationManager=4.5.0 \
		System.Console=4.3.0 \
		System.Data.DataSetExtensions=4.5.0 \
		System.Data.Odbc=4.5.0 \
		System.Data.SqlClient=4.5.1 \
		System.Diagnostics.Debug=4.0.11 \
		System.Diagnostics.Debug=4.3.0 \
		System.Diagnostics.DiagnosticSource=4.3.0 \
		System.Diagnostics.DiagnosticSource=4.4.0 \
		System.Diagnostics.EventLog=4.5.0 \
		System.Diagnostics.FileVersionInfo=4.3.0 \
		System.Diagnostics.PerformanceCounter=4.5.0 \
		System.Diagnostics.StackTrace=4.3.0 \
		System.Diagnostics.Tools=4.0.1 \
		System.Diagnostics.Tools=4.3.0 \
		System.Diagnostics.Tracing=4.3.0 \
		System.DirectoryServices=4.5.0 \
		System.DirectoryServices.AccountManagement=4.5.0 \
		System.DirectoryServices.Protocols=4.5.0 \
		System.Drawing.Common=4.5.0 \
		System.Dynamic.Runtime=4.0.11 \
		System.Dynamic.Runtime=4.3.0 \
		System.Globalization=4.0.11 \
		System.Globalization=4.3.0 \
		System.Globalization.Calendars=4.3.0 \
		System.Globalization.Extensions=4.3.0 \
		System.IO=4.1.0 \
		System.IO=4.3.0 \
		System.IO.Compression=4.3.0 \
		System.IO.FileSystem=4.0.1 \
		System.IO.FileSystem=4.3.0 \
		System.IO.FileSystem.AccessControl=4.5.0 \
		System.IO.FileSystem.Primitives=4.0.1 \
		System.IO.FileSystem.Primitives=4.3.0 \
		System.IO.Packaging=4.5.0 \
		System.IO.Pipes.AccessControl=4.5.0 \
		System.IO.Ports=4.5.0 \
		System.Linq=4.1.0 \
		System.Linq=4.3.0 \
		System.Linq.Expressions=4.1.0 \
		System.Linq.Expressions=4.3.0 \
		System.Management=4.5.0 \
		System.Net.Http=4.3.0 \
		System.Net.Http.WinHttpHandler=4.5.0 \
		System.Net.Primitives=4.3.0 \
		System.Net.Requests=4.3.0 \
		System.Net.WebHeaderCollection=4.3.0 \
		System.ObjectModel=4.0.12 \
		System.ObjectModel=4.3.0 \
		System.Private.DataContractSerialization=4.3.0 \
		System.Private.ServiceModel=4.5.2 \
		System.Reflection=4.1.0 \
		System.Reflection=4.3.0 \
		System.Reflection.DispatchProxy=4.5.0 \
		System.Reflection.Emit=4.0.1 \
		System.Reflection.Emit=4.3.0 \
		System.Reflection.Emit.ILGeneration=4.0.1 \
		System.Reflection.Emit.ILGeneration=4.3.0 \
		System.Reflection.Emit.Lightweight=4.0.1 \
		System.Reflection.Emit.Lightweight=4.3.0 \
		System.Reflection.Extensions=4.0.1 \
		System.Reflection.Extensions=4.3.0 \
		System.Reflection.Metadata=1.4.1 \
		System.Reflection.Metadata=1.4.2 \
		System.Reflection.Primitives=4.0.1 \
		System.Reflection.Primitives=4.3.0 \
		System.Reflection.TypeExtensions=4.1.0 \
		System.Reflection.TypeExtensions=4.3.0 \
		System.Resources.ResourceManager=4.0.1 \
		System.Resources.ResourceManager=4.3.0 \
		System.Runtime=4.1.0 \
		System.Runtime=4.3.0 \
		System.Runtime.Caching=4.5.0 \
		System.Runtime.CompilerServices.Unsafe=4.5.0 \
		System.Runtime.CompilerServices.VisualC=4.3.0 \
		System.Runtime.Extensions=4.1.0 \
		System.Runtime.Extensions=4.3.0 \
		System.Runtime.Handles=4.0.1 \
		System.Runtime.Handles=4.3.0 \
		System.Runtime.InteropServices=4.1.0 \
		System.Runtime.InteropServices=4.3.0 \
		System.Runtime.Numerics=4.3.0 \
		System.Runtime.Serialization.Primitives=4.1.1 \
		System.Runtime.Serialization.Primitives=4.3.0 \
		System.Runtime.Serialization.Xml=4.3.0 \
		System.Security.AccessControl=4.5.0 \
		System.Security.Cryptography.Algorithms=4.3.0 \
		System.Security.Cryptography.Cng=4.3.0 \
		System.Security.Cryptography.Cng=4.5.0 \
		System.Security.Cryptography.Csp=4.3.0 \
		System.Security.Cryptography.Encoding=4.3.0 \
		System.Security.Cryptography.OpenSsl=4.3.0 \
		System.Security.Cryptography.Pkcs=4.5.0 \
		System.Security.Cryptography.Primitives=4.3.0 \
		System.Security.Cryptography.ProtectedData=4.5.0 \
		System.Security.Cryptography.X509Certificates=4.3.0 \
		System.Security.Cryptography.Xml=4.5.0 \
		System.Security.Permissions=4.5.0 \
		System.Security.Principal.Windows=4.5.0 \
		System.Security.SecureString=4.3.0 \
		System.ServiceModel.Duplex=4.5.2 \
		System.ServiceModel.Http=4.5.2 \
		System.ServiceModel.NetTcp=4.5.2 \
		System.ServiceModel.Primitives=4.5.2 \
		System.ServiceModel.Security=4.5.2 \
		System.ServiceModel.Syndication=4.5.0 \
		System.ServiceProcess.ServiceController=4.5.0 \
		System.Text.Encoding=4.0.11 \
		System.Text.Encoding=4.3.0 \
		System.Text.Encoding.CodePages=4.3.0 \
		System.Text.Encoding.CodePages=4.5.0 \
		System.Text.Encoding.Extensions=4.0.11 \
		System.Text.Encoding.Extensions=4.3.0 \
		System.Text.Encodings.Web=4.5.0 \
		System.Text.RegularExpressions=4.1.0 \
		System.Text.RegularExpressions=4.3.0 \
		System.Threading=4.0.11 \
		System.Threading=4.3.0 \
		System.Threading.AccessControl=4.5.0 \
		System.Threading.Tasks=4.0.11 \
		System.Threading.Tasks=4.3.0 \
		System.Threading.Tasks.Extensions=4.0.0 \
		System.Threading.Tasks.Extensions=4.3.0 \
		System.Threading.Tasks.Parallel=4.3.0 \
		System.Threading.Thread=4.3.0 \
		System.Threading.ThreadPool=4.3.0 \
		System.ValueTuple=4.3.0 \
		System.Xml.ReaderWriter=4.0.11 \
		System.Xml.ReaderWriter=4.3.0 \
		System.Xml.XDocument=4.0.11 \
		System.Xml.XDocument=4.3.0 \
		System.Xml.XmlDocument=4.3.0 \
		System.Xml.XmlSerializer=4.3.0 \
		System.Xml.XPath=4.3.0 \
		System.Xml.XPath.XDocument=4.3.0 \

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
	sh -c "cd ${WRKSRC}/src/ResGen && dotnet build --no-restore && dotnet --fx-version $$(cat ${WRKSRC}/shared-framework-version.txt) bin/Debug/netcoreapp2.0/resgen.dll"
	# generate type catalog
	cat files/typecatalog.txt > ${WRKSRC}/src/Microsoft.PowerShell.SDK/obj/Microsoft.PowerShell.SDK.csproj.TypeCatalog.targets
	dotnet msbuild ${WRKSRC}/src/Microsoft.PowerShell.SDK/Microsoft.PowerShell.SDK.csproj /t:_GetDependencies "/property:DesignTimeBuild=true;_DependencyFile=${WRKSRC}/src/TypeCatalogGen/powershell.inc" /nologo
	sh -c "cd ${WRKSRC}/src/TypeCatalogGen && dotnet run --no-restore ../System.Management.Automation/CoreCLR/CorePsTypeCatalog.cs powershell.inc"
	# build powershell
	sh -c "cd ${WRKSRC}/src/powershell-unix && dotnet build --no-restore"
	# build powershell-native
	sh -c "cd ${WRKSRC}/external/powershell-native/src/libpsl-native && make"
	# copy native build results
	${CP} ${WRKSRC}/external/powershell-native/src/powershell-unix/libpsl-native.so ${WRKSRC}/src/powershell-unix/bin/Debug/netcoreapp2.1/libpsl-native.so
	# copy executable
	${CP} files/pwsh ${WRKSRC}/src/powershell-unix/bin/Debug/netcoreapp2.1/pwsh

.include <bsd.port.mk>
