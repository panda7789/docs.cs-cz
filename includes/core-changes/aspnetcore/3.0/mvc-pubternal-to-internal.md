---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901833"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: "Pubternal" typy změněny na vnitřní

V ASP.NET Core 3.0 byly všechny typy pubternal v MVC aktualizovány tak, aby byly `public` buď v podporovaném oboru názvů, nebo `internal` podle potřeby.

#### <a name="change-description"></a>Popis změny

V ASP.NET Core jsou typy "pubternal" deklarovány jako, `public` ale jsou umístěny v oboru názvů `.Internal`s uznanou suffixed. Zatímco tyto `public`typy jsou , nemají žádné zásady podpory a jsou předmětem změny. Bohužel náhodné použití těchto typů bylo běžné, což má za následek porušení změn těchto projektů a omezení schopnosti udržovat rámec.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Některé typy v MVC `public` `.Internal` byly, ale v oboru názvů. Tyto typy neměly žádné zásady podpory a byly předmětem porušení změn.

#### <a name="new-behavior"></a>Nové chování

Všechny tyto typy jsou `public` aktualizovány buď tak, `internal`aby byly v podporovaném oboru názvů, nebo označeny jako .

#### <a name="reason-for-change"></a>Důvod změny

Náhodné použití typů "pubternal" bylo běžné, což vedlo k porušení změn těchto projektů a omezení schopnosti udržovat rámec.

#### <a name="recommended-action"></a>Doporučená akce

Pokud používáte typy, které `public` se skutečně staly a byly přesunuty do nového podporovaného oboru názvů, aktualizujte odkazy tak, aby odpovídaly novým oborům názvů.

Pokud používáte typy, které byly `internal`označeny jako , budete muset najít alternativu. Dříve "pubternal" typy nebyly nikdy podporovány pro veřejné použití. Pokud existují určité typy v těchto oborech názvů, které jsou důležité pro vaše aplikace, soubor problém [na dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues). Lze vzít v úvahu vytvoření `public`požadovaných typů .

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Tato změna zahrnuje typy v následujících oborech názvů:

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
