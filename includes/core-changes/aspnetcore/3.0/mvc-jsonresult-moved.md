---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901941"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult byl přesunut do microsoft.aspNetCore.Mvc.Core

`JsonResult`přesunuta do `Microsoft.AspNetCore.Mvc.Core` sestavy. Tento typ byl definován v [souboru Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Atribut [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) na úrovni sestavení `Microsoft.AspNetCore.Mvc.Formatters.Json` byl přidán k řešení tohoto problému pro většinu uživatelů. S aplikacemi, které používají knihovny třetích stran, se mohou vyskytnat problémy.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 6

#### <a name="old-behavior"></a>Staré chování

Aplikace používající knihovnu založenou na 2,2 úspěšně vytvoří.

#### <a name="new-behavior"></a>Nové chování

Aplikace používající knihovnu založenou na 2.2 se nezdaří kompilace. Je k dispozici chyba obsahující variantu následujícího textu:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Příklad takového problému naleznete v tématu [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).

#### <a name="reason-for-change"></a>Důvod změny

Změny na úrovni platformy ve složení ASP.NET Core, jak je popsáno na [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Doporučená akce

Knihovny zkompilované proti verzi `Microsoft.AspNetCore.Mvc.Formatters.Json` 2.2 může být nutné překompilovat k řešení problému pro všechny spotřebitele. Pokud je to ovlivněno, obraťte se na autora knihovny. Požádejte o rekompilaci knihovny, která bude cílit ASP.NET jádrem 3.0.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
