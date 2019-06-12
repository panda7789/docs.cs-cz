---
title: Operátory jazyka C#
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: c6b83779a630c6d797968d79635793e229751f93
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833276"
---
# <a name="c-operators"></a><span data-ttu-id="e9cf8-102">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9cf8-102">C# operators</span></span>

<span data-ttu-id="e9cf8-103">C#poskytuje řadu předdefinovaných operátory podporovaných předdefinovaných typů.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="e9cf8-104">Například [aritmetické operátory](arithmetic-operators.md) provádění aritmetických operací s operandy předdefinovaných číselných typů a [logické logické operátory](boolean-logical-operators.md) provádí logické operace s [bool ](../keywords/bool.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="e9cf8-105">Uživatelem definovaný typ může přetížit některé operátory definovat odpovídající chování pro operandy typu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="e9cf8-106">Další informace najdete v tématu [operátor](../keywords/operator.md) článku – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-106">For more information, see the [operator](../keywords/operator.md) keyword article.</span></span>

<span data-ttu-id="e9cf8-107">Následující části seznamu C# operátory od nejvyšší prioritu, takže nejnižší.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="e9cf8-108">Operátory v jednotlivých částech sdílet stejnou úrovní priority.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="e9cf8-109">Primární operátory</span><span class="sxs-lookup"><span data-stu-id="e9cf8-109">Primary operators</span></span>

