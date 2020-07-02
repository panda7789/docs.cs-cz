---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620032"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="7582c-101">Vyčíslitelné. Empty &lt; TResult &gt; vždycky vrátí instanci uloženou v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="7582c-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="7582c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7582c-102">Details</span></span>

<span data-ttu-id="7582c-103">Počínaje .NET Framework 4,5 <xref:System.Linq.Enumerable.Empty%60%601> vždy vrátí interní instanci uloženou v mezipaměti <xref:System.Collections.Generic.IEnumerable%601> . Dřív <xref:System.Linq.Enumerable.Empty%60%601> by do mezipaměti bylo v <xref:System.Collections.Generic.IEnumerable%601> době volání rozhraní API prázdné, což znamená, že v některých podmínkách, které <xref:System.Linq.Enumerable.Empty%60%601> byly volány rychle a souběžně, mohou být vráceny různé instance typu pro různá volání rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7582c-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7582c-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="7582c-104">Suggestion</span></span>

<span data-ttu-id="7582c-105">Vzhledem k tomu, že předchozí chování nebylo deterministické, je pravděpodobné, že na něm závisí kód.</span><span class="sxs-lookup"><span data-stu-id="7582c-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="7582c-106">Nicméně v nepravděpodobném případě, že jsou vypočítány prázdné výčty a očekává se, že jsou někdy stejné, explicitní prázdná pole by měla být vytvořena ( <code>new T[0]</code> ) namísto použití <xref:System.Linq.Enumerable.Empty%60%601> .</span><span class="sxs-lookup"><span data-stu-id="7582c-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="7582c-107">Name</span><span class="sxs-lookup"><span data-stu-id="7582c-107">Name</span></span>    | <span data-ttu-id="7582c-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7582c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7582c-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7582c-109">Scope</span></span>   |<span data-ttu-id="7582c-110">Edge</span><span class="sxs-lookup"><span data-stu-id="7582c-110">Edge</span></span>|
|<span data-ttu-id="7582c-111">Verze</span><span class="sxs-lookup"><span data-stu-id="7582c-111">Version</span></span>|<span data-ttu-id="7582c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="7582c-112">4.5</span></span>|
|<span data-ttu-id="7582c-113">Typ</span><span class="sxs-lookup"><span data-stu-id="7582c-113">Type</span></span>|<span data-ttu-id="7582c-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="7582c-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7582c-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7582c-115">Affected APIs</span></span>

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
