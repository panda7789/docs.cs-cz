---
title: Zabezpečení mikroslužeb a webových aplikací .NET
description: Zabezpečení u mikroslužeb a webových aplikací .NET – Získejte informace o možnostech ověřování v ASP.NET Core webových aplikacích.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: b25f02140915ce87c5c478d8a8a5fe28ba7693b3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736943"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Zajištění zabezpečených mikroslužeb a webových aplikací .NET

K dispozici je mnoho aspektů zabezpečení v mikroslužbách a webových aplikacích, které může toto téma snadno provést několik knih, jako je tato, v této části se zaměříme na ověřování, autorizaci a tajné klíče aplikací.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementace ověřování v mikroslužbách a webových aplikacích .NET

Pro prostředky a rozhraní API, které služba publikovala, je často potřeba omezit na určité důvěryhodné uživatele nebo klienty. Prvním krokem pro provedení těchto řazení rozhodnutí o důvěryhodnosti na úrovni rozhraní API je ověřování. Ověřování je proces spolehlivého ověření identity uživatele.

Ve scénářích mikroslužeb se ověřování obvykle zpracovává centrálně. Pokud používáte bránu API, je brána vhodná pro ověření, jak je znázorněno na obrázku 9-1. Pokud použijete tento přístup, ujistěte se, že k jednotlivým mikroslužbám nejde získat přímý přístup (bez brány API), pokud se neuskuteční další zabezpečení pro ověřování zpráv bez ohledu na to, jestli pocházejí z brány nebo ne.

![Diagram znázorňující, jak mobilní aplikace klienta komunikuje s back-endu.](./media/index/api-gateway-centralized-authentication.png)

**Obrázek 9-1**. Centralizované ověřování pomocí brány rozhraní API

Když brána API vycentralizaci ověřování, přidá informace o uživateli při předávání požadavků mikroslužbám. Pokud se k službám dají získat přístup přímo, můžete k ověřování uživatelů použít ověřovací službu, jako je Azure Active Directory nebo vyhrazená mikroslužba ověřování, která funguje jako služba tokenů zabezpečení (STS). Rozhodnutí o důvěryhodnosti se sdílí mezi službami s tokeny zabezpečení nebo soubory cookie. (Tyto tokeny je možné v případě potřeby sdílet mezi ASP.NET Core aplikacemi, a to implementací [sdílení souborů cookie](/aspnet/core/security/cookie-sharing).) Tento model je znázorněn na obrázku 9-2.

![Diagram znázorňující ověřování prostřednictvím back-endovéch mikroslužeb.](./media/index/identity-microservice-authentication.png)

**Obrázek 9-2**. Ověřování pomocí mikroslužby identity; vztah důvěryhodnosti se sdílí pomocí autorizačního tokenu.

Pokud jsou mikroslužby k dispozici přímo, důvěřuje, která zahrnuje ověřování a autorizaci, je zpracována tokenem zabezpečení vydaným pomocí vyhrazené mikroslužby, která je sdílena mezi mikroslužbami.

### <a name="authenticate-with-aspnet-core-identity"></a>Ověřování pomocí ASP.NET Core identity

Primárním mechanismem v ASP.NET Core pro identifikaci uživatelů aplikace je systém členství [ASP.NET Core identit](/aspnet/core/security/authentication/identity) . ASP.NET Core identity ukládá informace o uživateli (včetně přihlašovacích údajů, rolí a deklarací) do úložiště dat nakonfigurovaného vývojářem. Úložiště dat ASP.NET Core identity je obvykle Entity Framework úložiště, které je k dispozici v balíčku `Microsoft.AspNetCore.Identity.EntityFrameworkCore`. Vlastní úložiště nebo jiné balíčky třetích stran ale můžou sloužit k ukládání informací o identitě do Azure Table Storage, CosmosDB nebo jiných umístění.

Následující kód je pořízen ze šablony projektu ASP.NET Core webové aplikace s vybraným ověřováním individuálního uživatelského účtu. Ukazuje, jak nakonfigurovat ASP.NET Core identity pomocí EntityFramework. Core v metodě Startup. ConfigureServices.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Po nakonfigurování ASP.NET Core identity ji povolíte voláním aplikace. UseIdentity v metodě `Startup.Configure` služby.

