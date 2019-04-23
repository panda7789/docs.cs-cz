---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803655"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Přístup k WPF DataGrid vybrané položky z obslužné rutiny události UnloadingRow DataGrid může způsobit NullReferenceException

|   |   |
|---|---|
|Podrobnosti|Kvůli chybě v rozhraní .NET Framework 4.5, obslužné rutiny událostí pro <xref:System.Windows.Controls.DataGrid> události týkající se odebrání řádek může způsobit, že <xref:System.NullReferenceException?displayProperty=name> která je vyvolána, pokud budou přistupovat k <xref:System.Windows.Controls.DataGrid>společnosti <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> nebo <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> vlastnosti.|
|Doporučení|Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
