---
title: Tuple – typy – reference jazyka C#
description: 'Další informace o řazených kolekcích členů jazyka C#: zjednodušené datové struktury, které lze použít k seskupení volně souvisejících datových prvků'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174987"
---
# <a name="tuple-types-c-reference"></a><span data-ttu-id="461f1-103">Tuple – typy (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="461f1-103">Tuple types (C# reference)</span></span>

<span data-ttu-id="461f1-104">K dispozici v C# 7,0 a novějších funkce *řazené kolekce členů* poskytuje stručnou syntaxi pro seskupení více datových elementů ve zjednodušené datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="461f1-104">Available in C# 7.0 and later, the *tuples* feature provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="461f1-105">Následující příklad ukazuje, jak lze deklarovat proměnnou řazené kolekce členů, inicializovat ji a přistupovat k jejím datovým členům:</span><span class="sxs-lookup"><span data-stu-id="461f1-105">The following example shows how you can declare a tuple variable, initialize it, and access its data members:</span></span>

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

<span data-ttu-id="461f1-106">Jak ukazuje předchozí příklad, pro definování typu řazené kolekce členů, zadáte typy všech datových členů a volitelně také [názvy polí](#tuple-field-names).</span><span class="sxs-lookup"><span data-stu-id="461f1-106">As the preceding example shows, to define a tuple type, you specify types of all its data members and, optionally, the [field names](#tuple-field-names).</span></span> <span data-ttu-id="461f1-107">Nemůžete definovat metody v typu řazené kolekce členů, ale můžete použít metody poskytované rozhraním .NET, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="461f1-107">You cannot define methods in a tuple type, but you can use the methods provided by .NET, as the following example shows:</span></span>

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

<span data-ttu-id="461f1-108">Počínaje jazykem C# 7,3 typy řazené kolekce členů podporují [operátory rovnosti](../operators/equality-operators.md) `==` a `!=` .</span><span class="sxs-lookup"><span data-stu-id="461f1-108">Beginning with C# 7.3, tuple types support [equality operators](../operators/equality-operators.md) `==` and `!=`.</span></span> <span data-ttu-id="461f1-109">Další informace najdete v oddílu [rovnosti řazené kolekce členů](#tuple-equality) .</span><span class="sxs-lookup"><span data-stu-id="461f1-109">For more information, see the [Tuple equality](#tuple-equality) section.</span></span>

<span data-ttu-id="461f1-110">Typy řazené kolekce členů jsou [typy hodnot](value-types.md); prvky řazené kolekce členů jsou veřejné pole.</span><span class="sxs-lookup"><span data-stu-id="461f1-110">Tuple types are [value types](value-types.md); tuple elements are public fields.</span></span> <span data-ttu-id="461f1-111">Který zpřístupňuje řazené kolekce členů *proměnlivých* hodnotových typů.</span><span class="sxs-lookup"><span data-stu-id="461f1-111">That makes tuples *mutable* value types.</span></span>

> [!NOTE]
> <span data-ttu-id="461f1-112">Funkce řazené kolekce členů vyžaduje <xref:System.ValueTuple?displayProperty=nameWithType> typ a související obecné typy (například <xref:System.ValueTuple%602?displayProperty=nameWithType> ), které jsou k dispozici v rozhraní .NET Core a .NET Framework 4,7 a novější.</span><span class="sxs-lookup"><span data-stu-id="461f1-112">The tuples feature requires the <xref:System.ValueTuple?displayProperty=nameWithType> type and related generic types (for example, <xref:System.ValueTuple%602?displayProperty=nameWithType>), which are available in .NET Core and .NET Framework 4.7 and later.</span></span> <span data-ttu-id="461f1-113">Chcete-li použít řazené kolekce členů v projektu, který se zaměřuje na .NET Framework 4.6.2 nebo dříve, přidejte [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) do projektu balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="461f1-113">To use tuples in a project that targets .NET Framework 4.6.2 or earlier, add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) to the project.</span></span>

<span data-ttu-id="461f1-114">Můžete definovat řazené kolekce členů s libovolným velkým počtem prvků:</span><span class="sxs-lookup"><span data-stu-id="461f1-114">You can define tuples with an arbitrary large number of elements:</span></span>

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a><span data-ttu-id="461f1-115">Použití případů řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="461f1-115">Use cases of tuples</span></span>

