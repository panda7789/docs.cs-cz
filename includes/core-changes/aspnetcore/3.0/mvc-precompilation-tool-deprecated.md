---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902043"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: Nástroj předběžné kompilace se zastaral

V ASP.NET Core 1.1 byl zaveden balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool), který přidává podporu pro kompilaci souborů Razor (*.cshtml).* V ASP.NET Core 2.1 byla zavedena [sada Razor SDK,](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) která rozšiřuje funkce nástroje pro předkompilaci. Sada Razor SDK přidala podporu pro kompilaci souborů Razor v době sestavení a publikování. Sada SDK ověřuje správnost souborů *.cshtml* v době sestavení a zároveň zlepšuje dobu spuštění aplikace. Sada Razor SDK je ve výchozím nastavení zapnutá a není nutné žádné gesto, které by ji začalo používat.

V ASP.NET Core 3.0 byl ASP.NET nástroj předkompilace MVC core 1.1 éry odebrán. Starší verze balíčků budou i nadále dostávat důležité opravy chyb a zabezpečení ve verzi opravy.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` byl použit k předkompilaci zobrazení MVC Razor.

#### <a name="new-behavior"></a>Nové chování

Sada Razor SDK nativně podporuje tuto funkci. Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` již není aktualizován.

#### <a name="reason-for-change"></a>Důvod změny

Sada Razor SDK poskytuje další funkce a ověřuje správnost souborů *.cshtml* v době sestavení. Sada SDK také zlepšuje dobu spuštění aplikace.

#### <a name="recommended-action"></a>Doporučená akce

Pro uživatele ASP.NET Jádrem 2.1 nebo novějším aktualizujte tak, aby používala nativní podporu pro předkompilaci v [sada Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Pokud chyby nebo chybějící funkce brání migraci do sady Razor SDK, otevřete problém na [adrese dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

### Affected APIs

Not detectable via API analysis

-->
