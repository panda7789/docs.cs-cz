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
ms.openlocfilehash: f4267caeb6301950b9f6a8b9545a47b9f48e7920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977376"
---
# <a name="c-operators"></a><span data-ttu-id="3ca06-102">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ca06-102">C# operators</span></span>

<span data-ttu-id="3ca06-103">Jazyk C# poskytuje mnoho operátorů, které jsou symboly, které určují operace, které (matematické, indexování, volání funkce atd.) provést ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="3ca06-104">Je možné [přetížení](../../programming-guide/statements-expressions-operators/overloadable-operators.md) mnoho operátorů, chcete-li změnit jejich význam při aplikování na uživatelem definovaného typu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="3ca06-105">Operace interních typů (například `==`, `!=`, `<`, `>`, `&`, `|`) jsou obecně povoleny na výčet (`enum`) typy.</span><span class="sxs-lookup"><span data-stu-id="3ca06-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="3ca06-106">Níže uvedených částech najdete seznam operátorů jazyka C# od nejvyšší prioritu, takže nejnižší.</span><span class="sxs-lookup"><span data-stu-id="3ca06-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="3ca06-107">Operátory v jednotlivých částech sdílet stejnou úrovní priority.</span><span class="sxs-lookup"><span data-stu-id="3ca06-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="3ca06-108">Primární operátory</span><span class="sxs-lookup"><span data-stu-id="3ca06-108">Primary operators</span></span>

