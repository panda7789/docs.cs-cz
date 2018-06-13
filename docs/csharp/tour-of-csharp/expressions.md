---
title: C# výrazy - přehled používání jazyka C#
description: výrazy, operandy a operátory jsou stavební bloky jazyka C#
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 8fa1c5d0464644b26eb457bca8ecaf007c288f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352296"
---
# <a name="expressions"></a><span data-ttu-id="d8e45-103">Výrazy</span><span class="sxs-lookup"><span data-stu-id="d8e45-103">Expressions</span></span>

<span data-ttu-id="d8e45-104">*Výrazy* se vytvářejí na základě *operandy* a *operátory*.</span><span class="sxs-lookup"><span data-stu-id="d8e45-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="d8e45-105">Operátory výrazu znamenat operací, které chcete použít pro operandy.</span><span class="sxs-lookup"><span data-stu-id="d8e45-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="d8e45-106">Příklady operátory `+`, `-`, `*`, `/`, a `new`.</span><span class="sxs-lookup"><span data-stu-id="d8e45-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="d8e45-107">Příklady operandy: literály, pole, místní proměnné a výrazy.</span><span class="sxs-lookup"><span data-stu-id="d8e45-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="d8e45-108">Pokud některý výraz obsahuje více operátorů *přednost před* operátory ovládací prvky pořadí, ve kterém jsou jednotlivé operátory vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="d8e45-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="d8e45-109">Například výraz `x + y * z` je vyhodnoceno jako `x + (y * z)` protože `*` operátor má vyšší prioritu než `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="d8e45-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="d8e45-110">Když dojde k operand mezi dva operátory se stejnou prioritou, *asociativnost* operátory ovládací prvky pořadí, ve kterém jsou prováděny operace:</span><span class="sxs-lookup"><span data-stu-id="d8e45-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="d8e45-111">S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="d8e45-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="d8e45-112">Například `x + y + z` je vyhodnoceno jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="d8e45-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="d8e45-113">Operátory přiřazení a podmíněný operátor (`?:`) jsou *zprava asociativní*, což znamená, že operací zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="d8e45-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="d8e45-114">Například `x = y = z` je vyhodnoceno jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="d8e45-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="d8e45-115">Přednost a asociativnost se dá řídit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="d8e45-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="d8e45-116">Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidává výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a potom vynásobí výsledek podle `z`.</span><span class="sxs-lookup"><span data-stu-id="d8e45-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="d8e45-117">Většina operátory mohou být *přetížený*.</span><span class="sxs-lookup"><span data-stu-id="d8e45-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="d8e45-118">Přetížení operátoru umožňuje implementace uživatelem definovaný operátor zadat pro operace, kde jsou jedno nebo obě operandy typu uživatelem definované třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="d8e45-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="d8e45-119">Následující možnost shrne operátory jazyka C# na, výpis kategorií operátor v pořadí podle priority od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="d8e45-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="d8e45-120">Operátory ve stejné kategorii nemá přednost.</span><span class="sxs-lookup"><span data-stu-id="d8e45-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="d8e45-121">V rámci každé kategorie je seznam výrazů v dané kategorii společně s popisem příslušného typu výraz.</span><span class="sxs-lookup"><span data-stu-id="d8e45-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="d8e45-122">primární</span><span class="sxs-lookup"><span data-stu-id="d8e45-122">Primary</span></span>
    - <span data-ttu-id="d8e45-123">`x.m`: Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="d8e45-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="d8e45-124">`x(...)`: Metoda a delegáta volání</span><span class="sxs-lookup"><span data-stu-id="d8e45-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="d8e45-125">`x[...]`: Pole a indexer přístup</span><span class="sxs-lookup"><span data-stu-id="d8e45-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="d8e45-126">`x++`: Přírůstek po</span><span class="sxs-lookup"><span data-stu-id="d8e45-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="d8e45-127">`x--`: Po snížení</span><span class="sxs-lookup"><span data-stu-id="d8e45-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="d8e45-128">`new T(...)`: Objekt a delegovat vytvoření</span><span class="sxs-lookup"><span data-stu-id="d8e45-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="d8e45-129">`new T(...){...}`: Vytvoření objektu pomocí inicializátoru</span><span class="sxs-lookup"><span data-stu-id="d8e45-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="d8e45-130">`new {...}`: Inicializátor anonymní objekt</span><span class="sxs-lookup"><span data-stu-id="d8e45-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="d8e45-131">`new T[...]`: Při vytváření pole</span><span class="sxs-lookup"><span data-stu-id="d8e45-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="d8e45-132">`typeof(T)`: Získat <xref:System.Type> objekt pro `T`</span><span class="sxs-lookup"><span data-stu-id="d8e45-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="d8e45-133">`checked(x)`: Výraz v kontextu zaškrtnuté vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="d8e45-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="d8e45-134">`unchecked(x)`: Vyhodnocení výrazu v kontextu nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="d8e45-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="d8e45-135">`default(T)`: Výchozí hodnota typu získat `T`</span><span class="sxs-lookup"><span data-stu-id="d8e45-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="d8e45-136">`delegate {...}`: Anonymní funkce (anonymní metoda)</span><span class="sxs-lookup"><span data-stu-id="d8e45-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="d8e45-137">Unární</span><span class="sxs-lookup"><span data-stu-id="d8e45-137">Unary</span></span>
    - <span data-ttu-id="d8e45-138">`+x`: Identity</span><span class="sxs-lookup"><span data-stu-id="d8e45-138">`+x`: Identity</span></span>
    - <span data-ttu-id="d8e45-139">`-x`: Negace</span><span class="sxs-lookup"><span data-stu-id="d8e45-139">`-x`: Negation</span></span>
    - <span data-ttu-id="d8e45-140">`!x`: Logická negace</span><span class="sxs-lookup"><span data-stu-id="d8e45-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="d8e45-141">`~x`: Bitovou negaci</span><span class="sxs-lookup"><span data-stu-id="d8e45-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="d8e45-142">`++x`: Přírůstek před</span><span class="sxs-lookup"><span data-stu-id="d8e45-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="d8e45-143">`--x`: Snížení před</span><span class="sxs-lookup"><span data-stu-id="d8e45-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="d8e45-144">`(T)x`: Explicitně převést `x` na typ `T`</span><span class="sxs-lookup"><span data-stu-id="d8e45-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="d8e45-145">`await x`: Asynchronně počkejte `x` k dokončení</span><span class="sxs-lookup"><span data-stu-id="d8e45-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="d8e45-146">Multiplikativní</span><span class="sxs-lookup"><span data-stu-id="d8e45-146">Multiplicative</span></span>
    - <span data-ttu-id="d8e45-147">`x * y`: Násobení</span><span class="sxs-lookup"><span data-stu-id="d8e45-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="d8e45-148">`x / y`: Dělení</span><span class="sxs-lookup"><span data-stu-id="d8e45-148">`x / y`: Division</span></span>
    - <span data-ttu-id="d8e45-149">`x % y`: Zbývající</span><span class="sxs-lookup"><span data-stu-id="d8e45-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="d8e45-150">Doplňkové</span><span class="sxs-lookup"><span data-stu-id="d8e45-150">Additive</span></span>
    - <span data-ttu-id="d8e45-151">`x + y`: Zřetězení řetězců přidání, kombinace delegáta</span><span class="sxs-lookup"><span data-stu-id="d8e45-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="d8e45-152">`x – y`: Odčítání, odebrání delegáta</span><span class="sxs-lookup"><span data-stu-id="d8e45-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="d8e45-153">Posunutí</span><span class="sxs-lookup"><span data-stu-id="d8e45-153">Shift</span></span>
    - <span data-ttu-id="d8e45-154">`x << y`: Posunutí doleva</span><span class="sxs-lookup"><span data-stu-id="d8e45-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="d8e45-155">`x >> y`: Posunutí doprava</span><span class="sxs-lookup"><span data-stu-id="d8e45-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="d8e45-156">Relační a typ testování</span><span class="sxs-lookup"><span data-stu-id="d8e45-156">Relational and type testing</span></span>
    - <span data-ttu-id="d8e45-157">`x < y`: Menší než</span><span class="sxs-lookup"><span data-stu-id="d8e45-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="d8e45-158">`x > y`: Větší než</span><span class="sxs-lookup"><span data-stu-id="d8e45-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="d8e45-159">`x <= y`: Menší než nebo rovno</span><span class="sxs-lookup"><span data-stu-id="d8e45-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="d8e45-160">`x >= y`: Větší než nebo rovno</span><span class="sxs-lookup"><span data-stu-id="d8e45-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="d8e45-161">`x is T`: Návratový `true` Pokud `x` je `T`, `false` jinak</span><span class="sxs-lookup"><span data-stu-id="d8e45-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="d8e45-162">`x as T`: Návratový `x` zadán jako `T`, nebo `null` Pokud `x` není `T`</span><span class="sxs-lookup"><span data-stu-id="d8e45-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="d8e45-163">Rovnost</span><span class="sxs-lookup"><span data-stu-id="d8e45-163">Equality</span></span>
    - <span data-ttu-id="d8e45-164">`x == y`: Rovná</span><span class="sxs-lookup"><span data-stu-id="d8e45-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="d8e45-165">`x != y`: Není rovno</span><span class="sxs-lookup"><span data-stu-id="d8e45-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="d8e45-166">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="d8e45-166">Logical AND</span></span>
    - <span data-ttu-id="d8e45-167">`x & y`: Celé číslo bitové a boolean logické a</span><span class="sxs-lookup"><span data-stu-id="d8e45-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="d8e45-168">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="d8e45-168">Logical XOR</span></span>
    - <span data-ttu-id="d8e45-169">`x ^ y`: Bitové operace XOR celé číslo, logickou logické XOR</span><span class="sxs-lookup"><span data-stu-id="d8e45-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="d8e45-170">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="d8e45-170">Logical OR</span></span>
    - <span data-ttu-id="d8e45-171">`x | y`: Celé číslo bitové nebo logická hodnota logické nebo</span><span class="sxs-lookup"><span data-stu-id="d8e45-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="d8e45-172">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="d8e45-172">Conditional AND</span></span>
    - <span data-ttu-id="d8e45-173">`x && y`: Vyhodnotí `y` pouze v případě `x` není `false`</span><span class="sxs-lookup"><span data-stu-id="d8e45-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="d8e45-174">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="d8e45-174">Conditional OR</span></span>
    - <span data-ttu-id="d8e45-175">`x || y`: Vyhodnotí `y` pouze v případě `x` není `true`</span><span class="sxs-lookup"><span data-stu-id="d8e45-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="d8e45-176">Nulové sloučení</span><span class="sxs-lookup"><span data-stu-id="d8e45-176">Null coalescing</span></span>
    - <span data-ttu-id="d8e45-177">`x ?? y`: Vyhodnocen `y` Pokud `x` má hodnotu null, k `x` jinak</span><span class="sxs-lookup"><span data-stu-id="d8e45-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="d8e45-178">Podmiňovací operátor</span><span class="sxs-lookup"><span data-stu-id="d8e45-178">Conditional</span></span>
    - <span data-ttu-id="d8e45-179">`x ? y : z`: Vyhodnotí `y` Pokud `x` je `true`, `z` Pokud `x` je `false`</span><span class="sxs-lookup"><span data-stu-id="d8e45-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="d8e45-180">Přiřazení nebo anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="d8e45-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="d8e45-181">`x = y`: Přiřazení</span><span class="sxs-lookup"><span data-stu-id="d8e45-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="d8e45-182">`x op= y`: Složené přiřazení; jsou podporované operátory</span><span class="sxs-lookup"><span data-stu-id="d8e45-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="d8e45-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="d8e45-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="d8e45-184">`(T x) => y`: Anonymní funkce (výrazu lambda)</span><span class="sxs-lookup"><span data-stu-id="d8e45-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="d8e45-185">[Předchozí](types-and-variables.md)
[další](statements.md)</span><span class="sxs-lookup"><span data-stu-id="d8e45-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
