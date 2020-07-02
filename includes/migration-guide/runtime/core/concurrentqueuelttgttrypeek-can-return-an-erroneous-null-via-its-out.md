---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622052"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="c69ed-101">ConcurrentQueue &lt; T &gt; . Metodě trypeek může vrátit chybnou hodnotu null prostřednictvím parametru out.</span><span class="sxs-lookup"><span data-stu-id="c69ed-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="c69ed-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c69ed-102">Details</span></span>

<span data-ttu-id="c69ed-103">V některých scénářích s více vlákny <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> může vrátit hodnotu true, ale vyplnit výstupní parametr hodnotou null (namísto správné, prohlížené hodnoty).</span><span class="sxs-lookup"><span data-stu-id="c69ed-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c69ed-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="c69ed-104">Suggestion</span></span>

<span data-ttu-id="c69ed-105">Tento problém je opravený ve .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="c69ed-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="c69ed-106">Upgrade na tuto architekturu vyřeší tento problém.</span><span class="sxs-lookup"><span data-stu-id="c69ed-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="c69ed-107">Name</span><span class="sxs-lookup"><span data-stu-id="c69ed-107">Name</span></span>    | <span data-ttu-id="c69ed-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c69ed-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c69ed-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c69ed-109">Scope</span></span>   |<span data-ttu-id="c69ed-110">Hlavní</span><span class="sxs-lookup"><span data-stu-id="c69ed-110">Major</span></span>|
|<span data-ttu-id="c69ed-111">Verze</span><span class="sxs-lookup"><span data-stu-id="c69ed-111">Version</span></span>|<span data-ttu-id="c69ed-112">4.5</span><span class="sxs-lookup"><span data-stu-id="c69ed-112">4.5</span></span>|
|<span data-ttu-id="c69ed-113">Typ</span><span class="sxs-lookup"><span data-stu-id="c69ed-113">Type</span></span>|<span data-ttu-id="c69ed-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c69ed-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c69ed-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c69ed-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
