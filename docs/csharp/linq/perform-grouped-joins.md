---
title: Provedení seskupených spojení (LINQ v C#)
description: Zjistěte, jak provádět seskupená spojení pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689135"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="f2b2f-103">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="f2b2f-103">Perform grouped joins</span></span>

<span data-ttu-id="f2b2f-104">Spojení skupiny je užitečné pro vytváření hierarchických datových struktur.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="f2b2f-105">Spáruje každý prvek z první kolekce se sadou korelovaných prvků z druhé kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="f2b2f-106">Například třída nebo relační databázová tabulka s názvem `Student` může obsahovat dvě pole: `Id` a `Name`.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="f2b2f-107">Druhá třída nebo relační `Course` databázová tabulka `StudentId` `CourseTitle`s názvem může obsahovat dvě pole: a .</span><span class="sxs-lookup"><span data-stu-id="f2b2f-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="f2b2f-108">Spojení skupiny těchto dvou zdrojů dat, `Course.StudentId`založené na `Student` porovnávání `Student.Id` `Course` a , by seskupit každý s kolekcí objektů (které mohou být prázdné).</span><span class="sxs-lookup"><span data-stu-id="f2b2f-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="f2b2f-109">Každý prvek první kolekce se zobrazí ve výsledkové sadě skupiny spojení bez ohledu na to, zda korelované prvky jsou nalezeny v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="f2b2f-110">V případě, kde jsou nalezeny žádné korelační prvky, pořadí korelovaných prvků pro tento prvek je prázdný.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="f2b2f-111">Volič výsledků má proto přístup ke každému prvku první kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="f2b2f-112">To se liší od voliče výsledků v neskupinovém spojení, které nemají přístup k prvkům z první kolekce, které nemají žádnou shodu v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="f2b2f-113">První příklad v tomto článku ukazuje, jak provést připojení ke skupině.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="f2b2f-114">Druhý příklad ukazuje, jak pomocí skupinového spojení vytvořit elementy XML.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="f2b2f-115">Příklad - Skupinové spojení</span><span class="sxs-lookup"><span data-stu-id="f2b2f-115">Example - Group join</span></span>

<span data-ttu-id="f2b2f-116">Následující příklad provádí skupinové spojení `Person` objektů `Pet` typu `Person` a `Pet.Owner` na základě odpovídající vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="f2b2f-117">Na rozdíl od spojení bez skupiny, které by vytvořilo dvojici prvků pro každou shodu, spojení skupiny vytvoří `Person` pouze jeden výsledný objekt pro každý prvek první kolekce, který v tomto příkladu je objekt.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="f2b2f-118">Odpovídající prvky z druhé kolekce, které `Pet` v tomto příkladu jsou objekty, jsou seskupeny do kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="f2b2f-119">Nakonec funkce selektoru výsledků vytvoří anonymní typ pro `Person.FirstName` každou shodu, která se skládá z `Pet` a kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="f2b2f-120">Příklad - Seskupit spojení pro vytvoření XML</span><span class="sxs-lookup"><span data-stu-id="f2b2f-120">Example - Group join to create XML</span></span>

<span data-ttu-id="f2b2f-121">Spojení skupin jsou ideální pro vytváření XML pomocí LINQ na XML.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="f2b2f-122">Následující příklad je podobný předchozímu příkladu s tím rozdílem, že namísto vytváření anonymních typů vytvoří funkce selektoru výsledků elementy XML, které představují spojené objekty.</span><span class="sxs-lookup"><span data-stu-id="f2b2f-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="f2b2f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2b2f-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="f2b2f-124">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="f2b2f-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="f2b2f-125">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="f2b2f-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="f2b2f-126">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f2b2f-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
