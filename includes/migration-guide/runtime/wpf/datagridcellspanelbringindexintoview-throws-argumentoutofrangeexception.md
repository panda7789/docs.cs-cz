---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802516"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView vyvolá argumentOutOfRangeException

|   |   |
|---|---|
|Podrobnosti|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>bude fungovat asynchronně, pokud je povolena virtualizace sloupců, ale šířky sloupců ještě nebyly určeny.  Pokud sloupce jsou odebrány před asynchronní <xref:System.ArgumentOutOfRangeException?displayProperty=name> práce se stane, může dojít k.|
|Návrh|Některý z následujících:<ol><li>Upgrade na rozhraní .NET Framework 4.7.</li><li>Nainstalujte nejnovější servisní opravu pro rozhraní .NET Framework 4.6.2.</li><li>Vyhněte se odebírání <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> sloupců, dokud nebude dokončena asynchronní odpověď na.</li></ol>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
