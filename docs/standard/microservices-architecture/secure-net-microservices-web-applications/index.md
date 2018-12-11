---
title: Zabezpečení Mikroslužby .NET a webové aplikace
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Zabezpečení Mikroslužby .NET a webové aplikace
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7ee559f3881101a2382e6767607d5de1482d74ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126468"
---
# <a name="securing-net-microservices-and-web-applications"></a>Zabezpečení Mikroslužby .NET a webové aplikace

Často je nezbytné pro rozhraní API, vystavené služby omezená na určité důvěryhodnými uživateli nebo klienty a prostředky. Prvním krokem při provádění těchto řadu rozhodnutí o důvěryhodnosti úroveň rozhraní API je ověřování. Ověřování je proces spolehlivě zjištění identity uživatele.

Ve scénářích mikroslužeb ověřování je obvykle zpracovávána centrálně. Pokud používáte bránu rozhraní API, brány je vhodné místo pro ověření, jak je znázorněno v obrázku 11-1. Pokud tuto metodu použijte, ujistěte se, že jednotlivých mikroslužeb není dostupný přímo (bez brány rozhraní API), není-li zvýšit zabezpečení se používají k ověření zprávy, jestli pocházejí z brány nebo ne.

![](./media/image1.png)

**Obrázek 11-1**. Centralizované ověření pomocí brány rozhraní API

