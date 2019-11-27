---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282532"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP: některé výchozí hodnoty souborů cookie SameSite se změnily na žádné.

`SameSite` je možnost souborů cookie, které mohou napomoci zmírnit útokům prostřednictvím CSRF (více lokalit). Při počátečním zavedení této možnosti se v různých ASP.NET Core rozhraní API používaly nekonzistentní výchozí hodnoty. Nekonzistence vedla k matoucímu výsledku. Od ASP.NET Core 3,0 jsou tyto výchozí hodnoty lépe zarovnané. K této funkci se musíte vyjádřit na základě jednotlivých komponent.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Podobná ASP.NET Core rozhraní API používala jiné výchozí hodnoty <xref:Microsoft.AspNetCore.Http.SameSiteMode>. Příklad nekonzistence se zobrazuje v `HttpResponse.Cookies.Append(String, String)` a `HttpResponse.Cookies.Append(String, String, CookieOptions)`, která je nastavená na `SameSiteMode.None` a `SameSiteMode.Lax`, v uvedeném pořadí.

#### <a name="new-behavior"></a>Nové chování

Všechna ovlivněná rozhraní API jsou ve výchozím nastavení `SameSiteMode.None`.

#### <a name="reason-for-change"></a>Důvod změny

Výchozí hodnota byla změněna, aby byla `SameSite` funkce výslovného souhlasu.

#### <a name="recommended-action"></a>Doporučená akce

Každá komponenta, která generuje soubory cookie, musí rozhodnout, zda je `SameSite` vhodná pro své scénáře. Zkontrolujte využití ovlivněných rozhraní API a podle potřeby `SameSite` znovu nakonfigurujte.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
