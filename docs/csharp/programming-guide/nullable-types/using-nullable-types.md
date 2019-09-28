---
title: Použití typů hodnot s možnou hodnotou null – C# Průvodce programováním
ms.custom: seodec18
description: Naučte se pracovat s C# typy hodnot s možnou hodnotou null.
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396172"
---
# <a name="using-nullable-value-types-c-programming-guide"></a><span data-ttu-id="5563d-103">Použití typů hodnot s možnou hodnotou null (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="5563d-103">Using nullable value types (C# Programming Guide)</span></span>

<span data-ttu-id="5563d-104">Typy s možnou hodnotou null jsou typy, které představují všechny hodnoty základního typu hodnoty `T` a další hodnotu [null](../../language-reference/keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="5563d-104">Nullable value types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="5563d-105">Další informace naleznete v tématu [typy hodnot s možnou hodnotou null](index.md) .</span><span class="sxs-lookup"><span data-stu-id="5563d-105">For more information, see the [Nullable value types](index.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="5563d-106">C#8,0 zavádí funkci typů odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5563d-106">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="5563d-107">Další informace naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="5563d-107">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="5563d-108">Typy s C# možnou hodnotou null jsou k dispozici od 2.</span><span class="sxs-lookup"><span data-stu-id="5563d-108">The nullable value types are available starting with C# 2.</span></span>

<span data-ttu-id="5563d-109">Můžete odkazovat na typ hodnoty s možnou hodnotou null v některém z následujících formulářů, které lze měnit: `Nullable<T>` nebo `T?`.</span><span class="sxs-lookup"><span data-stu-id="5563d-109">You can refer to a nullable value type in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="5563d-110">`T` musí být typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5563d-110">`T` must be a value type.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="5563d-111">Deklarace a přiřazení</span><span class="sxs-lookup"><span data-stu-id="5563d-111">Declaration and assignment</span></span>

<span data-ttu-id="5563d-112">Typ hodnoty lze implicitně převést na odpovídající typ hodnoty s možnou hodnotou null. přiřadíte hodnotu typu s možnou hodnotou null, jako byste to měli pro svůj základní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5563d-112">As a value type can be implicitly converted to the corresponding nullable value type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="5563d-113">Můžete také přiřadit hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="5563d-113">You also can assign the `null` value.</span></span> <span data-ttu-id="5563d-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5563d-114">For example:</span></span>

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="5563d-115">Prověření hodnoty typu s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="5563d-115">Examination of a nullable type value</span></span>

<span data-ttu-id="5563d-116">Pomocí následujících vlastností ReadOnly prověřte instanci typu hodnoty s možnou hodnotou null a načtěte hodnotu základního typu:</span><span class="sxs-lookup"><span data-stu-id="5563d-116">Use the following readonly properties to examine an instance of a nullable value type for null and retrieve a value of an underlying type:</span></span>

- <span data-ttu-id="5563d-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> označuje, zda instance typu s možnou hodnotou null má hodnotu svého nadřízeného typu.</span><span class="sxs-lookup"><span data-stu-id="5563d-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>

- <span data-ttu-id="5563d-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Získá hodnotu základního typu, pokud je <xref:System.Nullable%601.HasValue%2A> `true`.</span><span class="sxs-lookup"><span data-stu-id="5563d-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="5563d-119">Pokud je <xref:System.Nullable%601.HasValue%2A> `false`, vlastnost <xref:System.Nullable%601.Value%2A> vyvolá <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="5563d-119">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="5563d-120">Kód v následujícím příkladu používá vlastnost `HasValue` k otestování, zda proměnná obsahuje hodnotu před jejich zobrazením:</span><span class="sxs-lookup"><span data-stu-id="5563d-120">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

<span data-ttu-id="5563d-121">Můžete také porovnat proměnnou typu hodnoty s možnou hodnotou null s `null` namísto použití vlastnosti `HasValue`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="5563d-121">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="5563d-122">Počínaje C# 7,0 můžete použít [porovnávání vzorů](../../pattern-matching.md) pro kontrolu a získání hodnoty typu s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="5563d-122">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable value type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="5563d-123">Převod z typu hodnoty s možnou hodnotou null na nadřízený typ</span><span class="sxs-lookup"><span data-stu-id="5563d-123">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="5563d-124">Pokud potřebujete přiřadit hodnotu typu hodnoty s možnou hodnotou null k typu, který neumožňuje hodnotu null, použijte [operátor sloučení s hodnotou null `??`](../../language-reference/operators/null-coalescing-operator.md) k určení hodnoty, která má být přiřazena, pokud hodnota typu s možnou hodnotou null má hodnotu null (můžete také použít metodu <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> k tomu). :</span><span class="sxs-lookup"><span data-stu-id="5563d-124">If you need to assign a value of a nullable value type to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a value of a nullable value type is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="5563d-125">Použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, pokud je hodnota, která se má použít, pokud je hodnota typu s možnou hodnotou null `null` výchozí hodnotou základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5563d-125">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a value of a nullable value type is `null` should be the default value of the underlying value type.</span></span>

<span data-ttu-id="5563d-126">Typ hodnoty s možnou hodnotou null můžete explicitně přetypovat na typ, který není null.</span><span class="sxs-lookup"><span data-stu-id="5563d-126">You can explicitly cast a nullable value type to a non-nullable type.</span></span> <span data-ttu-id="5563d-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5563d-127">For example:</span></span>

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="5563d-128">V době běhu, pokud je hodnota typu s možnou hodnotou null `null`, explicitní přetypování vyvolá <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="5563d-128">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="5563d-129">Typ hodnoty, která není null, je implicitně převeden na odpovídající typ s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5563d-129">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>

## <a name="operators"></a><span data-ttu-id="5563d-130">Operátory</span><span class="sxs-lookup"><span data-stu-id="5563d-130">Operators</span></span>

<span data-ttu-id="5563d-131">Předdefinované unární a binární operátory a jakékoli uživatelsky definované operátory, které existují pro typy hodnot, mohou být použity také odpovídajícími typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5563d-131">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by corresponding nullable types.</span></span> <span data-ttu-id="5563d-132">Tyto operátory vytváří `null`, pokud jsou jeden nebo oba operandy `null`; v opačném případě operátor používá k výpočtu výsledku obsažené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5563d-132">These operators produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="5563d-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5563d-133">For example:</span></span>

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="5563d-134">U typu `bool?` se předdefinované operátory `&` a `|` nepoužijí pravidla popsaná v této části: výsledek vyhodnocení operátoru nemůže být null, i když je jeden z operandů `null`.</span><span class="sxs-lookup"><span data-stu-id="5563d-134">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="5563d-135">Další informace naleznete v části s [možnou hodnotou null logických operátorů](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../../language-reference/operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="5563d-135">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="5563d-136">V případě relačních operátorů (`<`, `>`, `<=`, `>=`) platí, že pokud je jeden nebo oba operandy `null`, výsledek je `false`.</span><span class="sxs-lookup"><span data-stu-id="5563d-136">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are `null`, the result is `false`.</span></span> <span data-ttu-id="5563d-137">Nepředpokládáme, že vzhledem k tomu, že konkrétní porovnání (například `<=`) vrátí `false`, opačné porovnání (`>`) vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="5563d-137">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="5563d-138">Následující příklad ukazuje, že 10</span><span class="sxs-lookup"><span data-stu-id="5563d-138">The following example shows that 10 is</span></span>

- <span data-ttu-id="5563d-139">ani větší než nebo rovno `null`,</span><span class="sxs-lookup"><span data-stu-id="5563d-139">neither greater than or equal to `null`,</span></span>
- <span data-ttu-id="5563d-140">ani menší než `null`.</span><span class="sxs-lookup"><span data-stu-id="5563d-140">nor less than `null`.</span></span>

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

<span data-ttu-id="5563d-141">Výše uvedený příklad také ukazuje, že porovnání rovnosti dvou typů hodnot s možnou hodnotou null, které jsou obě hodnoty null, jsou vyhodnoceny jako `true`.</span><span class="sxs-lookup"><span data-stu-id="5563d-141">The above example also shows that an equality comparison of two nullable value types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="5563d-142">Další informace naleznete v části předané [operátory](~/_csharplang/spec/expressions.md#lifted-operators) v tématu [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5563d-142">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="5563d-143">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="5563d-143">Boxing and unboxing</span></span>

<span data-ttu-id="5563d-144">Typ hodnoty s možnou hodnotou null je [zabalený](../types/boxing-and-unboxing.md) podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="5563d-144">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="5563d-145">Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `false`, bude vytvořen odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="5563d-145">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="5563d-146">Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`, hodnota základního typu hodnoty `T` je zabalena, nikoli instance <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="5563d-146">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="5563d-147">Můžete unbox typ zabalené hodnoty na odpovídající typ s povolenou hodnotou null, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="5563d-147">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="5563d-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5563d-148">See also</span></span>

- [<span data-ttu-id="5563d-149">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="5563d-149">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="5563d-150">Co přesně znamená "vyvoláno"?</span><span class="sxs-lookup"><span data-stu-id="5563d-150">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
