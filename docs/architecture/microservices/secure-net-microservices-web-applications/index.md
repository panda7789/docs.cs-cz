---
title: Zabezpečení mikroslužeb a webových aplikací .NET
description: Zabezpečení u mikroslužeb a webových aplikací .NET – Získejte informace o možnostech ověřování v ASP.NET Core webových aplikacích.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 0894465858e3503e2eddb5299b404f7ba95fdd6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296473"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="70e61-103">Zajištění zabezpečených mikroslužeb a webových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="70e61-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="70e61-104">K dispozici je mnoho aspektů zabezpečení v mikroslužbách a webových aplikacích, které může toto téma snadno provést několik knih, jako je tato, v této části se zaměříme na ověřování, autorizaci a tajné klíče aplikací.</span><span class="sxs-lookup"><span data-stu-id="70e61-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="70e61-105">Implementace ověřování v mikroslužbách a webových aplikacích .NET</span><span class="sxs-lookup"><span data-stu-id="70e61-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="70e61-106">Pro prostředky a rozhraní API, které služba publikovala, je často potřeba omezit na určité důvěryhodné uživatele nebo klienty.</span><span class="sxs-lookup"><span data-stu-id="70e61-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="70e61-107">Prvním krokem pro provedení těchto řazení rozhodnutí o důvěryhodnosti na úrovni rozhraní API je ověřování.</span><span class="sxs-lookup"><span data-stu-id="70e61-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="70e61-108">Ověřování je proces spolehlivého ověření identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="70e61-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="70e61-109">Ve scénářích mikroslužeb se ověřování obvykle zpracovává centrálně.</span><span class="sxs-lookup"><span data-stu-id="70e61-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="70e61-110">Pokud používáte bránu API, je brána vhodná pro ověření, jak je znázorněno na obrázku 9-1.</span><span class="sxs-lookup"><span data-stu-id="70e61-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="70e61-111">Pokud použijete tento přístup, ujistěte se, že k jednotlivým mikroslužbám nejde získat přímý přístup (bez brány API), pokud se neuskuteční další zabezpečení pro ověřování zpráv bez ohledu na to, jestli pocházejí z brány nebo ne.</span><span class="sxs-lookup"><span data-stu-id="70e61-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Když brána API vycentralizaci ověřování, přidá informace o uživateli při předávání požadavků mikroslužbám.](./media/image1.png)

<span data-ttu-id="70e61-113">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="70e61-113">**Figure 9-1**.</span></span> <span data-ttu-id="70e61-114">Centralizované ověřování pomocí brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="70e61-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="70e61-115">Pokud se k službám dají získat přístup přímo, můžete k ověřování uživatelů použít ověřovací službu, jako je Azure Active Directory nebo vyhrazená mikroslužba ověřování, která funguje jako služba tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="70e61-115">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="70e61-116">Rozhodnutí o důvěryhodnosti se sdílí mezi službami s tokeny zabezpečení nebo soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="70e61-116">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="70e61-117">(Tyto tokeny je možné v případě potřeby sdílet mezi ASP.NET Core aplikacemi, a to implementací [sdílení souborů cookie](/aspnet/core/security/cookie-sharing).) Tento model je znázorněn na obrázku 9-2.</span><span class="sxs-lookup"><span data-stu-id="70e61-117">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Pokud jsou mikroslužby k dispozici přímo, důvěřuje, která zahrnuje ověřování a autorizaci, je zpracována tokenem zabezpečení vydaným pomocí vyhrazené mikroslužby, která je sdílena mezi mikroslužbami.](./media/image2.png)

