---
ms.openlocfilehash: b5f12e648a82ebaba7d09b546e8aa2fc7cd82a37
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803205"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Volání z obslužné rutiny CellEditEnding DataGrid.CommitEdit zahodí fokus

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednoho z <xref:System.Windows.Controls.DataGrid?displayProperty=name>společnosti <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> způsobí, že obslužné rutiny událostí <xref:System.Windows.Controls.DataGrid?displayProperty=name> ztratí fokus.|
|Doporučení|Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže lze se vyhnout upgradem rozhraní .NET Framework. Alternativně můžete se vyhnout výběrem explicitně znovu <xref:System.Windows.Controls.DataGrid?displayProperty=name> po volání <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Scope|Edge|
|Version|4.5|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

