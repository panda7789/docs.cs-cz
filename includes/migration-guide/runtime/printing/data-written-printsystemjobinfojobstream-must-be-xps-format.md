---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620044"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="3c0a4-101">Data zapsaná do PrintSystemJobInfo. tok úloh musí být ve formátu XPS.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

#### <a name="details"></a><span data-ttu-id="3c0a4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3c0a4-102">Details</span></span>

<span data-ttu-id="3c0a4-103"><xref:System.Printing.PrintSystemJobInfo.JobStream>Vlastnost zpřístupňuje datový proud tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="3c0a4-104">Uživatel může do tohoto datového proudu odeslat nezpracovaná data do základních tiskových součástí operačního systému. Od verze .NET Framework 4,5 ve Windows 8 a novějších verzích operačního systému Windows musí být data zapsaná do tohoto datového proudu ve formátu XPS jako datový proud balíčku.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3c0a4-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="3c0a4-105">Suggestion</span></span>

<span data-ttu-id="3c0a4-106">Pro výstup tiskového obsahu můžete provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="3c0a4-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="3c0a4-107">Použijte <xref:System.Windows.Xps.XpsDocumentWriter> třídu pro výstup tiskového obsahu.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="3c0a4-108">Toto je Doporučená alternativa.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="3c0a4-109">Zajistěte, aby data odesílaná do datového proudu vráceného <xref:System.Printing.PrintSystemJobInfo.JobStream> vlastností byla ve formátu XPS jako datový proud balíčku.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>

| <span data-ttu-id="3c0a4-110">Name</span><span class="sxs-lookup"><span data-stu-id="3c0a4-110">Name</span></span>    | <span data-ttu-id="3c0a4-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c0a4-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3c0a4-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3c0a4-112">Scope</span></span>   |<span data-ttu-id="3c0a4-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="3c0a4-113">Minor</span></span>|
|<span data-ttu-id="3c0a4-114">Verze</span><span class="sxs-lookup"><span data-stu-id="3c0a4-114">Version</span></span>|<span data-ttu-id="3c0a4-115">4.5</span><span class="sxs-lookup"><span data-stu-id="3c0a4-115">4.5</span></span>|
|<span data-ttu-id="3c0a4-116">Typ</span><span class="sxs-lookup"><span data-stu-id="3c0a4-116">Type</span></span>|<span data-ttu-id="3c0a4-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3c0a4-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c0a4-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3c0a4-118">Affected APIs</span></span>

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
