---
title: Operátory související s ukazateli – C# reference
description: Přečtěte C# si o operátorech, které můžete použít při práci s ukazateli.
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
ms.openlocfilehash: 830aef8546191df3df4a70e350ba561367a9e474
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512358"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="4bd8c-103">Operátory související s ukazateli (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="4bd8c-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="4bd8c-104">Pro práci s ukazateli můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="4bd8c-105">Unární operátor ( [ Address-of):prozískáníadresy`&` ](#address-of-operator-) proměnné</span><span class="sxs-lookup"><span data-stu-id="4bd8c-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="4bd8c-106">Unární operátor ( [ indirekceukazatele):prozískáníproměnné,nakterouodkazuje`*` ](#pointer-indirection-operator-) ukazatel</span><span class="sxs-lookup"><span data-stu-id="4bd8c-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="4bd8c-107">Operátory [(přístup ke členům) a (přístup k prvkům) `->` ](#pointer-member-access-operator--) [ `[]` ](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="4bd8c-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="4bd8c-108">Aritmetické [ `+`operátory `-`,, `++`a`--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="4bd8c-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="4bd8c-109">Operátory [ `==`porovnání ,`!=`, `<` ,,a`<=` `>``>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="4bd8c-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="4bd8c-110">Informace o typech ukazatelů naleznete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4bd8c-111">Jakákoli operace s ukazateli vyžaduje nezabezpečený kontext. [](../keywords/unsafe.md)</span><span class="sxs-lookup"><span data-stu-id="4bd8c-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="4bd8c-112">Kód, který obsahuje nebezpečné bloky, musí být zkompilován s [`-unsafe`](../compiler-options/unsafe-compiler-option.md) možností kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-"></a><span data-ttu-id="4bd8c-113">Address-of – operátor&amp;</span><span class="sxs-lookup"><span data-stu-id="4bd8c-113">Address-of operator &amp;</span></span>

<span data-ttu-id="4bd8c-114">Unární `&` operátor vrátí adresu svého operandu:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

<span data-ttu-id="4bd8c-115">Operandem `&` operátoru musí být pevná proměnná.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="4bd8c-116">*Pevné* proměnné jsou proměnné, které jsou umístěny v umístěních úložiště, která nejsou ovlivněna operací [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="4bd8c-117">V předchozím příkladu je místní proměnná `number` pevnou proměnnou, protože se nachází v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="4bd8c-118">Proměnné, které jsou umístěné v umístění úložiště, které může být ovlivněno systémem uvolňování paměti (například přemístěné) , se nazývají pohyblivé proměnné.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="4bd8c-119">V příkladech pohyblivých proměnných jsou pole objektů a prvky pole.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="4bd8c-120">Adresu pohyblivé proměnné můžete získat, pokud "opravíte" nebo "PIN", pomocí příkazu [fixed](../keywords/fixed-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="4bd8c-120">You can get the address of a movable variable if you "fix", or "pin", it with the [fixed](../keywords/fixed-statement.md) statement.</span></span> <span data-ttu-id="4bd8c-121">Získaná adresa je platná pouze po dobu trvání `fixed` bloku příkazu.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-121">The obtained address is valid only for the duration of the `fixed` statement block.</span></span> <span data-ttu-id="4bd8c-122">Následující příklad ukazuje, jak použít `fixed` příkaz `&` a operátor:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-122">The following example shows how to use the `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="4bd8c-123">Nemůžete získat adresu konstanty nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="4bd8c-124">Další informace o pevných a pohyblivých proměnných naleznete v části [pevné a mobilní](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) proměnné [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="4bd8c-125">Binární `&` operátor vypočítá [logický a](boolean-logical-operators.md#logical-and-operator-) jeho logický operandy nebo bitovou logickou hodnotu [a](bitwise-and-shift-operators.md#logical-and-operator-) její celočíselné operandy.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="4bd8c-126">Operátor dereference ukazatele \*</span><span class="sxs-lookup"><span data-stu-id="4bd8c-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="4bd8c-127">Operátor `*` dereference unárního ukazatele získá proměnnou, do které se operandy vykáže.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="4bd8c-128">Označuje se také jako operátor odkázání.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="4bd8c-129">Operand `*` operátoru musí být typu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="4bd8c-130">`*` Operátor nelze použít na výraz typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="4bd8c-131">Binární `*` operátor vypočítá [součin](arithmetic-operators.md#multiplication-operator-) svých číselných operandů.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="4bd8c-132">Operátor přístupu členů ukazatele-></span><span class="sxs-lookup"><span data-stu-id="4bd8c-132">Pointer member access operator -></span></span>

<span data-ttu-id="4bd8c-133">Operátor `->` kombinuje [nepřímý odkaz na ukazatele](#pointer-indirection-operator-) a [přístup ke členu](member-access-operators.md#member-access-operator-).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="4bd8c-134">To znamená, že `x` Pokud je ukazatel typu `T*` a `y` je přístupným členem `T`, výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="4bd8c-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="4bd8c-135">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="4bd8c-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="4bd8c-136">Následující příklad ukazuje použití `->` operátoru:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="4bd8c-137">`->` Operátor nelze použít na výraz typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="4bd8c-138">Operátor přístupu k elementu ukazatele []</span><span class="sxs-lookup"><span data-stu-id="4bd8c-138">Pointer element access operator []</span></span>

<span data-ttu-id="4bd8c-139">Pro výraz `p` typu ukazatele je přístup k elementu formuláře `p[n]` vyhodnocen jako `*(p + n)`, kde `n` musí být typu implicitně převoditelný na `int`, `uint`, `long`nebo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="4bd8c-140">Informace o chování `+` operátoru s ukazateli naleznete v části [sčítání nebo odčítání celočíselné hodnoty nebo z ukazatele na ukazatel](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .</span><span class="sxs-lookup"><span data-stu-id="4bd8c-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="4bd8c-141">Následující příklad ukazuje, jak přistupovat k prvkům pole s ukazatelem a `[]` operátorem:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="4bd8c-142">V příkladu se pomocí [ `stackalloc` operátoru](stackalloc.md) přidělí blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-142">The example uses the [`stackalloc` operator](stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="4bd8c-143">Operátor přístupu elementu ukazatele nekontroluje chyby mimo hranice.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="4bd8c-144">Nemůžete `[]` použít pro přístup k prvku ukazatele s výrazem `void*`typu.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="4bd8c-145">`[]` Operátor můžete použít také pro [prvek pole nebo pro přístup k indexeru](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="4bd8c-146">Aritmetické operátory ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="4bd8c-147">S ukazateli můžete provádět následující aritmetické operace:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="4bd8c-148">Přidat nebo odečíst celočíselnou hodnotu do nebo z ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="4bd8c-149">Odečíst dva ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-149">Subtract two pointers</span></span>
- <span data-ttu-id="4bd8c-150">Zvýšení nebo snížení ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="4bd8c-151">Tyto operace nelze provést s ukazateli typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="4bd8c-152">Informace o podporovaných aritmetických operacích s číselnými typy naleznete v tématu [aritmetické operátory](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="4bd8c-153">Sčítání nebo odečítání celočíselné hodnoty do nebo z ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="4bd8c-154">Pro ukazatel `p` typu `long` `int` `ulong` `uint`a výraz `n` typu implicitně převoditelné na,, nebo sčítání a odčítání jsou definovány takto: `T*`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="4bd8c-155">Oba `p + n` výrazy `n + p` a vytvoří ukazatel typu `T*` , který je `p`výsledkem přidání `n * sizeof(T)` na adresu danou adresou.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="4bd8c-156">Výraz vytvoří ukazatel typu `T*` , který je `n * sizeof(T)` výsledkem odečtení od adresy uvedené `p`v. `p - n`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="4bd8c-157">Operátor získá velikost typu v bajtech. [ `sizeof` ](sizeof.md)</span><span class="sxs-lookup"><span data-stu-id="4bd8c-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="4bd8c-158">Následující příklad ukazuje použití `+` operátoru s ukazatelem:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="4bd8c-159">Odečtení ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-159">Pointer subtraction</span></span>

<span data-ttu-id="4bd8c-160">`p1` Pro dva ukazatele a `p2` typ `T*`je `p1 - p2` `p1` výsledkemvýrazu`p2` rozdíl mezi adresami předanými a dělenou. `sizeof(T)`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="4bd8c-161">Typ výsledku je `long`.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-161">The type of the result is `long`.</span></span> <span data-ttu-id="4bd8c-162">To znamená, `p1 - p2` že je vypočítávána jako. `((long)(p1) - (long)(p2)) / sizeof(T)`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="4bd8c-163">Následující příklad ukazuje odčítání ukazatele:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="4bd8c-164">Zvýšení a snížení ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-164">Pointer increment and decrement</span></span>

<span data-ttu-id="4bd8c-165">Operátor přírůstku přidá hodnotu 1 k operandu ukazatele. [](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) `++`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="4bd8c-166">Operátor snížení odečte 1 od jeho operandu ukazatele. [](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) `--`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="4bd8c-167">Oba operátory jsou podporovány ve dvou formulářích: přípona`p++` ( `p--`a) a předpona `--p`(`++p` a).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="4bd8c-168">Výsledek `p++` a `p--` je hodnota `p` *před* operací.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="4bd8c-169">Výsledek `++p` a `--p` je hodnota `p` *po* operaci.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="4bd8c-170">Následující příklad demonstruje chování obou operátorů přípony i prefixu:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="4bd8c-171">Operátory porovnání ukazatelů</span><span class="sxs-lookup"><span data-stu-id="4bd8c-171">Pointer comparison operators</span></span>

<span data-ttu-id="4bd8c-172">`==` `void*`Operátory ,`!=` ,`>`,, a`<=`můžete použít k porovnání operandů libovolného typu ukazatele, včetně. `<` `>=`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="4bd8c-173">Tyto operátory porovnávají adresy zadané dvěma operandy, jako by šlo o celá čísla bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="4bd8c-174">Informace o chování těchto operátorů pro operandy jiných typů naleznete v článcích [operátory rovnosti](equality-operators.md) a [operátory porovnání](comparison-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="4bd8c-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="4bd8c-175">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="4bd8c-175">Operator precedence</span></span>

<span data-ttu-id="4bd8c-176">Následující seznam uvádí operátory související s ukazateli počínaje od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="4bd8c-177">Operátory `x++` přírůstku `x--` a snížení přípony `->` a `[]` operátory a</span><span class="sxs-lookup"><span data-stu-id="4bd8c-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="4bd8c-178">Operátory `++x` přírůstku `--x` a snížení předpony `*` a `&` operátory a</span><span class="sxs-lookup"><span data-stu-id="4bd8c-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="4bd8c-179">`+` Doplňková `-` a operátor</span><span class="sxs-lookup"><span data-stu-id="4bd8c-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="4bd8c-180">Operátory `<`porovnání `>`, ,a`<=` `>=`</span><span class="sxs-lookup"><span data-stu-id="4bd8c-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="4bd8c-181">Rovnost `==` a `!=` operátory</span><span class="sxs-lookup"><span data-stu-id="4bd8c-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="4bd8c-182">Použijte závorky, `()`Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="4bd8c-183">Úplný seznam C# operátorů seřazených podle priority úrovně naleznete v tématu [ C# operátory](index.md).</span><span class="sxs-lookup"><span data-stu-id="4bd8c-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4bd8c-184">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="4bd8c-184">Operator overloadability</span></span>

<span data-ttu-id="4bd8c-185">Uživatelsky definovaný typ nemůže `&`přetížit operátory související s ukazatelem `->`, `*`, a `[]`.</span><span class="sxs-lookup"><span data-stu-id="4bd8c-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4bd8c-186">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4bd8c-186">C# language specification</span></span>

<span data-ttu-id="4bd8c-187">Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4bd8c-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4bd8c-188">Pevné a mobilní proměnné</span><span class="sxs-lookup"><span data-stu-id="4bd8c-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="4bd8c-189">Operátor address-of</span><span class="sxs-lookup"><span data-stu-id="4bd8c-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="4bd8c-190">Indirekce ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="4bd8c-191">Přístup ke členu ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="4bd8c-192">Přístup k prvku ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="4bd8c-193">Aritmetický ukazatel</span><span class="sxs-lookup"><span data-stu-id="4bd8c-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="4bd8c-194">Zvýšení a snížení ukazatele</span><span class="sxs-lookup"><span data-stu-id="4bd8c-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="4bd8c-195">Porovnání ukazatelů</span><span class="sxs-lookup"><span data-stu-id="4bd8c-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="4bd8c-196">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bd8c-196">See also</span></span>

- [<span data-ttu-id="4bd8c-197">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="4bd8c-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4bd8c-198">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4bd8c-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="4bd8c-199">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="4bd8c-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="4bd8c-200">UNSAFE – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="4bd8c-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="4bd8c-201">klíčové slovo fixed</span><span class="sxs-lookup"><span data-stu-id="4bd8c-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="4bd8c-202">stackalloc – operátor</span><span class="sxs-lookup"><span data-stu-id="4bd8c-202">stackalloc operator</span></span>](stackalloc.md)
- [<span data-ttu-id="4bd8c-203">sizeof – operátor</span><span class="sxs-lookup"><span data-stu-id="4bd8c-203">sizeof operator</span></span>](sizeof.md)
