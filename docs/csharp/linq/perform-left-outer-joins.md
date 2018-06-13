---
title: Provedení levých vnějších spojení
description: Postup provedení levých vnějších spojení.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: aacab1ac6f4ab2c10b393cf0b2c578a13d9b9306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284274"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="a553e-103">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="a553e-103">Perform left outer joins</span></span>
<span data-ttu-id="a553e-104">Levé vnější spojení je výsledkem spojení v které každý prvek první kolekce se vrátí, bez ohledu na to, jestli má všechny korelační elementy v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="a553e-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="a553e-105">Je možné použít k provedení levé vnější spojení voláním LINQ <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metoda na výsledcích skupiny spojení.</span><span class="sxs-lookup"><span data-stu-id="a553e-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a553e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a553e-106">Example</span></span>  
 <span data-ttu-id="a553e-107">Následující příklad ukazuje, jak používat <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metoda na výsledcích spojení skupiny účelem levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="a553e-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="a553e-108">Prvním krokem při vytváření levé vnější spojení dvou kolekcí je provést vnitřní spojení pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="a553e-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="a553e-109">(Viz [provádění vnitřních spojení](perform-inner-joins.md) vysvětlení tohoto procesu.) V tomto příkladu seznam `Person` objektů je připojený k vnitřní do seznamu `Pet` na základě objektů `Person` objekt, který odpovídá `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="a553e-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="a553e-110">Druhým krokem je zahrnout každý prvek první kolekce (levém) i v případě, že element má žádné odpovídající položky v pravém kolekci sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="a553e-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="a553e-111">To lze provést voláním <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na každé pořadí odpovídajících prvky ze skupiny spojení.</span><span class="sxs-lookup"><span data-stu-id="a553e-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="a553e-112">V tomto příkladu <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> se volá na každé pořadí odpovídajících `Pet` objekty.</span><span class="sxs-lookup"><span data-stu-id="a553e-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="a553e-113">Vrátí kolekci, která obsahuje jednu, výchozí hodnotu, pokud metoda pořadí odpovídajících `Pet` je prázdná pro všechny objekty `Person` objekt, a zajistí tak, aby se každý `Person` objekt je znázorněn v kolekci výsledek.</span><span class="sxs-lookup"><span data-stu-id="a553e-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a553e-114">Výchozí hodnota pro typ odkaz je `null`; proto v příkladu vyhledává odkaz s hodnotou null před přístupem k každý prvek jednotlivých `Pet` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a553e-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="a553e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a553e-115">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="a553e-116">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="a553e-116">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="a553e-117">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="a553e-117">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="a553e-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="a553e-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
