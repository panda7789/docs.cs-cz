---
title: Operátory jazyka C#
ms.date: 04/04/2018
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
ms.openlocfilehash: 4958f3e28b80fca2086d45827df1ced8fc26bd8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672287"
---
# <a name="c-operators"></a><span data-ttu-id="90ddb-102">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="90ddb-102">C# operators</span></span>

<span data-ttu-id="90ddb-103">Jazyk C# poskytuje mnoho operátorů, které jsou symboly, které určují operace, které (matematické, indexování, volání funkce atd.) provést ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="90ddb-104">Je možné [přetížení](../../programming-guide/statements-expressions-operators/overloadable-operators.md) mnoho operátorů, chcete-li změnit jejich význam při aplikování na uživatelem definovaného typu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="90ddb-105">Operace interních typů (například `==`, `!=`, `<`, `>`, `&`, `|`) jsou obecně povoleny na výčet (`enum`) typy.</span><span class="sxs-lookup"><span data-stu-id="90ddb-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="90ddb-106">Níže uvedených částech najdete seznam operátorů jazyka C# od nejvyšší prioritu, takže nejnižší.</span><span class="sxs-lookup"><span data-stu-id="90ddb-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="90ddb-107">Operátory v jednotlivých částech sdílet stejnou úrovní priority.</span><span class="sxs-lookup"><span data-stu-id="90ddb-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="90ddb-108">Primární operátory</span><span class="sxs-lookup"><span data-stu-id="90ddb-108">Primary operators</span></span>

