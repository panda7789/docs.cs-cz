---
ms.openlocfilehash: 3d0a90a57c2b1c2759b8420e74c284668d54e9cb
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72526737"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>Odebrala se duplicitní rozhraní API z model Windows Forms.

Počet rozhraní API náhodně duplicitních duplikován v oboru názvů <xref:System.Windows.Forms?displayProperty=fullName>, který začíná v rozhraní .NET Core 3,0 Preview 4, byl v rozhraní .NET Core 3,0 RC1 odebraný.

#### <a name="change-description"></a>Změnit popis

.NET Core 3,0 Preview 4 neúmyslně duplikoval určitý počet typů v oboru názvů <xref:System.Windows.Forms?displayProperty=fullName>, který již existoval v oboru názvů <xref:System.ComponentModel.Design?displayProperty=fullName>. Od verze .NET Core 3,0 RC1 tyto duplicitní typy již nejsou k dispozici. V následující tabulce je uveden původní typ a jeho duplicitní typ:

|Původní typ|Duplicitní typ|
|---|---|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
|<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
|<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

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