Pokud přímo přístupné služby, jako ověřovací služba Azure Active Directory nebo vyhrazené ověřování mikroslužby funguje jako bezpečnostní služby tokenu (STS) se dá použít k ověřování uživatelů. Rozhodnutí o důvěryhodnosti jsou sdíleny mezi službami s tokeny zabezpečení nebo soubory cookie. (Tento dokument mohou sdílet mezi aplikacemi, v případě potřeby v ASP.NET Core s [služby ochrany dat](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Tento model je znázorněn v obrázku 11-2.

![](./media/image2.png)

**Obrázek 11-2**. Ověření identity mikroslužeb; vztah důvěryhodnosti se sdílí pomocí autorizační token

## <a name="authenticating-using-aspnet-core-identity"></a>Ověřování pomocí ASP.NET Core Identity

Je primární mechanismus v ASP.NET Core pro identifikaci aplikace uživatele [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) systému členství. ASP.NET Core Identity ukládá informace o uživatelském (včetně přihlašovací údaje, rolí a deklarací identity) v úložišti dat nakonfigurované vývojářem. Obvykle úložiště dat ASP.NET Core Identity je zahrnutý v balíčku Microsoft.AspNetCore.Identity.EntityFrameworkCore obchod Entity Framework. Ale vlastní úložiště nebo jiné balíčky třetích stran slouží k ukládání informací o identitě v Azure Table Storage, DocumentDB nebo jiné umístění.

Následující kód je převzatý z šablony projektu webové aplikace ASP.NET Core ověřováním účet jednotlivého uživatele vybrali. Ukazuje, jak nakonfigurovat pomocí EntityFramework.Core v metodě Startup.ConfigureServices ASP.NET Core Identity.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Po nakonfigurování technologie ASP.NET Core Identity povolit volání aplikace. UseIdentity v metodě Startup.Configure služby.

Použití ASP.NET Core Identity umožňuje několika situacích:

-   Vytvoření nového uživatele pomocí objektu UserManager. typ (userManager.CreateAsync).

-   Ověřování uživatelů pomocí SignInManager typu. SignInManager.SignInAsync můžete přihlásit přímo, nebo signInManager.PasswordSignInAsync potvrďte heslo uživatele je správný a pak přihlásí jej.

-   Identifikace uživatele na základě informací uložených v souboru cookie (který je pro čtení middlewarem ASP.NET Core Identity), tak, aby následné žádosti z prohlížeče bude obsahovat identita přihlášeného uživatele a deklarace identity.

ASP.NET Core Identity podporuje také [dvojúrovňového ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).

Scénáře ověřování služby, které usnadňují použití místního úložiště dat a který zachování identity mezi požadavky na používání souborů cookie (což je typické pro webové aplikace MVC), ASP.NET Core Identity je doporučené řešení.

## <a name="authenticating-using-external-providers"></a>Ověřování pomocí externí zprostředkovatele

ASP.NET Core také podporuje používání [externího zprostředkovatele ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/social/) umožňuje uživatelům přihlásit se přes [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) toky. To znamená, že uživatelé mohou přihlásit pomocí existujících procesů ověřování od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter a přiřadit tyto identity s ASP.NET Core identity ve vaší aplikaci.

Použití externího ověřování, zahrnují příslušný ověřovací middleware v kanálu zpracování požadavku HTTP vaší aplikace. Tento middleware je zodpovědná za zpracování žádostí má vrátit z zprostředkovatele ověřování, zaznamenávání informací o identitě a jejich zpřístupnění prostřednictvím metody SignInManager.GetExternalLoginInfo trasy identifikátoru URI.

Níže se zobrazují oblíbená externího zprostředkovatele ověřování a jejich přidružené balíčky NuGet.

**Společnosti Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google:** Microsoft.AspNetCore.Authentication.Google

**Facebooku:** Microsoft.AspNetCore.Authentication.Facebook

**Twitter:** Microsoft.AspNetCore.Authentication.Twitter

Ve všech případech middleware zaregistrován pomocí volání metody registrace podobné aplikace. V Startup.Configure použijte ověřování {ExternalProvider}. Tyto metody registrace trvat možnosti objekt, který obsahuje ID aplikace a tajných informací (s heslem, například), podle potřeby zprostředkovatelem. Externí zprostředkovatelé ověřování potřeba, aby aplikace k registraci (jak je vysvětleno v [dokumentace k ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) tak, aby se může informovat uživatele jaké aplikace žádá o přístup k svoji identitu.

Po registraci middleware v Startup.Configure můžete vyzvat uživatele k přihlášení z jakékoli akce kontroleru. K tomuto účelu vytvoříte AuthenticationProperties objekt, který obsahuje název zprostředkovatele ověřování a adresa URL přesměrování. Potom vrátí odpověď na výzvu, která předá objekt AuthenticationProperties. Následující kód ukazuje příklad tohoto objektu.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Parametr redirectUrl zahrnuje adresu URL, která by se měla přesměrovat externího poskytovatele, jakmile uživatel byl ověřen. Adresa URL by měla představovat akci, která se přihlásit uživatele na základě informací o externí identity, jako v následujícím příkladu zjednodušené:

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

Pokud se rozhodnete **jednotlivé uživatelské účty** možnost ověřování při vytváření projektu kódu ASP.NET a webové aplikace v sadě Visual Studio, veškerý kód se přihlásit pomocí externího poskytovatele je už v projektu, jak je znázorněno v obrázku 11-3.

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

**Obrázek 11-3**. Vyberete možnost pro použití externího ověřování při vytváření projektu webové aplikace

Kromě externího ověřování poskytovatelů uvedených výše, balíčky třetích stran jsou k dispozici, které poskytují middleware pro použití mnoha další externí zprostředkovatele ověřování. Seznam najdete v tématu [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) úložišti na Githubu.

Samozřejmě je také možné, vytvořte vlastní middleware externího ověřování.

## <a name="authenticating-with-bearer-tokens"></a>Ověřování pomocí nosných tokenů

Ověřování pomocí ASP.NET Core Identity (nebo identitu a externí zprostředkovatelé ověřování) funguje dobře pro řadu scénářů webové aplikace, ve kterých je vhodné ukládání informací o uživateli v souboru cookie. V jiných případech však souborů cookie nejsou přirozené prostředky uchování a přenosu dat.

Například v rozhraní API pro ASP.NET Core Web, který zveřejňuje koncové body RESTful, jednostránkové aplikace (SPA), ke kterým může přistupovat nativní klienty, nebo dokonce i pomocí dalších webových rozhraní API, obvykle je vhodné místo toho použít ověřování pomocí tokenu nosiče. Tyto typy aplikací není pracovat se soubory cookie, ale můžete snadno získat nosný token a zahrnout v hlavičce autorizace odeslání dalších žádostí. Pokud chcete povolit ověřování pomocí tokenu, ASP.NET Core podporuje několik možností pro používání [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>Ověřování pomocí poskytovatele OpenID Connect nebo identitu OAuth 2.0

Pokud uživatelské informace uloženy v Azure Active Directory nebo jiném řešení identity, která podporuje OpenID Connect nebo OAuth 2.0, můžete použít balíček Microsoft.AspNetCore.Authentication.OpenIdConnect k ověření pomocí OpenID Connect. pracovní postup. Například [ověřování na základě Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), webová aplikace ASP.NET Core můžete použít middleware z tohoto balíčku, jak je znázorněno v následujícím příkladu:

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

Konfigurační hodnoty jsou hodnoty Azure Active Directory, které vytvářejí, když je vaše aplikace [zaregistrovaný jako klient služby Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad). ID jednoho klienta je sdílet mezi různými mikroslužbami v aplikaci, pokud všechny se musí ověřovat uživatele ověřený přes Azure Active Directory.

Všimněte si, že pokud použijete tento pracovní postup, middleware ASP.NET Core Identity není potřeba, protože jsou všechny uživatelské informace úložiště a ověření zpracovávané službou Azure Active Directory.

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>Vystavování tokenů zabezpečení ze služby ASP.NET Core

Pokud chcete vystavovat tokeny zabezpečení pro místní uživatele ASP.NET Core Identity místo pomocí externího zprostředkovatele identity, můžete využít výhod některé dobré knihovny třetích stran.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) poskytovatel OpenID Connect, které lze snadno integrovat s ASP.NET Core Identity umožňuje vydávala tokeny zabezpečení ze služby ASP.NET Core. [IdentityServer4 dokumentaci](https://identityserver4.readthedocs.io/en/release/) obsahuje podrobné pokyny pro používání knihovny. Základní postup pomocí IdentityServer4 problém tokeny jsou však následujícím způsobem.

1.  Volání aplikace. UseIdentityServer v metodě Startup.Configure přidat IdentityServer4 kanál zpracování požadavků HTTP vaší aplikace. Díky tomu knihovny obsluhovat požadavky do koncových bodů OAuth2 jako /connect/token a OpenID Connect.

2.  IdentityServer4 Startup.ConfigureServices zobrazit, je možné nakonfigurovat tak, že volání služby. AddIdentityServer.

3.  Konfigurace identity serveru tím, že poskytuje následující data:

-   [Pověření](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) má použít pro podepisování.

-   [Identity a rozhraní API prostředky](https://identityserver4.readthedocs.io/en/release/topics/resources.html) , že uživatelé můžou žádat o přístup k:

<!-- -->

-   Prostředky rozhraní API představují chráněných dat nebo funkce, které má uživatel přístup s přístupovým tokenem. Příkladem prostředku rozhraní API může být webového rozhraní API (nebo sadu rozhraní API), který vyžaduje ověření.

-   Prostředky identity představují informace (deklarace identity), které jsou uvedeny na klienta k identifikaci uživatele. Deklarace mohou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.

<!-- -->

-   [Klienti](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , která se připojují k vyžádání tokeny.

-   Mechanismus úložiště pro informace o uživateli, jako například [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) nebo alternativu.

Když zadáte klienty a zdroje informací pro IdentityServer4 použít, můžete předat hodnota IEnumerable&lt;T&gt; kolekce příslušného typu metodám, které přebírají klienta nebo prostředků úložiště v paměti. Nebo pro složitější scénáře, můžete zadat klienta nebo prostředků poskytovatele typů pomocí vkládání závislostí.

Ukázka konfigurace pro IdentityServer4 používat prostředky v paměti a poskytuje vlastní typ IClientStore klientů může vypadat jako v následujícím příkladu:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>Využívání tokenů zabezpečení

Ověřování koncového bodu OpenID Connect nebo vystavování tokenů zabezpečení řeší některé scénáře. Ale co služba, která jednoduše potřebuje k omezení přístupu k těmto uživatelům, kteří mají platný zabezpečení tokeny, které byly poskytnuty jiné služby?

Pro tento scénář je k dispozici v balíčku Microsoft.AspNetCore.Authentication.JwtBearer ověřovací middleware, který zpracovává tokeny JWT. Token JWT zastupuje "[webového tokenu JSON](https://tools.ietf.org/html/rfc7519)" a je běžný formát tokenu zabezpečení (definované RFC 7519) pro komunikaci deklarací identity zabezpečení. Jednoduchý příklad, jak používat middleware pro využívání těchto tokenů může vypadat jako v následujícím příkladu. Tento kód musí předcházet volání s middlewarem ASP.NET Core MVC (aplikace. UseMvc).

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

Parametry v tomto použití jsou:

-   Cílová skupina představuje příjemce příchozím tokenu nebo tokenu uděluje přístup k prostředku. Hodnota zadaná v tomto parametru se neshoduje s parametrem aud v tokenu, token odmítne.

-   Autorita je adresa serveru vydání tokenu ověřování. Middlewaru ověřování nosiče JWT používá tento identifikátor URI k získání veřejného klíče, který slouží k ověření podpisu tokenu. Middleware také potvrdí, že parametr jednotky ISS – překročené v tokenu shoduje se pomocí tohoto identifikátoru URI.

-   AutomaticAuthenticate je logická hodnota, která určuje, zda uživatel definoval token, který by měl automaticky přihlášeni.

Dalším parametrem, RequireHttpsMetadata, se nepoužívá v tomto příkladu. Je vhodné pro testovací účely; Tento parametr nastavíte na hodnotu false, můžete otestovat v prostředích, kde nemáte certifikáty. V nasazení reálné nosné tokeny JWT vždy předat pouze přes protokol HTTPS.

Pomocí tohoto middlewaru v místě se automaticky tokeny JWT extrahují z autorizační hlavičky. Jejich jsou poté deserializován, ověří (pomocí hodnot v cílové skupině a autorita parametry) a ukládá jako uživatelské informace, které se později odkazovalo akce MVC nebo filtry autorizace.

Middlewaru ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je třeba použití místní certifikát ověřit token, pokud není k dispozici. V tomto scénáři můžete zadat objekt parametry tokenvalidationparameters v objektu JwtBearerOptions.

## <a name="additional-resources"></a>Další zdroje

-   **Sdílení souborů cookie mezi aplikacemi**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Úvod do Identity**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson. Dvoufaktorové ověřování přes SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Povolení ověřování přes Facebook, Google a další externí zprostředkovatele**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas. Úvod do OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (úložiště GitHub pro poskytovatelů OAuth technologie ASP.NET.
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   **Danny Strockis. Integrace Azure AD do webové aplikace ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **IdentityServer4. Oficiální dokumentaci**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)

>[!div class="step-by-step"]
>[Předchozí](../implement-resilient-applications/monitor-app-health.md)
>[další](authorization-net-microservices-web-applications.md)