<span data-ttu-id="e9cf8-110">Jedná se o nejvyšší priorita operátorů.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="e9cf8-111">[x.y](member-access-operators.md#member-access-operator-) – přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="e9cf8-112">[x?. y](member-access-operators.md#null-conditional-operators--and-) – přístup Podmíněný člen s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="e9cf8-113">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="e9cf8-114">[x? [y] ](member-access-operators.md#null-conditional-operators--and-) – prvek Podmíněné pole s hodnotou null, nebo zadejte přístup indexeru.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="e9cf8-115">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="e9cf8-116">[f(x)](member-access-operators.md#invocation-operator-) – metoda volání nebo vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="e9cf8-117">[&#91;x&#93; ](member-access-operators.md#indexer-operator-) – element pole nebo typ přístup indexeru.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="e9cf8-118">[x ++](arithmetic-operators.md#increment-operator-) – Příponové operátory Inkrementace.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="e9cf8-119">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden znak větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="e9cf8-120">[x--](arithmetic-operators.md#decrement-operator---) – snížení příponového operátora.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="e9cf8-121">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="e9cf8-122">[nové](../keywords/new-operator.md) – typ vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-122">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="e9cf8-123">[typeof](../keywords/typeof.md) – vrátí <xref:System.Type> objekt představující operand.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-123">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="e9cf8-124">[checked](../keywords/checked.md) – umožňuje pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="e9cf8-125">[unchecked](../keywords/unchecked.md) – zakáže pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="e9cf8-126">Toto je výchozí chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="e9cf8-127">[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="e9cf8-128">[nameof](../keywords/nameof.md) -získá jednoduchého (nekvalifikovaného) název proměnné, typ nebo člena jako konstanty typu řetězec.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-128">[nameof](../keywords/nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="e9cf8-129">[Delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="e9cf8-130">[operátor sizeof:](../keywords/sizeof.md) – vrátí velikost v bajtech typ operandu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="e9cf8-131">[stackalloc](stackalloc.md) -přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-131">[stackalloc](stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="e9cf8-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – dereferenci ukazatele v kombinaci s přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="e9cf8-133">Unární operátory</span><span class="sxs-lookup"><span data-stu-id="e9cf8-133">Unary operators</span></span>

<span data-ttu-id="e9cf8-134">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-135">[+ x](addition-operator.md) – vrátí hodnotu x.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="e9cf8-136">[-x](subtraction-operator.md) – číselné negace.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="e9cf8-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – Logická negace.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="e9cf8-138">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitového doplňku.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="e9cf8-139">[++ x](arithmetic-operators.md#increment-operator-) – předponového.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="e9cf8-140">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="e9cf8-141">[--x](arithmetic-operators.md#decrement-operator---) – předponového.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="e9cf8-142">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="e9cf8-143">[(T) x](invocation-operator.md) – typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-143">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="e9cf8-144">[operátor await](../keywords/await.md) – čeká `Task`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="e9cf8-145">[& x](pointer-related-operators.md#address-of-operator-) – adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="e9cf8-146">[\* x](pointer-related-operators.md#pointer-indirection-operator-) – dereferenci ukazatele nebo přístup přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="e9cf8-147">[True – – operátor](true-false-operators.md) – vrátí [bool](../keywords/bool.md) hodnotu `true` označuje jednoznačně true operand.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="e9cf8-148">[false – – operátor](true-false-operators.md) – vrátí [bool](../keywords/bool.md) hodnotu `true` k označení, že operand je jednoznačně false.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="e9cf8-149">Operátory násobení</span><span class="sxs-lookup"><span data-stu-id="e9cf8-149">Multiplicative operators</span></span>

<span data-ttu-id="e9cf8-150">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – násobení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="e9cf8-152">[x a y](arithmetic-operators.md#division-operator-) – dělení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="e9cf8-153">Pokud jsou operandy celých čísel, výsledek je celé číslo zkráceno směrem k nule (například `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="e9cf8-154">[x, % y](arithmetic-operators.md#remainder-operator-) – zbytek.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="e9cf8-155">Pokud jsou operandy celých čísel, vrátí zbytek dělicí x y.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="e9cf8-156">Pokud `q = x / y` a `r = x % y`, pak `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="e9cf8-157">Operátory sčítání</span><span class="sxs-lookup"><span data-stu-id="e9cf8-157">Additive operators</span></span>

<span data-ttu-id="e9cf8-158">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-159">[x + y](arithmetic-operators.md#addition-operator-) – přidání.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="e9cf8-160">[x-y](arithmetic-operators.md#subtraction-operator--) – odčítání.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="e9cf8-161">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="e9cf8-161">Shift operators</span></span>

<span data-ttu-id="e9cf8-162">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-163">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – posunutí bitů doleva a vyplnit nula na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="e9cf8-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – posunutí bitů doprava.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="e9cf8-165">Pokud levý operand `int` nebo `long`, pak levé bity jsou vyplněny na bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="e9cf8-166">Pokud levý operand `uint` nebo `ulong`, pak levé bity jsou vyplněny hodnotou nula.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="e9cf8-167">Operátory relační a typové zkoušky</span><span class="sxs-lookup"><span data-stu-id="e9cf8-167">Relational and type-testing operators</span></span>

<span data-ttu-id="e9cf8-168">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-169">[x \< y](comparison-operators.md#less-than-operator-) – menší než (true, pokud x je menší než y).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="e9cf8-170">[x > y](comparison-operators.md#greater-than-operator-) – větší než (true, pokud x je větší než y).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="e9cf8-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – menší než nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="e9cf8-172">[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – větší než nebo rovna hodnotě.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="e9cf8-173">[je](../keywords/is.md) – typ kompatibility.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-173">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="e9cf8-174">Vrátí true, pokud vyhodnocený levý operand může být převeden na typ určený v pravý operand (statického typu).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-174">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="e9cf8-175">[jako](../keywords/as.md) – převod typu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-175">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="e9cf8-176">Vrátí levý operand přetypování na typ určený pravý operand (statického typu), ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-176">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="e9cf8-177">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="e9cf8-177">Equality operators</span></span>

<span data-ttu-id="e9cf8-178">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-179">[x == y](equality-operators.md#equality-operator-) – rovnosti.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="e9cf8-180">Ve výchozím nastavení, pro referenční typy jiné než `string`tento vrátí referenční rovnosti (identity test).</span><span class="sxs-lookup"><span data-stu-id="e9cf8-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="e9cf8-181">Však můžete přetížit typy `==`, takže pokud máte v úmyslu k otestování identity, je nejvhodnější použít `ReferenceEquals` metodu na `object`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="e9cf8-182">[x! = y](equality-operators.md#inequality-operator-) – není rovno.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="e9cf8-183">Viz komentář `==`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-183">See comment for `==`.</span></span> <span data-ttu-id="e9cf8-184">Pokud typ přetížení `==`, pak musí přetížení `!=`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="e9cf8-185">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="e9cf8-185">Logical AND operator</span></span>

<span data-ttu-id="e9cf8-186">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-187">`x & y` – [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) pro `bool` operandy nebo [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) pro operandy integrální typy.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="e9cf8-188">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="e9cf8-188">Logical XOR operator</span></span>

<span data-ttu-id="e9cf8-189">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-190">`x ^ y` – [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) pro `bool` operandy nebo [bitové logické XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) pro operandy integrální typy.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="e9cf8-191">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="e9cf8-191">Logical OR operator</span></span>

<span data-ttu-id="e9cf8-192">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-193">`x | y` – [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) pro `bool` operandy nebo [bitové logické OR](bitwise-and-shift-operators.md#logical-or-operator-) pro operandy integrální typy.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="e9cf8-194">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="e9cf8-194">Conditional AND operator</span></span>

<span data-ttu-id="e9cf8-195">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-196">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – logickým operátorem a.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="e9cf8-197">Pokud je první operand vyhodnocen na hodnotu false, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-197">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="e9cf8-198">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="e9cf8-198">Conditional OR operator</span></span>

<span data-ttu-id="e9cf8-199">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-200">[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logický operátor OR.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="e9cf8-201">Pokud je první operand vyhodnocen na hodnotu true, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-201">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="e9cf8-202">Operátoru nulového sjednocení</span><span class="sxs-lookup"><span data-stu-id="e9cf8-202">Null-coalescing operator</span></span>

<span data-ttu-id="e9cf8-203">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-204">[x?? y](null-coalescing-operator.md) – vrátí `x` jde-li jinou hodnotu než`null`; v opačném případě vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="e9cf8-205">Podmíněný operátor</span><span class="sxs-lookup"><span data-stu-id="e9cf8-205">Conditional operator</span></span>

<span data-ttu-id="e9cf8-206">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-207">[t? x: y](conditional-operator.md) – Pokud test `t` vyhodnotí jako true, pak vyhodnotí a vrátí `x`; v opačném případě vyhodnotí a vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="e9cf8-208">Operátory přiřazení a lambda</span><span class="sxs-lookup"><span data-stu-id="e9cf8-208">Assignment and lambda operators</span></span>

<span data-ttu-id="e9cf8-209">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9cf8-210">[x = y](assignment-operator.md) – přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="e9cf8-211">[x += y](arithmetic-operators.md#compound-assignment) – přírůstku.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="e9cf8-212">Přidat hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="e9cf8-213">Pokud `x` označí [události](../keywords/event.md), pak `y` musí být odpovídající metodu, která C# přidá jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="e9cf8-214">[x-= y](arithmetic-operators.md#compound-assignment) – sníží.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="e9cf8-215">Odečte hodnotu `y` od hodnoty `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="e9cf8-216">Pokud `x` označí [události](../keywords/event.md), pak `y` musí být odpovídající metodu, která C# odebere jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="e9cf8-217">[x \* = y](arithmetic-operators.md#compound-assignment) – přiřazení násobení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="e9cf8-218">Vynásobí hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-219">[x / = y](arithmetic-operators.md#compound-assignment) – přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="e9cf8-220">Vydělí hodnotu `x` hodnotou `y`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-221">[x % = y](arithmetic-operators.md#compound-assignment) – remainder přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="e9cf8-222">Vydělí hodnotu `x` hodnotou `y`, uložení zbytku v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-223">[x & = y](boolean-logical-operators.md#compound-assignment) – a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="e9cf8-224">A hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – přiřazení OR.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="e9cf8-226">NEBO hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-227">[x ^ = y](boolean-logical-operators.md#compound-assignment) – XOR přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="e9cf8-228">XOR hodnotu z `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-229">[x << = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="e9cf8-230">Posune hodnotu `x` vlevo po `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-231">[x >> = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="e9cf8-232">Posune hodnotu `x` právo `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9cf8-233">[=>](lambda-operator.md) – deklaraci lambda.</span><span class="sxs-lookup"><span data-stu-id="e9cf8-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9cf8-234">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9cf8-234">See also</span></span>

- [<span data-ttu-id="e9cf8-235">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9cf8-235">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e9cf8-236">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e9cf8-236">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e9cf8-237">C#</span><span class="sxs-lookup"><span data-stu-id="e9cf8-237">C#</span></span>](../../index.md)
- [<span data-ttu-id="e9cf8-238">Přetížitelné operátory</span><span class="sxs-lookup"><span data-stu-id="e9cf8-238">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="e9cf8-239">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9cf8-239">C# Keywords</span></span>](../keywords/index.md)
