---
title: IdentityServer pro nativní cloudové aplikace
description: Architekt cloudových nativních aplikací .NET pro Azure | IdentityServer
ms.date: 05/13/2020
ms.openlocfilehash: 81cce30568becacda29f65f9506398790af321e0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614029"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="d1741-103">IdentityServer pro cloudové nativní aplikace</span><span class="sxs-lookup"><span data-stu-id="d1741-103">IdentityServer for cloud-native applications</span></span>

<span data-ttu-id="d1741-104">IdentityServer je Open Source Server pro ověřování, který implementuje standardy OpenID Connect (OIDC) a OAuth 2,0 pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d1741-104">IdentityServer is an open-source authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="d1741-105">Je navržený tak, aby poskytoval běžný způsob, jak ověřovat požadavky na všechny vaše aplikace, ať už jsou to webové, nativní, mobilní nebo koncové body rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d1741-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="d1741-106">IdentityServer se dá použít k implementaci jednotného přihlašování (SSO) pro více aplikací a typů aplikací.</span><span class="sxs-lookup"><span data-stu-id="d1741-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="d1741-107">Dá se použít k ověření skutečných uživatelů pomocí formulářů pro přihlášení a podobných uživatelských rozhraní i ověřování na základě služby, které obvykle zahrnuje vystavení, ověřování a obnovování tokenů bez uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d1741-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="d1741-108">IdentityServer je navržený tak, aby bylo přizpůsobitelné řešení.</span><span class="sxs-lookup"><span data-stu-id="d1741-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="d1741-109">Každá instance se obvykle přizpůsobí konkrétní organizaci a/nebo sadě požadavků aplikací.</span><span class="sxs-lookup"><span data-stu-id="d1741-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="d1741-110">Běžné scénáře webových aplikací</span><span class="sxs-lookup"><span data-stu-id="d1741-110">Common web app scenarios</span></span>

<span data-ttu-id="d1741-111">Aplikace obvykle potřebují podporovat některé nebo všechny z následujících scénářů:</span><span class="sxs-lookup"><span data-stu-id="d1741-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="d1741-112">Lidé, kteří přistupují k webovým aplikacím pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="d1741-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="d1741-113">Uživatelé, kteří získávají přístup k webovým rozhraním API back-endu z aplikací založených na prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="d1741-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="d1741-114">Uživatelé s mobilními nebo nativními klienty, kteří přistupují k back-endové webové rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d1741-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="d1741-115">Jiné aplikace přistupující do back-endové webové rozhraní API (bez aktivního uživatele nebo uživatelského rozhraní).</span><span class="sxs-lookup"><span data-stu-id="d1741-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="d1741-116">Každá aplikace může potřebovat interakci s dalšími webovými rozhraními API, pomocí vlastní identity nebo delegování identitě uživatele.</span><span class="sxs-lookup"><span data-stu-id="d1741-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

![Typy aplikací a scénáře](./media/application-types.png)

<span data-ttu-id="d1741-118">**Obrázek 8-1**.</span><span class="sxs-lookup"><span data-stu-id="d1741-118">**Figure 8-1**.</span></span> <span data-ttu-id="d1741-119">Typy a scénáře aplikace</span><span class="sxs-lookup"><span data-stu-id="d1741-119">Application types and scenarios.</span></span>

<span data-ttu-id="d1741-120">V každém z těchto scénářů musí být vystavené funkce zabezpečené před neoprávněným použitím.</span><span class="sxs-lookup"><span data-stu-id="d1741-120">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="d1741-121">Minimálně to obvykle vyžaduje ověření uživatele nebo objektu zabezpečení, který vytváří požadavek na prostředek.</span><span class="sxs-lookup"><span data-stu-id="d1741-121">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="d1741-122">Toto ověřování může používat jeden z několika běžných protokolů, jako je SAML2p, WS-doOpenID nebo Connect.</span><span class="sxs-lookup"><span data-stu-id="d1741-122">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="d1741-123">Komunikace s rozhraními API obvykle používá protokol OAuth2 a jeho podporu pro tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d1741-123">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="d1741-124">Oddělení těchto důležitých otázek zabezpečení a jejich prováděcích detailů od samotných aplikací zajišťuje konzistenci a zlepšuje zabezpečení a udržovatelnost.</span><span class="sxs-lookup"><span data-stu-id="d1741-124">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="d1741-125">Použití těchto otázek pro vyhrazený produkt, jako je IdentityServer, pomáhá požadavek každé aplikace tyto problémy vyřešit sami.</span><span class="sxs-lookup"><span data-stu-id="d1741-125">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="d1741-126">IdentityServer poskytuje middleware, který běží v aplikaci ASP.NET Core a přidává podporu pro OpenID Connect a OAuth2 (viz článek [podporované specifikace](http://docs.identityserver.io/en/latest/intro/specs.html)).</span><span class="sxs-lookup"><span data-stu-id="d1741-126">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](http://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="d1741-127">Organizace vytvoří svou vlastní aplikaci ASP.NET Core s využitím middlewaru IdentityServer k tomu, aby fungovala jako STS pro všechny protokoly zabezpečení založené na tokenech.</span><span class="sxs-lookup"><span data-stu-id="d1741-127">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="d1741-128">Middleware IdentityServer zpřístupňuje koncové body pro podporu standardních funkcí, včetně:</span><span class="sxs-lookup"><span data-stu-id="d1741-128">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="d1741-129">Autorizovat (ověření koncového uživatele)</span><span class="sxs-lookup"><span data-stu-id="d1741-129">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="d1741-130">Token (žádost o token prostřednictvím kódu programu)</span><span class="sxs-lookup"><span data-stu-id="d1741-130">Token (request a token programmatically)</span></span>
- <span data-ttu-id="d1741-131">Zjišťování (metadata o serveru)</span><span class="sxs-lookup"><span data-stu-id="d1741-131">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="d1741-132">Informace o uživateli (získat informace o uživateli pomocí platného přístupového tokenu)</span><span class="sxs-lookup"><span data-stu-id="d1741-132">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="d1741-133">Autorizace zařízení (používá se ke spuštění autorizace toku zařízení)</span><span class="sxs-lookup"><span data-stu-id="d1741-133">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="d1741-134">Introspekce (ověření tokenu)</span><span class="sxs-lookup"><span data-stu-id="d1741-134">Introspection (token validation)</span></span>
- <span data-ttu-id="d1741-135">Odvolání (odvolání tokenu)</span><span class="sxs-lookup"><span data-stu-id="d1741-135">Revocation (token revocation)</span></span>
- <span data-ttu-id="d1741-136">Ukončit relaci (aktivovat jednotné odhlašování napříč všemi aplikacemi)</span><span class="sxs-lookup"><span data-stu-id="d1741-136">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="d1741-137">Začínáme</span><span class="sxs-lookup"><span data-stu-id="d1741-137">Getting started</span></span>

