---
title: Typové zkoušky a převod operators – C# odkaz
description: Další informace o C# operátory, které můžete použít ke kontrole typu výsledek výrazu a v případě potřeby ji převést na jiného typu.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: a9e5139e6d650aa6935bff934ca25502fdc14775
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744070"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a><span data-ttu-id="78f8e-103">Typové zkoušky a převod operátorů (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="78f8e-103">Type-testing and conversion operators (C# reference)</span></span>

<span data-ttu-id="78f8e-104">K provedení kontroly typu nebo konverze typu můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="78f8e-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="78f8e-105">[je operátor](#is-operator): Chcete-li zkontrolovat, jestli je kompatibilní s daným typem modulu runtime typu výrazu</span><span class="sxs-lookup"><span data-stu-id="78f8e-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="78f8e-106">[jako operátor](#as-operator): k explicitnímu převodu výrazu na daný typ, pokud je jeho typ runtime kompatibilní s tímto typem</span><span class="sxs-lookup"><span data-stu-id="78f8e-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="78f8e-107">[přetypování () operátor](#cast-operator-): k provedení explicitního převodu</span><span class="sxs-lookup"><span data-stu-id="78f8e-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="78f8e-108">[operátor typeof](#typeof-operator): získání <xref:System.Type?displayProperty=nameWithType> instance typu</span><span class="sxs-lookup"><span data-stu-id="78f8e-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="78f8e-109">is – operátor</span><span class="sxs-lookup"><span data-stu-id="78f8e-109">is operator</span></span>

<span data-ttu-id="78f8e-110">`is` Operátor ověří, zda modul runtime typu výsledek výrazu kompatibilní s daným typem.</span><span class="sxs-lookup"><span data-stu-id="78f8e-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="78f8e-111">Počínaje C# 7.0, `is` operátor také testy výsledek výrazu se vzorem.</span><span class="sxs-lookup"><span data-stu-id="78f8e-111">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="78f8e-112">Výraz s typové zkoušky `is` operátor má následující podobu.</span><span class="sxs-lookup"><span data-stu-id="78f8e-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="78f8e-113">kde `E` je výraz, který vrací hodnotu a `T` je název typu nebo parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="78f8e-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="78f8e-114">`E` nemůže být anonymní metody nebo výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="78f8e-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="78f8e-115">`E is T` Výraz vrátí `true` Pokud výsledek `E` je jiná než null a je možné převést na typ `T` převod odkazu, převodu zabalení nebo unboxingového převodu; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="78f8e-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="78f8e-116">`is` Operátor nebere v úvahu uživatelem definovaných převodů.</span><span class="sxs-lookup"><span data-stu-id="78f8e-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="78f8e-117">Následující příklad ukazuje, že `is` operátor vrátí `true` Pokud běhového typu výsledek výrazu je odvozena z daného typu, to znamená, že existuje odkaz na převod mezi typy:</span><span class="sxs-lookup"><span data-stu-id="78f8e-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="78f8e-118">Následující příklad ukazuje, že `is` operátor bere v úvahu zabalení a rozbalení převody, ale nezahrne číselných převodů:</span><span class="sxs-lookup"><span data-stu-id="78f8e-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider numeric conversions:</span></span>

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="78f8e-119">Informace o C# převody, naleznete v tématu [převody](~/_csharplang/spec/conversions.md) kapitoly [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="78f8e-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="78f8e-120">Typ testování pomocí porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="78f8e-120">Type testing with pattern matching</span></span>

<span data-ttu-id="78f8e-121">Počínaje C# 7.0, `is` operátor také testy výsledek výrazu se vzorem.</span><span class="sxs-lookup"><span data-stu-id="78f8e-121">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="78f8e-122">Konkrétně se podporuje vzor typu v následujícím tvaru:</span><span class="sxs-lookup"><span data-stu-id="78f8e-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="78f8e-123">kde `E` je výraz, který vrátí hodnotu, která `T` je název typu nebo parametr typu a `v` je nová místní proměnná typu `T`.</span><span class="sxs-lookup"><span data-stu-id="78f8e-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="78f8e-124">Pokud výsledek `E` je jiná než null a je možné převést na `T` odkazem, zabalení a rozbalení převodu `E is T v` výraz vrátí `true` a převedená hodnota výsledku `E` přiřazen Proměnná `v`.</span><span class="sxs-lookup"><span data-stu-id="78f8e-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="78f8e-125">Následující příklad ukazuje použití `is` operátor se vzorem typu:</span><span class="sxs-lookup"><span data-stu-id="78f8e-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="78f8e-126">Další informace o typu model a jiné podporované vzory najdete v tématu [porovnávání vzorů s je](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="78f8e-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="78f8e-127">jako operátor</span><span class="sxs-lookup"><span data-stu-id="78f8e-127">as operator</span></span>

<span data-ttu-id="78f8e-128">`as` Operátor explicitně převádí výsledek výrazu na daný odkaz nebo typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="78f8e-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="78f8e-129">Pokud převod není možné, `as` operátor vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="78f8e-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="78f8e-130">Na rozdíl od [přetypování () operátor](#cast-operator-), `as` operátor nikdy nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="78f8e-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="78f8e-131">Výraz tvaru</span><span class="sxs-lookup"><span data-stu-id="78f8e-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="78f8e-132">kde `E` je výraz, který vrací hodnotu a `T` je název typu nebo parametr typu, vytvoří stejný výsledek jako</span><span class="sxs-lookup"><span data-stu-id="78f8e-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="78f8e-133">s tím rozdílem, že `E` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="78f8e-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="78f8e-134">`as` Operátor bere v úvahu jenom převody odkazů, s možnou hodnotou Null, zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="78f8e-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="78f8e-135">Nelze použít `as` operátor uživatelsky definovaný převod.</span><span class="sxs-lookup"><span data-stu-id="78f8e-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="78f8e-136">Chcete-li to mohli udělat, použijte [přetypování () operátor](#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="78f8e-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="78f8e-137">Následující příklad ukazuje použití `as` operátor:</span><span class="sxs-lookup"><span data-stu-id="78f8e-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="78f8e-138">Jak ukazuje předchozí příklad, potřebujete porovnat výsledek `as` výraz s `null` ke kontrole, pokud převod není úspěšná.</span><span class="sxs-lookup"><span data-stu-id="78f8e-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="78f8e-139">Počínaje C# 7.0, můžete použít [je operátor](#type-testing-with-pattern-matching) i k testování v případě, že převod je úspěšný, a pokud se aktivace podaří, přiřadit výsledek do nové proměnné.</span><span class="sxs-lookup"><span data-stu-id="78f8e-139">Starting with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="78f8e-140">Operátor přetypování)</span><span class="sxs-lookup"><span data-stu-id="78f8e-140">Cast operator ()</span></span>

<span data-ttu-id="78f8e-141">Přetypování výrazu v podobě `(T)E` provádí explicitní převod výsledku výrazu `E` na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="78f8e-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="78f8e-142">Pokud neexistuje žádný explicitní převod z typu `E` na typ `T`, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="78f8e-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="78f8e-143">V době běhu by se nemusela podařit explicitní převod a výraz přetypování může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="78f8e-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="78f8e-144">Následující příklad ukazuje explicitní převody číselné a odkaz:</span><span class="sxs-lookup"><span data-stu-id="78f8e-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="78f8e-145">Informace o podporovaných explicitní převody, naleznete v tématu [explicitních převodů](~/_csharplang/spec/conversions.md#explicit-conversions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="78f8e-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="78f8e-146">Informace o tom, jak definovat vlastní typ explicitní nebo implicitní převod, naleznete v tématu [uživatelsky definovaný převod operátorů](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="78f8e-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="78f8e-147">Další využití)</span><span class="sxs-lookup"><span data-stu-id="78f8e-147">Other usages of ()</span></span>

<span data-ttu-id="78f8e-148">Také při použití závorek k [volání metody nebo vyvolat delegáta](member-access-operators.md#invocation-operator-).</span><span class="sxs-lookup"><span data-stu-id="78f8e-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="78f8e-149">Další závorky slouží k určení pořadí, ve kterém se má vyhodnotit operací ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="78f8e-149">Other use of parentheses is to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="78f8e-150">Další informace najdete v tématu [závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) část [operátory](../../programming-guide/statements-expressions-operators/operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="78f8e-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="78f8e-151">Seznam operátorů seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="78f8e-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="78f8e-152">typeof – operátor</span><span class="sxs-lookup"><span data-stu-id="78f8e-152">typeof operator</span></span>

<span data-ttu-id="78f8e-153">`typeof` Získá operátor <xref:System.Type?displayProperty=nameWithType> instanci typu.</span><span class="sxs-lookup"><span data-stu-id="78f8e-153">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="78f8e-154">Argument `typeof` operator musí být název typu nebo parametr typu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="78f8e-154">An argument of the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="78f8e-155">Můžete také použít `typeof` operátor s nevázaného obecných typů.</span><span class="sxs-lookup"><span data-stu-id="78f8e-155">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="78f8e-156">Název nevázaný parametr generického typu musí obsahovat odpovídající počet čárkami, které je menší než počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="78f8e-156">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="78f8e-157">Následující příklad ukazuje použití `typeof` operátor s nevázaný parametr generického typu:</span><span class="sxs-lookup"><span data-stu-id="78f8e-157">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="78f8e-158">Výraz nemůže být argument `typeof` operátor.</span><span class="sxs-lookup"><span data-stu-id="78f8e-158">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="78f8e-159">Chcete-li získat <xref:System.Type?displayProperty=nameWithType> instance modulu runtime typu výsledku výrazu, použijte <xref:System.Object.GetType%2A?displayProperty=nameWithType> – metoda.</span><span class="sxs-lookup"><span data-stu-id="78f8e-159">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of the expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="78f8e-160">Typ testování se `typeof` – operátor</span><span class="sxs-lookup"><span data-stu-id="78f8e-160">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="78f8e-161">Použití `typeof` operátor ke kontrole, pokud modul runtime typu výsledku výrazu přesně odpovídá daného typu.</span><span class="sxs-lookup"><span data-stu-id="78f8e-161">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="78f8e-162">Následující příklad ukazuje rozdíl mezi kontrola typu pomocí provádí `typeof` operátor a [je operátor](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="78f8e-162">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="78f8e-163">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="78f8e-163">Operator overloadability</span></span>

<span data-ttu-id="78f8e-164">`is`, `as`, A `typeof` nejsou přetížitelné operátory.</span><span class="sxs-lookup"><span data-stu-id="78f8e-164">The `is`, `as`, and `typeof` operators are not overloadable.</span></span>

<span data-ttu-id="78f8e-165">Uživatelem definovaný typ nejde přetížit `()` operátoru, ale můžete definovat vlastní typ převody, které může provádět výraz přetypování.</span><span class="sxs-lookup"><span data-stu-id="78f8e-165">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="78f8e-166">Další informace najdete v tématu [uživatelsky definovaný převod operátorů](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="78f8e-166">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="78f8e-167">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="78f8e-167">C# language specification</span></span>

<span data-ttu-id="78f8e-168">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="78f8e-168">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="78f8e-169">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="78f8e-169">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="78f8e-170">Operátor as</span><span class="sxs-lookup"><span data-stu-id="78f8e-170">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="78f8e-171">Výrazy přetypování</span><span class="sxs-lookup"><span data-stu-id="78f8e-171">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="78f8e-172">Typeof – operátor</span><span class="sxs-lookup"><span data-stu-id="78f8e-172">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="78f8e-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78f8e-173">See also</span></span>

- [<span data-ttu-id="78f8e-174">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="78f8e-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="78f8e-175">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="78f8e-175">C# operators</span></span>](index.md)
- [<span data-ttu-id="78f8e-176">Postupy: bezpečné vícesměrového vysílání pomocí porovnávání vzorů a je a jako operátory</span><span class="sxs-lookup"><span data-stu-id="78f8e-176">How to: safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
