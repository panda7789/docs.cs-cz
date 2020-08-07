---
title: Operátory testování typů a přetypování – reference jazyka C#
description: Seznamte se s operátory jazyka C#, které lze použít ke kontrole typu výsledku výrazu a v případě potřeby jej převést na jiný typ.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
- as
- typeof
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
ms.openlocfilehash: 328a40f0213cbb55f86e16625507c1a5a5d775fb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855826"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="cf271-103">Operátory testování typů a výraz přetypování (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cf271-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="cf271-104">Pomocí následujících operátorů a výrazů můžete provést kontrolu typu nebo převod typu:</span><span class="sxs-lookup"><span data-stu-id="cf271-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="cf271-105">[is – operátor](#is-operator): Pokud chcete zjistit, jestli je běhový typ výrazu kompatibilní s daným typem</span><span class="sxs-lookup"><span data-stu-id="cf271-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="cf271-106">[as – operátor](#as-operator)pro explicitní převod výrazu na daný typ, pokud je jeho typ modulu runtime kompatibilní s daným typem</span><span class="sxs-lookup"><span data-stu-id="cf271-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="cf271-107">[výraz cast](#cast-expression): k provedení explicitního převodu</span><span class="sxs-lookup"><span data-stu-id="cf271-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="cf271-108">[typeof – operátor](#typeof-operator): pro získání <xref:System.Type?displayProperty=nameWithType> instance pro typ</span><span class="sxs-lookup"><span data-stu-id="cf271-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="cf271-109">is – operátor</span><span class="sxs-lookup"><span data-stu-id="cf271-109">is operator</span></span>

<span data-ttu-id="cf271-110">`is`Operátor zkontroluje, zda je typ modulu runtime výsledku výrazu kompatibilní s daným typem.</span><span class="sxs-lookup"><span data-stu-id="cf271-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="cf271-111">Počínaje jazykem C# 7,0 `is` operátor také testuje výsledek výrazu proti vzorci.</span><span class="sxs-lookup"><span data-stu-id="cf271-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="cf271-112">Výraz s `is` operátorem testování typu má následující formu.</span><span class="sxs-lookup"><span data-stu-id="cf271-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="cf271-113">kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="cf271-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="cf271-114">`E`nemůže být anonymní metoda nebo výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="cf271-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="cf271-115">`E is T`Výraz vrátí `true` , pokud výsledek `E` není null a lze jej převést na typ `T` pomocí převodu odkazu, převodu zabalení nebo převodu rozbalení. v opačném případě vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="cf271-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="cf271-116">`is`Operátor nebere v úvahu uživatelsky definované převody.</span><span class="sxs-lookup"><span data-stu-id="cf271-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="cf271-117">Následující příklad ukazuje, že `is` operátor vrátí, `true` Pokud typ modulu runtime výsledku výrazu je odvozen z daného typu, to znamená, že existuje převod odkazu mezi typy:</span><span class="sxs-lookup"><span data-stu-id="cf271-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="cf271-118">Následující příklad ukazuje, že `is` operátor vezme v úvahu převody zabalení a rozbalení, ale nebere v úvahu [číselné převody](../builtin-types/numeric-conversions.md):</span><span class="sxs-lookup"><span data-stu-id="cf271-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="cf271-119">Informace o převodech jazyka C# naleznete v kapitole [převody](~/_csharplang/spec/conversions.md) [specifikace jazyka c#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cf271-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="cf271-120">Testování typu s porovnáváním vzorů</span><span class="sxs-lookup"><span data-stu-id="cf271-120">Type testing with pattern matching</span></span>

<span data-ttu-id="cf271-121">Počínaje jazykem C# 7,0 `is` operátor také testuje výsledek výrazu proti vzorci.</span><span class="sxs-lookup"><span data-stu-id="cf271-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="cf271-122">Konkrétně podporuje vzor typu v následujícím tvaru:</span><span class="sxs-lookup"><span data-stu-id="cf271-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="cf271-123">kde `E` je výraz, který vrací hodnotu, `T` je název typu nebo parametr typu a `v` je nová lokální proměnná typu `T` .</span><span class="sxs-lookup"><span data-stu-id="cf271-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="cf271-124">Pokud výsledek `E` je jiný než null a lze jej převést na `T` odkaz, zabalení nebo rozbalení, `E is T v` výraz se vrátí `true` a převedená hodnota výsledku `E` je přiřazena proměnné `v` .</span><span class="sxs-lookup"><span data-stu-id="cf271-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="cf271-125">Následující příklad ukazuje použití `is` operátoru se vzorem typu:</span><span class="sxs-lookup"><span data-stu-id="cf271-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="cf271-126">Další informace o vzoru typu a dalších podporovaných vzorech naleznete v tématu [porovnávání vzorů s](../keywords/is.md#pattern-matching-with-is)parametrem is.</span><span class="sxs-lookup"><span data-stu-id="cf271-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="cf271-127">Operátor as</span><span class="sxs-lookup"><span data-stu-id="cf271-127">as operator</span></span>

<span data-ttu-id="cf271-128">`as`Operátor explicitně převede výsledek výrazu na daný odkaz nebo typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="cf271-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="cf271-129">Pokud převod není možný, `as` vrátí operátor `null` .</span><span class="sxs-lookup"><span data-stu-id="cf271-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="cf271-130">Na rozdíl od [výrazu přetypování](#cast-expression) `as` operátor nikdy nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="cf271-130">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="cf271-131">Výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="cf271-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="cf271-132">kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu, vytvoří stejný výsledek jako</span><span class="sxs-lookup"><span data-stu-id="cf271-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="cf271-133">s výjimkou, že `E` je vyhodnocena pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="cf271-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="cf271-134">`as`Operátor zohledňuje pouze odkazy, převody s možnou hodnotou null, zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="cf271-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="cf271-135">Operátor nelze použít `as` k provedení převodu definovaného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="cf271-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="cf271-136">K tomu použijte [výraz cast](#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="cf271-136">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="cf271-137">Následující příklad ukazuje použití `as` operátoru:</span><span class="sxs-lookup"><span data-stu-id="cf271-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="cf271-138">Jak ukazuje předchozí příklad, je nutné porovnat výsledek `as` výrazu s `null` a zjistit, zda převod proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="cf271-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="cf271-139">Počínaje jazykem C# 7,0 můžete použít [operátor is](#type-testing-with-pattern-matching) pro testování, zda je převod úspěšný, a pokud je úspěšný, přiřaďte výsledek k nové proměnné.</span><span class="sxs-lookup"><span data-stu-id="cf271-139">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="cf271-140">Výraz cast</span><span class="sxs-lookup"><span data-stu-id="cf271-140">Cast expression</span></span>

<span data-ttu-id="cf271-141">Výraz přetypování formuláře `(T)E` provádí explicitní převod výsledku výrazu `E` na typ `T` .</span><span class="sxs-lookup"><span data-stu-id="cf271-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="cf271-142">Pokud neexistuje žádný explicitní převod z typu `E` na typ `T` , dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="cf271-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="cf271-143">V době spuštění explicitní převod nemusí být úspěšný a výraz přetypování může vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="cf271-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="cf271-144">Následující příklad ukazuje explicitní číselné a referenční převody:</span><span class="sxs-lookup"><span data-stu-id="cf271-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="cf271-145">Informace o podporovaných explicitních převodech naleznete v části [explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cf271-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="cf271-146">Informace o tom, jak definovat vlastní explicitní nebo implicitní převod typu, naleznete v části [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf271-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="cf271-147">Další použití pro ()</span><span class="sxs-lookup"><span data-stu-id="cf271-147">Other usages of ()</span></span>

<span data-ttu-id="cf271-148">K [volání metody nebo vyvolání delegáta](member-access-operators.md#invocation-expression-)můžete také použít kulaté závorky.</span><span class="sxs-lookup"><span data-stu-id="cf271-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="cf271-149">Jiné použití závorek je upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="cf271-149">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="cf271-150">Další informace naleznete v tématu [operátory jazyka C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="cf271-150">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="cf271-151">typeof – operátor</span><span class="sxs-lookup"><span data-stu-id="cf271-151">typeof operator</span></span>

<span data-ttu-id="cf271-152">`typeof`Operátor získá <xref:System.Type?displayProperty=nameWithType> instanci pro typ.</span><span class="sxs-lookup"><span data-stu-id="cf271-152">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="cf271-153">Argument `typeof` operátoru musí být název typu nebo parametr typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="cf271-153">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="cf271-154">Operátor můžete také použít `typeof` s nevázanými obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="cf271-154">You can also use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="cf271-155">Název nevázaného obecného typu musí obsahovat odpovídající počet čárek, což je jedna hodnota, která je menší než počet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="cf271-155">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="cf271-156">Následující příklad ukazuje použití `typeof` operátoru s nevázaným obecným typem:</span><span class="sxs-lookup"><span data-stu-id="cf271-156">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="cf271-157">Výraz nemůže být argumentem `typeof` operátoru.</span><span class="sxs-lookup"><span data-stu-id="cf271-157">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="cf271-158">Chcete-li získat <xref:System.Type?displayProperty=nameWithType> instanci pro běhový typ výsledku výrazu, použijte <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="cf271-158">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="cf271-159">Testování typu pomocí `typeof` operátoru</span><span class="sxs-lookup"><span data-stu-id="cf271-159">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="cf271-160">Použijte `typeof` operátor ke kontrole, zda typ modulu runtime výsledku výrazu přesně odpovídá danému typu.</span><span class="sxs-lookup"><span data-stu-id="cf271-160">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="cf271-161">Následující příklad ukazuje rozdíl mezi kontrolou typu provedenými s `typeof` operátorem a [operátorem is](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="cf271-161">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="cf271-162">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="cf271-162">Operator overloadability</span></span>

<span data-ttu-id="cf271-163">`is`Operátory, `as` a `typeof` nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="cf271-163">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="cf271-164">Uživatelsky definovaný typ nemůže přetížit `()` operátor, ale může definovat vlastní převody typů, které mohou být provedeny výrazem přetypování.</span><span class="sxs-lookup"><span data-stu-id="cf271-164">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="cf271-165">Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cf271-165">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cf271-166">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cf271-166">C# language specification</span></span>

<span data-ttu-id="cf271-167">Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="cf271-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="cf271-168">Operátor is</span><span class="sxs-lookup"><span data-stu-id="cf271-168">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="cf271-169">Operátor as</span><span class="sxs-lookup"><span data-stu-id="cf271-169">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="cf271-170">Výrazy cast</span><span class="sxs-lookup"><span data-stu-id="cf271-170">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="cf271-171">Operátor typeof</span><span class="sxs-lookup"><span data-stu-id="cf271-171">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="cf271-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf271-172">See also</span></span>

- [<span data-ttu-id="cf271-173">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="cf271-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cf271-174">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="cf271-174">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="cf271-175">Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů is a as</span><span class="sxs-lookup"><span data-stu-id="cf271-175">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="cf271-176">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="cf271-176">Generics in .NET</span></span>](../../../standard/generics/index.md)
