---
title: Použití typů s možnou hodnotou null – C# Průvodce programováním
ms.custom: seodec18
description: Naučte se pracovat s C# typy s možnou hodnotou null.
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588830"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="ee95f-103">Použití typů s možnou hodnotou null (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ee95f-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="ee95f-104">Typy s možnou hodnotou null jsou typy, které představují všechny hodnoty základního `T`typu hodnoty, a další hodnotu [null](../../language-reference/keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="ee95f-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="ee95f-105">Další informace najdete v tématu [typy s možnou hodnotou null](index.md) .</span><span class="sxs-lookup"><span data-stu-id="ee95f-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="ee95f-106">Na typ s možnou hodnotou null můžete odkazovat v některé z následujících forem `Nullable<T>` : `T?`nebo.</span><span class="sxs-lookup"><span data-stu-id="ee95f-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="ee95f-107">Tyto dva formuláře jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="ee95f-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="ee95f-108">Deklarace a přiřazení</span><span class="sxs-lookup"><span data-stu-id="ee95f-108">Declaration and assignment</span></span>

<span data-ttu-id="ee95f-109">Typ hodnoty lze implicitně převést na odpovídající typ s povolenou hodnotou null. přiřadíte hodnotu typu s možnou hodnotou null, jako byste to měli pro svůj základní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee95f-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="ee95f-110">Můžete také přiřadit `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee95f-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="ee95f-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ee95f-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="ee95f-112">Prověření hodnoty typu s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="ee95f-112">Examination of a nullable type value</span></span>

<span data-ttu-id="ee95f-113">Pomocí následujících vlastností ReadOnly prověřte instanci typu s možnou hodnotou null a načtěte hodnotu základního typu:</span><span class="sxs-lookup"><span data-stu-id="ee95f-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="ee95f-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>Určuje, zda instance typu s možnou hodnotou null má hodnotu svého nadřízeného typu.</span><span class="sxs-lookup"><span data-stu-id="ee95f-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="ee95f-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>Získá hodnotu základního typu, pokud <xref:System.Nullable%601.HasValue%2A> je. `true`</span><span class="sxs-lookup"><span data-stu-id="ee95f-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="ee95f-116">Pokud <xref:System.Nullable%601.HasValue%2A> je `false` ,<xref:System.Nullable%601.Value%2A>vlastnost vyvolá .<xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="ee95f-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="ee95f-117">Kód v následujícím příkladu používá `HasValue` vlastnost k otestování, zda proměnná obsahuje hodnotu před jejich zobrazením:</span><span class="sxs-lookup"><span data-stu-id="ee95f-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="ee95f-118">Můžete také porovnat proměnnou typu s možnou hodnotou `null` null s namísto `HasValue` použití vlastnosti, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ee95f-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="ee95f-119">Počínaje C# 7,0 můžete použít [porovnávání vzorů](../../pattern-matching.md) pro kontrolu a získání hodnoty typu s možnou hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="ee95f-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="ee95f-120">Převod z typu s možnou hodnotou null na nadřízený typ</span><span class="sxs-lookup"><span data-stu-id="ee95f-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="ee95f-121">Pokud potřebujete přiřadit hodnotu typu s možnou hodnotou null k typu bez hodnoty null, použijte [operátor `??` ](../../language-reference/operators/null-coalescing-operator.md) pro sjednocení null k určení hodnoty, která má být přiřazena, pokud je hodnota typu s povolenou hodnotou null nulová ( <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> můžete také použít metodu k tomu):</span><span class="sxs-lookup"><span data-stu-id="ee95f-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="ee95f-122">Použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , pokud hodnota, která se má použít, když má hodnota typu Nullable hodnotu null, by měla být výchozí hodnotou základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee95f-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="ee95f-123">Typ s možnou hodnotou null můžete explicitně přetypovat na typ, který není null.</span><span class="sxs-lookup"><span data-stu-id="ee95f-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="ee95f-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ee95f-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="ee95f-125">V době běhu, pokud je hodnota typu s možnou hodnotou null null, vyvolá <xref:System.InvalidOperationException>explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="ee95f-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="ee95f-126">Typ hodnoty, která není null, je implicitně převeden na odpovídající typ s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ee95f-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="ee95f-127">Operátory</span><span class="sxs-lookup"><span data-stu-id="ee95f-127">Operators</span></span>

<span data-ttu-id="ee95f-128">Předdefinované unární a binární operátory a jakékoli uživatelsky definované operátory, které existují pro typy hodnot, mohou být použity i pro typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ee95f-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="ee95f-129">Tyto operátory vytvoří hodnotu null, pokud má jeden nebo oba operandy hodnotu null. v opačném případě operátor používá k výpočtu výsledku obsažené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee95f-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="ee95f-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ee95f-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="ee95f-131">Pro typ se předdefinované `&` a `|` operátory nevztahují na pravidla popsaná v této části: výsledek vyhodnocení operátoru nemůže mít hodnotu null, i když jeden z operandů je null. `bool?`</span><span class="sxs-lookup"><span data-stu-id="ee95f-131">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span> <span data-ttu-id="ee95f-132">Další informace naleznete v části s [možnou hodnotou null](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) logických operátorů v článku [Boolean Logical Operators](../../language-reference/operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="ee95f-132">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="ee95f-133">V případě relačních operátorů `>`( `<=``<`, `>=`,,), pokud je jeden nebo oba operandy NULL, je `false`výsledek.</span><span class="sxs-lookup"><span data-stu-id="ee95f-133">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="ee95f-134">Nepředpokládáme, že vzhledem k tomu, že konkrétní porovnání `<=`(například `false`) vrátí, vrátí `true`opačné porovnání (`>`).</span><span class="sxs-lookup"><span data-stu-id="ee95f-134">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="ee95f-135">Následující příklad ukazuje, že 10</span><span class="sxs-lookup"><span data-stu-id="ee95f-135">The following example shows that 10 is</span></span>

- <span data-ttu-id="ee95f-136">ani větší nebo rovno hodnotě null,</span><span class="sxs-lookup"><span data-stu-id="ee95f-136">neither greater than or equal to null,</span></span>
- <span data-ttu-id="ee95f-137">ani menší než null.</span><span class="sxs-lookup"><span data-stu-id="ee95f-137">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="ee95f-138">Výše uvedený příklad také ukazuje, že porovnání rovnosti dvou typů s možnou hodnotou null, na `true`které jsou obě hodnoty null, jsou vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="ee95f-138">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="ee95f-139">Další informace naleznete v části předané [operátory](~/_csharplang/spec/expressions.md#lifted-operators) v tématu [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ee95f-139">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="ee95f-140">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="ee95f-140">Boxing and unboxing</span></span>

<span data-ttu-id="ee95f-141">Typ hodnoty s možnou [](../types/boxing-and-unboxing.md) hodnotou null je zabalený podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="ee95f-141">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="ee95f-142">Pokud <xref:System.Nullable%601.HasValue%2A> se `false`vrátí, je vytvořen odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ee95f-142">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="ee95f-143">Pokud <xref:System.Nullable%601.HasValue%2A> se `true`vrátí, hodnota základního typu `T` hodnoty je zabalená, nikoli instance <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="ee95f-143">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="ee95f-144">Můžete unbox typ zabalené hodnoty na odpovídající typ s povolenou hodnotou null, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ee95f-144">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="ee95f-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee95f-145">See also</span></span>

- [<span data-ttu-id="ee95f-146">Typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="ee95f-146">Nullable types</span></span>](index.md)
- [<span data-ttu-id="ee95f-147">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ee95f-147">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ee95f-148">Co přesně znamená "vyvoláno"?</span><span class="sxs-lookup"><span data-stu-id="ee95f-148">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
