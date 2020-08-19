---
title: Zabezpečení mikroslužeb a webových aplikací .NET
description: Zabezpečení u mikroslužeb a webových aplikací .NET – Získejte informace o možnostech ověřování v ASP.NET Core webových aplikacích.
author: mjrousos
ms.date: 08/07/2020
ms.openlocfilehash: 1dcdb5d2987360ac583fa700a387d977f498d1d9
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608098"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="02557-103">Zajištění zabezpečených mikroslužeb a webových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="02557-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="02557-104">K dispozici je mnoho aspektů zabezpečení v mikroslužbách a webových aplikacích, které mohou v tématu snadno získat několik knih, jako je tato.</span><span class="sxs-lookup"><span data-stu-id="02557-104">There are so many aspects about security in microservices and web applications that the topic could easily take several books like this one.</span></span> <span data-ttu-id="02557-105">V této části se proto zaměříme na ověřování, autorizaci a tajné klíče aplikací.</span><span class="sxs-lookup"><span data-stu-id="02557-105">So, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="02557-106">Implementace ověřování v mikroslužbách a webových aplikacích .NET</span><span class="sxs-lookup"><span data-stu-id="02557-106">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="02557-107">Pro prostředky a rozhraní API, které služba publikovala, je často potřeba omezit na určité důvěryhodné uživatele nebo klienty.</span><span class="sxs-lookup"><span data-stu-id="02557-107">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="02557-108">Prvním krokem pro provedení těchto řazení rozhodnutí o důvěryhodnosti na úrovni rozhraní API je ověřování.</span><span class="sxs-lookup"><span data-stu-id="02557-108">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="02557-109">Ověřování je proces spolehlivého ověřování identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="02557-109">Authentication is the process of reliably verifying a user's identity.</span></span>

