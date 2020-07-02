---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614453"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="160fc-101">Názvy událostí ETW se nemůžou lišit jenom od přípony "Start" nebo "Stop".</span><span class="sxs-lookup"><span data-stu-id="160fc-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

#### <a name="details"></a><span data-ttu-id="160fc-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="160fc-102">Details</span></span>

<span data-ttu-id="160fc-103">V .NET Framework 4,6 a 4.6.1 modul runtime vyvolá výjimku, <xref:System.ArgumentException> Pokud se dva názvy událostí trasování událostí pro Windows (ETW) liší pouze příponou "Start" nebo "Stop" (jako když jedna událost je pojmenována `LogUser` a jiná má název `LogUserStart` ).</span><span class="sxs-lookup"><span data-stu-id="160fc-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a "Start" or "Stop" suffix (as when one event is named `LogUser` and another is named `LogUserStart`).</span></span> <span data-ttu-id="160fc-104">V takovém případě modul runtime nemůže vytvořit zdroj události, který nemůže vygenerovat žádné protokolování.</span><span class="sxs-lookup"><span data-stu-id="160fc-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="160fc-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="160fc-105">Suggestion</span></span>

<span data-ttu-id="160fc-106">Chcete-li zabránit výjimce, zajistěte, aby se žádné dva názvy událostí nelišily pouze příponou "Start" nebo "Stop". Tento požadavek se odebere počínaje .NET Framework 4.6.2; modul runtime může lišit názvy událostí, které se liší pouze příponou "Start" a "Stop".</span><span class="sxs-lookup"><span data-stu-id="160fc-106">To prevent the exception, ensure that no two event names differ only by a "Start" or "Stop" suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the "Start" and "Stop" suffix.</span></span>

| <span data-ttu-id="160fc-107">Name</span><span class="sxs-lookup"><span data-stu-id="160fc-107">Name</span></span>    | <span data-ttu-id="160fc-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="160fc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="160fc-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="160fc-109">Scope</span></span>   | <span data-ttu-id="160fc-110">Edge</span><span class="sxs-lookup"><span data-stu-id="160fc-110">Edge</span></span>        |
| <span data-ttu-id="160fc-111">Verze</span><span class="sxs-lookup"><span data-stu-id="160fc-111">Version</span></span> | <span data-ttu-id="160fc-112">4.6</span><span class="sxs-lookup"><span data-stu-id="160fc-112">4.6</span></span>         |
| <span data-ttu-id="160fc-113">Typ</span><span class="sxs-lookup"><span data-stu-id="160fc-113">Type</span></span>    | <span data-ttu-id="160fc-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="160fc-114">Retargeting</span></span> |
