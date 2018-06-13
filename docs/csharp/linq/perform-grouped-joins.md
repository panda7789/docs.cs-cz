---
title: Provádění seskupených spojení
description: Postup provádění seskupených spojení.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288174"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="110ef-103">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="110ef-103">Perform grouped joins</span></span>

<span data-ttu-id="110ef-104">Připojení skupiny jsou užitečné pro vytváření hierarchické datové struktury.</span><span class="sxs-lookup"><span data-stu-id="110ef-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="110ef-105">Je to dvojice každý prvek z první kolekce sadu korelační elementy z druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="110ef-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="110ef-106">Například třídu nebo tabulku relační databáze s názvem `Student` může obsahovat dvě pole: `Id` a `Name`.</span><span class="sxs-lookup"><span data-stu-id="110ef-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="110ef-107">Tabulku druhé třídy nebo relační databáze s názvem `Course` může obsahovat dvě pole: `StudentId` a `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="110ef-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="110ef-108">Skupiny připojení z těchto dvou zdrojů dat, na základě shody `Student.Id` a `Course.StudentId`, by skupiny každý `Student` s kolekcí `Course` objekty (které mohou být prázdné).</span><span class="sxs-lookup"><span data-stu-id="110ef-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="110ef-109">Každý prvek první kolekce se zobrazí v sadě výsledků dotazu spojení skupiny bez ohledu na to, jestli se nacházejí korelační elementy v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="110ef-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="110ef-110">V případě, kde nebyly nalezeny žádné korelační elementy je prázdný pořadí elementů korelační pro daný element.</span><span class="sxs-lookup"><span data-stu-id="110ef-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="110ef-111">Selektor výsledek proto má přístup k každý element první kolekce.</span><span class="sxs-lookup"><span data-stu-id="110ef-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="110ef-112">To se liší od výsledku selektoru v mimo skupinu spojení, které nelze získat přístup elementy z první kolekci, které mají žádná shoda v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="110ef-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="110ef-113">V prvním příkladu v tomto tématu se dozvíte, jak provést připojení k skupiny.</span><span class="sxs-lookup"><span data-stu-id="110ef-113">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="110ef-114">V druhém příkladu se dozvíte, jak vytvořit elementů XML pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="110ef-114">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="110ef-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="110ef-115">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="110ef-116">Příklad spojení skupiny</span><span class="sxs-lookup"><span data-stu-id="110ef-116">Group join example</span></span>  
 <span data-ttu-id="110ef-117">Následující příklad spojí skupinu objektů typu `Person` a `Pet` na základě `Person` odpovídající `Pet.Owner` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="110ef-117">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="110ef-118">Na rozdíl od jiných skupiny spojení, které byste mohli vytvořit pár elementů pro každý shodu, vytvoří spojení skupiny pouze jeden výsledný objekt pro každý prvek první kolekce, která v tomto příkladu je `Person` objektu.</span><span class="sxs-lookup"><span data-stu-id="110ef-118">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="110ef-119">Odpovídající elementy z druhé kolekci, které v tomto příkladu jsou `Pet` objekty, jsou seskupeny do kolekce.</span><span class="sxs-lookup"><span data-stu-id="110ef-119">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="110ef-120">Nakonec funkce selektor výsledek vytvoří anonymní typ pro každý shodu, která se skládá z `Person.FirstName` a kolekce `Pet` objekty.</span><span class="sxs-lookup"><span data-stu-id="110ef-120">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="110ef-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="110ef-121">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="110ef-122">Připojení skupiny pro vytvoření ukázkový kód XML</span><span class="sxs-lookup"><span data-stu-id="110ef-122">Group join to create XML example</span></span>  
 <span data-ttu-id="110ef-123">Group JOIN – klauzule jsou ideální pro vytvoření XML s použitím technologie LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="110ef-123">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="110ef-124">V následujícím příkladu je podobně jako v předchozím příkladu s tím rozdílem, že místo vytvoření anonymní typy, vytvoří funkce selektor výsledek elementů XML, které představují připojených objektů.</span><span class="sxs-lookup"><span data-stu-id="110ef-124">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="110ef-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="110ef-125">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="110ef-126">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="110ef-126">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="110ef-127">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="110ef-127">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="110ef-128">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="110ef-128">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
