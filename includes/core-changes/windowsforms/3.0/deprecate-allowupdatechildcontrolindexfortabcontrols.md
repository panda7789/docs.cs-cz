---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556155"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.

`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Přepínač kompatibility je podporován v model Windows Forms v .NET Framework 4,6 a novějších verzích, ale není podporován v rozhraní .NET Core nebo .net 5,0 a novějším.

#### <a name="change-description"></a>Popis změny

V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků. `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`Přepínač kompatibility umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.

V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
