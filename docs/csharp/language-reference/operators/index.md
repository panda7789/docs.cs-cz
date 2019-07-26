---
title: C#operátory – C# referenční informace
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
ms.openlocfilehash: b6a1cc3ced3205037eb5b83ac3841efbfbd1b5b9
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331213"
---
# <a name="c-operators-c-reference"></a><span data-ttu-id="72965-102">C#operátory (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="72965-102">C# operators (C# reference)</span></span>

<span data-ttu-id="72965-103">C#poskytuje několik předdefinovaných operátorů podporovaných integrovanými typy.</span><span class="sxs-lookup"><span data-stu-id="72965-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="72965-104">Například aritmetické [operátory](arithmetic-operators.md) provádějí aritmetické operace s operandy předdefinovaných číselných typů a logické [logické operátory](boolean-logical-operators.md) provádějí logické operace s logickými [operandy](../keywords/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="72965-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="72965-105">Uživatelsky definovaný typ může přetížit určité operátory pro definování odpovídajícího chování pro operandy daného typu.</span><span class="sxs-lookup"><span data-stu-id="72965-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="72965-106">Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="72965-106">For more information, see [Operator overloading](operator-overloading.md).</span></span>

<span data-ttu-id="72965-107">V následujících částech jsou uvedeny C# operátory začínající nejvyšší prioritou na nejnižší.</span><span class="sxs-lookup"><span data-stu-id="72965-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="72965-108">Operátory v jednotlivých oddílech sdílí stejnou úroveň priority.</span><span class="sxs-lookup"><span data-stu-id="72965-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="72965-109">Primární operátory</span><span class="sxs-lookup"><span data-stu-id="72965-109">Primary operators</span></span>

