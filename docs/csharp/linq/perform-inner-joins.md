---
title: "Provádění vnitřních spojení"
description: "Postup provádění vnitřních spojení."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: fdf75c0b7195742bdce70566ebb3880bb0565f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="perform-inner-joins"></a><span data-ttu-id="3044a-104">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="3044a-104">Perform inner joins</span></span>

<span data-ttu-id="3044a-105">V podmínkách relační databáze *vnitřní spojení* vytváří je sada výsledků dotazu, ve kterém každého prvku první kolekce se zobrazí jednou pro každý odpovídající element v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="3044a-105">In relational database terms, an *inner join* produces a result set in which each element of the first collection appears one time for every matching element in the second collection.</span></span> <span data-ttu-id="3044a-106">Pokud element v první kolekce nemá žádné odpovídající prvky, nezobrazí se v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="3044a-106">If an element in the first collection has no matching elements, it does not appear in the result set.</span></span> <span data-ttu-id="3044a-107"><xref:System.Linq.Enumerable.Join%2A> Metodu, která je volána metodou `join` klauzule v jazyce C#, implementuje vnitřní spojení.</span><span class="sxs-lookup"><span data-stu-id="3044a-107">The <xref:System.Linq.Enumerable.Join%2A> method, which is called by the `join` clause in C#, implements an inner join.</span></span>  
  
 <span data-ttu-id="3044a-108">Toto téma ukazuje, jak provést čtyři variace vnitřní spojení:</span><span class="sxs-lookup"><span data-stu-id="3044a-108">This topic shows you how to perform four variations of an inner join:</span></span>  
  
-   <span data-ttu-id="3044a-109">Jednoduché vnitřní spojení, které koreluje elementy ze dvou zdrojů dat na základě jednoduché klíče.</span><span class="sxs-lookup"><span data-stu-id="3044a-109">A simple inner join that correlates elements from two data sources based on a simple key.</span></span>  
  
-   <span data-ttu-id="3044a-110">Vnitřní spojení, které koreluje elementy ze dvou zdrojů dat na základě *složené* klíč.</span><span class="sxs-lookup"><span data-stu-id="3044a-110">An inner join that correlates elements from two data sources based on a *composite* key.</span></span> <span data-ttu-id="3044a-111">Složený klíč, který je klíč, který se skládá z více než jednu hodnotu, umožňuje korelovat prvky založené na více než jednu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3044a-111">A composite key, which is a key that consists of more than one value, enables you to correlate elements based on more than one property.</span></span>  
  
-   <span data-ttu-id="3044a-112">A *více spojení* v které následných spojení jsou operace přidat k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="3044a-112">A *multiple join* in which successive join operations are appended to each other.</span></span>  
  
-   <span data-ttu-id="3044a-113">Vnitřní spojení, které je implementována pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="3044a-113">An inner join that is implemented by using a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3044a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3044a-114">Example</span></span>  
  
## <a name="simple-key-join-example"></a><span data-ttu-id="3044a-115">Příklad jednoduchého klíče připojení</span><span class="sxs-lookup"><span data-stu-id="3044a-115">Simple key join example</span></span>  
 <span data-ttu-id="3044a-116">Následující příklad vytvoří dvě kolekce, které obsahují objekty dvou uživatelem definované typy `Person` a `Pet`.</span><span class="sxs-lookup"><span data-stu-id="3044a-116">The following example creates two collections that contain objects of two user-defined types, `Person` and `Pet`.</span></span> <span data-ttu-id="3044a-117">Dotaz používá `join` klauzule v jazyce C# tak, aby odpovídaly `Person` objekty s `Pet` objekty, jehož `Owner` je, že `Person`.</span><span class="sxs-lookup"><span data-stu-id="3044a-117">The query uses the `join` clause in C# to match `Person` objects with `Pet` objects whose `Owner` is that `Person`.</span></span> <span data-ttu-id="3044a-118">`select` Klauzule v jazyce C# definuje, jak bude vypadat výsledných objektech.</span><span class="sxs-lookup"><span data-stu-id="3044a-118">The `select` clause in C# defines how the resulting objects will look.</span></span> <span data-ttu-id="3044a-119">V tomto příkladu jsou výsledných objektech anonymní typy, které se skládají z vlastníka křestní jméno a název pet.</span><span class="sxs-lookup"><span data-stu-id="3044a-119">In this example the resulting objects are anonymous types that consist of the owner's first name and the pet's name.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#1](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]  
  
 <span data-ttu-id="3044a-120">Všimněte si, že `Person` objekt, jehož `LastName` je "Huff" v sadě výsledků, protože je nezobrazí žádné `Pet` objekt, který má `Pet.Owner` rovnající se `Person`.</span><span class="sxs-lookup"><span data-stu-id="3044a-120">Note that the `Person` object whose `LastName` is "Huff" does not appear in the result set because there is no `Pet` object that has `Pet.Owner` equal to that `Person`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3044a-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="3044a-121">Example</span></span>  
  
