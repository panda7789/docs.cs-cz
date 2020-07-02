---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619917"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items. Clear neodebere duplicity z SelectedItems.

#### <a name="details"></a>Podrobnosti

Předpokládejme, že selektor (s povoleným více výběry) má duplicity v <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> kolekci – stejná položka se vyskytuje více než jednou.  Odebrání těchto položek ze zdroje dat (např. volání Items. Clear) se neodstraní z; odebere <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> se pouze první instance. Kromě toho může následující použití <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (například SelectedItems. Clear ()) narazit na problémy jako <xref:System.ArgumentException?displayProperty=fullName> , protože <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> obsahuje položky, které již nejsou ve zdroji dat.

#### <a name="suggestion"></a>Návrh

Upgradujte, pokud je to možné, .NET Framework 4.6.2.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
