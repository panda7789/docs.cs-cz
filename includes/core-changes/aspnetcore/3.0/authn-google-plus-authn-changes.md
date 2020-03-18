---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394238"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Ověřování: Google+ se zastaral a nahrazuje

Google začíná [vypínat](https://developers.google.com/+/api-shutdown) Přihlášení google+ pro aplikace již v lednu 28, 2019.

#### <a name="change-description"></a>Popis změny

ASP.NET 4.x a ASP.NET Core používají k ověřování uživatelů účtu Google ve webových aplikacích přihlašovací api služby Google+. Ovlivněné balíčky NuGet jsou [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pro ASP.NET Core a `Microsoft.Owin` [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pro ASP.NET webových formulářů a MVC.

Náhradní api Společnosti Google používají jiný zdroj a formát dat. Níže uvedená opatření ke zmírnění rizik a řešení mj. Aplikace by měly ověřit, že samotná data stále splňují jejich požadavky. Například jména, e-mailové adresy, odkazy na profil a profilové fotografie mohou poskytovat nenápadně odlišné hodnoty než dříve.

#### <a name="version-introduced"></a>Zavedená verze

Všechny verze. Tato změna je externí pro ASP.NET core.

#### <a name="recommended-action"></a>Doporučená akce

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>Owin s ASP.NET webovými formuláři a MVC

Pro `Microsoft.Owin` 3.1.0 a novější je [zde](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)uvedeno dočasné zmírnění . Aplikace by měly dokončit testování s zmírnění mů e-li zkontrolovat změny ve formátu dat. Existují plány `Microsoft.Owin` na vydání 4.0.1 s opravou. Aplikace používající jakoukoli předchozí verzi by se měly aktualizovat na verzi 4.0.1.

##### <a name="aspnet-core-1x"></a>ASP.NET jádro 1.x

Zmírnění v [Owin u ASP.NET Web Forms a MVC](#owin-with-aspnet-web-forms-and-mvc) lze přizpůsobit ASP.NET Core 1.x. Opravy balíčků NuGet nejsou plánovány, protože 1.x dosáhl [stavu konce životnosti.](https://dotnet.microsoft.com/platform/support-policy)

##### <a name="aspnet-core-2x"></a>ASP.NET Jádro 2.x

Pro `Microsoft.AspNetCore.Authentication.Google` verzi 2.x nahraďte `AddGoogle` `Startup.ConfigureServices` stávající volání do aplikace následujícím kódem:

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

Opravy z února 2.1 a 2.2 začlenili předchozí rekonfiguraci jako nové výchozí. Žádná oprava je plánována pro ASP.NET Core 2.0, protože dosáhl [konce životnosti](https://dotnet.microsoft.com/platform/support-policy).

##### <a name="aspnet-core-30"></a>ASP.NET jádro 3.0

Zmírnění uvedené pro ASP.NET Core 2.x lze také použít pro ASP.NET Core 3.0. V budoucích náhledech 3.0 může být `Microsoft.AspNetCore.Authentication.Google` balíček odstraněn. Uživatelé by `Microsoft.AspNetCore.Authentication.OpenIdConnect` místo toho byli přesměrováni. Následující kód ukazuje, `AddGoogle` jak `AddOpenIdConnect` `Startup.ConfigureServices`nahradit v . Tato náhrada může být použita s ASP.NET Core 2.0 a novějším a může být podle potřeby přizpůsobena pro ASP.NET Core 1.x.

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
