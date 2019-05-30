---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379528"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="0396c-101">FlowDocument můžou zobrazovat další řádek textu</span><span class="sxs-lookup"><span data-stu-id="0396c-101">FlowDocument may show an extra line of text</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0396c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0396c-102">Details</span></span>|<span data-ttu-id="0396c-103">V některých případech <xref:System.Windows.Documents.FlowDocument> elementu se zobrazí další řádek textu při spuštění v rozhraní .NET Framework 4.5 ve srovnání s způsob zobrazení při spuštění v rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="0396c-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="0396c-104">Nejsou žádné známé případy změny způsobující jakýkoli text, který se má zobrazit nesprávně nebo illegibly, ale může způsobit text, který se zobrazí, která dříve byla vynechána z <xref:System.Windows.Documents.FlowDocument>v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0396c-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>|
|<span data-ttu-id="0396c-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="0396c-105">Suggestion</span></span>|<span data-ttu-id="0396c-106">V některých případech můžete zmenšit vlastnost PageHeight zobrazení elementu jednou obnovit předchozí počet zobrazených řádků.</span><span class="sxs-lookup"><span data-stu-id="0396c-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>|
|<span data-ttu-id="0396c-107">Scope</span><span class="sxs-lookup"><span data-stu-id="0396c-107">Scope</span></span>|<span data-ttu-id="0396c-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0396c-108">Edge</span></span>|
|<span data-ttu-id="0396c-109">Version</span><span class="sxs-lookup"><span data-stu-id="0396c-109">Version</span></span>|<span data-ttu-id="0396c-110">4.5</span><span class="sxs-lookup"><span data-stu-id="0396c-110">4.5</span></span>|
|<span data-ttu-id="0396c-111">Type</span><span class="sxs-lookup"><span data-stu-id="0396c-111">Type</span></span>|<span data-ttu-id="0396c-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="0396c-112">Runtime</span></span>|
|<span data-ttu-id="0396c-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0396c-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|
