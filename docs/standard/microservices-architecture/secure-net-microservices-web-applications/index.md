---
title: Zabezpečení Mikroslužby .NET a webové aplikace
description: Zabezpečení v rozhraní .NET Mikroslužeb a webových aplikací – seznámení s možností ověřování webové aplikace ASP.NET Core.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 3e2598f58bf2fb34a7ad7c107066d34e0e7c3408
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464811"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Zabezpečení Mikroslužby .NET a webové aplikace

Existuje mnoho aspektů zabezpečení v mikroslužbách a webových aplikacích, tématu snadné trvat několik knihy podobný následujícímu tak v této části se zaměříme na ověřování, autorizaci a tajných klíčů aplikací.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementace ověřování v mikroslužbách a webových aplikací .NET

Často je nezbytné pro prostředky a rozhraní API publikovat službou omezená na určité důvěryhodnými uživateli nebo klienti. Prvním krokem při provádění těchto řadu rozhodnutí o důvěryhodnosti úroveň rozhraní API je ověřování. Ověřování je proces spolehlivě ověřit identitu uživatele.

Ve scénářích mikroslužeb ověřování je obvykle zpracovávána centrálně. Pokud používáte bránu rozhraní API, brány je vhodné místo pro ověření, jak je znázorněno v obrázek 9-1. Pokud tuto metodu použijte, ujistěte se, že jednotlivých mikroslužeb není dostupný přímo (bez brány rozhraní API), není-li zvýšit zabezpečení se používají k ověření zprávy, jestli pocházejí z brány nebo ne.

![Pokud brána rozhraní API centralizuje ověřování, přidá informace o uživateli, když předává požadavky do mikroslužeb.](./media/image1.png)

**Obrázek 9-1**. Centralizované ověření pomocí brány rozhraní API

Pokud přímo přístupné služby, jako ověřovací služba Azure Active Directory nebo vyhrazené ověřování mikroslužby funguje jako bezpečnostní služby tokenu (STS) se dá použít k ověřování uživatelů. Rozhodnutí o důvěryhodnosti jsou sdíleny mezi službami s tokeny zabezpečení nebo soubory cookie. (Tyto tokeny lze sdílet mezi aplikací ASP.NET Core, v případě potřeby implementací [sdílení souborů cookie](/aspnet/core/security/cookie-sharing).) Tento model je znázorněn v obrázek 9-2.

![Když mikroslužeb jsou přímo přístupné, vztah důvěryhodnosti, který zahrnuje ověřování a autorizace, zařizuje služba tokenu zabezpečení vydaného službou vyhrazené mikroslužeb, sdílené mezi mikroslužbami.](./media/image2.png)

**Obrázek 9-2**. Ověření identity mikroslužeb; vztah důvěryhodnosti se sdílí pomocí autorizační token

### <a name="authenticate-with-aspnet-core-identity"></a>Ověřování pomocí ASP.NET Core Identity

Je primární mechanismus v ASP.NET Core pro identifikaci aplikace uživatele [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) systému členství. ASP.NET Core Identity ukládá informace o uživatelském (včetně přihlašovací údaje, rolí a deklarací identity) v úložišti dat nakonfigurované vývojářem. Rozhraní Entity Framework úložiště k dispozici v úložišti dat ASP.NET Core Identity je obvykle `Microsoft.AspNetCore.Identity.EntityFrameworkCore` balíčku. Ale vlastní úložiště nebo jiné balíčky třetích stran slouží k ukládání informací o identitě v Azure Table Storage, služby cosmos DB nebo jiné umístění.

Následující kód je převzatý z šablony projektu webové aplikace ASP.NET Core ověřováním účet jednotlivého uživatele vybrali. Ukazuje, jak nakonfigurovat pomocí EntityFramework.Core v metodě Startup.ConfigureServices ASP.NET Core Identity.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Po nakonfigurování technologie ASP.NET Core Identity povolit volání aplikace. UseIdentity ve vaší službě `Startup.Configure` metody.

Použití ASP.NET Core Identity umožňuje několika situacích:

- Vytvoření nového uživatele pomocí objektu UserManager. typ (userManager.CreateAsync).

- Ověřování uživatelů pomocí SignInManager typu. Můžete použít `signInManager.SignInAsync` přihlásit přímo, nebo `signInManager.PasswordSignInAsync` a potvrďte je zadáno správné heslo uživatele a pak přihlásí jej.

- Identifikace uživatele na základě informací uložených v souboru cookie (který je pro čtení middlewarem ASP.NET Core Identity), tak, aby následné žádosti z prohlížeče bude obsahovat identita přihlášeného uživatele a deklarace identity.

ASP.NET Core Identity podporuje také [dvojúrovňového ověřování](/aspnet/core/security/authentication/2fa).

Scénáře ověřování služby, které usnadňují použití místního úložiště dat a který zachování identity mezi požadavky na používání souborů cookie (což je typické pro webové aplikace MVC), ASP.NET Core Identity je doporučené řešení.

### <a name="authenticate-with-external-providers"></a>Ověřování pomocí externí zprostředkovatele

