---
ms.openlocfilehash: 3f702febc78488b9413ec9303ded211493650f02
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198406"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC: zastaralý nástroj předkompilace

V ASP.NET Core 1,1 byl zaveden balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (nástroj předkompilace MVC), který přidává podporu pro kompilaci souborů Razor v době publikování (soubory *. cshtml* ). V ASP.NET Core 2,1 byla [sada Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) představena za účelem rozšíření funkcí nástroje předkompilace. Sada Razor SDK přidala podporu pro kompilaci souborů Razor při sestavení a publikování. Sada SDK ověřuje správnost souborů *. cshtml* při sestavování a současně zlepšuje čas spuštění aplikace. Sada Razor SDK je ve výchozím nastavení zapnutá a není nutná žádná gesta, která by ji mohla začít používat.

V ASP.NET Core 3,0 byl odebrán nástroj předkompilace sady ASP.NET Core 1,1-éry MVC. Starší verze balíčků budou dál získávat důležité opravy chyb a zabezpečení ve verzi opravy.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` byl použit k předkompilování zobrazení MVC Razor.

#### <a name="new-behavior"></a>Nové chování

Tato funkce je nativně podporovaná sadou SDK Razor. Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` už není aktualizovaný.

#### <a name="reason-for-change"></a>Důvod změny

Sada Razor SDK poskytuje více funkcí a ověřuje správnost souborů *. cshtml* v době sestavení. Sada SDK také vylepšuje čas spuštění aplikace.

#### <a name="recommended-action"></a>Doporučená akce

Pro uživatele ASP.NET Core 2,1 nebo novější verzi aktualizujte, aby používaly nativní podporu předkompilace v [sadě Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Pokud chyby nebo chybějící funkce brání migraci do sady Razor SDK, otevřete problém v [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

### Affected APIs

Not detectable via API analysis

-->
