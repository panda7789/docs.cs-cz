---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967940"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="0c955-101">HTTP: Prohlížeč SameSite změny dopad ověřování</span><span class="sxs-lookup"><span data-stu-id="0c955-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="0c955-102">Některé prohlížeče, například Chrome a Firefox, provedly `SameSite` v implementaci souborů cookie neaktualizační změny.</span><span class="sxs-lookup"><span data-stu-id="0c955-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="0c955-103">Změny mají vliv na scénáře vzdáleného ověřování, jako je například OpenID Connect a WS-Federation, které se musí odhlásit odesláním `SameSite=None`.</span><span class="sxs-lookup"><span data-stu-id="0c955-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="0c955-104">Nicméně, `SameSite=None` přestávky na iOS 12 a některé starší verze jiných prohlížečů.</span><span class="sxs-lookup"><span data-stu-id="0c955-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="0c955-105">Aplikace musí čichat tyto verze a `SameSite`vynechat .</span><span class="sxs-lookup"><span data-stu-id="0c955-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="0c955-106">Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="0c955-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0c955-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0c955-107">Version introduced</span></span>

<span data-ttu-id="0c955-108">3.1 Náhled 1</span><span class="sxs-lookup"><span data-stu-id="0c955-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0c955-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0c955-109">Old behavior</span></span>

<span data-ttu-id="0c955-110">`SameSite`je 2016 návrh standardní rozšíření http cookies.</span><span class="sxs-lookup"><span data-stu-id="0c955-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="0c955-111">Je určena ke zmírnění cross-site request padělek (CSRF).</span><span class="sxs-lookup"><span data-stu-id="0c955-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="0c955-112">To byl původně navržen jako funkce servery by se rozhodnout do přidáním nových parametrů.</span><span class="sxs-lookup"><span data-stu-id="0c955-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="0c955-113">ASP.NET Core 2.0 přidal `SameSite`počáteční podporu pro .</span><span class="sxs-lookup"><span data-stu-id="0c955-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0c955-114">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0c955-114">New behavior</span></span>

<span data-ttu-id="0c955-115">Google navrhl nový návrh standardu, který není zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="0c955-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="0c955-116">Standard změní výchozí režim `Lax` a přidá `None` novou položku, aby se odhlásila. `Lax` stačí pro většinu souborů cookie aplikací; však přeruší scénáře mezi servery, jako je OpenID Connect a WS-Federation přihlášení.</span><span class="sxs-lookup"><span data-stu-id="0c955-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="0c955-117">Většina přihlášení OAuth nejsou ovlivněny z důvodu rozdílů v tom, jak toky požadavku.</span><span class="sxs-lookup"><span data-stu-id="0c955-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="0c955-118">Nový `None` parametr způsobuje problémy s kompatibilitou s klienty, kteří implementovali předchozí koncept standardu (například iOS 12).</span><span class="sxs-lookup"><span data-stu-id="0c955-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="0c955-119">Chrome 80 bude obsahovat změny.</span><span class="sxs-lookup"><span data-stu-id="0c955-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="0c955-120">Na časové ose spuštění produktu Chrome najdete stránku [Stejné aktualizace webu.](https://www.chromium.org/updates/same-site)</span><span class="sxs-lookup"><span data-stu-id="0c955-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="0c955-121">ASP.NET Core 3.1 byla aktualizována `SameSite` implementovat nové chování.</span><span class="sxs-lookup"><span data-stu-id="0c955-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="0c955-122">`SameSiteMode.None` Aktualizace předefinuje chování vyzařovat `SameSite=None` a přidá novou `SameSiteMode.Unspecified` hodnotu vynechat `SameSite` atribut.</span><span class="sxs-lookup"><span data-stu-id="0c955-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="0c955-123">Všechna souborová nastavení `Unspecified`cookie jsou nyní ve výchozím nastavení pro , ačkoli některé součásti, které používají soubory cookie, nastavují hodnoty, které jsou konkrétnější pro jejich scénáře, jako je korelace OpenID Connect a soubory cookie nonce.</span><span class="sxs-lookup"><span data-stu-id="0c955-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="0c955-124">Další nedávné změny v této oblasti naleznete v tématu [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="0c955-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="0c955-125">V ASP.NET Core 3.0, většina <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> výchozích hodnot byla změněna z (ale stále pomocí předchozího standardu).</span><span class="sxs-lookup"><span data-stu-id="0c955-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0c955-126">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0c955-126">Reason for change</span></span>

<span data-ttu-id="0c955-127">Změny prohlížeče a specifikace, jak je uvedeno v předchozím textu.</span><span class="sxs-lookup"><span data-stu-id="0c955-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0c955-128">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0c955-128">Recommended action</span></span>

