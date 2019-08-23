---
title: Operátory přístupu členů – C# referenční informace
description: Další informace C# o operátorech, které lze použít pro přístup ke členům typu.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: 5ff5e68fbce320076e6d18e9e139b418a15bba77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924645"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="f2192-103">Operátory přístupu členů (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="f2192-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="f2192-104">Při přístupu k členu typu můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="f2192-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="f2192-105">(přístup ke členu): přístup ke členu oboru názvů nebo typu [ `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="f2192-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="f2192-106">[(element pole nebo přístup indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="f2192-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="f2192-107">[a (podmíněnéoperátoryshodnotounull):kprovedeníoperacepřístupučlenaneboelementupouzevpřípadě,žeoperandjenenulový`?[]` `?.` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="f2192-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="f2192-108">(vyvolání): pro volání metody, která je k dispozici, nebo vyvolání delegáta [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="f2192-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="f2192-109">Operátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="f2192-109">Member access operator .</span></span>

<span data-ttu-id="f2192-110">`.` Token použijete pro přístup ke členu oboru názvů nebo typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="f2192-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="f2192-111">Použijte `.` pro přístup k vnořenému oboru názvů v rámci oboru názvů, jak ukazuje následující [ `using` ](../keywords/using-directive.md) příklad direktivy:</span><span class="sxs-lookup"><span data-stu-id="f2192-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="f2192-112">Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f2192-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="f2192-113">Použijte směrnici pro použití kvalifikovaných názvů jako nepovinné. [ `using` ](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="f2192-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="f2192-114">Použijte `.` pro přístup ke [členům typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="f2192-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="f2192-115">Můžete také použít `.` pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f2192-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="f2192-116">Operátor indexer []</span><span class="sxs-lookup"><span data-stu-id="f2192-116">Indexer operator []</span></span>

<span data-ttu-id="f2192-117">Hranaté závorky `[]`se obvykle používají pro přístup k objektům Array, indexer nebo Pointer.</span><span class="sxs-lookup"><span data-stu-id="f2192-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="f2192-118">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="f2192-118">Array access</span></span>

<span data-ttu-id="f2192-119">Následující příklad ukazuje, jak získat přístup k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="f2192-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="f2192-120">Pokud je index pole mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f2192-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="f2192-121">Jak ukazuje předchozí příklad, je také možné použít hranaté závorky, pokud deklarujete typ pole nebo instanci pole instance.</span><span class="sxs-lookup"><span data-stu-id="f2192-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="f2192-122">Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2192-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="f2192-123">Přístup indexeru</span><span class="sxs-lookup"><span data-stu-id="f2192-123">Indexer access</span></span>

<span data-ttu-id="f2192-124">Následující příklad používá typ .NET <xref:System.Collections.Generic.Dictionary%602> k demonstraci přístupu indexeru:</span><span class="sxs-lookup"><span data-stu-id="f2192-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="f2192-125">Indexery umožňují indexovat instance uživatelsky definovaného typu podobným způsobem jako indexování pole.</span><span class="sxs-lookup"><span data-stu-id="f2192-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="f2192-126">Na rozdíl od indexů pole, který musí být celé číslo, argumenty indexeru lze deklarovat jako libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="f2192-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="f2192-127">Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2192-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="f2192-128">Další použití []</span><span class="sxs-lookup"><span data-stu-id="f2192-128">Other usages of []</span></span>

<span data-ttu-id="f2192-129">Informace o přístupu k prvkům ukazatele naleznete v části [operátor přístupu k prvku ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku o [operátorech souvisejících s ukazateli](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="f2192-129">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="f2192-130">Pomocí hranatých závorek určíte [atributy](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="f2192-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="f2192-131">Podmíněné operátory s hodnotou null?.</span><span class="sxs-lookup"><span data-stu-id="f2192-131">Null-conditional operators ?.</span></span> <span data-ttu-id="f2192-132">ani? []</span><span class="sxs-lookup"><span data-stu-id="f2192-132">and ?[]</span></span>

<span data-ttu-id="f2192-133">K dispozici v 6 nebo novějším, operátor s hodnotou null aplikuje na `?.`operand přístup člena, `?[]`nebo element, operace na jeho operand pouze v C# případě, že se tento operand vyhodnocuje jako nenulový.</span><span class="sxs-lookup"><span data-stu-id="f2192-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="f2192-134">Pokud je operand vyhodnocen `null`jako, výsledek použití operátoru je. `null`</span><span class="sxs-lookup"><span data-stu-id="f2192-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="f2192-135">Operátor `?.` přístupu k podmíněnému členu s hodnotou null je také označován jako Elvis operátor.</span><span class="sxs-lookup"><span data-stu-id="f2192-135">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="f2192-136">Operátory podmíněné hodnotou null jsou krátkodobé okruhy.</span><span class="sxs-lookup"><span data-stu-id="f2192-136">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="f2192-137">To znamená, že pokud se vrátí `null`jedna operace v řetězci podmíněného člena nebo operace přístupu k prvkům, zbytek řetězu se nespustí.</span><span class="sxs-lookup"><span data-stu-id="f2192-137">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="f2192-138">V následujícím `B` příkladu není vyhodnocena, pokud `A` `null` je vyhodnocena `C` jako a není vyhodnocena v případě `null`, že `A` nebo `B` je vyhodnocena jako:</span><span class="sxs-lookup"><span data-stu-id="f2192-138">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="f2192-139">Následující příklad ukazuje použití `?.` operátorů a: `?[]`</span><span class="sxs-lookup"><span data-stu-id="f2192-139">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="f2192-140">Předchozí příklad také ukazuje použití operátoru nulového [slučování](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f2192-140">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="f2192-141">Operátor pro sjednocení hodnoty null můžete použít k poskytnutí alternativního výrazu pro vyhodnocení pro případ, že je `null`výsledkem operace podmíněného zpracování hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="f2192-141">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="f2192-142">Volání delegáta bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="f2192-142">Thread-safe delegate invocation</span></span>

<span data-ttu-id="f2192-143">Použijte operátor ke kontrole, zda delegát není null a vyvolá ho v bezpečném režimu (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód: `?.`</span><span class="sxs-lookup"><span data-stu-id="f2192-143">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="f2192-144">Tento kód je ekvivalentní následujícímu kódu, který byste použili v C# 5 nebo starších verzích:</span><span class="sxs-lookup"><span data-stu-id="f2192-144">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="f2192-145">Operátor vyvolání ()</span><span class="sxs-lookup"><span data-stu-id="f2192-145">Invocation operator ()</span></span>

<span data-ttu-id="f2192-146">Použijte závorky, `()`, pro volání [metody](../../programming-guide/classes-and-structs/methods.md) nebo vyvolání delegáta [](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2192-146">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="f2192-147">Následující příklad ukazuje, jak zavolat metodu s argumenty nebo bez argumentů a vyvolat delegáta:</span><span class="sxs-lookup"><span data-stu-id="f2192-147">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="f2192-148">Při vyvolání [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s [`new`](new-operator.md) operátorem můžete také použít závorky.</span><span class="sxs-lookup"><span data-stu-id="f2192-148">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="f2192-149">Další použití pro ()</span><span class="sxs-lookup"><span data-stu-id="f2192-149">Other usages of ()</span></span>

<span data-ttu-id="f2192-150">Pomocí závorek můžete také upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="f2192-150">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="f2192-151">Další informace najdete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="f2192-151">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="f2192-152">[Výrazy přetypování](type-testing-and-cast.md#cast-operator-), které provádějí explicitní převody typů, používají také závorky.</span><span class="sxs-lookup"><span data-stu-id="f2192-152">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f2192-153">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="f2192-153">Operator overloadability</span></span>

<span data-ttu-id="f2192-154">Operátory `.` a`()` nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="f2192-154">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="f2192-155">`[]` Operátor je také považován za operátor, který není přetížen.</span><span class="sxs-lookup"><span data-stu-id="f2192-155">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="f2192-156">Použijte [indexery](../../programming-guide/indexers/index.md) k podpoře indexování s uživatelsky definovanými typy.</span><span class="sxs-lookup"><span data-stu-id="f2192-156">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2192-157">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2192-157">C# language specification</span></span>

<span data-ttu-id="f2192-158">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="f2192-158">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f2192-159">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="f2192-159">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="f2192-160">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="f2192-160">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="f2192-161">Podmíněný operátor s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="f2192-161">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="f2192-162">Výrazy vyvolání</span><span class="sxs-lookup"><span data-stu-id="f2192-162">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="f2192-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2192-163">See also</span></span>

- [<span data-ttu-id="f2192-164">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="f2192-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f2192-165">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2192-165">C# operators</span></span>](index.md)
- [<span data-ttu-id="f2192-166">?? (operátor slučování null)</span><span class="sxs-lookup"><span data-stu-id="f2192-166">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="f2192-167">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="f2192-167">:: operator</span></span>](namespace-alias-qualifier.md)
