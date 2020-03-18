---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936990"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Přepínač kompatibility AllowUpdateChildControlIndexForTabControls není podporován.

Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility je podporován ve formulářích Windows v rozhraní .NET Framework 4.6 a novějších verzích, ale není podporován ve formulářích Windows počínaje rozhraním .NET Core 3.0.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Framework 4.6 a novějších verzích výběr karty přeřazuje její kolekci ovládacích prvku. Přepínač `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` kompatibility umožňuje aplikaci přeskočit toto změny pořadí, pokud je toto chování nežádoucí.

V rozhraní .NET `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` Core není přepínač podporován.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Odstraňte spínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádný

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
