---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619981"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="3c0b6-101">List. Sort – algoritmus se změnil.</span><span class="sxs-lookup"><span data-stu-id="3c0b6-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="3c0b6-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3c0b6-102">Details</span></span>

<span data-ttu-id="3c0b6-103">Počínaje .NET Framework 4,5 se <xref:System.Collections.Generic.List%601?displayProperty=fullName> algoritmus řazení změnil (aby bylo řazení introspective místo rychlého řazení).</span><span class="sxs-lookup"><span data-stu-id="3c0b6-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="3c0b6-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>řazení nikdy nebylo stabilní, ale tato změna může způsobit nestabilní způsoby řazení různých scénářů.</span><span class="sxs-lookup"><span data-stu-id="3c0b6-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="3c0b6-105">To jednoduše znamená, že ekvivalentní položky mohou být seřazeny v různých objednávkách v následných voláních rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3c0b6-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3c0b6-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="3c0b6-106">Suggestion</span></span>

<span data-ttu-id="3c0b6-107">Vzhledem k tomu, že starý algoritmus řazení byl také nestabilní (ale mírně různými způsoby), neměl by být žádný kód, který závisí na ekvivalentních položkách, vždy řadit v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="3c0b6-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="3c0b6-108">Pokud existují instance kódu v závislosti na tom, že se štěstí se starým chováním, měl by se tento kód aktualizovat, aby se použila porovnávací položka, která bude deterministické seřazení položek v požadovaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3c0b6-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="3c0b6-109">Name</span><span class="sxs-lookup"><span data-stu-id="3c0b6-109">Name</span></span>    | <span data-ttu-id="3c0b6-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c0b6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3c0b6-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3c0b6-111">Scope</span></span>   |<span data-ttu-id="3c0b6-112">Průhlednost</span><span class="sxs-lookup"><span data-stu-id="3c0b6-112">Transparent</span></span>|
|<span data-ttu-id="3c0b6-113">Verze</span><span class="sxs-lookup"><span data-stu-id="3c0b6-113">Version</span></span>|<span data-ttu-id="3c0b6-114">4.5</span><span class="sxs-lookup"><span data-stu-id="3c0b6-114">4.5</span></span>|
|<span data-ttu-id="3c0b6-115">Typ</span><span class="sxs-lookup"><span data-stu-id="3c0b6-115">Type</span></span>|<span data-ttu-id="3c0b6-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3c0b6-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c0b6-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3c0b6-117">Affected APIs</span></span>

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
