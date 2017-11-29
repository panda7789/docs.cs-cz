---
title: "C# výrazy - přehled používání jazyka C#"
description: "výrazy, operandy a operátory jsou stavební bloky jazyka C#"
keywords: "Rozhraní .NET, csharp, výrazu, operátoru, operand"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 7b7e321e6554818924a8a2b68afa4c787807bcba
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="expressions"></a><span data-ttu-id="0c119-104">Výrazy</span><span class="sxs-lookup"><span data-stu-id="0c119-104">Expressions</span></span>

<span data-ttu-id="0c119-105">*Výrazy* se vytvářejí na základě *operandy* a *operátory*.</span><span class="sxs-lookup"><span data-stu-id="0c119-105">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="0c119-106">Operátory výrazu znamenat operací, které chcete použít pro operandy.</span><span class="sxs-lookup"><span data-stu-id="0c119-106">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="0c119-107">Příklady operátory `+`, `-`, `*`, `/`, a `new`.</span><span class="sxs-lookup"><span data-stu-id="0c119-107">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="0c119-108">Příklady operandy: literály, pole, místní proměnné a výrazy.</span><span class="sxs-lookup"><span data-stu-id="0c119-108">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="0c119-109">Pokud některý výraz obsahuje více operátorů *přednost před* operátory ovládací prvky pořadí, ve kterém jsou jednotlivé operátory vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="0c119-109">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="0c119-110">Například výraz `x + y * z` je vyhodnoceno jako `x + (y * z)` protože `*` operátor má vyšší prioritu než `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="0c119-110">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="0c119-111">Když dojde k operand mezi dva operátory se stejnou prioritou, *asociativnost* operátory ovládací prvky pořadí, ve kterém jsou prováděny operace:</span><span class="sxs-lookup"><span data-stu-id="0c119-111">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="0c119-112">S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="0c119-112">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="0c119-113">Například `x + y + z` je vyhodnoceno jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="0c119-113">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="0c119-114">Operátory přiřazení a podmíněný operátor (`?:`) jsou *zprava asociativní*, což znamená, že operací zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="0c119-114">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="0c119-115">Například `x = y = z` je vyhodnoceno jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="0c119-115">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="0c119-116">Přednost a asociativnost se dá řídit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="0c119-116">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="0c119-117">Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidává výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a potom vynásobí výsledek podle `z`.</span><span class="sxs-lookup"><span data-stu-id="0c119-117">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="0c119-118">Většina operátory mohou být *přetížený*.</span><span class="sxs-lookup"><span data-stu-id="0c119-118">Most operators can be *overloaded*.</span></span> <span data-ttu-id="0c119-119">Přetížení operátoru umožňuje implementace uživatelem definovaný operátor zadat pro operace, kde jsou jedno nebo obě operandy typu uživatelem definované třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="0c119-119">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="0c119-120">Následující možnost shrne operátory jazyka C# na, výpis kategorií operátor v pořadí podle priority od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="0c119-120">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="0c119-121">Operátory ve stejné kategorii nemá přednost.</span><span class="sxs-lookup"><span data-stu-id="0c119-121">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="0c119-122">V rámci každé kategorie je seznam výrazů v dané kategorii společně s popisem příslušného typu výraz.</span><span class="sxs-lookup"><span data-stu-id="0c119-122">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="0c119-123">primární</span><span class="sxs-lookup"><span data-stu-id="0c119-123">Primary</span></span>
    - <span data-ttu-id="0c119-124">`x.m`: Přístup ke členu</span><span class="sxs-lookup"><span data-stu-id="0c119-124">`x.m`: Member access</span></span>
    - <span data-ttu-id="0c119-125">`x(...)`: Metoda a delegáta volání</span><span class="sxs-lookup"><span data-stu-id="0c119-125">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="0c119-126">`x[...]`: Pole a indexer přístup</span><span class="sxs-lookup"><span data-stu-id="0c119-126">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="0c119-127">`x++`: Přírůstek po</span><span class="sxs-lookup"><span data-stu-id="0c119-127">`x++`: Post-increment</span></span>
    - <span data-ttu-id="0c119-128">`x--`: Po snížení</span><span class="sxs-lookup"><span data-stu-id="0c119-128">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="0c119-129">`new T(...)`: Objekt a delegovat vytvoření</span><span class="sxs-lookup"><span data-stu-id="0c119-129">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="0c119-130">`new T(...){...}`: Vytvoření objektu pomocí inicializátoru</span><span class="sxs-lookup"><span data-stu-id="0c119-130">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="0c119-131">`new {...}`: Inicializátor anonymní objekt</span><span class="sxs-lookup"><span data-stu-id="0c119-131">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="0c119-132">`new T[...]`: Při vytváření pole</span><span class="sxs-lookup"><span data-stu-id="0c119-132">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="0c119-133">`typeof(T)`: Získat <xref:System.Type> objekt pro`T`</span><span class="sxs-lookup"><span data-stu-id="0c119-133">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="0c119-134">`checked(x)`: Výraz v kontextu zaškrtnuté vyhodnocení</span><span class="sxs-lookup"><span data-stu-id="0c119-134">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="0c119-135">`unchecked(x)`: Vyhodnocení výrazu v kontextu nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="0c119-135">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="0c119-136">`default(T)`: Výchozí hodnota typu získat`T`</span><span class="sxs-lookup"><span data-stu-id="0c119-136">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="0c119-137">`delegate {...}`: Anonymní funkce (anonymní metoda)</span><span class="sxs-lookup"><span data-stu-id="0c119-137">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="0c119-138">Unární</span><span class="sxs-lookup"><span data-stu-id="0c119-138">Unary</span></span>
    - <span data-ttu-id="0c119-139">`+x`: Identity</span><span class="sxs-lookup"><span data-stu-id="0c119-139">`+x`: Identity</span></span>
    - <span data-ttu-id="0c119-140">`-x`: Negace</span><span class="sxs-lookup"><span data-stu-id="0c119-140">`-x`: Negation</span></span>
    - <span data-ttu-id="0c119-141">`!x`: Logická negace</span><span class="sxs-lookup"><span data-stu-id="0c119-141">`!x`: Logical negation</span></span>
    - <span data-ttu-id="0c119-142">`~x`: Bitovou negaci</span><span class="sxs-lookup"><span data-stu-id="0c119-142">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="0c119-143">`++x`: Přírůstek před</span><span class="sxs-lookup"><span data-stu-id="0c119-143">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="0c119-144">`--x`: Snížení před</span><span class="sxs-lookup"><span data-stu-id="0c119-144">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="0c119-145">`(T)x`: Explicitně převést `x` na typ`T`</span><span class="sxs-lookup"><span data-stu-id="0c119-145">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="0c119-146">`await x`: Asynchronně počkejte `x` k dokončení</span><span class="sxs-lookup"><span data-stu-id="0c119-146">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="0c119-147">Multiplikativní</span><span class="sxs-lookup"><span data-stu-id="0c119-147">Multiplicative</span></span>
    - <span data-ttu-id="0c119-148">`x * y`: Násobení</span><span class="sxs-lookup"><span data-stu-id="0c119-148">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="0c119-149">`x / y`: Dělení</span><span class="sxs-lookup"><span data-stu-id="0c119-149">`x / y`: Division</span></span>
    - <span data-ttu-id="0c119-150">`x % y`: Zbývající</span><span class="sxs-lookup"><span data-stu-id="0c119-150">`x % y`: Remainder</span></span>
* <span data-ttu-id="0c119-151">Doplňkové</span><span class="sxs-lookup"><span data-stu-id="0c119-151">Additive</span></span>
    - <span data-ttu-id="0c119-152">`x + y`: Zřetězení řetězců přidání, kombinace delegáta</span><span class="sxs-lookup"><span data-stu-id="0c119-152">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="0c119-153">`x – y`: Odčítání, odebrání delegáta</span><span class="sxs-lookup"><span data-stu-id="0c119-153">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="0c119-154">Posunutí</span><span class="sxs-lookup"><span data-stu-id="0c119-154">Shift</span></span>
    - <span data-ttu-id="0c119-155">`x << y`: Posunutí doleva</span><span class="sxs-lookup"><span data-stu-id="0c119-155">`x << y`: Shift left</span></span>
    - <span data-ttu-id="0c119-156">`x >> y`: Posunutí doprava</span><span class="sxs-lookup"><span data-stu-id="0c119-156">`x >> y`: Shift right</span></span>
* <span data-ttu-id="0c119-157">Relační a typ testování</span><span class="sxs-lookup"><span data-stu-id="0c119-157">Relational and type testing</span></span>
    - <span data-ttu-id="0c119-158">`x < y`: Menší než</span><span class="sxs-lookup"><span data-stu-id="0c119-158">`x < y`: Less than</span></span>
    - <span data-ttu-id="0c119-159">`x > y`: Větší než</span><span class="sxs-lookup"><span data-stu-id="0c119-159">`x > y`: Greater than</span></span>
    - <span data-ttu-id="0c119-160">`x <= y`: Menší než nebo rovno</span><span class="sxs-lookup"><span data-stu-id="0c119-160">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="0c119-161">`x >= y`: Větší než nebo rovno</span><span class="sxs-lookup"><span data-stu-id="0c119-161">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="0c119-162">`x is T`: Návratový `true` Pokud `x` je `T`, `false` jinak</span><span class="sxs-lookup"><span data-stu-id="0c119-162">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="0c119-163">`x as T`: Návratový `x` zadán jako `T`, nebo `null` Pokud `x` není`T`</span><span class="sxs-lookup"><span data-stu-id="0c119-163">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="0c119-164">Rovnost</span><span class="sxs-lookup"><span data-stu-id="0c119-164">Equality</span></span>
    - <span data-ttu-id="0c119-165">`x == y`: Rovná</span><span class="sxs-lookup"><span data-stu-id="0c119-165">`x == y`: Equal</span></span>
    - <span data-ttu-id="0c119-166">`x != y`: Není rovno</span><span class="sxs-lookup"><span data-stu-id="0c119-166">`x != y`: Not equal</span></span>
* <span data-ttu-id="0c119-167">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="0c119-167">Logical AND</span></span>
    - <span data-ttu-id="0c119-168">`x & y`: Celé číslo bitové a boolean logické a</span><span class="sxs-lookup"><span data-stu-id="0c119-168">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="0c119-169">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="0c119-169">Logical XOR</span></span>
    - <span data-ttu-id="0c119-170">`x ^ y`: Bitové operace XOR celé číslo, logickou logické XOR</span><span class="sxs-lookup"><span data-stu-id="0c119-170">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="0c119-171">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="0c119-171">Logical OR</span></span>
    - <span data-ttu-id="0c119-172">`x | y`: Celé číslo bitové nebo logická hodnota logické nebo</span><span class="sxs-lookup"><span data-stu-id="0c119-172">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="0c119-173">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="0c119-173">Conditional AND</span></span>
    - <span data-ttu-id="0c119-174">`x && y`: Vyhodnotí `y` pouze v případě `x` není`false`</span><span class="sxs-lookup"><span data-stu-id="0c119-174">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="0c119-175">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="0c119-175">Conditional OR</span></span>
    - <span data-ttu-id="0c119-176">`x || y`: Vyhodnotí `y` pouze v případě `x` není`true`</span><span class="sxs-lookup"><span data-stu-id="0c119-176">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="0c119-177">Nulové sloučení</span><span class="sxs-lookup"><span data-stu-id="0c119-177">Null coalescing</span></span>
    - <span data-ttu-id="0c119-178">`x ?? y`: Vyhodnocen `y` Pokud `x` má hodnotu null, k `x` jinak</span><span class="sxs-lookup"><span data-stu-id="0c119-178">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="0c119-179">Podmiňovací operátor</span><span class="sxs-lookup"><span data-stu-id="0c119-179">Conditional</span></span>
    - <span data-ttu-id="0c119-180">`x ? y : z`: Vyhodnotí `y` Pokud `x` je `true`, `z` Pokud `x` je`false`</span><span class="sxs-lookup"><span data-stu-id="0c119-180">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="0c119-181">Přiřazení nebo anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="0c119-181">Assignment or anonymous function</span></span>
    - <span data-ttu-id="0c119-182">`x = y`: Přiřazení</span><span class="sxs-lookup"><span data-stu-id="0c119-182">`x = y`: Assignment</span></span>
    - <span data-ttu-id="0c119-183">`x op= y`: Složené přiřazení; jsou podporované operátory</span><span class="sxs-lookup"><span data-stu-id="0c119-183">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="0c119-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="0c119-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="0c119-185">`(T x) => y`: Anonymní funkce (výrazu lambda)</span><span class="sxs-lookup"><span data-stu-id="0c119-185">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="0c119-186">[Předchozí](types-and-variables.md)
[další](statements.md)</span><span class="sxs-lookup"><span data-stu-id="0c119-186">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
