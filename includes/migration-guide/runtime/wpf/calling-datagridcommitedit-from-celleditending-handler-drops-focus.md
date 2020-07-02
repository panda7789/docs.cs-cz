---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622028"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>Volání metody DataGrid. CommitEdit z obslužné rutiny CellEditEnding zruší fokus.

#### <a name="details"></a>Podrobnosti

Volání <xref:System.Windows.Controls.DataGrid.CommitEdit> z jedné z <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> obslužných rutin událostí způsobí <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> ztrátu fokusu.

#### <a name="suggestion"></a>Návrh

Tato chyba byla opravena v .NET Framework 4.5.2, takže se ji můžete vyhnout upgradem .NET Framework. Alternativně se můžete vyhnout explicitním výběrem <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> po volání <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