Použití ASP.NET Core identity umožňuje několik scénářů:

- Vytvořte nové informace o uživateli pomocí typu UserManager (userManager. CreateAsync).

- Ověřování uživatelů pomocí typu SignInManager Můžete použít `signInManager.SignInAsync` k přímému přihlášení nebo `signInManager.PasswordSignInAsync` k potvrzení hesla uživatele a jeho přihlášení.

- Identifikujte uživatele na základě informací uložených v souboru cookie (načtený middleware ASP.NET Core identity) tak, aby následné požadavky z prohlížeče zahrnovaly identitu a deklarace uživatele přihlášeného uživatele.

ASP.NET Core identita také podporuje [dvojúrovňové ověřování](/aspnet/core/security/authentication/2fa).

V případě scénářů ověřování, které využívají úložiště dat místního uživatele a které trvaly identity mezi požadavky pomocí souborů cookie (jako jsou typické pro webové aplikace MVC), ASP.NET Core identita je doporučené řešení.

### <a name="authenticate-with-external-providers"></a>Ověřování pomocí externích zprostředkovatelů

ASP.NET Core podporuje také použití [externích zprostředkovatelů ověřování](/aspnet/core/security/authentication/social/) , aby se uživatelé mohli přihlašovat prostřednictvím toků [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) . To znamená, že se uživatelé můžou přihlásit pomocí stávajících procesů ověřování od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter, a přidružit tyto identity k identitě ASP.NET Core ve vaší aplikaci.

Chcete-li použít externí ověřování, zahrňte příslušný middleware ověřování do kanálu zpracování požadavků HTTP vaší aplikace. Tento middleware zodpovídá za zpracování žádostí o vrácení tras identifikátorů URI od poskytovatele ověřování, zaznamenání informací o identitě a jejich zpřístupnění prostřednictvím metody SignInManager. GetExternalLoginInfo.

Oblíbená externí poskytovatelé ověřování a jejich přidružené balíčky NuGet jsou uvedené v následující tabulce:

| **Zprostředkovatele**  | **Balíček**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft. AspNetCore. Authentication. MicrosoftAccount** |
| **Internetového**    | **Microsoft. AspNetCore. Authentication. Google**           |
| **Přes**  | **Microsoft. AspNetCore. Authentication. Facebook**         |
| **Službě**   | **Microsoft. AspNetCore. Authentication. Twitter**          |

Ve všech případech je middleware zaregistrován voláním metody registrace podobné `app.Use{ExternalProvider}Authentication` v `Startup.Configure`. Tyto metody registrace přebírají objekt Options, který obsahuje ID aplikace a tajné informace (například heslo), jak to vyžaduje poskytovatel. Externí zprostředkovatelé ověřování vyžadují, aby se aplikace zaregistrovala (jak je vysvětleno v [dokumentaci ASP.NET Core](/aspnet/core/security/authentication/social/)), aby mohla informovat uživatele o tom, co aplikace žádá o přístup k jejich identitě.

Jakmile je middleware zaregistrován v `Startup.Configure`, můžete uživatele vyzvat, aby se přihlásili z jakékoli akce kontroleru. Uděláte to tak, že vytvoříte objekt `AuthenticationProperties`, který obsahuje název poskytovatele ověřování a adresu URL pro přesměrování. Pak vrátíte odpověď na výzvu, která předá objekt `AuthenticationProperties`. Příklad ukazuje následující kód.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Parametr redirectUrl zahrnuje adresu URL, na kterou by měl externí poskytovatel přesměrovat po ověření uživatele. Adresa URL by měla představovat akci, která bude uživatele podepsat na základě externích informací o identitě, jako v následujícím zjednodušeném příkladu:

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

