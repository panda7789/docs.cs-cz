---
title: C#operátory
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
ms.openlocfilehash: 6380fa4ec99f598be0d01db1061900520e94d5f1
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333405"
---
# <a name="c-operators"></a><span data-ttu-id="1b074-102">C#operátory</span><span class="sxs-lookup"><span data-stu-id="1b074-102">C# operators</span></span>

<span data-ttu-id="1b074-103">Jazyk C# poskytuje mnoho operátorů, které jsou symboly, které určují operace, které (matematické, indexování, volání funkce atd.) provést ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="1b074-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="1b074-104">Je možné [přetížení](../../programming-guide/statements-expressions-operators/overloadable-operators.md) mnoho operátorů, chcete-li změnit jejich význam při aplikování na uživatelem definovaného typu.</span><span class="sxs-lookup"><span data-stu-id="1b074-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="1b074-105">Operace interních typů (například `==`, `!=`, `<`, `>`, `&`, `|`) jsou obecně povoleny na výčet (`enum`) typy.</span><span class="sxs-lookup"><span data-stu-id="1b074-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="1b074-106">Níže uvedených částech najdete seznam operátorů jazyka C# od nejvyšší prioritu, takže nejnižší.</span><span class="sxs-lookup"><span data-stu-id="1b074-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="1b074-107">Operátory v jednotlivých částech sdílet stejnou úrovní priority.</span><span class="sxs-lookup"><span data-stu-id="1b074-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="1b074-108">Primární operátory</span><span class="sxs-lookup"><span data-stu-id="1b074-108">Primary operators</span></span>

