---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804455"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="ef1f5-101">Názvy událostí ETW se nemohou lišit pouze příponou "Start" nebo "Stop".</span><span class="sxs-lookup"><span data-stu-id="ef1f5-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ef1f5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ef1f5-102">Details</span></span>|<span data-ttu-id="ef1f5-103">V rozhraní .NET Framework 4.6 a 4.6.1 <xref:System.ArgumentException> modul runtime vyvolá při dvou názvech událostí trasování &quot;&quot; událostí &quot;&quot; pro Windows (ETW) <code>LogUser</code> liší pouze <code>LogUserStart</code>příponou Start nebo Stop (jako když je jedna událost pojmenována a druhá je pojmenována ).</span><span class="sxs-lookup"><span data-stu-id="ef1f5-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="ef1f5-104">V tomto případě runtime nelze vytvořit zdroj události, který nemůže vyzařovat žádné protokolování.</span><span class="sxs-lookup"><span data-stu-id="ef1f5-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="ef1f5-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="ef1f5-105">Suggestion</span></span>|<span data-ttu-id="ef1f5-106">Chcete-li zabránit výjimce, ujistěte se,&quot; &quot;že&quot; žádné dva názvy událostí se liší pouze příponou &quot;Start nebo Stop. Tento požadavek je odebrán počínaje rozhraním .NET Framework 4.6.2; modul runtime může rozptýlit názvy událostí, &quot;které&quot; &quot;se&quot; liší pouze příponou Start a Stop.</span><span class="sxs-lookup"><span data-stu-id="ef1f5-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="ef1f5-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ef1f5-107">Scope</span></span>|<span data-ttu-id="ef1f5-108">Edge</span><span class="sxs-lookup"><span data-stu-id="ef1f5-108">Edge</span></span>|
|<span data-ttu-id="ef1f5-109">Version</span><span class="sxs-lookup"><span data-stu-id="ef1f5-109">Version</span></span>|<span data-ttu-id="ef1f5-110">4.6</span><span class="sxs-lookup"><span data-stu-id="ef1f5-110">4.6</span></span>|
|<span data-ttu-id="ef1f5-111">Typ</span><span class="sxs-lookup"><span data-stu-id="ef1f5-111">Type</span></span>|<span data-ttu-id="ef1f5-112">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="ef1f5-112">Retargeting</span></span>|
