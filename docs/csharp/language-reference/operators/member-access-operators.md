---
title: Operátory přístupu členů a výrazy – reference jazyka C#
description: Přečtěte si o operátorech jazyka C#, které lze použít pro přístup ke členům typu.
ms.date: 04/17/2020
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
ms.openlocfilehash: 86c8cce79e447bee638e1c5c7cb2fdbc64f630f3
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595894"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="808ee-103">Operátory a výrazy přístupu členů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="808ee-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="808ee-104">Při přístupu k členu typu můžete použít následující operátory a výrazy:</span><span class="sxs-lookup"><span data-stu-id="808ee-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="808ee-105">[(přístup ke členu): přístup ke členu oboru názvů nebo typu `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="808ee-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="808ee-106">[(element pole nebo přístup indexeru): pro přístup k prvku pole nebo indexeru typu `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="808ee-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="808ee-107">[a `?[]` podmíněné operátory s hodnotou null): k provedení operace přístupu člena nebo elementu pouze v případě, že operand je `?.` ](#null-conditional-operators--and-)nenulový</span><span class="sxs-lookup"><span data-stu-id="808ee-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="808ee-108">(vyvolání): pro volání metody, která je k dispozici, nebo vyvolání delegáta [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="808ee-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="808ee-109">[(index od konce): k označení, že pozice prvku je od konce sekvence `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="808ee-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="808ee-110">(rozsah): Pokud chcete zadat rozsah indexů, které můžete použít k získání rozsahu elementů Sequence. [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="808ee-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="808ee-111">Výraz přístupu členů</span><span class="sxs-lookup"><span data-stu-id="808ee-111">Member access expression .</span></span>

<span data-ttu-id="808ee-112">`.` Token použijete pro přístup ke členu oboru názvů nebo typu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="808ee-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="808ee-113">Použijte `.` pro přístup k vnořenému oboru názvů v rámci oboru názvů, jak ukazuje následující příklad [ `using` direktivy](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="808ee-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="808ee-114">Slouží `.` k vytvoření *kvalifikovaného názvu* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="808ee-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="808ee-115">Použijte [ `using` směrnici](../keywords/using-directive.md) pro použití kvalifikovaných názvů jako nepovinné.</span><span class="sxs-lookup"><span data-stu-id="808ee-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="808ee-116">Použijte `.` pro přístup ke [členům typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="808ee-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="808ee-117">Můžete také použít `.` pro přístup k [metodě rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="808ee-118">Operátor indexer []</span><span class="sxs-lookup"><span data-stu-id="808ee-118">Indexer operator []</span></span>

<span data-ttu-id="808ee-119">Hranaté závorky `[]`se obvykle používají pro přístup k objektům Array, indexer nebo Pointer.</span><span class="sxs-lookup"><span data-stu-id="808ee-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="808ee-120">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="808ee-120">Array access</span></span>

<span data-ttu-id="808ee-121">Následující příklad ukazuje, jak získat přístup k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="808ee-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="808ee-122">Pokud je index pole mimo hranice odpovídající dimenze pole, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="808ee-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="808ee-123">Jak ukazuje předchozí příklad, je také možné použít hranaté závorky, pokud deklarujete typ pole nebo instanci pole instance.</span><span class="sxs-lookup"><span data-stu-id="808ee-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="808ee-124">Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="808ee-125">Přístup indexeru</span><span class="sxs-lookup"><span data-stu-id="808ee-125">Indexer access</span></span>

<span data-ttu-id="808ee-126">Následující příklad používá typ .NET <xref:System.Collections.Generic.Dictionary%602> k demonstraci přístupu indexeru:</span><span class="sxs-lookup"><span data-stu-id="808ee-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="808ee-127">Indexery umožňují indexovat instance uživatelsky definovaného typu podobným způsobem jako indexování pole.</span><span class="sxs-lookup"><span data-stu-id="808ee-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="808ee-128">Na rozdíl od indexů pole, který musí být celé číslo, lze parametry indexeru deklarovat jako libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="808ee-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="808ee-129">Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="808ee-130">Další použití []</span><span class="sxs-lookup"><span data-stu-id="808ee-130">Other usages of []</span></span>

<span data-ttu-id="808ee-131">Informace o přístupu k prvkům ukazatele naleznete v části [operátor přístupu k prvku ukazatele []](pointer-related-operators.md#pointer-element-access-operator-) v článku o [operátorech souvisejících s ukazateli](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="808ee-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="808ee-132">Pomocí hranatých závorek určíte [atributy](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="808ee-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="808ee-133">Podmíněné operátory s hodnotou null?.</span><span class="sxs-lookup"><span data-stu-id="808ee-133">Null-conditional operators ?.</span></span> <span data-ttu-id="808ee-134">ani? []</span><span class="sxs-lookup"><span data-stu-id="808ee-134">and ?[]</span></span>

<span data-ttu-id="808ee-135">K dispozici v C# 6 a novějším, operátor s hodnotou null [member access](#member-access-expression-)aplikuje na `?.`operand přístup člena, nebo `?[]`k [elementu](#indexer-operator-), a operaci na jeho operand pouze v případě, že je tento operand vyhodnocen jako jiný než null; v opačném případě `null`vrátí.</span><span class="sxs-lookup"><span data-stu-id="808ee-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="808ee-136">To je</span><span class="sxs-lookup"><span data-stu-id="808ee-136">That is,</span></span>

- <span data-ttu-id="808ee-137">Pokud `a` `null`se vyhodnotí jako, výsledek `a?.x` nebo `a?[x]` je `null`.</span><span class="sxs-lookup"><span data-stu-id="808ee-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="808ee-138">Pokud `a` se vyhodnotí jako jiné než null, výsledek `a?.x` nebo `a?[x]` je stejný jako výsledek `a.x` nebo `a[x]`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="808ee-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="808ee-139">Pokud `a.x` nebo `a[x]` vyvolá výjimku `a?.x` nebo `a?[x]` by vyvolala stejnou výjimku pro jinou hodnotu než null `a`.</span><span class="sxs-lookup"><span data-stu-id="808ee-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="808ee-140">Například `a` Pokud je instance pole `x` `a`, která není null a je mimo hranice, `a?[x]` by vyvolala. <xref:System.IndexOutOfRangeException></span><span class="sxs-lookup"><span data-stu-id="808ee-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="808ee-141">Operátory podmíněné hodnotou null jsou krátkodobé okruhy.</span><span class="sxs-lookup"><span data-stu-id="808ee-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="808ee-142">To znamená, že pokud se vrátí `null`jedna operace v řetězci podmíněného člena nebo operace přístupu k prvkům, zbytek řetězu se nespustí.</span><span class="sxs-lookup"><span data-stu-id="808ee-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="808ee-143">V `B` následujícím příkladu není vyhodnocena, pokud `A` je vyhodnocena jako `null` a `C` není vyhodnocena v případě, že `A` nebo `B` je vyhodnocena jako: `null`</span><span class="sxs-lookup"><span data-stu-id="808ee-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="808ee-144">Následující příklad ukazuje použití operátorů `?.` a: `?[]`</span><span class="sxs-lookup"><span data-stu-id="808ee-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="808ee-145">Předchozí příklad také používá [ `??` operátor slučování null](null-coalescing-operator.md) k určení alternativního výrazu pro vyhodnocení pro případ, že je `null`výsledkem operace podmíněného zpracování hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="808ee-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="808ee-146">Pokud `a.x` nebo `a[x]` je typ `T` `a?.x` hodnoty, která není null, nebo `a?[x]` je odpovídající [typ](../builtin-types/nullable-value-types.md) `T?`hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="808ee-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="808ee-147">Pokud potřebujete výraz typu `T`, použijte operátor `??` slučování null na podmíněný výraz s hodnotou null, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="808ee-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="808ee-148">V `??` předchozím příkladu, pokud operátor nepoužíváte, se vyhodnotí `numbers?.Length < 2` `false` jako, `numbers` Pokud `null`je.</span><span class="sxs-lookup"><span data-stu-id="808ee-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="808ee-149">Operátor `?.` přístupu k podmíněnému členu s hodnotou null je také označován jako Elvis operátor.</span><span class="sxs-lookup"><span data-stu-id="808ee-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

> [!NOTE]
> <span data-ttu-id="808ee-150">V jazyce C# 8 operátory s hodnotou null vzájemně fungují s [operátorem null-striktní](null-forgiving.md) a neočekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="808ee-150">In C# 8, the null-conditional operators interacts with the [null-forgiving operator](null-forgiving.md) in an unexpected way.</span></span> <span data-ttu-id="808ee-151">Například výraz `x?.y!.z` je analyzován jako `(x?.y)!.z`.</span><span class="sxs-lookup"><span data-stu-id="808ee-151">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="808ee-152">Z důvodu této interpretace `z` je vyhodnocena `x` i `null`v případě, že je, <xref:System.NullReferenceException>což může vést k.</span><span class="sxs-lookup"><span data-stu-id="808ee-152">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="808ee-153">Volání delegáta bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="808ee-153">Thread-safe delegate invocation</span></span>

<span data-ttu-id="808ee-154">Použijte `?.` operátor ke kontrole, zda delegát není null a vyvolá ho v bezpečném režimu (například při [vyvolání události](../../../standard/events/how-to-raise-and-consume-events.md)), jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="808ee-154">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="808ee-155">Tento kód je ekvivalentní následujícímu kódu, který byste použili v C# 5 nebo starší:</span><span class="sxs-lookup"><span data-stu-id="808ee-155">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="808ee-156">To je způsob bezpečný pro přístup z více vláken, aby bylo zajištěno, `handler` že je vyvolána pouze hodnota, která není null.</span><span class="sxs-lookup"><span data-stu-id="808ee-156">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="808ee-157">Vzhledem k tomu, že instance delegátů jsou neměnné, nemůže žádné vlákno změnit `handler` hodnotu, na kterou odkazuje místní proměnná.</span><span class="sxs-lookup"><span data-stu-id="808ee-157">Because delegate instances are immutable, no thread can change the value referenced by the `handler` local variable.</span></span> <span data-ttu-id="808ee-158">Zejména pokud je kód, který je spuštěn jiným vláknem, odhlásil odběr `PropertyChanged` z události `PropertyChanged` a `null` stane `handler` se před vyvoláním, hodnota `handler` odkazovaná zůstává neovlivněno.</span><span class="sxs-lookup"><span data-stu-id="808ee-158">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the value referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="808ee-159">`?.` Operátor vyhodnocuje svůj operand na levé straně více než jednou a zaručuje, že nemůže být změněn na `null` po ověření jako nenulového typu.</span><span class="sxs-lookup"><span data-stu-id="808ee-159">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="808ee-160">Výraz vyvolání ()</span><span class="sxs-lookup"><span data-stu-id="808ee-160">Invocation expression ()</span></span>

<span data-ttu-id="808ee-161">Použijte závorky, `()`, pro volání [metody](../../programming-guide/classes-and-structs/methods.md) nebo vyvolání [delegáta](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-161">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="808ee-162">Následující příklad ukazuje, jak zavolat metodu s argumenty nebo bez argumentů a vyvolat delegáta:</span><span class="sxs-lookup"><span data-stu-id="808ee-162">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="808ee-163">Při vyvolání [konstruktoru](../../programming-guide/classes-and-structs/constructors.md) s [`new`](new-operator.md) operátorem můžete také použít závorky.</span><span class="sxs-lookup"><span data-stu-id="808ee-163">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="808ee-164">Další použití pro ()</span><span class="sxs-lookup"><span data-stu-id="808ee-164">Other usages of ()</span></span>

<span data-ttu-id="808ee-165">Pomocí závorek můžete také upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="808ee-165">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="808ee-166">Další informace naleznete v tématu [operátory jazyka C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-166">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="808ee-167">[Výrazy přetypování](type-testing-and-cast.md#cast-expression), které provádějí explicitní převody typů, používají také závorky.</span><span class="sxs-lookup"><span data-stu-id="808ee-167">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="808ee-168">Index z operátoru end ^</span><span class="sxs-lookup"><span data-stu-id="808ee-168">Index from end operator ^</span></span>

<span data-ttu-id="808ee-169">K dispozici v C# 8,0 a novějším, `^` operátor označuje pozici elementu na konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="808ee-169">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="808ee-170">Pro sekvenci délky `length` `^n` odkazuje na prvek s posunem `length - n` od začátku sekvence.</span><span class="sxs-lookup"><span data-stu-id="808ee-170">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="808ee-171">Například `^1` odkazuje na poslední prvek sekvence a `^length` odkazuje na první prvek sekvence.</span><span class="sxs-lookup"><span data-stu-id="808ee-171">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="808ee-172">Jak ukazuje předchozí příklad, výraz `^e` je <xref:System.Index?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="808ee-172">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="808ee-173">Ve výrazu `^e`je výsledek `e` nutné implicitně převést na `int`.</span><span class="sxs-lookup"><span data-stu-id="808ee-173">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="808ee-174">Můžete také použít `^` operátor s [operátorem Range](#range-operator-) a vytvořit tak rozsah indexů.</span><span class="sxs-lookup"><span data-stu-id="808ee-174">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="808ee-175">Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-175">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="808ee-176">Operátor rozsahu..</span><span class="sxs-lookup"><span data-stu-id="808ee-176">Range operator ..</span></span>

<span data-ttu-id="808ee-177">K dispozici v C# 8,0 a novějších `..` operátor určuje začátek a konec rozsahu indexů jako své operandy.</span><span class="sxs-lookup"><span data-stu-id="808ee-177">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="808ee-178">Levý operand je *Celková* začátek rozsahu.</span><span class="sxs-lookup"><span data-stu-id="808ee-178">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="808ee-179">Pravý operand je *výhradním* koncem rozsahu.</span><span class="sxs-lookup"><span data-stu-id="808ee-179">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="808ee-180">Jedním z operandů může být index od začátku nebo po konci sekvence, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="808ee-180">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="808ee-181">Jak ukazuje předchozí příklad, výraz `a..b` je <xref:System.Range?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="808ee-181">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="808ee-182">Ve výrazu `a..b`jsou výsledky `a` a `b` musí být implicitně převoditelné na `int` nebo <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="808ee-182">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="808ee-183">Pokud chcete získat rozsah otevřeného a koncového výrazu `..` , můžete vynechat kterýkoli z operandů operátoru:</span><span class="sxs-lookup"><span data-stu-id="808ee-183">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="808ee-184">`a..`je ekvivalentem`a..^0`</span><span class="sxs-lookup"><span data-stu-id="808ee-184">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="808ee-185">`..b`je ekvivalentem`0..b`</span><span class="sxs-lookup"><span data-stu-id="808ee-185">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="808ee-186">`..`je ekvivalentem`0..^0`</span><span class="sxs-lookup"><span data-stu-id="808ee-186">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="808ee-187">Další informace najdete v tématu [indexy a rozsahy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-187">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="808ee-188">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="808ee-188">Operator overloadability</span></span>

<span data-ttu-id="808ee-189">`..` Operátory `.`, `()`, `^`a nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="808ee-189">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="808ee-190">`[]` Operátor je také považován za operátor, který není přetížen.</span><span class="sxs-lookup"><span data-stu-id="808ee-190">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="808ee-191">Použijte [indexery](../../programming-guide/indexers/index.md) k podpoře indexování s uživatelsky definovanými typy.</span><span class="sxs-lookup"><span data-stu-id="808ee-191">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="808ee-192">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="808ee-192">C# language specification</span></span>

<span data-ttu-id="808ee-193">Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="808ee-193">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="808ee-194">Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="808ee-194">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="808ee-195">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="808ee-195">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="808ee-196">Podmíněný operátor s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="808ee-196">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="808ee-197">Výrazy vyvolání</span><span class="sxs-lookup"><span data-stu-id="808ee-197">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="808ee-198">Další informace o indexech a oblastech najdete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="808ee-198">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="808ee-199">Viz také</span><span class="sxs-lookup"><span data-stu-id="808ee-199">See also</span></span>

- [<span data-ttu-id="808ee-200">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="808ee-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="808ee-201">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="808ee-201">C# operators</span></span>](index.md)
- [<span data-ttu-id="808ee-202">?? (operátor slučování null)</span><span class="sxs-lookup"><span data-stu-id="808ee-202">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="808ee-203">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="808ee-203">:: operator</span></span>](namespace-alias-qualifier.md)
