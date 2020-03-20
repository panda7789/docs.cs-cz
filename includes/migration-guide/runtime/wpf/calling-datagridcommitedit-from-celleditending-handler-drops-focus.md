---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803205"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Volání DataGrid.CommitEdit z obslužné rutiny CellEditEnding klesne fokus

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednoho <xref:System.Windows.Controls.DataGrid?displayProperty=name>z <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> obslužné rutiny události 's způsobí, <xref:System.Windows.Controls.DataGrid?displayProperty=name> že ztratí fokus.|
|Návrh|Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže se jí lze vyhnout upgradem rozhraní .NET Framework. Alternativně se lze vyhnout explicitním opětovným <xref:System.Windows.Controls.DataGrid?displayProperty=name> výběrem <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>po volání .|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
