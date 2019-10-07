---
ms.openlocfilehash: 4d67da34cf692133df95480a7f0215943337a34e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003025"
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
