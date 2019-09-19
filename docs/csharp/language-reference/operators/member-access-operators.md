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
ms.openlocfilehash: 45af31d10d77f4c63b27b34595b97fdd11ef95a1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116128"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="2e3cb-103">Operátory přístupu členů (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="2e3cb-104">Při přístupu k členu typu můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="2e3cb-105">[(přístup ke členu): přístup ke členu oboru názvů nebo typu `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="2e3cb-106">[(element pole nebo přístup indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="2e3cb-107">[a (podmíněnéoperátoryshodnotounull):kprovedeníoperacepřístupučlenaneboelementupouzevpřípadě,žeoperandjenenulový`?[]` `?.` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="2e3cb-108">(vyvolání): pro volání metody, která je k dispozici, nebo vyvolání delegáta [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="2e3cb-109">[(index od konce): k označení, že pozice prvku je od konce sekvence `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="2e3cb-110">(rozsah): Pokud chcete zadat rozsah indexů, které můžete použít k získání rozsahu elementů Sequence. [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="2e3cb-111">Operátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-111">Member access operator .</span></span>

<span data-ttu-id="2e3cb-112">`.` Token použijete pro přístup ke členu oboru názvů nebo typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="2e3cb-113">Použijte `.` pro přístup k vnořenému oboru názvů v rámci oboru názvů, jak ukazuje následující příklad [ `using` direktivy](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="2e3cb-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="2e3cb-114">Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="2e3cb-115">Použijte směrnici pro použití kvalifikovaných názvů jako nepovinné. [ `using` ](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="2e3cb-116">Použijte `.` pro přístup ke [členům typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="2e3cb-117">Můžete také použít `.` pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="2e3cb-118">Operátor indexer []</span><span class="sxs-lookup"><span data-stu-id="2e3cb-118">Indexer operator []</span></span>

<span data-ttu-id="2e3cb-119">Hranaté závorky `[]`se obvykle používají pro přístup k objektům Array, indexer nebo Pointer.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="2e3cb-120">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="2e3cb-120">Array access</span></span>

<span data-ttu-id="2e3cb-121">Následující příklad ukazuje, jak získat přístup k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="2e3cb-122">Pokud je index pole mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="2e3cb-123">Jak ukazuje předchozí příklad, je také možné použít hranaté závorky, pokud deklarujete typ pole nebo instanci pole instance.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="2e3cb-124">Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="2e3cb-125">Přístup indexeru</span><span class="sxs-lookup"><span data-stu-id="2e3cb-125">Indexer access</span></span>

<span data-ttu-id="2e3cb-126">Následující příklad používá typ .NET <xref:System.Collections.Generic.Dictionary%602> k demonstraci přístupu indexeru:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-126">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="2e3cb-127">Indexery umožňují indexovat instance uživatelsky definovaného typu podobným způsobem jako indexování pole.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="2e3cb-128">Na rozdíl od indexů pole, který musí být celé číslo, argumenty indexeru lze deklarovat jako libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-128">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="2e3cb-129">Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="2e3cb-130">Další použití []</span><span class="sxs-lookup"><span data-stu-id="2e3cb-130">Other usages of []</span></span>

<span data-ttu-id="2e3cb-131">Informace o přístupu k prvkům ukazatele naleznete v části [operátor přístupu k prvku ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku o [operátorech souvisejících s ukazateli](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="2e3cb-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="2e3cb-132">Pomocí hranatých závorek určíte [atributy](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="2e3cb-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="2e3cb-133">Podmíněné operátory s hodnotou null?.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-133">Null-conditional operators ?.</span></span> <span data-ttu-id="2e3cb-134">ani? []</span><span class="sxs-lookup"><span data-stu-id="2e3cb-134">and ?[]</span></span>

<span data-ttu-id="2e3cb-135">K dispozici v 6 nebo novějším, operátor s hodnotou null aplikuje na `?.`operand přístup člena, `?[]`nebo element, operace na jeho operand pouze v C# případě, že se tento operand vyhodnocuje jako nenulový.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="2e3cb-136">Pokud je operand vyhodnocen `null`jako, výsledek použití operátoru je. `null`</span><span class="sxs-lookup"><span data-stu-id="2e3cb-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="2e3cb-137">Operátor `?.` přístupu k podmíněnému členu s hodnotou null je také označován jako Elvis operátor.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="2e3cb-138">Operátory podmíněné hodnotou null jsou krátkodobé okruhy.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="2e3cb-139">To znamená, že pokud se vrátí `null`jedna operace v řetězci podmíněného člena nebo operace přístupu k prvkům, zbytek řetězu se nespustí.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="2e3cb-140">V následujícím `B` příkladu není vyhodnocena, pokud `A` `null` je vyhodnocena `C` jako a není vyhodnocena v případě `null`, že `A` nebo `B` je vyhodnocena jako:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="2e3cb-141">Následující příklad ukazuje použití `?.` operátorů a: `?[]`</span><span class="sxs-lookup"><span data-stu-id="2e3cb-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="2e3cb-142">Předchozí příklad také ukazuje použití [operátoru nulového slučování](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-142">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="2e3cb-143">Operátor pro sjednocení hodnoty null můžete použít k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že je `null`výsledkem operace podmíněného zpracování hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-143">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="2e3cb-144">Volání delegáta bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="2e3cb-144">Thread-safe delegate invocation</span></span>

<span data-ttu-id="2e3cb-145">Použijte operátor ke kontrole, zda delegát není null a vyvolá ho v bezpečném režimu (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód: `?.`</span><span class="sxs-lookup"><span data-stu-id="2e3cb-145">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="2e3cb-146">Tento kód je ekvivalentní následujícímu kódu, který byste použili v C# 5 nebo starších verzích:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-146">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="2e3cb-147">Operátor vyvolání ()</span><span class="sxs-lookup"><span data-stu-id="2e3cb-147">Invocation operator ()</span></span>

<span data-ttu-id="2e3cb-148">Použijte závorky, `()`, pro volání [metody](../../programming-guide/classes-and-structs/methods.md) nebo vyvolání [delegáta](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-148">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="2e3cb-149">Následující příklad ukazuje, jak zavolat metodu s argumenty nebo bez argumentů a vyvolat delegáta:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-149">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="2e3cb-150">Při vyvolání [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s [`new`](new-operator.md) operátorem můžete také použít závorky.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-150">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="2e3cb-151">Další použití pro ()</span><span class="sxs-lookup"><span data-stu-id="2e3cb-151">Other usages of ()</span></span>

<span data-ttu-id="2e3cb-152">Pomocí závorek můžete také upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-152">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="2e3cb-153">Další informace najdete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-153">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="2e3cb-154">[Výrazy přetypování](type-testing-and-cast.md#cast-operator-), které provádějí explicitní převody typů, používají také závorky.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-154">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="2e3cb-155">Index z operátoru end ^</span><span class="sxs-lookup"><span data-stu-id="2e3cb-155">Index from end operator ^</span></span>

<span data-ttu-id="2e3cb-156">K dispozici v C# 8,0 a novějším, `^` operátor označuje pozici elementu na konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-156">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="2e3cb-157">Pro sekvenci délky `length` `^n` odkazuje na prvek s posunem `length - n` od začátku sekvence.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-157">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="2e3cb-158">Například `^1` odkazuje na poslední prvek sekvence a `^length` odkazuje na první prvek sekvence.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-158">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="2e3cb-159">Jak ukazuje předchozí příklad, výraz `^e` je <xref:System.Index?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-159">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="2e3cb-160">Ve výrazu `^e`je `e` výsledek nutné implicitně převést na `int`.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-160">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="2e3cb-161">Můžete také použít `^` operátor s [operátorem Range](#range-operator-) a vytvořit tak rozsah indexů.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-161">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="2e3cb-162">Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-162">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="2e3cb-163">Operátor rozsahu..</span><span class="sxs-lookup"><span data-stu-id="2e3cb-163">Range operator ..</span></span>

<span data-ttu-id="2e3cb-164">K dispozici v C# 8,0 a novějším, `..` operátor určuje začátek a konec rozsahu indexů jako své operandy.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-164">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="2e3cb-165">Levý operand je *Celková* začátek rozsahu.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-165">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="2e3cb-166">Pravý operand je *výhradním* koncem rozsahu.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-166">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="2e3cb-167">Jedním z operandů může být index od začátku nebo po konci sekvence, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-167">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="2e3cb-168">Jak ukazuje předchozí příklad, výraz `a..b` je <xref:System.Range?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-168">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="2e3cb-169">Ve výrazu `a..b` `a` jsou výsledky a `b` musí být implicitně převoditelné na `int` nebo <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-169">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="2e3cb-170">Pokud chcete získat rozsah otevřeného a koncového výrazu `..` , můžete vynechat kterýkoli z operandů operátoru:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-170">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="2e3cb-171">`a..`je ekvivalentem`a..^0`</span><span class="sxs-lookup"><span data-stu-id="2e3cb-171">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="2e3cb-172">`..b`je ekvivalentem`0..b`</span><span class="sxs-lookup"><span data-stu-id="2e3cb-172">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="2e3cb-173">`..`je ekvivalentem`0..^0`</span><span class="sxs-lookup"><span data-stu-id="2e3cb-173">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="2e3cb-174">Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="2e3cb-174">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2e3cb-175">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="2e3cb-175">Operator overloadability</span></span>

<span data-ttu-id="2e3cb-176">Operátory, `()` ,`^`anemohoubýtpřetíženy. `.` `..`</span><span class="sxs-lookup"><span data-stu-id="2e3cb-176">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="2e3cb-177">`[]` Operátor je také považován za operátor, který není přetížen.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-177">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="2e3cb-178">Použijte [indexery](../../programming-guide/indexers/index.md) k podpoře indexování s uživatelsky definovanými typy.</span><span class="sxs-lookup"><span data-stu-id="2e3cb-178">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2e3cb-179">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2e3cb-179">C# language specification</span></span>

<span data-ttu-id="2e3cb-180">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="2e3cb-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2e3cb-181">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="2e3cb-181">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="2e3cb-182">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="2e3cb-182">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="2e3cb-183">Podmíněný operátor s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="2e3cb-183">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="2e3cb-184">Výrazy vyvolání</span><span class="sxs-lookup"><span data-stu-id="2e3cb-184">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="2e3cb-185">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e3cb-185">See also</span></span>

- [<span data-ttu-id="2e3cb-186">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="2e3cb-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2e3cb-187">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2e3cb-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="2e3cb-188">?? (operátor slučování null)</span><span class="sxs-lookup"><span data-stu-id="2e3cb-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="2e3cb-189">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="2e3cb-189">:: operator</span></span>](namespace-alias-qualifier.md)