Pokud zvolíte možnost ověřování **individuálního uživatelského účtu** při vytváření projektu webové aplikace ASP.NET code v aplikaci Visual Studio, veškerý kód nezbytný pro přihlášení k externímu poskytovateli je již v projektu obsažen, jak je znázorněno na obrázku 9-3.

![Snímek obrazovky dialogového okna Nový ASP.NET Core webové aplikace](./media/index/select-external-authentication-option.png)

**Obrázek 9-3**. Výběr možnosti pro použití externího ověřování při vytváření projektu webové aplikace

Kromě externích poskytovatelů ověřování uvedených v předchozích částech jsou k dispozici balíčky třetích stran, které poskytují middleware pro používání mnoha dalších externích poskytovatelů ověřování. Seznam naleznete v tématu [ASPNET. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) na GitHubu.

Můžete také vytvořit vlastní middleware pro externí ověřování a vyřešit určité zvláštní potřeby.

### <a name="authenticate-with-bearer-tokens"></a>Ověřování pomocí nosných tokenů

Ověřování pomocí ASP.NET Core identity (nebo zprostředkovatelů identity a externích ověřování) funguje dobře pro mnoho scénářů webových aplikací, ve kterých je vhodné ukládat informace o uživatelích v souboru cookie. V jiných scénářích se ale soubory cookie nejedná o přirozený způsob uchování a přenosu dat.

Například v ASP.NET Core webové rozhraní API, které zveřejňuje koncové body RESTful, které mohou být k dispozici v aplikacích s jedním stránkou (jednostránkové), nativními klienty nebo dokonce jinými webovými rozhraními API, obvykle chcete místo toho použít ověřování pomocí nosných tokenů. Tyto typy aplikací nefungují se soubory cookie, ale můžou snadno získat nosný token a zahrnout ho do autorizační hlavičky dalších požadavků. Pokud chcete povolit ověřování pomocí tokenu, ASP.NET Core podporuje několik možností pro použití [OAuth 2,0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Ověřování pomocí zprostředkovatele identity OpenID Connect nebo OAuth 2,0

Pokud jsou informace o uživateli uložené v Azure Active Directory nebo jiném řešení identity, které podporuje OpenID Connect nebo OAuth 2,0, můžete k ověření pomocí OpenID Connect použít balíček **Microsoft. AspNetCore. Authentication. OpenIdConnect** . pracovního postupu. Například pro ověření identity. v ASP.NET Core eShopOnContainers může webová aplikace použít middleware z tohoto balíčku, jak je znázorněno v následujícím zjednodušeném příkladu v `Startup.cs`:

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

Pamatujte na to, že když použijete tento pracovní postup, ASP.NET Core middleware identity není potřeba, protože veškeré úložiště informací o uživatelích a ověřování zpracovává služba identit.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Vydávání tokenů zabezpečení z ASP.NET Core služby

Pokud dáváte přednost vydávání tokenů zabezpečení pro místní ASP.NET Core uživatelů identity místo používání externího poskytovatele identity, můžete využít některé z dobrých knihoven třetích stran.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) jsou poskytovatelé, kteří se snadno integrují pomocí ASP.NET Core identity, a umožňují tak vydávat tokeny zabezpečení ze služby ASP.NET Core. [Dokumentace k IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) obsahuje podrobné pokyny pro používání knihovny. Základní kroky pro použití IdentityServer4 k vydávání tokenů jsou ale následující.

1. Voláte aplikaci. UseIdentityServer v metodě Startup. Configure, která přidá IdentityServer4 do kanálu zpracování požadavků HTTP aplikace. To umožňuje knihovně zajišťovat požadavky na koncové body OpenID Connect a OAuth2 jako/Connect/token.

2. IdentityServer4 v Startup. ConfigureServices nakonfigurujete tak, že provedete volání služeb. AddIdentityServer.

