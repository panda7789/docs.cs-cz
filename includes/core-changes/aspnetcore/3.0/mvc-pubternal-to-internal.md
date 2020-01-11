---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901833"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: typy "Pubternal" se změnily na interní

V ASP.NET Core 3,0 se všechny typy "pubternal" v MVC aktualizovaly buď jako `public` v podporovaném oboru názvů, nebo v případě potřeby `internal`.

#### <a name="change-description"></a>Popis změny

V ASP.NET Core jsou typy "pubternal" deklarovány jako `public`, ale nacházejí se v oboru názvů `.Internal`s příponou. I když jsou tyto typy `public`, nemají žádné zásady podpory a podléhají změnám. Omlouváme se, ale náhodné použití těchto typů je běžné, což vedlo k zásadním změnám těchto projektů a omezení schopnosti zachovat rozhraní.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Některé typy v MVC byly `public`, ale v oboru názvů `.Internal`. Tyto typy neobsahovaly žádné zásady podpory a měly by podléhat nezměněným změnám.

#### <a name="new-behavior"></a>Nové chování

Všechny tyto typy jsou aktualizovány tak, aby byly `public` v podporovaném oboru názvů nebo označené jako `internal`.

#### <a name="reason-for-change"></a>Důvod změny

Náhodné použití typů "pubternal" bylo běžné, což vede k zásadním změnám těchto projektů a omezení schopnosti zachovat rozhraní.

#### <a name="recommended-action"></a>Doporučená akce

Pokud používáte typy, které se stanou skutečně `public` a byly přesunuty do nového podporovaného oboru názvů, aktualizujte odkazy tak, aby odpovídaly novým oborům názvů.

Pokud používáte typy, které se stanou označenými jako `internal`, budete muset najít alternativu. Předchozí typy "pubternal" nebyly nikdy podporovány pro veřejné použití. Pokud existují konkrétní typy v těchto oborech názvů, které jsou pro vaše aplikace kritické, zapište problém v [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues). Mohou být provedeny důvody pro vytvoření požadovaných typů `public`.

#### <a name="category"></a>Kategorie

ASP.NET Core

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
