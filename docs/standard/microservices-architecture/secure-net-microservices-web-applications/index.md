---
title: Zabezpečení rozhraní .NET Mikroslužeb a webových aplikací
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Zabezpečení rozhraní .NET Mikroslužeb a webových aplikací
keywords: Docker, Mikroslužeb, ASP.NET, kontejneru
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0ca69ada16fbb5a6757da96a7ea64d2113c15b6f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="securing-net-microservices-and-web-applications"></a>Zabezpečení rozhraní .NET Mikroslužeb a webových aplikací

Často je nutné pro prostředky a rozhraní API vystavené služby omezeny na určité důvěryhodných uživatelů nebo klienti. Prvním krokem k provedení těchto nastavení neovlivní rozhodnutí týkající se rozhraní API úrovně důvěryhodnosti je ověřování. Ověřování je proces spolehlivě zjištění identity uživatele.

Ve scénářích mikroslužbu ověřování je obvykle zpracovávány centrálně. Pokud používáte bránu rozhraní API, brána je vhodná k ověření, jak je znázorněno v obrázek 11-1. Pokud tuto metodu použijte, ujistěte se, že jednotlivé mikroslužeb přímo (bez bránou rozhraní API) není dostupný, není-li zvýšit zabezpečení na místě k ověření zprávy jestli pocházejí z brány nebo ne.

![](./media/image1.png)

**Obrázek 11-1**. Centralizované ověřování s bránu rozhraní API

