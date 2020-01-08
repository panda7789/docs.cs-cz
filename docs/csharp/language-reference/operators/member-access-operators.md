---
title: Operátory přístupu členů – C# referenční informace
description: Další informace C# o operátorech, které lze použít pro přístup ke členům typu.
ms.date: 09/18/2019
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
ms.openlocfilehash: e69cc5a9634f0b5232562782557645894f94ce2e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345306"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="e6042-103">Operátory přístupu členů (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="e6042-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="e6042-104">Při přístupu k členu typu můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="e6042-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="e6042-105">[`.` (přístup do členů)](#member-access-operator-): přístup ke členu oboru názvů nebo typu</span><span class="sxs-lookup"><span data-stu-id="e6042-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="e6042-106">[`[]` (element pole nebo přístup indexeru)](#indexer-operator-): pro přístup k prvku pole nebo indexeru typu</span><span class="sxs-lookup"><span data-stu-id="e6042-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="e6042-107">[`?.` a `?[]` (koncoví operátoři s hodnotou null)](#null-conditional-operators--and-): k provedení operace přístupu člena nebo elementu pouze v případě, že operand je jiný než null</span><span class="sxs-lookup"><span data-stu-id="e6042-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="e6042-108">[`()` (vyvolání)](#invocation-operator-): pro volání metody, která je k dispozici, nebo vyvolání delegáta</span><span class="sxs-lookup"><span data-stu-id="e6042-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="e6042-109">[`^` (index z konce)](#index-from-end-operator-): k označení, že pozice prvku je od konce sekvence</span><span class="sxs-lookup"><span data-stu-id="e6042-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="e6042-110">[`..` (rozsah)](#range-operator-): Pokud chcete zadat rozsah indexů, které můžete použít k získání rozsahu elementů Sequence.</span><span class="sxs-lookup"><span data-stu-id="e6042-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="e6042-111">Operátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="e6042-111">Member access operator .</span></span>

<span data-ttu-id="e6042-112">Token `.` použijete pro přístup ke členu oboru názvů nebo typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e6042-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="e6042-113">Použijte `.` pro přístup k vnořenému oboru názvů v rámci oboru názvů, jak ukazuje následující příklad [direktivy`using`](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="e6042-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="e6042-114">Použijte `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="e6042-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="e6042-115">Použijte [direktivu`using`](../keywords/using-directive.md) , aby bylo možné používat kvalifikované názvy jako nepovinné.</span><span class="sxs-lookup"><span data-stu-id="e6042-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="e6042-116">Použijte `.` pro přístup ke [členům typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="e6042-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="e6042-117">Pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md)můžete použít také `.`.</span><span class="sxs-lookup"><span data-stu-id="e6042-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="e6042-118">Operátor indexer []</span><span class="sxs-lookup"><span data-stu-id="e6042-118">Indexer operator []</span></span>

<span data-ttu-id="e6042-119">Hranaté závorky, `[]`, se obvykle používají pro přístup k objektům Array, indexer nebo Pointer.</span><span class="sxs-lookup"><span data-stu-id="e6042-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="e6042-120">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="e6042-120">Array access</span></span>

<span data-ttu-id="e6042-121">Následující příklad ukazuje, jak získat přístup k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="e6042-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="e6042-122">Pokud je index pole mimo hranice odpovídající dimenze pole, je vyvolána <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="e6042-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="e6042-123">Jak ukazuje předchozí příklad, je také možné použít hranaté závorky, pokud deklarujete typ pole nebo instanci pole instance.</span><span class="sxs-lookup"><span data-stu-id="e6042-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="e6042-124">Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6042-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="e6042-125">Přístup indexeru</span><span class="sxs-lookup"><span data-stu-id="e6042-125">Indexer access</span></span>

<span data-ttu-id="e6042-126">Následující příklad používá typ <xref:System.Collections.Generic.Dictionary%602> .NET k demonstraci přístupu indexeru:</span><span class="sxs-lookup"><span data-stu-id="e6042-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="e6042-127">Indexery umožňují indexovat instance uživatelsky definovaného typu podobným způsobem jako indexování pole.</span><span class="sxs-lookup"><span data-stu-id="e6042-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="e6042-128">Na rozdíl od indexů pole, který musí být celé číslo, lze parametry indexeru deklarovat jako libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="e6042-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="e6042-129">Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6042-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e6042-130">Další použití []</span><span class="sxs-lookup"><span data-stu-id="e6042-130">Other usages of []</span></span>

<span data-ttu-id="e6042-131">Informace o přístupu k prvkům ukazatele naleznete v části [operátor přístupu k prvku ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku o [operátorech souvisejících s ukazateli](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="e6042-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="e6042-132">Pomocí hranatých závorek určíte [atributy](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="e6042-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="e6042-133">Podmíněné operátory s hodnotou null?.</span><span class="sxs-lookup"><span data-stu-id="e6042-133">Null-conditional operators ?.</span></span> <span data-ttu-id="e6042-134">ani? []</span><span class="sxs-lookup"><span data-stu-id="e6042-134">and ?[]</span></span>

<span data-ttu-id="e6042-135">K dispozici v 6 nebo novějším, operátor s hodnotou null používá pro přístup C# [člena přístup](#member-access-operator-), `?.`nebo [k elementu](#indexer-operator-), `?[]`, operaci na jeho operand pouze v případě, že je tento operand vyhodnocen jako jiný než null; v opačném případě vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="e6042-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-operator-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="e6042-136">To je</span><span class="sxs-lookup"><span data-stu-id="e6042-136">That is,</span></span>

- <span data-ttu-id="e6042-137">Pokud se `a` vyhodnotí jako `null`, výsledek `a?.x` nebo `a?[x]` je `null`.</span><span class="sxs-lookup"><span data-stu-id="e6042-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="e6042-138">Pokud je `a` vyhodnocena jako nenulová, výsledek `a?.x` nebo `a?[x]` je stejný jako výsledek `a.x` nebo `a[x]`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e6042-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e6042-139">Pokud `a.x` nebo `a[x]` vyvolá výjimku, `a?.x` nebo `a?[x]` by vyvolal stejnou výjimku pro `a`, který není null.</span><span class="sxs-lookup"><span data-stu-id="e6042-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="e6042-140">Například pokud `a` je instance pole, která není null a `x` je mimo hranice `a`, `a?[x]` by vyvolala <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="e6042-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="e6042-141">Operátory podmíněné hodnotou null jsou krátkodobé okruhy.</span><span class="sxs-lookup"><span data-stu-id="e6042-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="e6042-142">To znamená, že pokud jedna operace v řetězci podmíněného člena nebo operace přístupu k elementu vrátí `null`, zbytek řetězu se nespustí.</span><span class="sxs-lookup"><span data-stu-id="e6042-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="e6042-143">V následujícím příkladu není `B` vyhodnocena, pokud `A` vyhodnocena `null` a `C` nejsou vyhodnoceny, pokud `A` nebo `B` vyhodnocena jako `null`:</span><span class="sxs-lookup"><span data-stu-id="e6042-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="e6042-144">Následující příklad ukazuje použití operátorů `?.` a `?[]`:</span><span class="sxs-lookup"><span data-stu-id="e6042-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="e6042-145">Předchozí příklad také používá [operátor slučování null `??`](null-coalescing-operator.md) k určení alternativního výrazu pro vyhodnocení pro případ, že je `null`výsledek operace podmíněného hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e6042-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="e6042-146">Podmíněný operátor přístupu člena s hodnotou null `?.` je také označován jako operátor Elvis.</span><span class="sxs-lookup"><span data-stu-id="e6042-146">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="e6042-147">Volání delegáta bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="e6042-147">Thread-safe delegate invocation</span></span>

<span data-ttu-id="e6042-148">Použijte operátor `?.`, chcete-li zjistit, zda delegát není null, a vyvolat ho v bezpečném režimu (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="e6042-148">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="e6042-149">Tento kód je ekvivalentní následujícímu kódu, který byste použili v C# 5 nebo starších verzích:</span><span class="sxs-lookup"><span data-stu-id="e6042-149">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="e6042-150">Operátor vyvolání ()</span><span class="sxs-lookup"><span data-stu-id="e6042-150">Invocation operator ()</span></span>

<span data-ttu-id="e6042-151">Použijte kulaté závorky, `()`, pro volání [metody](../../programming-guide/classes-and-structs/methods.md) nebo vyvolání [delegáta](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6042-151">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="e6042-152">Následující příklad ukazuje, jak zavolat metodu s argumenty nebo bez argumentů a vyvolat delegáta:</span><span class="sxs-lookup"><span data-stu-id="e6042-152">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="e6042-153">Závorky můžete použít také při volání [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s operátorem [`new`](new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="e6042-153">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="e6042-154">Další použití pro ()</span><span class="sxs-lookup"><span data-stu-id="e6042-154">Other usages of ()</span></span>

<span data-ttu-id="e6042-155">Pomocí závorek můžete také upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="e6042-155">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="e6042-156">Další informace najdete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="e6042-156">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="e6042-157">[Výrazy přetypování](type-testing-and-cast.md#cast-operator-), které provádějí explicitní převody typů, používají také závorky.</span><span class="sxs-lookup"><span data-stu-id="e6042-157">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="e6042-158">Index z operátoru end ^</span><span class="sxs-lookup"><span data-stu-id="e6042-158">Index from end operator ^</span></span>

<span data-ttu-id="e6042-159">K dispozici v C# 8,0 a novějším, operátor `^` označuje pozici elementu na konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="e6042-159">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="e6042-160">Pro sekvenci délky `length``^n` odkazuje na prvek s posunem `length - n` od začátku sekvence.</span><span class="sxs-lookup"><span data-stu-id="e6042-160">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="e6042-161">Například `^1` odkazuje na poslední prvek sekvence a `^length` odkazuje na první prvek sekvence.</span><span class="sxs-lookup"><span data-stu-id="e6042-161">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="e6042-162">Jak ukazuje předchozí příklad, `^e` výrazů je typ <xref:System.Index?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6042-162">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e6042-163">Ve výrazu `^e`musí být výsledek `e` implicitně převoditelné na `int`.</span><span class="sxs-lookup"><span data-stu-id="e6042-163">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="e6042-164">Můžete také použít operátor `^` s [operátorem Range](#range-operator-) a vytvořit tak rozsah indexů.</span><span class="sxs-lookup"><span data-stu-id="e6042-164">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="e6042-165">Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="e6042-165">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="e6042-166">Operátor rozsahu..</span><span class="sxs-lookup"><span data-stu-id="e6042-166">Range operator ..</span></span>

<span data-ttu-id="e6042-167">K dispozici v C# 8,0 a novějším, operátor `..` Určuje začátek a konec rozsahu indexů jako své operandy.</span><span class="sxs-lookup"><span data-stu-id="e6042-167">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="e6042-168">Levý operand je *Celková* začátek rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e6042-168">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="e6042-169">Pravý operand je *výhradním* koncem rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e6042-169">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="e6042-170">Jedním z operandů může být index od začátku nebo po konci sekvence, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e6042-170">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="e6042-171">Jak ukazuje předchozí příklad, `a..b` výrazů je typ <xref:System.Range?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6042-171">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e6042-172">Ve výrazu `a..b`musí být výsledky `a` a `b` implicitně převoditelné na `int` nebo <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="e6042-172">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="e6042-173">Můžete vynechat kterýkoli z operandů operátoru `..`, abyste získali rozsah otevřeného a koncového výrazu:</span><span class="sxs-lookup"><span data-stu-id="e6042-173">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="e6042-174">`a..` je ekvivalentem `a..^0`</span><span class="sxs-lookup"><span data-stu-id="e6042-174">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="e6042-175">`..b` je ekvivalentem `0..b`</span><span class="sxs-lookup"><span data-stu-id="e6042-175">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="e6042-176">`..` je ekvivalentem `0..^0`</span><span class="sxs-lookup"><span data-stu-id="e6042-176">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="e6042-177">Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="e6042-177">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e6042-178">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="e6042-178">Operator overloadability</span></span>

<span data-ttu-id="e6042-179">Operátory `.`, `()`, `^`a `..` nelze přečítat.</span><span class="sxs-lookup"><span data-stu-id="e6042-179">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="e6042-180">Operátor `[]` je také považován za operátor, který není přetížen.</span><span class="sxs-lookup"><span data-stu-id="e6042-180">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="e6042-181">Použijte [indexery](../../programming-guide/indexers/index.md) k podpoře indexování s uživatelsky definovanými typy.</span><span class="sxs-lookup"><span data-stu-id="e6042-181">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e6042-182">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6042-182">C# language specification</span></span>

<span data-ttu-id="e6042-183">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="e6042-183">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e6042-184">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="e6042-184">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="e6042-185">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="e6042-185">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="e6042-186">Podmíněný operátor s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="e6042-186">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="e6042-187">Výrazy vyvolání</span><span class="sxs-lookup"><span data-stu-id="e6042-187">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="e6042-188">Další informace o indexech a oblastech najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="e6042-188">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6042-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6042-189">See also</span></span>

- [<span data-ttu-id="e6042-190">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="e6042-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e6042-191">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6042-191">C# operators</span></span>](index.md)
- [<span data-ttu-id="e6042-192">?? (operátor slučování null)</span><span class="sxs-lookup"><span data-stu-id="e6042-192">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="e6042-193">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="e6042-193">:: operator</span></span>](namespace-alias-qualifier.md)
