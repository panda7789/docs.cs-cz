---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888109"
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

- Žádné.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