<span data-ttu-id="d1741-138">IdentityServer4 je open source a zdarma ho použít.</span><span class="sxs-lookup"><span data-stu-id="d1741-138">IdentityServer4 is open-source and free to use.</span></span> <span data-ttu-id="d1741-139">Můžete ji přidat do svých aplikací pomocí svých balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="d1741-139">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="d1741-140">Hlavní balíček je [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) , který se stáhl více než 4 000 000 krát.</span><span class="sxs-lookup"><span data-stu-id="d1741-140">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="d1741-141">Základní balíček neobsahuje žádný kód uživatelského rozhraní a podporuje se jenom v konfiguraci paměti.</span><span class="sxs-lookup"><span data-stu-id="d1741-141">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="d1741-142">Pokud ho chcete použít s databází, budete také chtít poskytovatele dat, jako je [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) , který používá Entity Framework Core k ukládání konfiguračních a provozních dat pro IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="d1741-142">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="d1741-143">V případě uživatelského rozhraní můžete zkopírovat soubory z [úložiště uživatelského rozhraní pro rychlé](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) zprovoznění do aplikace ASP.NET Core MVC a přidat podporu pro přihlášení a odhlášení pomocí middlewaru IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="d1741-143">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="d1741-144">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d1741-144">Configuration</span></span>

<span data-ttu-id="d1741-145">IdentityServer podporuje různé druhy protokolů a poskytovatele pro sociální ověřování, které se dají konfigurovat jako součást každé vlastní instalace.</span><span class="sxs-lookup"><span data-stu-id="d1741-145">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="d1741-146">To se obvykle provádí ve třídě ASP.NET Core aplikace `Startup` v `ConfigureServices` metodě.</span><span class="sxs-lookup"><span data-stu-id="d1741-146">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="d1741-147">Konfigurace zahrnuje určení podporovaných protokolů a cest k serverům a koncovým bodům, které budou použity.</span><span class="sxs-lookup"><span data-stu-id="d1741-147">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="d1741-148">Obrázek 8-2 ukazuje ukázkovou konfiguraci pořízenou z projektu uživatelského rozhraní rychlého startu IdentityServer4:</span><span class="sxs-lookup"><span data-stu-id="d1741-148">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="d1741-149">**Obrázek 8-2**.</span><span class="sxs-lookup"><span data-stu-id="d1741-149">**Figure 8-2**.</span></span> <span data-ttu-id="d1741-150">Konfigurace IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="d1741-150">Configuring IdentityServer.</span></span>

<span data-ttu-id="d1741-151">IdentityServer také hostuje veřejnou ukázkovou lokalitu, která se dá použít k otestování různých protokolů a konfigurací.</span><span class="sxs-lookup"><span data-stu-id="d1741-151">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="d1741-152">Je umístěný na adrese [https://demo.identityserver.io/](https://demo.identityserver.io/) a obsahuje informace o tom, jak nakonfigurovat chování na základě `client_id` poskytovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="d1741-152">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="d1741-153">Klienti JavaScriptu</span><span class="sxs-lookup"><span data-stu-id="d1741-153">JavaScript clients</span></span>

<span data-ttu-id="d1741-154">Mnoho cloudových nativních aplikací využívá na front-endu rozhraní API na straně serveru a bohatých klientských aplikacích (jednostránkové).</span><span class="sxs-lookup"><span data-stu-id="d1741-154">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="d1741-155">IdentityServer dodává [JavaScriptový klient](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) ( `oidc-client.js` ) prostřednictvím NPM, který se dá přidat do jednostránkové a povolit tak použití IdentityServer pro přihlášení, odhlášení a ověřování webových rozhraní API na základě tokenu.</span><span class="sxs-lookup"><span data-stu-id="d1741-155">IdentityServer ships a [JavaScript client](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="d1741-156">Odkazy</span><span class="sxs-lookup"><span data-stu-id="d1741-156">References</span></span>

- [<span data-ttu-id="d1741-157">Dokumentace k IdentityServer</span><span class="sxs-lookup"><span data-stu-id="d1741-157">IdentityServer documentation</span></span>](http://docs.identityserver.io/en/latest/)
- [<span data-ttu-id="d1741-158">Typy aplikací</span><span class="sxs-lookup"><span data-stu-id="d1741-158">Application types</span></span>](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [<span data-ttu-id="d1741-159">Klient OIDC JavaScript</span><span class="sxs-lookup"><span data-stu-id="d1741-159">JavaScript OIDC client</span></span>](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="d1741-160">[Předchozí](azure-active-directory.md) 
> [Další](security.md)</span><span class="sxs-lookup"><span data-stu-id="d1741-160">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