<span data-ttu-id="1b074-109">Jedná se o nejvyšší priorita operátorů.</span><span class="sxs-lookup"><span data-stu-id="1b074-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="1b074-110">[x.y](member-access-operator.md) – přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="1b074-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="1b074-111">[x?. y](null-conditional-operators.md) – přístup Podmíněný člen s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1b074-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="1b074-112">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="1b074-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1b074-113">[x? [y] ](null-conditional-operators.md) -index podmíněného přístupu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1b074-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="1b074-114">Vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="1b074-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1b074-115">[f(x)](invocation-operator.md) – funkce volání.</span><span class="sxs-lookup"><span data-stu-id="1b074-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="1b074-116">[&#91;x&#93; ](index-operator.md) – indexování agregovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="1b074-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="1b074-117">[x ++](increment-operator.md) – Příponové operátory Inkrementace.</span><span class="sxs-lookup"><span data-stu-id="1b074-117">[x++](increment-operator.md) – postfix increment.</span></span> <span data-ttu-id="1b074-118">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden znak větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="1b074-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1b074-119">[x--](decrement-operator.md) – snížení příponového operátora.</span><span class="sxs-lookup"><span data-stu-id="1b074-119">[x--](decrement-operator.md) –  postfix decrement.</span></span> <span data-ttu-id="1b074-120">Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="1b074-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1b074-121">[nové](../keywords/new-operator.md) – typ vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="1b074-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="1b074-122">[typeof](../keywords/typeof.md) – vrátí <xref:System.Type> objekt představující operand.</span><span class="sxs-lookup"><span data-stu-id="1b074-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="1b074-123">[checked](../keywords/checked.md) – umožňuje pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="1b074-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="1b074-124">[unchecked](../keywords/unchecked.md) – zakáže pro celočíselné operace kontroly přetečení.</span><span class="sxs-lookup"><span data-stu-id="1b074-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="1b074-125">Toto je výchozí chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1b074-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="1b074-126">[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.</span><span class="sxs-lookup"><span data-stu-id="1b074-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="1b074-127">[Delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="1b074-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="1b074-128">[operátor sizeof:](../keywords/sizeof.md) – vrátí velikost v bajtech typ operandu.</span><span class="sxs-lookup"><span data-stu-id="1b074-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="1b074-129">[->](dereference-operator.md) – přístup přes ukazatel v kombinaci s přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="1b074-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="1b074-130">Unární operátory</span><span class="sxs-lookup"><span data-stu-id="1b074-130">Unary operators</span></span>

<span data-ttu-id="1b074-131">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-132">[+ x](addition-operator.md) – vrátí hodnotu x.</span><span class="sxs-lookup"><span data-stu-id="1b074-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="1b074-133">[-x](subtraction-operator.md) – číselné negace.</span><span class="sxs-lookup"><span data-stu-id="1b074-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="1b074-134">[\!x](logical-negation-operator.md) – Logická negace.</span><span class="sxs-lookup"><span data-stu-id="1b074-134">[\!x](logical-negation-operator.md) – logical negation.</span></span>

<span data-ttu-id="1b074-135">[~ x](bitwise-complement-operator.md) – bitového doplňku.</span><span class="sxs-lookup"><span data-stu-id="1b074-135">[~x](bitwise-complement-operator.md) – bitwise complement.</span></span>

<span data-ttu-id="1b074-136">[++ x](increment-operator.md) – předponového.</span><span class="sxs-lookup"><span data-stu-id="1b074-136">[++x](increment-operator.md) – prefix increment.</span></span> <span data-ttu-id="1b074-137">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je větší (obvykle přidá na celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="1b074-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1b074-138">[--x](decrement-operator.md) – předponového.</span><span class="sxs-lookup"><span data-stu-id="1b074-138">[--x](decrement-operator.md) – prefix decrement.</span></span> <span data-ttu-id="1b074-139">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x je jeden méně (obvykle odečte 1 na celé číslo).</span><span class="sxs-lookup"><span data-stu-id="1b074-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1b074-140">[(T) x](invocation-operator.md) – typ přetypování.</span><span class="sxs-lookup"><span data-stu-id="1b074-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="1b074-141">[operátor await](../keywords/await.md) – čeká `Task`.</span><span class="sxs-lookup"><span data-stu-id="1b074-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="1b074-142">[& x](and-operator.md) – adresu.</span><span class="sxs-lookup"><span data-stu-id="1b074-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="1b074-143">[\* x](multiplication-operator.md) – přesměrování.</span><span class="sxs-lookup"><span data-stu-id="1b074-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="1b074-144">Operátory násobení</span><span class="sxs-lookup"><span data-stu-id="1b074-144">Multiplicative operators</span></span>

<span data-ttu-id="1b074-145">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-145">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-146">[x \* y](multiplication-operator.md) – násobení.</span><span class="sxs-lookup"><span data-stu-id="1b074-146">[x \* y](multiplication-operator.md) – multiplication.</span></span>

<span data-ttu-id="1b074-147">[x a y](division-operator.md) – dělení.</span><span class="sxs-lookup"><span data-stu-id="1b074-147">[x / y](division-operator.md) – division.</span></span> <span data-ttu-id="1b074-148">Pokud jsou operandy celých čísel, výsledek je celé číslo zkráceno směrem k nule (například `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="1b074-148">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="1b074-149">[x, % y](remainder-operator.md) – zbytek.</span><span class="sxs-lookup"><span data-stu-id="1b074-149">[x % y](remainder-operator.md) – remainder.</span></span> <span data-ttu-id="1b074-150">Pokud jsou operandy celých čísel, vrátí zbytek dělicí x y.</span><span class="sxs-lookup"><span data-stu-id="1b074-150">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="1b074-151">Pokud `q = x / y` a `r = x % y`, pak `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="1b074-151">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="1b074-152">Operátory sčítání</span><span class="sxs-lookup"><span data-stu-id="1b074-152">Additive operators</span></span>

<span data-ttu-id="1b074-153">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-153">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-154">[x + y](addition-operator.md) – přidání.</span><span class="sxs-lookup"><span data-stu-id="1b074-154">[x + y](addition-operator.md) – addition.</span></span>

<span data-ttu-id="1b074-155">[x-y](subtraction-operator.md) – odčítání.</span><span class="sxs-lookup"><span data-stu-id="1b074-155">[x – y](subtraction-operator.md) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="1b074-156">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="1b074-156">Shift operators</span></span>

<span data-ttu-id="1b074-157">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-157">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-158">[x <\< y](left-shift-operator.md) – posunutí bitů doleva a vyplnit nula na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="1b074-158">[x <\<  y](left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="1b074-159">[x >> y](right-shift-operator.md) – posunutí bitů doprava.</span><span class="sxs-lookup"><span data-stu-id="1b074-159">[x >> y](right-shift-operator.md) – shift bits right.</span></span> <span data-ttu-id="1b074-160">Pokud levý operand `int` nebo `long`, pak levé bity jsou vyplněny na bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="1b074-160">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="1b074-161">Pokud levý operand `uint` nebo `ulong`, pak levé bity jsou vyplněny hodnotou nula.</span><span class="sxs-lookup"><span data-stu-id="1b074-161">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="1b074-162">Operátory relační a typové zkoušky</span><span class="sxs-lookup"><span data-stu-id="1b074-162">Relational and type-testing operators</span></span>

<span data-ttu-id="1b074-163">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-163">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-164">[x \< y](less-than-operator.md) – menší než (true, pokud x je menší než y).</span><span class="sxs-lookup"><span data-stu-id="1b074-164">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="1b074-165">[x > y](greater-than-operator.md) – větší než (true, pokud x je větší než y).</span><span class="sxs-lookup"><span data-stu-id="1b074-165">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="1b074-166">[x \<= y](less-than-equal-operator.md) – menší než nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="1b074-166">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="1b074-167">[x > = y](greater-than-equal-operator.md) – větší než nebo rovna hodnotě.</span><span class="sxs-lookup"><span data-stu-id="1b074-167">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="1b074-168">[je](../keywords/is.md) – typ kompatibility.</span><span class="sxs-lookup"><span data-stu-id="1b074-168">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="1b074-169">Vrátí true, pokud vyhodnocený levý operand může být převeden na typ určený v pravý operand (statického typu).</span><span class="sxs-lookup"><span data-stu-id="1b074-169">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="1b074-170">[jako](../keywords/as.md) – převod typu.</span><span class="sxs-lookup"><span data-stu-id="1b074-170">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="1b074-171">Vrátí levý operand přetypování na typ určený pravý operand (statického typu), ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="1b074-171">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="1b074-172">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="1b074-172">Equality operators</span></span>

<span data-ttu-id="1b074-173">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-173">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-174">[x == y](equality-comparison-operator.md) – rovnosti.</span><span class="sxs-lookup"><span data-stu-id="1b074-174">[x == y](equality-comparison-operator.md) – equality.</span></span> <span data-ttu-id="1b074-175">Ve výchozím nastavení, pro referenční typy jiné než `string`tento vrátí referenční rovnosti (identity test).</span><span class="sxs-lookup"><span data-stu-id="1b074-175">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="1b074-176">Však můžete přetížit typy `==`, takže pokud máte v úmyslu k otestování identity, je nejvhodnější použít `ReferenceEquals` metodu na `object`.</span><span class="sxs-lookup"><span data-stu-id="1b074-176">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="1b074-177">[x! = y](not-equal-operator.md) – není rovno.</span><span class="sxs-lookup"><span data-stu-id="1b074-177">[x != y](not-equal-operator.md) – not equal.</span></span> <span data-ttu-id="1b074-178">Viz komentář `==`.</span><span class="sxs-lookup"><span data-stu-id="1b074-178">See comment for `==`.</span></span> <span data-ttu-id="1b074-179">Pokud typ přetížení `==`, pak musí přetížení `!=`.</span><span class="sxs-lookup"><span data-stu-id="1b074-179">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="1b074-180">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="1b074-180">Logical AND operator</span></span>

<span data-ttu-id="1b074-181">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-181">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-182">[x & y](and-operator.md) – logický operátor or bitový AND.</span><span class="sxs-lookup"><span data-stu-id="1b074-182">[x & y](and-operator.md) – logical or bitwise AND.</span></span> <span data-ttu-id="1b074-183">Obecně můžete s celočíselnými typy a `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="1b074-183">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="1b074-184">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="1b074-184">Logical XOR operator</span></span>

<span data-ttu-id="1b074-185">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-185">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-186">[x ^ y](xor-operator.md) – logické a bitové operace XOR.</span><span class="sxs-lookup"><span data-stu-id="1b074-186">[x ^ y](xor-operator.md) – logical or bitwise XOR.</span></span> <span data-ttu-id="1b074-187">Obecně můžete s celočíselnými typy a `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="1b074-187">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="1b074-188">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="1b074-188">Logical OR operator</span></span>

<span data-ttu-id="1b074-189">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-190">[x &#124; y](or-operator.md) – logické a bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="1b074-190">[x &#124; y](or-operator.md) – logical or bitwise OR.</span></span> <span data-ttu-id="1b074-191">Obecně můžete s celočíselnými typy a `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="1b074-191">You can generally use this with integer types and `enum` types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="1b074-192">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="1b074-192">Conditional AND operator</span></span>

<span data-ttu-id="1b074-193">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-193">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-194">[x & & y](conditional-and-operator.md) – logickým operátorem a.</span><span class="sxs-lookup"><span data-stu-id="1b074-194">[x && y](conditional-and-operator.md) – logical AND.</span></span> <span data-ttu-id="1b074-195">Pokud je první operand vyhodnocen na hodnotu false, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="1b074-195">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="1b074-196">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="1b074-196">Conditional OR operator</span></span>

<span data-ttu-id="1b074-197">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-197">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-198">[x &#124; &#124; y](conditional-or-operator.md) – logický operátor OR.</span><span class="sxs-lookup"><span data-stu-id="1b074-198">[x &#124;&#124; y](conditional-or-operator.md) – logical OR.</span></span> <span data-ttu-id="1b074-199">Pokud je první operand vyhodnocen na hodnotu true, pak C# není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="1b074-199">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="1b074-200">Operátoru nulového sjednocení</span><span class="sxs-lookup"><span data-stu-id="1b074-200">Null-coalescing operator</span></span>

<span data-ttu-id="1b074-201">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-201">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-202">[x?? y](null-coalescing-operator.md) – vrátí `x` jde-li jinou hodnotu než`null`; v opačném případě vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="1b074-202">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="1b074-203">Podmíněný operátor</span><span class="sxs-lookup"><span data-stu-id="1b074-203">Conditional operator</span></span>

<span data-ttu-id="1b074-204">Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-204">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-205">[t? x: y](conditional-operator.md) – Pokud test `t` vyhodnotí jako true, pak vyhodnotí a vrátí `x`; v opačném případě vyhodnotí a vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="1b074-205">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="1b074-206">Operátory přiřazení a Lambda</span><span class="sxs-lookup"><span data-stu-id="1b074-206">Assignment and Lambda operators</span></span>

<span data-ttu-id="1b074-207">Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1b074-207">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1b074-208">[x = y](assignment-operator.md) – přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1b074-208">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="1b074-209">[x += y](addition-assignment-operator.md) – přírůstku.</span><span class="sxs-lookup"><span data-stu-id="1b074-209">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="1b074-210">Přidat hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-210">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1b074-211">Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# přidá jako obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1b074-211">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="1b074-212">[x-= y](subtraction-assignment-operator.md) – sníží.</span><span class="sxs-lookup"><span data-stu-id="1b074-212">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="1b074-213">Odečte hodnotu `y` od hodnoty `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-213">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1b074-214">Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# odebere jako obslužné rutiny události</span><span class="sxs-lookup"><span data-stu-id="1b074-214">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>

<span data-ttu-id="1b074-215">[x \* = y](multiplication-assignment-operator.md) – přiřazení násobení.</span><span class="sxs-lookup"><span data-stu-id="1b074-215">[x \*= y](multiplication-assignment-operator.md) – multiplication assignment.</span></span> <span data-ttu-id="1b074-216">Vynásobí hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-216">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-217">[x / = y](division-assignment-operator.md) – přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="1b074-217">[x /= y](division-assignment-operator.md) – division assignment.</span></span> <span data-ttu-id="1b074-218">Vydělí hodnotu `x` hodnotou `y`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-218">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-219">[x % = y](remainder-assignment-operator.md) – remainder přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1b074-219">[x %= y](remainder-assignment-operator.md) – remainder assignment.</span></span> <span data-ttu-id="1b074-220">Vydělí hodnotu `x` hodnotou `y`, uložení zbytku v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-220">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-221">[x & = y](and-assignment-operator.md) – a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1b074-221">[x &= y](and-assignment-operator.md) – AND assignment.</span></span> <span data-ttu-id="1b074-222">A hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-222">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-223">[x &#124;= y](or-assignment-operator.md) – přiřazení OR.</span><span class="sxs-lookup"><span data-stu-id="1b074-223">[x &#124;= y](or-assignment-operator.md) – OR assignment.</span></span> <span data-ttu-id="1b074-224">NEBO hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-224">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-225">[x ^ = y](xor-assignment-operator.md) – XOR přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1b074-225">[x ^= y](xor-assignment-operator.md) – XOR assignment.</span></span> <span data-ttu-id="1b074-226">XOR hodnotu z `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-226">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-227">[x << = y](left-shift-assignment-operator.md) – přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="1b074-227">[x <<= y](left-shift-assignment-operator.md) – left-shift assignment.</span></span> <span data-ttu-id="1b074-228">Posune hodnotu `x` vlevo po `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-228">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-229">[x >> = y](right-shift-assignment-operator.md) – přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="1b074-229">[x >>= y](right-shift-assignment-operator.md) – right-shift assignment.</span></span> <span data-ttu-id="1b074-230">Posune hodnotu `x` právo `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b074-230">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1b074-231">[=>](lambda-operator.md) – deklaraci lambda.</span><span class="sxs-lookup"><span data-stu-id="1b074-231">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="arithmetic-overflow"></a><span data-ttu-id="1b074-232">Aritmetické přetečení</span><span class="sxs-lookup"><span data-stu-id="1b074-232">Arithmetic overflow</span></span>

<span data-ttu-id="1b074-233">Aritmetické operátory ([+](addition-operator.md), [ - ](subtraction-operator.md), [ \* ](multiplication-operator.md), [ / ](division-operator.md)) může výsledky, které jsou mimo rozsah možných hodnot pro uvedeného číselného typu.</span><span class="sxs-lookup"><span data-stu-id="1b074-233">The arithmetic operators ([+](addition-operator.md), [-](subtraction-operator.md), [\*](multiplication-operator.md), [/](division-operator.md)) can produce results that are outside the range of possible values for the numeric type involved.</span></span> <span data-ttu-id="1b074-234">By měla odkazovat na část na konkrétní operátor podrobnosti, ale obecně:</span><span class="sxs-lookup"><span data-stu-id="1b074-234">You should refer to the section on a particular operator for details, but in general:</span></span>

- <span data-ttu-id="1b074-235">Aritmetické přetečení celého čísla buď vyvolá <xref:System.OverflowException> nebo zruší nejvýznamnější části výsledku.</span><span class="sxs-lookup"><span data-stu-id="1b074-235">Integer arithmetic overflow either throws an <xref:System.OverflowException> or discards the most significant bits of the result.</span></span> <span data-ttu-id="1b074-236">Dělení celého čísla nulou vždy vyvolá <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="1b074-236">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

   <span data-ttu-id="1b074-237">Pokud dojde k přetečení celého čísla, co se stane, závisí na kontextu spuštění, který může být [zaškrtnuté nebo nezaškrtnuté](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="1b074-237">When integer overflow occurs, what happens depends on the execution context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="1b074-238">Ve zkontrolovaném kontextu <xref:System.OverflowException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1b074-238">In a checked context, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="1b074-239">V nekontrolovaném kontextu jsou nejvýznamnější části výsledku ignorovány a provádění bude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="1b074-239">In an unchecked context, the most significant bits of the result are discarded and execution continues.</span></span> <span data-ttu-id="1b074-240">Proto jazyk C# umožňuje volbu zpracování nebo ignorování přetečení.</span><span class="sxs-lookup"><span data-stu-id="1b074-240">Thus, C# gives you the choice of handling or ignoring overflow.</span></span> <span data-ttu-id="1b074-241">Ve výchozím nastavení, aritmetické operace prováděny v *Nekontrolovaná* kontextu.</span><span class="sxs-lookup"><span data-stu-id="1b074-241">By default, arithmetic operations occur in an *unchecked* context.</span></span>

   <span data-ttu-id="1b074-242">Kromě aritmetických operací, přetypování integrálového typu na integrálový typ může způsobit přetečení (jako je například, pokud přetypovat [dlouhé](../keywords/long.md) do [int](../keywords/int.md)) a můžou se nekontrolovaným prováděním.</span><span class="sxs-lookup"><span data-stu-id="1b074-242">In addition to the arithmetic operations, integral-type to integral-type casts can cause overflow (such as when you cast a [long](../keywords/long.md) to an [int](../keywords/int.md)), and are subject to checked or unchecked execution.</span></span> <span data-ttu-id="1b074-243">Nicméně bitové operátory a operátory posunutí nikdy nezpůsobí přetečení.</span><span class="sxs-lookup"><span data-stu-id="1b074-243">However, bitwise operators and shift operators never cause overflow.</span></span>

- <span data-ttu-id="1b074-244">Plovoucí aritmetické přetečení nebo dělení nulou nikdy nevyvolá výjimku, protože typy s plovoucí desetinnou čárkou jsou založeny na standardu IEEE 754 a tak mají opatření představující nekonečno a NaN (není číslo).</span><span class="sxs-lookup"><span data-stu-id="1b074-244">Floating-point arithmetic overflow or division by zero never throws an exception, because floating-point types are based on IEEE 754 and so have provisions for representing infinity and NaN (Not a Number).</span></span>

- <span data-ttu-id="1b074-245">[Desetinné](../keywords/decimal.md) aritmetické přetečení vždy vyvolá <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="1b074-245">[Decimal](../keywords/decimal.md) arithmetic overflow always throws an <xref:System.OverflowException>.</span></span> <span data-ttu-id="1b074-246">Dělení desetinného čísla nulou vždy vyvolá <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="1b074-246">Decimal division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b074-247">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b074-247">See also</span></span>

- [<span data-ttu-id="1b074-248">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1b074-248">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1b074-249">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1b074-249">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1b074-250">C#</span><span class="sxs-lookup"><span data-stu-id="1b074-250">C#</span></span>](../../index.md)
- [<span data-ttu-id="1b074-251">Přetížitelné operátory</span><span class="sxs-lookup"><span data-stu-id="1b074-251">Overloadable Operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="1b074-252">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1b074-252">C# Keywords</span></span>](../keywords/index.md)