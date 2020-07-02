---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620086"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument může zobrazit další řádek textu.

#### <a name="details"></a>Podrobnosti

V některých případech prvek při spuštění <xref:System.Windows.Documents.FlowDocument> na .NET Framework 4,5 ve srovnání se zobrazením na .NET Framework 4,0 zobrazí další řádek textu. Neexistují žádné známé případy změny, což způsobí, že by se text zobrazil špatně nebo illegibly, ale může to způsobit, že se text v zobrazení dříve vynechal <xref:System.Windows.Documents.FlowDocument> .

#### <a name="suggestion"></a>Návrh

V některých případech může zmenšit předchozí počet zobrazených řádků tím, že se zmenší vlastnost PageHeight elementu zobrazení o jeden.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
