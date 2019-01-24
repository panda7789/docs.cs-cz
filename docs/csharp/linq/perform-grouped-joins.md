---
title: Provádění seskupených spojení (LINQ v JAZYKU C#)
description: Zjistěte, jak k provádění seskupených spojení pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: d8a2d7bbbe78d3fc1f2518e057ade5045cee43e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511824"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="ba581-103">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="ba581-103">Perform grouped joins</span></span>

<span data-ttu-id="ba581-104">Spojení skupiny je užitečné při vytváření hierarchických datové struktury.</span><span class="sxs-lookup"><span data-stu-id="ba581-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="ba581-105">Je to dvojice každý prvek od první kolekce sadu korelační prvky z druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="ba581-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="ba581-106">Například třída nebo relační databázi tabulku s názvem `Student` může obsahovat dvě pole: `Id` a `Name`.</span><span class="sxs-lookup"><span data-stu-id="ba581-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="ba581-107">Druhé třídy nebo relační databázi tabulku s názvem `Course` může obsahovat dvě pole: `StudentId` a `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="ba581-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="ba581-108">Skupiny spojení těchto dvou zdrojů dat, na základě porovnání `Student.Id` a `Course.StudentId`, by každé skupině `Student` sbírka `Course` objekty (které můžou být prázdné).</span><span class="sxs-lookup"><span data-stu-id="ba581-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="ba581-109">Každý prvek první kolekce se zobrazí v sadě výsledků spojení skupiny bez ohledu na to, jestli se korelační elementy nacházejí v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="ba581-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="ba581-110">V tomto případě se nenašly žádné korelační prvky je prázdná sekvence korelační prvků tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="ba581-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="ba581-111">Výběr výsledku proto má přístup k každý prvek první kolekce.</span><span class="sxs-lookup"><span data-stu-id="ba581-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="ba581-112">Tím se liší od výsledku selektoru v jiné skupině spojení, které nelze přistupovat k prvkům z první kolekce, které nemají žádná shoda v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="ba581-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="ba581-113">První příklad v tomto článku se dozvíte, jak provést spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="ba581-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="ba581-114">Druhý příklad ukazuje, jak vytvořit elementů XML pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="ba581-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="ba581-115">Příklad - Group join</span><span class="sxs-lookup"><span data-stu-id="ba581-115">Example - Group join</span></span>

<span data-ttu-id="ba581-116">Následující příklad provádí spojení skupiny objektů typu `Person` a `Pet` na základě `Person` odpovídající `Pet.Owner` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ba581-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="ba581-117">Na rozdíl od jiných skupiny spojení, které byste mohli vytvořit dvojici prvků pro jednotlivé shody, spojení skupiny vytváří jediný výsledný objekt pro každý prvek první kolekce, která v tomto příkladu je `Person` objektu.</span><span class="sxs-lookup"><span data-stu-id="ba581-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="ba581-118">Odpovídající prvky z druhého kolekce, které v tomto příkladu jsou `Pet` objekty, jsou seskupené do kolekce.</span><span class="sxs-lookup"><span data-stu-id="ba581-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="ba581-119">Nakonec funkce selektor výsledek vytvoří anonymního typu pro jednotlivé shody, který se skládá z `Person.FirstName` a kolekce `Pet` objekty.</span><span class="sxs-lookup"><span data-stu-id="ba581-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="ba581-120">Příklad - Group join k vytvoření XML</span><span class="sxs-lookup"><span data-stu-id="ba581-120">Example - Group join to create XML</span></span>

<span data-ttu-id="ba581-121">Group JOIN – klauzule jsou ideální pro vytváření XML pomocí LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="ba581-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="ba581-122">Následující příklad je podobný jako předchozí příklad, s tím rozdílem, že místo vytvoření anonymní typy, funkce selektor výsledek vytvoří elementů XML, které představují připojených objektů.</span><span class="sxs-lookup"><span data-stu-id="ba581-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="ba581-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba581-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="ba581-124">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="ba581-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="ba581-125">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="ba581-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="ba581-126">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="ba581-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
