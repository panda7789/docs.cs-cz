---
ms.openlocfilehash: 4f2ace670884d154b219d2146a242d2cee098831
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344270"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult se přesunula do Microsoft. AspNetCore. Mvc. Core.

`JsonResult` přesunul do sestavení `Microsoft.AspNetCore.Mvc.Core`. Tento typ se používá pro definování v [Microsoft. AspNetCore. Mvc. formátovací modul. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Do `Microsoft.AspNetCore.Mvc.Formatters.Json` byl přidán atribut na úrovni sestavení [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) , který bude tento problém řešit pro většinu uživatelů. V aplikacích, které používají knihovny třetích stran, může dojít k problémům.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 6

#### <a name="old-behavior"></a>Staré chování

Aplikace, která používá sestavení knihovny založené na 2,2, se úspěšně sestavuje.

#### <a name="new-behavior"></a>Nové chování

V aplikaci, která používá knihovnu založenou na 2,2, se kompilace nezdařila. K dispozici je chyba obsahující variaci následujícího textu:

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Příklad takového problému naleznete v tématu [ASPNET/AspNetCore # 7220](https://github.com/aspnet/AspNetCore/issues/7220).

#### <a name="reason-for-change"></a>Důvod změny

Změny na úrovni platformy pro složení ASP.NET Core, jak je popsáno v tématu [ASPNET/oznámení # 325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Doporučená akce

Knihovny zkompilované proti verzi 2,2 `Microsoft.AspNetCore.Mvc.Formatters.Json` může být nutné znovu zkompilovat, aby se vyřešil problém pro všechny uživatele. Pokud je to ovlivněno, obraťte se na autora knihovny. Požadavek na opětovnou kompilaci knihovny pro cílovou ASP.NET Core 3,0.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
