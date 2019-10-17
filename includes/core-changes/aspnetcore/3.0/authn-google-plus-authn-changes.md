---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394238"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Ověřování: Google + zastaralé a nahrazené

Google se zahájí [vypnutí](https://developers.google.com/+/api-shutdown) služby Google + Sign-in pro aplikace hned po 28. lednu 2019.

#### <a name="change-description"></a>Změnit popis

ASP.NET 4. x a ASP.NET Core používaly rozhraní API pro přihlašování Google + k ověřování uživatelů účtu Google ve službě Web Apps. Ovlivněné balíčky NuGet jsou [Microsoft. AspNetCore. Authentication. Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pro ASP.NET Core a [Microsoft. Owin. Security. Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pro `Microsoft.Owin` s ASP.NET webovými formuláři a MVC.

Rozhraní API pro nahrazení Google používají jiný zdroj dat a formát. Rizika a řešení uvedená níže jsou k dispozici pro strukturální změny. Aplikace by měly ověřit, že samotná data stále splňují jejich požadavky. Například názvy, e-mailové adresy, odkazy na profily a profily profilů můžou poskytovat nepřesné odlišné hodnoty.

#### <a name="version-introduced"></a>Představená verze

Všechny verze. Tato změna je externě ASP.NET Core.

#### <a name="recommended-action"></a>Doporučená akce

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>Owin s webovými formuláři ASP.NET a MVC

V případě `Microsoft.Owin` 3.1.0 a novějšího je [zde](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)popsaný dočasný dopad. Aplikace by měly dokončit testování s rizikem, aby kontrolovaly změny ve formátu dat. K dispozici jsou plány pro vydání `Microsoft.Owin` 4.0.1 s opravou. Aplikace používající jakoukoli předchozí verzi by se měly aktualizovat na verzi 4.0.1.

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1. x

Zmírnění rizika v [Owin s webovými formuláři ASP.NET a MVC](#owin-with-aspnet-web-forms-and-mvc) se dá přizpůsobit ASP.NET Core 1. x. Opravy balíčků NuGet nejsou plánované, protože 1. x dosáhlo stavu [konce životnosti](https://dotnet.microsoft.com/platform/support-policy) .

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2. x

U `Microsoft.AspNetCore.Authentication.Google` verze 2. x nahraďte existující volání `AddGoogle` v `Startup.ConfigureServices` následujícím kódem:

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

Opravy z února 2,1 a 2,2 zahrnovaly předchozí znovu konfiguraci jako nové výchozí nastavení. Pro ASP.NET Core 2,0 není plánována žádná oprava, protože dosáhla [konce životnosti](https://dotnet.microsoft.com/platform/support-policy).

##### <a name="aspnet-core-30"></a>ASP.NET Core 3,0

Zmírnění rizika poskytnutého ASP.NET Core 2. x se dá použít i pro ASP.NET Core 3,0. V budoucích verzích 3,0 verze Preview může být balíček `Microsoft.AspNetCore.Authentication.Google` odebraný. Místo toho budou uživatelé přesměrováni na `Microsoft.AspNetCore.Authentication.OpenIdConnect`. Následující kód ukazuje, jak nahradit `AddGoogle` s `AddOpenIdConnect` v `Startup.ConfigureServices`. Tato náhrada se dá použít s ASP.NET Core 2,0 a novějším a dá se podle potřeby přizpůsobit pro ASP.NET Core 1. x.

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

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
