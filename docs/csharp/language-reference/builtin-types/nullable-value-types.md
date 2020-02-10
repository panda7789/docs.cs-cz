---
title: Typy hodnot s možnou hodnotou null – C# referenční informace
description: Další informace C# o typech hodnot s možnou hodnotou null a jejich použití
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: bd90a0b1b77349efe581eb8aae44c58802ba756d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093185"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="b1dad-103">Typy hodnot s možnou hodnotou null (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="b1dad-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="b1dad-104">*Typ hodnoty s možnou hodnotou null* `T?` představuje všechny hodnoty svého základního [typu hodnoty](value-types.md) `T` a další hodnotu [null](../keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="b1dad-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="b1dad-105">Můžete například přiřadit libovolné z následujících tří hodnot `bool?` proměnné: `true`, `false`nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="b1dad-106">Základní typ hodnoty `T` nemůže být typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b1dad-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="b1dad-107">C#8,0 zavádí funkci typů odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b1dad-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="b1dad-108">Další informace naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="b1dad-108">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="b1dad-109">Typy s C# možnou hodnotou null jsou k dispozici od 2.</span><span class="sxs-lookup"><span data-stu-id="b1dad-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="b1dad-110">Libovolný typ hodnoty s možnou hodnotou null je instance obecné <xref:System.Nullable%601?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="b1dad-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="b1dad-111">Můžete odkazovat na typ hodnoty s možnou hodnotou null s podkladovým typem `T` v některém z následujících formulářů, které lze zaměnit: `Nullable<T>` nebo `T?`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="b1dad-112">Pokud potřebujete reprezentovat nedefinovanou hodnotu základního typu hodnoty, obvykle se používá typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b1dad-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="b1dad-113">Například logická hodnota nebo `bool`proměnná může být pouze `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="b1dad-114">V některých aplikacích však může být hodnota proměnné nedefinovaná nebo chybí.</span><span class="sxs-lookup"><span data-stu-id="b1dad-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="b1dad-115">Pole databáze může například obsahovat `true` nebo `false`, nebo nemusí vůbec obsahovat žádnou hodnotu, to znamená `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="b1dad-116">V tomto scénáři můžete použít `bool?` typ.</span><span class="sxs-lookup"><span data-stu-id="b1dad-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="b1dad-117">Deklarace a přiřazení</span><span class="sxs-lookup"><span data-stu-id="b1dad-117">Declaration and assignment</span></span>

<span data-ttu-id="b1dad-118">Typ hodnoty je implicitně převoditelný na odpovídající typ hodnoty s možnou hodnotou null, takže můžete přiřadit hodnotu proměnné typu hodnoty s možnou hodnotou null, jako byste to proznamenali pro svůj základní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b1dad-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="b1dad-119">Můžete také přiřadit hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-119">You also can assign the `null` value.</span></span> <span data-ttu-id="b1dad-120">Například:</span><span class="sxs-lookup"><span data-stu-id="b1dad-120">For example:</span></span>

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="b1dad-121">Výchozí hodnota typu hodnoty s možnou hodnotou null představuje `null`, to znamená, že se jedná o instanci, jejíž vlastnost <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> vrací `false`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="b1dad-122">Zkoumání instance typu hodnoty s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b1dad-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="b1dad-123">Počínaje C# 7,0 můžete použít [operátor`is` se vzorkem typu](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) pro prohlédnutí instance typu hodnoty s možnou hodnotou null pro `null` a načtení hodnoty nadřazeného typu:</span><span class="sxs-lookup"><span data-stu-id="b1dad-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="b1dad-124">Vždy můžete použít následující vlastnosti jen pro čtení k prohlédnutí a získání hodnoty proměnné typu s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="b1dad-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="b1dad-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> určuje, zda instance typu hodnoty s možnou hodnotou null má hodnotu svého nadřízeného typu.</span><span class="sxs-lookup"><span data-stu-id="b1dad-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="b1dad-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Získá hodnotu základního typu, pokud je <xref:System.Nullable%601.HasValue%2A> `true`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="b1dad-127">Pokud je <xref:System.Nullable%601.HasValue%2A> `false`, vlastnost <xref:System.Nullable%601.Value%2A> vyvolá <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="b1dad-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="b1dad-128">Následující příklad používá vlastnost `HasValue` k otestování, zda proměnná obsahuje hodnotu před jejich zobrazením:</span><span class="sxs-lookup"><span data-stu-id="b1dad-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="b1dad-129">Můžete také porovnat proměnnou typu hodnoty s možnou hodnotou null s `null` namísto použití vlastnosti `HasValue`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="b1dad-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="b1dad-130">Převod z typu hodnoty s možnou hodnotou null na nadřízený typ</span><span class="sxs-lookup"><span data-stu-id="b1dad-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="b1dad-131">Pokud chcete přiřadit hodnotu typu hodnoty s možnou hodnotou null na proměnnou typu hodnoty, která není null, možná budete muset zadat hodnotu, která má být přiřazena místo `null`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="b1dad-132">Použijte [operátor slučování s hodnotou null `??`](../operators/null-coalescing-operator.md) k tomu, abyste to mohli udělat (můžete také použít metodu <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> pro stejný účel):</span><span class="sxs-lookup"><span data-stu-id="b1dad-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="b1dad-133">Pokud chcete použít [výchozí](default-values.md) hodnotu základního typu hodnoty místo `null`, použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1dad-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b1dad-134">Typ hodnoty s možnou hodnotou null můžete také explicitně přetypovat na typ, který není null, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="b1dad-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

<span data-ttu-id="b1dad-135">V době běhu, pokud je hodnota typu hodnoty s možnou hodnotou null `null`, vyvolá explicitní přetypování <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="b1dad-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="b1dad-136">Typ hodnoty, která není null, `T`, se implicitně převodit na odpovídající typ hodnoty s možnou hodnotou null `T?`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="b1dad-137">Zrušené operátory</span><span class="sxs-lookup"><span data-stu-id="b1dad-137">Lifted operators</span></span>

<span data-ttu-id="b1dad-138">Předdefinované unární a binární [operátory](../operators/index.md) nebo jakékoli přetížené operátory, které jsou podporovány hodnotou typu `T`, jsou podporovány také odpovídajícím typem hodnoty s možnou hodnotou null `T?`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="b1dad-139">Tyto operátory, označované také jako přenesené *operátory*, vyvolávají `null`, pokud jsou jeden nebo oba operandy `null`; v opačném případě operátor používá k výpočtu výsledku obsažené hodnoty operandů.</span><span class="sxs-lookup"><span data-stu-id="b1dad-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="b1dad-140">Například:</span><span class="sxs-lookup"><span data-stu-id="b1dad-140">For example:</span></span>

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="b1dad-141">Pro `bool?` typ `&` předdefinované operátory a `|` nepostupují podle pravidel popsaných v této části: výsledek vyhodnocení operátoru může být bez hodnoty null, i když je jeden z operandů `null`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="b1dad-142">Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="b1dad-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="b1dad-143">Pro [operátory porovnání](../operators/comparison-operators.md) `<`, `>`, `<=`a `>=`platí, že pokud je jeden nebo oba operandy `null`, výsledek je `false`; v opačném případě jsou obsažené hodnoty operandů porovnány.</span><span class="sxs-lookup"><span data-stu-id="b1dad-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="b1dad-144">Nepředpokládáme, že protože konkrétní porovnání (například `<=`) vrátí `false`, opačné porovnání (`>`) vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="b1dad-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="b1dad-145">Následující příklad ukazuje, že 10</span><span class="sxs-lookup"><span data-stu-id="b1dad-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="b1dad-146">ani větší než nebo rovno `null`</span><span class="sxs-lookup"><span data-stu-id="b1dad-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="b1dad-147">bez `null`</span><span class="sxs-lookup"><span data-stu-id="b1dad-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="b1dad-148">U [operátoru rovnosti](../operators/equality-operators.md#equality-operator-) `==`, pokud jsou oba operandy `null`, je výsledek `true`, pokud je `null`pouze jeden z operandů, výsledek je `false`; v opačném případě jsou obsažené hodnoty operandů porovnány.</span><span class="sxs-lookup"><span data-stu-id="b1dad-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="b1dad-149">Pro [operátor nerovnosti](../operators/equality-operators.md#inequality-operator-) `!=`, jsou-li oba operandy `null`, je výsledek `false`, pokud je `null`pouze jeden z operandů, výsledek je `true`; v opačném případě jsou obsažené hodnoty operandů porovnány.</span><span class="sxs-lookup"><span data-stu-id="b1dad-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="b1dad-150">Pokud existuje [uživatelem definovaný převod](../operators/user-defined-conversion-operators.md) mezi dvěma typy hodnot, stejný převod lze použít také mezi odpovídajícími typy hodnot s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b1dad-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="b1dad-151">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="b1dad-151">Boxing and unboxing</span></span>

<span data-ttu-id="b1dad-152">Instance typu hodnoty s možnou hodnotou null `T?` je [zabalená](../../programming-guide/types/boxing-and-unboxing.md) takto:</span><span class="sxs-lookup"><span data-stu-id="b1dad-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="b1dad-153">Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `false`, je vytvořen odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b1dad-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="b1dad-154">Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`, odpovídající hodnota typu podkladové hodnoty `T` je zabalená, nikoli instance <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="b1dad-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="b1dad-155">Můžete unbox zabalenou hodnotu typu hodnoty `T` k odpovídajícímu typu hodnoty s možnou hodnotou null `T?`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="b1dad-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="b1dad-156">Jak identifikovat typ hodnoty s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b1dad-156">How to identify a nullable value type</span></span>

<span data-ttu-id="b1dad-157">Následující příklad ukazuje, jak určit, zda <xref:System.Type?displayProperty=nameWithType> instance představuje konstruovaný typ hodnoty s možnou hodnotou null, tj. <xref:System.Nullable%601?displayProperty=nameWithType> typ se zadaným parametrem typu `T`:</span><span class="sxs-lookup"><span data-stu-id="b1dad-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="b1dad-158">Jak ukazuje příklad, použijte operátor [typeof](../operators/type-testing-and-cast.md#typeof-operator) k vytvoření instance <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1dad-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="b1dad-159">Chcete-li určit, zda je instance typu s možnou hodnotou null, nepoužívejte metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> k získání <xref:System.Type> instance, která má být testována pomocí předchozího kódu.</span><span class="sxs-lookup"><span data-stu-id="b1dad-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="b1dad-160">Při volání metody <xref:System.Object.GetType%2A?displayProperty=nameWithType> u instance typu hodnoty s možnou hodnotou null je instance [zabalena](#boxing-and-unboxing) do <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b1dad-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="b1dad-161">Jako zabalení instance typu s možnou hodnotou null je ekvivalentem zabalení hodnoty nenulového typu, <xref:System.Object.GetType%2A> vrátí instanci <xref:System.Type>, která představuje nadřízený typ hodnoty s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="b1dad-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

<span data-ttu-id="b1dad-162">Nepoužívejte také operátor [is](../operators/type-testing-and-cast.md#is-operator) k určení, zda je instance typu hodnot s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b1dad-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="b1dad-163">Jak ukazuje následující příklad, nelze odlišit typy instance typu s možnou hodnotou null a její základní typ instance s operátorem `is`:</span><span class="sxs-lookup"><span data-stu-id="b1dad-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="b1dad-164">K určení, zda je instance typu s možnou hodnotou null, lze použít kód prezentovaný v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b1dad-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="b1dad-165">Metody popsané v této části se nevztahují na [typy odkazů s možnou hodnotou null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="b1dad-165">The methods described in this section are not applicable in the case of [nullable reference types](../../nullable-references.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b1dad-166">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1dad-166">C# language specification</span></span>

<span data-ttu-id="b1dad-167">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="b1dad-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b1dad-168">Typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b1dad-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="b1dad-169">Zrušené operátory</span><span class="sxs-lookup"><span data-stu-id="b1dad-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="b1dad-170">Implicitní převody s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b1dad-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="b1dad-171">Explicitní převody s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b1dad-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="b1dad-172">Zrušené operátory převodu</span><span class="sxs-lookup"><span data-stu-id="b1dad-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="b1dad-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1dad-173">See also</span></span>

- [<span data-ttu-id="b1dad-174">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="b1dad-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b1dad-175">Co přesně znamená "vyvoláno"?</span><span class="sxs-lookup"><span data-stu-id="b1dad-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b1dad-176">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b1dad-176">Nullable reference types</span></span>](../../nullable-references.md)