Je-li služby je přístupná přímo, jako ověřovací služba Azure Active Directory nebo vyhrazené ověřování mikroslužby, který funguje jako zabezpečení služby tokenů (STS) lze použít k ověřování uživatelů. Rozhodnutí o důvěryhodnosti jsou sdíleny mezi službami s tokeny zabezpečení nebo soubory cookie. (To je možné sdílet mezi aplikacemi, v případě potřeby v ASP.NET Core s [služby ochrany dat](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Tento vzor je zobrazená v obrázek 11-2.

![](./media/image2.png)

**Obrázek 11-2**. Ověřování pomocí identity mikroslužbu; vztah důvěryhodnosti se sdílí pomocí autorizační token

## <a name="authenticating-using-aspnet-core-identity"></a>Ověřování pomocí ASP.NET Core Identity

Primární mechanismus v ASP.NET Core identifikace uživatelů aplikace je [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) systému členství. Identitu ASP.NET Core uchovává informace o uživateli (včetně přihlašovací údaje, rolí a deklarací identity) v úložišti dat konfigurovat tak, že vývojář. Úložiště dat ASP.NET Core Identity je obvykle úložišti Entity Framework, který je zahrnutý v balíčku Microsoft.AspNetCore.Identity.EntityFrameworkCore. Ale vlastního úložiště nebo jiné balíčky třetích stran slouží k ukládání informací o identitě Azure Table Storage, DocumentDB nebo jiné umístění.

Následující kód je převzat ze šablony projektu webové aplikace ASP.NET Core s ověřováním účtu jednotlivé uživatele vybrali. Ukazuje, jak nakonfigurovat ASP.NET Identity Core pomocí EntityFramework.Core v metodě Startup.ConfigureServices.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Po nakonfigurování ASP.NET Core Identity povolit volání aplikace. UseIdentity v metodě Startup.Configure služby.

Pomocí Identity kódu ASP.NET umožňuje několika scénářích:

-   Vytvořte nové informace o uživateli pomocí typu objekt UserManager (userManager.CreateAsync).

-   Ověřování uživatelů pomocí SignInManager typu. SignInManager.SignInAsync můžete použít k přihlášení přímo, nebo signInManager.PasswordSignInAsync k potvrzení hesla je správný a potom se přihlaste je.

-   Identifikace uživatele na základě informací v souborech cookie (což je pro čtení middlewarem ASP.NET Core Identity) tak, aby následné žádosti z prohlížeč bude obsahovat identita přihlášeného uživatele a deklarace identity.

Také podporuje ASP.NET Core Identity [dvoufaktorové ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).

Pro scénáře ověřování, které využívají úložiště dat, které místní uživatele a které ukládají identity mezi požadavky pomocí souborů cookie (jako je typický pro webové aplikace MVC), ASP.NET Core Identity je doporučená řešení.

## <a name="authenticating-using-external-providers"></a>Ověřování pomocí externího zprostředkovatele

ASP.NET Core také podporuje používání [externí zprostředkovatelé ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/social/) tak, aby uživatelé přihlásit pomocí [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) toky. To znamená, že uživatelé můžete přihlásit pomocí stávající ověřovací procesy od poskytovatelů, jako je Microsoft, Google, Facebook nebo Twitter a přidružit tyto identity ASP.NET Core identity ve vaší aplikaci.

Chcete-li použít externího ověřování, obsahovat příslušný ověřovací middleware v kanálu zpracování požadavku HTTP vaší aplikace. Tento middleware je zodpovědná za zpracování žádostí se vrátí identifikátor URI trasy ze zprostředkovatele ověřování, zaznamenávání informací o identitě a zpřístupnění prostřednictvím metody SignInManager.GetExternalLoginInfo.

Níže jsou uvedeny oblíbených externí zprostředkovatelé ověřování a jejich přidružené balíčky NuGet.

**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google:** Microsoft.AspNetCore.Authentication.Google

**Facebook:** Microsoft.AspNetCore.Authentication.Facebook

**Twitter:** Microsoft.AspNetCore.Authentication.Twitter

Ve všech případech middleware není zaregistrována volání metody registrace podobné aplikace. V Startup.Configure používejte ověřování {ExternalProvider}. Tyto metody registrace trvat možnosti objekt, který obsahuje ID aplikace a tajné informace (heslo, například), podle potřeby zprostředkovatelem. Externí zprostředkovatelé ověřování vyžadovat pro zaregistrovat (jak je popsáno v [ASP.NET Core dokumentaci](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) tak, aby se může informovat uživatele co aplikace požaduje přístup k svou identitu.

Jakmile middleware je zaregistrován v Startup.Configure, můžete vyzvat uživatele k přihlášení z jakékoli akce kontroleru. K tomuto účelu vytvořte AuthenticationProperties objekt, který obsahuje název zprostředkovatele ověřování a adresu URL pro přesměrování. Odpověď na výzvu, která předá objekt AuthenticationProperties vrátíte. Následující kód ukazuje příklad tohoto objektu.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Parametr redirectUrl obsahuje adresu URL, která by se měla přesměrovat externího poskytovatele, jakmile se uživatel byl ověřen. Adresa URL by měla představovat akci, která budou uživatele přihlásit na základě informací o externí identity, jako v následujícím příkladu zjednodušené:

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

Pokud se rozhodnete **individuální uživatelský účet** možnost ověřování při vytváření projektu webové aplikace ASP.NET kód v sadě Visual Studio, kód nutné se přihlásit pomocí externího poskytovatele je již v projektu, jak je znázorněno 11 obrázek-3.

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

**Obrázek 11-3**. Vyberete možnost použití externího ověřování, při vytváření projektu webové aplikace

Kromě externího ověřování, zprostředkovatelé uvedených výše, balíčky jiných výrobců jsou k dispozici, které poskytují middleware pro použití mnoha více externí zprostředkovatele ověřování. Seznam najdete v tématu [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) úložišti na Githubu.

Samozřejmě, je také možné, vytvořte vlastní middleware externího ověřování.

## <a name="authenticating-with-bearer-tokens"></a>Ověřování pomocí nosných tokenů

Ověřování pomocí ASP.NET Core Identity (nebo identitu a externí zprostředkovatelé ověřování) funguje dobře pro mnoho scénářů webové aplikace, ve kterých je vhodné ukládání informací o uživateli v souboru cookie. V dalších scénářích ale soubory cookie nejsou fyzické prostředky k uchování a přenosu dat.

Například pro ASP.NET Web API Core RESTful koncových bodů, které může získat přístup k jednostránkové aplikace (SPA), která zveřejňuje nativní klienty, nebo i pomocí dalších webových rozhraní API, obvykle je vhodné místo toho použít ověřování tokenu nosiče. Tyto aplikace není pracovat se soubory cookie, ale můžete snadno získat token nosiče a její zahrnutí do hlavičce autorizace následných žádostí. Pokud chcete povolit ověřování tokenem, ASP.NET Core podporuje několik možností pro používání [OAuth 2.0](https://oauth.net/2/) a [OpenID Connect](https://openid.net/connect/).

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>Ověřování pomocí zprostředkovatele OpenID Connect nebo identitu OAuth 2.0

Pokud uživatelské informace uloženy v Azure Active Directory nebo jiné řešení identity, který podporuje OpenID Connect nebo OAuth 2.0, můžete použít balíček Microsoft.AspNetCore.Authentication.OpenIdConnect ověřování pomocí pracovního postupu OpenID Connect. Například pro [ověřování na základě Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), webovou aplikaci ASP.NET Core můžete použít middleware z tohoto balíčku, jak je znázorněno v následujícím příkladu:

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

Hodnoty konfigurace jsou hodnoty Azure Active Directory, které vytvářejí, když je aplikace [registrován jako klient Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad). ID jednoho klienta může být sdílen více mikroslužeb v aplikaci pokud všechny potřebují k ověřování uživatelů, ověření přes Azure Active Directory.

Všimněte si, že pokud použijete tento pracovní postup, middleware ASP.NET Core Identity není nutné, protože zajišťuje všechny informace úložiště uživatele a ověřování přes Azure Active Directory.

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>Vystavování tokenů zabezpečení ze služby ASP.NET Core

Pokud dáváte přednost vystavovat tokeny zabezpečení pro místní uživatele ASP.NET Core Identity místo pomocí zprostředkovatele externí identity, můžete využít některé funkční knihoven třetích stran.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) a [OpenIddict](https://github.com/openiddict/openiddict-core) poskytovatelé OpenID Connect, které se integrují s ASP.NET Identity Core k vám umožní snadno vydávala tokeny zabezpečení ze služby ASP.NET Core. [IdentityServer4 dokumentace](https://identityserver4.readthedocs.io/en/release/) obsahuje podrobné pokyny pro používání knihovny. Základní postup pomocí IdentityServer4 problém tokeny jsou však následujícím způsobem.

1.  Volání aplikace. UseIdentityServer v metodě Startup.Configure přidání IdentityServer4 do kanálu zpracování žádostí HTTP aplikace. To umožňuje knihovně obsluhovat požadavky na koncové body OAuth2 jako /connect/token a OpenID Connect.

2.  Nakonfigurujete IdentityServer4 v Startup.ConfigureServices tím, že zavoláte na služby. AddIdentityServer.

3.  Nakonfigurujete identity server tím, že poskytuje následující data:

-   [Pověření](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) má použít pro podepisování.

-   [Identity a rozhraní API prostředky](https://identityserver4.readthedocs.io/en/release/topics/resources.html) , uživatelé si mohou vyžádat přístup k:

<!-- -->

-   Rozhraní API prostředky představují chráněných dat nebo funkce, které může uživatel získat přístup k tokenu přístupu. Příkladem prostředku, který rozhraní API může být webového rozhraní API (nebo sadu rozhraní API), vyžaduje ověření.

-   Identity prostředky představují informace (deklarace identity), které jsou uvedeny na klienta k identifikaci uživatele. Deklarace identity může zahrnovat uživatelské jméno, e-mailovou adresu a tak dále.

<!-- -->

-   [Klienti](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , budou připojovat k žádosti o tokeny.

-   Mechanismus úložiště pro informace o uživateli, jako například [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) nebo alternativu.

Když zadáte klientů a prostředky pro IdentityServer4 na používání, abyste mohli předávat použití rozhraní IEnumerable&lt;T&gt; kolekce příslušného typu do metod, které berou v paměti klienta nebo prostředků úložiště. Nebo pro složitějšími scénáři, můžete zadat klienta nebo prostředek typy zprostředkovatele pomocí vkládání závislostí.

Ukázková konfigurace pro IdentityServer4 používat prostředky v paměti a klienti poskytované vlastního typu IClientStore může vypadat jako v následujícím příkladu:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>Použití tokenů zabezpečení

Ověřování proti koncový bod OpenID Connect nebo vystavením vlastní tokeny zabezpečení obsahuje některé scénáře. Ale co o službu, která jednoduše omezit přístup na uživatele, kteří mají platný zabezpečení tokeny, které byly poskytovaný jinou službu?

Pro tento scénář je k dispozici v balíčku Microsoft.AspNetCore.Authentication.JwtBearer middleware ověřování, která zpracovává tokeny JWT. JWT znamená "[webových tokenů JSON](https://tools.ietf.org/html/rfc7519)" a je formát common token zabezpečení (definované RFC 7519) pro komunikaci deklarací identity zabezpečení. Jednoduchý příklad toho, jak používat tyto tokeny pomocí middlewaru může vypadat jako v následujícím příkladu. Tento kód musí předcházet volání middleware ASP.NET Core MVC (aplikace. UseMvc).

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

Parametry v toto použití jsou:

-   Cílová skupina představuje příchozím tokenu nebo prostředek, který token uděluje přístup k příjemce. Pokud je hodnota zadaná v tomto parametru neodpovídá parametr oblast v tokenu, budou odmítnuty token.

-   Autorita je adresa serveru vydání tokenu ověřování. Middlewaru ověřování nosiče JWT používá tento identifikátor URI k získání veřejný klíč, který slouží k ověření podpisu tokenu. Middleware také potvrdí, že parametr iss v tokenu odpovídá tento identifikátor URI.

-   AutomaticAuthenticate je logická hodnota, která označuje, zda uživatel definované token by měl být automaticky přihlášeni.

Jiný parametr, RequireHttpsMetadata, se nepoužívá v tomto příkladu. Je vhodné pro testovací účely; Tento parametr nastavíte na hodnotu false, mohli otestovat v prostředích kde nemáte certifikáty. Skutečné nasazení by měl nosné tokeny JWT předat vždy pouze prostřednictvím protokolu HTTPS.

Pomocí tohoto middlewaru v místě tokeny JWT automaticky se extrahují z hlavičky ověření. Jejich jsou poté deserializován, ověřit (pomocí hodnot v parametrech cílovou skupinu a autorita) a ukládají jako informace o uživateli bude odkazovat později akce MVC nebo filtry autorizace.

Middlewaru ověřování nosiče JWT může také podporovat pokročilejší scénáře, jako je třeba použití místní certifikát ověřit token, pokud není k dispozici pro autoritu. V tomto scénáři můžete parametry tokenvalidationparameters objekt v objektu JwtBearerOptions.

## <a name="additional-resources"></a>Další zdroje

-   **Sdílení souborů cookie mezi aplikacemi**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sdílení – ověřování – soubory cookie mezi – aplikace*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Úvod do Identity**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson. Dvoufaktorové ověřování pomocí serveru SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Povolení ověřování pomocí služby Facebook, Google a dalších externích zprostředkovatelů**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas. Úvod do OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (úložiště GitHub zprostředkovatelů ASP.NET OAuth.
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   **Danny Strockis. Integrace Azure AD do webové aplikace ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **IdentityServer4. Oficiální dokumentaci**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)


>[!div class="step-by-step"]
[Předchozí] (.. /Implement-resilient-Applications/monitor-App-Health.MD) [Další] (autorizace net mikroslužeb web-applications.md)
