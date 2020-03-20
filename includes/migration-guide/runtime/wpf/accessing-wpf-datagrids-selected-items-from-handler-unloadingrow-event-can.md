---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858533"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a>Přístup k vybraným položkám WPF DataGrid z obslužné rutiny události UnloadingRow serveru DataGrid může způsobit výjimku NullReferenceException

|   |   |
|---|---|
|Podrobnosti|Z důvodu chyby v rozhraní .NET Framework 4.5, obslužné rutiny <xref:System.Windows.Controls.DataGrid> událostí pro události zahrnující odebrání řádku může způsobit vyvolání, <xref:System.NullReferenceException?displayProperty=name> pokud mají přístup <xref:System.Windows.Controls.DataGrid>k 's <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> nebo <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> vlastnosti.|
|Návrh|Tento problém byl vyřešen v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