<span data-ttu-id="3ca06-109">Jedná se o nejvyšší priorita operátorů.</span><span class="sxs-lookup"><span data-stu-id="3ca06-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="3ca06-110">[x.y](member-access-operator.md) – přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="3ca06-111">[x?. y](null-conditional-operators.md) – přístup Podmíněný člen s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3ca06-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="3ca06-112">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="3ca06-113">[x? [y] ](null-conditional-operators.md) -index podmíněného přístupu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3ca06-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="3ca06-114">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="3ca06-115">[f(x)](invocation-operator.md) – funkce volání.</span><span class="sxs-lookup"><span data-stu-id="3ca06-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="3ca06-116">[&#91;x&#93; ](index-operator.md) – indexování agregovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="3ca06-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="3ca06-117">[x ++](arithmetic-operators.md#increment-operator-) – Příponové operátory Inkrementace.</span><span class="sxs-lookup"><span data-stu-id="3ca06-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="3ca06-118">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden znak větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="3ca06-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="3ca06-119">[x--](arithmetic-operators.md#decrement-operator---) – snížení příponového operátora.</span><span class="sxs-lookup"><span data-stu-id="3ca06-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="3ca06-120">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="3ca06-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="3ca06-121">[nové](../keywords/new-operator.md) – typ vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="3ca06-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="3ca06-122">[typeof](../keywords/typeof.md) – vrátí <xref:System.Type> objekt představující operand.</span><span class="sxs-lookup"><span data-stu-id="3ca06-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="3ca06-123">[checked](../keywords/checked.md) – umožňuje pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="3ca06-124">[unchecked](../keywords/unchecked.md) – zakáže pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="3ca06-125">Toto je výchozí chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3ca06-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="3ca06-126">[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.</span><span class="sxs-lookup"><span data-stu-id="3ca06-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="3ca06-127">[Delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="3ca06-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="3ca06-128">[operátor sizeof:](../keywords/sizeof.md) – vrátí velikost v bajtech typ operandu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="3ca06-129">[->](dereference-operator.md) – přístup přes ukazatel v kombinaci s přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="3ca06-130">Unární operátory</span><span class="sxs-lookup"><span data-stu-id="3ca06-130">Unary operators</span></span>

<span data-ttu-id="3ca06-131">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-132">[+ x](addition-operator.md) – vrátí hodnotu x.</span><span class="sxs-lookup"><span data-stu-id="3ca06-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="3ca06-133">[-x](subtraction-operator.md) – číselné negace.</span><span class="sxs-lookup"><span data-stu-id="3ca06-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="3ca06-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – Logická negace.</span><span class="sxs-lookup"><span data-stu-id="3ca06-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="3ca06-135">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitového doplňku.</span><span class="sxs-lookup"><span data-stu-id="3ca06-135">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="3ca06-136">[++ x](arithmetic-operators.md#increment-operator-) – předponového.</span><span class="sxs-lookup"><span data-stu-id="3ca06-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="3ca06-137">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="3ca06-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="3ca06-138">[--x](arithmetic-operators.md#decrement-operator---) – předponového.</span><span class="sxs-lookup"><span data-stu-id="3ca06-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="3ca06-139">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="3ca06-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="3ca06-140">[(T) x](invocation-operator.md) – typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="3ca06-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="3ca06-141">[operátor await](../keywords/await.md) – čeká `Task`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="3ca06-142">[& x](and-operator.md) – adresu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="3ca06-143">[\* x](multiplication-operator.md) – přesměrování.</span><span class="sxs-lookup"><span data-stu-id="3ca06-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

<span data-ttu-id="3ca06-144">[True – – operátor](../keywords/true-false-operators.md) – vrátí [bool](../keywords/bool.md) hodnotu `true` označuje jednoznačně true operand.</span><span class="sxs-lookup"><span data-stu-id="3ca06-144">[true operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="3ca06-145">[false – – operátor](../keywords/true-false-operators.md) – vrátí [bool](../keywords/bool.md) hodnotu `true` k označení, že operand je jednoznačně false.</span><span class="sxs-lookup"><span data-stu-id="3ca06-145">[false operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="3ca06-146">Operátory násobení</span><span class="sxs-lookup"><span data-stu-id="3ca06-146">Multiplicative operators</span></span>

<span data-ttu-id="3ca06-147">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-147">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-148">[x \* y](arithmetic-operators.md#multiplication-operator-) – násobení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-148">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="3ca06-149">[x a y](arithmetic-operators.md#division-operator-) – dělení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-149">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="3ca06-150">Pokud jsou operandy celých čísel, výsledek je celé číslo zkráceno směrem k nule (například `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="3ca06-150">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="3ca06-151">[x, % y](arithmetic-operators.md#remainder-operator-) – zbytek.</span><span class="sxs-lookup"><span data-stu-id="3ca06-151">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="3ca06-152">Pokud jsou operandy celých čísel, vrátí zbytek dělicí x y.</span><span class="sxs-lookup"><span data-stu-id="3ca06-152">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="3ca06-153">Pokud `q = x / y` a `r = x % y`, pak `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-153">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="3ca06-154">Operátory sčítání</span><span class="sxs-lookup"><span data-stu-id="3ca06-154">Additive operators</span></span>

<span data-ttu-id="3ca06-155">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-155">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-156">[x + y](arithmetic-operators.md#addition-operator-) – přidání.</span><span class="sxs-lookup"><span data-stu-id="3ca06-156">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="3ca06-157">[x-y](arithmetic-operators.md#subtraction-operator--) – odčítání.</span><span class="sxs-lookup"><span data-stu-id="3ca06-157">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="3ca06-158">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="3ca06-158">Shift operators</span></span>

<span data-ttu-id="3ca06-159">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-159">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-160">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – posunutí bitů doleva a vyplnit nula na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="3ca06-160">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="3ca06-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – posunutí bitů doprava.</span><span class="sxs-lookup"><span data-stu-id="3ca06-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="3ca06-162">Pokud levý operand `int` nebo `long`, pak levé bity jsou vyplněny na bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="3ca06-162">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="3ca06-163">Pokud levý operand `uint` nebo `ulong`, pak levé bity jsou vyplněny hodnotou nula.</span><span class="sxs-lookup"><span data-stu-id="3ca06-163">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="3ca06-164">Operátory relační a typové zkoušky</span><span class="sxs-lookup"><span data-stu-id="3ca06-164">Relational and type-testing operators</span></span>

<span data-ttu-id="3ca06-165">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-165">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-166">[x \< y](less-than-operator.md) – menší než (true, pokud x je menší než y).</span><span class="sxs-lookup"><span data-stu-id="3ca06-166">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="3ca06-167">[x > y](greater-than-operator.md) – větší než (true, pokud x je větší než y).</span><span class="sxs-lookup"><span data-stu-id="3ca06-167">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="3ca06-168">[x \<= y](less-than-equal-operator.md) – menší než nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="3ca06-168">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="3ca06-169">[x > = y](greater-than-equal-operator.md) – větší než nebo rovna hodnotě.</span><span class="sxs-lookup"><span data-stu-id="3ca06-169">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="3ca06-170">[je](../keywords/is.md) – typ kompatibility.</span><span class="sxs-lookup"><span data-stu-id="3ca06-170">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="3ca06-171">Vrátí true, pokud vyhodnocený levý operand může být převeden na typ určený v pravý operand (statického typu).</span><span class="sxs-lookup"><span data-stu-id="3ca06-171">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="3ca06-172">[jako](../keywords/as.md) – převod typu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-172">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="3ca06-173">Vrátí levý operand přetypování na typ určený pravý operand (statického typu), ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="3ca06-173">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="3ca06-174">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="3ca06-174">Equality operators</span></span>

<span data-ttu-id="3ca06-175">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-175">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-176">[x == y](equality-operators.md#equality-operator-) – rovnosti.</span><span class="sxs-lookup"><span data-stu-id="3ca06-176">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="3ca06-177">Ve výchozím nastavení, pro referenční typy jiné než `string`tento vrátí referenční rovnosti (identity test).</span><span class="sxs-lookup"><span data-stu-id="3ca06-177">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="3ca06-178">Však můžete přetížit typy `==`, takže pokud máte v úmyslu k otestování identity, je nejvhodnější použít `ReferenceEquals` metodu na `object`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-178">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="3ca06-179">[x! = y](equality-operators.md#inequality-operator-) – není rovno.</span><span class="sxs-lookup"><span data-stu-id="3ca06-179">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="3ca06-180">Viz komentář `==`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-180">See comment for `==`.</span></span> <span data-ttu-id="3ca06-181">Pokud typ přetížení `==`, pak musí přetížení `!=`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-181">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="3ca06-182">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="3ca06-182">Logical AND operator</span></span>

<span data-ttu-id="3ca06-183">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-183">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-184">`x & y` – [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) pro `bool` operandy nebo [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) pro operandy integrální typy.</span><span class="sxs-lookup"><span data-stu-id="3ca06-184">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="3ca06-185">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="3ca06-185">Logical XOR operator</span></span>

<span data-ttu-id="3ca06-186">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-187">`x ^ y` – [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) pro `bool` operandy nebo [bitové logické XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) pro operandy integrální typy.</span><span class="sxs-lookup"><span data-stu-id="3ca06-187">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="3ca06-188">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="3ca06-188">Logical OR operator</span></span>

<span data-ttu-id="3ca06-189">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-190">`x | y` – [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) pro `bool` operandy nebo [bitové logické OR](bitwise-and-shift-operators.md#logical-or-operator-) pro operandy integrální typy.</span><span class="sxs-lookup"><span data-stu-id="3ca06-190">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="3ca06-191">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="3ca06-191">Conditional AND operator</span></span>

<span data-ttu-id="3ca06-192">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-193">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – logickým operátorem a.</span><span class="sxs-lookup"><span data-stu-id="3ca06-193">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="3ca06-194">Pokud je první operand vyhodnocen na hodnotu false, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="3ca06-194">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="3ca06-195">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="3ca06-195">Conditional OR operator</span></span>

<span data-ttu-id="3ca06-196">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-196">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-197">[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logický operátor OR.</span><span class="sxs-lookup"><span data-stu-id="3ca06-197">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="3ca06-198">Pokud je první operand vyhodnocen na hodnotu true, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="3ca06-198">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="3ca06-199">Operátoru nulového sjednocení</span><span class="sxs-lookup"><span data-stu-id="3ca06-199">Null-coalescing operator</span></span>

<span data-ttu-id="3ca06-200">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-200">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-201">[x?? y](null-coalescing-operator.md) – vrátí `x` jde-li jinou hodnotu než`null`; v opačném případě vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-201">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="3ca06-202">Podmíněný operátor</span><span class="sxs-lookup"><span data-stu-id="3ca06-202">Conditional operator</span></span>

<span data-ttu-id="3ca06-203">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-204">[t? x: y](conditional-operator.md) – Pokud test `t` vyhodnotí jako true, pak vyhodnotí a vrátí `x`; v opačném případě vyhodnotí a vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="3ca06-204">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="3ca06-205">Operátory přiřazení a Lambda</span><span class="sxs-lookup"><span data-stu-id="3ca06-205">Assignment and Lambda operators</span></span>

<span data-ttu-id="3ca06-206">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3ca06-206">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="3ca06-207">[x = y](assignment-operator.md) – přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-207">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="3ca06-208">[x += y](addition-assignment-operator.md) – přírůstku.</span><span class="sxs-lookup"><span data-stu-id="3ca06-208">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="3ca06-209">Přidat hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-209">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="3ca06-210">Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# přidá jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3ca06-210">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="3ca06-211">[x-= y](subtraction-assignment-operator.md) – sníží.</span><span class="sxs-lookup"><span data-stu-id="3ca06-211">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="3ca06-212">Odečte hodnotu `y` od hodnoty `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-212">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="3ca06-213">Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, které C# odebere jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3ca06-213">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler.</span></span>

<span data-ttu-id="3ca06-214">[x \* = y](arithmetic-operators.md#compound-assignment) – přiřazení násobení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-214">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="3ca06-215">Vynásobí hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-215">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-216">[x / = y](arithmetic-operators.md#compound-assignment) – přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-216">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="3ca06-217">Vydělí hodnotu `x` hodnotou `y`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-217">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-218">[x % = y](arithmetic-operators.md#compound-assignment) – remainder přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-218">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="3ca06-219">Vydělí hodnotu `x` hodnotou `y`, uložení zbytku v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-219">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-220">[x & = y](boolean-logical-operators.md#compound-assignment) – a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-220">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="3ca06-221">A hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-221">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-222">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – přiřazení OR.</span><span class="sxs-lookup"><span data-stu-id="3ca06-222">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="3ca06-223">NEBO hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-223">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-224">[x ^ = y](boolean-logical-operators.md#compound-assignment) – XOR přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3ca06-224">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="3ca06-225">XOR hodnotu z `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-225">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-226">[x << = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="3ca06-226">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="3ca06-227">Posune hodnotu `x` vlevo po `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-227">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-228">[x >> = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="3ca06-228">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="3ca06-229">Posune hodnotu `x` právo `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ca06-229">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="3ca06-230">[=>](lambda-operator.md) – deklaraci lambda.</span><span class="sxs-lookup"><span data-stu-id="3ca06-230">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ca06-231">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ca06-231">See also</span></span>

- [<span data-ttu-id="3ca06-232">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ca06-232">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3ca06-233">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3ca06-233">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ca06-234">C#</span><span class="sxs-lookup"><span data-stu-id="3ca06-234">C#</span></span>](../../index.md)
- [<span data-ttu-id="3ca06-235">Přetížitelné operátory</span><span class="sxs-lookup"><span data-stu-id="3ca06-235">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="3ca06-236">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ca06-236">C# Keywords</span></span>](../keywords/index.md)
