---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622347"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel. BringIndexIntoView vyvolá výjimku ArgumentOutOfRangeException.

#### <a name="details"></a>Podrobnosti

<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>bude pracovat asynchronně, pokud je povolena virtualizace sloupce, ale ještě nebyly určeny šířky sloupců.  Pokud jsou sloupce odebrány před tím, než dojde k asynchronní práci, <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> může dojít k chybě.

#### <a name="suggestion"></a>Návrh

Jednu z následujících možností:<ol><li>Upgradujte na .NET Framework 4,7.</li><li>Nainstalujte nejnovější servisní opravu pro .NET Framework 4.6.2.</li><li>Vyhněte se odebírání sloupců, dokud nebude <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> dokončena asynchronní odpověď.</li></ol>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
