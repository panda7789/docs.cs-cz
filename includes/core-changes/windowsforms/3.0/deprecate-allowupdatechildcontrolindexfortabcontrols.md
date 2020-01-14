---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936990"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Přepínač kompatibility AllowUpdateChildControlIndexForTabControls se nepodporuje.

Přepínač kompatibility `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` je podporován v model Windows Forms na .NET Framework 4,6 a novějších verzích, ale není podporován v model Windows Forms Počínaje rozhraním .NET Core 3,0.

#### <a name="change-description"></a>Popis změny

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
