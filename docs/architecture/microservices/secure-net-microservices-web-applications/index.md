---
title: Zabezpečení mikroslužeb a webových aplikací .NET
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – seznamte se s možnostmi ověřování v ASP.NET základních webových aplikacích.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 0ac2591f8650e9f8cf29560735a9ec803d29ee4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628329"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="c091e-103">Zabezpečení mikroslužeb a webových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="c091e-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="c091e-104">Existuje tolik aspektů o zabezpečení v mikroslužbách a webových aplikacích, že téma může snadno trvat několik knih, jako je tento, takže v této části se zaměříme na ověřování, autorizaci a tajné kódy aplikací.</span><span class="sxs-lookup"><span data-stu-id="c091e-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="c091e-105">Implementace ověřování v mikroslužbách a webových aplikacích rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="c091e-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="c091e-106">Často je nutné, aby prostředky a api publikovaná službou byly omezeny na určité důvěryhodné uživatele nebo klienty.</span><span class="sxs-lookup"><span data-stu-id="c091e-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="c091e-107">Prvním krokem k provedení těchto druhů rozhodnutí o důvěryhodnosti na úrovni rozhraní API je ověřování.</span><span class="sxs-lookup"><span data-stu-id="c091e-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="c091e-108">Ověřování je proces spolehlivého ověření identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="c091e-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="c091e-109">Ve scénářích mikroslužeb ověřování se obvykle zpracovává centrálně.</span><span class="sxs-lookup"><span data-stu-id="c091e-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="c091e-110">Pokud používáte bránu rozhraní API, brána je vhodné místo k ověření, jak je znázorněno na obrázku 9-1.</span><span class="sxs-lookup"><span data-stu-id="c091e-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="c091e-111">Pokud použijete tento přístup, ujistěte se, že jednotlivé mikroslužeb nelze dosáhnout přímo (bez brány rozhraní API), pokud je další zabezpečení na místě k ověření zprávy, zda pocházejí z brány nebo ne.</span><span class="sxs-lookup"><span data-stu-id="c091e-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Diagram znázorňující interakci klientské mobilní aplikace s back-endem.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="c091e-113">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="c091e-113">**Figure 9-1**.</span></span> <span data-ttu-id="c091e-114">Centralizované ověřování pomocí brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c091e-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="c091e-115">Když brána rozhraní API centralizuje ověřování, přidá informace o uživateli při předávání požadavků mikroslužbám.</span><span class="sxs-lookup"><span data-stu-id="c091e-115">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="c091e-116">Pokud ke službám lze přistupovat přímo, lze k ověření uživatelů použít ověřovací službu, jako je Azure Active Directory nebo vyhrazená mikroslužba pro ověřování, která funguje jako služba tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="c091e-116">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="c091e-117">Rozhodnutí o důvěryhodnosti jsou sdílena mezi službami pomocí tokenů zabezpečení nebo souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="c091e-117">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="c091e-118">(Tyto tokeny lze v případě potřeby sdílet mezi aplikacemi ASP.NET Core implementací [sdílení souborů cookie](/aspnet/core/security/cookie-sharing).) Tento vzor je znázorněn na obrázku 9-2.</span><span class="sxs-lookup"><span data-stu-id="c091e-118">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Diagram zobrazující ověřování prostřednictvím back-endových mikroslužeb.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="c091e-120">**Obrázek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="c091e-120">**Figure 9-2**.</span></span> <span data-ttu-id="c091e-121">Ověřování pomocí mikroslužby identity; vztah důvěryhodnosti je sdílen pomocí autorizačního tokenu</span><span class="sxs-lookup"><span data-stu-id="c091e-121">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="c091e-122">Při přístupu k mikroslužbám přímo, vztah důvěryhodnosti, který zahrnuje ověřování a autorizaci, je zpracován tokenem zabezpečení vydaným vyhrazenou mikroslužbou sdílenou mezi mikroslužbami.</span><span class="sxs-lookup"><span data-stu-id="c091e-122">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="c091e-123">Ověření pomocí ASP.NET základní identity</span><span class="sxs-lookup"><span data-stu-id="c091e-123">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="c091e-124">Primární mechanismus v ASP.NET Core pro identifikaci uživatelů aplikace je ASP.NET systém členství [základní identity.](/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="c091e-124">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="c091e-125">ASP.NET Core Identity ukládá informace o uživateli (včetně přihlašovacích informací, rolí a deklarací) v úložišti dat nakonfigurovaném vývojářem.</span><span class="sxs-lookup"><span data-stu-id="c091e-125">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="c091e-126">Úložiště dat ASP.NET základní identity je obvykle úložiště entity `Microsoft.AspNetCore.Identity.EntityFrameworkCore` framework poskytované v balíčku.</span><span class="sxs-lookup"><span data-stu-id="c091e-126">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="c091e-127">Vlastní úložiště nebo jiné balíčky třetích stran však lze použít k ukládání informací o identitě v Azure Table Storage, CosmosDB nebo jiných umístěních.</span><span class="sxs-lookup"><span data-stu-id="c091e-127">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="c091e-128">ASP.NET Core 2.1 a novější poskytuje [ASP.NET základní identity](/aspnet/core/security/authentication/identity) jako [knihovny tříd razor](/aspnet/core/razor-pages/ui-class), takže neuvidíte mnoho potřebného kódu v projektu, jako tomu bylo v případě předchozích verzí.</span><span class="sxs-lookup"><span data-stu-id="c091e-128">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="c091e-129">Podrobnosti o tom, jak přizpůsobit kód identity tak, aby vyhovoval vašim potřebám, naleznete v tématu [Identita lešení v ASP.NET základní projekty](/aspnet/core/security/authentication/scaffold-identity).</span><span class="sxs-lookup"><span data-stu-id="c091e-129">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="c091e-130">Následující kód je převzat z ASP.NET základní webové aplikace MVC 3.1 šablony projektu s individuální ověřování uživatelských účtů.</span><span class="sxs-lookup"><span data-stu-id="c091e-130">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="c091e-131">Ukazuje, jak nakonfigurovat ASP.NET základní identity `Startup.ConfigureServices` pomocí entity framework core v metodě.</span><span class="sxs-lookup"><span data-stu-id="c091e-131">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

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

<span data-ttu-id="c091e-132">Jakmile je ASP.NET základní identity nakonfigurován, `app.UseAuthentication()` `endpoints.MapRazorPages()` povolte ji přidáním a jak `Startup.Configure` je znázorněno v následujícím kódu v metodě služby:</span><span class="sxs-lookup"><span data-stu-id="c091e-132">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

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
> <span data-ttu-id="c091e-133">Řádky v předčíslí kód **musí být v pořadí zobrazeno** pro identitu pracovat správně.</span><span class="sxs-lookup"><span data-stu-id="c091e-133">The lines in the preceeding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="c091e-134">Použití ASP.NET základní identity umožňuje několik scénářů:</span><span class="sxs-lookup"><span data-stu-id="c091e-134">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="c091e-135">Vytvořte nové informace o uživateli pomocí typu UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="c091e-135">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="c091e-136">Ověřujte uživatele pomocí typu SignInManager.</span><span class="sxs-lookup"><span data-stu-id="c091e-136">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="c091e-137">Můžete použít `signInManager.SignInAsync` k přihlášení přímo, nebo `signInManager.PasswordSignInAsync` potvrdit heslo uživatele je správné a potom je přihlásit.</span><span class="sxs-lookup"><span data-stu-id="c091e-137">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="c091e-138">Identifikujte uživatele na základě informací uložených v souboru cookie (který je čten ASP.NET middleware Core Identity), takže následné požadavky z prohlížeče budou obsahovat identitu a deklarace identity přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="c091e-138">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="c091e-139">ASP.NET Core Identity také podporuje [dvoufaktorové ověřování](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="c091e-139">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="c091e-140">Pro scénáře ověřování, které využívají úložiště místních uživatelských dat a které přetrvávají identitu mezi požadavky pomocí souborů cookie (jak je typické pro webové aplikace MVC), ASP.NET core identity je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="c091e-140">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="c091e-141">Ověření u externích zprostředkovatelů</span><span class="sxs-lookup"><span data-stu-id="c091e-141">Authenticate with external providers</span></span>

<span data-ttu-id="c091e-142">ASP.NET Core také podporuje použití [externích poskytovatelů ověřování,](/aspnet/core/security/authentication/social/) aby uživatelé přihlášení prostřednictvím [Toků OAuth 2.0.](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="c091e-142">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="c091e-143">To znamená, že se uživatelé mohou přihlásit pomocí stávajících ověřovacích procesů od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter, a přidružit tyto identity k ASP.NET základní identity ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c091e-143">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="c091e-144">Chcete-li použít externí ověřování, kromě včetně ověřování middleware, jak je uvedeno dříve, pomocí `app.UseAuthentication()` metody, musíte také zaregistrovat externího zprostředkovatele v, `Startup` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c091e-144">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

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

<span data-ttu-id="c091e-145">Populární externí poskytovatelé ověřování a jejich přidružené balíčky NuGet jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c091e-145">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="c091e-146">**Poskytovatel**</span><span class="sxs-lookup"><span data-stu-id="c091e-146">**Provider**</span></span>  | <span data-ttu-id="c091e-147">**Balíček**</span><span class="sxs-lookup"><span data-stu-id="c091e-147">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="c091e-148">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="c091e-148">**Microsoft**</span></span> | <span data-ttu-id="c091e-149">**Účet Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="c091e-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="c091e-150">**Google**</span><span class="sxs-lookup"><span data-stu-id="c091e-150">**Google**</span></span>    | <span data-ttu-id="c091e-151">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="c091e-151">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="c091e-152">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="c091e-152">**Facebook**</span></span>  | <span data-ttu-id="c091e-153">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="c091e-153">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="c091e-154">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="c091e-154">**Twitter**</span></span>   | <span data-ttu-id="c091e-155">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="c091e-155">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="c091e-156">Ve všech případech je nutné provést postup registrace přihlášky, který je závislý na dodavateli a který obvykle zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="c091e-156">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="c091e-157">Získání ID klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c091e-157">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="c091e-158">Získání tajného klíče klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c091e-158">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="c091e-159">Konfigurace adresy URL přesměrování, která je zpracována middlewarem autorizace a registrovaným poskytovatelem</span><span class="sxs-lookup"><span data-stu-id="c091e-159">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="c091e-160">Volitelně konfigurace přihlašovací adresy URL pro správné zpracování odhlásit ve scénáři jednotného přihlášení (SSO).</span><span class="sxs-lookup"><span data-stu-id="c091e-160">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="c091e-161">Podrobnosti o konfiguraci aplikace pro externího zprostředkovatele najdete [v tématu ověřování externího zprostředkovatele v dokumentaci ASP.NET Core](/aspnet/core/security/authentication/social/)).</span><span class="sxs-lookup"><span data-stu-id="c091e-161">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

>[!TIP]
><span data-ttu-id="c091e-162">Všechny podrobnosti jsou zpracovány autorizace middleware a služby výše uvedené.</span><span class="sxs-lookup"><span data-stu-id="c091e-162">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="c091e-163">Takže stačí zvolit možnost ověřování **individuálního uživatelského účtu** při vytváření projektu webové aplikace ASP.NET code v sadě Visual Studio, jak je znázorněno na obrázku 9-3, kromě registrace poskytovatelů ověřování, které byly zmíněny.</span><span class="sxs-lookup"><span data-stu-id="c091e-163">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![Snímek obrazovky s dialogovým oknem Nová ASP.NET základní webová aplikace](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="c091e-165">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="c091e-165">**Figure 9-3**.</span></span> <span data-ttu-id="c091e-166">Výběr možnosti Jednotlivé uživatelské účty pro použití externího ověřování při vytváření projektu webové aplikace v Sadě Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="c091e-166">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="c091e-167">Kromě dříve uvedených externích poskytovatelů ověřování jsou k dispozici balíčky třetích stran, které poskytují middleware pro použití mnoha dalších externích poskytovatelů ověřování.</span><span class="sxs-lookup"><span data-stu-id="c091e-167">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="c091e-168">Seznam najdete v úložišti [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c091e-168">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="c091e-169">Můžete také vytvořit vlastní externí ověřování middleware vyřešit některé zvláštní potřeby.</span><span class="sxs-lookup"><span data-stu-id="c091e-169">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="c091e-170">Ověření pomocí nosné tokeny</span><span class="sxs-lookup"><span data-stu-id="c091e-170">Authenticate with bearer tokens</span></span>

<span data-ttu-id="c091e-171">Ověřování pomocí ASP.NET základní identity (nebo identity plus externích poskytovatelů ověřování) funguje dobře pro mnoho scénářů webových aplikací, ve kterých je vhodné ukládání informací o uživateli v souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="c091e-171">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="c091e-172">V jiných scénářích však soubory cookie nejsou přirozeným prostředkem k uchování a přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="c091e-172">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="c091e-173">Například v ASP.NET základní webové rozhraní API, které zpřístupňuje koncové body RESTful, ke kterým mohou přistupovat aplikace s jednou stránkou (SPA), nativní klienti nebo dokonce jinými webovými rozhraními API, obvykle chcete místo toho použít ověřování tokenu nosiče.</span><span class="sxs-lookup"><span data-stu-id="c091e-173">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="c091e-174">Tyto typy aplikací nefungují se soubory cookie, ale mohou snadno načíst token nosiče a zahrnout jej do hlavičky autorizace následných požadavků.</span><span class="sxs-lookup"><span data-stu-id="c091e-174">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="c091e-175">Chcete-li povolit ověřování tokenů, ASP.NET Core podporuje několik možností pro použití [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="c091e-175">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="c091e-176">Ověření pomocí poskytovatele identity OpenID Connect nebo OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="c091e-176">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="c091e-177">Pokud jsou informace o uživateli uložené ve službě Azure Active Directory nebo v jiném řešení identity, které podporuje OpenID Connect nebo OAuth 2.0, můžete použít balíček **Microsoft.AspNetCore.Authentication.OpenIdConnect** k ověření pomocí pracovního postupu OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="c091e-177">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="c091e-178">Například k ověření na Identity.Api mikroslužby v eShopOnContainers, ASP.NET základní webové aplikace můžete použít middleware `Startup.cs`z tohoto balíčku, jak je znázorněno v následujícím zjednodušeném příkladu v :</span><span class="sxs-lookup"><span data-stu-id="c091e-178">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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
    var sessionCookieLifetime = configuration.GetValue("SessionCookieLifetimeMinutes", 60);

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

<span data-ttu-id="c091e-179">Všimněte si, že při použití tohoto pracovního postupu middleware ASP.NET core identity není potřeba, protože všechny úložiště informací o uživateli a ověřování je zpracována službou Identity.</span><span class="sxs-lookup"><span data-stu-id="c091e-179">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="c091e-180">Vydávání tokenů zabezpečení ze služby ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c091e-180">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="c091e-181">Pokud dáváte přednost vydávání tokenů zabezpečení pro místní ASP.NET uživatele základní identity, než pomocí externího zprostředkovatele identity, můžete využít některé dobré knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="c091e-181">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="c091e-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) jsou poskytovatelé OpenID Connect, kteří se snadno integrují s ASP.NET základní identitou, aby vám dovolili vydávat tokeny zabezpečení ze služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c091e-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="c091e-183">Dokumentace [identityServer4](https://identityserver4.readthedocs.io/en/latest/) obsahuje podrobné pokyny pro použití knihovny.</span><span class="sxs-lookup"><span data-stu-id="c091e-183">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="c091e-184">Základní kroky k použití IdentityServer4 k vydávání tokenů jsou však následující.</span><span class="sxs-lookup"><span data-stu-id="c091e-184">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="c091e-185">Voláš do aplikace. UseIdentityServer v metodě Startup.Configure pro přidání identityServer4 do kanálu zpracování požadavků HTTP aplikace.</span><span class="sxs-lookup"><span data-stu-id="c091e-185">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="c091e-186">To umožňuje knihovně obsluhovat požadavky na koncové body OpenID Connect a OAuth2 jako /connect/token.</span><span class="sxs-lookup"><span data-stu-id="c091e-186">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="c091e-187">Server IdentityServer4 nakonfigurujete při spuštění.ConfigureServices voláním služeb. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="c091e-187">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="c091e-188">Server identit nakonfigurujete nastavením následujících dat:</span><span class="sxs-lookup"><span data-stu-id="c091e-188">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="c091e-189">[Pověření, která](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) chcete použít k podepisování.</span><span class="sxs-lookup"><span data-stu-id="c091e-189">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="c091e-190">Prostředky [identity a rozhraní API,](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) ke kterým mohou uživatelé požadovat přístup:</span><span class="sxs-lookup"><span data-stu-id="c091e-190">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="c091e-191">Prostředky rozhraní API představují chráněná data nebo funkce, ke kterým má uživatel přístup pomocí přístupového tokenu.</span><span class="sxs-lookup"><span data-stu-id="c091e-191">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="c091e-192">Příkladem prostředku rozhraní API by bylo webové rozhraní API (nebo sada rozhraní API), které vyžaduje autorizaci.</span><span class="sxs-lookup"><span data-stu-id="c091e-192">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="c091e-193">Prostředky identity představují informace (deklarace), které jsou dány klientovi k identifikaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="c091e-193">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="c091e-194">Deklarace identity mohou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c091e-194">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="c091e-195">[Klienti,](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) kteří se budou připojovat, aby mohli požadovat tokeny.</span><span class="sxs-lookup"><span data-stu-id="c091e-195">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="c091e-196">Mechanismus úložiště pro informace o uživateli, jako je [například ASP.NET základní identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) nebo alternativu.</span><span class="sxs-lookup"><span data-stu-id="c091e-196">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="c091e-197">Když zadáte klienty a prostředky pro IdentityServer4 <xref:System.Collections.Generic.IEnumerable%601> použít, můžete předat kolekci příslušného typu metody, které se v paměti klienta nebo úložiště prostředků.</span><span class="sxs-lookup"><span data-stu-id="c091e-197">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="c091e-198">Nebo pro složitější scénáře můžete poskytnout typy klienta nebo zprostředkovatele prostředků prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="c091e-198">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="c091e-199">Ukázková konfigurace pro IdentityServer4 pro použití prostředků v paměti a klientů poskytovaných vlastním typem IClientStore může vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c091e-199">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

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

### <a name="consume-security-tokens"></a><span data-ttu-id="c091e-200">Využití tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c091e-200">Consume security tokens</span></span>

<span data-ttu-id="c091e-201">Ověřování podle koncového bodu OpenID Connect nebo vydávání vlastních tokenů zabezpečení zahrnuje některé scénáře.</span><span class="sxs-lookup"><span data-stu-id="c091e-201">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="c091e-202">Ale co služba, která prostě potřebuje omezit přístup k těm uživatelům, kteří mají platné tokeny zabezpečení, které byly poskytnuty jinou službou?</span><span class="sxs-lookup"><span data-stu-id="c091e-202">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="c091e-203">Pro tento scénář je middleware ověřování, který zpracovává tokeny JWT, k dispozici v balíčku **Microsoft.AspNetCore.Authentication.JwtBearer.**</span><span class="sxs-lookup"><span data-stu-id="c091e-203">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="c091e-204">JWT je zkratka pro "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" a je společný formát tokenu zabezpečení (definovaný RFC 7519) pro komunikaci deklarací zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c091e-204">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="c091e-205">Zjednodušený příklad použití middleware ke spotřebovávat tyto tokeny může vypadat jako tento fragment kódu, převzato z Ordering.Api mikroslužby eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c091e-205">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="c091e-206">Parametry v tomto použití jsou:</span><span class="sxs-lookup"><span data-stu-id="c091e-206">The parameters in this usage are:</span></span>

- <span data-ttu-id="c091e-207">`Audience`představuje příjemce příchozí token nebo prostředek, který uděluje přístup tokenu.</span><span class="sxs-lookup"><span data-stu-id="c091e-207">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="c091e-208">Pokud hodnota zadaná v tomto parametru neodpovídá parametru v tokenu, token bude odmítnut.</span><span class="sxs-lookup"><span data-stu-id="c091e-208">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="c091e-209">`Authority`je adresa ověřovacího serveru vydávajícího tokeny.</span><span class="sxs-lookup"><span data-stu-id="c091e-209">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="c091e-210">Middleware pro ověřování nosiče JWT používá tento identifikátor URI k získání veřejného klíče, který lze použít k ověření podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="c091e-210">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="c091e-211">Middleware také potvrzuje, `iss` že parametr v tokenu odpovídá této uri.</span><span class="sxs-lookup"><span data-stu-id="c091e-211">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="c091e-212">Další parametr `RequireHttpsMetadata`, je užitečné pro účely testování; nastavíte tento parametr na hodnotu false, takže můžete testovat v prostředích, kde nemáte certifikáty.</span><span class="sxs-lookup"><span data-stu-id="c091e-212">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="c091e-213">V reálném nasazení JWT nosné tokeny by měly být vždy předány pouze přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c091e-213">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="c091e-214">S tímto middleware na místě, JWT tokeny jsou automaticky extrahovány z autorizace záhlaví.</span><span class="sxs-lookup"><span data-stu-id="c091e-214">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="c091e-215">Poté jsou deserializovány, ověřeny (pomocí `Audience` `Authority` hodnot v parametrech a) a uloženy jako informace o uživateli, na které budou později odkazovat akce MVC nebo filtry autorizace.</span><span class="sxs-lookup"><span data-stu-id="c091e-215">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="c091e-216">Middleware ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je například použití místního certifikátu k ověření tokenu, pokud autorita není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c091e-216">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="c091e-217">V tomto scénáři můžete `TokenValidationParameters` zadat `JwtBearerOptions` objekt v objektu.</span><span class="sxs-lookup"><span data-stu-id="c091e-217">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c091e-218">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c091e-218">Additional resources</span></span>

- <span data-ttu-id="c091e-219">**Sdílení souborů cookie mezi aplikacemi** </span><span class="sxs-lookup"><span data-stu-id="c091e-219">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="c091e-220">**Úvod do identity** </span><span class="sxs-lookup"><span data-stu-id="c091e-220">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="c091e-221">**Rick Anderson. Dvoufaktorové ověřování pomocí SMS** </span><span class="sxs-lookup"><span data-stu-id="c091e-221">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="c091e-222">**Povolení ověřování pomocí Facebooku, Googlu a dalších externích poskytovatelů** </span><span class="sxs-lookup"><span data-stu-id="c091e-222">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="c091e-223">**Michell Anicas. Úvod do OAuth 2** </span><span class="sxs-lookup"><span data-stu-id="c091e-223">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="c091e-224">**AspNet.Security.OAuth.Providers** (Úložiště GitHub pro ASP.NET zprostředkovatelů OAuth) </span><span class="sxs-lookup"><span data-stu-id="c091e-224">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="c091e-225">**IdentityServer4. Oficiální dokumentace** </span><span class="sxs-lookup"><span data-stu-id="c091e-225">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="c091e-226">[Předchozí](../implement-resilient-applications/monitor-app-health.md)
>[další](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="c091e-226">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
