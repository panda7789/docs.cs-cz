---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803654"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear neodebere z SelectedItems duplicitní položky

|   |   |
|---|---|
|Podrobnosti|Předpokládejme, že selektor (s povoleno více výběrů) má duplicitní položky v jeho <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> kolekce - jedné položce se objevuje víckrát.  Odebrání položky ze zdroje dat (například voláním Items.Clear) se nepodařilo odebrat z <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; pouze první instance se odebere. Kromě toho při dalším použití <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (třeba SelectedItems.Clear()) můžou mít problémy, jako <xref:System.ArgumentException?displayProperty=name>, protože <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> obsahuje položky, které jsou už ve zdroji dat.|
|Doporučení|Pokud je to možné upgradujte na rozhraní .NET Framework 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
