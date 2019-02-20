---
title: Zabezpečení Mikroslužby .NET a webové aplikace
description: Zabezpečení v rozhraní .NET Mikroslužeb a webových aplikací – seznámení s možností ověřování webové aplikace ASP.NET Core.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="eb984-103">Zabezpečení Mikroslužby .NET a webové aplikace</span><span class="sxs-lookup"><span data-stu-id="eb984-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="eb984-104">Existuje mnoho aspektů zabezpečení v mikroslužbách a webových aplikacích, tématu snadné trvat několik knihy podobný následujícímu tak v této části se zaměříme na ověřování, autorizaci a tajných klíčů aplikací.</span><span class="sxs-lookup"><span data-stu-id="eb984-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="eb984-105">Implementace ověřování v mikroslužbách a webových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="eb984-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="eb984-106">Často je nezbytné pro prostředky a rozhraní API publikovat službou omezená na určité důvěryhodnými uživateli nebo klienti.</span><span class="sxs-lookup"><span data-stu-id="eb984-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="eb984-107">Prvním krokem při provádění těchto řadu rozhodnutí o důvěryhodnosti úroveň rozhraní API je ověřování.</span><span class="sxs-lookup"><span data-stu-id="eb984-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="eb984-108">Ověřování je proces spolehlivě ověřit identitu uživatele.</span><span class="sxs-lookup"><span data-stu-id="eb984-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="eb984-109">Ve scénářích mikroslužeb ověřování je obvykle zpracovávána centrálně.</span><span class="sxs-lookup"><span data-stu-id="eb984-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="eb984-110">Pokud používáte bránu rozhraní API, brány je vhodné místo pro ověření, jak je znázorněno v obrázek 9-1.</span><span class="sxs-lookup"><span data-stu-id="eb984-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="eb984-111">Pokud tuto metodu použijte, ujistěte se, že jednotlivých mikroslužeb není dostupný přímo (bez brány rozhraní API), není-li zvýšit zabezpečení se používají k ověření zprávy, jestli pocházejí z brány nebo ne.</span><span class="sxs-lookup"><span data-stu-id="eb984-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Pokud brána rozhraní API centralizuje ověřování, přidá informace o uživateli, když předává požadavky do mikroslužeb.](./media/image1.png)