<span data-ttu-id="70e61-119">**Obrázek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="70e61-119">**Figure 9-2**.</span></span> <span data-ttu-id="70e61-120">Ověřování pomocí mikroslužby identity; vztah důvěryhodnosti se sdílí pomocí autorizačního tokenu.</span><span class="sxs-lookup"><span data-stu-id="70e61-120">Authentication by identity microservice; trust is shared using an authorization token</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="70e61-121">Ověřování pomocí ASP.NET Core identity</span><span class="sxs-lookup"><span data-stu-id="70e61-121">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="70e61-122">Primárním mechanismem v ASP.NET Core pro identifikaci uživatelů aplikace je systém členství [ASP.NET Core identit](/aspnet/core/security/authentication/identity) .</span><span class="sxs-lookup"><span data-stu-id="70e61-122">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="70e61-123">ASP.NET Core identity ukládá informace o uživateli (včetně přihlašovacích údajů, rolí a deklarací) do úložiště dat nakonfigurovaného vývojářem.</span><span class="sxs-lookup"><span data-stu-id="70e61-123">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="70e61-124">Úložiště dat ASP.NET Core identity je obvykle úložiště Entity Framework, které je součástí `Microsoft.AspNetCore.Identity.EntityFrameworkCore` balíčku.</span><span class="sxs-lookup"><span data-stu-id="70e61-124">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="70e61-125">Vlastní úložiště nebo jiné balíčky třetích stran ale můžou sloužit k ukládání informací o identitě do Azure Table Storage, CosmosDB nebo jiných umístění.</span><span class="sxs-lookup"><span data-stu-id="70e61-125">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="70e61-126">Následující kód je pořízen ze šablony projektu ASP.NET Core webové aplikace s vybraným ověřováním individuálního uživatelského účtu.</span><span class="sxs-lookup"><span data-stu-id="70e61-126">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="70e61-127">Ukazuje, jak nakonfigurovat ASP.NET Core identity pomocí EntityFramework. Core v metodě Startup. ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="70e61-127">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="70e61-128">Po nakonfigurování ASP.NET Core identity ji povolíte voláním aplikace. UseIdentity v `Startup.Configure` metodě služby.</span><span class="sxs-lookup"><span data-stu-id="70e61-128">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="70e61-129">Použití ASP.NET Core identity umožňuje několik scénářů:</span><span class="sxs-lookup"><span data-stu-id="70e61-129">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="70e61-130">Vytvořte nové informace o uživateli pomocí typu UserManager (userManager. CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="70e61-130">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="70e61-131">Ověřování uživatelů pomocí typu SignInManager</span><span class="sxs-lookup"><span data-stu-id="70e61-131">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="70e61-132">Můžete použít `signInManager.SignInAsync` pro přihlášení přímo nebo `signInManager.PasswordSignInAsync` pro potvrzení, že je heslo uživatele správné a pak se do něj přihlásí.</span><span class="sxs-lookup"><span data-stu-id="70e61-132">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="70e61-133">Identifikujte uživatele na základě informací uložených v souboru cookie (načtený middleware ASP.NET Core identity) tak, aby následné požadavky z prohlížeče zahrnovaly identitu a deklarace uživatele přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="70e61-133">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="70e61-134">ASP.NET Core identita také podporuje [dvojúrovňové ověřování](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="70e61-134">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="70e61-135">V případě scénářů ověřování, které využívají úložiště dat místního uživatele a které trvaly identity mezi požadavky pomocí souborů cookie (jako jsou typické pro webové aplikace MVC), ASP.NET Core identita je doporučené řešení.</span><span class="sxs-lookup"><span data-stu-id="70e61-135">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="70e61-136">Ověřování pomocí externích zprostředkovatelů</span><span class="sxs-lookup"><span data-stu-id="70e61-136">Authenticate with external providers</span></span>

<span data-ttu-id="70e61-137">ASP.NET Core podporuje také použití [externích zprostředkovatelů ověřování](/aspnet/core/security/authentication/social/) , aby se uživatelé mohli přihlašovat prostřednictvím toků [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) .</span><span class="sxs-lookup"><span data-stu-id="70e61-137">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="70e61-138">To znamená, že se uživatelé můžou přihlásit pomocí stávajících procesů ověřování od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter, a přidružit tyto identity k identitě ASP.NET Core ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="70e61-138">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="70e61-139">Chcete-li použít externí ověřování, zahrňte příslušný middleware ověřování do kanálu zpracování požadavků HTTP vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="70e61-139">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="70e61-140">Tento middleware zodpovídá za zpracování žádostí o vrácení tras identifikátorů URI od poskytovatele ověřování, zaznamenání informací o identitě a jejich zpřístupnění prostřednictvím metody SignInManager. GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="70e61-140">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="70e61-141">Oblíbená externí poskytovatelé ověřování a jejich přidružené balíčky NuGet jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="70e61-141">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="70e61-142">**Poskytovatel**</span><span class="sxs-lookup"><span data-stu-id="70e61-142">**Provider**</span></span>  | <span data-ttu-id="70e61-143">**Balíček**</span><span class="sxs-lookup"><span data-stu-id="70e61-143">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="70e61-144">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="70e61-144">**Microsoft**</span></span> | <span data-ttu-id="70e61-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="70e61-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="70e61-146">**Google**</span><span class="sxs-lookup"><span data-stu-id="70e61-146">**Google**</span></span>    | <span data-ttu-id="70e61-147">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="70e61-147">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="70e61-148">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="70e61-148">**Facebook**</span></span>  | <span data-ttu-id="70e61-149">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="70e61-149">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="70e61-150">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="70e61-150">**Twitter**</span></span>   | <span data-ttu-id="70e61-151">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="70e61-151">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="70e61-152">Ve všech případech je middleware zaregistrován voláním metody registrace podobné `app.Use{ExternalProvider}Authentication` v. `Startup.Configure`</span><span class="sxs-lookup"><span data-stu-id="70e61-152">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="70e61-153">Tyto metody registrace přebírají objekt Options, který obsahuje ID aplikace a tajné informace (například heslo), jak to vyžaduje poskytovatel.</span><span class="sxs-lookup"><span data-stu-id="70e61-153">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="70e61-154">Externí zprostředkovatelé ověřování vyžadují, aby se aplikace zaregistrovala (jak je vysvětleno v [dokumentaci ASP.NET Core](/aspnet/core/security/authentication/social/)), aby mohla informovat uživatele o tom, co aplikace žádá o přístup k jejich identitě.</span><span class="sxs-lookup"><span data-stu-id="70e61-154">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="70e61-155">Jakmile je middleware zaregistrován v `Startup.Configure`nástroji, můžete uživatele vyzvat, aby se přihlásili z jakékoli akce kontroleru.</span><span class="sxs-lookup"><span data-stu-id="70e61-155">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="70e61-156">K tomu je potřeba vytvořit `AuthenticationProperties` objekt, který obsahuje název poskytovatele ověřování a adresu URL pro přesměrování.</span><span class="sxs-lookup"><span data-stu-id="70e61-156">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="70e61-157">Pak vrátíte odpověď na výzvu, která `AuthenticationProperties` objekt předává.</span><span class="sxs-lookup"><span data-stu-id="70e61-157">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="70e61-158">Příklad ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="70e61-158">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="70e61-159">Parametr redirectUrl zahrnuje adresu URL, na kterou by měl externí poskytovatel přesměrovat po ověření uživatele.</span><span class="sxs-lookup"><span data-stu-id="70e61-159">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="70e61-160">Adresa URL by měla představovat akci, která bude uživatele podepsat na základě externích informací o identitě, jako v následujícím zjednodušeném příkladu:</span><span class="sxs-lookup"><span data-stu-id="70e61-160">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="70e61-161">Pokud zvolíte možnost ověřování **individuálního uživatelského účtu** při vytváření projektu webové aplikace ASP.NET code v aplikaci Visual Studio, veškerý kód nezbytný pro přihlášení k externímu poskytovateli je již v projektu obsažen, jak je znázorněno na obrázku 9-3.</span><span class="sxs-lookup"><span data-stu-id="70e61-161">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Dialog pro novou ASP.NET Core webovou aplikaci zvýrazněním tlačítka pro změnu ověřování.](./media/image3.png)

<span data-ttu-id="70e61-163">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="70e61-163">**Figure 9-3**.</span></span> <span data-ttu-id="70e61-164">Výběr možnosti pro použití externího ověřování při vytváření projektu webové aplikace</span><span class="sxs-lookup"><span data-stu-id="70e61-164">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="70e61-165">Kromě externích poskytovatelů ověřování uvedených v předchozích částech jsou k dispozici balíčky třetích stran, které poskytují middleware pro používání mnoha dalších externích poskytovatelů ověřování.</span><span class="sxs-lookup"><span data-stu-id="70e61-165">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="70e61-166">Seznam naleznete v tématu [ASPNET. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="70e61-166">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="70e61-167">Můžete také vytvořit vlastní middleware pro externí ověřování a vyřešit určité zvláštní potřeby.</span><span class="sxs-lookup"><span data-stu-id="70e61-167">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="70e61-168">Ověřování pomocí nosných tokenů</span><span class="sxs-lookup"><span data-stu-id="70e61-168">Authenticate with bearer tokens</span></span>

<span data-ttu-id="70e61-169">Ověřování pomocí ASP.NET Core identity (nebo zprostředkovatelů identity a externích ověřování) funguje dobře pro mnoho scénářů webových aplikací, ve kterých je vhodné ukládat informace o uživatelích v souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="70e61-169">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="70e61-170">V jiných scénářích se ale soubory cookie nejedná o přirozený způsob uchování a přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="70e61-170">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="70e61-171">Například v ASP.NET Core webové rozhraní API, které zveřejňuje koncové body RESTful, které mohou být k dispozici v aplikacích s jedním stránkou (jednostránkové), nativními klienty nebo dokonce jinými webovými rozhraními API, obvykle chcete místo toho použít ověřování pomocí nosných tokenů.</span><span class="sxs-lookup"><span data-stu-id="70e61-171">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="70e61-172">Tyto typy aplikací nefungují se soubory cookie, ale můžou snadno získat nosný token a zahrnout ho do autorizační hlavičky dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="70e61-172">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="70e61-173">Pokud chcete povolit ověřování pomocí tokenu, ASP.NET Core podporuje několik možností pro použití [OAuth 2,0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="70e61-173">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="70e61-174">Ověřování pomocí zprostředkovatele identity OpenID Connect nebo OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="70e61-174">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="70e61-175">Pokud jsou informace o uživateli uložené v Azure Active Directory nebo jiném řešení identity, které podporuje OpenID Connect nebo OAuth 2,0, můžete k ověření pomocí OpenID Connect použít balíček **Microsoft. AspNetCore. Authentication. OpenIdConnect** . pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="70e61-175">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="70e61-176">Chcete-li například ověřit identitu. rozhraní API mikroslužeb v eShopOnContainers, může webová aplikace ASP.NET Core použít middleware z tohoto balíčku, jak je znázorněno v následujícím zjednodušeném `Startup.cs`příkladu:</span><span class="sxs-lookup"><span data-stu-id="70e61-176">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="70e61-177">Pamatujte na to, že když použijete tento pracovní postup, ASP.NET Core middleware identity není potřeba, protože veškeré úložiště informací o uživatelích a ověřování zpracovává služba identit.</span><span class="sxs-lookup"><span data-stu-id="70e61-177">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="70e61-178">Vydávání tokenů zabezpečení z ASP.NET Core služby</span><span class="sxs-lookup"><span data-stu-id="70e61-178">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="70e61-179">Pokud dáváte přednost vydávání tokenů zabezpečení pro místní ASP.NET Core uživatelů identity místo používání externího poskytovatele identity, můžete využít některé z dobrých knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="70e61-179">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="70e61-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) jsou poskytovatelé, kteří se snadno integrují pomocí ASP.NET Core identity, a umožňují tak vydávat tokeny zabezpečení ze služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="70e61-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="70e61-181">[Dokumentace k IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) obsahuje podrobné pokyny pro používání knihovny.</span><span class="sxs-lookup"><span data-stu-id="70e61-181">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="70e61-182">Základní kroky pro použití IdentityServer4 k vydávání tokenů jsou ale následující.</span><span class="sxs-lookup"><span data-stu-id="70e61-182">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="70e61-183">Voláte aplikaci. UseIdentityServer v metodě Startup. Configure, která přidá IdentityServer4 do kanálu zpracování požadavků HTTP aplikace.</span><span class="sxs-lookup"><span data-stu-id="70e61-183">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="70e61-184">To umožňuje knihovně zajišťovat požadavky na koncové body OpenID Connect a OAuth2 jako/Connect/token.</span><span class="sxs-lookup"><span data-stu-id="70e61-184">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="70e61-185">IdentityServer4 v Startup. ConfigureServices nakonfigurujete tak, že provedete volání služeb. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="70e61-185">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="70e61-186">Server identit konfigurujete nastavením následujících dat:</span><span class="sxs-lookup"><span data-stu-id="70e61-186">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="70e61-187">[Přihlašovací údaje](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) , které se mají použít k podepisování</span><span class="sxs-lookup"><span data-stu-id="70e61-187">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="70e61-188">[Prostředky identity a rozhraní API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) , které uživatelé mohou požadovat přístup:</span><span class="sxs-lookup"><span data-stu-id="70e61-188">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="70e61-189">Prostředky rozhraní API reprezentují chráněná data nebo funkce, ke kterým má uživatel přístup pomocí přístupového tokenu.</span><span class="sxs-lookup"><span data-stu-id="70e61-189">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="70e61-190">Příkladem prostředku rozhraní API může být webové rozhraní API (nebo sada rozhraní API), které vyžaduje autorizaci.</span><span class="sxs-lookup"><span data-stu-id="70e61-190">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="70e61-191">Prostředky identity představují informace (deklarace identity), které jsou předány klientovi k identifikaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="70e61-191">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="70e61-192">Deklarace identity můžou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="70e61-192">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="70e61-193">[Klienti](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , kteří se budou připojovat za účelem žádosti o tokeny.</span><span class="sxs-lookup"><span data-stu-id="70e61-193">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="70e61-194">Mechanizmus úložiště pro informace o uživateli, například [ASP.NET Core identitu](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) nebo alternativu.</span><span class="sxs-lookup"><span data-stu-id="70e61-194">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="70e61-195">Když zadáte klienty a prostředky, které má IdentityServer4 použít, můžete předat <xref:System.Collections.Generic.IEnumerable%601> kolekci příslušného typu metodám, které přijímají úložiště klientů v paměti nebo zdrojů.</span><span class="sxs-lookup"><span data-stu-id="70e61-195">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="70e61-196">V případě složitějších scénářů můžete poskytovat typy klientů nebo prostředků poskytovatele prostřednictvím injektáže závislostí.</span><span class="sxs-lookup"><span data-stu-id="70e61-196">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="70e61-197">Ukázková konfigurace IdentityServer4 pro použití prostředků v paměti a klientů, které poskytuje vlastní typ IClientStore, může vypadat podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70e61-197">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="70e61-198">Využívat tokeny zabezpečení</span><span class="sxs-lookup"><span data-stu-id="70e61-198">Consume security tokens</span></span>

<span data-ttu-id="70e61-199">Ověřování pomocí koncového bodu OpenID Connect nebo vydávání vlastních tokenů zabezpečení se zabývá některými scénáři.</span><span class="sxs-lookup"><span data-stu-id="70e61-199">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="70e61-200">Ale jak potřebujete službu, která jednoduše potřebuje omezit přístup k uživatelům, kteří mají platné tokeny zabezpečení, které byly poskytnuty jinou službou?</span><span class="sxs-lookup"><span data-stu-id="70e61-200">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="70e61-201">V tomto scénáři je k dispozici middleware ověřování, který zpracovává tokeny JWT v balíčku **Microsoft. AspNetCore. Authentication. JwtBearer** .</span><span class="sxs-lookup"><span data-stu-id="70e61-201">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="70e61-202">JWT představuje "[JSON web token](https://tools.ietf.org/html/rfc7519)" a je běžný formát tokenu zabezpečení (definovaný v dokumentu RFC 7519) pro komunikaci s deklaracemi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="70e61-202">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="70e61-203">Zjednodušený příklad, jak použít middleware ke využívání takových tokenů, může vypadat jako fragment kódu z řazení. mikroslužba API eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="70e61-203">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="70e61-204">Parametry v tomto použití jsou:</span><span class="sxs-lookup"><span data-stu-id="70e61-204">The parameters in this usage are:</span></span>

- <span data-ttu-id="70e61-205">`Audience`představuje přijímač příchozího tokenu nebo prostředku, ke kterému token uděluje přístup.</span><span class="sxs-lookup"><span data-stu-id="70e61-205">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="70e61-206">Pokud hodnota zadaná v tomto parametru neodpovídá parametru v tokenu, token se odmítne.</span><span class="sxs-lookup"><span data-stu-id="70e61-206">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="70e61-207">`Authority`je adresa ověřovacího serveru pro vydávání tokenů.</span><span class="sxs-lookup"><span data-stu-id="70e61-207">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="70e61-208">Middleware pro ověření nosiče JWT pomocí tohoto identifikátoru URI získá veřejný klíč, který lze použít k ověření podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="70e61-208">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="70e61-209">Middleware také potvrdí, že `iss` parametr v tokenu odpovídá tomuto identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="70e61-209">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="70e61-210">Další parametr, `RequireHttpsMetadata`, je užitečný pro účely testování. Tento parametr nastavíte na hodnotu false, abyste mohli testovat v prostředích, kde nemáte certifikáty.</span><span class="sxs-lookup"><span data-stu-id="70e61-210">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="70e61-211">V reálných nasazeních by se tokeny JWT nosiče měly vždycky předávat jenom přes HTTPS.</span><span class="sxs-lookup"><span data-stu-id="70e61-211">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="70e61-212">Díky tomuto middlewaru jsou tokeny JWT automaticky extrahovány z autorizačních hlaviček.</span><span class="sxs-lookup"><span data-stu-id="70e61-212">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="70e61-213">Pak jsou deserializovatelné, ověřené (pomocí hodnot v `Audience` parametrech a `Authority` ) a uložené jako informace o uživateli, na které se později odkazuje pomocí akcí MVC nebo filtrů autorizace.</span><span class="sxs-lookup"><span data-stu-id="70e61-213">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="70e61-214">Middleware pro ověření nosiče JWT může také podporovat pokročilejší scénáře, jako je například použití místního certifikátu k ověření tokenu, není-li tato autorita k dispozici.</span><span class="sxs-lookup"><span data-stu-id="70e61-214">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="70e61-215">V tomto scénáři můžete určit `TokenValidationParameters` objekt v objektu.`JwtBearerOptions`</span><span class="sxs-lookup"><span data-stu-id="70e61-215">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="70e61-216">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="70e61-216">Additional resources</span></span>

- <span data-ttu-id="70e61-217">**Sdílení souborů cookie mezi aplikacemi** </span><span class="sxs-lookup"><span data-stu-id="70e61-217">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="70e61-218">**Úvod do identity** </span><span class="sxs-lookup"><span data-stu-id="70e61-218">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="70e61-219">**Rick Anderson. Dvojúrovňové ověřování pomocí SMS** </span><span class="sxs-lookup"><span data-stu-id="70e61-219">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="70e61-220">**Povolení ověřování přes Facebook, Google a další externí poskytovatele** </span><span class="sxs-lookup"><span data-stu-id="70e61-220">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="70e61-221">**Michell Anicas. Úvod k OAuth 2** </span><span class="sxs-lookup"><span data-stu-id="70e61-221">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="70e61-222">**ASPNET. Security. OAuth. Providers** (úložiště GitHub pro poskytovatele OAuth ASP.NET) </span><span class="sxs-lookup"><span data-stu-id="70e61-222">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="70e61-223">**Danny Strockis. Integrace Azure AD do webové aplikace ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="70e61-223">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app** </span></span>\
  <https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/>

- <span data-ttu-id="70e61-224">**IdentityServer4. Oficiální dokumentace** </span><span class="sxs-lookup"><span data-stu-id="70e61-224">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="70e61-225">[Předchozí](../implement-resilient-applications/monitor-app-health.md)Další
>[](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="70e61-225">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
