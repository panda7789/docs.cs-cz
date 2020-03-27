---
title: ASP.NET Zásadní změny
titleSuffix: ''
description: Uvádí nejnovější změny v ASP.NET jádru.
ms.date: 03/26/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 05272032f2b93c8ae89377a20e6fdafc2ff0eb7b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345331"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Zásadní změny

ASP.NET Core poskytuje funkce vývoje webových aplikací používané rozhraním .NET Core.

Na této stránce jsou popsány následující změny:

- [Byla odebrána zastaralá antiforgerií, CORS, diagnostika, MVC a směrovací api](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Ověřování: Vyřazení Google+](#authentication-google-deprecated-and-replaced)
- [Ověřování: Vlastnost HttpContext.Authentication byla odebrána.](#authentication-httpcontextauthentication-property-removed)
- [Ověřování: Newtonsoft.Json typy nahrazeny](#authentication-newtonsoftjson-types-replaced)
- [Ověřování: Podpis OAuthHandler ExchangeCodeAsync byl změněn.](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Autorizace: AddAuthorization přetížení přesunuta do jiného sestavení](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Autorizace: IAllowAnonymous odebrán z AuthorizationFilterContext.Filters](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Autorizace: Implementace IAuthorizationPolicyProvider vyžadují novou metodu](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure: Odebrané balíčky integrace Azure s předponou Microsoftu](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Ukládání do mezipaměti: CompactOnMemoryPressure vlastnost odstraněna](#caching-compactonmemorypressure-property-removed)
- [Ukládání do mezipaměti: Microsoft.Extensions.Caching.SqlServer používá nový balíček SqlClient](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Ukládání do mezipaměti: ResponseCaching "pubternal" typy změněny na vnitřní](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Ochrana dat: DataProtection.AzureStorage používá nová api úložiště Azure](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Hosting: AspNetCoreModule V1 odstraněn z Windows Hosting Bundle](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Hostování: Obecný hostitel omezuje injekci konstruktoru spuštění](#hosting-generic-host-restricts-startup-constructor-injection)
- [Hostování: Přesměrování HTTPS povoleno pro mimoprocesové aplikace služby IIS](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hosting: IHostingEnvironment a IApplicationLifetime typy nahrazeny](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Hostování: Objekt Usvého zprostředkovatele objectpoolu odebrán ze závislostí WebHostBuilder](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: Prohlížeč SameSite změny dopad ověřování](#http-browser-samesite-changes-impact-authentication)
- [HTTP: VýchozíhttpContext rozšiřitelnost odebrána](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: Pole HeaderNames byla změněna na statickou jen pro čtení.](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: Změny infrastruktury těla odezvy](#http-response-body-infrastructure-changes)
- [HTTP: Některé výchozí hodnoty cookie SameSite se změnily](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: Synchronní vi zakázánve výchozím nastavení](#http-synchronous-io-disabled-in-all-servers)
- [Identita: Přetížení metody AddDefaultUI bylo odebráno.](#identity-adddefaultui-method-overload-removed)
- [Identita: Změna verze zaváděcích verzí ui bootstrap](#identity-default-bootstrap-version-of-ui-changed)
- [Identita: SignInAsync vyvolá výjimku pro neověřenou identitu](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Identita: Konstruktor SignInManager přijímá nový parametr.](#identity-signinmanager-constructor-accepts-new-parameter)
- [Identita: Uživatelské uživatelské zařízení používá funkci statických webových datových zdrojů](#identity-ui-uses-static-web-assets-feature)
- [Poštolka: Připojení adaptéry odstraněny](#kestrel-connection-adapters-removed)
- [Poštolek: Prázdná sestava HTTPS byla odebrána.](#kestrel-empty-https-assembly-removed)
- [Poštolka: Žádost trailer záhlaví přesunuta do nové kolekce](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Poštolek: Změny vrstvy transportní abstrakce](#kestrel-transport-abstractions-removed-and-made-public)
- [Lokalizace: API označená jako zastaralá](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Protokolování: Třída DebugLogger byla interní](#logging-debuglogger-class-made-internal)
- [MVC: Akce řadiče Asynchronní přípona byla odebrána](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult byl přesunut do microsoft.aspNetCore.Mvc.Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: Nástroj předběžné kompilace se zastaral](#mvc-precompilation-tool-deprecated)
- [MVC: Typy změněné na interní](#mvc-pubternal-types-changed-to-internal)
- [MVC: Překrytí kompatibility webového rozhraní byla odstraněna.](#mvc-web-api-compatibility-shim-removed)
- [Razor: Runtime kompilace přesunuta do balíčku](#razor-runtime-compilation-moved-to-a-package)
- [Stav relace: Odebraná zastaralá api](#session-state-obsolete-apis-removed)
- [Sdílený rámec: Odebrání sestavení z Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Sdílený rámec: Microsoft.AspNetCore.All odebrán](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR: HandshakeProtocol.SuccessHandshakeData nahrazen](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR: Metody připojení hubu odebrány](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR: Konstruktory HubConnectionContext byly změněny.](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR: Změna názvu klientského balíčku JavaScript](#signalr-javascript-client-package-name-changed)
- [SignalR: MessagePack Hub Protocol byl přesunut na balíček MessagePack 2.x](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [Signalizátor: Zastaralá api](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [SignalR: UseSignalR a UseConnections metody odebrány](#signalr-usesignalr-and-useconnections-methods-removed)
- [SPAServices a NodeServices konzola logger záložní změna](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [SPAServices a NodeServices označené jako zastaralé](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Cílový rámec: Rozhraní .NET Framework není podporováno.](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET jádro 5.0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET jádro 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET jádro 3.0

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
