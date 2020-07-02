---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617222"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="6171a-101">Seznam &lt; T &gt; . ForEach může vyvolat výjimku při změně položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="6171a-101">List&lt;T&gt;.ForEach can throw exception when modifying list item</span></span>

#### <a name="details"></a><span data-ttu-id="6171a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6171a-102">Details</span></span>

<span data-ttu-id="6171a-103">Počínaje .NET Framework 4,5, <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerátor vyvolá <xref:System.InvalidOperationException?displayProperty=fullName> výjimku, pokud je změněn element v kolekci volání.</span><span class="sxs-lookup"><span data-stu-id="6171a-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=fullName> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="6171a-104">Dřív to nevyvolalo výjimku, ale může vést ke konfliktům časování.</span><span class="sxs-lookup"><span data-stu-id="6171a-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6171a-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="6171a-105">Suggestion</span></span>

<span data-ttu-id="6171a-106">V ideálním případě by měl být kód při vytváření výčtu svých prvků vyřešen, aby se seznamy nezměnily, protože to není nikdy bezpečná operace.</span><span class="sxs-lookup"><span data-stu-id="6171a-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="6171a-107">Pokud se chcete vrátit k předchozímu chování, může se stát, že se aplikace bude cílit .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="6171a-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>

| <span data-ttu-id="6171a-108">Name</span><span class="sxs-lookup"><span data-stu-id="6171a-108">Name</span></span>    | <span data-ttu-id="6171a-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6171a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6171a-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6171a-110">Scope</span></span>   | <span data-ttu-id="6171a-111">Edge</span><span class="sxs-lookup"><span data-stu-id="6171a-111">Edge</span></span>        |
| <span data-ttu-id="6171a-112">Verze</span><span class="sxs-lookup"><span data-stu-id="6171a-112">Version</span></span> | <span data-ttu-id="6171a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="6171a-113">4.5</span></span>         |
| <span data-ttu-id="6171a-114">Typ</span><span class="sxs-lookup"><span data-stu-id="6171a-114">Type</span></span>    | <span data-ttu-id="6171a-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="6171a-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6171a-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6171a-116">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
