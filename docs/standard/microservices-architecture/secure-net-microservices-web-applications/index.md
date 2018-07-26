---
title: Zabezpečení Mikroslužby .NET a webové aplikace
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Zabezpečení Mikroslužby .NET a webové aplikace
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 0e55a68432dfd44c7a73ae51512f50d481ae100c
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937030"
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="69057-103">Zabezpečení Mikroslužby .NET a webové aplikace</span><span class="sxs-lookup"><span data-stu-id="69057-103">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="69057-104">Často je nezbytné pro rozhraní API, vystavené služby omezená na určité důvěryhodnými uživateli nebo klienty a prostředky.</span><span class="sxs-lookup"><span data-stu-id="69057-104">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="69057-105">Prvním krokem při provádění těchto řadu rozhodnutí o důvěryhodnosti úroveň rozhraní API je ověřování.</span><span class="sxs-lookup"><span data-stu-id="69057-105">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="69057-106">Ověřování je proces spolehlivě zjištění identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="69057-106">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="69057-107">Ve scénářích mikroslužeb ověřování je obvykle zpracovávána centrálně.</span><span class="sxs-lookup"><span data-stu-id="69057-107">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="69057-108">Pokud používáte bránu rozhraní API, brány je vhodné místo pro ověření, jak je znázorněno v obrázku 11-1.</span><span class="sxs-lookup"><span data-stu-id="69057-108">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="69057-109">Pokud tuto metodu použijte, ujistěte se, že jednotlivých mikroslužeb není dostupný přímo (bez brány rozhraní API), není-li zvýšit zabezpečení se používají k ověření zprávy, jestli pocházejí z brány nebo ne.</span><span class="sxs-lookup"><span data-stu-id="69057-109">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="69057-110">**Obrázek 11-1**.</span><span class="sxs-lookup"><span data-stu-id="69057-110">**Figure 11-1**.</span></span> <span data-ttu-id="69057-111">Centralizované ověření pomocí brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="69057-111">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="69057-112">Pokud přímo přístupné služby, jako ověřovací služba Azure Active Directory nebo vyhrazené ověřování mikroslužby funguje jako bezpečnostní služby tokenu (STS) se dá použít k ověřování uživatelů.</span><span class="sxs-lookup"><span data-stu-id="69057-112">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="69057-113">Rozhodnutí o důvěryhodnosti jsou sdíleny mezi službami s tokeny zabezpečení nebo soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="69057-113">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="69057-114">(Tento dokument mohou sdílet mezi aplikacemi, v případě potřeby v ASP.NET Core s [služby ochrany dat](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Tento model je znázorněn v obrázku 11-2.</span><span class="sxs-lookup"><span data-stu-id="69057-114">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="69057-115">**Obrázek 11-2**.</span><span class="sxs-lookup"><span data-stu-id="69057-115">**Figure 11-2**.</span></span> <span data-ttu-id="69057-116">Ověření identity mikroslužeb; vztah důvěryhodnosti se sdílí pomocí autorizační token</span><span class="sxs-lookup"><span data-stu-id="69057-116">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="69057-117">Ověřování pomocí ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="69057-117">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="69057-118">Je primární mechanismus v ASP.NET Core pro identifikaci aplikace uživatele [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) systému členství.</span><span class="sxs-lookup"><span data-stu-id="69057-118">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="69057-119">ASP.NET Core Identity ukládá informace o uživatelském (včetně přihlašovací údaje, rolí a deklarací identity) v úložišti dat nakonfigurované vývojářem.</span><span class="sxs-lookup"><span data-stu-id="69057-119">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="69057-120">Obvykle úložiště dat ASP.NET Core Identity je zahrnutý v balíčku Microsoft.AspNetCore.Identity.EntityFrameworkCore obchod Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="69057-120">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="69057-121">Ale vlastní úložiště nebo jiné balíčky třetích stran slouží k ukládání informací o identitě v Azure Table Storage, DocumentDB nebo jiné umístění.</span><span class="sxs-lookup"><span data-stu-id="69057-121">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="69057-122">Následující kód je převzatý z šablony projektu webové aplikace ASP.NET Core ověřováním účet jednotlivého uživatele vybrali.</span><span class="sxs-lookup"><span data-stu-id="69057-122">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="69057-123">Ukazuje, jak nakonfigurovat pomocí EntityFramework.Core v metodě Startup.ConfigureServices ASP.NET Core Identity.</span><span class="sxs-lookup"><span data-stu-id="69057-123">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="69057-124">Po nakonfigurování technologie ASP.NET Core Identity povolit volání aplikace. UseIdentity v metodě Startup.Configure služby.</span><span class="sxs-lookup"><span data-stu-id="69057-124">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="69057-125">Použití ASP.NET Core Identity umožňuje několika situacích:</span><span class="sxs-lookup"><span data-stu-id="69057-125">Using ASP.NET Core Identity enables several scenarios:</span></span>

-   <span data-ttu-id="69057-126">Vytvoření nového uživatele pomocí objektu UserManager. typ (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="69057-126">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="69057-127">Ověřování uživatelů pomocí SignInManager typu.</span><span class="sxs-lookup"><span data-stu-id="69057-127">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="69057-128">SignInManager.SignInAsync můžete přihlásit přímo, nebo signInManager.PasswordSignInAsync potvrďte heslo uživatele je správný a pak přihlásí jej.</span><span class="sxs-lookup"><span data-stu-id="69057-128">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="69057-129">Identifikace uživatele na základě informací uložených v souboru cookie (který je pro čtení middlewarem ASP.NET Core Identity), tak, aby následné žádosti z prohlížeče bude obsahovat identita přihlášeného uživatele a deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="69057-129">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="69057-130">ASP.NET Core Identity podporuje také [dvojúrovňového ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="69057-130">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="69057-131">Scénáře ověřování služby, které usnadňují použití místního úložiště dat a který zachování identity mezi požadavky na používání souborů cookie (což je typické pro webové aplikace MVC), ASP.NET Core Identity je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="69057-131">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="69057-132">Ověřování pomocí externí zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="69057-132">Authenticating using external providers</span></span>

<span data-ttu-id="69057-133">ASP.NET Core také podporuje používání [externího zprostředkovatele ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/social/) umožňuje uživatelům přihlásit se přes [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) toky.</span><span class="sxs-lookup"><span data-stu-id="69057-133">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="69057-134">To znamená, že uživatelé mohou přihlásit pomocí existujících procesů ověřování od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter a přiřadit tyto identity s ASP.NET Core identity ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="69057-134">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="69057-135">Použití externího ověřování, zahrnují příslušný ověřovací middleware v kanálu zpracování požadavku HTTP vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="69057-135">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="69057-136">Tento middleware je zodpovědná za zpracování žádostí má vrátit z zprostředkovatele ověřování, zaznamenávání informací o identitě a jejich zpřístupnění prostřednictvím metody SignInManager.GetExternalLoginInfo trasy identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="69057-136">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="69057-137">Níže se zobrazují oblíbená externího zprostředkovatele ověřování a jejich přidružené balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="69057-137">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="69057-138">**Společnosti Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="69057-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="69057-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="69057-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="69057-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="69057-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="69057-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="69057-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="69057-142">Ve všech případech middleware zaregistrován pomocí volání metody registrace podobné aplikace. V Startup.Configure použijte ověřování {ExternalProvider}.</span><span class="sxs-lookup"><span data-stu-id="69057-142">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="69057-143">Tyto metody registrace trvat možnosti objekt, který obsahuje ID aplikace a tajných informací (s heslem, například), podle potřeby zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="69057-143">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="69057-144">Externí zprostředkovatelé ověřování potřeba, aby aplikace k registraci (jak je vysvětleno v [dokumentace k ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) tak, aby se může informovat uživatele jaké aplikace žádá o přístup k svoji identitu.</span><span class="sxs-lookup"><span data-stu-id="69057-144">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="69057-145">Po registraci middleware v Startup.Configure můžete vyzvat uživatele k přihlášení z jakékoli akce kontroleru.</span><span class="sxs-lookup"><span data-stu-id="69057-145">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="69057-146">K tomuto účelu vytvoříte AuthenticationProperties objekt, který obsahuje název zprostředkovatele ověřování a adresa URL přesměrování.</span><span class="sxs-lookup"><span data-stu-id="69057-146">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="69057-147">Potom vrátí odpověď na výzvu, která předá objekt AuthenticationProperties.</span><span class="sxs-lookup"><span data-stu-id="69057-147">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="69057-148">Následující kód ukazuje příklad tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="69057-148">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="69057-149">Parametr redirectUrl zahrnuje adresu URL, která by se měla přesměrovat externího poskytovatele, jakmile uživatel byl ověřen.</span><span class="sxs-lookup"><span data-stu-id="69057-149">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="69057-150">Adresa URL by měla představovat akci, která se přihlásit uživatele na základě informací o externí identity, jako v následujícím příkladu zjednodušené:</span><span class="sxs-lookup"><span data-stu-id="69057-150">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="69057-151">Pokud se rozhodnete **jednotlivé uživatelské účty** možnost ověřování při vytváření projektu kódu ASP.NET a webové aplikace v sadě Visual Studio, veškerý kód se přihlásit pomocí externího poskytovatele je už v projektu, jak je znázorněno v obrázku 11-3.</span><span class="sxs-lookup"><span data-stu-id="69057-151">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

<span data-ttu-id="69057-152">**Obrázek 11-3**.</span><span class="sxs-lookup"><span data-stu-id="69057-152">**Figure 11-3**.</span></span> <span data-ttu-id="69057-153">Vyberete možnost pro použití externího ověřování při vytváření projektu webové aplikace</span><span class="sxs-lookup"><span data-stu-id="69057-153">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="69057-154">Kromě externího ověřování poskytovatelů uvedených výše, balíčky třetích stran jsou k dispozici, které poskytují middleware pro použití mnoha další externí zprostředkovatele ověřování.</span><span class="sxs-lookup"><span data-stu-id="69057-154">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="69057-155">Seznam najdete v tématu [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="69057-155">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="69057-156">Samozřejmě je také možné, vytvořte vlastní middleware externího ověřování.</span><span class="sxs-lookup"><span data-stu-id="69057-156">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="69057-157">Ověřování pomocí nosných tokenů</span><span class="sxs-lookup"><span data-stu-id="69057-157">Authenticating with bearer tokens</span></span>

<span data-ttu-id="69057-158">Ověřování pomocí ASP.NET Core Identity (nebo identitu a externí zprostředkovatelé ověřování) funguje dobře pro řadu scénářů webové aplikace, ve kterých je vhodné ukládání informací o uživateli v souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="69057-158">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="69057-159">V jiných případech však souborů cookie nejsou přirozené prostředky uchování a přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="69057-159">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="69057-160">Například v rozhraní API pro ASP.NET Core Web, který zveřejňuje koncové body RESTful, jednostránkové aplikace (SPA), ke kterým může přistupovat nativní klienty, nebo dokonce i pomocí dalších webových rozhraní API, obvykle je vhodné místo toho použít ověřování pomocí tokenu nosiče.</span><span class="sxs-lookup"><span data-stu-id="69057-160">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="69057-161">Tyto typy aplikací není pracovat se soubory cookie, ale můžete snadno získat nosný token a zahrnout v hlavičce autorizace odeslání dalších žádostí.</span><span class="sxs-lookup"><span data-stu-id="69057-161">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="69057-162">Pokud chcete povolit ověřování pomocí tokenu, ASP.NET Core podporuje několik možností pro používání [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="69057-162">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="69057-163">Ověřování pomocí poskytovatele OpenID Connect nebo identitu OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="69057-163">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="69057-164">Pokud uživatelské informace uloženy v Azure Active Directory nebo jiném řešení identity, která podporuje OpenID Connect nebo OAuth 2.0, můžete použít balíček Microsoft.AspNetCore.Authentication.OpenIdConnect k ověření pomocí OpenID Connect. pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="69057-164">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="69057-165">Například [ověřování na základě Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), webová aplikace ASP.NET Core můžete použít middleware z tohoto balíčku, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="69057-165">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

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

<span data-ttu-id="69057-166">Konfigurační hodnoty jsou hodnoty Azure Active Directory, které vytvářejí, když je vaše aplikace [zaregistrovaný jako klient služby Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span><span class="sxs-lookup"><span data-stu-id="69057-166">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="69057-167">ID jednoho klienta je sdílet mezi různými mikroslužbami v aplikaci, pokud všechny se musí ověřovat uživatele ověřený přes Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="69057-167">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="69057-168">Všimněte si, že pokud použijete tento pracovní postup, middleware ASP.NET Core Identity není potřeba, protože jsou všechny uživatelské informace úložiště a ověření zpracovávané službou Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="69057-168">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="69057-169">Vystavování tokenů zabezpečení ze služby ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69057-169">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="69057-170">Pokud chcete vystavovat tokeny zabezpečení pro místní uživatele ASP.NET Core Identity místo pomocí externího zprostředkovatele identity, můžete využít výhod některé dobré knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="69057-170">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="69057-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) poskytovatel OpenID Connect, které lze snadno integrovat s ASP.NET Core Identity umožňuje vydávala tokeny zabezpečení ze služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="69057-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="69057-172">[IdentityServer4 dokumentaci](https://identityserver4.readthedocs.io/en/release/) obsahuje podrobné pokyny pro používání knihovny.</span><span class="sxs-lookup"><span data-stu-id="69057-172">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="69057-173">Základní postup pomocí IdentityServer4 problém tokeny jsou však následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="69057-173">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="69057-174">Volání aplikace. UseIdentityServer v metodě Startup.Configure přidat IdentityServer4 kanál zpracování požadavků HTTP vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="69057-174">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="69057-175">Díky tomu knihovny obsluhovat požadavky do koncových bodů OAuth2 jako /connect/token a OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="69057-175">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="69057-176">IdentityServer4 Startup.ConfigureServices zobrazit, je možné nakonfigurovat tak, že volání služby. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="69057-176">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="69057-177">Konfigurace identity serveru tím, že poskytuje následující data:</span><span class="sxs-lookup"><span data-stu-id="69057-177">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="69057-178">[Pověření](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) má použít pro podepisování.</span><span class="sxs-lookup"><span data-stu-id="69057-178">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="69057-179">[Identity a rozhraní API prostředky](https://identityserver4.readthedocs.io/en/release/topics/resources.html) , že uživatelé můžou žádat o přístup k:</span><span class="sxs-lookup"><span data-stu-id="69057-179">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="69057-180">Prostředky rozhraní API představují chráněných dat nebo funkce, které má uživatel přístup s přístupovým tokenem.</span><span class="sxs-lookup"><span data-stu-id="69057-180">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="69057-181">Příkladem prostředku rozhraní API může být webového rozhraní API (nebo sadu rozhraní API), který vyžaduje ověření.</span><span class="sxs-lookup"><span data-stu-id="69057-181">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="69057-182">Prostředky identity představují informace (deklarace identity), které jsou uvedeny na klienta k identifikaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="69057-182">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="69057-183">Deklarace mohou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="69057-183">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="69057-184">[Klienti](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , která se připojují k vyžádání tokeny.</span><span class="sxs-lookup"><span data-stu-id="69057-184">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="69057-185">Mechanismus úložiště pro informace o uživateli, jako například [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) nebo alternativu.</span><span class="sxs-lookup"><span data-stu-id="69057-185">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="69057-186">Když zadáte klienty a zdroje informací pro IdentityServer4 použít, můžete předat hodnota IEnumerable&lt;T&gt; kolekce příslušného typu metodám, které přebírají klienta nebo prostředků úložiště v paměti.</span><span class="sxs-lookup"><span data-stu-id="69057-186">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="69057-187">Nebo pro složitější scénáře, můžete zadat klienta nebo prostředků poskytovatele typů pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="69057-187">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="69057-188">Ukázka konfigurace pro IdentityServer4 používat prostředky v paměti a poskytuje vlastní typ IClientStore klientů může vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="69057-188">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="69057-189">Využívání tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="69057-189">Consuming security tokens</span></span>

<span data-ttu-id="69057-190">Ověřování koncového bodu OpenID Connect nebo vystavování tokenů zabezpečení řeší některé scénáře.</span><span class="sxs-lookup"><span data-stu-id="69057-190">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="69057-191">Ale co služba, která jednoduše potřebuje k omezení přístupu k těmto uživatelům, kteří mají platný zabezpečení tokeny, které byly poskytnuty jiné služby?</span><span class="sxs-lookup"><span data-stu-id="69057-191">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="69057-192">Pro tento scénář je k dispozici v balíčku Microsoft.AspNetCore.Authentication.JwtBearer ověřovací middleware, který zpracovává tokeny JWT.</span><span class="sxs-lookup"><span data-stu-id="69057-192">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="69057-193">Token JWT zastupuje "[webového tokenu JSON](https://tools.ietf.org/html/rfc7519)" a je běžný formát tokenu zabezpečení (definované RFC 7519) pro komunikaci deklarací identity zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="69057-193">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="69057-194">Jednoduchý příklad, jak používat middleware pro využívání těchto tokenů může vypadat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69057-194">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="69057-195">Tento kód musí předcházet volání s middlewarem ASP.NET Core MVC (aplikace. UseMvc).</span><span class="sxs-lookup"><span data-stu-id="69057-195">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="69057-196">Parametry v tomto použití jsou:</span><span class="sxs-lookup"><span data-stu-id="69057-196">The parameters in this usage are:</span></span>

-   <span data-ttu-id="69057-197">Cílová skupina představuje příjemce příchozím tokenu nebo tokenu uděluje přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="69057-197">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="69057-198">Hodnota zadaná v tomto parametru se neshoduje s parametrem aud v tokenu, token odmítne.</span><span class="sxs-lookup"><span data-stu-id="69057-198">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="69057-199">Autorita je adresa serveru vydání tokenu ověřování.</span><span class="sxs-lookup"><span data-stu-id="69057-199">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="69057-200">Middlewaru ověřování nosiče JWT používá tento identifikátor URI k získání veřejného klíče, který slouží k ověření podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="69057-200">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="69057-201">Middleware také potvrdí, že parametr jednotky ISS – překročené v tokenu shoduje se pomocí tohoto identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="69057-201">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="69057-202">AutomaticAuthenticate je logická hodnota, která určuje, zda uživatel definoval token, který by měl automaticky přihlášeni.</span><span class="sxs-lookup"><span data-stu-id="69057-202">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="69057-203">Dalším parametrem, RequireHttpsMetadata, se nepoužívá v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="69057-203">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="69057-204">Je vhodné pro testovací účely; Tento parametr nastavíte na hodnotu false, můžete otestovat v prostředích, kde nemáte certifikáty.</span><span class="sxs-lookup"><span data-stu-id="69057-204">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="69057-205">V nasazení reálné nosné tokeny JWT vždy předat pouze přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="69057-205">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="69057-206">Pomocí tohoto middlewaru v místě se automaticky tokeny JWT extrahují z autorizační hlavičky.</span><span class="sxs-lookup"><span data-stu-id="69057-206">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="69057-207">Jejich jsou poté deserializován, ověří (pomocí hodnot v cílové skupině a autorita parametry) a ukládá jako uživatelské informace, které se později odkazovalo akce MVC nebo filtry autorizace.</span><span class="sxs-lookup"><span data-stu-id="69057-207">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="69057-208">Middlewaru ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je třeba použití místní certifikát ověřit token, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="69057-208">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="69057-209">V tomto scénáři můžete zadat objekt parametry tokenvalidationparameters v objektu JwtBearerOptions.</span><span class="sxs-lookup"><span data-stu-id="69057-209">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="69057-210">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="69057-210">Additional resources</span></span>

-   <span data-ttu-id="69057-211">**Sdílení souborů cookie mezi aplikacemi**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="69057-211">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="69057-212">**Úvod do Identity**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="69057-212">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="69057-213">**Rick Anderson. Dvoufaktorové ověřování přes SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="69057-213">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="69057-214">**Povolení ověřování přes Facebook, Google a další externí zprostředkovatele**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="69057-214">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="69057-215">**Michell Anicas. Úvod do OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="69057-215">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="69057-216">**AspNet.Security.OAuth.Providers** (úložiště GitHub pro poskytovatelů OAuth technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="69057-216">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="69057-217">**Danny Strockis. Integrace Azure AD do webové aplikace ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="69057-217">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="69057-218">**IdentityServer4. Oficiální dokumentaci**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="69057-218">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="69057-219">[Předchozí](../implement-resilient-applications/monitor-app-health.md)
[další](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="69057-219">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
