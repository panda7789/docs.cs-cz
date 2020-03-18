---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282532"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: Některé výchozí hodnoty cookie SameSite se změnily na Žádné

`SameSite`je možnost pro soubory cookie, které mohou pomoci zmírnit některé útoky na vyžádání mezi stránkami (CSRF). Když byla tato možnost původně zavedena, byly použity nekonzistentní výchozí hodnoty v různých ASP.NET základní chod y API. Nekonzistence vedla k matoucím výsledkům. Od ASP.NET jádra 3.0 jsou tyto výchozí hodnoty lépe zarovnány. K této funkci se musíte přihlásit pro jednotlivé komponenty.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Podobná ASP.NET jádrová api <xref:Microsoft.AspNetCore.Http.SameSiteMode> používají různé výchozí hodnoty. Příklad nekonzistence je zobrazen `HttpResponse.Cookies.Append(String, String)` `HttpResponse.Cookies.Append(String, String, CookieOptions)`v a , `SameSiteMode.None` `SameSiteMode.Lax`které defaulted a , v uvedeném pořadí.

#### <a name="new-behavior"></a>Nové chování

Všechna ovlivněná nastavení `SameSiteMode.None`API jsou ve výchozím nastavení nastavena na hodnotu .

#### <a name="reason-for-change"></a>Důvod změny

Výchozí hodnota byla změněna tak, aby byla nastavena `SameSite` funkce pro přihlášení.

#### <a name="recommended-action"></a>Doporučená akce

Každá komponenta, která vydává `SameSite` soubory cookie, se musí rozhodnout, zda je pro její scénáře vhodná. Zkontrolujte využití postižených rozhraní API `SameSite` a podle potřeby je překonfigurujte.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