<span data-ttu-id="0c955-129">Aplikace, které interagují se vzdálenými weby, například prostřednictvím přihlášení třetích stran, musí:</span><span class="sxs-lookup"><span data-stu-id="0c955-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="0c955-130">Otestujte tyto scénáře ve více prohlížečích.</span><span class="sxs-lookup"><span data-stu-id="0c955-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="0c955-131">Použijte cookie zásad prohlížeče sniffing zmírnění popsané v [podpoře starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="0c955-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="0c955-132">Pokyny pro testování a čichání prohlížeče naleznete v následující části.</span><span class="sxs-lookup"><span data-stu-id="0c955-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="0c955-133">Zjistěte, zda jste ovlivněni</span><span class="sxs-lookup"><span data-stu-id="0c955-133">Determine if you're affected</span></span>

<span data-ttu-id="0c955-134">Otestujte webovou aplikaci pomocí klientské verze, která se může přihlásit k novému chování.</span><span class="sxs-lookup"><span data-stu-id="0c955-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="0c955-135">Chrome, Firefox a Microsoft Edge Chromium mají nové příznaky funkcí opt-in, které lze použít k testování.</span><span class="sxs-lookup"><span data-stu-id="0c955-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="0c955-136">Po použití oprav, zejména Safari, ověřte, zda je vaše aplikace kompatibilní se staršími klientskými verzemi.</span><span class="sxs-lookup"><span data-stu-id="0c955-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="0c955-137">Další informace naleznete v [tématu Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="0c955-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="0c955-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="0c955-138">Chrome</span></span>

<span data-ttu-id="0c955-139">Chrome 78 a novější poskytují zavádějící výsledky testů.</span><span class="sxs-lookup"><span data-stu-id="0c955-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="0c955-140">Tyto verze mají dočasné zmírnění na místě a umožňují soubory cookie méně než dvě minuty staré.</span><span class="sxs-lookup"><span data-stu-id="0c955-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="0c955-141">S povolenými testovacími příznaky poskytuje Chrome 76 a 77 přesnější výsledky.</span><span class="sxs-lookup"><span data-stu-id="0c955-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="0c955-142">Chcete-li otestovat nové `chrome://flags/#same-site-by-default-cookies` chování, přepněte na povoleno.</span><span class="sxs-lookup"><span data-stu-id="0c955-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="0c955-143">Chrome 75 a starší jsou hlášeny `None` selhání s novým nastavením.</span><span class="sxs-lookup"><span data-stu-id="0c955-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="0c955-144">Další informace naleznete v [tématu Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="0c955-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="0c955-145">Google nezpřístupní starší verze Chromu.</span><span class="sxs-lookup"><span data-stu-id="0c955-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="0c955-146">Můžete si však stáhnout starší verze chromu, které budou stačit pro testování.</span><span class="sxs-lookup"><span data-stu-id="0c955-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="0c955-147">Postupujte podle pokynů na [download chrom .](https://www.chromium.org/getting-involved/download-chromium)</span><span class="sxs-lookup"><span data-stu-id="0c955-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="0c955-148">Chrom 76 Win64</span><span class="sxs-lookup"><span data-stu-id="0c955-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="0c955-149">Chrom 74 Win64</span><span class="sxs-lookup"><span data-stu-id="0c955-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="0c955-150">Safari</span><span class="sxs-lookup"><span data-stu-id="0c955-150">Safari</span></span>

<span data-ttu-id="0c955-151">Safari 12 přísně implementoval předchozí návrh a `None` selže, pokud vidí novou hodnotu v cookies.</span><span class="sxs-lookup"><span data-stu-id="0c955-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="0c955-152">Tomu je třeba se vyhnout prostřednictvím prohlížeče čichání kód je uvedeno v [podpoře starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="0c955-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="0c955-153">Ujistěte se, že testujete Safari 12 a 13, stejně jako přihlášení ve stylu operačního systému WebKit pomocí Knihovny ověřování Microsoft (MSAL), Knihovny ověřování služby Active Directory (ADAL) nebo knihovny, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="0c955-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="0c955-154">Problém je závislý na základní verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="0c955-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="0c955-155">OsX Mojave 10.14 a iOS 12 je známo, že problémy s kompatibilitou s novým chováním.</span><span class="sxs-lookup"><span data-stu-id="0c955-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="0c955-156">Upgrade na OSX Catalina 10.15 nebo iOS 13 řeší problém.</span><span class="sxs-lookup"><span data-stu-id="0c955-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="0c955-157">Safari nemá v současné době příznak pro přihlášení pro testování chování nové specifikace.</span><span class="sxs-lookup"><span data-stu-id="0c955-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="0c955-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="0c955-158">Firefox</span></span>

<span data-ttu-id="0c955-159">Firefox podporu pro nový standard lze testovat na verzi 68 a `about:config` později se `network.cookie.sameSite.laxByDefault`přihlásili na stránce s funkcí příznakem .</span><span class="sxs-lookup"><span data-stu-id="0c955-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="0c955-160">U starších verzí Firefoxu nebyly hlášeny žádné problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="0c955-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="0c955-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0c955-161">Microsoft Edge</span></span>

<span data-ttu-id="0c955-162">Zatímco Microsoft Edge `SameSite` podporuje starý standard, od verze 44 neměl žádné problémy s kompatibilitou s novým standardem.</span><span class="sxs-lookup"><span data-stu-id="0c955-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="0c955-163">Microsoft Edge Chromium</span><span class="sxs-lookup"><span data-stu-id="0c955-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="0c955-164">Příznak funkce `edge://flags/#same-site-by-default-cookies`je .</span><span class="sxs-lookup"><span data-stu-id="0c955-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="0c955-165">Při testování pomocí microsoft edge chromu 78 nebyly pozorovány žádné problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="0c955-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="0c955-166">Elektronová</span><span class="sxs-lookup"><span data-stu-id="0c955-166">Electron</span></span>

<span data-ttu-id="0c955-167">Verze Electronu obsahují starší verze chromu.</span><span class="sxs-lookup"><span data-stu-id="0c955-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="0c955-168">Například verze Electron používá Microsoft Teams je Chromium 66, který vykazuje starší chování.</span><span class="sxs-lookup"><span data-stu-id="0c955-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="0c955-169">Proveďte vlastní testování kompatibility s verzí Electron, kterou váš produkt používá.</span><span class="sxs-lookup"><span data-stu-id="0c955-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="0c955-170">Další informace naleznete v [tématu Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="0c955-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="0c955-171">Podpora starších prohlížečů</span><span class="sxs-lookup"><span data-stu-id="0c955-171">Support older browsers</span></span>

<span data-ttu-id="0c955-172">Norma z roku `SameSite` 2016 stanovila, `SameSite=Strict` že s neznámými hodnotami se zachází jako s hodnotami.</span><span class="sxs-lookup"><span data-stu-id="0c955-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="0c955-173">V důsledku toho všechny starší prohlížeče, které podporují původní `SameSite` standard může `None`přerušit, když vidí vlastnost s hodnotou .</span><span class="sxs-lookup"><span data-stu-id="0c955-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="0c955-174">Webové aplikace musí implementovat procházení prohlížeče, pokud mají v úmyslu podporovat tyto staré prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="0c955-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="0c955-175">ASP.NET Core neimplementuje prohlížeč sniffing pro vás, protože `User-Agent` hodnoty záhlaví požadavku jsou vysoce nestabilní a měnit na týdenní bázi.</span><span class="sxs-lookup"><span data-stu-id="0c955-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="0c955-176">Místo toho bod rozšíření v zásadách `User-Agent`souborů cookie umožňuje přidat -specifickou logiku.</span><span class="sxs-lookup"><span data-stu-id="0c955-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="0c955-177">V *Startup.cs*přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="0c955-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="0c955-178">Odhlášení</span><span class="sxs-lookup"><span data-stu-id="0c955-178">Opt-out switches</span></span>

<span data-ttu-id="0c955-179">Přepínač `Microsoft.AspNetCore.SuppressSameSiteNone` kompatibility umožňuje dočasně odhlásit z nového ASP.NET chování souborů cookie Core.</span><span class="sxs-lookup"><span data-stu-id="0c955-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="0c955-180">Přidejte následující json do souboru *runtimeconfig.template.json* v projektu:</span><span class="sxs-lookup"><span data-stu-id="0c955-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="0c955-181">Jiné verze</span><span class="sxs-lookup"><span data-stu-id="0c955-181">Other Versions</span></span>

<span data-ttu-id="0c955-182">Související `SameSite` záplaty jsou připravovány pro:</span><span class="sxs-lookup"><span data-stu-id="0c955-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="0c955-183">ASP.NET jádra 2.1, 2.2 a 3.0</span><span class="sxs-lookup"><span data-stu-id="0c955-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="0c955-184">`Microsoft.Owin`4.1</span><span class="sxs-lookup"><span data-stu-id="0c955-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="0c955-185">`System.Web`(pro rozhraní .NET Framework 4.7.2 a novější)</span><span class="sxs-lookup"><span data-stu-id="0c955-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="0c955-186">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0c955-186">Category</span></span>

<span data-ttu-id="0c955-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0c955-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c955-188">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0c955-188">Affected APIs</span></span>

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
