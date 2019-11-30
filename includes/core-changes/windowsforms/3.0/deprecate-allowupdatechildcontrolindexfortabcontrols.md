---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643996"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls není podporovaný.

Přepínač kompatibility `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` je podporován v model Windows Forms na .NET Framework 4,6 a novějších verzích, ale není podporován v model Windows Forms Počínaje rozhraním .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků. Přepínač kompatibility `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` podporován.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