3. Server identit konfigurujete nastavením následujících dat:

   - [Přihlašovací údaje](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) , které se mají použít k podepisování

   - [Prostředky identity a rozhraní API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) , které uživatelé mohou požadovat přístup:

      - Prostředky rozhraní API reprezentují chráněná data nebo funkce, ke kterým má uživatel přístup pomocí přístupového tokenu. Příkladem prostředku rozhraní API může být webové rozhraní API (nebo sada rozhraní API), které vyžaduje autorizaci.

      - Prostředky identity představují informace (deklarace identity), které jsou předány klientovi k identifikaci uživatele. Deklarace identity můžou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.

   - [Klienti](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , kteří se budou připojovat za účelem žádosti o tokeny.

   - Mechanizmus úložiště pro informace o uživateli, například [ASP.NET Core identitu](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) nebo alternativu.

Když zadáte klienty a prostředky, které má IdentityServer4 použít, můžete předat <xref:System.Collections.Generic.IEnumerable%601> kolekci příslušného typu do metod, které přijímají úložiště klientů v paměti nebo zdrojů. V případě složitějších scénářů můžete poskytovat typy klientů nebo prostředků poskytovatele prostřednictvím injektáže závislostí.

Ukázková konfigurace IdentityServer4 pro použití prostředků v paměti a klientů, které poskytuje vlastní typ IClientStore, může vypadat podobně jako v následujícím příkladu:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>Využívat tokeny zabezpečení

Ověřování pomocí koncového bodu OpenID Connect nebo vydávání vlastních tokenů zabezpečení se zabývá některými scénáři. Ale jak potřebujete službu, která jednoduše potřebuje omezit přístup k uživatelům, kteří mají platné tokeny zabezpečení, které byly poskytnuty jinou službou?

V tomto scénáři je k dispozici middleware ověřování, který zpracovává tokeny JWT v balíčku **Microsoft. AspNetCore. Authentication. JwtBearer** . JWT představuje "[JSON web token](https://tools.ietf.org/html/rfc7519)" a je běžný formát tokenu zabezpečení (definovaný v dokumentu RFC 7519) pro komunikaci s deklaracemi zabezpečení. Zjednodušený příklad, jak použít middleware ke využívání takových tokenů, může vypadat jako fragment kódu z řazení. mikroslužba API eShopOnContainers.

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

- `Audience` představuje přijímač příchozího tokenu nebo prostředku, ke kterému token uděluje přístup. Pokud hodnota zadaná v tomto parametru neodpovídá parametru v tokenu, token se odmítne.

- `Authority` je adresa ověřovacího serveru pro vydávání tokenů. Middleware pro ověření nosiče JWT pomocí tohoto identifikátoru URI získá veřejný klíč, který lze použít k ověření podpisu tokenu. Middleware také potvrdí, že parametr `iss` v tokenu odpovídá tomuto identifikátoru URI.

Další parametr, `RequireHttpsMetadata`, je užitečný pro účely testování; Nastavte tento parametr na hodnotu false, abyste mohli testovat v prostředích, kde nemáte certifikáty. V reálných nasazeních by se tokeny JWT nosiče měly vždycky předávat jenom přes HTTPS.

Díky tomuto middlewaru jsou tokeny JWT automaticky extrahovány z autorizačních hlaviček. Poté jsou deserializovány, ověřovány (pomocí hodnot v parametrech `Audience` a `Authority`) a uloženy jako informace o uživateli, které budou později odkazovány pomocí akcí MVC nebo filtrů autorizace.

Middleware pro ověření nosiče JWT může také podporovat pokročilejší scénáře, jako je například použití místního certifikátu k ověření tokenu, není-li tato autorita k dispozici. V tomto scénáři můžete zadat objekt `TokenValidationParameters` v objektu `JwtBearerOptions`.

## <a name="additional-resources"></a>Další zdroje

- **Sdílení souborů cookie mezi aplikacemi** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Úvod k identitě** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Dvojúrovňové ověřování pomocí serveru SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Povolení ověřování přes Facebook, Google a další externí poskytovatele** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Úvod k OAuth 2** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **ASPNET. Security. OAuth. Providers** (úložiště GitHub pro poskytovatele OAuth ASP.NET) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **IdentityServer4. Oficiální dokumentace** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Předchozí](../implement-resilient-applications/monitor-app-health.md)
>[Další](authorization-net-microservices-web-applications.md)
