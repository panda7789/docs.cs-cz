---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857513"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear neodstraní duplikáty z SelectedItems

|   |   |
|---|---|
|Podrobnosti|Předpokládejme, že selektor (s povoleným <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> více násobným výběrem) má ve své kolekci duplikáty - stejná položka se zobrazí více než jednou.  Odebrání těchto položek ze zdroje dat (např. voláním Items.Clear) <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>se nezdaří odebrat z ; pouze první instance je odebrána. Kromě toho následné <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> použití (např. SelectedItems.Clear()) může dojít <xref:System.ArgumentException?displayProperty=name>k <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> problémům, jako je například , protože obsahuje položky, které již nejsou ve zdroji dat.|
|Návrh|Pokud je to možné, upgradujte na rozhraní .NET Framework 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
