---
ms.openlocfilehash: a8f51dfa1c82e3b166449d2432dfe8a9b96564b9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619951"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="54492-101">Blokujícícollection &lt; T &gt; . TryTakeFromAny už nevyvolává</span><span class="sxs-lookup"><span data-stu-id="54492-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="54492-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="54492-102">Details</span></span>

<span data-ttu-id="54492-103">Je-li jedna ze vstupních kolekcí označena jako dokončená, již <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> nevrací hodnotu-1 a <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> již nevyvolává výjimku.</span><span class="sxs-lookup"><span data-stu-id="54492-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="54492-104">Tato změna umožňuje pracovat s kolekcemi, pokud je jedna z kolekcí prázdná nebo dokončená, ale další kolekce stále obsahuje položky, které lze načíst.</span><span class="sxs-lookup"><span data-stu-id="54492-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="54492-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="54492-105">Suggestion</span></span>

<span data-ttu-id="54492-106">Pokud byla v případě dokončení blokující kolekce použita TryTakeFromAny vracející-1 nebo TakeFromAny, měla by být tento kód změněn, aby se použila <code>.Any(b =&gt; b.IsCompleted)</code> k detekci této podmínky.</span><span class="sxs-lookup"><span data-stu-id="54492-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="54492-107">Name</span><span class="sxs-lookup"><span data-stu-id="54492-107">Name</span></span>    | <span data-ttu-id="54492-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="54492-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="54492-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="54492-109">Scope</span></span>   |<span data-ttu-id="54492-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="54492-110">Minor</span></span>|
|<span data-ttu-id="54492-111">Verze</span><span class="sxs-lookup"><span data-stu-id="54492-111">Version</span></span>|<span data-ttu-id="54492-112">4.5</span><span class="sxs-lookup"><span data-stu-id="54492-112">4.5</span></span>|
|<span data-ttu-id="54492-113">Typ</span><span class="sxs-lookup"><span data-stu-id="54492-113">Type</span></span>|<span data-ttu-id="54492-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="54492-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="54492-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="54492-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|
