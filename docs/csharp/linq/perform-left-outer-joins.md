---
title: "Provedení levých vnějších spojení"
description: "Postup provedení levých vnějších spojení."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 0c28c85bf933a411403aefcb91801d28fe1c268e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="a5061-104">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="a5061-104">Perform left outer joins</span></span>
<span data-ttu-id="a5061-105">Levé vnější spojení je výsledkem spojení v které každý prvek první kolekce se vrátí, bez ohledu na to, jestli má všechny korelační elementy v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="a5061-105">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="a5061-106">Je možné použít k provedení levé vnější spojení voláním LINQ <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metoda na výsledcích skupiny spojení.</span><span class="sxs-lookup"><span data-stu-id="a5061-106">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5061-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5061-107">Example</span></span>  
 <span data-ttu-id="a5061-108">Následující příklad ukazuje, jak používat <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metoda na výsledcích spojení skupiny účelem levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="a5061-108">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="a5061-109">Prvním krokem při vytváření levé vnější spojení dvou kolekcí je provést vnitřní spojení pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="a5061-109">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="a5061-110">(Viz [provádění vnitřních spojení](perform-inner-joins.md) vysvětlení tohoto procesu.) V tomto příkladu seznam `Person` objektů je připojený k vnitřní do seznamu `Pet` na základě objektů `Person` objekt, který odpovídá `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="a5061-110">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="a5061-111">Druhým krokem je zahrnout každý prvek první kolekce (levém) i v případě, že element má žádné odpovídající položky v pravém kolekci sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="a5061-111">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="a5061-112">To lze provést voláním <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na každé pořadí odpovídajících prvky ze skupiny spojení.</span><span class="sxs-lookup"><span data-stu-id="a5061-112">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="a5061-113">V tomto příkladu <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> se volá na každé pořadí odpovídajících `Pet` objekty.</span><span class="sxs-lookup"><span data-stu-id="a5061-113">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="a5061-114">Vrátí kolekci, která obsahuje jednu, výchozí hodnotu, pokud metoda pořadí odpovídajících `Pet` je prázdná pro všechny objekty `Person` objekt, a zajistí tak, aby se každý `Person` objekt je znázorněn v kolekci výsledek.</span><span class="sxs-lookup"><span data-stu-id="a5061-114">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5061-115">Výchozí hodnota pro typ odkaz je `null`; proto v příkladu vyhledává odkaz s hodnotou null před přístupem k každý prvek jednotlivých `Pet` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a5061-115">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="a5061-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5061-116">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="a5061-117">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="a5061-117">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="a5061-118">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="a5061-118">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="a5061-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a5061-119">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
