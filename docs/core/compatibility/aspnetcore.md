---
title: ASP.NET Core přerušující změny
titleSuffix: ''
description: Zobrazí seznam nejnovějších změn v ASP.NET Core.
ms.date: 08/20/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 4f37bf73c13379bce006c9a3b51302c09562cc44
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811256"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="e2a0a-103">ASP.NET Core přerušující změny</span><span class="sxs-lookup"><span data-stu-id="e2a0a-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="e2a0a-104">ASP.NET Core poskytuje funkce pro vývoj webových aplikací, které používá .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="e2a0a-105">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="e2a0a-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="e2a0a-106">Odebrání zastaralých rozhraní API pro antipadělání, CORS, diagnostiku, MVC a směrování</span><span class="sxs-lookup"><span data-stu-id="e2a0a-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="e2a0a-107">Ověřování: Google + zastaralá</span><span class="sxs-lookup"><span data-stu-id="e2a0a-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="e2a0a-108">Ověřování: vlastnost HttpContext. Authentication byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="e2a0a-109">Ověřování: Newtonsoft.Jsu nahrazených typů</span><span class="sxs-lookup"><span data-stu-id="e2a0a-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="e2a0a-110">Ověřování: změnil se podpis OAuthHandler ExchangeCodeAsync.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="e2a0a-111">Autorizace: přetížení AddAuthorization se přesunulo do jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="e2a0a-112">Autorizace: IAllowAnonymous se odebral z AuthorizationFilterContext. filters.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="e2a0a-113">Autorizace: implementace IAuthorizationPolicyProvider vyžadují novou metodu.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="e2a0a-114">Autorizace: prostředek ve směrování koncového bodu je HttpContext</span><span class="sxs-lookup"><span data-stu-id="e2a0a-114">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="e2a0a-115">Azure: odebraly se balíčky Microsoft infixních integrací Azure.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-115">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="e2a0a-116">Metody serializace BinaryFormatter jsou zastaralé a zakázané v aplikacích ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e2a0a-116">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="e2a0a-117">Blazor: nevýznamné prázdné znaky oříznuté z komponent v době kompilace</span><span class="sxs-lookup"><span data-stu-id="e2a0a-117">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="e2a0a-118">Blazor: Cílová architektura balíčků NuGet se změnila</span><span class="sxs-lookup"><span data-stu-id="e2a0a-118">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="e2a0a-119">Ukládání do mezipaměti: byla odebrána vlastnost CompactOnMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="e2a0a-119">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="e2a0a-120">Ukládání do mezipaměti: Microsoft. Extensions. Caching. SqlServer používá nový balíček SqlClient.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-120">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="e2a0a-121">Ukládání do mezipaměti: ResponseCaching typy "pubternal" se změnily na interní</span><span class="sxs-lookup"><span data-stu-id="e2a0a-121">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="e2a0a-122">Ochrana dat: DataProtection. AzureStorage používá nová rozhraní API Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-122">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="e2a0a-123">Rozšíření: změny odkazů balíčku ovlivňují některé balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="e2a0a-123">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="e2a0a-124">Hostování: AspNetCoreModule v1 odebrané ze sady hostování Windows</span><span class="sxs-lookup"><span data-stu-id="e2a0a-124">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="e2a0a-125">Hostování: obecný hostitel omezuje úvodní vkládání spouštěcího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-125">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="e2a0a-126">Hostování: přesměrování protokolu HTTPS je povolené pro vnitroprocesové aplikace IIS.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-126">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="e2a0a-127">Hostování: nahrazené typy IHostingEnvironment a IApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="e2a0a-127">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="e2a0a-128">Hostování: ObjectPoolProvider se odebral ze závislostí WebHostBuilder.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-128">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="e2a0a-129">HTTP: typy Kestrel a IIS BadHttpRequestException označené jako zastaralé a nahrazené</span><span class="sxs-lookup"><span data-stu-id="e2a0a-129">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="e2a0a-130">HTTP: Browser SameSite změny dopadu na ověření</span><span class="sxs-lookup"><span data-stu-id="e2a0a-130">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="e2a0a-131">HTTP: rozšíření DefaultHttpContext bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-131">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="e2a0a-132">HTTP: HeaderNames pole se změnila na static jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-132">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="e2a0a-133">HTTP: HttpClient instance vytvořené pomocí kódů IHttpClientFactory pro celočíselné hodnoty log status</span><span class="sxs-lookup"><span data-stu-id="e2a0a-133">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="e2a0a-134">HTTP: změny infrastruktury textu odpovědi</span><span class="sxs-lookup"><span data-stu-id="e2a0a-134">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="e2a0a-135">HTTP: některé soubory cookie SameSite výchozí hodnoty se změnily</span><span class="sxs-lookup"><span data-stu-id="e2a0a-135">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="e2a0a-136">HTTP: ve výchozím nastavení je zakázaná synchronní v/v.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-136">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="e2a0a-137">HttpSys: nové vyjednávání klientského certifikátu je ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-137">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="e2a0a-138">Identita: přetížení metody AddDefaultUI bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-138">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="e2a0a-139">Identita: Změna verze Bootstrap uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2a0a-139">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="e2a0a-140">Identita: SignInAsync vyvolá výjimku pro neověřenou identitu.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-140">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="e2a0a-141">Identita: konstruktor SignInManager akceptuje nový parametr.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-141">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="e2a0a-142">Identita: uživatelské rozhraní používá funkci statických webových prostředků.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-142">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="e2a0a-143">IIS: UrlRewrite řetězce dotazů middleware jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-143">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="e2a0a-144">Kestrel: ve výchozím nastavení se zjistily změny v konfiguraci v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-144">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="e2a0a-145">Kestrel: odebrané adaptéry připojení</span><span class="sxs-lookup"><span data-stu-id="e2a0a-145">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="e2a0a-146">Kestrel: výchozí podporované verze protokolu TLS se změnily</span><span class="sxs-lookup"><span data-stu-id="e2a0a-146">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="e2a0a-147">Kestrel: bylo odebráno prázdné sestavení HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-147">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="e2a0a-148">Kestrel: HTTP/2 zakázáno přes TLS v nekompatibilních verzích Windows</span><span class="sxs-lookup"><span data-stu-id="e2a0a-148">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="e2a0a-149">Kestrel: přenos Libuv označený jako zastaralý</span><span class="sxs-lookup"><span data-stu-id="e2a0a-149">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="e2a0a-150">Kestrel: hlavičky přípojných vozidel žádosti přesunuté do nové kolekce</span><span class="sxs-lookup"><span data-stu-id="e2a0a-150">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="e2a0a-151">Kestrel: změny vrstvy abstrakce transportu</span><span class="sxs-lookup"><span data-stu-id="e2a0a-151">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="e2a0a-152">Lokalizace: rozhraní API označená jako zastaralá</span><span class="sxs-lookup"><span data-stu-id="e2a0a-152">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="e2a0a-153">Lokalizace: rozhraní API "Pubternal" byla odebrána</span><span class="sxs-lookup"><span data-stu-id="e2a0a-153">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="e2a0a-154">Lokalizace: v middlewari pro lokalizaci požadavků byl odebrán zastaralý konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-154">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="e2a0a-155">Lokalizace: odebral se člen rozhraní třídy ResourceManagerWithCultureStringLocalizer a WithCulture.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-155">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="e2a0a-156">Protokolování: DebugLogger třída provedla interní</span><span class="sxs-lookup"><span data-stu-id="e2a0a-156">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="e2a0a-157">Middleware: chybová stránka databáze je označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-157">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="e2a0a-158">MVC: byla odebrána asynchronní přípona akce řadiče.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-158">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="e2a0a-159">MVC: JsonResult se přesunula do Microsoft. AspNetCore. Mvc. Core.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-159">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="e2a0a-160">MVC: zastaralý nástroj předkompilace</span><span class="sxs-lookup"><span data-stu-id="e2a0a-160">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="e2a0a-161">MVC: typy se změnily na interní</span><span class="sxs-lookup"><span data-stu-id="e2a0a-161">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="e2a0a-162">MVC: překrytí kompatibility webového rozhraní API se odebralo.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-162">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="e2a0a-163">Razor: kompilace za běhu byla přesunuta do balíčku</span><span class="sxs-lookup"><span data-stu-id="e2a0a-163">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="e2a0a-164">Zabezpečení: odebrání kódování názvu souboru cookie</span><span class="sxs-lookup"><span data-stu-id="e2a0a-164">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="e2a0a-165">Zabezpečení: aktualizace verzí balíčku NuGet IdentityModel</span><span class="sxs-lookup"><span data-stu-id="e2a0a-165">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="e2a0a-166">Stav relace: odebrané zastaralé rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e2a0a-166">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="e2a0a-167">Sdílené rozhraní: odebrání sestavení z Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="e2a0a-167">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="e2a0a-168">Sdílené rozhraní: Microsoft. AspNetCore. All odebral</span><span class="sxs-lookup"><span data-stu-id="e2a0a-168">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="e2a0a-169">Signál: HandshakeProtocol. SuccessHandshakeData nahrazeno</span><span class="sxs-lookup"><span data-stu-id="e2a0a-169">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="e2a0a-170">Signál: odebrané metody HubConnection</span><span class="sxs-lookup"><span data-stu-id="e2a0a-170">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="e2a0a-171">Signál: HubConnectionContext konstruktory se změnily.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-171">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="e2a0a-172">Signal: Změna názvu balíčku klienta JavaScript</span><span class="sxs-lookup"><span data-stu-id="e2a0a-172">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="e2a0a-173">Signal: protokol centra MessagePack se přesunul do balíčku MessagePack 2. x.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-173">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="e2a0a-174">Signal: typ možností protokolu centra MessagePack se změnil.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-174">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="e2a0a-175">Signál: zastaralé rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e2a0a-175">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="e2a0a-176">Signál: metody UseSignalR a UseConnections se odebraly.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-176">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="e2a0a-177">Jednostránkové: SpaServices a výchozí změna nouzového výchozího nastavení nástroje konzoly NodeServices</span><span class="sxs-lookup"><span data-stu-id="e2a0a-177">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="e2a0a-178">Jednostránkové: SpaServices a NodeServices označené jako zastaralé</span><span class="sxs-lookup"><span data-stu-id="e2a0a-178">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="e2a0a-179">Statické soubory: typ obsahu CSV se změnil na vyhovující standardům.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-179">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="e2a0a-180">Cílová architektura: .NET Framework není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="e2a0a-180">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="e2a0a-181">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="e2a0a-181">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Blazor: Target framework of NuGet packages changed](~/includes/core-changes/aspnetcore/5.0/blazor-packages-target-framework-changed.md)]

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

[!INCLUDE[Kestrel: Libuv transport marked as obsolete](~/includes/core-changes/aspnetcore/5.0/kestrel-libuv-transport-obsolete.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[Middleware: Database error page marked as obsolete](~/includes/core-changes/aspnetcore/5.0/middleware-database-error-page-obsolete.md)]

***

[!INCLUDE[Security: Cookie name encoding removed](~/includes/core-changes/aspnetcore/5.0/security-cookie-name-encoding-removed.md)]

***

[!INCLUDE[Security: IdentityModel NuGet package versions updated](~/includes/core-changes/aspnetcore/5.0/security-identitymodel-nuget-package-versions-updated.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="e2a0a-182">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e2a0a-182">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="e2a0a-183">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="e2a0a-183">ASP.NET Core 3.0</span></span>

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
