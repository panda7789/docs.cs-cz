---
ms.openlocfilehash: 02602c70689a6d2729e03d3d7230cda5ae7a4994
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901883"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: Browser SameSite změny dopadu na ověření

Některé prohlížeče, jako je například Chrome a Firefox, provedly zásadní změny jejich implementace `SameSite` pro soubory cookie. Změny mají vliv na scénáře vzdáleného ověřování, například OpenID Connect a WS-Federation, které se musí odhlásit odesláním `SameSite=None`. Nicméně `SameSite=None` přerušují iOS 12 a některé starší verze jiných prohlížečů. Aplikace potřebuje tyto verze zachytit a vypustit `SameSite`.

Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Představená verze

3,1 Preview 1

#### <a name="old-behavior"></a>Staré chování

`SameSite` je 2016 koncept standardního rozšíření pro soubory cookie HTTP. Slouží ke zmírnění omezení padělání žádostí mezi weby (CSRF). Tato možnost byla původně navržena jako funkce, které by servery mohly vyjádřit přidáním nových parametrů. ASP.NET Core 2,0 byla přidána počáteční podpora pro `SameSite`.

#### <a name="new-behavior"></a>Nové chování

Společnost Google navrhla nový koncept Standard, který není zpětně kompatibilní. Standard změní výchozí režim na `Lax` a přidá novou položku `None` k odhlášení. pro většinu souborů cookie aplikace postačuje `Lax`. dojde ale k přerušení scénářů mezi lokalitami, jako je OpenID Connect a přihlášení ke službě WS-Federation. Většina přihlášení OAuth není ovlivněná kvůli rozdílům ve způsobu, jakým jsou požadavky v toku. Nový parametr `None` způsobuje problémy s kompatibilitou s klienty, kteří implementovali předchozí koncept Standard (například iOS 12). Chrome 80 bude obsahovat změny. Podívejte se na [SameSite aktualizace](https://www.chromium.org/updates/same-site) pro časovou osu spuštění produktu Chrome.

ASP.NET Core 3,1 byl aktualizován, aby implementoval nové chování `SameSite`. Aktualizace předefinuje chování `SameSiteMode.None` k vygenerování `SameSite=None` a přidá novou hodnotu `SameSiteMode.Unspecified` pro vynechání atributu `SameSite`. Všechna rozhraní API souborů cookie teď `Unspecified`výchozí, i když některé komponenty, které používají soubory cookie, nastavily hodnoty lépe specifické pro jejich scénáře, jako je například korelace OpenID Connect a soubory nonce.

Další nedávné změny v této oblasti najdete v tématu [http: některé výchozí hodnoty SameSite souborů cookie se změnily na žádné](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). V ASP.NET Core 3,0 se většina výchozích hodnot změnila z <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> na <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (ale pořád se používá předchozí Standard).

#### <a name="reason-for-change"></a>Důvod změny

Změny v prohlížeči a specifikaci, jak je uvedeno v předchozím textu.

#### <a name="recommended-action"></a>Doporučená akce

Aplikace, které komunikují se vzdálenými lokalitami, například prostřednictvím přihlášení třetí strany, potřebují:

* Otestujte tyto scénáře ve více prohlížečích.
* Použijte zásady souborů cookie v prohlížeči zásady zmírnění rizika popsané v tématu [Podpora starších prohlížečů](#support-older-browsers).

Pokyny k testování a sledování v prohlížeči najdete v následující části.

##### <a name="determine-if-youre-affected"></a>Určení, jestli jste to ovlivnili

Otestujte webovou aplikaci pomocí verze klienta, která se může přihlásit k novému chování. Pro Chrome, Firefox a Microsoft Edge chrom existují nové příznaky funkcí pro výslovný souhlas, které lze použít k testování. Ověřte, jestli je vaše aplikace kompatibilní se staršími verzemi klientů, i když jste použili opravy, zejména Safari. Další informace najdete v tématu [Podpora starších prohlížečů](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Chrome 78 a novější je výsledkem zavádějících výsledků testů. Tyto verze mají dočasné omezení na místě a umožňují, aby soubory cookie byly starší než dvě minuty. S povolenými příznakem testu jsou k dispozici přesnější výsledky Chrome 76 a 77. Chcete-li otestovat nové chování, přepněte `chrome://flags/#same-site-by-default-cookies` na povoleno. Rozhraní Chrome 75 a starší se hlásí jako neúspěšná s nastavením nového `None`. Další informace najdete v tématu [Podpora starších prohlížečů](#support-older-browsers).

Google nezpřístupňuje starší verze Chrome. Můžete si však stáhnout starší verze Chromu, které budou postačovat pro testování. Postupujte podle pokynů na [webu Stažení Chromu](https://www.chromium.org/getting-involved/download-chromium).

* [Chróm 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chróm 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Prohlížeč Safari 12 striktně implementuje předchozí koncept a v případě, že se v souborech cookie zobrazí nová hodnota `None`, se nezdařila. K tomu je potřeba se vyhnout prostřednictvím kódu sledování prohlížeče, který je uvedený v části [Podpora starších prohlížečů](#support-older-browsers). Ujistěte se, že otestujete prohlížeč Safari 12 a 13, stejně jako WebKit, přihlášení pomocí knihovny Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL) nebo libovolnou knihovnu, kterou používáte. Problém závisí na základní verzi operačního systému. OSX Mojave 10,14 a iOS 12 se nazývají problémy s kompatibilitou s novým chováním. Při upgradu na OSX Catalina 10,15 nebo iOS 13 se problém vyřeší. Prohlížeč Safari nemá v současné době příznak výslovného souhlasu pro testování nového chování specifikace.

##### <a name="firefox"></a>Firefox

Podporu aplikace Firefox pro nový standard lze otestovat na verzi 68 a novější, a to tak, že na stránce `about:config` `network.cookie.sameSite.laxByDefault`příznak funkce. Ve starších verzích prohlížeče Firefox nebyly hlášeny žádné problémy s kompatibilitou.

##### <a name="microsoft-edge"></a>Microsoft Edge

Zatímco Microsoft Edge podporuje starý `SameSite` Standard, od verze 44 nemá žádné problémy s kompatibilitou s novým standardem.

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge chrom

Příznak funkce je `edge://flags/#same-site-by-default-cookies`. Při testování s Microsoft Edge chrom 78 nebyly pozorovány žádné problémy s kompatibilitou.

##### <a name="electron"></a>Chyt

K verzím elektronů patří starší verze Chromu. Například verze elektronicky používaného Microsoft Teams je chrom 66, který vykazuje starší chování. Proveďte vlastní testování kompatibility s verzí elektronů, kterou váš produkt používá. Další informace najdete v tématu [Podpora starších prohlížečů](#support-older-browsers).

##### <a name="support-older-browsers"></a>Podpora starších prohlížečů

2016 `SameSite` standardně posuzuje, že neznámé hodnoty se budou považovat za `SameSite=Strict` hodnoty. V důsledku toho se všechny starší prohlížeče, které podporují původní standard, mohou přerušit, když uvidí vlastnost `SameSite` s hodnotou `None`. Pokud mají uživatelé v úmyslu podporovat tyto staré prohlížeče, musí webové aplikace implementovat monitorování v prohlížeči. ASP.NET Core neimplementuje pro vás monitorování, protože `User-Agent` hodnoty hlaviček žádostí jsou vysoce nestabilní a každý týden se mění. Místo toho vám rozšiřující bod v zásadách souborů cookie umožňuje přidat logiku specifickou pro `User-Agent`.

Do *Startup.cs*přidejte následující kód:

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None) 
    { 
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here. 
        if (/* UserAgent doesn't support new behavior */) 
        { 
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services) 
{ 
    services.Configure<CookiePolicyOptions>(options => 
    { 
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    }); 
} 

public void Configure(IApplicationBuilder app) 
{ 
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication(); 
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a>Přepínače pro výslovný souhlas

Přepínač kompatibility `Microsoft.AspNetCore.SuppressSameSiteNone` umožňuje dočasně odhlásit nové chování souborů cookie ASP.NET Core. Do souboru *runtimeconfig. template. JSON* v projektu přidejte následující JSON:

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a>Jiné verze

Související opravy `SameSite` jsou pro:

* ASP.NET Core 2,1, 2,2 a 3,0
* `Microsoft.Owin` 4,1
* `System.Web` (pro .NET Framework 4.7.2 a novější)

#### <a name="category"></a>Kategorie

ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
