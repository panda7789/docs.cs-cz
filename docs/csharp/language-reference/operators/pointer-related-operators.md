---
title: Operátory související s ukazatelem – odkaz jazyka C#
description: Další informace o operátory Jazyka C#, které můžete použít při práci s ukazateli.
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
ms.openlocfilehash: 7eb6666d10c44c342f69c7cfc763feb1b7b98c9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738606"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="85fa3-103">Operátory související s ukazatelem (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="85fa3-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="85fa3-104">Pro práci s ukazateli můžete použít následující operátory:</span><span class="sxs-lookup"><span data-stu-id="85fa3-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="85fa3-105">Unární [ `&` (adresa- of)](#address-of-operator-) operátor: získat adresu proměnné</span><span class="sxs-lookup"><span data-stu-id="85fa3-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="85fa3-106">Unární [ `*` (směrový bod)](#pointer-indirection-operator-) operátor: chcete-li získat proměnnou špičatou ukazatelem</span><span class="sxs-lookup"><span data-stu-id="85fa3-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="85fa3-107">[ `->` Operátory (přístup u členů)](#pointer-member-access-operator--) a [ `[]` (přístup k prvkům)](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="85fa3-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="85fa3-108">Aritmetické obsluze [ `+`, `-` `++`, , a`--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="85fa3-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="85fa3-109">Srovnávací operátory [ `==` `>`, `<=` `!=`, `<`, , a`>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="85fa3-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="85fa3-110">Informace o typech ukazatelů naleznete v tématu [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="85fa3-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="85fa3-111">Každá operace s ukazateli vyžaduje [nebezpečný](../keywords/unsafe.md) kontext.</span><span class="sxs-lookup"><span data-stu-id="85fa3-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="85fa3-112">Kód, který obsahuje nebezpečné bloky, [`-unsafe`](../compiler-options/unsafe-compiler-option.md) musí být zkompilován s možností kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="85fa3-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a><span data-ttu-id="85fa3-113">Adresa operátora&amp;</span><span class="sxs-lookup"><span data-stu-id="85fa3-113">Address-of operator &amp;</span></span>

<span data-ttu-id="85fa3-114">Unární `&` operátor vrátí adresu svého operandu:</span><span class="sxs-lookup"><span data-stu-id="85fa3-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

<span data-ttu-id="85fa3-115">Operand `&` provozovatele musí být pevná proměnná.</span><span class="sxs-lookup"><span data-stu-id="85fa3-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="85fa3-116">*Pevné* proměnné jsou proměnné, které se nacházejí v umístěních úložiště, které nejsou ovlivněny provozem [systému uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="85fa3-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="85fa3-117">V předchozím příkladu je `number` místní proměnná pevnou proměnnou, protože je umístěna v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="85fa3-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="85fa3-118">Proměnné, které jsou umístěny v umístěníúložiště, které mohou být ovlivněny systémem uvolňování paměti (například přemístěné) se nazývají *pohyblivé* proměnné.</span><span class="sxs-lookup"><span data-stu-id="85fa3-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="85fa3-119">Pole objektů a prvky pole jsou příklady pohyblivých proměnných.</span><span class="sxs-lookup"><span data-stu-id="85fa3-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="85fa3-120">Můžete získat adresu pohyblivé proměnné, pokud "opravit", nebo "pin", to s [ `fixed` příkazem](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="85fa3-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="85fa3-121">Získaná adresa je `fixed` platná pouze uvnitř bloku příkazu.</span><span class="sxs-lookup"><span data-stu-id="85fa3-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="85fa3-122">Následující příklad ukazuje, jak `fixed` používat `&` příkaz a operátor:</span><span class="sxs-lookup"><span data-stu-id="85fa3-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="85fa3-123">Nelze získat adresu konstanty nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="85fa3-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="85fa3-124">Další informace o pevných a pohyblivých proměnných naleznete v části [Pevné a pohyblivé proměnné](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="85fa3-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="85fa3-125">Binární `&` operátor vypočítá [logické and](boolean-logical-operators.md#logical-and-operator-) jeho logické operandy nebo [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) jeho integrální operandy.</span><span class="sxs-lookup"><span data-stu-id="85fa3-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="85fa3-126">Operátor přesměrování ukazatele \*</span><span class="sxs-lookup"><span data-stu-id="85fa3-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="85fa3-127">Unární ukazatel dereference `*` operátor získá proměnnou, na kterou jeho operand odkazuje.</span><span class="sxs-lookup"><span data-stu-id="85fa3-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="85fa3-128">Je také známý jako dereference operátor.</span><span class="sxs-lookup"><span data-stu-id="85fa3-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="85fa3-129">Operand operátoru `*` musí být typu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="85fa3-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="85fa3-130">`*` Operátor nelze použít na výraz `void*`typu .</span><span class="sxs-lookup"><span data-stu-id="85fa3-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="85fa3-131">Binární `*` operátor vypočítá [součin](arithmetic-operators.md#multiplication-operator-) jeho číselné operandy.</span><span class="sxs-lookup"><span data-stu-id="85fa3-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="85fa3-132">Operátor přístupu člena ukazatele -></span><span class="sxs-lookup"><span data-stu-id="85fa3-132">Pointer member access operator -></span></span>

<span data-ttu-id="85fa3-133">Operátor `->` kombinuje [dereference ukazatele](#pointer-indirection-operator-) a [přístup členů](member-access-operators.md#member-access-expression-).</span><span class="sxs-lookup"><span data-stu-id="85fa3-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="85fa3-134">To znamená, `x` pokud je `T*` ukazatel `y` typu a je `T`přístupný člen typu , výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="85fa3-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="85fa3-135">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="85fa3-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="85fa3-136">Následující příklad ukazuje použití operátoru: `->`</span><span class="sxs-lookup"><span data-stu-id="85fa3-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="85fa3-137">`->` Operátor nelze použít na výraz `void*`typu .</span><span class="sxs-lookup"><span data-stu-id="85fa3-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="85fa3-138">Operátor přístupu k elementu ukazatele []</span><span class="sxs-lookup"><span data-stu-id="85fa3-138">Pointer element access operator []</span></span>

<span data-ttu-id="85fa3-139">Pro výraz `p` typu ukazatele je přístup prvku ukazatele `p[n]` formuláře `*(p + n)`vyhodnocen jako `n` , kde musí `int` `uint`být typu implicitně převoditelného na , , `long`, nebo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="85fa3-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="85fa3-140">Informace o chování operátoru `+` s ukazateli naleznete v tématu Sčítání nebo [odčítání integrální hodnoty do nebo z oddílu ukazatele.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)</span><span class="sxs-lookup"><span data-stu-id="85fa3-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="85fa3-141">Následující příklad ukazuje, jak získat přístup k `[]` prvkům pole s ukazatelem a operátorem:</span><span class="sxs-lookup"><span data-stu-id="85fa3-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="85fa3-142">V předchozím příkladu [ `stackalloc` výraz](stackalloc.md) přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="85fa3-142">In the preceding example, a [`stackalloc` expression](stackalloc.md) allocates a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="85fa3-143">Operátor přístupu prvku ukazatele nekontroluje chyby mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="85fa3-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="85fa3-144">Nelze použít `[]` pro přístup k elementu `void*`ukazatele s výrazem typu .</span><span class="sxs-lookup"><span data-stu-id="85fa3-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="85fa3-145">Operátor můžete také `[]` použít pro [přístup k prvku pole nebo indexeru](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="85fa3-145">You can also use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="85fa3-146">Aritmetické operátory ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="85fa3-147">S ukazateli můžete provádět následující aritmetické operace:</span><span class="sxs-lookup"><span data-stu-id="85fa3-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="85fa3-148">Sčítání nebo odečtení integrální hodnoty k ukazateli nebo od něj</span><span class="sxs-lookup"><span data-stu-id="85fa3-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="85fa3-149">Odečtení dvou ukazatelů</span><span class="sxs-lookup"><span data-stu-id="85fa3-149">Subtract two pointers</span></span>
- <span data-ttu-id="85fa3-150">Zvýšení nebo snížení ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="85fa3-151">Tyto operace nelze provádět s `void*`ukazateli typu .</span><span class="sxs-lookup"><span data-stu-id="85fa3-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="85fa3-152">Informace o podporovaných aritmetických operacích s číselnými typy naleznete [v tématu Aritmetické operátory](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="85fa3-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="85fa3-153">Sčítání nebo odčítání integrální hodnoty do ukazatele nebo z ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="85fa3-154">Pro ukazatel `p` typu `T*` a `n` výraz typu implicitně `int`převoditelný na , `uint`, , `long`nebo `ulong`, sčítání a odčítání jsou definovány takto:</span><span class="sxs-lookup"><span data-stu-id="85fa3-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="85fa3-155">Oba `p + n` `n + p` a výrazy vytvořit `T*` ukazatel typu, `n * sizeof(T)` který je `p`výsledkem přidání na adresu danou .</span><span class="sxs-lookup"><span data-stu-id="85fa3-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="85fa3-156">Výraz `p - n` vytvoří ukazatel typu, `T*` který je výsledkem odečtení `n * sizeof(T)` `p`od adresy zadané .</span><span class="sxs-lookup"><span data-stu-id="85fa3-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="85fa3-157">[ `sizeof` Operátor](sizeof.md) získá velikost typu v bajtů.</span><span class="sxs-lookup"><span data-stu-id="85fa3-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="85fa3-158">Následující příklad ukazuje použití operátoru `+` s ukazatelem:</span><span class="sxs-lookup"><span data-stu-id="85fa3-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="85fa3-159">Odečtení ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-159">Pointer subtraction</span></span>

<span data-ttu-id="85fa3-160">Pro dva `p1` ukazatele `p2` a `T*`typu `p1 - p2` výraz vytváří rozdíl mezi adresami `p1` `p2` danými `sizeof(T)`a dělené .</span><span class="sxs-lookup"><span data-stu-id="85fa3-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="85fa3-161">Typ výsledku je `long`.</span><span class="sxs-lookup"><span data-stu-id="85fa3-161">The type of the result is `long`.</span></span> <span data-ttu-id="85fa3-162">To znamená, `p1 - p2` že `((long)(p1) - (long)(p2)) / sizeof(T)`je vypočítán jako .</span><span class="sxs-lookup"><span data-stu-id="85fa3-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="85fa3-163">Následující příklad ukazuje odčítání ukazatele:</span><span class="sxs-lookup"><span data-stu-id="85fa3-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="85fa3-164">Přírůstek a snížení ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-164">Pointer increment and decrement</span></span>

<span data-ttu-id="85fa3-165">Operátor `++` přírůstek [přidá](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do operandu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="85fa3-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="85fa3-166">Operátor `--` snížení [odečte](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 z jeho operand ukazovátku.</span><span class="sxs-lookup"><span data-stu-id="85fa3-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="85fa3-167">Oba operátory jsou podporovány ve`p++` `p--`dvou formách:`++p` `--p`postfix ( a ) a prefix ( a ).</span><span class="sxs-lookup"><span data-stu-id="85fa3-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="85fa3-168">Výsledek `p++` a `p--` je hodnota `p` *před* operací.</span><span class="sxs-lookup"><span data-stu-id="85fa3-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="85fa3-169">Výsledek `++p` a `--p` je hodnota `p` *po* operaci.</span><span class="sxs-lookup"><span data-stu-id="85fa3-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="85fa3-170">Následující příklad ukazuje chování operátorů přípony i přírůstku předpony:</span><span class="sxs-lookup"><span data-stu-id="85fa3-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="85fa3-171">Operátory porovnání ukazatelů</span><span class="sxs-lookup"><span data-stu-id="85fa3-171">Pointer comparison operators</span></span>

<span data-ttu-id="85fa3-172">Operandy `==` `!=` `<` `>` `<=`libovolného typu ukazatele, včetně `void*` `>=` .</span><span class="sxs-lookup"><span data-stu-id="85fa3-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="85fa3-173">Tito operátoři porovnávají adresy dané dvěma operandy, jako by se jednalo o nepodepsaná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="85fa3-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="85fa3-174">Informace o chování těchto operátorů pro operandy jiných typů naleznete v [článcích Operátory rovnosti](equality-operators.md) a [Operátory porovnání.](comparison-operators.md)</span><span class="sxs-lookup"><span data-stu-id="85fa3-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="85fa3-175">Priorita operátorů</span><span class="sxs-lookup"><span data-stu-id="85fa3-175">Operator precedence</span></span>

<span data-ttu-id="85fa3-176">Následující seznam seřídí operátory související s ukazatelem od nejvyšší priority k nejnižší:</span><span class="sxs-lookup"><span data-stu-id="85fa3-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="85fa3-177">Operátory přírůstek `x++` a `x--` snížení přípony a operátory `->` a `[]`</span><span class="sxs-lookup"><span data-stu-id="85fa3-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="85fa3-178">Operátory přírůstku `++x` a snížení předpony `*` a operátory a operátory `&` `--x`</span><span class="sxs-lookup"><span data-stu-id="85fa3-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="85fa3-179">Doplňkové `+` `-` látky a obsluha</span><span class="sxs-lookup"><span data-stu-id="85fa3-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="85fa3-180">Srovnání `<` `>`, `<=`, `>=` , a operátory</span><span class="sxs-lookup"><span data-stu-id="85fa3-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="85fa3-181">Rovnost `==` a `!=` provozovatelé</span><span class="sxs-lookup"><span data-stu-id="85fa3-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="85fa3-182">Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru.</span><span class="sxs-lookup"><span data-stu-id="85fa3-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="85fa3-183">Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="85fa3-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="85fa3-184">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="85fa3-184">Operator overloadability</span></span>

<span data-ttu-id="85fa3-185">Uživatelem definovaný typ nemůže přetížit `*` `->`operátory `[]` `&`související s ukazatelem , , a .</span><span class="sxs-lookup"><span data-stu-id="85fa3-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="85fa3-186">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85fa3-186">C# language specification</span></span>

<span data-ttu-id="85fa3-187">Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="85fa3-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="85fa3-188">Pevné a pohyblivé proměnné</span><span class="sxs-lookup"><span data-stu-id="85fa3-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="85fa3-189">Adresa operátora</span><span class="sxs-lookup"><span data-stu-id="85fa3-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="85fa3-190">Přesměrování ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="85fa3-191">Přístup člena ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="85fa3-192">Přístup k elementu ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="85fa3-193">Aritmetika ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="85fa3-194">Přírůstek a snížení ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="85fa3-195">Porovnání ukazatele</span><span class="sxs-lookup"><span data-stu-id="85fa3-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="85fa3-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="85fa3-196">See also</span></span>

- [<span data-ttu-id="85fa3-197">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="85fa3-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="85fa3-198">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="85fa3-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="85fa3-199">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="85fa3-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="85fa3-200">nebezpečné klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="85fa3-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="85fa3-201">pevné klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="85fa3-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="85fa3-202">stackalloc</span><span class="sxs-lookup"><span data-stu-id="85fa3-202">stackalloc</span></span>](stackalloc.md)
- [<span data-ttu-id="85fa3-203">sizeof – operátor</span><span class="sxs-lookup"><span data-stu-id="85fa3-203">sizeof operator</span></span>](sizeof.md)