<span data-ttu-id="02557-110">Ve scénářích mikroslužeb se ověřování obvykle zpracovává centrálně.</span><span class="sxs-lookup"><span data-stu-id="02557-110">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="02557-111">Pokud používáte bránu API, je brána vhodná pro ověření, jak je znázorněno na obrázku 9-1.</span><span class="sxs-lookup"><span data-stu-id="02557-111">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="02557-112">Pokud použijete tento přístup, ujistěte se, že k jednotlivým mikroslužbám nejde získat přímý přístup (bez brány API), pokud se neuskuteční další zabezpečení pro ověřování zpráv bez ohledu na to, jestli pocházejí z brány nebo ne.</span><span class="sxs-lookup"><span data-stu-id="02557-112">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Diagram znázorňující, jak mobilní aplikace klienta komunikuje s back-endu.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="02557-114">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="02557-114">**Figure 9-1**.</span></span> <span data-ttu-id="02557-115">Centralizované ověřování pomocí brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="02557-115">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="02557-116">Když brána API vycentralizaci ověřování, přidá informace o uživateli při předávání požadavků mikroslužbám.</span><span class="sxs-lookup"><span data-stu-id="02557-116">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="02557-117">Pokud se k službám dají získat přístup přímo, můžete k ověřování uživatelů použít ověřovací službu, jako je Azure Active Directory nebo vyhrazená mikroslužba ověřování, která funguje jako služba tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="02557-117">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="02557-118">Rozhodnutí o důvěryhodnosti se sdílí mezi službami s tokeny zabezpečení nebo soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="02557-118">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="02557-119">(Tyto tokeny je možné v případě potřeby sdílet mezi ASP.NET Core aplikacemi, a to implementací [sdílení souborů cookie](/aspnet/core/security/cookie-sharing).) Tento model je znázorněn na obrázku 9-2.</span><span class="sxs-lookup"><span data-stu-id="02557-119">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Diagram znázorňující ověřování prostřednictvím back-endovéch mikroslužeb.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="02557-121">**Obrázek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="02557-121">**Figure 9-2**.</span></span> <span data-ttu-id="02557-122">Ověřování pomocí mikroslužby identity; vztah důvěryhodnosti se sdílí pomocí autorizačního tokenu.</span><span class="sxs-lookup"><span data-stu-id="02557-122">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="02557-123">Pokud jsou mikroslužby k dispozici přímo, důvěřuje, která zahrnuje ověřování a autorizaci, je zpracována tokenem zabezpečení vydaným pomocí vyhrazené mikroslužby, která je sdílena mezi mikroslužbami.</span><span class="sxs-lookup"><span data-stu-id="02557-123">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="02557-124">Ověřování pomocí ASP.NET Core identity</span><span class="sxs-lookup"><span data-stu-id="02557-124">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="02557-125">Primárním mechanismem v ASP.NET Core pro identifikaci uživatelů aplikace je systém členství [ASP.NET Core identit](/aspnet/core/security/authentication/identity) .</span><span class="sxs-lookup"><span data-stu-id="02557-125">The primary mechanism in ASP.NET Core for identifying an application's users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="02557-126">ASP.NET Core identity ukládá informace o uživateli (včetně přihlašovacích údajů, rolí a deklarací) do úložiště dat nakonfigurovaného vývojářem.</span><span class="sxs-lookup"><span data-stu-id="02557-126">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="02557-127">Úložiště dat ASP.NET Core identity je obvykle úložiště Entity Framework, které je součástí `Microsoft.AspNetCore.Identity.EntityFrameworkCore` balíčku.</span><span class="sxs-lookup"><span data-stu-id="02557-127">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="02557-128">Vlastní úložiště nebo jiné balíčky třetích stran ale můžou sloužit k ukládání informací o identitě do Azure Table Storage, CosmosDB nebo jiných umístění.</span><span class="sxs-lookup"><span data-stu-id="02557-128">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="02557-129">ASP.NET Core 2,1 a novější poskytuje [ASP.NET Core identitu](/aspnet/core/security/authentication/identity) jako [knihovnu tříd Razor](/aspnet/core/razor-pages/ui-class), takže v projektu neuvidíte spoustu potřebného kódu, stejně jako v případě předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="02557-129">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="02557-130">Podrobnosti o tom, jak přizpůsobit kód identity podle vašich potřeb, najdete v tématu [Identita uživatelského rozhraní v ASP.NET Core projektech](/aspnet/core/security/authentication/scaffold-identity).</span><span class="sxs-lookup"><span data-stu-id="02557-130">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="02557-131">Následující kód je pořízen z šablony projektu ASP.NET Core Web Application MVC 3,1 s vybraným ověřováním individuálního uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="02557-131">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="02557-132">Ukazuje, jak nakonfigurovat ASP.NET Core identity pomocí Entity Framework Core v `Startup.ConfigureServices` metodě.</span><span class="sxs-lookup"><span data-stu-id="02557-132">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

