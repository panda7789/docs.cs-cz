---
title: Zabezpečení mikroslužeb a webových aplikací .NET
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – seznamte se s možnostmi ověřování v ASP.NET základních webových aplikacích.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 56ebd95c8a24c7c8d30d3c6acef6650cb63383c6
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988112"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Zabezpečení mikroslužeb a webových aplikací .NET

Existuje tolik aspektů o zabezpečení v mikroslužbách a webových aplikacích, že téma může snadno trvat několik knih, jako je tento, takže v této části se zaměříme na ověřování, autorizaci a tajné kódy aplikací.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementace ověřování v mikroslužbách a webových aplikacích rozhraní .NET

Často je nutné, aby prostředky a api publikovaná službou byly omezeny na určité důvěryhodné uživatele nebo klienty. Prvním krokem k provedení těchto druhů rozhodnutí o důvěryhodnosti na úrovni rozhraní API je ověřování. Ověřování je proces spolehlivého ověření identity uživatele.

Ve scénářích mikroslužeb ověřování se obvykle zpracovává centrálně. Pokud používáte bránu rozhraní API, brána je vhodné místo k ověření, jak je znázorněno na obrázku 9-1. Pokud použijete tento přístup, ujistěte se, že jednotlivé mikroslužeb nelze dosáhnout přímo (bez brány rozhraní API), pokud je další zabezpečení na místě k ověření zprávy, zda pocházejí z brány nebo ne.

![Diagram znázorňující interakci klientské mobilní aplikace s back-endem.](./media/index/api-gateway-centralized-authentication.png)

**Obrázek 9-1**. Centralizované ověřování pomocí brány rozhraní API

Když brána rozhraní API centralizuje ověřování, přidá informace o uživateli při předávání požadavků mikroslužbám. Pokud ke službám lze přistupovat přímo, lze k ověření uživatelů použít ověřovací službu, jako je Azure Active Directory nebo vyhrazená mikroslužba pro ověřování, která funguje jako služba tokenů zabezpečení (STS). Rozhodnutí o důvěryhodnosti jsou sdílena mezi službami pomocí tokenů zabezpečení nebo souborů cookie. (Tyto tokeny lze v případě potřeby sdílet mezi aplikacemi ASP.NET Core implementací [sdílení souborů cookie](/aspnet/core/security/cookie-sharing).) Tento vzor je znázorněn na obrázku 9-2.

![Diagram zobrazující ověřování prostřednictvím back-endových mikroslužeb.](./media/index/identity-microservice-authentication.png)

**Obrázek 9-2**. Ověřování pomocí mikroslužby identity; vztah důvěryhodnosti je sdílen pomocí autorizačního tokenu

Při přístupu k mikroslužbám přímo, vztah důvěryhodnosti, který zahrnuje ověřování a autorizaci, je zpracován tokenem zabezpečení vydaným vyhrazenou mikroslužbou sdílenou mezi mikroslužbami.

### <a name="authenticate-with-aspnet-core-identity"></a>Ověření pomocí ASP.NET základní identity

Primární mechanismus v ASP.NET Core pro identifikaci uživatelů aplikace je ASP.NET systém členství [základní identity.](/aspnet/core/security/authentication/identity) ASP.NET Core Identity ukládá informace o uživateli (včetně přihlašovacích informací, rolí a deklarací) v úložišti dat nakonfigurovaném vývojářem. Úložiště dat ASP.NET základní identity je obvykle úložiště entity `Microsoft.AspNetCore.Identity.EntityFrameworkCore` framework poskytované v balíčku. Vlastní úložiště nebo jiné balíčky třetích stran však lze použít k ukládání informací o identitě v Azure Table Storage, CosmosDB nebo jiných umístěních.

