---
title: 'Postupy: Přidání vlastních metod pro dotazy LINQ'
ms.date: 08/28/2020
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 7d38a45263135fa10dc53dc0d09b8129838e78e6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117776"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="fa6e8-102">Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa6e8-102">How to: Add custom methods for LINQ queries (Visual Basic)</span></span>

<span data-ttu-id="fa6e8-103">Můžete rozšířit sadu metod, které používáte pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-103">You extend the set of methods that you use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="fa6e8-104">Například kromě standardních průměrných nebo maximálních operací můžete vytvořit vlastní agregační metodu pro výpočet jedné hodnoty z sekvence hodnot.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-104">For example, in addition to the standard average or maximum operations, you create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="fa6e8-105">Také vytvoříte metodu, která funguje jako vlastní filtr nebo konkrétní transformace dat pro posloupnost hodnot a vrátí novou sekvenci.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-105">You also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="fa6e8-106">Příklady takových metod jsou <xref:System.Linq.Enumerable.Distinct%2A> , <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="fa6e8-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="fa6e8-107">Když rozšíříte <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete použít vlastní metody na jakoukoli vyčíslitelné kolekci.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="fa6e8-108">Další informace naleznete v tématu [metody rozšíření](../../language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="fa6e8-108">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="fa6e8-109">Přidání agregační metody</span><span class="sxs-lookup"><span data-stu-id="fa6e8-109">Adding an aggregate method</span></span>

<span data-ttu-id="fa6e8-110">Agregační metoda vypočítá jednu hodnotu ze sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="fa6e8-111">LINQ poskytuje několik agregačních metod, včetně <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Min%2A> a <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="fa6e8-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="fa6e8-112">Můžete vytvořit vlastní agregační metodu přidáním metody rozšíření do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="fa6e8-113">Následující příklad kódu ukazuje, jak vytvořit rozšiřující metodu volanou pro `Median` Výpočet mediánu pro sekvenci čísel typu `double` .</span><span class="sxs-lookup"><span data-stu-id="fa6e8-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

:::code language="vb" source="./snippets/LinqExtension.vb" :::

<span data-ttu-id="fa6e8-114">Tuto metodu rozšíření pro každou vyčíslitelné kolekci můžete zavolat stejným způsobem jako jiné agregační metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="fa6e8-115">V Visual Basic můžete buď použít volání metody, nebo standardní syntaxi dotazu pro `Aggregate` `Group By` klauzuli OR.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="fa6e8-116">Další informace naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md) a [klauzule GROUP by](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fa6e8-116">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="fa6e8-117">Následující příklad kódu ukazuje, jak použít `Median` metodu pro pole typu `double` .</span><span class="sxs-lookup"><span data-stu-id="fa6e8-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="fa6e8-118">Přetížení agregované metody pro příjem různých typů</span><span class="sxs-lookup"><span data-stu-id="fa6e8-118">Overloading an aggregate method to accept various types</span></span>

<span data-ttu-id="fa6e8-119">Můžete přetížit agregační metodu tak, aby mohla přijímat sekvence různých typů.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="fa6e8-120">Standardní přístup je vytvořit přetížení pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="fa6e8-121">Další možností je vytvořit přetížení, které bude přebírat obecný typ a převést jej na konkrétní typ pomocí delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="fa6e8-122">Oba přístupy můžete také kombinovat.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="fa6e8-123">Pro vytvoření přetížení pro každý typ</span><span class="sxs-lookup"><span data-stu-id="fa6e8-123">To create an overload for each type</span></span>

<span data-ttu-id="fa6e8-124">Můžete vytvořit konkrétní přetížení pro každý typ, který chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="fa6e8-125">Následující příklad kódu ukazuje přetížení `Median` metody pro daný `integer` typ.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="IntOverload":::

<span data-ttu-id="fa6e8-126">Nyní můžete volat `Median` přetížení pro oba `integer` `double` typy a, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="fa6e8-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="fa6e8-127">Vytvoření obecného přetížení</span><span class="sxs-lookup"><span data-stu-id="fa6e8-127">To create a generic overload</span></span>

<span data-ttu-id="fa6e8-128">Můžete také vytvořit přetížení, které přijímá sekvenci generických objektů.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="fa6e8-129">Toto přetížení přebírá jako parametr delegáta a používá ho k převodu sekvence objektů obecného typu na konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="fa6e8-130">Následující kód ukazuje přetížení `Median` metody, která přebírá <xref:System.Func%602> delegáta jako parametr.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="fa6e8-131">Tento delegát přebírá objekt obecného typu `T` a vrací objekt typu `double` .</span><span class="sxs-lookup"><span data-stu-id="fa6e8-131">This delegate takes an object of generic type `T` and returns an object of type `double`.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="GenericOverload":::

<span data-ttu-id="fa6e8-132">Nyní můžete zavolat `Median` metodu pro sekvenci objektů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="fa6e8-133">Pokud typ nemá vlastní metodu přetížení, je nutné předat parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="fa6e8-134">V Visual Basic můžete pro tento účel použít výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="fa6e8-135">Také Pokud použijete `Aggregate` `Group By` klauzuli OR namísto volání metody, můžete předat libovolnou hodnotu nebo výraz, který je v rámci této klauzule Scope.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="fa6e8-136">Následující příklad kódu ukazuje, jak zavolat `Median` metodu pro pole celých čísel a pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="fa6e8-137">Pro řetězce se počítá medián pro délky řetězců v poli.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="fa6e8-138">Příklad ukazuje, jak předat <xref:System.Func%602> parametr delegáta `Median` metodě pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="fa6e8-139">Přidání metody, která vrátí kolekci</span><span class="sxs-lookup"><span data-stu-id="fa6e8-139">Adding a method that returns a collection</span></span>

<span data-ttu-id="fa6e8-140">Rozhraní můžete roztáhnout <xref:System.Collections.Generic.IEnumerable%601> vlastní metodou dotazu, která vrací sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="fa6e8-141">V tomto případě musí metoda vracet kolekci typu <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="fa6e8-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="fa6e8-142">Tyto metody lze použít k aplikování filtrů nebo transformací dat na sekvenci hodnot.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="fa6e8-143">Následující příklad ukazuje, jak vytvořit rozšiřující metodu s názvem `AlternateElements` , která vrátí všechny ostatní prvky v kolekci počínaje prvním prvkem.</span><span class="sxs-lookup"><span data-stu-id="fa6e8-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="SequenceElement":::

<span data-ttu-id="fa6e8-144">Tuto metodu rozšíření můžete zavolat pro všechny vyčíslitelné kolekce stejně, jako byste volali jiné metody z <xref:System.Collections.Generic.IEnumerable%601> rozhraní, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="fa6e8-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="SequenceUsage":::

## <a name="see-also"></a><span data-ttu-id="fa6e8-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa6e8-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="fa6e8-146">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="fa6e8-146">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
