---
title: Operátory přístupu k členům – odkaz jazyka C#
description: Další informace o operátory Jazyka C#, které můžete použít pro přístup k členům typu.
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
ms.openlocfilehash: 4d4bc0c192912b5fa87a8e91bc5ba0e1d4ce3598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399509"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="f8fda-103">Operátory přístupu k členům (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="f8fda-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="f8fda-104">Při přístupu k členu typu můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="f8fda-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="f8fda-105">(členský přístup) : přístup k členovi oboru názvů nebo typu [ `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="f8fda-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="f8fda-106">[(element pole nebo přístup k indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="f8fda-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="f8fda-107">[a `?[]` (operátory s nulovým podmíněným podmínkou): provádět operaci přístupu k členu nebo prvku pouze v případě, že operand není `?.` ](#null-conditional-operators--and-)null</span><span class="sxs-lookup"><span data-stu-id="f8fda-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="f8fda-108">(vyvolání) : volání přístupné metody nebo vyvolání delegáta [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="f8fda-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="f8fda-109">(index od konce): označuje, že pozice prvku je od konce sekvence [ `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="f8fda-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="f8fda-110">(rozsah) : určení rozsahu indexů, které můžete použít k získání rozsahu sekvenčních prvků [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="f8fda-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="f8fda-111">Operátor přístupu člena .</span><span class="sxs-lookup"><span data-stu-id="f8fda-111">Member access operator .</span></span>

<span data-ttu-id="f8fda-112">`.` Token se používá pro přístup k členu oboru názvů nebo typu, jak ukazují následující příklady:</span><span class="sxs-lookup"><span data-stu-id="f8fda-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="f8fda-113">Slouží `.` k přístupu k vnořené oboru názvů v oboru názvů, jak ukazuje následující příklad [ `using` směrnice:](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="f8fda-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="f8fda-114">Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f8fda-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="f8fda-115">Použití [ `using` směrnice,](../keywords/using-directive.md) aby bylo použití kvalifikovaných názvů volitelné.</span><span class="sxs-lookup"><span data-stu-id="f8fda-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="f8fda-116">Slouží `.` k přístupu k [členům typu](../../programming-guide/classes-and-structs/index.md#members), statickým a nestatickým, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f8fda-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="f8fda-117">Můžete také `.` použít pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="f8fda-118">Operátor indexeru []</span><span class="sxs-lookup"><span data-stu-id="f8fda-118">Indexer operator []</span></span>

<span data-ttu-id="f8fda-119">Hranaté `[]`závorky , , se obvykle používají pro přístup k polím, indexeru nebo elementu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f8fda-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="f8fda-120">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="f8fda-120">Array access</span></span>

<span data-ttu-id="f8fda-121">Následující příklad ukazuje, jak získat přístup k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="f8fda-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="f8fda-122">Pokud index pole je mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f8fda-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="f8fda-123">Jak ukazuje předchozí příklad, čtvercové závorky použijete také při deklarování typu pole nebo instance instance pole.</span><span class="sxs-lookup"><span data-stu-id="f8fda-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="f8fda-124">Další informace o polích naleznete v [tématu Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="f8fda-125">Přístup k indexeru</span><span class="sxs-lookup"><span data-stu-id="f8fda-125">Indexer access</span></span>

<span data-ttu-id="f8fda-126">Následující příklad používá typ <xref:System.Collections.Generic.Dictionary%602> .NET k demonstraci přístupu indexeru:</span><span class="sxs-lookup"><span data-stu-id="f8fda-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="f8fda-127">Indexery umožňují indexovat instance uživatelem definovaného typu podobným způsobem jako indexování polí.</span><span class="sxs-lookup"><span data-stu-id="f8fda-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="f8fda-128">Na rozdíl od indexů pole, které musí být celé číslo, parametry indexeru mohou být deklarovány jako libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="f8fda-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="f8fda-129">Další informace o indexerech naleznete v tématu [Indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="f8fda-130">Jiné použití []</span><span class="sxs-lookup"><span data-stu-id="f8fda-130">Other usages of []</span></span>

<span data-ttu-id="f8fda-131">Informace o přístupu k elementu ukazatele naleznete v části [Operátor přístupu elementu ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku [Operátory související s ukazatelem.](pointer-related-operators.md)</span><span class="sxs-lookup"><span data-stu-id="f8fda-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="f8fda-132">K určení [atributů](../../programming-guide/concepts/attributes/index.md)se také používají hranatá závorka :</span><span class="sxs-lookup"><span data-stu-id="f8fda-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="f8fda-133">Operátory s nulovým podmíněným podmínkami?.</span><span class="sxs-lookup"><span data-stu-id="f8fda-133">Null-conditional operators ?.</span></span> <span data-ttu-id="f8fda-134">A? []</span><span class="sxs-lookup"><span data-stu-id="f8fda-134">and ?[]</span></span>

<span data-ttu-id="f8fda-135">K dispozici v C# 6 a novější, operátor s `?.`nulovou podmíněnou podmínkou použije přístup [člena](#member-access-operator-), nebo přístup k [elementu](#indexer-operator-), `?[]`, operace na jeho operand pouze v případě, že operand vyhodnotí na non-null; v opačném `null`případě vrátí .</span><span class="sxs-lookup"><span data-stu-id="f8fda-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-operator-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="f8fda-136">To je</span><span class="sxs-lookup"><span data-stu-id="f8fda-136">That is,</span></span>

- <span data-ttu-id="f8fda-137">Pokud `a` je `null`vyhodnocena `a?.x` `a?[x]` , `null`výsledek nebo je .</span><span class="sxs-lookup"><span data-stu-id="f8fda-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="f8fda-138">Pokud `a` je vyhodnocena na `a?.x` non-null, výsledek `a?[x]` nebo `a.x` `a[x]`je stejný jako výsledek nebo , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f8fda-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f8fda-139">Pokud `a.x` `a[x]` nebo vyvolá výjimku nebo `a?.x` `a?[x]` by vyvolat stejnou `a`výjimku pro non-null .</span><span class="sxs-lookup"><span data-stu-id="f8fda-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="f8fda-140">Například pokud `a` je non-null pole `x` instance a je `a` `a?[x]` mimo hranice <xref:System.IndexOutOfRangeException>, by vyvolat .</span><span class="sxs-lookup"><span data-stu-id="f8fda-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="f8fda-141">Operátory s nulovým podmíněným podmínkami zkratují.</span><span class="sxs-lookup"><span data-stu-id="f8fda-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="f8fda-142">To znamená, že pokud jedna operace v řetězci `null`operace přístupu podmíněného člena nebo prvku vrátí , zbytek řetězce neprovede.</span><span class="sxs-lookup"><span data-stu-id="f8fda-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="f8fda-143">V následujícím `B` příkladu není `A` vyhodnocena, `null` pokud je vyhodnocena `C` a není vyhodnocena, pokud `A` nebo `B` vyhodnocuje na `null`:</span><span class="sxs-lookup"><span data-stu-id="f8fda-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="f8fda-144">Následující příklad ukazuje použití `?.` a `?[]` operátory:</span><span class="sxs-lookup"><span data-stu-id="f8fda-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="f8fda-145">Předchozí příklad také používá [operátor `??` null-coalescing](null-coalescing-operator.md) k určení alternativního výrazu k vyhodnocení v `null`případě, že výsledek operace s nulovou podmínkou je .</span><span class="sxs-lookup"><span data-stu-id="f8fda-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="f8fda-146">Operátor `?.` přístupu podmíněného člena null je také označován jako operátor Elvis.</span><span class="sxs-lookup"><span data-stu-id="f8fda-146">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="f8fda-147">Vyvolání delegáta bezpečného pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="f8fda-147">Thread-safe delegate invocation</span></span>

<span data-ttu-id="f8fda-148">Pomocí `?.` operátoru zkontrolujte, zda delegát není null a vyvolat jej způsobem bezpečným pro přístup z více vláken (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f8fda-148">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="f8fda-149">Tento kód je ekvivalentní následující kód, který byste použili v C # 5 nebo starší:</span><span class="sxs-lookup"><span data-stu-id="f8fda-149">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="f8fda-150">Operátor vyvolání ()</span><span class="sxs-lookup"><span data-stu-id="f8fda-150">Invocation operator ()</span></span>

<span data-ttu-id="f8fda-151">Pomocí závorek `()`, můžete volat [metodu](../../programming-guide/classes-and-structs/methods.md) nebo vyvolat [delegáta](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-151">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="f8fda-152">Následující příklad ukazuje, jak volat metodu, s argumenty nebo bez argumentů a vyvolat delegáta:</span><span class="sxs-lookup"><span data-stu-id="f8fda-152">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="f8fda-153">Závorky můžete také použít při vyvolání [`new`](new-operator.md) [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s operátorem.</span><span class="sxs-lookup"><span data-stu-id="f8fda-153">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="f8fda-154">Ostatní použití ()</span><span class="sxs-lookup"><span data-stu-id="f8fda-154">Other usages of ()</span></span>

<span data-ttu-id="f8fda-155">Závorky můžete také použít k úpravě pořadí, ve kterém chcete vyhodnotit operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="f8fda-155">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="f8fda-156">Další informace naleznete v tématu [C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-156">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="f8fda-157">[Výrazy přetypování](type-testing-and-cast.md#cast-operator-), které provádějí explicitní převody typů, také používají závorky.</span><span class="sxs-lookup"><span data-stu-id="f8fda-157">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="f8fda-158">Index od koncového operátora ^</span><span class="sxs-lookup"><span data-stu-id="f8fda-158">Index from end operator ^</span></span>

<span data-ttu-id="f8fda-159">K dispozici v C# 8.0 a novější, `^` operátor označuje pozici prvku od konce sekvence.</span><span class="sxs-lookup"><span data-stu-id="f8fda-159">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="f8fda-160">Pro posloupnost `length` `^n` délky odkazuje na `length - n` prvek s posunem od začátku sekvence.</span><span class="sxs-lookup"><span data-stu-id="f8fda-160">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="f8fda-161">Například `^1` odkazuje na poslední prvek sekvence `^length` a odkazuje na první prvek sekvence.</span><span class="sxs-lookup"><span data-stu-id="f8fda-161">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="f8fda-162">Jak ukazuje předchozí příklad, `^e` výraz <xref:System.Index?displayProperty=nameWithType> je typu.</span><span class="sxs-lookup"><span data-stu-id="f8fda-162">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="f8fda-163">Ve `^e`výrazu `e` musí být výsledek implicitně převoditelný na `int`.</span><span class="sxs-lookup"><span data-stu-id="f8fda-163">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="f8fda-164">Můžete také použít `^` operátor s [operátorem rozsahu](#range-operator-) k vytvoření rozsahu indexů.</span><span class="sxs-lookup"><span data-stu-id="f8fda-164">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="f8fda-165">Další informace naleznete [v tématu Indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-165">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="f8fda-166">Operátor rozsahu ..</span><span class="sxs-lookup"><span data-stu-id="f8fda-166">Range operator ..</span></span>

<span data-ttu-id="f8fda-167">K dispozici v C# 8.0 a `..` novější, operátor určuje začátek a konec rozsahu indexů jako jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="f8fda-167">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="f8fda-168">Levostranný operand je *včetně* začátku řady.</span><span class="sxs-lookup"><span data-stu-id="f8fda-168">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="f8fda-169">Pravostranný operand je *exkluzivní* konec řady.</span><span class="sxs-lookup"><span data-stu-id="f8fda-169">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="f8fda-170">Buď operandy může být index od začátku nebo od konce sekvence, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="f8fda-170">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="f8fda-171">Jak ukazuje předchozí příklad, `a..b` výraz <xref:System.Range?displayProperty=nameWithType> je typu.</span><span class="sxs-lookup"><span data-stu-id="f8fda-171">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="f8fda-172">Ve `a..b`výrazu musí `a` `b` být výsledky a `int` musí <xref:System.Index>být implicitně převoditelné na nebo .</span><span class="sxs-lookup"><span data-stu-id="f8fda-172">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="f8fda-173">Můžete vynechat některý z operandů operátoru `..` a získat tak otevřený rozsah:</span><span class="sxs-lookup"><span data-stu-id="f8fda-173">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="f8fda-174">`a..`je ekvivalentní`a..^0`</span><span class="sxs-lookup"><span data-stu-id="f8fda-174">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="f8fda-175">`..b`je ekvivalentní`0..b`</span><span class="sxs-lookup"><span data-stu-id="f8fda-175">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="f8fda-176">`..`je ekvivalentní`0..^0`</span><span class="sxs-lookup"><span data-stu-id="f8fda-176">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="f8fda-177">Další informace naleznete [v tématu Indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-177">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f8fda-178">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="f8fda-178">Operator overloadability</span></span>

<span data-ttu-id="f8fda-179">V `.` `()`, `^`, `..` a operátory nelze přetíženy.</span><span class="sxs-lookup"><span data-stu-id="f8fda-179">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="f8fda-180">Operátor `[]` je také považován za nepřetížený operátor.</span><span class="sxs-lookup"><span data-stu-id="f8fda-180">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="f8fda-181">[Indexery](../../programming-guide/indexers/index.md) slouží k podpoře indexování s typy definovanými uživatelem.</span><span class="sxs-lookup"><span data-stu-id="f8fda-181">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f8fda-182">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f8fda-182">C# language specification</span></span>

<span data-ttu-id="f8fda-183">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="f8fda-183">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f8fda-184">Přístup členů</span><span class="sxs-lookup"><span data-stu-id="f8fda-184">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="f8fda-185">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="f8fda-185">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="f8fda-186">Operátor s nulovým podmíněným podmínkou</span><span class="sxs-lookup"><span data-stu-id="f8fda-186">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="f8fda-187">Výrazy vyvolání</span><span class="sxs-lookup"><span data-stu-id="f8fda-187">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="f8fda-188">Další informace o indexech a rozsahech naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="f8fda-188">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8fda-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8fda-189">See also</span></span>

- [<span data-ttu-id="f8fda-190">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="f8fda-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f8fda-191">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f8fda-191">C# operators</span></span>](index.md)
- [<span data-ttu-id="f8fda-192">?? (operátor null-coalescing)</span><span class="sxs-lookup"><span data-stu-id="f8fda-192">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="f8fda-193">:: operátor</span><span class="sxs-lookup"><span data-stu-id="f8fda-193">:: operator</span></span>](namespace-alias-qualifier.md)
