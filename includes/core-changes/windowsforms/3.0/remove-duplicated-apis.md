---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937040"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Duplicitní api odebraná z formulářů systému Windows Forms

V rozhraní .NET Core 3.0 RC1 byl odebrán počet rozhraní API, která byla omylem duplikována v oboru <xref:System.Windows.Forms?displayProperty=fullName> názvů počínaje rozhraním .NET Core 3.0 Preview 4.

#### <a name="change-description"></a>Popis změny

.NET Core 3.0 Preview 4 neúmyslně duplikoval počet typů v oboru <xref:System.Windows.Forms?displayProperty=fullName> názvů, které již v oboru <xref:System.ComponentModel.Design?displayProperty=fullName> názvů existovaly. Počínaje rozhraním .NET Core 3.0 RC1 již tyto duplicitní typy nejsou k dispozici. V následující tabulce je uveden původní typ a jeho duplicitní typ:

> [!div class="mx-tdCol2BreakAll"]
> |Původní typ|Duplicitní typ|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Zavedená verze

3.0 RC1

#### <a name="recommended-action"></a>Doporučená akce

Aktualizujte kód tak, aby odkazoval na původní typ, jak je znázorněno ve sloupci **Původní typ** tabulky.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Nelze zjistit pomocí analýzy rozhraní API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