<span data-ttu-id="461f1-116">Jedním z nejběžnějších případů použití řazených kolekcí členů je jako návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="461f1-116">One of the most common use cases of tuples is as a method return type.</span></span> <span data-ttu-id="461f1-117">To znamená, že namísto definování [ `out` parametrů metody](../keywords/out-parameter-modifier.md)lze seskupit metodu do návratového typu řazené kolekce členů, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="461f1-117">That is, instead of defining [`out` method parameters](../keywords/out-parameter-modifier.md), you can group method results in a tuple return type, as the following example shows:</span></span>

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

<span data-ttu-id="461f1-118">Jak ukazuje předchozí příklad, můžete pracovat s vrácenou instancí řazené kolekce členů přímo nebo ji [dekonstruovat](#tuple-assignment-and-deconstruction) v samostatných proměnných.</span><span class="sxs-lookup"><span data-stu-id="461f1-118">As the preceding example shows, you can work with the returned tuple instance directly or [deconstruct](#tuple-assignment-and-deconstruction) it in separate variables.</span></span>

<span data-ttu-id="461f1-119">Namísto [anonymních typů](../../programming-guide/classes-and-structs/anonymous-types.md)lze také použít typy řazené kolekce členů; například v dotazech LINQ.</span><span class="sxs-lookup"><span data-stu-id="461f1-119">You can also use tuple types instead of [anonymous types](../../programming-guide/classes-and-structs/anonymous-types.md); for example, in LINQ queries.</span></span> <span data-ttu-id="461f1-120">Další informace najdete v tématu [Volba mezi anonymními a řazenými kolekcemi členů](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span><span class="sxs-lookup"><span data-stu-id="461f1-120">For more information, see [Choosing between anonymous and tuple types](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span></span>

<span data-ttu-id="461f1-121">Obvykle používáte řazené kolekce členů k seskupení volně souvisejících datových prvků.</span><span class="sxs-lookup"><span data-stu-id="461f1-121">Typically, you use tuples to group loosely related data elements.</span></span> <span data-ttu-id="461f1-122">To je obvykle užitečné v rámci privátních a interních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="461f1-122">That is usually useful within private and internal utility methods.</span></span> <span data-ttu-id="461f1-123">V případě veřejného rozhraní API zvažte definování [třídy](../keywords/class.md) nebo typu [struktury](struct.md) .</span><span class="sxs-lookup"><span data-stu-id="461f1-123">In the case of public API, consider defining a [class](../keywords/class.md) or a [structure](struct.md) type.</span></span>

## <a name="tuple-field-names"></a><span data-ttu-id="461f1-124">Názvy polí řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="461f1-124">Tuple field names</span></span>

<span data-ttu-id="461f1-125">Můžete explicitně zadat názvy polí řazené kolekce členů buď v inicializačním výrazu řazené kolekce členů, nebo v definici typu řazené kolekce členů, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="461f1-125">You can explicitly specify the names of tuple fields either in a tuple initialization expression or in the definition of a tuple type, as the following example shows:</span></span>

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

<span data-ttu-id="461f1-126">Počínaje jazykem C# 7,1, pokud nezadáte název pole, může být odvozen z názvu odpovídající proměnné v inicializačním výrazu řazené kolekce členů, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="461f1-126">Beginning with C# 7.1, if you don't specify a field name, it may be inferred from the name of the corresponding variable in a tuple initialization expression, as the following example shows:</span></span>

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

<span data-ttu-id="461f1-127">Označuje se jako Inicializátory řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="461f1-127">That's known as tuple projection initializers.</span></span> <span data-ttu-id="461f1-128">Název proměnné není v následujících případech promítnut do pole řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="461f1-128">The name of a variable isn't projected onto a tuple field name in the following cases:</span></span>

- <span data-ttu-id="461f1-129">Kandidátský název je název členu typu řazené kolekce členů, například, `Item3` , `ToString` nebo `Rest` .</span><span class="sxs-lookup"><span data-stu-id="461f1-129">The candidate name is a member name of a tuple type, for example, `Item3`, `ToString`, or `Rest`.</span></span>
- <span data-ttu-id="461f1-130">Název kandidáta je duplikátem jiného názvu pole řazené kolekce členů, ať už explicitního, nebo implicitního.</span><span class="sxs-lookup"><span data-stu-id="461f1-130">The candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="461f1-131">V těchto případech buď explicitně zadáte název pole, nebo přístup k poli s jeho výchozím názvem.</span><span class="sxs-lookup"><span data-stu-id="461f1-131">In those cases you either explicitly specify the name of a field or access a field by its default name.</span></span>

<span data-ttu-id="461f1-132">Výchozí názvy polí řazené kolekce členů `Item1` jsou `Item2` , `Item3` a tak dále.</span><span class="sxs-lookup"><span data-stu-id="461f1-132">The default names of tuple fields are `Item1`, `Item2`, `Item3` and so on.</span></span> <span data-ttu-id="461f1-133">Můžete vždy použít výchozí název pole, a to i v případě, že je název pole zadán explicitně nebo odvozený, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="461f1-133">You can always use the default name of a field, even when a field name is specified explicitly or inferred, as the following example shows:</span></span>

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

<span data-ttu-id="461f1-134">[Přiřazení řazené kolekce členů](#tuple-assignment-and-deconstruction) a [porovnání rovnosti řazené kolekce členů](#tuple-equality) nevezmou názvy polí v účtu.</span><span class="sxs-lookup"><span data-stu-id="461f1-134">[Tuple assignment](#tuple-assignment-and-deconstruction) and [tuple equality comparisons](#tuple-equality) don't take field names into account.</span></span>

<span data-ttu-id="461f1-135">V době kompilace kompilátor nahrazuje názvy polí, které nejsou výchozí, odpovídajícími výchozími názvy.</span><span class="sxs-lookup"><span data-stu-id="461f1-135">At compile time, the compiler replaces non-default field names with the corresponding default names.</span></span> <span data-ttu-id="461f1-136">V důsledku toho nejsou explicitně zadané nebo odvozené názvy polí k dispozici v době běhu.</span><span class="sxs-lookup"><span data-stu-id="461f1-136">As a result, explicitly specified or inferred field names aren't available at run time.</span></span>

## <a name="tuple-assignment-and-deconstruction"></a><span data-ttu-id="461f1-137">Přiřazení a dekonstrukce řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="461f1-137">Tuple assignment and deconstruction</span></span>

<span data-ttu-id="461f1-138">Jazyk C# podporuje přiřazení mezi typy řazené kolekce členů, které splní obě následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="461f1-138">C# supports assignment between tuple types that satisfy both of the following conditions:</span></span>

- <span data-ttu-id="461f1-139">Oba typy řazené kolekce členů mají stejný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="461f1-139">both tuple types have the same number of elements</span></span>
- <span data-ttu-id="461f1-140">u každé pozice řazené kolekce členů je typ prvku řazené kolekce členů stejný jako nebo implicitně převoditelné na typ odpovídajícího elementu řazené kolekce členů na levé straně.</span><span class="sxs-lookup"><span data-stu-id="461f1-140">for each tuple position, the type of the right-hand tuple element is the same as or implicitly convertible to the type of the corresponding left-hand tuple element</span></span>

<span data-ttu-id="461f1-141">Hodnoty prvků řazené kolekce členů jsou přiřazeny za pořadí prvků řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="461f1-141">Tuple element values are assigned following the order of tuple elements.</span></span> <span data-ttu-id="461f1-142">Názvy polí řazené kolekce členů jsou ignorovány a nejsou přiřazeny, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="461f1-142">The names of tuple fields are ignored and not assigned, as the following example shows:</span></span>

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

<span data-ttu-id="461f1-143">Můžete také použít operátor přiřazení `=` k *dekonstrukci* instance řazené kolekce členů v samostatných proměnných.</span><span class="sxs-lookup"><span data-stu-id="461f1-143">You can also use the assignment operator `=` to *deconstruct* a tuple instance in separate variables.</span></span> <span data-ttu-id="461f1-144">Můžete to udělat jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="461f1-144">You can do that in one of the following ways:</span></span>

- <span data-ttu-id="461f1-145">Explicitně deklarovat typ každé proměnné uvnitř závorek:</span><span class="sxs-lookup"><span data-stu-id="461f1-145">Explicitly declare the type of each variable inside parentheses:</span></span>

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- <span data-ttu-id="461f1-146">Použijte `var` klíčové slovo mimo závorky k deklaraci implicitně typových proměnných a nechejte kompilátor odvodit své typy:</span><span class="sxs-lookup"><span data-stu-id="461f1-146">Use the `var` keyword outside the parentheses to declare implicitly typed variables and let the compiler infer their types:</span></span>

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- <span data-ttu-id="461f1-147">Použít existující proměnné:</span><span class="sxs-lookup"><span data-stu-id="461f1-147">Use existing variables:</span></span>

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

<span data-ttu-id="461f1-148">Další informace o dekonstrukci řazených kolekcí členů a dalších typů naleznete v tématu [dekonstrukce řazených kolekcí členů a dalších typů](../../deconstruct.md).</span><span class="sxs-lookup"><span data-stu-id="461f1-148">For more information about deconstruction of tuples and other types, see [Deconstructing tuples and other types](../../deconstruct.md).</span></span>

## <a name="tuple-equality"></a><span data-ttu-id="461f1-149">Rovnost řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="461f1-149">Tuple equality</span></span>

<span data-ttu-id="461f1-150">Počínaje jazykem C# 7,3 typy řazené kolekce členů `==` podporují `!=` operátory a.</span><span class="sxs-lookup"><span data-stu-id="461f1-150">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="461f1-151">Tyto operátory porovnávají členy operandu na levé straně s odpovídajícími členy pravého operandu po pořadí prvků řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="461f1-151">These operators compare members of the left-hand operand with the corresponding members of the right-hand operand following the order of tuple elements.</span></span>

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

<span data-ttu-id="461f1-152">Jak ukazuje předchozí příklad, `==` `!=` operace a neberou v úvahu názvy polí řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="461f1-152">As the preceding example shows, the `==` and `!=` operations don't take into account tuple field names.</span></span>

<span data-ttu-id="461f1-153">Dvě řazené kolekce členů jsou srovnatelné, pokud jsou splněny obě následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="461f1-153">Two tuples are comparable when both of the following conditions are satisfied:</span></span>

- <span data-ttu-id="461f1-154">Obě řazené kolekce členů mají stejný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="461f1-154">Both tuples have the same number of elements.</span></span> <span data-ttu-id="461f1-155">Například `t1 != t2` není zkompilován, pokud `t1` a `t2` má různý počet prvků.</span><span class="sxs-lookup"><span data-stu-id="461f1-155">For example, `t1 != t2` doesn't compile if `t1` and `t2` have different numbers of elements.</span></span>
- <span data-ttu-id="461f1-156">Pro každou pozici řazené kolekce členů jsou odpovídající prvky z operandů řazené kolekce na levé straně a na pravé straně porovnatelné s `==` `!=` operátory a.</span><span class="sxs-lookup"><span data-stu-id="461f1-156">For each tuple position, the corresponding elements from the left-hand and right-hand tuple operands are comparable with the `==` and `!=` operators.</span></span> <span data-ttu-id="461f1-157">Například není `(1, (2, 3)) == ((1, 2), 3)` zkompilován, protože není `1` porovnatelný s `(1, 2)` .</span><span class="sxs-lookup"><span data-stu-id="461f1-157">For example, `(1, (2, 3)) == ((1, 2), 3)` doesn't compile because `1` is not comparable with `(1, 2)`.</span></span>

<span data-ttu-id="461f1-158">`==`Operátory a `!=` porovnávají řazené kolekce členů v podobě krátkodobého okruhu.</span><span class="sxs-lookup"><span data-stu-id="461f1-158">The `==` and `!=` operators compare tuples in short-circuiting way.</span></span> <span data-ttu-id="461f1-159">To znamená, že operace se zastaví, jakmile splní pár nerovných prvků nebo dosáhne konců řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="461f1-159">That is, an operation stops as soon as it meets a pair of non equal elements or reaches the ends of tuples.</span></span> <span data-ttu-id="461f1-160">Před jakýmkoli porovnáním však jsou vyhodnocovány *všechny* prvky řazené kolekce členů, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="461f1-160">However, before any comparison, *all* tuple elements are evaluated, as the following example shows:</span></span>

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="461f1-161">Řazené kolekce členů jako výstupní parametry</span><span class="sxs-lookup"><span data-stu-id="461f1-161">Tuples as out parameters</span></span>

<span data-ttu-id="461f1-162">Obvykle refaktorujte metodu, která má [ `out` parametry](../keywords/out-parameter-modifier.md) do metody, která vrací řazenou kolekci členů.</span><span class="sxs-lookup"><span data-stu-id="461f1-162">Typically, you refactor a method that has [`out` parameters](../keywords/out-parameter-modifier.md) into a method that returns a tuple.</span></span> <span data-ttu-id="461f1-163">Existují však případy, ve kterých `out` parametr může být typu řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="461f1-163">However, there are cases in which an `out` parameter can be of a tuple type.</span></span> <span data-ttu-id="461f1-164">Následující příklad ukazuje, jak pracovat s řazenými kolekcemi členů jako `out` parametry:</span><span class="sxs-lookup"><span data-stu-id="461f1-164">The following example shows how to work with tuples as `out` parameters:</span></span>

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a><span data-ttu-id="461f1-165">Řazené kolekce členů vs`System.Tuple`</span><span class="sxs-lookup"><span data-stu-id="461f1-165">Tuples vs `System.Tuple`</span></span>

<span data-ttu-id="461f1-166">Řazené kolekce členů jazyka C#, které jsou zálohovány <xref:System.ValueTuple?displayProperty=nameWithType> typy, se liší od řazených kolekcí členů, které jsou zastoupeny <xref:System.Tuple?displayProperty=nameWithType> typy.</span><span class="sxs-lookup"><span data-stu-id="461f1-166">C# tuples, which are backed by <xref:System.ValueTuple?displayProperty=nameWithType> types, are different from tuples that are represented by <xref:System.Tuple?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="461f1-167">Hlavní rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="461f1-167">The main differences are as follows:</span></span>

- <span data-ttu-id="461f1-168">`ValueTuple`typy jsou [typy hodnot](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="461f1-168">`ValueTuple` types are [value types](value-types.md).</span></span> <span data-ttu-id="461f1-169">`Tuple`typy jsou [odkazové typy](../keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="461f1-169">`Tuple` types are [reference types](../keywords/reference-types.md).</span></span>
- <span data-ttu-id="461f1-170">`ValueTuple`typy jsou proměnlivé.</span><span class="sxs-lookup"><span data-stu-id="461f1-170">`ValueTuple` types are mutable.</span></span> <span data-ttu-id="461f1-171">`Tuple`typy jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="461f1-171">`Tuple` types are immutable.</span></span>
- <span data-ttu-id="461f1-172">Datové členy `ValueTuple` typů jsou pole.</span><span class="sxs-lookup"><span data-stu-id="461f1-172">Data members of `ValueTuple` types are fields.</span></span> <span data-ttu-id="461f1-173">Datové členy `Tuple` typů jsou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="461f1-173">Data members of `Tuple` types are properties.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="461f1-174">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="461f1-174">C# language specification</span></span>

<span data-ttu-id="461f1-175">Další informace najdete v těchto poznámkách k návrhu funkcí:</span><span class="sxs-lookup"><span data-stu-id="461f1-175">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="461f1-176">Odvodit názvy řazených kolekcí členů (neboli inicializátorů řazené kolekce členů)</span><span class="sxs-lookup"><span data-stu-id="461f1-176">Infer tuple names (aka. tuple projection initializers)</span></span>](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [<span data-ttu-id="461f1-177">Podpora pro `==` `!=` typy řazené kolekce členů a</span><span class="sxs-lookup"><span data-stu-id="461f1-177">Support for `==` and `!=` on tuple types</span></span>](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a><span data-ttu-id="461f1-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="461f1-178">See also</span></span>

- [<span data-ttu-id="461f1-179">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="461f1-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="461f1-180">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="461f1-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="461f1-181">Volba mezi anonymními a řazenými typy řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="461f1-181">Choosing between anonymous and tuple types</span></span>](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
