---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620086"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="1a4d4-101">FlowDocument může zobrazit další řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1a4d4-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="1a4d4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1a4d4-102">Details</span></span>

<span data-ttu-id="1a4d4-103">V některých případech prvek při spuštění <xref:System.Windows.Documents.FlowDocument> na .NET Framework 4,5 ve srovnání se zobrazením na .NET Framework 4,0 zobrazí další řádek textu.</span><span class="sxs-lookup"><span data-stu-id="1a4d4-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="1a4d4-104">Neexistují žádné známé případy změny, což způsobí, že by se text zobrazil špatně nebo illegibly, ale může to způsobit, že se text v zobrazení dříve vynechal <xref:System.Windows.Documents.FlowDocument> .</span><span class="sxs-lookup"><span data-stu-id="1a4d4-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1a4d4-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="1a4d4-105">Suggestion</span></span>

<span data-ttu-id="1a4d4-106">V některých případech může zmenšit předchozí počet zobrazených řádků tím, že se zmenší vlastnost PageHeight elementu zobrazení o jeden.</span><span class="sxs-lookup"><span data-stu-id="1a4d4-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="1a4d4-107">Name</span><span class="sxs-lookup"><span data-stu-id="1a4d4-107">Name</span></span>    | <span data-ttu-id="1a4d4-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1a4d4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1a4d4-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1a4d4-109">Scope</span></span>   |<span data-ttu-id="1a4d4-110">Edge</span><span class="sxs-lookup"><span data-stu-id="1a4d4-110">Edge</span></span>|
|<span data-ttu-id="1a4d4-111">Verze</span><span class="sxs-lookup"><span data-stu-id="1a4d4-111">Version</span></span>|<span data-ttu-id="1a4d4-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1a4d4-112">4.5</span></span>|
|<span data-ttu-id="1a4d4-113">Typ</span><span class="sxs-lookup"><span data-stu-id="1a4d4-113">Type</span></span>|<span data-ttu-id="1a4d4-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1a4d4-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a4d4-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1a4d4-115">Affected APIs</span></span>

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
