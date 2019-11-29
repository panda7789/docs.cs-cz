---
ms.openlocfilehash: b0d093cc30a09b3248cc57a521b386bf581b5451
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552142"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="2b489-101">HTTP: Browser SameSite změny dopadu na ověření</span><span class="sxs-lookup"><span data-stu-id="2b489-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="2b489-102">Některé prohlížeče, jako je například Chrome a Firefox, provedly zásadní změny jejich implementace `SameSite` pro soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="2b489-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="2b489-103">Změny mají vliv na scénáře vzdáleného ověřování, například OpenID Connect a WS-Federation, které se musí odhlásit odesláním `SameSite=None`.</span><span class="sxs-lookup"><span data-stu-id="2b489-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="2b489-104">Nicméně `SameSite=None` přerušují iOS 12 a některé starší verze jiných prohlížečů.</span><span class="sxs-lookup"><span data-stu-id="2b489-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="2b489-105">Aplikace potřebuje tyto verze zachytit a vypustit `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="2b489-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="2b489-106">Diskuzi o tomto problému najdete v tématu [ASPNET/AspNetCore # 14996](https://github.com/aspnet/AspNetCore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="2b489-106">For discussion on this issue, see [aspnet/AspNetCore#14996](https://github.com/aspnet/AspNetCore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b489-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2b489-107">Version introduced</span></span>

<span data-ttu-id="2b489-108">3,1 Preview 1</span><span class="sxs-lookup"><span data-stu-id="2b489-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2b489-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="2b489-109">Old behavior</span></span>

<span data-ttu-id="2b489-110">`SameSite` je 2016 koncept standardního rozšíření pro soubory cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="2b489-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="2b489-111">Slouží ke zmírnění omezení padělání žádostí mezi weby (CSRF).</span><span class="sxs-lookup"><span data-stu-id="2b489-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="2b489-112">Tato možnost byla původně navržena jako funkce, které by servery mohly vyjádřit přidáním nových parametrů.</span><span class="sxs-lookup"><span data-stu-id="2b489-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="2b489-113">ASP.NET Core 2,0 byla přidána počáteční podpora pro `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="2b489-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2b489-114">Nové chování</span><span class="sxs-lookup"><span data-stu-id="2b489-114">New behavior</span></span>

<span data-ttu-id="2b489-115">Společnost Google navrhla nový koncept Standard, který není zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="2b489-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="2b489-116">Standard změní výchozí režim na `Lax` a přidá novou položku `None` k odhlášení. pro většinu souborů cookie aplikace postačuje `Lax`. dojde ale k přerušení scénářů mezi lokalitami, jako je OpenID Connect a přihlášení ke službě WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="2b489-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="2b489-117">Většina přihlášení OAuth není ovlivněná kvůli rozdílům ve způsobu, jakým jsou požadavky v toku.</span><span class="sxs-lookup"><span data-stu-id="2b489-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="2b489-118">Nový parametr `None` způsobuje problémy s kompatibilitou s klienty, kteří implementovali předchozí koncept Standard (například iOS 12).</span><span class="sxs-lookup"><span data-stu-id="2b489-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="2b489-119">Chrome 80 bude obsahovat změny.</span><span class="sxs-lookup"><span data-stu-id="2b489-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="2b489-120">Podívejte se na [SameSite aktualizace](https://www.chromium.org/updates/same-site) pro časovou osu spuštění produktu Chrome.</span><span class="sxs-lookup"><span data-stu-id="2b489-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="2b489-121">ASP.NET Core 3,1 byl aktualizován, aby implementoval nové chování `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="2b489-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="2b489-122">Aktualizace předefinuje chování `SameSiteMode.None` k vygenerování `SameSite=None` a přidá novou hodnotu `SameSiteMode.Unspecified` pro vynechání atributu `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="2b489-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="2b489-123">Všechna rozhraní API souborů cookie teď `Unspecified`výchozí, i když některé komponenty, které používají soubory cookie, nastavily hodnoty lépe specifické pro jejich scénáře, jako je například korelace OpenID Connect a soubory nonce.</span><span class="sxs-lookup"><span data-stu-id="2b489-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="2b489-124">Další nedávné změny v této oblasti najdete v tématu [http: některé výchozí hodnoty SameSite souborů cookie se změnily na žádné](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="2b489-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="2b489-125">V ASP.NET Core 3,0 se většina výchozích hodnot změnila z <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> na <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (ale pořád se používá předchozí Standard).</span><span class="sxs-lookup"><span data-stu-id="2b489-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2b489-126">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="2b489-126">Reason for change</span></span>

<span data-ttu-id="2b489-127">Změny v prohlížeči a specifikaci, jak je uvedeno v předchozím textu.</span><span class="sxs-lookup"><span data-stu-id="2b489-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2b489-128">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2b489-128">Recommended action</span></span>

<span data-ttu-id="2b489-129">Aplikace, které komunikují se vzdálenými lokalitami, například prostřednictvím přihlášení třetí strany, potřebují:</span><span class="sxs-lookup"><span data-stu-id="2b489-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="2b489-130">Otestujte tyto scénáře ve více prohlížečích.</span><span class="sxs-lookup"><span data-stu-id="2b489-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="2b489-131">Použijte zásady souborů cookie v prohlížeči zásady zmírnění rizika popsané v tématu [Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="2b489-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="2b489-132">Pokyny k testování a sledování v prohlížeči najdete v následující části.</span><span class="sxs-lookup"><span data-stu-id="2b489-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="2b489-133">Určení, jestli jste to ovlivnili</span><span class="sxs-lookup"><span data-stu-id="2b489-133">Determine if you're affected</span></span>

<span data-ttu-id="2b489-134">Otestujte webovou aplikaci pomocí verze klienta, která se může přihlásit k novému chování.</span><span class="sxs-lookup"><span data-stu-id="2b489-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="2b489-135">Pro Chrome, Firefox a Microsoft Edge chrom existují nové příznaky funkcí pro výslovný souhlas, které lze použít k testování.</span><span class="sxs-lookup"><span data-stu-id="2b489-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="2b489-136">Ověřte, jestli je vaše aplikace kompatibilní se staršími verzemi klientů, i když jste použili opravy, zejména Safari.</span><span class="sxs-lookup"><span data-stu-id="2b489-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="2b489-137">Další informace najdete v tématu [Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="2b489-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="2b489-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="2b489-138">Chrome</span></span>

<span data-ttu-id="2b489-139">Chrome 78 a novější je výsledkem zavádějících výsledků testů.</span><span class="sxs-lookup"><span data-stu-id="2b489-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="2b489-140">Tyto verze mají dočasné omezení na místě a umožňují, aby soubory cookie byly starší než dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="2b489-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="2b489-141">S povolenými příznakem testu jsou k dispozici přesnější výsledky Chrome 76 a 77.</span><span class="sxs-lookup"><span data-stu-id="2b489-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="2b489-142">Chcete-li otestovat nové chování, přepněte `chrome://flags/#same-site-by-default-cookies` na povoleno.</span><span class="sxs-lookup"><span data-stu-id="2b489-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="2b489-143">Rozhraní Chrome 75 a starší se hlásí jako neúspěšná s nastavením nového `None`.</span><span class="sxs-lookup"><span data-stu-id="2b489-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="2b489-144">Další informace najdete v tématu [Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="2b489-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="2b489-145">Google nezpřístupňuje starší verze Chrome.</span><span class="sxs-lookup"><span data-stu-id="2b489-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="2b489-146">Můžete si však stáhnout starší verze Chromu, které budou postačovat pro testování.</span><span class="sxs-lookup"><span data-stu-id="2b489-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="2b489-147">Postupujte podle pokynů na [webu Stažení Chromu](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="2b489-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="2b489-148">Chróm 76 Win64</span><span class="sxs-lookup"><span data-stu-id="2b489-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="2b489-149">Chróm 74 Win64</span><span class="sxs-lookup"><span data-stu-id="2b489-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="2b489-150">Safari</span><span class="sxs-lookup"><span data-stu-id="2b489-150">Safari</span></span>

<span data-ttu-id="2b489-151">Prohlížeč Safari 12 striktně implementuje předchozí koncept a v případě, že se v souborech cookie zobrazí nová hodnota `None`, se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="2b489-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="2b489-152">K tomu je potřeba se vyhnout prostřednictvím kódu sledování prohlížeče, který je uvedený v části [Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="2b489-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="2b489-153">Ujistěte se, že otestujete prohlížeč Safari 12 a 13, stejně jako WebKit, přihlášení pomocí knihovny Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL) nebo libovolnou knihovnu, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="2b489-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="2b489-154">Problém závisí na základní verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2b489-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="2b489-155">OSX Mojave 10,14 a iOS 12 se nazývají problémy s kompatibilitou s novým chováním.</span><span class="sxs-lookup"><span data-stu-id="2b489-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="2b489-156">Při upgradu na OSX Catalina 10,15 nebo iOS 13 se problém vyřeší.</span><span class="sxs-lookup"><span data-stu-id="2b489-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="2b489-157">Prohlížeč Safari nemá v současné době příznak výslovného souhlasu pro testování nového chování specifikace.</span><span class="sxs-lookup"><span data-stu-id="2b489-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="2b489-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="2b489-158">Firefox</span></span>

<span data-ttu-id="2b489-159">Podporu aplikace Firefox pro nový standard lze otestovat na verzi 68 a novější, a to tak, že na stránce `about:config` `network.cookie.sameSite.laxByDefault`příznak funkce.</span><span class="sxs-lookup"><span data-stu-id="2b489-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="2b489-160">Ve starších verzích prohlížeče Firefox nebyly hlášeny žádné problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="2b489-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="2b489-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2b489-161">Microsoft Edge</span></span>

<span data-ttu-id="2b489-162">Zatímco Microsoft Edge podporuje starý `SameSite` Standard, od verze 44 nemá žádné problémy s kompatibilitou s novým standardem.</span><span class="sxs-lookup"><span data-stu-id="2b489-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="2b489-163">Microsoft Edge chrom</span><span class="sxs-lookup"><span data-stu-id="2b489-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="2b489-164">Příznak funkce je `edge://flags/#same-site-by-default-cookies`.</span><span class="sxs-lookup"><span data-stu-id="2b489-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="2b489-165">Při testování s Microsoft Edge chrom 78 nebyly pozorovány žádné problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="2b489-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="2b489-166">Chyt</span><span class="sxs-lookup"><span data-stu-id="2b489-166">Electron</span></span>

<span data-ttu-id="2b489-167">K verzím elektronů patří starší verze Chromu.</span><span class="sxs-lookup"><span data-stu-id="2b489-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="2b489-168">Například verze elektronicky používaného Microsoft Teams je chrom 66, který vykazuje starší chování.</span><span class="sxs-lookup"><span data-stu-id="2b489-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="2b489-169">Proveďte vlastní testování kompatibility s verzí elektronů, kterou váš produkt používá.</span><span class="sxs-lookup"><span data-stu-id="2b489-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="2b489-170">Další informace najdete v tématu [Podpora starších prohlížečů](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="2b489-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="2b489-171">Podpora starších prohlížečů</span><span class="sxs-lookup"><span data-stu-id="2b489-171">Support older browsers</span></span>

<span data-ttu-id="2b489-172">2016 `SameSite` standardně posuzuje, že neznámé hodnoty se budou považovat za `SameSite=Strict` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2b489-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="2b489-173">V důsledku toho se všechny starší prohlížeče, které podporují původní standard, mohou přerušit, když uvidí vlastnost `SameSite` s hodnotou `None`.</span><span class="sxs-lookup"><span data-stu-id="2b489-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="2b489-174">Pokud mají uživatelé v úmyslu podporovat tyto staré prohlížeče, musí webové aplikace implementovat monitorování v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="2b489-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="2b489-175">ASP.NET Core neimplementuje pro vás monitorování, protože `User-Agent` hodnoty hlaviček žádostí jsou vysoce nestabilní a každý týden se mění.</span><span class="sxs-lookup"><span data-stu-id="2b489-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="2b489-176">Místo toho vám rozšiřující bod v zásadách souborů cookie umožňuje přidat logiku specifickou pro `User-Agent`.</span><span class="sxs-lookup"><span data-stu-id="2b489-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="2b489-177">Do *Startup.cs*přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="2b489-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="2b489-178">Přepínače pro výslovný souhlas</span><span class="sxs-lookup"><span data-stu-id="2b489-178">Opt-out switches</span></span>

<span data-ttu-id="2b489-179">Přepínač kompatibility `Microsoft.AspNetCore.SuppressSameSiteNone` umožňuje dočasně odhlásit nové chování souborů cookie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b489-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="2b489-180">Do souboru *runtimeconfig. template. JSON* v projektu přidejte následující JSON:</span><span class="sxs-lookup"><span data-stu-id="2b489-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a><span data-ttu-id="2b489-181">Jiné verze</span><span class="sxs-lookup"><span data-stu-id="2b489-181">Other Versions</span></span>

<span data-ttu-id="2b489-182">Související opravy `SameSite` jsou pro:</span><span class="sxs-lookup"><span data-stu-id="2b489-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="2b489-183">ASP.NET Core 2,1, 2,2 a 3,0</span><span class="sxs-lookup"><span data-stu-id="2b489-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="2b489-184">`Microsoft.Owin` 4,1</span><span class="sxs-lookup"><span data-stu-id="2b489-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="2b489-185">`System.Web` (pro .NET Framework 4.7.2 a novější)</span><span class="sxs-lookup"><span data-stu-id="2b489-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="2b489-186">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2b489-186">Category</span></span>

<span data-ttu-id="2b489-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2b489-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b489-188">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2b489-188">Affected APIs</span></span>

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