## <a name="composite-key-join-example"></a><span data-ttu-id="3044a-122">Příklad složeného klíče připojení</span><span class="sxs-lookup"><span data-stu-id="3044a-122">Composite key join example</span></span>  
 <span data-ttu-id="3044a-123">Místo korelace prvky založené na právě jednu vlastnost, můžete porovnat elementy na víc vlastností na základě složený klíč.</span><span class="sxs-lookup"><span data-stu-id="3044a-123">Instead of correlating elements based on just one property, you can use a composite key to compare elements based on multiple properties.</span></span> <span data-ttu-id="3044a-124">Chcete-li to provést, zadejte funkci selektoru klíče pro každou kolekci vrátit anonymní typ, který se skládá z vlastnosti, které chcete porovnat.</span><span class="sxs-lookup"><span data-stu-id="3044a-124">To do this, specify the key selector function for each collection to return an anonymous type that consists of the properties you want to compare.</span></span> <span data-ttu-id="3044a-125">Pokud můžete označit vlastnosti, musí mít stejný popisek v anonymního typu každý klíč.</span><span class="sxs-lookup"><span data-stu-id="3044a-125">If you label the properties, they must have the same label in each key's anonymous type.</span></span> <span data-ttu-id="3044a-126">Vlastnosti musí být také ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3044a-126">The properties must also appear in the same order.</span></span>  
  
 <span data-ttu-id="3044a-127">Následující příklad používá seznam `Employee` objekty a seznam `Student` objekty, které chcete určit, které zaměstnanci jsou také studenty.</span><span class="sxs-lookup"><span data-stu-id="3044a-127">The following example uses a list of `Employee` objects and a list of `Student` objects to determine which employees are also students.</span></span> <span data-ttu-id="3044a-128">Mají obě tyto typy `FirstName` a `LastName` vlastnost typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3044a-128">Both of these types have a `FirstName` and a `LastName` property of type <xref:System.String>.</span></span> <span data-ttu-id="3044a-129">Vrátí instanci anonymního typu, který se skládá z funkcí, které vytvoří připojení k klíče z každé seznamu elementů `FirstName` a `LastName` vlastnosti každého prvku.</span><span class="sxs-lookup"><span data-stu-id="3044a-129">The functions that create the join keys from each list's elements return an anonymous type that consists of the `FirstName` and `LastName` properties of each element.</span></span> <span data-ttu-id="3044a-130">Operace spojení porovná tyto složené klíče rovnosti a vrátí páry objektů z každého seznamu tam, kde křestní jméno a příjmení shodují.</span><span class="sxs-lookup"><span data-stu-id="3044a-130">The join operation compares these composite keys for equality and returns pairs of objects from each list where both the first name and the last name match.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#2](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="3044a-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="3044a-131">Example</span></span>  
  
