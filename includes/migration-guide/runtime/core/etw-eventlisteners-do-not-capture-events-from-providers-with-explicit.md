---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619972"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="e14c8-101">ETW EventListeners nezachycuje události od zprostředkovatelů s explicitními klíčovými slovy (jako poskytovatel TPL).</span><span class="sxs-lookup"><span data-stu-id="e14c8-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

#### <a name="details"></a><span data-ttu-id="e14c8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e14c8-102">Details</span></span>

<span data-ttu-id="e14c8-103">ETW EventListeners s prázdnou maskou klíčového slova nezachycuje správně události od zprostředkovatelů s explicitními klíčovými slovy.</span><span class="sxs-lookup"><span data-stu-id="e14c8-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="e14c8-104">V .NET Framework 4,5 poskytovatel TPL začal poskytovat explicitní klíčová slova a aktivoval tento problém.</span><span class="sxs-lookup"><span data-stu-id="e14c8-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="e14c8-105">V .NET Framework 4,6 se EventListeners aktualizace, aby už nedošlo k tomuto problému.</span><span class="sxs-lookup"><span data-stu-id="e14c8-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e14c8-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="e14c8-106">Suggestion</span></span>

<span data-ttu-id="e14c8-107">Chcete-li tento problém obejít, nahraďte volání voláním <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> metody přetížení EnableEvents, která explicitně určuje &quot; masku klíčového slova, která &quot; se má použít: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code> . Případně byl tento problém opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e14c8-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="e14c8-108">Name</span><span class="sxs-lookup"><span data-stu-id="e14c8-108">Name</span></span>    | <span data-ttu-id="e14c8-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e14c8-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e14c8-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e14c8-110">Scope</span></span>   |<span data-ttu-id="e14c8-111">Edge</span><span class="sxs-lookup"><span data-stu-id="e14c8-111">Edge</span></span>|
|<span data-ttu-id="e14c8-112">Verze</span><span class="sxs-lookup"><span data-stu-id="e14c8-112">Version</span></span>|<span data-ttu-id="e14c8-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e14c8-113">4.5</span></span>|
|<span data-ttu-id="e14c8-114">Typ</span><span class="sxs-lookup"><span data-stu-id="e14c8-114">Type</span></span>|<span data-ttu-id="e14c8-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e14c8-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e14c8-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e14c8-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
