---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936990"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.

Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility je podporován v model Windows Forms v .NET Framework 4,6 a novějších verzích, ale není podporován v model Windows Forms Počínaje rozhraním .net Core 3,0.

#### <a name="change-description"></a>Popis změny

V .NET Framework 4,6 a novějších verzích vybere karta změnu pořadí kolekce ovládacích prvků. Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility umožňuje aplikaci přeskočit toto přeřazení, pokud je toto chování nežádoucí.

V rozhraní .NET Core není `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` přepínač podporován.

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