## <a name="multiple-join-example"></a><span data-ttu-id="3044a-132">Příklad více připojení k</span><span class="sxs-lookup"><span data-stu-id="3044a-132">Multiple join example</span></span>  
 <span data-ttu-id="3044a-133">Libovolný počet operací spojování můžete připojit k jiné k provedení více připojení.</span><span class="sxs-lookup"><span data-stu-id="3044a-133">Any number of join operations can be appended to each other to perform a multiple join.</span></span> <span data-ttu-id="3044a-134">Každý `join` klauzule v jazyce C# korelaci zadaný zdroj dat s výsledky předchozí spojení.</span><span class="sxs-lookup"><span data-stu-id="3044a-134">Each `join` clause in C# correlates a specified data source with the results of the previous join.</span></span>  
  
 <span data-ttu-id="3044a-135">Následující příklad vytvoří tři kolekce: seznam `Person` objekty, seznam `Cat` objekty a seznam `Dog` objekty.</span><span class="sxs-lookup"><span data-stu-id="3044a-135">The following example creates three collections: a list of `Person` objects, a list of `Cat` objects, and a list of `Dog` objects.</span></span>  
  
 <span data-ttu-id="3044a-136">První `join` klauzule v jazyce C# odpovídá osoby a na základě kočky `Person` odpovídající objekt `Cat.Owner`.</span><span class="sxs-lookup"><span data-stu-id="3044a-136">The first `join` clause in C# matches people and cats based on a `Person` object matching `Cat.Owner`.</span></span> <span data-ttu-id="3044a-137">Vrátí posloupnost anonymní typy, které obsahují `Person` objektu a `Cat.Name`.</span><span class="sxs-lookup"><span data-stu-id="3044a-137">It returns a sequence of anonymous types that contain the `Person` object and `Cat.Name`.</span></span>  
  
 <span data-ttu-id="3044a-138">Druhý `join` klauzule v jazyce C# korelaci anonymní typy vrácený toto spojení s `Dog` objekty v zadaný seznam psi, podle složený klíč, který se skládá z `Owner` vlastnost typu `Person`a první písmeno názvu zvířat.</span><span class="sxs-lookup"><span data-stu-id="3044a-138">The second `join` clause in C# correlates the anonymous types returned by the first join with `Dog` objects in the supplied list of dogs, based on a composite key that consists of the `Owner` property of type `Person`, and the first letter of the animal's name.</span></span> <span data-ttu-id="3044a-139">Vrátí posloupnost anonymní typy, které obsahují `Cat.Name` a `Dog.Name` vlastnosti z každý odpovídající pár.</span><span class="sxs-lookup"><span data-stu-id="3044a-139">It returns a sequence of anonymous types that contain the `Cat.Name` and `Dog.Name` properties from each matching pair.</span></span> <span data-ttu-id="3044a-140">Protože se jedná o vnitřní spojení, se vrátí pouze ty objekty z první zdroj dat se shodnou ve zdroji dat druhý.</span><span class="sxs-lookup"><span data-stu-id="3044a-140">Because this is an inner join, only those objects from the first data source that have a match in the second data source are returned.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#3](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="3044a-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="3044a-141">Example</span></span>  
  
## <a name="inner-join-by-using-grouped-join-example"></a><span data-ttu-id="3044a-142">Vnitřní spojení pomocí Příklad seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="3044a-142">Inner join by using grouped join example</span></span>  
 <span data-ttu-id="3044a-143">Následující příklad ukazuje, jak implementovat vnitřní spojení pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="3044a-143">The following example shows you how to implement an inner join by using a group join.</span></span>  
  
 <span data-ttu-id="3044a-144">V `query1`, seznam `Person` objekty jsou připojené do skupiny do seznamu `Pet` na základě objektů `Person` odpovídající `Pet.Owner` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3044a-144">In `query1`, the list of `Person` objects is group-joined to the list of `Pet` objects based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="3044a-145">Skupiny připojení vytvoří kolekci zprostředkujících skupin, kde se skládá z každé skupiny `Person` objekt a pořadí odpovídajících `Pet` objekty.</span><span class="sxs-lookup"><span data-stu-id="3044a-145">The group join creates a collection of intermediate groups, where each group consists of a `Person` object and a sequence of matching `Pet` objects.</span></span>  
  
 <span data-ttu-id="3044a-146">Přidáním druhý `from` klauzule do dotazu, toto pořadí pořadí kombinaci (nebo průmětu) do jedné delší sekvence.</span><span class="sxs-lookup"><span data-stu-id="3044a-146">By adding a second `from` clause to the query, this sequence of sequences is combined (or flattened) into one longer sequence.</span></span> <span data-ttu-id="3044a-147">Typ elementů konečné pořadí je zadána `select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="3044a-147">The type of the elements of the final sequence is specified by the `select` clause.</span></span> <span data-ttu-id="3044a-148">V tomto příkladu, že typ je anonymní typ, který se skládá z `Person.FirstName` a `Pet.Name` vlastnosti pro každý odpovídající pár.</span><span class="sxs-lookup"><span data-stu-id="3044a-148">In this example, that type is an anonymous type that consists of the `Person.FirstName` and `Pet.Name` properties for each matching pair.</span></span>  
  
 <span data-ttu-id="3044a-149">Výsledek `query1` je ekvivalentní sadu výsledků dotazu, který by byl získán pomocí `join` klauzule bez `into` klauzule provést vnitřní spojení.</span><span class="sxs-lookup"><span data-stu-id="3044a-149">The result of `query1` is equivalent to the result set that would have been obtained by using the `join` clause without the `into` clause to perform an inner join.</span></span> <span data-ttu-id="3044a-150">`query2` Proměnná ukazuje tento ekvivalentní dotaz.</span><span class="sxs-lookup"><span data-stu-id="3044a-150">The `query2` variable demonstrates this equivalent query.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#4](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3044a-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="3044a-151">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="3044a-152">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="3044a-152">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="3044a-153">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="3044a-153">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="3044a-154">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="3044a-154">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
