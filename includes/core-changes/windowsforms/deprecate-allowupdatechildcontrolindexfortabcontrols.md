---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181738"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls není podporovaný.

Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility je podporován v model Windows Forms v .NET Framework 4,6 a novějších verzích, ale není podporován v model Windows Forms Počínaje rozhraním .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků. Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.

V rozhraní .NET Core `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` není přepínač podporován.

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