<span data-ttu-id="90ddb-109">Jedná se o nejvyšší priorita operátorů.</span><span class="sxs-lookup"><span data-stu-id="90ddb-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="90ddb-110">[x.y](member-access-operator.md) – přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="90ddb-111">[x?. y](null-conditional-operators.md) – přístup Podmíněný člen s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="90ddb-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="90ddb-112">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="90ddb-113">[x? [y] ](null-conditional-operators.md) -index podmíněného přístupu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="90ddb-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="90ddb-114">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="90ddb-115">[f(x)](invocation-operator.md) – funkce volání.</span><span class="sxs-lookup"><span data-stu-id="90ddb-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="90ddb-116">[&#91;x&#93; ](index-operator.md) – indexování agregovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="90ddb-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="90ddb-117">[x ++](arithmetic-operators.md#increment-operator-) – Příponové operátory Inkrementace.</span><span class="sxs-lookup"><span data-stu-id="90ddb-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="90ddb-118">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden znak větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="90ddb-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="90ddb-119">[x--](arithmetic-operators.md#decrement-operator---) – snížení příponového operátora.</span><span class="sxs-lookup"><span data-stu-id="90ddb-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="90ddb-120">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="90ddb-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="90ddb-121">[nové](../keywords/new-operator.md) – typ vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="90ddb-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="90ddb-122">[typeof](../keywords/typeof.md) – vrátí <xref:System.Type> objekt představující operand.</span><span class="sxs-lookup"><span data-stu-id="90ddb-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="90ddb-123">[checked](../keywords/checked.md) – umožňuje pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="90ddb-124">[unchecked](../keywords/unchecked.md) – zakáže pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="90ddb-125">Toto je výchozí chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="90ddb-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="90ddb-126">[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.</span><span class="sxs-lookup"><span data-stu-id="90ddb-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="90ddb-127">[Delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="90ddb-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="90ddb-128">[operátor sizeof:](../keywords/sizeof.md) – vrátí velikost v bajtech typ operandu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="90ddb-129">[->](dereference-operator.md) – přístup přes ukazatel v kombinaci s přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="90ddb-130">Unární operátory</span><span class="sxs-lookup"><span data-stu-id="90ddb-130">Unary operators</span></span>

<span data-ttu-id="90ddb-131">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-132">[+ x](addition-operator.md) – vrátí hodnotu x.</span><span class="sxs-lookup"><span data-stu-id="90ddb-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="90ddb-133">[-x](subtraction-operator.md) – číselné negace.</span><span class="sxs-lookup"><span data-stu-id="90ddb-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="90ddb-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – Logická negace.</span><span class="sxs-lookup"><span data-stu-id="90ddb-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="90ddb-135">[~ x](bitwise-complement-operator.md) – bitového doplňku.</span><span class="sxs-lookup"><span data-stu-id="90ddb-135">[~x](bitwise-complement-operator.md) – bitwise complement.</span></span>

<span data-ttu-id="90ddb-136">[++ x](arithmetic-operators.md#increment-operator-) – předponového.</span><span class="sxs-lookup"><span data-stu-id="90ddb-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="90ddb-137">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="90ddb-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="90ddb-138">[--x](arithmetic-operators.md#decrement-operator---) – předponového.</span><span class="sxs-lookup"><span data-stu-id="90ddb-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="90ddb-139">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="90ddb-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="90ddb-140">[(T) x](invocation-operator.md) – typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="90ddb-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="90ddb-141">[operátor await](../keywords/await.md) – čeká `Task`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="90ddb-142">[& x](and-operator.md) – adresu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="90ddb-143">[\* x](multiplication-operator.md) – přesměrování.</span><span class="sxs-lookup"><span data-stu-id="90ddb-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="90ddb-144">Operátory násobení</span><span class="sxs-lookup"><span data-stu-id="90ddb-144">Multiplicative operators</span></span>

<span data-ttu-id="90ddb-145">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-145">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-146">[x \* y](arithmetic-operators.md#multiplication-operator-) – násobení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-146">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="90ddb-147">[x a y](arithmetic-operators.md#division-operator-) – dělení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-147">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="90ddb-148">Pokud jsou operandy celých čísel, výsledek je celé číslo zkráceno směrem k nule (například `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="90ddb-148">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="90ddb-149">[x, % y](arithmetic-operators.md#remainder-operator-) – zbytek.</span><span class="sxs-lookup"><span data-stu-id="90ddb-149">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="90ddb-150">Pokud jsou operandy celých čísel, vrátí zbytek dělicí x y.</span><span class="sxs-lookup"><span data-stu-id="90ddb-150">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="90ddb-151">Pokud `q = x / y` a `r = x % y`, pak `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-151">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="90ddb-152">Operátory sčítání</span><span class="sxs-lookup"><span data-stu-id="90ddb-152">Additive operators</span></span>

<span data-ttu-id="90ddb-153">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-153">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-154">[x + y](arithmetic-operators.md#addition-operator-) – přidání.</span><span class="sxs-lookup"><span data-stu-id="90ddb-154">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="90ddb-155">[x-y](arithmetic-operators.md#subtraction-operator--) – odčítání.</span><span class="sxs-lookup"><span data-stu-id="90ddb-155">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="90ddb-156">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="90ddb-156">Shift operators</span></span>

<span data-ttu-id="90ddb-157">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-157">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-158">[x <\< y](left-shift-operator.md) – posunutí bitů doleva a vyplnit nula na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="90ddb-158">[x <\<  y](left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="90ddb-159">[x >> y](right-shift-operator.md) – posunutí bitů doprava.</span><span class="sxs-lookup"><span data-stu-id="90ddb-159">[x >> y](right-shift-operator.md) – shift bits right.</span></span> <span data-ttu-id="90ddb-160">Pokud levý operand `int` nebo `long`, pak levé bity jsou vyplněny na bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="90ddb-160">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="90ddb-161">Pokud levý operand `uint` nebo `ulong`, pak levé bity jsou vyplněny hodnotou nula.</span><span class="sxs-lookup"><span data-stu-id="90ddb-161">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="90ddb-162">Operátory relační a typové zkoušky</span><span class="sxs-lookup"><span data-stu-id="90ddb-162">Relational and type-testing operators</span></span>

<span data-ttu-id="90ddb-163">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-163">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-164">[x \< y](less-than-operator.md) – menší než (true, pokud x je menší než y).</span><span class="sxs-lookup"><span data-stu-id="90ddb-164">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="90ddb-165">[x > y](greater-than-operator.md) – větší než (true, pokud x je větší než y).</span><span class="sxs-lookup"><span data-stu-id="90ddb-165">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="90ddb-166">[x \<= y](less-than-equal-operator.md) – menší než nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="90ddb-166">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="90ddb-167">[x > = y](greater-than-equal-operator.md) – větší než nebo rovna hodnotě.</span><span class="sxs-lookup"><span data-stu-id="90ddb-167">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="90ddb-168">[je](../keywords/is.md) – typ kompatibility.</span><span class="sxs-lookup"><span data-stu-id="90ddb-168">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="90ddb-169">Vrátí true, pokud vyhodnocený levý operand může být převeden na typ určený v pravý operand (statického typu).</span><span class="sxs-lookup"><span data-stu-id="90ddb-169">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="90ddb-170">[jako](../keywords/as.md) – převod typu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-170">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="90ddb-171">Vrátí levý operand přetypování na typ určený pravý operand (statického typu), ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="90ddb-171">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="90ddb-172">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="90ddb-172">Equality operators</span></span>

<span data-ttu-id="90ddb-173">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-173">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-174">[x == y](equality-operators.md#equality-operator-) – rovnosti.</span><span class="sxs-lookup"><span data-stu-id="90ddb-174">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="90ddb-175">Ve výchozím nastavení, pro referenční typy jiné než `string`tento vrátí referenční rovnosti (identity test).</span><span class="sxs-lookup"><span data-stu-id="90ddb-175">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="90ddb-176">Však můžete přetížit typy `==`, takže pokud máte v úmyslu k otestování identity, je nejvhodnější použít `ReferenceEquals` metodu na `object`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-176">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="90ddb-177">[x! = y](equality-operators.md#inequality-operator-) – není rovno.</span><span class="sxs-lookup"><span data-stu-id="90ddb-177">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="90ddb-178">Viz komentář `==`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-178">See comment for `==`.</span></span> <span data-ttu-id="90ddb-179">Pokud typ přetížení `==`, pak musí přetížení `!=`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-179">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="90ddb-180">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="90ddb-180">Logical AND operator</span></span>

<span data-ttu-id="90ddb-181">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-181">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-182">[x & y](and-operator.md) – logický operátor or bitový AND.</span><span class="sxs-lookup"><span data-stu-id="90ddb-182">[x & y](and-operator.md) – logical or bitwise AND.</span></span> <span data-ttu-id="90ddb-183">Obecně můžete s celočíselnými typy a `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="90ddb-183">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="90ddb-184">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="90ddb-184">Logical XOR operator</span></span>

<span data-ttu-id="90ddb-185">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-185">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-186">[x ^ y](xor-operator.md) – logické a bitové operace XOR.</span><span class="sxs-lookup"><span data-stu-id="90ddb-186">[x ^ y](xor-operator.md) – logical or bitwise XOR.</span></span> <span data-ttu-id="90ddb-187">Obecně můžete s celočíselnými typy a `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="90ddb-187">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="90ddb-188">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="90ddb-188">Logical OR operator</span></span>

<span data-ttu-id="90ddb-189">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-190">[x &#124; y](or-operator.md) – logické a bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="90ddb-190">[x &#124; y](or-operator.md) – logical or bitwise OR.</span></span> <span data-ttu-id="90ddb-191">Obecně můžete s celočíselnými typy a `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="90ddb-191">You can generally use this with integer types and `enum` types.</span></span>

## <a name="true-operator"></a><span data-ttu-id="90ddb-192">True – – operátor</span><span class="sxs-lookup"><span data-stu-id="90ddb-192">True operator</span></span>

<span data-ttu-id="90ddb-193">[True](../keywords/true-false-operators.md) operátor vrátí [bool](../keywords/bool.md) hodnotu `true` označuje jednoznačně true operand.</span><span class="sxs-lookup"><span data-stu-id="90ddb-193">The [true](../keywords/true-false-operators.md) operator returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span> 

## <a name="false-operator"></a><span data-ttu-id="90ddb-194">false – – operátor</span><span class="sxs-lookup"><span data-stu-id="90ddb-194">False operator</span></span>

<span data-ttu-id="90ddb-195">[False](../keywords/true-false-operators.md) operátor vrátí [bool](../keywords/bool.md) hodnotu `true` k označení, že operand je jednoznačně false.</span><span class="sxs-lookup"><span data-stu-id="90ddb-195">The [false](../keywords/true-false-operators.md) operator returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span> 

## <a name="conditional-and-operator"></a><span data-ttu-id="90ddb-196">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="90ddb-196">Conditional AND operator</span></span>

<span data-ttu-id="90ddb-197">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-197">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-198">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – logickým operátorem a.</span><span class="sxs-lookup"><span data-stu-id="90ddb-198">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="90ddb-199">Pokud je první operand vyhodnocen na hodnotu false, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="90ddb-199">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="90ddb-200">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="90ddb-200">Conditional OR operator</span></span>

<span data-ttu-id="90ddb-201">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-201">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-202">[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logický operátor OR.</span><span class="sxs-lookup"><span data-stu-id="90ddb-202">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="90ddb-203">Pokud je první operand vyhodnocen na hodnotu true, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="90ddb-203">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="90ddb-204">Operátoru nulového sjednocení</span><span class="sxs-lookup"><span data-stu-id="90ddb-204">Null-coalescing operator</span></span>

<span data-ttu-id="90ddb-205">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-205">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-206">[x?? y](null-coalescing-operator.md) – vrátí `x` jde-li jinou hodnotu než`null`; v opačném případě vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-206">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="90ddb-207">Podmíněný operátor</span><span class="sxs-lookup"><span data-stu-id="90ddb-207">Conditional operator</span></span>

<span data-ttu-id="90ddb-208">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-208">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-209">[t? x: y](conditional-operator.md) – Pokud test `t` vyhodnotí jako true, pak vyhodnotí a vrátí `x`; v opačném případě vyhodnotí a vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="90ddb-209">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="90ddb-210">Operátory přiřazení a Lambda</span><span class="sxs-lookup"><span data-stu-id="90ddb-210">Assignment and Lambda operators</span></span>

<span data-ttu-id="90ddb-211">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="90ddb-211">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="90ddb-212">[x = y](assignment-operator.md) – přiřazení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-212">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="90ddb-213">[x += y](addition-assignment-operator.md) – přírůstku.</span><span class="sxs-lookup"><span data-stu-id="90ddb-213">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="90ddb-214">Přidat hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-214">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="90ddb-215">Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# přidá jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="90ddb-215">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="90ddb-216">[x-= y](subtraction-assignment-operator.md) – sníží.</span><span class="sxs-lookup"><span data-stu-id="90ddb-216">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="90ddb-217">Odečte hodnotu `y` od hodnoty `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-217">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="90ddb-218">Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# odebere jako obslužné rutiny události</span><span class="sxs-lookup"><span data-stu-id="90ddb-218">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>

<span data-ttu-id="90ddb-219">[x \* = y](multiplication-assignment-operator.md) – přiřazení násobení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-219">[x \*= y](multiplication-assignment-operator.md) – multiplication assignment.</span></span> <span data-ttu-id="90ddb-220">Vynásobí hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-220">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-221">[x / = y](arithmetic-operators.md#compound-assignment) – přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-221">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="90ddb-222">Vydělí hodnotu `x` hodnotou `y`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-222">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-223">[x % = y](arithmetic-operators.md#compound-assignment) – remainder přiřazení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-223">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="90ddb-224">Vydělí hodnotu `x` hodnotou `y`, uložení zbytku v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-224">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-225">[x & = y](and-assignment-operator.md) – a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-225">[x &= y](and-assignment-operator.md) – AND assignment.</span></span> <span data-ttu-id="90ddb-226">A hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-226">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-227">[x &#124;= y](or-assignment-operator.md) – přiřazení OR.</span><span class="sxs-lookup"><span data-stu-id="90ddb-227">[x &#124;= y](or-assignment-operator.md) – OR assignment.</span></span> <span data-ttu-id="90ddb-228">NEBO hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-228">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-229">[x ^ = y](xor-assignment-operator.md) – XOR přiřazení.</span><span class="sxs-lookup"><span data-stu-id="90ddb-229">[x ^= y](xor-assignment-operator.md) – XOR assignment.</span></span> <span data-ttu-id="90ddb-230">XOR hodnotu z `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-230">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-231">[x << = y](left-shift-assignment-operator.md) – přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="90ddb-231">[x <<= y](left-shift-assignment-operator.md) – left-shift assignment.</span></span> <span data-ttu-id="90ddb-232">Posune hodnotu `x` vlevo po `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-232">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-233">[x >> = y](right-shift-assignment-operator.md) – přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="90ddb-233">[x >>= y](right-shift-assignment-operator.md) – right-shift assignment.</span></span> <span data-ttu-id="90ddb-234">Posune hodnotu `x` právo `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90ddb-234">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="90ddb-235">[=>](lambda-operator.md) – deklaraci lambda.</span><span class="sxs-lookup"><span data-stu-id="90ddb-235">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="90ddb-236">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90ddb-236">See also</span></span>

- [<span data-ttu-id="90ddb-237">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="90ddb-237">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="90ddb-238">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="90ddb-238">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="90ddb-239">C#</span><span class="sxs-lookup"><span data-stu-id="90ddb-239">C#</span></span>](../../index.md)
- [<span data-ttu-id="90ddb-240">Přetížitelné operátory</span><span class="sxs-lookup"><span data-stu-id="90ddb-240">Overloadable Operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="90ddb-241">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="90ddb-241">C# Keywords</span></span>](../keywords/index.md)
