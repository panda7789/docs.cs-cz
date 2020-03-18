---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967940"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: Prohlížeč SameSite změny dopad ověřování

Některé prohlížeče, například Chrome a Firefox, provedly `SameSite` v implementaci souborů cookie neaktualizační změny. Změny mají vliv na scénáře vzdáleného ověřování, jako je například OpenID Connect a WS-Federation, které se musí odhlásit odesláním `SameSite=None`. Nicméně, `SameSite=None` přestávky na iOS 12 a některé starší verze jiných prohlížečů. Aplikace musí čichat tyto verze a `SameSite`vynechat .

Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Zavedená verze

3.1 Náhled 1

#### <a name="old-behavior"></a>Staré chování

`SameSite`je 2016 návrh standardní rozšíření http cookies. Je určena ke zmírnění cross-site request padělek (CSRF). To byl původně navržen jako funkce servery by se rozhodnout do přidáním nových parametrů. ASP.NET Core 2.0 přidal `SameSite`počáteční podporu pro .

#### <a name="new-behavior"></a>Nové chování

Google navrhl nový návrh standardu, který není zpětně kompatibilní. Standard změní výchozí režim `Lax` a přidá `None` novou položku, aby se odhlásila. `Lax` stačí pro většinu souborů cookie aplikací; však přeruší scénáře mezi servery, jako je OpenID Connect a WS-Federation přihlášení. Většina přihlášení OAuth nejsou ovlivněny z důvodu rozdílů v tom, jak toky požadavku. Nový `None` parametr způsobuje problémy s kompatibilitou s klienty, kteří implementovali předchozí koncept standardu (například iOS 12). Chrome 80 bude obsahovat změny. Na časové ose spuštění produktu Chrome najdete stránku [Stejné aktualizace webu.](https://www.chromium.org/updates/same-site)

ASP.NET Core 3.1 byla aktualizována `SameSite` implementovat nové chování. `SameSiteMode.None` Aktualizace předefinuje chování vyzařovat `SameSite=None` a přidá novou `SameSiteMode.Unspecified` hodnotu vynechat `SameSite` atribut. Všechna souborová nastavení `Unspecified`cookie jsou nyní ve výchozím nastavení pro , ačkoli některé součásti, které používají soubory cookie, nastavují hodnoty, které jsou konkrétnější pro jejich scénáře, jako je korelace OpenID Connect a soubory cookie nonce.

Další nedávné změny v této oblasti naleznete v tématu [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). V ASP.NET Core 3.0, většina <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> výchozích hodnot byla změněna z (ale stále pomocí předchozího standardu).

#### <a name="reason-for-change"></a>Důvod změny

Změny prohlížeče a specifikace, jak je uvedeno v předchozím textu.

#### <a name="recommended-action"></a>Doporučená akce

Aplikace, které interagují se vzdálenými weby, například prostřednictvím přihlášení třetích stran, musí:

* Otestujte tyto scénáře ve více prohlížečích.
* Použijte cookie zásad prohlížeče sniffing zmírnění popsané v [podpoře starších prohlížečů](#support-older-browsers).

Pokyny pro testování a čichání prohlížeče naleznete v následující části.

##### <a name="determine-if-youre-affected"></a>Zjistěte, zda jste ovlivněni

Otestujte webovou aplikaci pomocí klientské verze, která se může přihlásit k novému chování. Chrome, Firefox a Microsoft Edge Chromium mají nové příznaky funkcí opt-in, které lze použít k testování. Po použití oprav, zejména Safari, ověřte, zda je vaše aplikace kompatibilní se staršími klientskými verzemi. Další informace naleznete v [tématu Podpora starších prohlížečů](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Chrome 78 a novější poskytují zavádějící výsledky testů. Tyto verze mají dočasné zmírnění na místě a umožňují soubory cookie méně než dvě minuty staré. S povolenými testovacími příznaky poskytuje Chrome 76 a 77 přesnější výsledky. Chcete-li otestovat nové `chrome://flags/#same-site-by-default-cookies` chování, přepněte na povoleno. Chrome 75 a starší jsou hlášeny `None` selhání s novým nastavením. Další informace naleznete v [tématu Podpora starších prohlížečů](#support-older-browsers).

Google nezpřístupní starší verze Chromu. Můžete si však stáhnout starší verze chromu, které budou stačit pro testování. Postupujte podle pokynů na [download chrom .](https://www.chromium.org/getting-involved/download-chromium)

* [Chrom 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chrom 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 přísně implementoval předchozí návrh a `None` selže, pokud vidí novou hodnotu v cookies. Tomu je třeba se vyhnout prostřednictvím prohlížeče čichání kód je uvedeno v [podpoře starších prohlížečů](#support-older-browsers). Ujistěte se, že testujete Safari 12 a 13, stejně jako přihlášení ve stylu operačního systému WebKit pomocí Knihovny ověřování Microsoft (MSAL), Knihovny ověřování služby Active Directory (ADAL) nebo knihovny, kterou používáte. Problém je závislý na základní verzi operačního systému. OsX Mojave 10.14 a iOS 12 je známo, že problémy s kompatibilitou s novým chováním. Upgrade na OSX Catalina 10.15 nebo iOS 13 řeší problém. Safari nemá v současné době příznak pro přihlášení pro testování chování nové specifikace.

##### <a name="firefox"></a>Firefox

Firefox podporu pro nový standard lze testovat na verzi 68 a `about:config` později se `network.cookie.sameSite.laxByDefault`přihlásili na stránce s funkcí příznakem . U starších verzí Firefoxu nebyly hlášeny žádné problémy s kompatibilitou.

##### <a name="microsoft-edge"></a>Microsoft Edge

Zatímco Microsoft Edge `SameSite` podporuje starý standard, od verze 44 neměl žádné problémy s kompatibilitou s novým standardem.

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge Chromium

Příznak funkce `edge://flags/#same-site-by-default-cookies`je . Při testování pomocí microsoft edge chromu 78 nebyly pozorovány žádné problémy s kompatibilitou.

##### <a name="electron"></a>Elektronová

Verze Electronu obsahují starší verze chromu. Například verze Electron používá Microsoft Teams je Chromium 66, který vykazuje starší chování. Proveďte vlastní testování kompatibility s verzí Electron, kterou váš produkt používá. Další informace naleznete v [tématu Podpora starších prohlížečů](#support-older-browsers).

##### <a name="support-older-browsers"></a>Podpora starších prohlížečů

Norma z roku `SameSite` 2016 stanovila, `SameSite=Strict` že s neznámými hodnotami se zachází jako s hodnotami. V důsledku toho všechny starší prohlížeče, které podporují původní `SameSite` standard může `None`přerušit, když vidí vlastnost s hodnotou . Webové aplikace musí implementovat procházení prohlížeče, pokud mají v úmyslu podporovat tyto staré prohlížeče. ASP.NET Core neimplementuje prohlížeč sniffing pro vás, protože `User-Agent` hodnoty záhlaví požadavku jsou vysoce nestabilní a měnit na týdenní bázi. Místo toho bod rozšíření v zásadách `User-Agent`souborů cookie umožňuje přidat -specifickou logiku.

V *Startup.cs*přidejte následující kód:

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

##### <a name="opt-out-switches"></a>Odhlášení

Přepínač `Microsoft.AspNetCore.SuppressSameSiteNone` kompatibility umožňuje dočasně odhlásit z nového ASP.NET chování souborů cookie Core. Přidejte následující json do souboru *runtimeconfig.template.json* v projektu:

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Jiné verze

Související `SameSite` záplaty jsou připravovány pro:

* ASP.NET jádra 2.1, 2.2 a 3.0
* `Microsoft.Owin`4.1
* `System.Web`(pro rozhraní .NET Framework 4.7.2 a novější)

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
