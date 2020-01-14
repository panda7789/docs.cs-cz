---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937040"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Odebrala se duplicitní rozhraní API z model Windows Forms.

V .NET Core 3,0 RC1 se odebralo několik rozhraní API náhodně duplicitních z oboru názvů <xref:System.Windows.Forms?displayProperty=fullName> od verze .NET Core 3,0 Preview 4.

#### <a name="change-description"></a>Popis změny

.NET Core 3,0 Preview 4 neúmyslně duplikoval určitý počet typů v oboru názvů <xref:System.Windows.Forms?displayProperty=fullName>, který již existoval v <xref:System.ComponentModel.Design?displayProperty=fullName>m oboru názvů. Od verze .NET Core 3,0 RC1 tyto duplicitní typy již nejsou k dispozici. V následující tabulce je uveden původní typ a jeho duplicitní typ:

> [!div class="mx-tdCol2BreakAll"]
> |Původní typ|Duplicitní typ|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Představená verze

3,0 RC1

#### <a name="recommended-action"></a>Doporučená akce

Aktualizujte kód tak, aby odkazoval na původní typ, jak je znázorněno ve sloupci **původní typ** tabulky.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Nedá se detekovat přes analýzu rozhraní API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
