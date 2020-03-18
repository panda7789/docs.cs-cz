---
title: Nullable typy hodnot - C# odkaz
description: Informace o typech hodnot s možnou hodnotou c# s možnou hodnotou a jejich použití
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: a84b3d60269491846b783e5046a84a1d14e258a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399586"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="752da-103">Typy hodnot s hodnotou Null (odkaz jazyka C# )</span><span class="sxs-lookup"><span data-stu-id="752da-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="752da-104">`T?` *Typ hodnoty s možnou hodnotou null* představuje všechny hodnoty jeho [základního typu](value-types.md) `T` hodnoty a další [hodnotu null.](../keywords/null.md)</span><span class="sxs-lookup"><span data-stu-id="752da-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="752da-105">Můžete například přiřadit `bool?` libovolnou z následujících tří `true` `false`hodnot `null`proměnné: , , nebo .</span><span class="sxs-lookup"><span data-stu-id="752da-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="752da-106">Základní typ `T` hodnoty nemůže být samotný typ hodnoty s možnou hodnotou s možnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="752da-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="752da-107">C# 8.0 zavádí funkci typů odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="752da-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="752da-108">Další informace naleznete v [tématu Nullable reference types](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="752da-108">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="752da-109">Null hodnoty typy jsou k dispozici počínaje C# 2.</span><span class="sxs-lookup"><span data-stu-id="752da-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="752da-110">Libovolný typ hodnoty s možnou <xref:System.Nullable%601?displayProperty=nameWithType> hodnotou null je instancí obecné struktury.</span><span class="sxs-lookup"><span data-stu-id="752da-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="752da-111">Můžete odkazovat na typ hodnoty s `T` možnou hodnotou s hodnotou `Nullable<T>` `T?`s hodnotou s podkladovým typem v některém z následujících zaměnitelných formulářů: nebo .</span><span class="sxs-lookup"><span data-stu-id="752da-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="752da-112">Typ hodnoty s možnou hodnotou s možnou hodnotou s možnou hodnotou, pokud potřebujete reprezentovat nedefinovanou hodnotu základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="752da-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="752da-113">Například boolean, nebo `bool`, proměnná `true` může `false`být pouze buď nebo .</span><span class="sxs-lookup"><span data-stu-id="752da-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="752da-114">V některých aplikacích však může být hodnota proměnné nedefinovaná nebo chybí.</span><span class="sxs-lookup"><span data-stu-id="752da-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="752da-115">Například databázové pole `true` může `false`obsahovat nebo , nebo může obsahovat žádnou hodnotu vůbec, to znamená . `NULL`</span><span class="sxs-lookup"><span data-stu-id="752da-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="752da-116">Můžete použít `bool?` typ v tomto scénáři.</span><span class="sxs-lookup"><span data-stu-id="752da-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="752da-117">Prohlášení a postoupení</span><span class="sxs-lookup"><span data-stu-id="752da-117">Declaration and assignment</span></span>

<span data-ttu-id="752da-118">Jako typ hodnoty je implicitně převoditelný na odpovídající typ hodnoty s hodnotou s hodnotou s hodnotou, můžete přiřadit hodnotu proměnné typu hodnoty s hodnotou s možnou hodnotou, jako byste to udělali pro jeho základní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="752da-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="752da-119">Můžete také přiřadit `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="752da-119">You also can assign the `null` value.</span></span> <span data-ttu-id="752da-120">Například:</span><span class="sxs-lookup"><span data-stu-id="752da-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="752da-121">Výchozí hodnota typu hodnoty s `null`možnou hodnotou s možnou <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> hodnotou s možnou hodnotou představuje , to znamená, že je to instance, jejíž vlastnost vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="752da-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="752da-122">Zkoumání instance typu hodnoty s možnou hodnotou, jejíž hodnotu lze</span><span class="sxs-lookup"><span data-stu-id="752da-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="752da-123">Počínaje C# 7.0, můžete použít [ `is` operátor s typem vzor](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) jak zkoumat instanci typu hodnoty s možnou hodnotou s hodnotou s hodnotou null `null` a načíst hodnotu základního typu:</span><span class="sxs-lookup"><span data-stu-id="752da-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="752da-124">Vždy můžete použít následující vlastnosti jen pro čtení prozkoumat a získat hodnotu proměnné typu hodnoty s hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="752da-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="752da-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>označuje, zda má instance typu hodnoty s možnou hodnotou, která má hodnotu, hodnotu svého základního typu.</span><span class="sxs-lookup"><span data-stu-id="752da-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="752da-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>získá hodnotu základního <xref:System.Nullable%601.HasValue%2A> typu, pokud je `true`.</span><span class="sxs-lookup"><span data-stu-id="752da-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="752da-127">Pokud <xref:System.Nullable%601.HasValue%2A> `false`je <xref:System.Nullable%601.Value%2A> , vlastnost <xref:System.InvalidOperationException>vyvolá .</span><span class="sxs-lookup"><span data-stu-id="752da-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="752da-128">Následující příklad používá `HasValue` vlastnost k testování, zda proměnná obsahuje hodnotu před zobrazením:</span><span class="sxs-lookup"><span data-stu-id="752da-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="752da-129">Můžete také porovnat proměnnou typu hodnoty `null` s možnou `HasValue` hodnotou s hodnotou s hodnotou s namísto použití vlastnosti, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="752da-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="752da-130">Převod z typu hodnoty s možnou hodnotou s možnou hodnotou na podkladový typ</span><span class="sxs-lookup"><span data-stu-id="752da-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="752da-131">Pokud chcete přiřadit hodnotu typu hodnoty s možnou hodnotou s hodnotou s hodnotou, která nelze `null`použít, proměnné typu hodnoty, kterou nelze hodnotit, může být nutné zadat hodnotu, která bude přiřazena místo .</span><span class="sxs-lookup"><span data-stu-id="752da-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="752da-132">K tomu použijte [operátor `??` null-coalescing](../operators/null-coalescing-operator.md) (metodu <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> můžete použít také ke stejnému účelu):</span><span class="sxs-lookup"><span data-stu-id="752da-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="752da-133">Pokud chcete použít [výchozí](default-values.md) hodnotu základního typu `null`hodnoty místo <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="752da-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="752da-134">Můžete také explicitně přetypovat typ hodnoty s hodnotou s hodnotou, který nelze uvážit, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="752da-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="752da-135">V době běhu, pokud je `null`hodnota typu hodnoty s možnou <xref:System.InvalidOperationException>hodnotou null , explicitní přetypování vyvolá .</span><span class="sxs-lookup"><span data-stu-id="752da-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="752da-136">Typ `T` hodnoty s hodnotou, který neshovuje, je implicitně převoditelný na odpovídající typ `T?`hodnoty s možnou hodnotou, kterou lze hodnotu hodnotit .</span><span class="sxs-lookup"><span data-stu-id="752da-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="752da-137">Zdvižené operátory</span><span class="sxs-lookup"><span data-stu-id="752da-137">Lifted operators</span></span>

<span data-ttu-id="752da-138">Předdefinované unární a binární [operátory](../operators/index.md) nebo všechny přetížené `T` operátory, které jsou podporovány `T?`typem hodnoty jsou také podporovány odpovídající typ hodnoty s možnou hodnotou null .</span><span class="sxs-lookup"><span data-stu-id="752da-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="752da-139">Tito provozovatelé, také známí jako `null` *zdvižené obsluhy*, vyrábějí, pokud se jedná `null`o jeden nebo oba operandy ; v opačném případě operátor používá obsažené hodnoty svých operandů k výpočtu výsledku.</span><span class="sxs-lookup"><span data-stu-id="752da-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="752da-140">Například:</span><span class="sxs-lookup"><span data-stu-id="752da-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="752da-141">Pro `bool?` typ předdefinované `&` a `|` operátory nedodržují pravidla popsaná v této části: výsledek vyhodnocení operátoru může být non-null i v případě, že jeden z operandů je `null`.</span><span class="sxs-lookup"><span data-stu-id="752da-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="752da-142">Další informace naleznete v části [Nullable Boolean logické operátory](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) článku [logické operátory logické.](../operators/boolean-logical-operators.md)</span><span class="sxs-lookup"><span data-stu-id="752da-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="752da-143">Pro [porovnávací operátory](../operators/comparison-operators.md) `<` `>`, `<=`, , a `null` `false` `>=`, pokud je jeden nebo oba operandy , je výsledkem ; jinak jsou porovnány obsažené hodnoty operandů.</span><span class="sxs-lookup"><span data-stu-id="752da-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="752da-144">Nepředpokládejte, že vzhledem k `<=`tomu, `false`že konkrétní`>`porovnání `true`(například ) vrátí , opačné porovnání ( ) vrátí .</span><span class="sxs-lookup"><span data-stu-id="752da-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="752da-145">Následující příklad ukazuje, že 10 je</span><span class="sxs-lookup"><span data-stu-id="752da-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="752da-146">větší nebo rovno`null`</span><span class="sxs-lookup"><span data-stu-id="752da-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="752da-147">ani méně než`null`</span><span class="sxs-lookup"><span data-stu-id="752da-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="752da-148">Pro [operátor](../operators/equality-operators.md#equality-operator-) `==`rovnosti , pokud jsou `null`oba operandy , je `true`výsledkem `null`výsledek , `false`pokud je pouze jeden z operandů , výsledek je ; jinak jsou porovnány obsažené hodnoty operandů.</span><span class="sxs-lookup"><span data-stu-id="752da-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="752da-149">Pro [operátor](../operators/equality-operators.md#inequality-operator-) `!=`nerovnosti , pokud jsou `null`oba operandy , je `false`výsledkem `null`výsledek , `true`pokud je pouze jeden z operandů , výsledek je ; jinak jsou porovnány obsažené hodnoty operandů.</span><span class="sxs-lookup"><span data-stu-id="752da-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="752da-150">Pokud existuje [uživatelem definovaný převod](../operators/user-defined-conversion-operators.md) mezi dvěma typy hodnot, lze použít stejný převod také mezi odpovídajícími typy hodnot s možnou hodnotou, kterou lze použít.</span><span class="sxs-lookup"><span data-stu-id="752da-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="752da-151">Box a rozbalení</span><span class="sxs-lookup"><span data-stu-id="752da-151">Boxing and unboxing</span></span>

<span data-ttu-id="752da-152">Instance typu `T?` hodnoty s možnou hodnotou s hodnotou s možnou hodnotou null je [zabalena](../../programming-guide/types/boxing-and-unboxing.md) takto:</span><span class="sxs-lookup"><span data-stu-id="752da-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="752da-153">Pokud <xref:System.Nullable%601.HasValue%2A> `false`vrátí , je vytvořen odkaz null.</span><span class="sxs-lookup"><span data-stu-id="752da-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="752da-154">Pokud <xref:System.Nullable%601.HasValue%2A> `true`vrátí , odpovídající hodnota základního typu `T` hodnoty je <xref:System.Nullable%601>zabalena, nikoli instance .</span><span class="sxs-lookup"><span data-stu-id="752da-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="752da-155">Zabalenou hodnotu typu `T` hodnoty můžete rozbalit na odpovídající `T?`hodnotu s hodnotou s možnou hodnotou , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="752da-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="752da-156">Jak identifikovat typ hodnoty s možnou hodnotou s možnou hodnotou</span><span class="sxs-lookup"><span data-stu-id="752da-156">How to identify a nullable value type</span></span>

<span data-ttu-id="752da-157">Následující příklad ukazuje, jak <xref:System.Type?displayProperty=nameWithType> zjistit, zda instance představuje početný typ <xref:System.Nullable%601?displayProperty=nameWithType> hodnoty s možnou `T`hodnotou s možnou hodnotou, to znamená typ s parametrem zadaného typu :</span><span class="sxs-lookup"><span data-stu-id="752da-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="752da-158">Jak ukazuje příklad, pomocí [operátoru typeof](../operators/type-testing-and-cast.md#typeof-operator) vytvořte instanci. <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="752da-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="752da-159">Pokud chcete určit, zda je instance typu hodnoty s možnou <xref:System.Object.GetType%2A?displayProperty=nameWithType> hodnotou, <xref:System.Type> kterou lze použít, nepoužívejte metodu k získání instance, která má být testována s předchozím kódem.</span><span class="sxs-lookup"><span data-stu-id="752da-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="752da-160">Při volání <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody na instanci typu hodnoty s možnou <xref:System.Object>hodnotou, kterou lze hodnotit, je instance [zabalena](#boxing-and-unboxing) do .</span><span class="sxs-lookup"><span data-stu-id="752da-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="752da-161">Jako zabalení non-null instance typu hodnoty s hodnotou, kterou lze hodnotu <xref:System.Type> null je ekvivalentní zabalení hodnoty základního typu, vrátí instanci, <xref:System.Object.GetType%2A> která představuje základní typ typu hodnoty s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="752da-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="752da-162">Také nepoužívejte [is](../operators/type-testing-and-cast.md#is-operator) operátor k určení, zda je instance typu hodnoty s možnou hodnotou s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="752da-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="752da-163">Jak ukazuje následující příklad, nelze rozlišit typy instance typu hodnoty s `is` možnou hodnotou s hodnotou s hodnotou s možnou hodnotou a její základní instanci typu s operátorem:</span><span class="sxs-lookup"><span data-stu-id="752da-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="752da-164">Kód uvedený v následujícím příkladu můžete použít k určení, zda je instance typu hodnoty s možnou hodnotou s hodnotou s možnou hodnotou:</span><span class="sxs-lookup"><span data-stu-id="752da-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="752da-165">Metody popsané v této části nejsou použitelné v případě [typů odkazů s možnou hodnotou null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="752da-165">The methods described in this section are not applicable in the case of [nullable reference types](../../nullable-references.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="752da-166">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="752da-166">C# language specification</span></span>

<span data-ttu-id="752da-167">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="752da-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="752da-168">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="752da-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="752da-169">Zdvižené operátory</span><span class="sxs-lookup"><span data-stu-id="752da-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="752da-170">Implicitní převody s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="752da-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="752da-171">Explicitní převody s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="752da-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="752da-172">Operátory zrušených konverzí</span><span class="sxs-lookup"><span data-stu-id="752da-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="752da-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="752da-173">See also</span></span>

- [<span data-ttu-id="752da-174">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="752da-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="752da-175">Co přesně znamená "zvednutý"?</span><span class="sxs-lookup"><span data-stu-id="752da-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="752da-176">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="752da-176">Nullable reference types</span></span>](../../nullable-references.md)