ASP.NET Core také podporuje používání [externího zprostředkovatele ověřování](/aspnet/core/security/authentication/social/) umožníte uživatelům přihlašovat se prostřednictvím [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) toky. To znamená, že uživatelé mohou přihlásit pomocí existujících procesů ověřování od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter a přiřadit tyto identity s ASP.NET Core identity ve vaší aplikaci.

Použití externího ověřování, zahrnují příslušný ověřovací middleware v kanálu zpracování požadavku HTTP vaší aplikace. Tento middleware je zodpovědná za zpracování žádostí má vrátit z zprostředkovatele ověřování, zaznamenávání informací o identitě a jejich zpřístupnění prostřednictvím metody SignInManager.GetExternalLoginInfo trasy identifikátoru URI.

Oblíbené externího zprostředkovatele ověřování a jejich přidružené balíčky NuGet jsou uvedeny v následující tabulce:

| **Poskytovatel**  | **Balíček**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

Ve všech případech, middleware zaregistrován pomocí volání metody registrace podobné `app.Use{ExternalProvider}Authentication` v `Startup.Configure`. Tyto metody registrace trvat možnosti objekt, který obsahuje ID aplikace a tajných informací (s heslem, například), podle potřeby zprostředkovatelem. Externí zprostředkovatelé ověřování potřeba, aby aplikace k registraci (jak je vysvětleno v [dokumentace k ASP.NET Core](/aspnet/core/security/authentication/social/)) tak, aby se může informovat uživatele jaké aplikace žádá o přístup k svoji identitu.

Jakmile middlewaru je registrovaný v `Startup.Configure`, můžete vyzvat uživatele k přihlášení z jakékoli akce kontroleru. K tomuto účelu vytvoříte `AuthenticationProperties` objekt, který obsahuje název zprostředkovatele ověřování a adresa URL přesměrování. Potom vrátit odpověď na výzvu, který předá `AuthenticationProperties` objektu. Následující kód ukazuje příklad tohoto objektu.

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

Pokud se rozhodnete **jednotlivé uživatelské účty** možnost ověřování při vytváření projektu kódu ASP.NET a webové aplikace v sadě Visual Studio, veškerý kód se přihlásit pomocí externího poskytovatele je už v projektu, jak je znázorněno v obrázku 9-3.

![Dialogové okno pro nová webová aplikace ASP.NET Core, zvýraznění na tlačítko Změnit ověřování.](./media/image3.png)

**Obrázek 9-3**. Vyberete možnost pro použití externího ověřování při vytváření projektu webové aplikace

Kromě externího ověřování poskytovatelů uvedených výše, balíčky třetích stran jsou k dispozici, které poskytují middleware pro použití mnoha další externí zprostředkovatele ověřování. Seznam najdete v tématu [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) úložišti na Githubu.

Můžete také vytvořit vlastní externí ověřovací middleware vyřešit některé zvláštní potřebu.

### <a name="authenticate-with-bearer-tokens"></a>Ověřování pomocí nosných tokenů

Ověřování pomocí ASP.NET Core Identity (nebo identitu a externí zprostředkovatelé ověřování) funguje dobře pro řadu scénářů webové aplikace, ve kterých je vhodné ukládání informací o uživateli v souboru cookie. V jiných případech však souborů cookie nejsou přirozené prostředky uchování a přenosu dat.

