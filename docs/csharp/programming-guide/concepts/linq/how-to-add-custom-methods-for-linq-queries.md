---
title: Postup přidání vlastních metod pro dotazy LINQ (C#)
description: Naučte se rozšířit syntaxi dotazů LINQ přidáním rozšiřujících metod do <T> rozhraní IEnumerable v jazyce C#.
ms.date: 08/26/2020
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 768882fce40a2fc6e018f24c8928341e7c65bc4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122422"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="63a4d-103">Postup přidání vlastních metod pro dotazy LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="63a4d-103">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="63a4d-104">Můžete rozšířit sadu metod, které používáte pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63a4d-104">You extend the set of methods that you use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="63a4d-105">Například kromě standardních průměrných nebo maximálních operací můžete vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="63a4d-105">For example, in addition to the standard average or maximum operations, you create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="63a4d-106">Také vytvoříte metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro posloupnost hodnot a vrátí novou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="63a4d-106">You also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="63a4d-107">Příklady takových metod jsou <xref:System.Linq.Enumerable.Distinct%2A> , <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="63a4d-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="63a4d-108">Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít vlastní metody na jakoukoli vyčíslitelné kolekci.</span><span class="sxs-lookup"><span data-stu-id="63a4d-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="63a4d-109">Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="63a4d-109">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="63a4d-110">Přidání agregační metody</span><span class="sxs-lookup"><span data-stu-id="63a4d-110">Adding an aggregate method</span></span>

<span data-ttu-id="63a4d-111">Agregační metoda vypočítá jednu hodnotu ze sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="63a4d-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="63a4d-112">LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Min%2A> a <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="63a4d-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="63a4d-113">Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63a4d-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="63a4d-114">Následující příklad kódu ukazuje, jak vytvořit rozšiřující metodu volanou pro `Median` Výpočet mediánu pro sekvenci čísel typu `double` .</span><span class="sxs-lookup"><span data-stu-id="63a4d-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="LinqExtensionClass":::

<span data-ttu-id="63a4d-115">Tuto metodu rozšíření pro každou vyčíslitelné kolekci můžete zavolat stejným způsobem jako jiné agregační metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63a4d-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="63a4d-116">Následující příklad kódu ukazuje, jak použít `Median` metodu pro pole typu `double` .</span><span class="sxs-lookup"><span data-stu-id="63a4d-116">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="63a4d-117">Přetížení agregované metody pro příjem různých typů</span><span class="sxs-lookup"><span data-stu-id="63a4d-117">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="63a4d-118">Můžete přetížit agregační metodu tak, aby mohla přijímat sekvence různých typů.</span><span class="sxs-lookup"><span data-stu-id="63a4d-118">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="63a4d-119">Standardní přístup je vytvořit přetížení pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="63a4d-119">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="63a4d-120">Další možností je vytvořit přetížení, které bude přebírat obecný typ a převést jej na konkrétní typ pomocí delegáta.</span><span class="sxs-lookup"><span data-stu-id="63a4d-120">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="63a4d-121">Oba přístupy můžete také kombinovat.</span><span class="sxs-lookup"><span data-stu-id="63a4d-121">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="63a4d-122">Pro vytvoření přetížení pro každý typ</span><span class="sxs-lookup"><span data-stu-id="63a4d-122">To create an overload for each type</span></span>

<span data-ttu-id="63a4d-123">Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="63a4d-123">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="63a4d-124">Následující příklad kódu ukazuje přetížení `Median` metody pro daný `int` typ.</span><span class="sxs-lookup"><span data-stu-id="63a4d-124">The following code example shows an overload of the `Median` method for the `int` type.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="IntOverload":::

<span data-ttu-id="63a4d-125">Nyní můžete volat `Median` přetížení pro oba `integer` `double` typy a, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="63a4d-125">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="63a4d-126">Vytvoření obecného přetížení</span><span class="sxs-lookup"><span data-stu-id="63a4d-126">To create a generic overload</span></span>

<span data-ttu-id="63a4d-127">Můžete také vytvořit přetížení, které přijímá sekvenci generických objektů.</span><span class="sxs-lookup"><span data-stu-id="63a4d-127">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="63a4d-128">Toto přetížení přebírá jako parametr delegáta a používá ho k převodu sekvence objektů obecného typu na konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="63a4d-128">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="63a4d-129">Následující kód ukazuje přetížení `Median` metody, která přebírá <xref:System.Func%602> delegáta jako parametr.</span><span class="sxs-lookup"><span data-stu-id="63a4d-129">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="63a4d-130">Tento delegát přebírá objekt typu Generic Type T a vrátí objekt typu `double` .</span><span class="sxs-lookup"><span data-stu-id="63a4d-130">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="GenericOverload":::

<span data-ttu-id="63a4d-131">Nyní můžete zavolat `Median` metodu pro sekvenci objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="63a4d-131">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="63a4d-132">Pokud typ nemá vlastní metodu přetížení, je nutné předat parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="63a4d-132">If the type doesn't have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="63a4d-133">V jazyce C# můžete pro tento účel použít výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="63a4d-133">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="63a4d-134">Také v Visual Basic pouze v případě, že použijete `Aggregate` `Group By` klauzuli OR namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v rozsahu této klauzule.</span><span class="sxs-lookup"><span data-stu-id="63a4d-134">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="63a4d-135">Následující příklad kódu ukazuje, jak zavolat `Median` metodu pro pole celých čísel a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="63a4d-135">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="63a4d-136">Pro řetězce se počítá medián pro délky řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="63a4d-136">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="63a4d-137">Příklad ukazuje, jak předat <xref:System.Func%602> parametr delegáta `Median` metodě pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="63a4d-137">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-sequence"></a><span data-ttu-id="63a4d-138">Přidání metody, která vrací sekvenci</span><span class="sxs-lookup"><span data-stu-id="63a4d-138">Adding a method that returns a sequence</span></span>

<span data-ttu-id="63a4d-139">Rozhraní můžete roztáhnout <xref:System.Collections.Generic.IEnumerable%601> vlastní metodou dotazu, která vrací sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="63a4d-139">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="63a4d-140">V tomto případě musí metoda vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="63a4d-140">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="63a4d-141">Tyto metody lze použít k aplikování filtrů nebo transformací dat na sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="63a4d-141">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="63a4d-142">Následující příklad ukazuje, jak vytvořit rozšiřující metodu s názvem `AlternateElements` , která vrátí všechny ostatní prvky v kolekci počínaje prvním prvkem.</span><span class="sxs-lookup"><span data-stu-id="63a4d-142">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="SequenceElement":::

<span data-ttu-id="63a4d-143">Tuto metodu rozšíření můžete zavolat pro všechny vyčíslitelné kolekce stejně, jako byste volali jiné metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="63a4d-143">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="SequenceUsage":::

## <a name="see-also"></a><span data-ttu-id="63a4d-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="63a4d-144">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="63a4d-145">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="63a4d-145">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
