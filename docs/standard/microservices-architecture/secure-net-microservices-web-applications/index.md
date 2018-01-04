---
title: "Zabezpečení rozhraní .NET Mikroslužeb a webových aplikací"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Zabezpečení rozhraní .NET Mikroslužeb a webových aplikací"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6281442f42b511170f83eaeb1c940a35a566e519
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="67baf-104">Zabezpečení rozhraní .NET Mikroslužeb a webových aplikací</span><span class="sxs-lookup"><span data-stu-id="67baf-104">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="67baf-105">Často je nutné pro prostředky a rozhraní API vystavené služby omezeny na určité důvěryhodných uživatelů nebo klienti.</span><span class="sxs-lookup"><span data-stu-id="67baf-105">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="67baf-106">Prvním krokem k provedení těchto nastavení neovlivní rozhodnutí týkající se rozhraní API úrovně důvěryhodnosti je ověřování.</span><span class="sxs-lookup"><span data-stu-id="67baf-106">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="67baf-107">Ověřování je proces spolehlivě zjištění identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="67baf-107">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="67baf-108">Ve scénářích mikroslužbu ověřování je obvykle zpracovávány centrálně.</span><span class="sxs-lookup"><span data-stu-id="67baf-108">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="67baf-109">Pokud používáte bránu rozhraní API, brána je vhodná k ověření, jak je znázorněno v obrázek 11-1.</span><span class="sxs-lookup"><span data-stu-id="67baf-109">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="67baf-110">Pokud tuto metodu použijte, ujistěte se, že jednotlivé mikroslužeb přímo (bez bránou rozhraní API) není dostupný, není-li zvýšit zabezpečení na místě k ověření zprávy jestli pocházejí z brány nebo ne.</span><span class="sxs-lookup"><span data-stu-id="67baf-110">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="67baf-111">**Obrázek 11-1**.</span><span class="sxs-lookup"><span data-stu-id="67baf-111">**Figure 11-1**.</span></span> <span data-ttu-id="67baf-112">Centralizované ověřování s bránu rozhraní API</span><span class="sxs-lookup"><span data-stu-id="67baf-112">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="67baf-113">Je-li služby je přístupná přímo, jako ověřovací služba Azure Active Directory nebo vyhrazené ověřování mikroslužby, který funguje jako zabezpečení služby tokenů (STS) lze použít k ověřování uživatelů.</span><span class="sxs-lookup"><span data-stu-id="67baf-113">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="67baf-114">Rozhodnutí o důvěryhodnosti jsou sdíleny mezi službami s tokeny zabezpečení nebo soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="67baf-114">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="67baf-115">(To je možné sdílet mezi aplikacemi, v případě potřeby v ASP.NET Core s [služby ochrany dat](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Tento vzor je zobrazená v obrázek 11-2.</span><span class="sxs-lookup"><span data-stu-id="67baf-115">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="67baf-116">**Obrázek 11-2**.</span><span class="sxs-lookup"><span data-stu-id="67baf-116">**Figure 11-2**.</span></span> <span data-ttu-id="67baf-117">Ověřování pomocí identity mikroslužbu; vztah důvěryhodnosti se sdílí pomocí autorizační token</span><span class="sxs-lookup"><span data-stu-id="67baf-117">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="67baf-118">Ověřování pomocí ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="67baf-118">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="67baf-119">Primární mechanismus v ASP.NET Core identifikace uživatelů aplikace je [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) systému členství.</span><span class="sxs-lookup"><span data-stu-id="67baf-119">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="67baf-120">Identitu ASP.NET Core uchovává informace o uživateli (včetně přihlašovací údaje, rolí a deklarací identity) v úložišti dat konfigurovat tak, že vývojář.</span><span class="sxs-lookup"><span data-stu-id="67baf-120">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="67baf-121">Úložiště dat ASP.NET Core Identity je obvykle úložišti Entity Framework, který je zahrnutý v balíčku Microsoft.AspNetCore.Identity.EntityFrameworkCore.</span><span class="sxs-lookup"><span data-stu-id="67baf-121">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="67baf-122">Ale vlastního úložiště nebo jiné balíčky třetích stran slouží k ukládání informací o identitě Azure Table Storage, DocumentDB nebo jiné umístění.</span><span class="sxs-lookup"><span data-stu-id="67baf-122">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="67baf-123">Následující kód je převzat ze šablony projektu webové aplikace ASP.NET Core s ověřováním účtu jednotlivé uživatele vybrali.</span><span class="sxs-lookup"><span data-stu-id="67baf-123">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="67baf-124">Ukazuje, jak nakonfigurovat ASP.NET Identity Core pomocí EntityFramework.Core v metodě Startup.ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="67baf-124">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="67baf-125">Po nakonfigurování ASP.NET Core Identity povolit volání aplikace. UseIdentity v metodě Startup.Configure služby.</span><span class="sxs-lookup"><span data-stu-id="67baf-125">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="67baf-126">Pomocí Identity kódu ASP.NET umožňuje několika scénářích:</span><span class="sxs-lookup"><span data-stu-id="67baf-126">Using ASP.NET Code Identity enables several scenarios:</span></span>

-   <span data-ttu-id="67baf-127">Vytvořte nové informace o uživateli pomocí typu objekt UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="67baf-127">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="67baf-128">Ověřování uživatelů pomocí SignInManager typu.</span><span class="sxs-lookup"><span data-stu-id="67baf-128">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="67baf-129">SignInManager.SignInAsync můžete použít k přihlášení přímo, nebo signInManager.PasswordSignInAsync k potvrzení hesla je správný a potom se přihlaste je.</span><span class="sxs-lookup"><span data-stu-id="67baf-129">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="67baf-130">Identifikace uživatele na základě informací v souborech cookie (což je pro čtení middlewarem ASP.NET Core Identity) tak, aby následné žádosti z prohlížeč bude obsahovat identita přihlášeného uživatele a deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="67baf-130">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="67baf-131">Také podporuje ASP.NET Core Identity [dvoufaktorové ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="67baf-131">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="67baf-132">Pro scénáře ověřování, které využívají úložiště dat, které místní uživatele a které ukládají identity mezi požadavky pomocí souborů cookie (jako je typický pro webové aplikace MVC), ASP.NET Core Identity je doporučená řešení.</span><span class="sxs-lookup"><span data-stu-id="67baf-132">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="67baf-133">Ověřování pomocí externího zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="67baf-133">Authenticating using external providers</span></span>

<span data-ttu-id="67baf-134">ASP.NET Core také podporuje používání [externí zprostředkovatelé ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/social/) tak, aby uživatelé přihlásit pomocí [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) toky.</span><span class="sxs-lookup"><span data-stu-id="67baf-134">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="67baf-135">To znamená, že uživatelé můžete přihlásit pomocí stávající ověřovací procesy od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter a přidružit tyto identity ASP.NET Core identity ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="67baf-135">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="67baf-136">Chcete-li použít externího ověřování, obsahovat příslušný ověřovací middleware v kanálu zpracování požadavku HTTP vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="67baf-136">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="67baf-137">Tento middleware je zodpovědná za zpracování žádostí se vrátí identifikátor URI trasy ze zprostředkovatele ověřování, zaznamenávání informací o identitě a zpřístupnění prostřednictvím metody SignInManager.GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="67baf-137">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="67baf-138">Níže jsou uvedeny oblíbených externí zprostředkovatelé ověřování a jejich přidružené balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="67baf-138">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="67baf-139">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="67baf-139">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="67baf-140">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="67baf-140">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="67baf-141">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="67baf-141">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="67baf-142">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="67baf-142">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="67baf-143">Ve všech případech middleware není zaregistrována volání metody registrace podobné aplikace. V Startup.Configure používejte ověřování {ExternalProvider}.</span><span class="sxs-lookup"><span data-stu-id="67baf-143">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="67baf-144">Tyto metody registrace trvat možnosti objekt, který obsahuje ID aplikace a tajné informace (heslo, například), podle potřeby zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="67baf-144">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="67baf-145">Externí zprostředkovatelé ověřování vyžadovat pro zaregistrovat (jak je popsáno v [ASP.NET Core dokumentaci](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) tak, aby se může informovat uživatele co aplikace požaduje přístup k svou identitu.</span><span class="sxs-lookup"><span data-stu-id="67baf-145">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="67baf-146">Jakmile middleware je zaregistrován v Startup.Configure, můžete vyzvat uživatele k přihlášení z jakékoli akce kontroleru.</span><span class="sxs-lookup"><span data-stu-id="67baf-146">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="67baf-147">K tomuto účelu vytvořte AuthenticationProperties objekt, který obsahuje název zprostředkovatele ověřování a adresu URL pro přesměrování.</span><span class="sxs-lookup"><span data-stu-id="67baf-147">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="67baf-148">Odpověď na výzvu, která předá objekt AuthenticationProperties vrátíte.</span><span class="sxs-lookup"><span data-stu-id="67baf-148">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="67baf-149">Následující kód ukazuje příklad tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="67baf-149">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="67baf-150">Parametr redirectUrl obsahuje adresu URL, která by se měla přesměrovat externího poskytovatele, jakmile se uživatel byl ověřen.</span><span class="sxs-lookup"><span data-stu-id="67baf-150">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="67baf-151">Adresa URL by měla představovat akci, která budou uživatele přihlásit na základě informací o externí identity, jako v následujícím příkladu zjednodušené:</span><span class="sxs-lookup"><span data-stu-id="67baf-151">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

<span data-ttu-id="67baf-152">Pokud se rozhodnete **individuální uživatelský účet** možnost ověřování při vytváření projektu webové aplikace ASP.NET kód v sadě Visual Studio, kód nutné se přihlásit pomocí externího poskytovatele je již v projektu, jak je znázorněno 11 obrázek-3.</span><span class="sxs-lookup"><span data-stu-id="67baf-152">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.BLOB.Core.Windows.NET/Media/2016/10/New-Web-App.PNG](./media/image3.png)

<span data-ttu-id="67baf-154">**Obrázek 11-3**.</span><span class="sxs-lookup"><span data-stu-id="67baf-154">**Figure 11-3**.</span></span> <span data-ttu-id="67baf-155">Vyberete možnost použití externího ověřování, při vytváření projektu webové aplikace</span><span class="sxs-lookup"><span data-stu-id="67baf-155">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="67baf-156">Kromě externího ověřování, zprostředkovatelé uvedených výše, balíčky jiných výrobců jsou k dispozici, které poskytují middleware pro použití mnoha více externí zprostředkovatele ověřování.</span><span class="sxs-lookup"><span data-stu-id="67baf-156">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="67baf-157">Seznam najdete v tématu [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="67baf-157">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="67baf-158">Samozřejmě, je také možné, vytvořte vlastní middleware externího ověřování.</span><span class="sxs-lookup"><span data-stu-id="67baf-158">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="67baf-159">Ověřování pomocí nosných tokenů</span><span class="sxs-lookup"><span data-stu-id="67baf-159">Authenticating with bearer tokens</span></span>

<span data-ttu-id="67baf-160">Ověřování pomocí ASP.NET Core Identity (nebo identitu a externí zprostředkovatelé ověřování) funguje dobře pro mnoho scénářů webové aplikace, ve kterých je vhodné ukládání informací o uživateli v souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="67baf-160">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="67baf-161">V dalších scénářích ale soubory cookie nejsou fyzické prostředky k uchování a přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="67baf-161">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="67baf-162">Například pro ASP.NET Web API Core RESTful koncových bodů, které může získat přístup k jednostránkové aplikace (SPA), která zveřejňuje nativní klienty, nebo i pomocí dalších webových rozhraní API, obvykle je vhodné místo toho použít ověřování tokenu nosiče.</span><span class="sxs-lookup"><span data-stu-id="67baf-162">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="67baf-163">Tyto aplikace není pracovat se soubory cookie, ale můžete snadno získat token nosiče a její zahrnutí do hlavičce autorizace následných žádostí.</span><span class="sxs-lookup"><span data-stu-id="67baf-163">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="67baf-164">Pokud chcete povolit ověřování tokenem, ASP.NET Core podporuje několik možností pro používání [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](http://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="67baf-164">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](http://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="67baf-165">Ověřování pomocí zprostředkovatele OpenID Connect nebo identitu OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="67baf-165">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="67baf-166">Pokud uživatelské informace uloženy v Azure Active Directory nebo jiné řešení identity, který podporuje OpenID Connect nebo OAuth 2.0, můžete použít balíček Microsoft.AspNetCore.Authentication.OpenIdConnect ověřování pomocí pracovního postupu OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="67baf-166">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="67baf-167">Například pro [ověřování na základě Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), webovou aplikaci ASP.NET Core můžete použít middleware z tohoto balíčku, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="67baf-167">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

```csharp
// Configure the OWIN pipeline to use OpenID Connect auth
app.UseOpenIdConnectAuthentication(new OpenIdConnectOptions
{
    ClientId = Configuration["AzureAD:ClientId"],
    Authority = String.Format(Configuration["AzureAd:AadInstance"],
    Configuration["AzureAd:Tenant"]),
    ResponseType = OpenIdConnectResponseType.IdToken,
    PostLogoutRedirectUri = Configuration["AzureAd:PostLogoutRedirectUri"]
});
```

<span data-ttu-id="67baf-168">Hodnoty konfigurace jsou hodnoty Azure Active Directory, které vytvářejí, když je aplikace [registrován jako klient Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span><span class="sxs-lookup"><span data-stu-id="67baf-168">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="67baf-169">ID jednoho klienta může být sdílen více mikroslužeb v aplikaci pokud všechny potřebují k ověřování uživatelů, ověření přes Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="67baf-169">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="67baf-170">Všimněte si, že pokud použijete tento pracovní postup, middleware ASP.NET Core Identity není nutné, protože zajišťuje všechny informace úložiště uživatele a ověřování přes Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="67baf-170">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="67baf-171">Vystavování tokenů zabezpečení ze služby ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="67baf-171">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="67baf-172">Pokud dáváte přednost vystavovat tokeny zabezpečení pro místní uživatele ASP.NET Core Identity místo pomocí zprostředkovatele externí identity, můžete využít některé funkční knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="67baf-172">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="67baf-173">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) poskytovatelé OpenID Connect, které se integrují s ASP.NET Identity Core k vám umožní snadno vydávala tokeny zabezpečení ze služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67baf-173">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="67baf-174">[IdentityServer4 dokumentace](https://identityserver4.readthedocs.io/en/release/) obsahuje podrobné pokyny pro používání knihovny.</span><span class="sxs-lookup"><span data-stu-id="67baf-174">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="67baf-175">Základní postup pomocí IdentityServer4 problém tokeny jsou však následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="67baf-175">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="67baf-176">Volání aplikace. UseIdentityServer v metodě Startup.Configure přidání IdentityServer4 do kanálu zpracování žádostí HTTP aplikace.</span><span class="sxs-lookup"><span data-stu-id="67baf-176">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="67baf-177">To umožňuje knihovně obsluhovat požadavky na koncové body OAuth2 jako /connect/token a OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="67baf-177">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="67baf-178">Nakonfigurujete IdentityServer4 v Startup.ConfigureServices tím, že zavoláte na služby. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="67baf-178">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="67baf-179">Nakonfigurujete identity server tím, že poskytuje následující data:</span><span class="sxs-lookup"><span data-stu-id="67baf-179">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="67baf-180">[Pověření](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) má použít pro podepisování.</span><span class="sxs-lookup"><span data-stu-id="67baf-180">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="67baf-181">[Identity a rozhraní API prostředky](https://identityserver4.readthedocs.io/en/release/topics/resources.html) , uživatelé si mohou vyžádat přístup k:</span><span class="sxs-lookup"><span data-stu-id="67baf-181">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="67baf-182">Rozhraní API prostředky představují chráněných dat nebo funkce, které může uživatel získat přístup k tokenu přístupu.</span><span class="sxs-lookup"><span data-stu-id="67baf-182">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="67baf-183">Příkladem prostředku, který rozhraní API může být webového rozhraní API (nebo sadu rozhraní API), vyžaduje ověření.</span><span class="sxs-lookup"><span data-stu-id="67baf-183">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="67baf-184">Identity prostředky představují informace (deklarace identity), které jsou uvedeny na klienta k identifikaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="67baf-184">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="67baf-185">Deklarace identity může zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="67baf-185">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="67baf-186">[Klienti](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , budou připojovat k žádosti o tokeny.</span><span class="sxs-lookup"><span data-stu-id="67baf-186">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="67baf-187">Mechanismus úložiště pro informace o uživateli, jako například [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) nebo alternativu.</span><span class="sxs-lookup"><span data-stu-id="67baf-187">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="67baf-188">Když zadáte klientů a prostředky pro IdentityServer4 na používání, abyste mohli předávat použití rozhraní IEnumerable&lt;T&gt; kolekce příslušného typu do metod, které berou v paměti klienta nebo prostředků úložiště.</span><span class="sxs-lookup"><span data-stu-id="67baf-188">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="67baf-189">Nebo pro složitějšími scénáři, můžete zadat klienta nebo prostředek typy zprostředkovatele pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="67baf-189">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="67baf-190">Ukázková konfigurace pro IdentityServer4 používat prostředky v paměti a klienti poskytované vlastního typu IClientStore může vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="67baf-190">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="67baf-191">Použití tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67baf-191">Consuming security tokens</span></span>

<span data-ttu-id="67baf-192">Ověřování proti koncový bod OpenID Connect nebo vystavením vlastní tokeny zabezpečení obsahuje některé scénáře.</span><span class="sxs-lookup"><span data-stu-id="67baf-192">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="67baf-193">Ale co o službu, která jednoduše omezit přístup na uživatele, kteří mají platný zabezpečení tokeny, které byly poskytovaný jinou službu?</span><span class="sxs-lookup"><span data-stu-id="67baf-193">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="67baf-194">Pro tento scénář je k dispozici v balíčku Microsoft.AspNetCore.Authentication.JwtBearer middleware ověřování, která zpracovává tokeny JWT.</span><span class="sxs-lookup"><span data-stu-id="67baf-194">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="67baf-195">JWT znamená "[webových tokenů JSON](https://tools.ietf.org/html/rfc7519)" a je formát common token zabezpečení (definované RFC 7519) pro komunikaci deklarací identity zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67baf-195">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="67baf-196">Jednoduchý příklad toho, jak používat tyto tokeny pomocí middlewaru může vypadat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="67baf-196">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="67baf-197">Tento kód musí předcházet volání middleware ASP.NET Core MVC (aplikace. UseMvc).</span><span class="sxs-lookup"><span data-stu-id="67baf-197">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="67baf-198">Parametry v toto použití jsou:</span><span class="sxs-lookup"><span data-stu-id="67baf-198">The parameters in this usage are:</span></span>

-   <span data-ttu-id="67baf-199">Cílová skupina představuje příchozím tokenu nebo prostředek, který token uděluje přístup k příjemce.</span><span class="sxs-lookup"><span data-stu-id="67baf-199">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="67baf-200">Pokud je hodnota zadaná v tomto parametru neodpovídá parametr oblast v tokenu, budou odmítnuty token.</span><span class="sxs-lookup"><span data-stu-id="67baf-200">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="67baf-201">Autorita je adresa serveru vydání tokenu ověřování.</span><span class="sxs-lookup"><span data-stu-id="67baf-201">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="67baf-202">Middlewaru ověřování nosiče JWT používá tento identifikátor URI k získání veřejný klíč, který slouží k ověření podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="67baf-202">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="67baf-203">Middleware také potvrdí, že parametr iss v tokenu odpovídá tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="67baf-203">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="67baf-204">AutomaticAuthenticate je logická hodnota, která označuje, zda uživatel definované token by měl být automaticky přihlášeni.</span><span class="sxs-lookup"><span data-stu-id="67baf-204">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="67baf-205">Jiný parametr, RequireHttpsMetadata, se nepoužívá v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="67baf-205">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="67baf-206">Je vhodné pro testovací účely; Tento parametr nastavíte na hodnotu false, mohli otestovat v prostředích kde nemáte certifikáty.</span><span class="sxs-lookup"><span data-stu-id="67baf-206">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="67baf-207">Skutečné nasazení by měl nosné tokeny JWT předat vždy pouze prostřednictvím protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="67baf-207">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="67baf-208">Pomocí tohoto middlewaru v místě tokeny JWT automaticky se extrahují z hlavičky ověření.</span><span class="sxs-lookup"><span data-stu-id="67baf-208">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="67baf-209">Jejich jsou poté deserializován, ověřit (pomocí hodnot v parametrech cílovou skupinu a autorita) a ukládají jako informace o uživateli bude odkazovat později akce MVC nebo filtry autorizace.</span><span class="sxs-lookup"><span data-stu-id="67baf-209">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="67baf-210">Middlewaru ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je třeba použití místní certifikát ověřit token, pokud není k dispozici pro autoritu.</span><span class="sxs-lookup"><span data-stu-id="67baf-210">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="67baf-211">V tomto scénáři můžete parametry tokenvalidationparameters objekt v objektu JwtBearerOptions.</span><span class="sxs-lookup"><span data-stu-id="67baf-211">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="67baf-212">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="67baf-212">Additional resources</span></span>

-   <span data-ttu-id="67baf-213">**Sdílení souborů cookie mezi aplikacemi**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\# sdílení – ověřování – soubory cookie mezi – aplikace*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="67baf-213">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="67baf-214">**Úvod do Identity**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="67baf-214">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="67baf-215">**Rick Anderson. Dvoufaktorové ověřování pomocí SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="67baf-215">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="67baf-216">**Povolení ověřování pomocí služby Facebook, Google a dalších externích zprostředkovatelů**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="67baf-216">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="67baf-217">**Michell Anicas. Úvod do OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="67baf-217">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="67baf-218">**AspNet.Security.OAuth.Providers** (úložiště GitHub zprostředkovatelů ASP.NET OAuth.</span><span class="sxs-lookup"><span data-stu-id="67baf-218">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [<span data-ttu-id="67baf-219">*https://github.com/ASPNET-contrib/ASPNET.Security.OAuth.Providers/Tree/dev/src*</span><span class="sxs-lookup"><span data-stu-id="67baf-219">*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*</span></span>](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="67baf-220">**Danny Strockis. Integrace Azure AD do webové aplikace ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="67baf-220">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="67baf-221">**IdentityServer4. Oficiální dokumentaci**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="67baf-221">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="67baf-222">[Předchozí] (.. /Implement-resilient-Applications/monitor-App-Health.MD) [Další] (autorizace net mikroslužeb web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="67baf-222">[Previous] (../implement-resilient-applications/monitor-app-health.md) [Next] (authorization-net-microservices-web-applications.md)</span></span>
