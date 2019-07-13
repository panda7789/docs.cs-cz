---
ms.openlocfilehash: 2f94ec58e6fdb56cfc5147e74b6ffd6bb657228d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857513"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear neodebere z SelectedItems duplicitní položky

|   |   |
|---|---|
|Podrobnosti|Předpokládejme, že selektor (s povoleno více výběrů) má duplicitní položky v jeho <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> kolekce - jedné položce se objevuje víckrát.  Odebrání položky ze zdroje dat (například voláním Items.Clear) se nepodařilo odebrat z <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; pouze první instance se odebere. Kromě toho při dalším použití <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (třeba SelectedItems.Clear()) můžou mít problémy, jako <xref:System.ArgumentException?displayProperty=name>, protože <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> obsahuje položky, které jsou už ve zdroji dat.|
|Doporučení|Pokud je to možné upgradujte na rozhraní .NET Framework 4.6.2.|
|Scope|Vedlejší|
|Version|4.5|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