> [!TIP]
> ASP.NET Core 2.1 a novější poskytuje [ASP.NET základní identity](/aspnet/core/security/authentication/identity) jako [knihovny tříd razor](/aspnet/core/razor-pages/ui-class), takže neuvidíte mnoho potřebného kódu v projektu, jako tomu bylo v případě předchozích verzí. Podrobnosti o tom, jak přizpůsobit kód identity tak, aby vyhovoval vašim potřebám, naleznete v tématu [Identita lešení v ASP.NET základní projekty](/aspnet/core/security/authentication/scaffold-identity).

Následující kód je převzat z ASP.NET základní webové aplikace MVC 3.1 šablony projektu s individuální ověřování uživatelských účtů. Ukazuje, jak nakonfigurovat ASP.NET základní identity `Startup.ConfigureServices` pomocí entity framework core v metodě.

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

Jakmile je ASP.NET základní identity nakonfigurován, `app.UseAuthentication()` `endpoints.MapRazorPages()` povolte ji přidáním a jak `Startup.Configure` je znázorněno v následujícím kódu v metodě služby:

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
> Řádky v předčíslí kód **musí být v pořadí zobrazeno** pro identitu pracovat správně.

Použití ASP.NET základní identity umožňuje několik scénářů:

- Vytvořte nové informace o uživateli pomocí typu UserManager (userManager.CreateAsync).

- Ověřujte uživatele pomocí typu SignInManager. Můžete použít `signInManager.SignInAsync` k přihlášení přímo, nebo `signInManager.PasswordSignInAsync` potvrdit heslo uživatele je správné a potom je přihlásit.

- Identifikujte uživatele na základě informací uložených v souboru cookie (který je čten ASP.NET middleware Core Identity), takže následné požadavky z prohlížeče budou obsahovat identitu a deklarace identity přihlášeného uživatele.

ASP.NET Core Identity také podporuje [dvoufaktorové ověřování](/aspnet/core/security/authentication/2fa).

Pro scénáře ověřování, které využívají úložiště místních uživatelských dat a které přetrvávají identitu mezi požadavky pomocí souborů cookie (jak je typické pro webové aplikace MVC), ASP.NET core identity je doporučené řešení.

### <a name="authenticate-with-external-providers"></a>Ověření u externích zprostředkovatelů

ASP.NET Core také podporuje použití [externích poskytovatelů ověřování,](/aspnet/core/security/authentication/social/) aby uživatelé přihlášení prostřednictvím [Toků OAuth 2.0.](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) To znamená, že se uživatelé mohou přihlásit pomocí stávajících ověřovacích procesů od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter, a přidružit tyto identity k ASP.NET základní identity ve vaší aplikaci.

Chcete-li použít externí ověřování, kromě včetně ověřování middleware, jak je uvedeno dříve, pomocí `app.UseAuthentication()` metody, musíte také zaregistrovat externího zprostředkovatele v, `Startup` jak je znázorněno v následujícím příkladu:

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

Populární externí poskytovatelé ověřování a jejich přidružené balíčky NuGet jsou uvedeny v následující tabulce:

| **Poskytovatel**  | **Balíček**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Účet Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

Ve všech případech je nutné provést postup registrace přihlášky, který je závislý na dodavateli a který obvykle zahrnuje:

1. Získání ID klientské aplikace.
2. Získání tajného klíče klientské aplikace.
3. Konfigurace adresy URL přesměrování, která je zpracována middlewarem autorizace a registrovaným poskytovatelem
4. Volitelně konfigurace přihlašovací adresy URL pro správné zpracování odhlásit ve scénáři jednotného přihlášení (SSO).

Podrobnosti o konfiguraci aplikace pro externího zprostředkovatele najdete [v tématu ověřování externího zprostředkovatele v dokumentaci ASP.NET Core](/aspnet/core/security/authentication/social/)).

>[!TIP]
>Všechny podrobnosti jsou zpracovány autorizace middleware a služby výše uvedené. Takže stačí zvolit možnost ověřování **individuálního uživatelského účtu** při vytváření projektu webové aplikace ASP.NET code v sadě Visual Studio, jak je znázorněno na obrázku 9-3, kromě registrace poskytovatelů ověřování, které byly zmíněny.

