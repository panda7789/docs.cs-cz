---
title: Operátory testování typů a výraz přetypování – odkaz Jazyka C#
description: Další informace o operátory Jazyka C#, které můžete použít ke kontrole typu výsledku výrazu a převést jej na jiný typ v případě potřeby.
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
ms.openlocfilehash: 5a4f1d4c0c2ddd0d3967e15090d8f8c1ac42f83e
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121420"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="9040c-103">Operátory testování typů a výraz přetypování (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="9040c-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="9040c-104">K provedení kontroly typu nebo převodu typu můžete použít následující operátory a výrazy:</span><span class="sxs-lookup"><span data-stu-id="9040c-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="9040c-105">[je operátor](#is-operator): kontrola, zda je typ runtime výrazu kompatibilní s daným typem</span><span class="sxs-lookup"><span data-stu-id="9040c-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="9040c-106">[jako operátor](#as-operator): explicitně převést výraz na daný typ, pokud je jeho typ runtime kompatibilní s tímto typem</span><span class="sxs-lookup"><span data-stu-id="9040c-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="9040c-107">[výraz přetypování](#cast-expression): provedení explicitního převodu</span><span class="sxs-lookup"><span data-stu-id="9040c-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="9040c-108">[typeof operátor](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> získat instanci pro typ</span><span class="sxs-lookup"><span data-stu-id="9040c-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="9040c-109">je operátor</span><span class="sxs-lookup"><span data-stu-id="9040c-109">is operator</span></span>

<span data-ttu-id="9040c-110">Operátor `is` zkontroluje, zda je typ runtime výsledku výrazu kompatibilní s daným typem.</span><span class="sxs-lookup"><span data-stu-id="9040c-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="9040c-111">Počínaje C# 7.0, `is` operátor také testuje výsledek výrazu proti vzoru.</span><span class="sxs-lookup"><span data-stu-id="9040c-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="9040c-112">Výraz s operátorem `is` typ-testing má následující formulář</span><span class="sxs-lookup"><span data-stu-id="9040c-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="9040c-113">kde `E` je výraz, který `T` vrací hodnotu a je název typu nebo typu parametr.</span><span class="sxs-lookup"><span data-stu-id="9040c-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="9040c-114">`E`nemůže být anonymní metoda nebo lambda výraz.</span><span class="sxs-lookup"><span data-stu-id="9040c-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="9040c-115">Výraz `E is T` vrátí, `true` pokud `E` výsledek je non-null a lze `T` převést na typ odkaz převodu, zabalení převodu nebo unboxing převodu; v opačném `false`případě vrátí .</span><span class="sxs-lookup"><span data-stu-id="9040c-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="9040c-116">Operátor `is` nebere v úvahu uživatelem definované převody.</span><span class="sxs-lookup"><span data-stu-id="9040c-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="9040c-117">Následující příklad ukazuje, `is` že `true` operátor vrátí, pokud typ runtime výsledku výrazu pochází z daného typu, to znamená, že existuje převod odkazu mezi typy:</span><span class="sxs-lookup"><span data-stu-id="9040c-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="9040c-118">Následující příklad ukazuje, `is` že operátor bere v úvahu převody zabalení a rozbalení, ale nebere v úvahu [číselné převody](../builtin-types/numeric-conversions.md):</span><span class="sxs-lookup"><span data-stu-id="9040c-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="9040c-119">Informace o převodech jazyka C# naleznete v kapitole [Převody](~/_csharplang/spec/conversions.md) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9040c-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="9040c-120">Testování typů s porovnáváním vzorů</span><span class="sxs-lookup"><span data-stu-id="9040c-120">Type testing with pattern matching</span></span>

<span data-ttu-id="9040c-121">Počínaje C# 7.0, `is` operátor také testuje výsledek výrazu proti vzoru.</span><span class="sxs-lookup"><span data-stu-id="9040c-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="9040c-122">Zejména podporuje vzor typu v následujícím formuláři:</span><span class="sxs-lookup"><span data-stu-id="9040c-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="9040c-123">kde `E` je výraz, který `T` vrací hodnotu, je název typu `v` nebo parametru typu `T`a je novou místní proměnnou typu .</span><span class="sxs-lookup"><span data-stu-id="9040c-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="9040c-124">`E` Pokud je výsledek nenulové a lze jej `T` převést na převod odkazu, zabalení nebo rozbalení, `E is T v` výraz vrátí `true` a převedená hodnota výsledku `E` je přiřazena proměnné `v`.</span><span class="sxs-lookup"><span data-stu-id="9040c-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="9040c-125">Následující příklad ukazuje použití operátoru `is` se vzorem typu:</span><span class="sxs-lookup"><span data-stu-id="9040c-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="9040c-126">Další informace o vzoru typu a dalších podporovaných vzorech naleznete v [tématu Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span><span class="sxs-lookup"><span data-stu-id="9040c-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="9040c-127">jako operátor</span><span class="sxs-lookup"><span data-stu-id="9040c-127">as operator</span></span>

<span data-ttu-id="9040c-128">Operátor `as` explicitně převede výsledek výrazu na daný odkaz nebo typ hodnoty s hodnotou, kterou lze hodnotit s hodnotou s hodnotou s možnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="9040c-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="9040c-129">Pokud převod není možný, `as` operátor `null`vrátí .</span><span class="sxs-lookup"><span data-stu-id="9040c-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="9040c-130">Na rozdíl od `as` [výrazu přetypování](#cast-expression)operátor nikdy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="9040c-130">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="9040c-131">Vyjádření formuláře</span><span class="sxs-lookup"><span data-stu-id="9040c-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="9040c-132">kde `E` je výraz, který `T` vrací hodnotu a je název typu nebo parametru typu, vytváří stejný výsledek jako</span><span class="sxs-lookup"><span data-stu-id="9040c-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="9040c-133">kromě `E` toho, že se vyhodnocuje pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="9040c-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="9040c-134">Operátor `as` považuje pouze odkaz, null, zabalení a unboxing převody.</span><span class="sxs-lookup"><span data-stu-id="9040c-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="9040c-135">`as` Operátor nelze použít k provedení převodu definovaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="9040c-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="9040c-136">Chcete-li to provést, použijte [výraz přetypování](#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="9040c-136">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="9040c-137">Následující příklad ukazuje použití operátoru: `as`</span><span class="sxs-lookup"><span data-stu-id="9040c-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="9040c-138">Jak ukazuje předchozí příklad, je třeba porovnat `as` výsledek `null` výrazu s ke kontrole, zda je převod úspěšný.</span><span class="sxs-lookup"><span data-stu-id="9040c-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="9040c-139">Počínaje C# 7.0, můžete použít [operátor is](#type-testing-with-pattern-matching) jak k testování, pokud je převod úspěšný, a pokud je úspěšný, přiřadit jeho výsledek nové proměnné.</span><span class="sxs-lookup"><span data-stu-id="9040c-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="9040c-140">Výraz přetypování</span><span class="sxs-lookup"><span data-stu-id="9040c-140">Cast expression</span></span>

<span data-ttu-id="9040c-141">Výraz přetypování `(T)E` formuláře provádí explicitní převod výsledku `E` `T`výrazu na typ .</span><span class="sxs-lookup"><span data-stu-id="9040c-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="9040c-142">Pokud neexistuje žádný explicitní převod `E` z `T`typu typu na typ , dojde k chybě v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="9040c-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="9040c-143">V době běhu explicitní převod nemusí být úspěšné a výraz přetypování může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="9040c-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="9040c-144">Následující příklad ukazuje explicitní číselné a referenční převody:</span><span class="sxs-lookup"><span data-stu-id="9040c-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="9040c-145">Informace o podporovaných explicitních konverzích naleznete v části [Explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9040c-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="9040c-146">Informace o tom, jak definovat vlastní explicitní nebo implicitní převod typu, naleznete v [tématu Uživatelem definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9040c-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="9040c-147">Ostatní použití ()</span><span class="sxs-lookup"><span data-stu-id="9040c-147">Other usages of ()</span></span>

<span data-ttu-id="9040c-148">Závorky můžete také použít k [volání metody nebo vyvolání delegáta](member-access-operators.md#invocation-expression-).</span><span class="sxs-lookup"><span data-stu-id="9040c-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="9040c-149">Jiné použití závorek je upravit pořadí, ve kterém chcete vyhodnotit operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="9040c-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="9040c-150">Další informace naleznete v tématu [C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="9040c-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="9040c-151">typeof – operátor</span><span class="sxs-lookup"><span data-stu-id="9040c-151">typeof operator</span></span>

<span data-ttu-id="9040c-152">Operátor `typeof` získá instanci <xref:System.Type?displayProperty=nameWithType> pro typ.</span><span class="sxs-lookup"><span data-stu-id="9040c-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="9040c-153">Argument pro `typeof` operátor musí být název typu nebo parametr typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="9040c-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="9040c-154">Můžete také použít `typeof` operátor s nevázanými obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="9040c-154">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="9040c-155">Název nevázaného obecného typu musí obsahovat příslušný počet čárek, což je o jeden menší než počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="9040c-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="9040c-156">Následující příklad ukazuje použití `typeof` operátoru s nevázaným obecným typem:</span><span class="sxs-lookup"><span data-stu-id="9040c-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="9040c-157">Výraz nemůže být argumentem `typeof` operátoru.</span><span class="sxs-lookup"><span data-stu-id="9040c-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="9040c-158">Chcete-li <xref:System.Type?displayProperty=nameWithType> získat instanci pro typ runtime <xref:System.Object.GetType%2A?displayProperty=nameWithType> výsledku výrazu, použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="9040c-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="9040c-159">Typové zkoušky `typeof` s obsluhou</span><span class="sxs-lookup"><span data-stu-id="9040c-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="9040c-160">Pomocí `typeof` operátoru zkontrolujte, zda typ runtime výsledku výrazu přesně odpovídá danému typu.</span><span class="sxs-lookup"><span data-stu-id="9040c-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="9040c-161">Následující příklad ukazuje rozdíl mezi kontrolou typu `typeof` provedenou s operátorem a [operátorem is](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="9040c-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="9040c-162">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="9040c-162">Operator overloadability</span></span>

<span data-ttu-id="9040c-163">V `is` `as`, `typeof` , a operátory nelze přetíženy.</span><span class="sxs-lookup"><span data-stu-id="9040c-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="9040c-164">Uživatelem definovaný typ nemůže `()` přetížit operátor, ale může definovat převody vlastního typu, které lze provést výrazem přetypování.</span><span class="sxs-lookup"><span data-stu-id="9040c-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="9040c-165">Další informace naleznete v [tématu User-defined operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9040c-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9040c-166">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9040c-166">C# language specification</span></span>

<span data-ttu-id="9040c-167">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="9040c-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="9040c-168">Operátor is</span><span class="sxs-lookup"><span data-stu-id="9040c-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="9040c-169">Jako operátor</span><span class="sxs-lookup"><span data-stu-id="9040c-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="9040c-170">Výrazy obsazení</span><span class="sxs-lookup"><span data-stu-id="9040c-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="9040c-171">Typ operátoru</span><span class="sxs-lookup"><span data-stu-id="9040c-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="9040c-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="9040c-172">See also</span></span>

- [<span data-ttu-id="9040c-173">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="9040c-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9040c-174">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9040c-174">C# operators</span></span>](index.md)
- [<span data-ttu-id="9040c-175">Jak bezpečně obsazení pomocí porovnávání vzorů a je a jako operátory</span><span class="sxs-lookup"><span data-stu-id="9040c-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="9040c-176">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="9040c-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
