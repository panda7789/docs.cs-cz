---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235367"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Volání z obslužné rutiny CellEditEnding DataGrid.CommitEdit zahodí fokus

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednoho z <xref:System.Windows.Controls.DataGrid?displayProperty=name>společnosti <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> způsobí, že obslužné rutiny událostí <xref:System.Windows.Controls.DataGrid?displayProperty=name> ztratí fokus.|
|Doporučení|Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže lze se vyhnout upgradem rozhraní .NET Framework. Alternativně můžete se vyhnout výběrem explicitně znovu <xref:System.Windows.Controls.DataGrid?displayProperty=name> po volání <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
