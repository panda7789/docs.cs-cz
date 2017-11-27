---
title: "Provádění seskupených spojení"
description: "Postup provádění seskupených spojení."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 5e26473e19a5b6107d7aceea5e9829b48aa522b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="dac44-104">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="dac44-104">Perform grouped joins</span></span>

<span data-ttu-id="dac44-105">Připojení skupiny jsou užitečné pro vytváření hierarchické datové struktury.</span><span class="sxs-lookup"><span data-stu-id="dac44-105">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="dac44-106">Je to dvojice každý prvek z první kolekce sadu korelační elementy z druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="dac44-106">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="dac44-107">Například třídu nebo tabulku relační databáze s názvem `Student` může obsahovat dvě pole: `Id` a `Name`.</span><span class="sxs-lookup"><span data-stu-id="dac44-107">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="dac44-108">Tabulku druhé třídy nebo relační databáze s názvem `Course` může obsahovat dvě pole: `StudentId` a `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="dac44-108">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="dac44-109">Skupiny připojení z těchto dvou zdrojů dat, na základě shody `Student.Id` a `Course.StudentId`, by skupiny každý `Student` s kolekcí `Course` objekty (které mohou být prázdné).</span><span class="sxs-lookup"><span data-stu-id="dac44-109">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dac44-110">Každý prvek první kolekce se zobrazí v sadě výsledků dotazu spojení skupiny bez ohledu na to, jestli se nacházejí korelační elementy v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="dac44-110">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="dac44-111">V případě, kde nebyly nalezeny žádné korelační elementy je prázdný pořadí elementů korelační pro daný element.</span><span class="sxs-lookup"><span data-stu-id="dac44-111">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="dac44-112">Selektor výsledek proto má přístup k každý element první kolekce.</span><span class="sxs-lookup"><span data-stu-id="dac44-112">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="dac44-113">To se liší od výsledku selektoru v mimo skupinu spojení, které nelze získat přístup elementy z první kolekci, které mají žádná shoda v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="dac44-113">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="dac44-114">V prvním příkladu v tomto tématu se dozvíte, jak provést připojení k skupiny.</span><span class="sxs-lookup"><span data-stu-id="dac44-114">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="dac44-115">V druhém příkladu se dozvíte, jak vytvořit elementů XML pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="dac44-115">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dac44-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="dac44-116">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="dac44-117">Příklad spojení skupiny</span><span class="sxs-lookup"><span data-stu-id="dac44-117">Group join example</span></span>  
 <span data-ttu-id="dac44-118">Následující příklad spojí skupinu objektů typu `Person` a `Pet` na základě `Person` odpovídající `Pet.Owner` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dac44-118">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="dac44-119">Na rozdíl od jiných skupiny spojení, které byste mohli vytvořit pár elementů pro každý shodu, vytvoří spojení skupiny pouze jeden výsledný objekt pro každý prvek první kolekce, která v tomto příkladu je `Person` objektu.</span><span class="sxs-lookup"><span data-stu-id="dac44-119">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="dac44-120">Odpovídající elementy z druhé kolekci, které v tomto příkladu jsou `Pet` objekty, jsou seskupeny do kolekce.</span><span class="sxs-lookup"><span data-stu-id="dac44-120">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="dac44-121">Nakonec funkce selektor výsledek vytvoří anonymní typ pro každý shodu, která se skládá z `Person.FirstName` a kolekce `Pet` objekty.</span><span class="sxs-lookup"><span data-stu-id="dac44-121">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="dac44-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="dac44-122">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="dac44-123">Připojení skupiny pro vytvoření ukázkový kód XML</span><span class="sxs-lookup"><span data-stu-id="dac44-123">Group join to create XML example</span></span>  
 <span data-ttu-id="dac44-124">Group JOIN – klauzule jsou ideální pro vytvoření XML s použitím technologie LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="dac44-124">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="dac44-125">V následujícím příkladu je podobně jako v předchozím příkladu s tím rozdílem, že místo vytvoření anonymní typy, vytvoří funkce selektor výsledek elementů XML, které představují připojených objektů.</span><span class="sxs-lookup"><span data-stu-id="dac44-125">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="dac44-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dac44-126">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="dac44-127">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="dac44-127">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="dac44-128">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="dac44-128">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="dac44-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="dac44-129">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
