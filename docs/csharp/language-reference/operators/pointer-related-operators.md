---
title: Ukazatel související operators – C# odkaz
description: Další informace o C# operátory, které můžete použít při práci s ukazateli.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 012e4fe9b8ee49f3b6b7240ac4ccb21dba70a8a9
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882659"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="677d9-103">Ukazatel související s operátory (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="677d9-103">Pointer related operators (C# Reference)</span></span>

<span data-ttu-id="677d9-104">Práce s ukazateli můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="677d9-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="677d9-105">Unární [ `&` (adresa of)](#address-of-operator-) operátor: při získávání adresy proměnné</span><span class="sxs-lookup"><span data-stu-id="677d9-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="677d9-106">Unární [ `*` (dereferenci ukazatele)](#pointer-indirection-operator-) operátor: získání proměnné, na kterou odkazuje ukazatel</span><span class="sxs-lookup"><span data-stu-id="677d9-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="677d9-107">[ `->` (Přístup ke členu)](#pointer-member-access-operator--) a [ `[]` (přístup k prvkům)](#pointer-element-access-operator-) operátory</span><span class="sxs-lookup"><span data-stu-id="677d9-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="677d9-108">Aritmetické operátory [ `+`, `-`, `++`, a `--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="677d9-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="677d9-109">Operátory porovnání [ `==`, `!=`, `<`, `>`, `<=`, a `>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="677d9-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="677d9-110">Informace o typy ukazatelů, naleznete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="677d9-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="677d9-111">Všechny operace s ukazateli vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="677d9-111">Any operation with pointers requires [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="677d9-112">Kód, který obsahuje nebezpečné bloky musí být kompilována s [ `-unsafe` ](../compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="677d9-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><span data-ttu-id="677d9-113">Operátor address-of &amp;</span><span class="sxs-lookup"><span data-stu-id="677d9-113">Address-of operator &amp;</span></span>

<span data-ttu-id="677d9-114">Unární `&` operátor vrátí adresu svého operandu:</span><span class="sxs-lookup"><span data-stu-id="677d9-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

<span data-ttu-id="677d9-115">Operand `&` operator musí být pevná proměnná.</span><span class="sxs-lookup"><span data-stu-id="677d9-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="677d9-116">*Oprava* proměnné jsou proměnné, které se nacházejí v umístění úložiště, které operace nemá vliv [systému uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="677d9-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="677d9-117">V předchozím příkladu, místní proměnná `number` je pevná proměnná, protože se nachází v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="677d9-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="677d9-118">Proměnné, které se nacházejí v umístění úložiště, které mohou být ovlivněny systému uvolňování paměti (například přemístění) se nazývají *přesouvatelný* proměnné.</span><span class="sxs-lookup"><span data-stu-id="677d9-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="677d9-119">Pole objektů a prvky pole jsou příkladem přesouvatelný proměnné.</span><span class="sxs-lookup"><span data-stu-id="677d9-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="677d9-120">Pokud "Opravit" nebo "připnout", můžete získat adresu přesouvatelný proměnné s [oprava](../keywords/fixed-statement.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="677d9-120">You can get the address of a movable variable if you "fix", or "pin", it with the [fixed](../keywords/fixed-statement.md) statement.</span></span> <span data-ttu-id="677d9-121">Získané adresa je platná jenom po dobu trvání `fixed` blok příkazů.</span><span class="sxs-lookup"><span data-stu-id="677d9-121">The obtained address is valid only for the duration of the `fixed` statement block.</span></span> <span data-ttu-id="677d9-122">Následující příklad ukazuje způsob použití `fixed` příkazu a `&` operátor:</span><span class="sxs-lookup"><span data-stu-id="677d9-122">The following example shows how to use the `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="677d9-123">Nelze získat adresu konstanta nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="677d9-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="677d9-124">Další informace o pevné a přesouvatelný proměnných najdete v tématu [Fixed a přesunutelný proměnné](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="677d9-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="677d9-125">Binární soubor `&` operátor výpočetní prostředí [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) z operandů logická nebo [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) z operandů integrální.</span><span class="sxs-lookup"><span data-stu-id="677d9-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="677d9-126">Operátor dereference ukazatele \*</span><span class="sxs-lookup"><span data-stu-id="677d9-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="677d9-127">Unární operátor dereference ukazatele `*` získá proměnné, na kterou operand ukazuje.</span><span class="sxs-lookup"><span data-stu-id="677d9-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="677d9-128">Je také známý jako operátor zrušení odkazu.</span><span class="sxs-lookup"><span data-stu-id="677d9-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="677d9-129">Operand `*` operator musí být typu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="677d9-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="677d9-130">Nelze použít `*` operátoru ve výrazu typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="677d9-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="677d9-131">Binární soubor `*` operátor výpočetní prostředí [produktu](arithmetic-operators.md#multiplication-operator-) z operandů číselná.</span><span class="sxs-lookup"><span data-stu-id="677d9-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="677d9-132">Operátor přístupu členů ukazatel -></span><span class="sxs-lookup"><span data-stu-id="677d9-132">Pointer member access operator -></span></span>

<span data-ttu-id="677d9-133">`->` Operátor kombinuje [dereferenci ukazatele](#pointer-indirection-operator-) a [přístup ke členu](member-access-operators.md#member-access-operator-).</span><span class="sxs-lookup"><span data-stu-id="677d9-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="677d9-134">To znamená pokud `x` je ukazatel typu `T*` a `y` je přístupný člen `T`, výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="677d9-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="677d9-135">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="677d9-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="677d9-136">Následující příklad ukazuje použití `->` operátor:</span><span class="sxs-lookup"><span data-stu-id="677d9-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="677d9-137">Nelze použít `->` operátoru ve výrazu typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="677d9-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="677d9-138">Operator []. přístup k elementu ukazatele</span><span class="sxs-lookup"><span data-stu-id="677d9-138">Pointer element access operator []</span></span>

<span data-ttu-id="677d9-139">Pro výraz `p` typu ukazatel, ukazatel přístup k prvkům ve tvaru `p[n]` se vyhodnotí jako `*(p + n)`, kde `n` musí být implicitně převeditelný na typu `int`, `uint`, `long`, nebo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="677d9-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="677d9-140">Informace o chování `+` operátor s ukazateli, najdete v článku [sčítání a odčítání celočíselnou hodnotu na nebo z ukazatele na](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) oddílu.</span><span class="sxs-lookup"><span data-stu-id="677d9-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="677d9-141">Následující příklad ukazuje, jak přistupovat k prvkům pole pomocí ukazatele a `[]` operátor:</span><span class="sxs-lookup"><span data-stu-id="677d9-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="677d9-142">V příkladu se používá [ `stackalloc` operátor](../keywords/stackalloc.md) přidělení bloku paměti na zásobníku.</span><span class="sxs-lookup"><span data-stu-id="677d9-142">The example uses the [`stackalloc` operator](../keywords/stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="677d9-143">Operátor přístupu k elementu ukazatel není celočíselných vyhledávat chyby.</span><span class="sxs-lookup"><span data-stu-id="677d9-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="677d9-144">Nemůžete použít `[]` pro přístup k prvkům ukazatel se výraz typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="677d9-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="677d9-145">Můžete také použít `[]` operátor pro [pole přístup k elementu nebo indexeru](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="677d9-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="677d9-146">Aritmetické operátory ukazatele</span><span class="sxs-lookup"><span data-stu-id="677d9-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="677d9-147">Můžete provádět následující aritmetických operací s ukazatele:</span><span class="sxs-lookup"><span data-stu-id="677d9-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="677d9-148">Můžete přidávat nebo odebírat integrální hodnotu na nebo z ukazatele na</span><span class="sxs-lookup"><span data-stu-id="677d9-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="677d9-149">Odečtení dvou ukazatelů</span><span class="sxs-lookup"><span data-stu-id="677d9-149">Subtract two pointers</span></span>
- <span data-ttu-id="677d9-150">Zvýšení nebo snížení ukazatel</span><span class="sxs-lookup"><span data-stu-id="677d9-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="677d9-151">Nelze provádět tyto operace s odkazy typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="677d9-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="677d9-152">Informace o podporovaných aritmetických operací s číselnými typy najdete v tématu [aritmetické operátory](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="677d9-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="677d9-153">Sčítání a odčítání celočíselnou hodnotu na nebo z ukazatele na</span><span class="sxs-lookup"><span data-stu-id="677d9-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="677d9-154">Ukazatele `p` typu `T*` a výraz `n` implicitně převést na typ `int`, `uint`, `long`, nebo `ulong`, sčítání a odčítání jsou definovány takto:</span><span class="sxs-lookup"><span data-stu-id="677d9-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="677d9-155">Obě `p + n` a `n + p` výrazy vytvořit ukazatel typu `T*` , která je výsledkem sečtení `n * sizeof(T)` adresu uvedenou ve `p`.</span><span class="sxs-lookup"><span data-stu-id="677d9-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="677d9-156">`p - n` Výraz vytvoří ukazatel typu `T*` , že výsledky daných `n * sizeof(T)` z adresy poskytnuté `p`.</span><span class="sxs-lookup"><span data-stu-id="677d9-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="677d9-157">[ `sizeof` Operátor](../keywords/sizeof.md) získá velikost typu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="677d9-157">The [`sizeof` operator](../keywords/sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="677d9-158">Následující příklad ukazuje použití `+` operátorem pomocí ukazatele:</span><span class="sxs-lookup"><span data-stu-id="677d9-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="677d9-159">Odečtení ukazatele</span><span class="sxs-lookup"><span data-stu-id="677d9-159">Pointer subtraction</span></span>

<span data-ttu-id="677d9-160">Pro dva ukazatele `p1` a `p2` typu `T*`, výraz `p1 - p2` tvoří rozdíl mezi adresami zadanými `p1` a `p2` dělený `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="677d9-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="677d9-161">Typ výsledku je `long`.</span><span class="sxs-lookup"><span data-stu-id="677d9-161">The type of the result is `long`.</span></span> <span data-ttu-id="677d9-162">To znamená `p1 - p2` je vypočítán jako `((long)(p1) - (long)(p2)) / sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="677d9-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="677d9-163">Následující příklad ukazuje odečtení ukazatele:</span><span class="sxs-lookup"><span data-stu-id="677d9-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="677d9-164">Ukazatel přírůstek a snížení</span><span class="sxs-lookup"><span data-stu-id="677d9-164">Pointer increment and decrement</span></span>

<span data-ttu-id="677d9-165">`++` Operátoru Inkrementace [přidá](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 operand ukazatel.</span><span class="sxs-lookup"><span data-stu-id="677d9-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="677d9-166">`--` Operátor dekrementace [odečte](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 z jeho operand ukazatele.</span><span class="sxs-lookup"><span data-stu-id="677d9-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="677d9-167">Oba operátory jsou podporovány ve dvou formách: přípony (`p++` a `p--`) a předpony (`++p` a `--p`).</span><span class="sxs-lookup"><span data-stu-id="677d9-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="677d9-168">Výsledek `p++` a `p--` je hodnota `p` *před* operaci.</span><span class="sxs-lookup"><span data-stu-id="677d9-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="677d9-169">Výsledek `++p` a `--p` je hodnota `p` *po* operaci.</span><span class="sxs-lookup"><span data-stu-id="677d9-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="677d9-170">Následující příklad ukazuje chování operátory zvýšení přípony a předpony:</span><span class="sxs-lookup"><span data-stu-id="677d9-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](~/samples/snippets/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="677d9-171">Operátory porovnání ukazatele</span><span class="sxs-lookup"><span data-stu-id="677d9-171">Pointer comparison operators</span></span>

<span data-ttu-id="677d9-172">Můžete použít `==`, `!=`, `<`, `>`, `<=`, a `>=` operátory porovnání operandy libovolný typ ukazatele, včetně `void*`.</span><span class="sxs-lookup"><span data-stu-id="677d9-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="677d9-173">Tyto operátory porovnávají adresy poskytnuté dva operandy, jako by byly celých čísel bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="677d9-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="677d9-174">Informace o chování těchto operátorů pro operandy jiných typů, najdete v článku [operátory rovnosti](equality-operators.md) a [operátory porovnání](comparison-operators.md) článků.</span><span class="sxs-lookup"><span data-stu-id="677d9-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="677d9-175">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="677d9-175">Operator precedence</span></span>

<span data-ttu-id="677d9-176">Následující ukazatel seznamu objednávek související s operátory od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="677d9-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="677d9-177">Zvýšení příponového operátora `x++` a dekrementace `x--` operátory a `->` a `[]` operátory</span><span class="sxs-lookup"><span data-stu-id="677d9-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="677d9-178">Předponového `++x` a dekrementace `--x` operátory a `&` a `*` operátory</span><span class="sxs-lookup"><span data-stu-id="677d9-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="677d9-179">Additive `+` a `-` operátory</span><span class="sxs-lookup"><span data-stu-id="677d9-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="677d9-180">Porovnání `<`, `>`, `<=`, a `>=` operátory</span><span class="sxs-lookup"><span data-stu-id="677d9-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="677d9-181">Rovnost `==` a `!=` operátory</span><span class="sxs-lookup"><span data-stu-id="677d9-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="677d9-182">Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů.</span><span class="sxs-lookup"><span data-stu-id="677d9-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="677d9-183">Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="677d9-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="677d9-184">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="677d9-184">Operator overloadability</span></span>

<span data-ttu-id="677d9-185">Uživatelem definovaný typ nejde přetížit ukazatel související s operátory `&`, `*`, `->`, a `[]`.</span><span class="sxs-lookup"><span data-stu-id="677d9-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="677d9-186">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="677d9-186">C# language specification</span></span>

<span data-ttu-id="677d9-187">Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="677d9-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="677d9-188">Oprava a přesunutelný proměnné</span><span class="sxs-lookup"><span data-stu-id="677d9-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="677d9-189">Operátor address-of</span><span class="sxs-lookup"><span data-stu-id="677d9-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="677d9-190">Dereferenci ukazatele</span><span class="sxs-lookup"><span data-stu-id="677d9-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="677d9-191">Přístupu k členovi</span><span class="sxs-lookup"><span data-stu-id="677d9-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="677d9-192">Přístup k prvkům ukazatele</span><span class="sxs-lookup"><span data-stu-id="677d9-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="677d9-193">Aritmetika ukazatele</span><span class="sxs-lookup"><span data-stu-id="677d9-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="677d9-194">Ukazatel přírůstek a snížení</span><span class="sxs-lookup"><span data-stu-id="677d9-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="677d9-195">Porovnání ukazatelů</span><span class="sxs-lookup"><span data-stu-id="677d9-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="677d9-196">Viz také:</span><span class="sxs-lookup"><span data-stu-id="677d9-196">See also</span></span>

- [<span data-ttu-id="677d9-197">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="677d9-197">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="677d9-198">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="677d9-198">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="677d9-199">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="677d9-199">C# Operators</span></span>](index.md)
- [<span data-ttu-id="677d9-200">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="677d9-200">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="677d9-201">`unsafe` Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="677d9-201">`unsafe` keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="677d9-202">`fixed` Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="677d9-202">`fixed` keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="677d9-203">`stackalloc` – Operátor</span><span class="sxs-lookup"><span data-stu-id="677d9-203">`stackalloc` operator</span></span>](../keywords/stackalloc.md)
- [<span data-ttu-id="677d9-204">`sizeof` – Operátor</span><span class="sxs-lookup"><span data-stu-id="677d9-204">`sizeof` operator</span></span>](../keywords/sizeof.md)