<span data-ttu-id="72965-110">Toto jsou operátory s nejvyšší prioritou.</span><span class="sxs-lookup"><span data-stu-id="72965-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="72965-111">[x. y](member-access-operators.md#member-access-operator-) – přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="72965-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="72965-112">[x?. y](member-access-operators.md#null-conditional-operators--and-) – null přístup podmíněného člena.</span><span class="sxs-lookup"><span data-stu-id="72965-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="72965-113">Vrátí `null` , zda je na levé straně operand vyhodnocen `null`.</span><span class="sxs-lookup"><span data-stu-id="72965-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="72965-114">[x? [y]](member-access-operators.md#null-conditional-operators--and-) – podmíněný element pole nebo typ přístupu indexeru typu null.</span><span class="sxs-lookup"><span data-stu-id="72965-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="72965-115">Vrátí `null` , zda je na levé straně operand vyhodnocen `null`.</span><span class="sxs-lookup"><span data-stu-id="72965-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="72965-116">[f (x)](member-access-operators.md#invocation-operator-) – volání metody nebo volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="72965-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="72965-117">přístup k elementu [&#91;x&#93; ](member-access-operators.md#indexer-operator-) -Array nebo k indexeru typů.</span><span class="sxs-lookup"><span data-stu-id="72965-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="72965-118">[x + +](arithmetic-operators.md#increment-operator-) – přírůstek přípony</span><span class="sxs-lookup"><span data-stu-id="72965-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="72965-119">Vrátí hodnotu x a poté aktualizuje umístění úložiště hodnotou x, která je jedna větší (obvykle přidá celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="72965-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="72965-120">[x--](arithmetic-operators.md#decrement-operator---) – – snížení přípony</span><span class="sxs-lookup"><span data-stu-id="72965-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="72965-121">Vrátí hodnotu x a poté aktualizuje umístění úložiště hodnotou x, která je menší (obvykle se odečte celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="72965-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="72965-122">[nové](new-operator.md) – vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="72965-122">[new](new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="72965-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) – vrátí <xref:System.Type> objekt představující operand.</span><span class="sxs-lookup"><span data-stu-id="72965-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="72965-124">[checked](../keywords/checked.md) – povolí kontrolu přetečení pro celočíselné operace.</span><span class="sxs-lookup"><span data-stu-id="72965-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="72965-125">[nezaškrtnuto](../keywords/unchecked.md) – zakáže kontrolu přetečení pro celočíselné operace.</span><span class="sxs-lookup"><span data-stu-id="72965-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="72965-126">Toto je výchozí chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="72965-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="72965-127">[Default (T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.</span><span class="sxs-lookup"><span data-stu-id="72965-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="72965-128">[nameof](nameof.md) – získá jednoduchý (nekvalifikovaný) název proměnné, typu nebo členu jako konstantní řetězec.</span><span class="sxs-lookup"><span data-stu-id="72965-128">[nameof](nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="72965-129">[Delegate](delegate-operator.md) – deklaruje a vrátí instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="72965-129">[delegate](delegate-operator.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="72965-130">[sizeof](../keywords/sizeof.md) – vrátí velikost operandu typu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="72965-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="72965-131">[stackalloc](stackalloc.md) – přidělí blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="72965-131">[stackalloc](stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="72965-132">[->](pointer-related-operators.md#pointer-member-access-operator--)– nepřímý odkaz v kombinaci s přístupem členů.</span><span class="sxs-lookup"><span data-stu-id="72965-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="72965-133">Unární operátory</span><span class="sxs-lookup"><span data-stu-id="72965-133">Unary operators</span></span>

<span data-ttu-id="72965-134">Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-135">[+ x](addition-operator.md) – vrátí hodnotu x.</span><span class="sxs-lookup"><span data-stu-id="72965-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="72965-136">[-x](subtraction-operator.md) – číselná negace.</span><span class="sxs-lookup"><span data-stu-id="72965-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="72965-137">x – logická negace. [ \!](boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="72965-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="72965-138">[~ ×](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitový doplněk.</span><span class="sxs-lookup"><span data-stu-id="72965-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="72965-139">[+ + x](arithmetic-operators.md#increment-operator-) – přírůstek předpony.</span><span class="sxs-lookup"><span data-stu-id="72965-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="72965-140">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je jedna větší (obvykle přidá celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="72965-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="72965-141">[--x](arithmetic-operators.md#decrement-operator---) – snížení předpony.</span><span class="sxs-lookup"><span data-stu-id="72965-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="72965-142">Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je o jednu méně (obvykle odečte celé číslo 1).</span><span class="sxs-lookup"><span data-stu-id="72965-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="72965-143">[(T) x](type-testing-and-conversion-operators.md#cast-operator-) – přetypování typu.</span><span class="sxs-lookup"><span data-stu-id="72965-143">[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – type casting.</span></span>

<span data-ttu-id="72965-144">[await](../keywords/await.md) – čeká na `Task`.</span><span class="sxs-lookup"><span data-stu-id="72965-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="72965-145">[& x](pointer-related-operators.md#address-of-operator-) – adresa proměnné.</span><span class="sxs-lookup"><span data-stu-id="72965-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="72965-146">[\* x](pointer-related-operators.md#pointer-indirection-operator-) – indirekce ukazatele nebo přereference.</span><span class="sxs-lookup"><span data-stu-id="72965-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="72965-147">[true – operátor](true-false-operators.md) – vrátí [](../keywords/bool.md) logickou `true` hodnotu pro indikaci, že operand má jednoznačně hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="72965-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="72965-148">[false – operátor](true-false-operators.md) – vrátí [](../keywords/bool.md) logickou `true` hodnotu pro indikaci, že operand je jednoznačně nepravdivý.</span><span class="sxs-lookup"><span data-stu-id="72965-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="72965-149">Operátory násobení</span><span class="sxs-lookup"><span data-stu-id="72965-149">Multiplicative operators</span></span>

<span data-ttu-id="72965-150">Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – násobení.</span><span class="sxs-lookup"><span data-stu-id="72965-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="72965-152">[x/y](arithmetic-operators.md#division-operator-) – dělení.</span><span class="sxs-lookup"><span data-stu-id="72965-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="72965-153">Pokud jsou operandy celé číslo, výsledkem je celé číslo, které je zkráceno směrem k nule ( `-7 / 2 is -3`například).</span><span class="sxs-lookup"><span data-stu-id="72965-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="72965-154">[x% y](arithmetic-operators.md#remainder-operator-) – zbytek</span><span class="sxs-lookup"><span data-stu-id="72965-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="72965-155">Pokud jsou operandy celé číslo, vrátí zbytek dělení x hodnotou y.</span><span class="sxs-lookup"><span data-stu-id="72965-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="72965-156">Pokud `q = x / y` a `r = x % y`, potom `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="72965-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="72965-157">Operátory sčítání</span><span class="sxs-lookup"><span data-stu-id="72965-157">Additive operators</span></span>

<span data-ttu-id="72965-158">Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-159">[x + y](arithmetic-operators.md#addition-operator-) – přidání.</span><span class="sxs-lookup"><span data-stu-id="72965-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="72965-160">[x – y](arithmetic-operators.md#subtraction-operator--) – odčítání.</span><span class="sxs-lookup"><span data-stu-id="72965-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="72965-161">Operátory posunutí</span><span class="sxs-lookup"><span data-stu-id="72965-161">Shift operators</span></span>

<span data-ttu-id="72965-162">Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-163">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – klávesy SHIFT vlevo a na pravé straně se vyplní nula.</span><span class="sxs-lookup"><span data-stu-id="72965-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="72965-164">[x > > y](bitwise-and-shift-operators.md#right-shift-operator-) – Shift + šipka doprava.</span><span class="sxs-lookup"><span data-stu-id="72965-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="72965-165">Pokud je `int` levý operand nebo `long`, pak jsou levé bity vyplněny znaménkem.</span><span class="sxs-lookup"><span data-stu-id="72965-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="72965-166">Pokud je `uint` levý operand nebo `ulong`, pak jsou levé bity vyplněny nulou.</span><span class="sxs-lookup"><span data-stu-id="72965-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="72965-167">Relační operátory a operátory testování typů</span><span class="sxs-lookup"><span data-stu-id="72965-167">Relational and type-testing operators</span></span>

<span data-ttu-id="72965-168">Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-169">[ x\< y](comparison-operators.md#less-than-operator-) – menší než (true, pokud je x menší než y).</span><span class="sxs-lookup"><span data-stu-id="72965-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="72965-170">[x > y](comparison-operators.md#greater-than-operator-) – větší než (true, pokud je x větší než y).</span><span class="sxs-lookup"><span data-stu-id="72965-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="72965-171">[ x\<= y](comparison-operators.md#less-than-or-equal-operator-) – je menší nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="72965-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="72965-172">[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – je větší než nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="72965-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="72965-173">[je](type-testing-and-conversion-operators.md#is-operator) – kompatibilita typů.</span><span class="sxs-lookup"><span data-stu-id="72965-173">[is](type-testing-and-conversion-operators.md#is-operator) – type compatibility.</span></span> <span data-ttu-id="72965-174">Vrátí `true` , zda je možné vyhodnocený levý operand přetypovat na typ zadaný pomocí pravého operandu.</span><span class="sxs-lookup"><span data-stu-id="72965-174">Returns `true` if the evaluated left operand can be cast to the type specified by the right operand.</span></span>

<span data-ttu-id="72965-175">převod [jako](type-testing-and-conversion-operators.md#as-operator) – typ.</span><span class="sxs-lookup"><span data-stu-id="72965-175">[as](type-testing-and-conversion-operators.md#as-operator) – type conversion.</span></span> <span data-ttu-id="72965-176">Vrátí levý operand přetypování na typ určený pravý operandem, ale `as` vrátí `null` , kde `(T)x` by vyvolala výjimku.</span><span class="sxs-lookup"><span data-stu-id="72965-176">Returns the left operand cast to the type specified by the right operand, but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="72965-177">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="72965-177">Equality operators</span></span>

<span data-ttu-id="72965-178">Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-179">[x = = y](equality-operators.md#equality-operator-) – rovnost.</span><span class="sxs-lookup"><span data-stu-id="72965-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="72965-180">Ve výchozím nastavení pro jiné typy odkazů než `string`, tato funkce vrátí rovnost odkazů (test identity).</span><span class="sxs-lookup"><span data-stu-id="72965-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="72965-181">Typy však mohou přetížit `==`, takže pokud je váš záměr testovat identitu, je nejvhodnější `ReferenceEquals` použít metodu na `object`.</span><span class="sxs-lookup"><span data-stu-id="72965-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="72965-182">[x! = y](equality-operators.md#inequality-operator-) – nerovná se</span><span class="sxs-lookup"><span data-stu-id="72965-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="72965-183">Viz komentář pro `==`.</span><span class="sxs-lookup"><span data-stu-id="72965-183">See comment for `==`.</span></span> <span data-ttu-id="72965-184">Je-li typ přetížen `==`, je nutné jej přetížit. `!=`</span><span class="sxs-lookup"><span data-stu-id="72965-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="72965-185">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="72965-185">Logical AND operator</span></span>

<span data-ttu-id="72965-186">Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-187">`x & y`– [logická a](boolean-logical-operators.md#logical-and-operator-) pro `bool` operandy nebo [bitové logické a](bitwise-and-shift-operators.md#logical-and-operator-) pro operandy integrálních typů.</span><span class="sxs-lookup"><span data-stu-id="72965-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="72965-188">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="72965-188">Logical XOR operator</span></span>

<span data-ttu-id="72965-189">Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-190">`x ^ y`– [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) pro `bool` operandy nebo [bitové logické XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) pro operandy integrálních typů.</span><span class="sxs-lookup"><span data-stu-id="72965-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="72965-191">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="72965-191">Logical OR operator</span></span>

<span data-ttu-id="72965-192">Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-193">`x | y`– [logická nebo](boolean-logical-operators.md#logical-or-operator-) pro `bool` operandy nebo [bitové logické číslo nebo](bitwise-and-shift-operators.md#logical-or-operator-) pro operandy integrálních typů.</span><span class="sxs-lookup"><span data-stu-id="72965-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="72965-194">Podmíněný operátor AND</span><span class="sxs-lookup"><span data-stu-id="72965-194">Conditional AND operator</span></span>

<span data-ttu-id="72965-195">Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-196">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – Logical a.</span><span class="sxs-lookup"><span data-stu-id="72965-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="72965-197">Pokud `x` se vyhodnotí `false`jako `y` , pak se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="72965-197">If `x` evaluates to `false`, then `y` is not evaluated.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="72965-198">Podmíněný operátor OR</span><span class="sxs-lookup"><span data-stu-id="72965-198">Conditional OR operator</span></span>

<span data-ttu-id="72965-199">Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-200">[ &#124; x &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logická nebo.</span><span class="sxs-lookup"><span data-stu-id="72965-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="72965-201">Pokud `x` se vyhodnotí `true`jako `y` , pak se nevyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="72965-201">If `x` evaluates to `true`, then `y` is not evaluated.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="72965-202">Operátor slučování null</span><span class="sxs-lookup"><span data-stu-id="72965-202">Null-coalescing operator</span></span>

<span data-ttu-id="72965-203">Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-204">[x?? y](null-coalescing-operator.md) – vrátí `x` , pokud je`null`to jiné než; v opačném případě vrátí `y`.</span><span class="sxs-lookup"><span data-stu-id="72965-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="72965-205">Podmíněný operátor</span><span class="sxs-lookup"><span data-stu-id="72965-205">Conditional operator</span></span>

<span data-ttu-id="72965-206">Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-207">[t? x: y](conditional-operator.md) – Pokud se `t` test vyhodnotí jako true, pak se `x`vyhodnotí a vrátí. `y`jinak se vyhodnotí a vrátí.</span><span class="sxs-lookup"><span data-stu-id="72965-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="72965-208">Operátory přiřazení a lambda</span><span class="sxs-lookup"><span data-stu-id="72965-208">Assignment and lambda operators</span></span>

<span data-ttu-id="72965-209">Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.</span><span class="sxs-lookup"><span data-stu-id="72965-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="72965-210">[x = y](assignment-operator.md) – přiřazení.</span><span class="sxs-lookup"><span data-stu-id="72965-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="72965-211">[x + = y](arithmetic-operators.md#compound-assignment) – přírůstek</span><span class="sxs-lookup"><span data-stu-id="72965-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="72965-212">Přidejte hodnotu `y` do `x`hodnoty, uložte výsledek do `x`a vraťte novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="72965-213">Pokud `x` Určuje C# [událost, musí být](../keywords/event.md)vhodná metoda, která je přidána jako obslužná rutina události. `y`</span><span class="sxs-lookup"><span data-stu-id="72965-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="72965-214">[x-= y](arithmetic-operators.md#compound-assignment) – snížení.</span><span class="sxs-lookup"><span data-stu-id="72965-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="72965-215">Odečte hodnotu `y` z `x`hodnoty, uloží výsledek do `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="72965-216">Pokud `x` Určuje C# [událost, musí být](../keywords/event.md)vhodná metoda, která se odebere jako obslužná rutina události. `y`</span><span class="sxs-lookup"><span data-stu-id="72965-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="72965-217">[x \* = y](arithmetic-operators.md#compound-assignment) – přiřazení násobení.</span><span class="sxs-lookup"><span data-stu-id="72965-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="72965-218">Vynásobte hodnotu `y` `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-219">přiřazení divize [x/= y](arithmetic-operators.md#compound-assignment) – dělení.</span><span class="sxs-lookup"><span data-stu-id="72965-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="72965-220">Vydělte hodnotu `x` `y`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-221">[x% = y](arithmetic-operators.md#compound-assignment) – přiřazení zbytku</span><span class="sxs-lookup"><span data-stu-id="72965-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="72965-222">Vydělte hodnotu `x` `y`hodnotou, uložte zbytek do `x`a vraťte novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-223">[x & = y](boolean-logical-operators.md#compound-assignment) – a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="72965-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="72965-224">A hodnotu `y` s `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – nebo přiřazení.</span><span class="sxs-lookup"><span data-stu-id="72965-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="72965-226">Nebo hodnotu `y` s `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-227">[x ^ = y](boolean-logical-operators.md#compound-assignment) – přiřazení XOR</span><span class="sxs-lookup"><span data-stu-id="72965-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="72965-228">XOR hodnotu `y` s `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-229">[x < < = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="72965-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="72965-230">Posune hodnotu `x` vlevo o `y` místa, uloží výsledek do `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-231">[x > > = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="72965-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="72965-232">Posune hodnotu `x` vpravo podle `y` míst, uloží výsledek do `x`a vrátí novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72965-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="72965-233">[=>](lambda-operator.md)– deklarace lambda</span><span class="sxs-lookup"><span data-stu-id="72965-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="72965-234">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72965-234">See also</span></span>

- [<span data-ttu-id="72965-235">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="72965-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="72965-236">Operátory</span><span class="sxs-lookup"><span data-stu-id="72965-236">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)