![Snímek obrazovky s dialogovým oknem Nová ASP.NET základní webová aplikace](./media/index/select-individual-user-account-authentication-option.png)

**Obrázek 9-3**. Výběr možnosti Jednotlivé uživatelské účty pro použití externího ověřování při vytváření projektu webové aplikace v Sadě Visual Studio 2019.

Kromě dříve uvedených externích poskytovatelů ověřování jsou k dispozici balíčky třetích stran, které poskytují middleware pro použití mnoha dalších externích poskytovatelů ověřování. Seznam najdete v úložišti [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) na GitHubu.

Můžete také vytvořit vlastní externí ověřování middleware vyřešit některé zvláštní potřeby.

### <a name="authenticate-with-bearer-tokens"></a>Ověření pomocí nosné tokeny

Ověřování pomocí ASP.NET základní identity (nebo identity plus externích poskytovatelů ověřování) funguje dobře pro mnoho scénářů webových aplikací, ve kterých je vhodné ukládání informací o uživateli v souboru cookie. V jiných scénářích však soubory cookie nejsou přirozeným prostředkem k uchování a přenosu dat.

Například v ASP.NET základní webové rozhraní API, které zpřístupňuje koncové body RESTful, ke kterým mohou přistupovat aplikace s jednou stránkou (SPA), nativní klienti nebo dokonce jinými webovými rozhraními API, obvykle chcete místo toho použít ověřování tokenu nosiče. Tyto typy aplikací nefungují se soubory cookie, ale mohou snadno načíst token nosiče a zahrnout jej do hlavičky autorizace následných požadavků. Chcete-li povolit ověřování tokenů, ASP.NET Core podporuje několik možností pro použití [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Ověření pomocí poskytovatele identity OpenID Connect nebo OAuth 2.0

Pokud jsou informace o uživateli uložené ve službě Azure Active Directory nebo v jiném řešení identity, které podporuje OpenID Connect nebo OAuth 2.0, můžete použít balíček **Microsoft.AspNetCore.Authentication.OpenIdConnect** k ověření pomocí pracovního postupu OpenID Connect. Například k ověření na Identity.Api mikroslužby v eShopOnContainers, ASP.NET základní webové aplikace můžete použít middleware `Startup.cs`z tohoto balíčku, jak je znázorněno v následujícím zjednodušeném příkladu v :

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

Všimněte si, že při použití tohoto pracovního postupu middleware ASP.NET core identity není potřeba, protože všechny úložiště informací o uživateli a ověřování je zpracována službou Identity.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Vydávání tokenů zabezpečení ze služby ASP.NET Core

Pokud dáváte přednost vydávání tokenů zabezpečení pro místní ASP.NET uživatele základní identity, než pomocí externího zprostředkovatele identity, můžete využít některé dobré knihovny třetích stran.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) jsou poskytovatelé OpenID Connect, kteří se snadno integrují s ASP.NET základní identitou, aby vám dovolili vydávat tokeny zabezpečení ze služby ASP.NET Core. Dokumentace [identityServer4](https://identityserver4.readthedocs.io/en/latest/) obsahuje podrobné pokyny pro použití knihovny. Základní kroky k použití IdentityServer4 k vydávání tokenů jsou však následující.

1. Voláš do aplikace. UseIdentityServer v metodě Startup.Configure pro přidání identityServer4 do kanálu zpracování požadavků HTTP aplikace. To umožňuje knihovně obsluhovat požadavky na koncové body OpenID Connect a OAuth2 jako /connect/token.

2. Server IdentityServer4 nakonfigurujete při spuštění.ConfigureServices voláním služeb. AddIdentityServer.

3. Server identit nakonfigurujete nastavením následujících dat:

   - [Pověření, která](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) chcete použít k podepisování.

   - Prostředky [identity a rozhraní API,](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) ke kterým mohou uživatelé požadovat přístup:

      - Prostředky rozhraní API představují chráněná data nebo funkce, ke kterým má uživatel přístup pomocí přístupového tokenu. Příkladem prostředku rozhraní API by bylo webové rozhraní API (nebo sada rozhraní API), které vyžaduje autorizaci.

      - Prostředky identity představují informace (deklarace), které jsou dány klientovi k identifikaci uživatele. Deklarace identity mohou zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.

   - [Klienti,](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) kteří se budou připojovat, aby mohli požadovat tokeny.

   - Mechanismus úložiště pro informace o uživateli, jako je [například ASP.NET základní identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) nebo alternativu.

Když zadáte klienty a prostředky pro IdentityServer4 <xref:System.Collections.Generic.IEnumerable%601> použít, můžete předat kolekci příslušného typu metody, které se v paměti klienta nebo úložiště prostředků. Nebo pro složitější scénáře můžete poskytnout typy klienta nebo zprostředkovatele prostředků prostřednictvím vkládání závislostí.

Ukázková konfigurace pro IdentityServer4 pro použití prostředků v paměti a klientů poskytovaných vlastním typem IClientStore může vypadat jako v následujícím příkladu:

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

### <a name="consume-security-tokens"></a>Využití tokenů zabezpečení

Ověřování podle koncového bodu OpenID Connect nebo vydávání vlastních tokenů zabezpečení zahrnuje některé scénáře. Ale co služba, která prostě potřebuje omezit přístup k těm uživatelům, kteří mají platné tokeny zabezpečení, které byly poskytnuty jinou službou?

Pro tento scénář je middleware ověřování, který zpracovává tokeny JWT, k dispozici v balíčku **Microsoft.AspNetCore.Authentication.JwtBearer.** JWT je zkratka pro "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" a je společný formát tokenu zabezpečení (definovaný RFC 7519) pro komunikaci deklarací zabezpečení. Zjednodušený příklad použití middleware ke spotřebovávat tyto tokeny může vypadat jako tento fragment kódu, převzato z Ordering.Api mikroslužby eShopOnContainers.

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

Parametry v tomto použití jsou:

- `Audience`představuje příjemce příchozí token nebo prostředek, který uděluje přístup tokenu. Pokud hodnota zadaná v tomto parametru neodpovídá parametru v tokenu, token bude odmítnut.

- `Authority`je adresa ověřovacího serveru vydávajícího tokeny. Middleware pro ověřování nosiče JWT používá tento identifikátor URI k získání veřejného klíče, který lze použít k ověření podpisu tokenu. Middleware také potvrzuje, `iss` že parametr v tokenu odpovídá této uri.

Další parametr `RequireHttpsMetadata`, je užitečné pro účely testování; nastavíte tento parametr na hodnotu false, takže můžete testovat v prostředích, kde nemáte certifikáty. V reálném nasazení JWT nosné tokeny by měly být vždy předány pouze přes HTTPS.

S tímto middleware na místě, JWT tokeny jsou automaticky extrahovány z autorizace záhlaví. Poté jsou deserializovány, ověřeny (pomocí `Audience` `Authority` hodnot v parametrech a) a uloženy jako informace o uživateli, na které budou později odkazovat akce MVC nebo filtry autorizace.

Middleware ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je například použití místního certifikátu k ověření tokenu, pokud autorita není k dispozici. V tomto scénáři můžete `TokenValidationParameters` zadat `JwtBearerOptions` objekt v objektu.

## <a name="additional-resources"></a>Další zdroje

- **Sdílení souborů cookie mezi aplikacemi** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Úvod do identity** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Dvoufaktorové ověřování pomocí SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Povolení ověřování pomocí Facebooku, Googlu a dalších externích poskytovatelů** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Úvod do OAuth 2** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **AspNet.Security.OAuth.Providers** (Úložiště GitHub pro ASP.NET zprostředkovatelů OAuth) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **IdentityServer4. Oficiální dokumentace** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Předchozí](../implement-resilient-applications/monitor-app-health.md)
>[další](authorization-net-microservices-web-applications.md)