Například v rozhraní API pro ASP.NET Core Web, který zveřejňuje koncové body RESTful, jednostránkové aplikace (SPA), ke kterým může přistupovat nativní klienty, nebo dokonce i pomocí dalších webových rozhraní API, obvykle je vhodné místo toho použít ověřování pomocí tokenu nosiče. Tyto typy aplikací není pracovat se soubory cookie, ale můžete snadno získat nosný token a zahrnout v hlavičce autorizace odeslání dalších žádostí. Pokud chcete povolit ověřování pomocí tokenu, ASP.NET Core podporuje několik možností pro používání [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Ověřování pomocí poskytovatele OpenID Connect nebo identitu OAuth 2.0

Pokud uživatelské informace uloženy v Azure Active Directory nebo jiném řešení identity, která podporuje OpenID Connect nebo OAuth 2.0, můžete použít **Microsoft.AspNetCore.Authentication.OpenIdConnect** balíčku provést ověření pomocí pracovní postup OpenID Connect. Například k ověření Identity.Api mikroslužeb v aplikaci eShopOnContainers, webová aplikace ASP.NET Core můžete použít middleware z tohoto balíčku jak je znázorněno v následující zjednodušený příklad v `Startup.cs`:

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

Všimněte si, že pokud použijete tento pracovní postup, middleware ASP.NET Core Identity není potřeba, vzhledem k tomu, že všechny informace úložiště uživatele a ověření se zpracovává souborem Identity služby.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Vystavovat tokeny zabezpečení ze služby ASP.NET Core

Pokud chcete vystavovat tokeny zabezpečení pro místní uživatele ASP.NET Core Identity místo pomocí externího zprostředkovatele identity, můžete využít výhod některé dobré knihovny třetích stran.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) poskytovatel OpenID Connect, které lze snadno integrovat s ASP.NET Core Identity umožňuje vydávala tokeny zabezpečení ze služby ASP.NET Core. [IdentityServer4 dokumentaci](https://identityserver4.readthedocs.io/en/latest/) obsahuje podrobné pokyny pro používání knihovny. Základní postup pomocí IdentityServer4 problém tokeny jsou však následujícím způsobem.

1. Volání aplikace. UseIdentityServer v metodě Startup.Configure přidat IdentityServer4 kanál zpracování požadavků HTTP vaší aplikace. Díky tomu knihovny obsluhovat požadavky do koncových bodů OAuth2 jako /connect/token a OpenID Connect.

2. IdentityServer4 Startup.ConfigureServices zobrazit, je možné nakonfigurovat tak, že volání služby. AddIdentityServer.

3. Konfigurace identity serveru tak, že nastavíte následující data:

   - [Pověření](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) má použít pro podepisování.

   - [Identity a rozhraní API prostředky](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) , že uživatelé můžou žádat o přístup k:

      - Prostředky rozhraní API představují chráněných dat nebo funkce, které má uživatel přístup s přístupovým tokenem. Příkladem prostředku rozhraní API může být webového rozhraní API (nebo sadu rozhraní API), který vyžaduje ověření.

      - Prostředky identity představují informace (deklarace identity), které jsou uvedeny na klienta k identifikaci uživatele. Deklarace mohou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.

   - [Klienti](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , která se připojují k vyžádání tokeny.

   - Mechanismus úložiště pro informace o uživateli, jako například [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) nebo alternativu.

Když zadáte klienty a zdroje informací pro IdentityServer4 použít, můžete předat <xref:System.Collections.Generic.IEnumerable%601> kolekce příslušného typu metodám, které přebírají klienta nebo prostředků úložiště v paměti. Nebo pro složitější scénáře, můžete zadat klienta nebo prostředků poskytovatele typů pomocí vkládání závislostí.

Ukázka konfigurace pro IdentityServer4 používat prostředky v paměti a poskytuje vlastní typ IClientStore klientů může vypadat jako v následujícím příkladu:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>Využívání tokenů zabezpečení

Ověřování koncového bodu OpenID Connect nebo vystavování tokenů zabezpečení řeší některé scénáře. Ale co služba, která jednoduše potřebuje k omezení přístupu k těmto uživatelům, kteří mají platný zabezpečení tokeny, které byly poskytnuty jiné služby?

Pro tento scénář je k dispozici v ověřovací middleware, který zpracovává tokenů JWT **Microsoft.AspNetCore.Authentication.JwtBearer** balíčku. Token JWT zastupuje "[webového tokenu JSON](https://tools.ietf.org/html/rfc7519)" a je běžný formát tokenu zabezpečení (definované RFC 7519) pro komunikaci deklarací identity zabezpečení. Zjednodušený příklad, jak používat middleware pro využívání těchto tokenů může vypadat jako tento fragment kódu na základě mikroslužeb Ordering.Api z aplikaci eShopOnContainers.

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

Parametry v tomto použití jsou:

- `Audience` představuje příjemce příchozím tokenu nebo tokenu uděluje přístup k prostředku. Hodnota zadaná v tomto parametru se neshoduje s parametrem tokenu, token odmítne.

- `Authority` je adresa serveru vydání tokenu ověřování. Middlewaru ověřování nosiče JWT používá tento identifikátor URI k získání veřejného klíče, který slouží k ověření podpisu tokenu. Middleware také potvrdí, že `iss` parametr v tokenu shoduje se pomocí tohoto identifikátoru URI.

Dalším parametrem, `RequireHttpsMetadata`, je užitečné pro testovací účely; tento parametr nastavíte na hodnotu false můžete otestovat v prostředích, ve kterém nemáte certifikáty. V nasazení reálné nosné tokeny JWT vždy předat pouze přes protokol HTTPS.

Pomocí tohoto middlewaru v místě se automaticky tokeny JWT extrahují z autorizační hlavičky. Jsou poté deserializován, ověřit (pomocí hodnot v `Audience` a `Authority` parametry) a uložené jako uživatelské informace, které se později odkazovalo akce MVC nebo filtry autorizace.

Middlewaru ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je třeba použití místní certifikát ověřit token, pokud není k dispozici. V tomto scénáři můžete zadat `TokenValidationParameters` objekt `JwtBearerOptions` objektu.

## <a name="additional-resources"></a>Další zdroje

- **Sdílení souborů cookie mezi aplikacemi** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Úvod do Identity** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Dvoufaktorové ověřování přes SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Povolení ověřování přes Facebook, Google a další externí zprostředkovatele** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Úvod do OAuth 2** \
  [https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- **AspNet.Security.OAuth.Providers** (úložiště GitHub pro poskytovatelů OAuth technologie ASP.NET) \
  [https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- **Danny Strockis. Integrace Azure AD do webové aplikace ASP.NET Core** \
  [https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- **IdentityServer4. Oficiální dokumentaci** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Předchozí](../implement-resilient-applications/monitor-app-health.md)
>[další](authorization-net-microservices-web-applications.md)
