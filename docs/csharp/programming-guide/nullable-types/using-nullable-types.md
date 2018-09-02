---
title: Použití typů s povolenou hodnotou Null (C# Programming Guide)
description: Zjistěte, jak pracovat s typy s možnou hodnotou Null C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 600a18cc4dc9d3eda5577336f209c5814a7edb88
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417872"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="8c463-103">Použití typů s povolenou hodnotou Null (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="8c463-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="8c463-104">Typy s možnou hodnotou Null jsou typy, které představují všechny hodnoty základního typu hodnoty `T`a další [null](../../language-reference/keywords/null.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8c463-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="8c463-105">Další informace najdete v tématu [typy připouštějící hodnotu Null](index.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="8c463-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="8c463-106">Můžete odkazovat na typ připouštějící hodnotu Null v některém z následujících forem: `Nullable<T>` nebo `T?`.</span><span class="sxs-lookup"><span data-stu-id="8c463-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="8c463-107">Tyto dvě formy jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="8c463-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="8c463-108">Deklaraci a přiřazení</span><span class="sxs-lookup"><span data-stu-id="8c463-108">Declaration and assignment</span></span>

<span data-ttu-id="8c463-109">Jako typ hodnoty lze implicitně převést na odpovídající typ s možnou hodnotou Null, přiřadíte hodnotu na typ připouštějící hodnotu null jako jeho základní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8c463-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="8c463-110">Také můžete přiřadit `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8c463-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="8c463-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8c463-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="8c463-112">Zkoumání hodnotu typu s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8c463-112">Examination of a nullable type value</span></span>

<span data-ttu-id="8c463-113">Použijte následující vlastnosti jen pro čtení sloužící ke zkoumání instanci typu s možnou hodnotou Null pro hodnotu null a načíst hodnotu podkladového typu:</span><span class="sxs-lookup"><span data-stu-id="8c463-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="8c463-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Označuje, zda obsahuje instanci typu s možnou hodnotou Null hodnotu jeho nadřízeného typu.</span><span class="sxs-lookup"><span data-stu-id="8c463-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="8c463-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Získá hodnotu základního typu, pokud <xref:System.Nullable%601.HasValue%2A> je `true`.</span><span class="sxs-lookup"><span data-stu-id="8c463-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="8c463-116">Pokud <xref:System.Nullable%601.HasValue%2A> je `false`, <xref:System.Nullable%601.Value%2A> vlastnost vyvolá <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="8c463-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="8c463-117">Kód v následujícím příkladu používá `HasValue` vlastnost k ověření, zda proměnná obsahuje hodnotu před zobrazením jej:</span><span class="sxs-lookup"><span data-stu-id="8c463-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="8c463-118">Typ s možnou hodnotou Null proměnné se taky můžete porovnat `null` namísto použití `HasValue` vlastnosti, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8c463-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="8c463-119">Od verze C# 7.0, můžete použít [porovnávání vzorů](../../pattern-matching.md) jak prozkoumat a získat hodnotu typu s možnou hodnotou NULL:</span><span class="sxs-lookup"><span data-stu-id="8c463-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="8c463-120">Převod z typu s možnou hodnotou Null na základní typ.</span><span class="sxs-lookup"><span data-stu-id="8c463-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="8c463-121">Pokud je potřeba přiřadit typ připouštějící hodnotu Null hodnotu typu Null, použijte [operátoru nulového sjednocení `??` ](../../language-reference/operators/null-coalescing-operator.md) zadat hodnotu pro přiřazení, pokud je typ připouštějící hodnotu Null hodnota null (můžete také použít <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> metodu který):</span><span class="sxs-lookup"><span data-stu-id="8c463-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="8c463-122">Použití <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metody, pokud hodnota má být použit při hodnota s možnou hodnotou Null typu má hodnotu null musí být výchozí hodnota základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8c463-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="8c463-123">Můžete explicitně přetypován typ připouštějící hodnotu NULL do typu Null.</span><span class="sxs-lookup"><span data-stu-id="8c463-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="8c463-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8c463-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="8c463-125">V době běhu, pokud hodnota s možnou hodnotou Null typu má hodnotu null, vyvolá explicitní přetypování <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="8c463-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="8c463-126">Typ hodnotu null je implicitně převést na odpovídající typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="8c463-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="8c463-127">Operátory</span><span class="sxs-lookup"><span data-stu-id="8c463-127">Operators</span></span>

<span data-ttu-id="8c463-128">Předdefinované jednočlenné a binární operátory a operátory definované uživatelem, které existují pro typy hodnot může také sloužit typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="8c463-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="8c463-129">Tyto operátory vytvořit hodnotu null, pokud jeden nebo oba operandy jsou null. v opačném případě operátor, který se používá omezením hodnoty k výpočtu výsledku.</span><span class="sxs-lookup"><span data-stu-id="8c463-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="8c463-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8c463-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]
  
<span data-ttu-id="8c463-131">Pro relační operátory (`<`, `>`, `<=`, `>=`), pokud jeden nebo oba operandy hodnotu null, je výsledkem `false`.</span><span class="sxs-lookup"><span data-stu-id="8c463-131">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="8c463-132">Nepředpokládejte, protože konkrétní porovnání (například `<=`) vrátí `false`, opačný porovnání (`>`) vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="8c463-132">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="8c463-133">Následující příklad ukazuje, že je 10</span><span class="sxs-lookup"><span data-stu-id="8c463-133">The following example shows that 10 is</span></span>

- <span data-ttu-id="8c463-134">ani větší než nebo rovna hodnotě null,</span><span class="sxs-lookup"><span data-stu-id="8c463-134">neither greater than or equal to null,</span></span>
- <span data-ttu-id="8c463-135">ani nižší než null.</span><span class="sxs-lookup"><span data-stu-id="8c463-135">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="8c463-136">Výše uvedený příklad také ukazuje, že porovnání rovnosti dvou typů s povolenou hodnotou Null, které jsou obě hodnotu null je vyhodnocen jako `true`.</span><span class="sxs-lookup"><span data-stu-id="8c463-136">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="8c463-137">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="8c463-137">Boxing and unboxing</span></span>

<span data-ttu-id="8c463-138">Typ s možnou hodnotou null je [boxed](../types/boxing-and-unboxing.md) následujícími pravidly:</span><span class="sxs-lookup"><span data-stu-id="8c463-138">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="8c463-139">Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `false`, je vytvořen nulový odkaz.</span><span class="sxs-lookup"><span data-stu-id="8c463-139">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="8c463-140">Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`, hodnota základního typu hodnoty `T` je zabalená, není instancí <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="8c463-140">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="8c463-141">Hodnotový typ, který má odpovídající typ s možnou hodnotou Null, může unbox jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8c463-141">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a><span data-ttu-id="8c463-142">Logická hodnota? Typ</span><span class="sxs-lookup"><span data-stu-id="8c463-142">The bool? type</span></span>

<span data-ttu-id="8c463-143">`bool?` Typ připouštějící hodnotu Null, může obsahovat tři různé hodnoty: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) a [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="8c463-143">The `bool?` nullable type can contain three different values: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) and [null](../../language-reference/keywords/null.md).</span></span> <span data-ttu-id="8c463-144">`bool?` Typ je jako logická typ proměnné, který se používá v SQL.</span><span class="sxs-lookup"><span data-stu-id="8c463-144">The `bool?` type is like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="8c463-145">Chcete-li zajistit výsledky vytvořené metodou `&` a `|` operátory jsou konzistentní s typem Boolean s hodnotou tři v SQL, jsou k dispozici následující předdefinované operátory:</span><span class="sxs-lookup"><span data-stu-id="8c463-145">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
<span data-ttu-id="8c463-146">Sémantika těchto operátorů je definována v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="8c463-146">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="8c463-147">x</span><span class="sxs-lookup"><span data-stu-id="8c463-147">x</span></span>|<span data-ttu-id="8c463-148">y</span><span class="sxs-lookup"><span data-stu-id="8c463-148">y</span></span>|<span data-ttu-id="8c463-149">x & y</span><span class="sxs-lookup"><span data-stu-id="8c463-149">x&y</span></span>|<span data-ttu-id="8c463-150">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="8c463-150">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="8c463-151">true</span><span class="sxs-lookup"><span data-stu-id="8c463-151">true</span></span>|<span data-ttu-id="8c463-152">true</span><span class="sxs-lookup"><span data-stu-id="8c463-152">true</span></span>|<span data-ttu-id="8c463-153">true</span><span class="sxs-lookup"><span data-stu-id="8c463-153">true</span></span>|<span data-ttu-id="8c463-154">true</span><span class="sxs-lookup"><span data-stu-id="8c463-154">true</span></span>|  
|<span data-ttu-id="8c463-155">true</span><span class="sxs-lookup"><span data-stu-id="8c463-155">true</span></span>|<span data-ttu-id="8c463-156">false</span><span class="sxs-lookup"><span data-stu-id="8c463-156">false</span></span>|<span data-ttu-id="8c463-157">false</span><span class="sxs-lookup"><span data-stu-id="8c463-157">false</span></span>|<span data-ttu-id="8c463-158">true</span><span class="sxs-lookup"><span data-stu-id="8c463-158">true</span></span>|  
|<span data-ttu-id="8c463-159">true</span><span class="sxs-lookup"><span data-stu-id="8c463-159">true</span></span>|<span data-ttu-id="8c463-160">null</span><span class="sxs-lookup"><span data-stu-id="8c463-160">null</span></span>|<span data-ttu-id="8c463-161">null</span><span class="sxs-lookup"><span data-stu-id="8c463-161">null</span></span>|<span data-ttu-id="8c463-162">true</span><span class="sxs-lookup"><span data-stu-id="8c463-162">true</span></span>|  
|<span data-ttu-id="8c463-163">false</span><span class="sxs-lookup"><span data-stu-id="8c463-163">false</span></span>|<span data-ttu-id="8c463-164">true</span><span class="sxs-lookup"><span data-stu-id="8c463-164">true</span></span>|<span data-ttu-id="8c463-165">false</span><span class="sxs-lookup"><span data-stu-id="8c463-165">false</span></span>|<span data-ttu-id="8c463-166">true</span><span class="sxs-lookup"><span data-stu-id="8c463-166">true</span></span>|  
|<span data-ttu-id="8c463-167">false</span><span class="sxs-lookup"><span data-stu-id="8c463-167">false</span></span>|<span data-ttu-id="8c463-168">false</span><span class="sxs-lookup"><span data-stu-id="8c463-168">false</span></span>|<span data-ttu-id="8c463-169">false</span><span class="sxs-lookup"><span data-stu-id="8c463-169">false</span></span>|<span data-ttu-id="8c463-170">false</span><span class="sxs-lookup"><span data-stu-id="8c463-170">false</span></span>|  
|<span data-ttu-id="8c463-171">false</span><span class="sxs-lookup"><span data-stu-id="8c463-171">false</span></span>|<span data-ttu-id="8c463-172">null</span><span class="sxs-lookup"><span data-stu-id="8c463-172">null</span></span>|<span data-ttu-id="8c463-173">false</span><span class="sxs-lookup"><span data-stu-id="8c463-173">false</span></span>|<span data-ttu-id="8c463-174">null</span><span class="sxs-lookup"><span data-stu-id="8c463-174">null</span></span>|  
|<span data-ttu-id="8c463-175">null</span><span class="sxs-lookup"><span data-stu-id="8c463-175">null</span></span>|<span data-ttu-id="8c463-176">true</span><span class="sxs-lookup"><span data-stu-id="8c463-176">true</span></span>|<span data-ttu-id="8c463-177">null</span><span class="sxs-lookup"><span data-stu-id="8c463-177">null</span></span>|<span data-ttu-id="8c463-178">true</span><span class="sxs-lookup"><span data-stu-id="8c463-178">true</span></span>|  
|<span data-ttu-id="8c463-179">null</span><span class="sxs-lookup"><span data-stu-id="8c463-179">null</span></span>|<span data-ttu-id="8c463-180">false</span><span class="sxs-lookup"><span data-stu-id="8c463-180">false</span></span>|<span data-ttu-id="8c463-181">false</span><span class="sxs-lookup"><span data-stu-id="8c463-181">false</span></span>|<span data-ttu-id="8c463-182">null</span><span class="sxs-lookup"><span data-stu-id="8c463-182">null</span></span>|  
|<span data-ttu-id="8c463-183">null</span><span class="sxs-lookup"><span data-stu-id="8c463-183">null</span></span>|<span data-ttu-id="8c463-184">null</span><span class="sxs-lookup"><span data-stu-id="8c463-184">null</span></span>|<span data-ttu-id="8c463-185">null</span><span class="sxs-lookup"><span data-stu-id="8c463-185">null</span></span>|<span data-ttu-id="8c463-186">null</span><span class="sxs-lookup"><span data-stu-id="8c463-186">null</span></span>|  

<span data-ttu-id="8c463-187">Všimněte si, že tyto dva operátory neodpovídají pravidel popsaných v [operátory](#operators) oddílu: výsledek vyhodnocení operátor může být jiná než null, i v případě, že jeden z operandů má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8c463-187">Note that these two operators don't follow the rules described in the [Operators](#operators) section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8c463-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c463-188">See also</span></span>

 [<span data-ttu-id="8c463-189">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8c463-189">Nullable types</span></span>](index.md)  
 [<span data-ttu-id="8c463-190">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8c463-190">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="8c463-191">Co přesně pojem "zrušeno" znamená?</span><span class="sxs-lookup"><span data-stu-id="8c463-191">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)  
