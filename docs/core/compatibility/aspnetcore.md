---
title: ASP.NET Core přerušující změny
titleSuffix: ''
description: Zobrazí seznam nejnovějších změn v ASP.NET Core.
ms.date: 07/10/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 1a3c8b04bc574822f1576ca0720ed7a01c303880
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281677"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Core přerušující změny

ASP.NET Core poskytuje funkce pro vývoj webových aplikací, které používá .NET Core.

Na této stránce jsou popsány následující přerušující se změny:

- [Odebrání zastaralých rozhraní API pro antipadělání, CORS, diagnostiku, MVC a směrování](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Ověřování: Google + zastaralá](#authentication-google-deprecated-and-replaced)
- [Ověřování: vlastnost HttpContext. Authentication byla odebrána.](#authentication-httpcontextauthentication-property-removed)
- [Ověřování: Newtonsoft.Jsu nahrazených typů](#authentication-newtonsoftjson-types-replaced)
- [Ověřování: změnil se podpis OAuthHandler ExchangeCodeAsync.](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Autorizace: přetížení AddAuthorization se přesunulo do jiného sestavení.](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Autorizace: IAllowAnonymous se odebral z AuthorizationFilterContext. filters.](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Autorizace: implementace IAuthorizationPolicyProvider vyžadují novou metodu.](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure: odebraly se balíčky Microsoft infixních integrací Azure.](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Blazor: nevýznamné prázdné znaky oříznuté z komponent v době kompilace](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [Ukládání do mezipaměti: byla odebrána vlastnost CompactOnMemoryPressure](#caching-compactonmemorypressure-property-removed)
- [Ukládání do mezipaměti: Microsoft. Extensions. Caching. SqlServer používá nový balíček SqlClient.](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Ukládání do mezipaměti: ResponseCaching typy "pubternal" se změnily na interní](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Ochrana dat: DataProtection. AzureStorage používá nová rozhraní API Azure Storage.](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Rozšíření: změny odkazů balíčku ovlivňují některé balíčky NuGet](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [Hostování: AspNetCoreModule v1 odebrané ze sady hostování Windows](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Hostování: obecný hostitel omezuje úvodní vkládání spouštěcího konstruktoru.](#hosting-generic-host-restricts-startup-constructor-injection)
- [Hostování: přesměrování protokolu HTTPS je povolené pro vnitroprocesové aplikace IIS.](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hostování: nahrazené typy IHostingEnvironment a IApplicationLifetime](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Hostování: ObjectPoolProvider se odebral ze závislostí WebHostBuilder.](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: typy Kestrel a IIS BadHttpRequestException označené jako zastaralé a nahrazené](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [HTTP: Browser SameSite změny dopadu na ověření](#http-browser-samesite-changes-impact-authentication)
- [HTTP: rozšíření DefaultHttpContext bylo odebráno.](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: HeaderNames pole se změnila na static jen pro čtení.](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: HttpClient instance vytvořené pomocí kódů IHttpClientFactory pro celočíselné hodnoty log status](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [HTTP: změny infrastruktury textu odpovědi](#http-response-body-infrastructure-changes)
- [HTTP: některé soubory cookie SameSite výchozí hodnoty se změnily](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: ve výchozím nastavení je zakázaná synchronní v/v.](#http-synchronous-io-disabled-in-all-servers)
- [HttpSys: nové vyjednávání klientského certifikátu je ve výchozím nastavení zakázané.](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [Identita: přetížení metody AddDefaultUI bylo odebráno.](#identity-adddefaultui-method-overload-removed)
- [Identita: Změna verze Bootstrap uživatelského rozhraní](#identity-default-bootstrap-version-of-ui-changed)
- [Identita: SignInAsync vyvolá výjimku pro neověřenou identitu.](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Identita: konstruktor SignInManager akceptuje nový parametr.](#identity-signinmanager-constructor-accepts-new-parameter)
- [Identita: uživatelské rozhraní používá funkci statických webových prostředků.](#identity-ui-uses-static-web-assets-feature)
- [IIS: UrlRewrite řetězce dotazů middleware jsou zachovány.](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [Kestrel: ve výchozím nastavení se zjistily změny v konfiguraci v době běhu.](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [Kestrel: odebrané adaptéry připojení](#kestrel-connection-adapters-removed)
- [Kestrel: výchozí podporované verze protokolu TLS se změnily](#kestrel-default-supported-tls-protocol-versions-changed)
- [Kestrel: bylo odebráno prázdné sestavení HTTPS.](#kestrel-empty-https-assembly-removed)
- [Kestrel: HTTP/2 zakázáno přes TLS v nekompatibilních verzích Windows](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [Kestrel: hlavičky přípojných vozidel žádosti přesunuté do nové kolekce](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel: změny vrstvy abstrakce transportu](#kestrel-transport-abstractions-removed-and-made-public)
- [Lokalizace: rozhraní API označená jako zastaralá](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Lokalizace: rozhraní API "Pubternal" byla odebrána](#localization-pubternal-apis-removed)
- [Lokalizace: v middlewari pro lokalizaci požadavků byl odebrán zastaralý konstruktor.](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [Lokalizace: odebral se člen rozhraní třídy ResourceManagerWithCultureStringLocalizer a WithCulture.](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [Protokolování: DebugLogger třída provedla interní](#logging-debuglogger-class-made-internal)
- [MVC: byla odebrána asynchronní přípona akce řadiče.](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult se přesunula do Microsoft. AspNetCore. Mvc. Core.](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: zastaralý nástroj předkompilace](#mvc-precompilation-tool-deprecated)
- [MVC: typy se změnily na interní](#mvc-pubternal-types-changed-to-internal)
- [MVC: překrytí kompatibility webového rozhraní API se odebralo.](#mvc-web-api-compatibility-shim-removed)
- [Razor: kompilace za běhu byla přesunuta do balíčku](#razor-runtime-compilation-moved-to-a-package)
- [Stav relace: odebrané zastaralé rozhraní API](#session-state-obsolete-apis-removed)
- [Sdílené rozhraní: odebrání sestavení z Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Sdílené rozhraní: Microsoft. AspNetCore. All odebral](#shared-framework-removed-microsoftaspnetcoreall)
- [Signál: HandshakeProtocol. SuccessHandshakeData nahrazeno](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [Signál: odebrané metody HubConnection](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [Signál: HubConnectionContext konstruktory se změnily.](#signalr-hubconnectioncontext-constructors-changed)
- [Signal: Změna názvu balíčku klienta JavaScript](#signalr-javascript-client-package-name-changed)
- [Signal: protokol centra MessagePack se přesunul do balíčku MessagePack 2. x.](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [Signal: typ možností protokolu centra MessagePack se změnil.](#signalr-messagepack-hub-protocol-options-type-changed)
- [Signál: zastaralé rozhraní API](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [Signál: metody UseSignalR a UseConnections se odebraly.](#signalr-usesignalr-and-useconnections-methods-removed)
- [Jednostránkové: SpaServices a výchozí změna nouzového výchozího nastavení nástroje konzoly NodeServices](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [Jednostránkové: SpaServices a NodeServices označené jako zastaralé](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Statické soubory: typ obsahu CSV se změnil na vyhovující standardům.](#static-files-csv-content-type-changed-to-standards-compliant)
- [Cílová architektura: .NET Framework není podporovaná.](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET Core 5,0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

***

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

***

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

***
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

***

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET Core 3,1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3,0

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
