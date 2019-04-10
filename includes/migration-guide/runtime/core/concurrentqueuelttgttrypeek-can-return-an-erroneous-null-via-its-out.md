---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236694"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="c92a5-101">ConcurrentQueue\<T >. Metodě TryPeek může vrátit chybné null prostřednictvím jeho výstupní parametr</span><span class="sxs-lookup"><span data-stu-id="c92a5-101">ConcurrentQueue\<T>.TryPeek can return an erroneous null via its out parameter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c92a5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c92a5-102">Details</span></span>|<span data-ttu-id="c92a5-103">V některých scénářích s více procesy <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> může vrátit hodnotu true, ale vyplnit výstupní parametr s hodnotou null (místo hodnoty správné, nahlédnout).</span><span class="sxs-lookup"><span data-stu-id="c92a5-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>|
|<span data-ttu-id="c92a5-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c92a5-104">Suggestion</span></span>|<span data-ttu-id="c92a5-105">Tento problém je vyřešen v rozhraní .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="c92a5-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="c92a5-106">Upgrade na tento rámec se vyřešit problém.</span><span class="sxs-lookup"><span data-stu-id="c92a5-106">Upgrading to that Framework will solve the issue.</span></span>|
|<span data-ttu-id="c92a5-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c92a5-107">Scope</span></span>|<span data-ttu-id="c92a5-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="c92a5-108">Major</span></span>|
|<span data-ttu-id="c92a5-109">Version</span><span class="sxs-lookup"><span data-stu-id="c92a5-109">Version</span></span>|<span data-ttu-id="c92a5-110">4.5</span><span class="sxs-lookup"><span data-stu-id="c92a5-110">4.5</span></span>|
|<span data-ttu-id="c92a5-111">Type</span><span class="sxs-lookup"><span data-stu-id="c92a5-111">Type</span></span>|<span data-ttu-id="c92a5-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c92a5-112">Runtime</span></span>|
|<span data-ttu-id="c92a5-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c92a5-113">Affected APIs</span></span>|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
