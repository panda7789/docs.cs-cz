---
title: Operátory přístupu členů a výrazy – odkaz jazyka C#
description: Další informace o operátory Jazyka C#, které můžete použít pro přístup k členům typu.
ms.date: 03/31/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: 90066b1e9c219f66fc0c76423679e81aa3fa6770
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81120986"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="a0cbc-103">Operátory přístupu k členům a výrazy (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="a0cbc-104">Při přístupu k členu typu můžete použít následující operátory a výrazy:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="a0cbc-105">(členský přístup) : přístup k členovi oboru názvů nebo typu [ `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="a0cbc-106">[(element pole nebo přístup k indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="a0cbc-107">[a `?[]` (operátory s nulovým podmíněným podmínkou): provádět operaci přístupu k členu nebo prvku pouze v případě, že operand není `?.` ](#null-conditional-operators--and-)null</span><span class="sxs-lookup"><span data-stu-id="a0cbc-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="a0cbc-108">(vyvolání) : volání přístupné metody nebo vyvolání delegáta [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="a0cbc-109">(index od konce): označuje, že pozice prvku je od konce sekvence [ `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="a0cbc-110">(rozsah) : určení rozsahu indexů, které můžete použít k získání rozsahu sekvenčních prvků [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="a0cbc-111">Výraz přístupu člena .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-111">Member access expression .</span></span>

<span data-ttu-id="a0cbc-112">`.` Token se používá pro přístup k členu oboru názvů nebo typu, jak ukazují následující příklady:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="a0cbc-113">Slouží `.` k přístupu k vnořené oboru názvů v oboru názvů, jak ukazuje následující příklad [ `using` směrnice:](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="a0cbc-114">Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="a0cbc-115">Použití [ `using` směrnice,](../keywords/using-directive.md) aby bylo použití kvalifikovaných názvů volitelné.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="a0cbc-116">Slouží `.` k přístupu k [členům typu](../../programming-guide/classes-and-structs/index.md#members), statickým a nestatickým, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="a0cbc-117">Můžete také `.` použít pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="a0cbc-118">Operátor indexeru []</span><span class="sxs-lookup"><span data-stu-id="a0cbc-118">Indexer operator []</span></span>

<span data-ttu-id="a0cbc-119">Hranaté `[]`závorky , , se obvykle používají pro přístup k polím, indexeru nebo elementu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="a0cbc-120">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="a0cbc-120">Array access</span></span>

<span data-ttu-id="a0cbc-121">Následující příklad ukazuje, jak získat přístup k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="a0cbc-122">Pokud index pole je mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="a0cbc-123">Jak ukazuje předchozí příklad, čtvercové závorky použijete také při deklarování typu pole nebo instance instance pole.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="a0cbc-124">Další informace o polích naleznete v [tématu Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="a0cbc-125">Přístup k indexeru</span><span class="sxs-lookup"><span data-stu-id="a0cbc-125">Indexer access</span></span>

<span data-ttu-id="a0cbc-126">Následující příklad používá typ <xref:System.Collections.Generic.Dictionary%602> .NET k demonstraci přístupu indexeru:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="a0cbc-127">Indexery umožňují indexovat instance uživatelem definovaného typu podobným způsobem jako indexování polí.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="a0cbc-128">Na rozdíl od indexů pole, které musí být celé číslo, parametry indexeru mohou být deklarovány jako libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="a0cbc-129">Další informace o indexerech naleznete v tématu [Indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="a0cbc-130">Jiné použití []</span><span class="sxs-lookup"><span data-stu-id="a0cbc-130">Other usages of []</span></span>

<span data-ttu-id="a0cbc-131">Informace o přístupu k elementu ukazatele naleznete v části [Operátor přístupu elementu ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku [Operátory související s ukazatelem.](pointer-related-operators.md)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="a0cbc-132">K určení [atributů](../../programming-guide/concepts/attributes/index.md)se také používají hranatá závorka :</span><span class="sxs-lookup"><span data-stu-id="a0cbc-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="a0cbc-133">Operátory s nulovým podmíněným podmínkami?.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-133">Null-conditional operators ?.</span></span> <span data-ttu-id="a0cbc-134">A? []</span><span class="sxs-lookup"><span data-stu-id="a0cbc-134">and ?[]</span></span>

<span data-ttu-id="a0cbc-135">K dispozici v C# 6 a novější, operátor s `?.`nulovou podmíněnou podmínkou použije přístup [člena](#member-access-expression-), nebo přístup k [elementu](#indexer-operator-), `?[]`, operace na jeho operand pouze v případě, že operand vyhodnotí na non-null; v opačném `null`případě vrátí .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="a0cbc-136">To je</span><span class="sxs-lookup"><span data-stu-id="a0cbc-136">That is,</span></span>

- <span data-ttu-id="a0cbc-137">Pokud `a` je `null`vyhodnocena `a?.x` `a?[x]` , `null`výsledek nebo je .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="a0cbc-138">Pokud `a` je vyhodnocena na `a?.x` non-null, výsledek `a?[x]` nebo `a.x` `a[x]`je stejný jako výsledek nebo , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a0cbc-139">Pokud `a.x` `a[x]` nebo vyvolá výjimku nebo `a?.x` `a?[x]` by vyvolat stejnou `a`výjimku pro non-null .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="a0cbc-140">Například pokud `a` je non-null pole `x` instance a je `a` `a?[x]` mimo hranice <xref:System.IndexOutOfRangeException>, by vyvolat .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="a0cbc-141">Operátory s nulovým podmíněným podmínkami zkratují.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="a0cbc-142">To znamená, že pokud jedna operace v řetězci `null`operace přístupu podmíněného člena nebo prvku vrátí , zbytek řetězce neprovede.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="a0cbc-143">V následujícím `B` příkladu není `A` vyhodnocena, `null` pokud je vyhodnocena `C` a není vyhodnocena, pokud `A` nebo `B` vyhodnocuje na `null`:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="a0cbc-144">Následující příklad ukazuje použití `?.` a `?[]` operátory:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="a0cbc-145">Předchozí příklad také používá [operátor `??` null-coalescing](null-coalescing-operator.md) k určení alternativního výrazu k vyhodnocení v `null`případě, že výsledek operace s nulovou podmínkou je .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="a0cbc-146">Pokud `a.x` `a[x]` nebo je typu `T`hodnoty, kterou `a?.x` `a?[x]` nelze hodnotu null , nebo je odpovídající `T?` [hodovatelný typ hodnoty s možnou hodnotou .](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="a0cbc-147">Pokud potřebujete výraz typu `T`, použijte operátor `??` null-coalescing na výraz s nulovým podmínkou, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="a0cbc-148">V předchozím příkladu pokud nepoužíváte `??` operátor, `numbers?.Length < 2` vyhodnotí, `numbers` `null` `false` kdy je .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="a0cbc-149">Operátor `?.` přístupu podmíněného člena null je také označován jako operátor Elvis.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="a0cbc-150">Vyvolání delegáta bezpečného pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="a0cbc-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="a0cbc-151">Pomocí `?.` operátoru zkontrolujte, zda delegát není null a vyvolat jej způsobem bezpečným pro přístup z více vláken (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="a0cbc-152">Tento kód je ekvivalentní následující kód, který byste použili v C # 5 nebo starší:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a><span data-ttu-id="a0cbc-153">Výraz vyvolání ()</span><span class="sxs-lookup"><span data-stu-id="a0cbc-153">Invocation expression ()</span></span>

<span data-ttu-id="a0cbc-154">Pomocí závorek `()`, můžete volat [metodu](../../programming-guide/classes-and-structs/methods.md) nebo vyvolat [delegáta](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-154">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="a0cbc-155">Následující příklad ukazuje, jak volat metodu, s argumenty nebo bez argumentů a vyvolat delegáta:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-155">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="a0cbc-156">Závorky můžete také použít při vyvolání [`new`](new-operator.md) [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s operátorem.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-156">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="a0cbc-157">Ostatní použití ()</span><span class="sxs-lookup"><span data-stu-id="a0cbc-157">Other usages of ()</span></span>

<span data-ttu-id="a0cbc-158">Závorky můžete také použít k úpravě pořadí, ve kterém chcete vyhodnotit operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-158">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="a0cbc-159">Další informace naleznete v tématu [C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-159">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="a0cbc-160">[Výrazy přetypování](type-testing-and-cast.md#cast-expression), které provádějí explicitní převody typů, také používají závorky.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-160">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="a0cbc-161">Index od koncového operátora ^</span><span class="sxs-lookup"><span data-stu-id="a0cbc-161">Index from end operator ^</span></span>

<span data-ttu-id="a0cbc-162">K dispozici v C# 8.0 a novější, `^` operátor označuje pozici prvku od konce sekvence.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-162">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="a0cbc-163">Pro posloupnost `length` `^n` délky odkazuje na `length - n` prvek s posunem od začátku sekvence.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-163">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="a0cbc-164">Například `^1` odkazuje na poslední prvek sekvence `^length` a odkazuje na první prvek sekvence.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-164">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="a0cbc-165">Jak ukazuje předchozí příklad, `^e` výraz <xref:System.Index?displayProperty=nameWithType> je typu.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-165">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="a0cbc-166">Ve `^e`výrazu `e` musí být výsledek implicitně převoditelný na `int`.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-166">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="a0cbc-167">Můžete také použít `^` operátor s [operátorem rozsahu](#range-operator-) k vytvoření rozsahu indexů.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-167">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="a0cbc-168">Další informace naleznete [v tématu Indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-168">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="a0cbc-169">Operátor rozsahu ..</span><span class="sxs-lookup"><span data-stu-id="a0cbc-169">Range operator ..</span></span>

<span data-ttu-id="a0cbc-170">K dispozici v C# 8.0 a `..` novější, operátor určuje začátek a konec rozsahu indexů jako jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-170">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="a0cbc-171">Levostranný operand je *včetně* začátku řady.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-171">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="a0cbc-172">Pravostranný operand je *exkluzivní* konec řady.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-172">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="a0cbc-173">Buď operandy může být index od začátku nebo od konce sekvence, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-173">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="a0cbc-174">Jak ukazuje předchozí příklad, `a..b` výraz <xref:System.Range?displayProperty=nameWithType> je typu.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-174">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="a0cbc-175">Ve `a..b`výrazu musí `a` `b` být výsledky a `int` musí <xref:System.Index>být implicitně převoditelné na nebo .</span><span class="sxs-lookup"><span data-stu-id="a0cbc-175">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="a0cbc-176">Můžete vynechat některý z operandů operátoru `..` a získat tak otevřený rozsah:</span><span class="sxs-lookup"><span data-stu-id="a0cbc-176">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="a0cbc-177">`a..`je ekvivalentní`a..^0`</span><span class="sxs-lookup"><span data-stu-id="a0cbc-177">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="a0cbc-178">`..b`je ekvivalentní`0..b`</span><span class="sxs-lookup"><span data-stu-id="a0cbc-178">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="a0cbc-179">`..`je ekvivalentní`0..^0`</span><span class="sxs-lookup"><span data-stu-id="a0cbc-179">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="a0cbc-180">Další informace naleznete [v tématu Indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-180">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a0cbc-181">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="a0cbc-181">Operator overloadability</span></span>

<span data-ttu-id="a0cbc-182">V `.` `()`, `^`, `..` a operátory nelze přetíženy.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-182">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="a0cbc-183">Operátor `[]` je také považován za nepřetížený operátor.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-183">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="a0cbc-184">[Indexery](../../programming-guide/indexers/index.md) slouží k podpoře indexování s typy definovanými uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a0cbc-184">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a0cbc-185">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0cbc-185">C# language specification</span></span>

<span data-ttu-id="a0cbc-186">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a0cbc-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a0cbc-187">Přístup členů</span><span class="sxs-lookup"><span data-stu-id="a0cbc-187">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="a0cbc-188">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="a0cbc-188">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="a0cbc-189">Operátor s nulovým podmíněným podmínkou</span><span class="sxs-lookup"><span data-stu-id="a0cbc-189">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="a0cbc-190">Výrazy vyvolání</span><span class="sxs-lookup"><span data-stu-id="a0cbc-190">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="a0cbc-191">Další informace o indexech a rozsahech naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="a0cbc-191">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0cbc-192">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0cbc-192">See also</span></span>

- [<span data-ttu-id="a0cbc-193">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="a0cbc-193">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a0cbc-194">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0cbc-194">C# operators</span></span>](index.md)
- [<span data-ttu-id="a0cbc-195">?? (operátor null-coalescing)</span><span class="sxs-lookup"><span data-stu-id="a0cbc-195">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="a0cbc-196">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="a0cbc-196">:: operator</span></span>](namespace-alias-qualifier.md)