<span data-ttu-id="02557-133">Jakmile je ASP.NET Core identita nakonfigurovaná, můžete ji povolit přidáním `app.UseAuthentication()` a, `endpoints.MapRazorPages()` jak je znázorněno v následujícím kódu v metodě služby `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="02557-133">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> <span data-ttu-id="02557-134">Řádky v předcházejícím kódu **musí být v pořadí, v jakém jsou uvedeny** pro správné fungování identity.</span><span class="sxs-lookup"><span data-stu-id="02557-134">The lines in the preceeding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="02557-135">Použití ASP.NET Core identity umožňuje několik scénářů:</span><span class="sxs-lookup"><span data-stu-id="02557-135">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="02557-136">Vytvořte nové informace o uživateli pomocí typu UserManager (userManager. CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="02557-136">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="02557-137">Ověřování uživatelů pomocí typu SignInManager</span><span class="sxs-lookup"><span data-stu-id="02557-137">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="02557-138">Můžete použít `signInManager.SignInAsync` pro přihlášení přímo nebo `signInManager.PasswordSignInAsync` pro potvrzení, že je heslo uživatele správné a pak se do něj přihlásí.</span><span class="sxs-lookup"><span data-stu-id="02557-138">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user's password is correct and then sign them in.</span></span>

- <span data-ttu-id="02557-139">Identifikujte uživatele na základě informací uložených v souboru cookie (načtený middleware ASP.NET Core identity) tak, aby následné požadavky z prohlížeče zahrnovaly identitu a deklarace uživatele přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="02557-139">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user's identity and claims.</span></span>

<span data-ttu-id="02557-140">ASP.NET Core identita také podporuje [dvojúrovňové ověřování](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="02557-140">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="02557-141">V případě scénářů ověřování, které využívají úložiště dat místního uživatele a které trvaly identity mezi požadavky pomocí souborů cookie (jako jsou typické pro webové aplikace MVC), ASP.NET Core identita je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="02557-141">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="02557-142">Ověřování pomocí externích zprostředkovatelů</span><span class="sxs-lookup"><span data-stu-id="02557-142">Authenticate with external providers</span></span>

<span data-ttu-id="02557-143">ASP.NET Core podporuje také použití [externích zprostředkovatelů ověřování](/aspnet/core/security/authentication/social/) , aby se uživatelé mohli přihlašovat prostřednictvím toků [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) .</span><span class="sxs-lookup"><span data-stu-id="02557-143">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="02557-144">To znamená, že se uživatelé můžou přihlásit pomocí stávajících procesů ověřování od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter, a přidružit tyto identity k identitě ASP.NET Core ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="02557-144">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="02557-145">Chcete-li použít externí ověřování, kromě včetně middlewaru ověřování, jak je uvedeno dříve, pomocí `app.UseAuthentication()` metody, je také nutné zaregistrovat externího poskytovatele v aplikaci, `Startup` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="02557-145">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

<span data-ttu-id="02557-146">Oblíbená externí poskytovatelé ověřování a jejich přidružené balíčky NuGet jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="02557-146">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="02557-147">**Poskytovatel**</span><span class="sxs-lookup"><span data-stu-id="02557-147">**Provider**</span></span>  | <span data-ttu-id="02557-148">**Balíček**</span><span class="sxs-lookup"><span data-stu-id="02557-148">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="02557-149">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="02557-149">**Microsoft**</span></span> | <span data-ttu-id="02557-150">**Microsoft. AspNetCore. Authentication. MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="02557-150">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="02557-151">**Google**</span><span class="sxs-lookup"><span data-stu-id="02557-151">**Google**</span></span>    | <span data-ttu-id="02557-152">**Microsoft. AspNetCore. Authentication. Google**</span><span class="sxs-lookup"><span data-stu-id="02557-152">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="02557-153">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="02557-153">**Facebook**</span></span>  | <span data-ttu-id="02557-154">**Microsoft. AspNetCore. Authentication. Facebook**</span><span class="sxs-lookup"><span data-stu-id="02557-154">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="02557-155">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="02557-155">**Twitter**</span></span>   | <span data-ttu-id="02557-156">**Microsoft. AspNetCore. Authentication. Twitter**</span><span class="sxs-lookup"><span data-stu-id="02557-156">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="02557-157">Ve všech případech musíte dokončit postup registrace aplikace, který je závislý na dodavateli a který obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="02557-157">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="02557-158">Získává se ID klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="02557-158">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="02557-159">Načítá se tajný klíč klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="02557-159">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="02557-160">Konfigurace adresy URL pro přesměrování, kterou zpracovává middleware autorizace a registrovaný poskytovatel</span><span class="sxs-lookup"><span data-stu-id="02557-160">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="02557-161">Volitelně můžete nakonfigurovat přihlašovací adresu URL pro správné zpracování odhlášení ve scénáři jednotného přihlašování (SSO).</span><span class="sxs-lookup"><span data-stu-id="02557-161">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="02557-162">Podrobnosti o konfiguraci aplikace pro externího poskytovatele najdete v dokumentaci k ASP.NET Core v tématu [ověřování externího poskytovatele](/aspnet/core/security/authentication/social/).</span><span class="sxs-lookup"><span data-stu-id="02557-162">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

>[!TIP]
><span data-ttu-id="02557-163">Všechny podrobnosti zpracovává middleware autorizace a výše zmíněné služby.</span><span class="sxs-lookup"><span data-stu-id="02557-163">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="02557-164">Proto stačí zvolit možnost ověřování **jednotlivých uživatelských účtů** při vytváření projektu webové aplikace ASP.NET code v aplikaci Visual Studio, jak je znázorněno na obrázku 9-3, kromě registrace výše zmíněných zprostředkovatelů ověřování.</span><span class="sxs-lookup"><span data-stu-id="02557-164">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![Snímek obrazovky dialogového okna Nový ASP.NET Core webové aplikace](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="02557-166">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="02557-166">**Figure 9-3**.</span></span> <span data-ttu-id="02557-167">Výběr možnosti jednotlivých uživatelských účtů pro použití externího ověřování při vytváření projektu webové aplikace v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="02557-167">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="02557-168">Kromě externích poskytovatelů ověřování uvedených v předchozích částech jsou k dispozici balíčky třetích stran, které poskytují middleware pro používání mnoha dalších externích poskytovatelů ověřování.</span><span class="sxs-lookup"><span data-stu-id="02557-168">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="02557-169">Seznam najdete v úložišti [ASPNET. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="02557-169">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="02557-170">Můžete také vytvořit vlastní middleware pro externí ověřování a vyřešit určité zvláštní potřeby.</span><span class="sxs-lookup"><span data-stu-id="02557-170">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="02557-171">Ověřování pomocí nosných tokenů</span><span class="sxs-lookup"><span data-stu-id="02557-171">Authenticate with bearer tokens</span></span>

<span data-ttu-id="02557-172">Ověřování pomocí ASP.NET Core identity (nebo zprostředkovatelů identity a externích ověřování) funguje dobře pro mnoho scénářů webových aplikací, ve kterých je vhodné ukládat informace o uživatelích v souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="02557-172">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="02557-173">V jiných scénářích se ale soubory cookie nejedná o přirozený způsob uchování a přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="02557-173">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="02557-174">Například v ASP.NET Core webové rozhraní API, které zveřejňuje koncové body RESTful, které mohou být k dispozici v aplikacích s jedním stránkou (jednostránkové), nativními klienty nebo dokonce jinými webovými rozhraními API, obvykle chcete místo toho použít ověřování pomocí nosných tokenů.</span><span class="sxs-lookup"><span data-stu-id="02557-174">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="02557-175">Tyto typy aplikací nefungují se soubory cookie, ale můžou snadno získat nosný token a zahrnout ho do autorizační hlavičky dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="02557-175">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="02557-176">Pokud chcete povolit ověřování pomocí tokenu, ASP.NET Core podporuje několik možností pro použití [OAuth 2,0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="02557-176">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="02557-177">Ověřování pomocí zprostředkovatele identity OpenID Connect nebo OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="02557-177">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="02557-178">Pokud jsou informace o uživateli uložené v Azure Active Directory nebo jiném řešení identity, které podporuje OpenID Connect nebo OAuth 2,0, můžete k ověření použít pracovní postup OpenID Connect pomocí balíčku **Microsoft. AspNetCore. Authentication. OpenIdConnect** .</span><span class="sxs-lookup"><span data-stu-id="02557-178">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="02557-179">Chcete-li například ověřit identitu. rozhraní API mikroslužeb v eShopOnContainers, může webová aplikace ASP.NET Core použít middleware z tohoto balíčku, jak je znázorněno v následujícím zjednodušeném příkladu `Startup.cs` :</span><span class="sxs-lookup"><span data-stu-id="02557-179">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = Configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

<span data-ttu-id="02557-180">Pamatujte na to, že když použijete tento pracovní postup, ASP.NET Core middleware identity není potřeba, protože veškeré úložiště informací o uživatelích a ověřování zpracovává služba identit.</span><span class="sxs-lookup"><span data-stu-id="02557-180">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="02557-181">Vydávání tokenů zabezpečení z ASP.NET Core služby</span><span class="sxs-lookup"><span data-stu-id="02557-181">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="02557-182">Pokud dáváte přednost vydávání tokenů zabezpečení pro místní ASP.NET Core uživatelů identity místo používání externího poskytovatele identity, můžete využít některé z dobrých knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="02557-182">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="02557-183">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) jsou poskytovatelé, kteří se snadno integrují pomocí ASP.NET Core identity, a umožňují tak vydávat tokeny zabezpečení ze služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="02557-183">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="02557-184">[Dokumentace k IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) obsahuje podrobné pokyny pro používání knihovny.</span><span class="sxs-lookup"><span data-stu-id="02557-184">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="02557-185">Základní kroky pro použití IdentityServer4 k vydávání tokenů jsou ale následující.</span><span class="sxs-lookup"><span data-stu-id="02557-185">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="02557-186">Voláte aplikaci. UseIdentityServer v metodě Startup.Configurovat pro přidání IdentityServer4 do kanálu zpracování požadavků HTTP aplikace.</span><span class="sxs-lookup"><span data-stu-id="02557-186">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application's HTTP request processing pipeline.</span></span> <span data-ttu-id="02557-187">To umožňuje knihovně zajišťovat požadavky na koncové body OpenID Connect a OAuth2 jako/Connect/token.</span><span class="sxs-lookup"><span data-stu-id="02557-187">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="02557-188">IdentityServer4 ve službě Startup.ConfigureServices nakonfigurujete tak, že zavoláte služby. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="02557-188">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="02557-189">Server identit konfigurujete nastavením následujících dat:</span><span class="sxs-lookup"><span data-stu-id="02557-189">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="02557-190">[Přihlašovací údaje](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) , které se mají použít k podepisování</span><span class="sxs-lookup"><span data-stu-id="02557-190">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="02557-191">[Prostředky identity a rozhraní API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) , které uživatelé mohou požadovat přístup:</span><span class="sxs-lookup"><span data-stu-id="02557-191">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="02557-192">Prostředky rozhraní API reprezentují chráněná data nebo funkce, ke kterým má uživatel přístup pomocí přístupového tokenu.</span><span class="sxs-lookup"><span data-stu-id="02557-192">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="02557-193">Příkladem prostředku rozhraní API může být webové rozhraní API (nebo sada rozhraní API), které vyžaduje autorizaci.</span><span class="sxs-lookup"><span data-stu-id="02557-193">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="02557-194">Prostředky identity představují informace (deklarace identity), které jsou předány klientovi k identifikaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="02557-194">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="02557-195">Deklarace identity můžou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="02557-195">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="02557-196">[Klienti](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , kteří se budou připojovat za účelem žádosti o tokeny.</span><span class="sxs-lookup"><span data-stu-id="02557-196">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="02557-197">Mechanizmus úložiště pro informace o uživateli, například [ASP.NET Core identitu](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) nebo alternativu.</span><span class="sxs-lookup"><span data-stu-id="02557-197">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="02557-198">Když zadáte klienty a prostředky, které má IdentityServer4 použít, můžete předat <xref:System.Collections.Generic.IEnumerable%601> kolekci příslušného typu metodám, které přijímají úložiště klientů v paměti nebo zdrojů.</span><span class="sxs-lookup"><span data-stu-id="02557-198">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="02557-199">V případě složitějších scénářů můžete poskytovat typy klientů nebo prostředků poskytovatele prostřednictvím injektáže závislostí.</span><span class="sxs-lookup"><span data-stu-id="02557-199">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="02557-200">Ukázková konfigurace IdentityServer4 pro použití prostředků v paměti a klientů, které poskytuje vlastní typ IClientStore, může vypadat podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="02557-200">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a><span data-ttu-id="02557-201">Využívat tokeny zabezpečení</span><span class="sxs-lookup"><span data-stu-id="02557-201">Consume security tokens</span></span>

<span data-ttu-id="02557-202">Ověřování pomocí koncového bodu OpenID Connect nebo vydávání vlastních tokenů zabezpečení se zabývá některými scénáři.</span><span class="sxs-lookup"><span data-stu-id="02557-202">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="02557-203">Ale jak potřebujete službu, která jednoduše potřebuje omezit přístup k uživatelům, kteří mají platné tokeny zabezpečení, které byly poskytnuty jinou službou?</span><span class="sxs-lookup"><span data-stu-id="02557-203">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="02557-204">V tomto scénáři je k dispozici middleware ověřování, který zpracovává tokeny JWT v balíčku **Microsoft. AspNetCore. Authentication. JwtBearer** .</span><span class="sxs-lookup"><span data-stu-id="02557-204">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="02557-205">JWT představuje "[JSON web token](https://tools.ietf.org/html/rfc7519)" a je běžný formát tokenu zabezpečení (definovaný v dokumentu RFC 7519) pro komunikaci s deklaracemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="02557-205">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="02557-206">Zjednodušený příklad, jak použít middleware ke využívání takových tokenů, může vypadat jako fragment kódu z řazení. mikroslužba API eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="02557-206">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

<span data-ttu-id="02557-207">Parametry v tomto použití jsou:</span><span class="sxs-lookup"><span data-stu-id="02557-207">The parameters in this usage are:</span></span>

- <span data-ttu-id="02557-208">`Audience` představuje přijímač příchozího tokenu nebo prostředku, ke kterému token uděluje přístup.</span><span class="sxs-lookup"><span data-stu-id="02557-208">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="02557-209">Pokud hodnota zadaná v tomto parametru neodpovídá parametru v tokenu, token se odmítne.</span><span class="sxs-lookup"><span data-stu-id="02557-209">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="02557-210">`Authority` je adresa ověřovacího serveru pro vydávání tokenů.</span><span class="sxs-lookup"><span data-stu-id="02557-210">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="02557-211">Middleware pro ověření nosiče JWT pomocí tohoto identifikátoru URI získá veřejný klíč, který lze použít k ověření podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="02557-211">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="02557-212">Middleware také potvrdí, že `iss` parametr v tokenu odpovídá tomuto identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="02557-212">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="02557-213">Další parametr, `RequireHttpsMetadata` , je užitečný pro účely testování. Tento parametr nastavíte na hodnotu false, abyste mohli testovat v prostředích, kde nemáte certifikáty.</span><span class="sxs-lookup"><span data-stu-id="02557-213">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="02557-214">V reálných nasazeních by se tokeny JWT nosiče měly vždycky předávat jenom přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="02557-214">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="02557-215">Díky tomuto middlewaru jsou tokeny JWT automaticky extrahovány z autorizačních hlaviček.</span><span class="sxs-lookup"><span data-stu-id="02557-215">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="02557-216">Pak jsou deserializovatelné, ověřené (pomocí hodnot v `Audience` `Authority` parametrech a) a uložené jako informace o uživateli, na které se později odkazuje pomocí akcí MVC nebo filtrů autorizace.</span><span class="sxs-lookup"><span data-stu-id="02557-216">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="02557-217">Middleware pro ověření nosiče JWT může také podporovat pokročilejší scénáře, jako je například použití místního certifikátu k ověření tokenu, není-li tato autorita k dispozici.</span><span class="sxs-lookup"><span data-stu-id="02557-217">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="02557-218">V tomto scénáři můžete určit `TokenValidationParameters` objekt v `JwtBearerOptions` objektu.</span><span class="sxs-lookup"><span data-stu-id="02557-218">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="02557-219">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="02557-219">Additional resources</span></span>

- <span data-ttu-id="02557-220">**Sdílení souborů cookie mezi aplikacemi** </span><span class="sxs-lookup"><span data-stu-id="02557-220">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="02557-221">**Úvod do identity** </span><span class="sxs-lookup"><span data-stu-id="02557-221">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="02557-222">**Rick Anderson. Dvojúrovňové ověřování pomocí SMS** </span><span class="sxs-lookup"><span data-stu-id="02557-222">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="02557-223">**Povolení ověřování přes Facebook, Google a další externí poskytovatele** </span><span class="sxs-lookup"><span data-stu-id="02557-223">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="02557-224">**Michell Anicas. Úvod k OAuth 2** </span><span class="sxs-lookup"><span data-stu-id="02557-224">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="02557-225">**ASPNET. Security. OAuth. Providers** (úložiště GitHub pro poskytovatele OAuth ASP.NET) </span><span class="sxs-lookup"><span data-stu-id="02557-225">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="02557-226">**IdentityServer4. Oficiální dokumentace** </span><span class="sxs-lookup"><span data-stu-id="02557-226">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="02557-227">[Předchozí](../implement-resilient-applications/monitor-app-health.md) 
> [Další](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="02557-227">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