<span data-ttu-id="eb984-113">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="eb984-113">**Figure 9-1**.</span></span> <span data-ttu-id="eb984-114">Centralizované ověření pomocí brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eb984-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="eb984-115">Pokud přímo přístupné služby, jako ověřovací služba Azure Active Directory nebo vyhrazené ověřování mikroslužby funguje jako bezpečnostní služby tokenu (STS) se dá použít k ověřování uživatelů.</span><span class="sxs-lookup"><span data-stu-id="eb984-115">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="eb984-116">Rozhodnutí o důvěryhodnosti jsou sdíleny mezi službami s tokeny zabezpečení nebo soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="eb984-116">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="eb984-117">(Tyto tokeny je možné sdílet mezi aplikacemi, v případě potřeby v ASP.NET Core s [služby ochrany dat](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Tento model je znázorněn v obrázek 9-2.</span><span class="sxs-lookup"><span data-stu-id="eb984-117">(These tokens can be shared between applications, if needed, in ASP.NET Core with [data protection services](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 9-2.</span></span>

![Když mikroslužeb jsou přímo přístupné, vztah důvěryhodnosti, který zahrnuje ověřování a autorizace, zařizuje služba tokenu zabezpečení vydaného službou vyhrazené mikroslužeb, sdílené mezi mikroslužbami.](./media/image2.png)

<span data-ttu-id="eb984-119">**Obrázek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="eb984-119">**Figure 9-2**.</span></span> <span data-ttu-id="eb984-120">Ověření identity mikroslužeb; vztah důvěryhodnosti se sdílí pomocí autorizační token</span><span class="sxs-lookup"><span data-stu-id="eb984-120">Authentication by identity microservice; trust is shared using an authorization token</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="eb984-121">Ověřování pomocí ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="eb984-121">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="eb984-122">Je primární mechanismus v ASP.NET Core pro identifikaci aplikace uživatele [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) systému členství.</span><span class="sxs-lookup"><span data-stu-id="eb984-122">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="eb984-123">ASP.NET Core Identity ukládá informace o uživatelském (včetně přihlašovací údaje, rolí a deklarací identity) v úložišti dat nakonfigurované vývojářem.</span><span class="sxs-lookup"><span data-stu-id="eb984-123">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="eb984-124">Rozhraní Entity Framework úložiště k dispozici v úložišti dat ASP.NET Core Identity je obvykle `Microsoft.AspNetCore.Identity.EntityFrameworkCore` balíčku.</span><span class="sxs-lookup"><span data-stu-id="eb984-124">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="eb984-125">Ale vlastní úložiště nebo jiné balíčky třetích stran slouží k ukládání informací o identitě v Azure Table Storage, služby cosmos DB nebo jiné umístění.</span><span class="sxs-lookup"><span data-stu-id="eb984-125">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="eb984-126">Následující kód je převzatý z šablony projektu webové aplikace ASP.NET Core ověřováním účet jednotlivého uživatele vybrali.</span><span class="sxs-lookup"><span data-stu-id="eb984-126">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="eb984-127">Ukazuje, jak nakonfigurovat pomocí EntityFramework.Core v metodě Startup.ConfigureServices ASP.NET Core Identity.</span><span class="sxs-lookup"><span data-stu-id="eb984-127">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="eb984-128">Po nakonfigurování technologie ASP.NET Core Identity povolit volání aplikace. UseIdentity ve vaší službě `Startup.Configure` metody.</span><span class="sxs-lookup"><span data-stu-id="eb984-128">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="eb984-129">Použití ASP.NET Core Identity umožňuje několika situacích:</span><span class="sxs-lookup"><span data-stu-id="eb984-129">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="eb984-130">Vytvoření nového uživatele pomocí objektu UserManager. typ (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="eb984-130">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="eb984-131">Ověřování uživatelů pomocí SignInManager typu.</span><span class="sxs-lookup"><span data-stu-id="eb984-131">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="eb984-132">Můžete použít `signInManager.SignInAsync` přihlásit přímo, nebo `signInManager.PasswordSignInAsync` a potvrďte je zadáno správné heslo uživatele a pak přihlásí jej.</span><span class="sxs-lookup"><span data-stu-id="eb984-132">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="eb984-133">Identifikace uživatele na základě informací uložených v souboru cookie (který je pro čtení middlewarem ASP.NET Core Identity), tak, aby následné žádosti z prohlížeče bude obsahovat identita přihlášeného uživatele a deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="eb984-133">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="eb984-134">ASP.NET Core Identity podporuje také [dvojúrovňového ověřování](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="eb984-134">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="eb984-135">Scénáře ověřování služby, které usnadňují použití místního úložiště dat a který zachování identity mezi požadavky na používání souborů cookie (což je typické pro webové aplikace MVC), ASP.NET Core Identity je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="eb984-135">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="eb984-136">Ověřování pomocí externí zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="eb984-136">Authenticate with external providers</span></span>

<span data-ttu-id="eb984-137">ASP.NET Core také podporuje používání [externího zprostředkovatele ověřování](/aspnet/core/security/authentication/social/) umožníte uživatelům přihlašovat se prostřednictvím [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) toky.</span><span class="sxs-lookup"><span data-stu-id="eb984-137">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="eb984-138">To znamená, že uživatelé mohou přihlásit pomocí existujících procesů ověřování od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter a přiřadit tyto identity s ASP.NET Core identity ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eb984-138">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="eb984-139">Použití externího ověřování, zahrnují příslušný ověřovací middleware v kanálu zpracování požadavku HTTP vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb984-139">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="eb984-140">Tento middleware je zodpovědná za zpracování žádostí má vrátit z zprostředkovatele ověřování, zaznamenávání informací o identitě a jejich zpřístupnění prostřednictvím metody SignInManager.GetExternalLoginInfo trasy identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="eb984-140">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="eb984-141">Oblíbené externího zprostředkovatele ověřování a jejich přidružené balíčky NuGet jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="eb984-141">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="eb984-142">**Poskytovatel**</span><span class="sxs-lookup"><span data-stu-id="eb984-142">**Provider**</span></span>  | <span data-ttu-id="eb984-143">**Balíček**</span><span class="sxs-lookup"><span data-stu-id="eb984-143">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="eb984-144">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="eb984-144">**Microsoft**</span></span> | <span data-ttu-id="eb984-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="eb984-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="eb984-146">**Google**</span><span class="sxs-lookup"><span data-stu-id="eb984-146">**Google**</span></span>    | <span data-ttu-id="eb984-147">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="eb984-147">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="eb984-148">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="eb984-148">**Facebook**</span></span>  | <span data-ttu-id="eb984-149">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="eb984-149">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="eb984-150">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="eb984-150">**Twitter**</span></span>   | <span data-ttu-id="eb984-151">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="eb984-151">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="eb984-152">Ve všech případech, middleware zaregistrován pomocí volání metody registrace podobné `app.Use{ExternalProvider}Authentication` v `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="eb984-152">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="eb984-153">Tyto metody registrace trvat možnosti objekt, který obsahuje ID aplikace a tajných informací (s heslem, například), podle potřeby zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="eb984-153">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="eb984-154">Externí zprostředkovatelé ověřování potřeba, aby aplikace k registraci (jak je vysvětleno v [dokumentace k ASP.NET Core](/aspnet/core/security/authentication/social/)) tak, aby se může informovat uživatele jaké aplikace žádá o přístup k svoji identitu.</span><span class="sxs-lookup"><span data-stu-id="eb984-154">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="eb984-155">Jakmile middlewaru je registrovaný v `Startup.Configure`, můžete vyzvat uživatele k přihlášení z jakékoli akce kontroleru.</span><span class="sxs-lookup"><span data-stu-id="eb984-155">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="eb984-156">K tomuto účelu vytvoříte `AuthenticationProperties` objekt, který obsahuje název zprostředkovatele ověřování a adresa URL přesměrování.</span><span class="sxs-lookup"><span data-stu-id="eb984-156">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="eb984-157">Potom vrátit odpověď na výzvu, který předá `AuthenticationProperties` objektu.</span><span class="sxs-lookup"><span data-stu-id="eb984-157">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="eb984-158">Následující kód ukazuje příklad tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="eb984-158">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="eb984-159">Parametr redirectUrl zahrnuje adresu URL, která by se měla přesměrovat externího poskytovatele, jakmile uživatel byl ověřen.</span><span class="sxs-lookup"><span data-stu-id="eb984-159">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="eb984-160">Adresa URL by měla představovat akci, která se přihlásit uživatele na základě informací o externí identity, jako v následujícím příkladu zjednodušené:</span><span class="sxs-lookup"><span data-stu-id="eb984-160">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="eb984-161">Pokud se rozhodnete **jednotlivé uživatelské účty** možnost ověřování při vytváření projektu kódu ASP.NET a webové aplikace v sadě Visual Studio, veškerý kód se přihlásit pomocí externího poskytovatele je už v projektu, jak je znázorněno v obrázku 9-3.</span><span class="sxs-lookup"><span data-stu-id="eb984-161">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Dialogové okno pro nová webová aplikace ASP.NET Core, zvýraznění na tlačítko Změnit ověřování.](./media/image3.png)

<span data-ttu-id="eb984-163">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="eb984-163">**Figure 9-3**.</span></span> <span data-ttu-id="eb984-164">Vyberete možnost pro použití externího ověřování při vytváření projektu webové aplikace</span><span class="sxs-lookup"><span data-stu-id="eb984-164">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="eb984-165">Kromě externího ověřování poskytovatelů uvedených výše, balíčky třetích stran jsou k dispozici, které poskytují middleware pro použití mnoha další externí zprostředkovatele ověřování.</span><span class="sxs-lookup"><span data-stu-id="eb984-165">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="eb984-166">Seznam najdete v tématu [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="eb984-166">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="eb984-167">Můžete také vytvořit vlastní externí ověřovací middleware vyřešit některé zvláštní potřebu.</span><span class="sxs-lookup"><span data-stu-id="eb984-167">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="eb984-168">Ověřování pomocí nosných tokenů</span><span class="sxs-lookup"><span data-stu-id="eb984-168">Authenticate with bearer tokens</span></span>

<span data-ttu-id="eb984-169">Ověřování pomocí ASP.NET Core Identity (nebo identitu a externí zprostředkovatelé ověřování) funguje dobře pro řadu scénářů webové aplikace, ve kterých je vhodné ukládání informací o uživateli v souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="eb984-169">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="eb984-170">V jiných případech však souborů cookie nejsou přirozené prostředky uchování a přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="eb984-170">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="eb984-171">Například v rozhraní API pro ASP.NET Core Web, který zveřejňuje koncové body RESTful, jednostránkové aplikace (SPA), ke kterým může přistupovat nativní klienty, nebo dokonce i pomocí dalších webových rozhraní API, obvykle je vhodné místo toho použít ověřování pomocí tokenu nosiče.</span><span class="sxs-lookup"><span data-stu-id="eb984-171">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="eb984-172">Tyto typy aplikací není pracovat se soubory cookie, ale můžete snadno získat nosný token a zahrnout v hlavičce autorizace odeslání dalších žádostí.</span><span class="sxs-lookup"><span data-stu-id="eb984-172">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="eb984-173">Pokud chcete povolit ověřování pomocí tokenu, ASP.NET Core podporuje několik možností pro používání [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="eb984-173">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="eb984-174">Ověřování pomocí poskytovatele OpenID Connect nebo identitu OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="eb984-174">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="eb984-175">Pokud uživatelské informace uloženy v Azure Active Directory nebo jiném řešení identity, která podporuje OpenID Connect nebo OAuth 2.0, můžete použít **Microsoft.AspNetCore.Authentication.OpenIdConnect** balíčku provést ověření pomocí pracovní postup OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="eb984-175">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="eb984-176">Například k ověření Identity.Api mikroslužeb v aplikaci eShopOnContainers, webová aplikace ASP.NET Core můžete použít middleware z tohoto balíčku jak je znázorněno v následující zjednodušený příklad v `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="eb984-176">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie()
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl;
        options.SignedOutRedirectUri = callBackUrl;
        options.ClientSecret = "secret";
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

<span data-ttu-id="eb984-177">Všimněte si, že pokud použijete tento pracovní postup, middleware ASP.NET Core Identity není potřeba, vzhledem k tomu, že všechny informace úložiště uživatele a ověření se zpracovává souborem Identity služby.</span><span class="sxs-lookup"><span data-stu-id="eb984-177">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="eb984-178">Vystavovat tokeny zabezpečení ze služby ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eb984-178">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="eb984-179">Pokud chcete vystavovat tokeny zabezpečení pro místní uživatele ASP.NET Core Identity místo pomocí externího zprostředkovatele identity, můžete využít výhod některé dobré knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="eb984-179">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="eb984-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) poskytovatel OpenID Connect, které lze snadno integrovat s ASP.NET Core Identity umožňuje vydávala tokeny zabezpečení ze služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb984-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="eb984-181">[IdentityServer4 dokumentaci](https://identityserver4.readthedocs.io/en/latest/) obsahuje podrobné pokyny pro používání knihovny.</span><span class="sxs-lookup"><span data-stu-id="eb984-181">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="eb984-182">Základní postup pomocí IdentityServer4 problém tokeny jsou však následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="eb984-182">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="eb984-183">Volání aplikace. UseIdentityServer v metodě Startup.Configure přidat IdentityServer4 kanál zpracování požadavků HTTP vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb984-183">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="eb984-184">Díky tomu knihovny obsluhovat požadavky do koncových bodů OAuth2 jako /connect/token a OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="eb984-184">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="eb984-185">IdentityServer4 Startup.ConfigureServices zobrazit, je možné nakonfigurovat tak, že volání služby. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="eb984-185">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="eb984-186">Konfigurace identity serveru tak, že nastavíte následující data:</span><span class="sxs-lookup"><span data-stu-id="eb984-186">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="eb984-187">[Pověření](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) má použít pro podepisování.</span><span class="sxs-lookup"><span data-stu-id="eb984-187">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="eb984-188">[Identity a rozhraní API prostředky](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) , že uživatelé můžou žádat o přístup k:</span><span class="sxs-lookup"><span data-stu-id="eb984-188">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="eb984-189">Prostředky rozhraní API představují chráněných dat nebo funkce, které má uživatel přístup s přístupovým tokenem.</span><span class="sxs-lookup"><span data-stu-id="eb984-189">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="eb984-190">Příkladem prostředku rozhraní API může být webového rozhraní API (nebo sadu rozhraní API), který vyžaduje ověření.</span><span class="sxs-lookup"><span data-stu-id="eb984-190">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="eb984-191">Prostředky identity představují informace (deklarace identity), které jsou uvedeny na klienta k identifikaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="eb984-191">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="eb984-192">Deklarace mohou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="eb984-192">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="eb984-193">[Klienti](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , která se připojují k vyžádání tokeny.</span><span class="sxs-lookup"><span data-stu-id="eb984-193">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="eb984-194">Mechanismus úložiště pro informace o uživateli, jako například [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) nebo alternativu.</span><span class="sxs-lookup"><span data-stu-id="eb984-194">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="eb984-195">Když zadáte klienty a zdroje informací pro IdentityServer4 použít, můžete předat <xref:System.Collections.Generic.IEnumerable%601> kolekce příslušného typu metodám, které přebírají klienta nebo prostředků úložiště v paměti.</span><span class="sxs-lookup"><span data-stu-id="eb984-195">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="eb984-196">Nebo pro složitější scénáře, můžete zadat klienta nebo prostředků poskytovatele typů pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="eb984-196">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="eb984-197">Ukázka konfigurace pro IdentityServer4 používat prostředky v paměti a poskytuje vlastní typ IClientStore klientů může vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="eb984-197">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="eb984-198">Využívání tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="eb984-198">Consume security tokens</span></span>

<span data-ttu-id="eb984-199">Ověřování koncového bodu OpenID Connect nebo vystavování tokenů zabezpečení řeší některé scénáře.</span><span class="sxs-lookup"><span data-stu-id="eb984-199">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="eb984-200">Ale co služba, která jednoduše potřebuje k omezení přístupu k těmto uživatelům, kteří mají platný zabezpečení tokeny, které byly poskytnuty jiné služby?</span><span class="sxs-lookup"><span data-stu-id="eb984-200">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="eb984-201">Pro tento scénář je k dispozici v ověřovací middleware, který zpracovává tokenů JWT **Microsoft.AspNetCore.Authentication.JwtBearer** balíčku.</span><span class="sxs-lookup"><span data-stu-id="eb984-201">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="eb984-202">Token JWT zastupuje "[webového tokenu JSON](https://tools.ietf.org/html/rfc7519)" a je běžný formát tokenu zabezpečení (definované RFC 7519) pro komunikaci deklarací identity zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="eb984-202">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="eb984-203">Zjednodušený příklad, jak používat middleware pro využívání těchto tokenů může vypadat jako tento fragment kódu na základě mikroslužeb Ordering.Api z aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="eb984-203">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

<span data-ttu-id="eb984-204">Parametry v tomto použití jsou:</span><span class="sxs-lookup"><span data-stu-id="eb984-204">The parameters in this usage are:</span></span>

- <span data-ttu-id="eb984-205">`Audience` představuje příjemce příchozím tokenu nebo tokenu uděluje přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="eb984-205">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="eb984-206">Hodnota zadaná v tomto parametru se neshoduje s parametrem tokenu, token odmítne.</span><span class="sxs-lookup"><span data-stu-id="eb984-206">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="eb984-207">`Authority` je adresa serveru vydání tokenu ověřování.</span><span class="sxs-lookup"><span data-stu-id="eb984-207">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="eb984-208">Middlewaru ověřování nosiče JWT používá tento identifikátor URI k získání veřejného klíče, který slouží k ověření podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="eb984-208">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="eb984-209">Middleware také potvrdí, že `iss` parametr v tokenu shoduje se pomocí tohoto identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="eb984-209">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="eb984-210">Dalším parametrem, `RequireHttpsMetadata`, je užitečné pro testovací účely; tento parametr nastavíte na hodnotu false můžete otestovat v prostředích, ve kterém nemáte certifikáty.</span><span class="sxs-lookup"><span data-stu-id="eb984-210">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="eb984-211">V nasazení reálné nosné tokeny JWT vždy předat pouze přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eb984-211">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="eb984-212">Pomocí tohoto middlewaru v místě se automaticky tokeny JWT extrahují z autorizační hlavičky.</span><span class="sxs-lookup"><span data-stu-id="eb984-212">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="eb984-213">Jsou poté deserializován, ověřit (pomocí hodnot v `Audience` a `Authority` parametry) a uložené jako uživatelské informace, které se později odkazovalo akce MVC nebo filtry autorizace.</span><span class="sxs-lookup"><span data-stu-id="eb984-213">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="eb984-214">Middlewaru ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je třeba použití místní certifikát ověřit token, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="eb984-214">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="eb984-215">V tomto scénáři můžete zadat `TokenValidationParameters` objekt `JwtBearerOptions` objektu.</span><span class="sxs-lookup"><span data-stu-id="eb984-215">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="eb984-216">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="eb984-216">Additional resources</span></span>

- <span data-ttu-id="eb984-217">**Sdílení souborů cookie mezi aplikacemi** \\</span><span class="sxs-lookup"><span data-stu-id="eb984-217">**Sharing cookies between applications** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

- <span data-ttu-id="eb984-218">**Úvod do Identity** \\</span><span class="sxs-lookup"><span data-stu-id="eb984-218">**Introduction to Identity** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="eb984-219">**Rick Anderson. Dvoufaktorové ověřování přes SMS** \\</span><span class="sxs-lookup"><span data-stu-id="eb984-219">**Rick Anderson. Two-factor authentication with SMS** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="eb984-220">**Povolení ověřování přes Facebook, Google a další externí zprostředkovatele** \\</span><span class="sxs-lookup"><span data-stu-id="eb984-220">**Enabling authentication using Facebook, Google and other external providers** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="eb984-221">**Michell Anicas. Úvod do OAuth 2** \\</span><span class="sxs-lookup"><span data-stu-id="eb984-221">**Michell Anicas. An Introduction to OAuth 2** \\</span></span>
  [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- <span data-ttu-id="eb984-222">**AspNet.Security.OAuth.Providers** (úložiště GitHub pro poskytovatelů OAuth technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eb984-222">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span> \
  [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- <span data-ttu-id="eb984-223">**Danny Strockis. Integrace Azure AD do webové aplikace ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="eb984-223">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app** \\</span></span>
  [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- <span data-ttu-id="eb984-224">**IdentityServer4. Oficiální dokumentaci** \\</span><span class="sxs-lookup"><span data-stu-id="eb984-224">**IdentityServer4. Official documentation** \\</span></span>
  *<https://identityserver4.readthedocs.io/en/latest/>*

>[!div class="step-by-step"]
><span data-ttu-id="eb984-225">[Předchozí](../implement-resilient-applications/monitor-app-health.md)
>[další](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="eb984-225">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
