---
title: C#Výrazy – připravuje C# jazyka
description: výrazy, operandy a operátory jsou stavební bloky C# jazyka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 28e1d6952975c6932dc9ae40af28c7201d61d778
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154931"
---
# <a name="expressions"></a><span data-ttu-id="83e28-103">Výrazy</span><span class="sxs-lookup"><span data-stu-id="83e28-103">Expressions</span></span>

<span data-ttu-id="83e28-104">*Výrazy* se vytvářejí na základě *operandy* a *operátory*.</span><span class="sxs-lookup"><span data-stu-id="83e28-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="83e28-105">Operátory výrazu označují operace, které chcete použít pro operandy.</span><span class="sxs-lookup"><span data-stu-id="83e28-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="83e28-106">Příklady operátorů `+`, `-`, `*`, `/`, a `new`.</span><span class="sxs-lookup"><span data-stu-id="83e28-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="83e28-107">Příklady operandy: literály, pole, místní proměnné a výrazy.</span><span class="sxs-lookup"><span data-stu-id="83e28-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="83e28-108">Pokud výraz obsahuje více operátorů *prioritu* operátorů určuje pořadí, ve kterém jsou jednotlivé operátory vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="83e28-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="83e28-109">Například výraz `x + y * z` se vyhodnotí jako `x + (y * z)` protože `*` má vyšší prioritu než operátor `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="83e28-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="83e28-110">Dojde-li operand mezi dva operátory se stejnou prioritou, *asociativita* operátorů určuje pořadí, ve kterém jsou operace prováděny:</span><span class="sxs-lookup"><span data-stu-id="83e28-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="83e28-111">S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádějí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="83e28-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="83e28-112">Například `x + y + z` se vyhodnotí jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="83e28-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="83e28-113">Operátory přiřazení a podmiňovací operátor (`?:`) jsou *asociativní zprava*, což znamená, že operace se provádějí zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="83e28-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="83e28-114">Například `x = y = z` se vyhodnotí jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="83e28-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="83e28-115">Přednost a asociativita operátorů lze ovládat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="83e28-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="83e28-116">Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidá výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a pak vynásobí výsledků `z`.</span><span class="sxs-lookup"><span data-stu-id="83e28-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="83e28-117">Většina operátory mohou být *přetížené*.</span><span class="sxs-lookup"><span data-stu-id="83e28-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="83e28-118">Přetížení operátoru umožňuje uživatelem definovaný operátor implementace pro operace, kde jeden nebo oba operandy jsou třídy nebo struktury typu uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="83e28-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="83e28-119">Shrnuje následující C#pro operátory, výpis operátor kategorií v pořadí podle priority od nejvyšší k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="83e28-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="83e28-120">Operátory ve stejné kategorii mají stejnou prioritu.</span><span class="sxs-lookup"><span data-stu-id="83e28-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="83e28-121">V rámci každé kategorie je seznamem výrazů v dané kategorii spolu s popis tohoto typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="83e28-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="83e28-122">Primární</span><span class="sxs-lookup"><span data-stu-id="83e28-122">Primary</span></span>
    - <span data-ttu-id="83e28-123">`x.m`: Přístup ke členům</span><span class="sxs-lookup"><span data-stu-id="83e28-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="83e28-124">`x(...)`: Vyvolání metod a delegátů</span><span class="sxs-lookup"><span data-stu-id="83e28-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="83e28-125">`x[...]`: Přístup k poli a indexeru</span><span class="sxs-lookup"><span data-stu-id="83e28-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="83e28-126">`x++`: Postinkrementace</span><span class="sxs-lookup"><span data-stu-id="83e28-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="83e28-127">`x--`: Postdekrementace</span><span class="sxs-lookup"><span data-stu-id="83e28-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="83e28-128">`new T(...)`: Vytvoření objektu a delegátu</span><span class="sxs-lookup"><span data-stu-id="83e28-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="83e28-129">`new T(...){...}`: Vytvoření objektu s inicializátorem</span><span class="sxs-lookup"><span data-stu-id="83e28-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="83e28-130">`new {...}`:  Inicializátor anonymních objektů</span><span class="sxs-lookup"><span data-stu-id="83e28-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="83e28-131">`new T[...]`: Vytvoření pole</span><span class="sxs-lookup"><span data-stu-id="83e28-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="83e28-132">`typeof(T)`: Získat <xref:System.Type> objekt pro `T`</span><span class="sxs-lookup"><span data-stu-id="83e28-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="83e28-133">`checked(x)`: Vyhodnocení výrazu ve zkontrolovaném kontextu</span><span class="sxs-lookup"><span data-stu-id="83e28-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="83e28-134">`unchecked(x)`: Vyhodnocení výrazu v nezkontrolovaném kontextu</span><span class="sxs-lookup"><span data-stu-id="83e28-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="83e28-135">`default(T)`: Získat výchozí hodnotu typu `T`</span><span class="sxs-lookup"><span data-stu-id="83e28-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="83e28-136">`delegate {...}`: Anonymní funkce (anonymní metoda)</span><span class="sxs-lookup"><span data-stu-id="83e28-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="83e28-137">Unární</span><span class="sxs-lookup"><span data-stu-id="83e28-137">Unary</span></span>
    - <span data-ttu-id="83e28-138">`+x`: Identita</span><span class="sxs-lookup"><span data-stu-id="83e28-138">`+x`: Identity</span></span>
    - <span data-ttu-id="83e28-139">`-x`: Negace</span><span class="sxs-lookup"><span data-stu-id="83e28-139">`-x`: Negation</span></span>
    - <span data-ttu-id="83e28-140">`!x`: Logická negace</span><span class="sxs-lookup"><span data-stu-id="83e28-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="83e28-141">`~x`: Bitová negace.</span><span class="sxs-lookup"><span data-stu-id="83e28-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="83e28-142">`++x`: Preinkrementace</span><span class="sxs-lookup"><span data-stu-id="83e28-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="83e28-143">`--x`: Predekrementace</span><span class="sxs-lookup"><span data-stu-id="83e28-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="83e28-144">`(T)x`: Explicitně převést `x` na typ `T`</span><span class="sxs-lookup"><span data-stu-id="83e28-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="83e28-145">`await x`: Asynchronně počkejte `x` k dokončení</span><span class="sxs-lookup"><span data-stu-id="83e28-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="83e28-146">Násobení</span><span class="sxs-lookup"><span data-stu-id="83e28-146">Multiplicative</span></span>
    - <span data-ttu-id="83e28-147">`x * y`: Násobení</span><span class="sxs-lookup"><span data-stu-id="83e28-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="83e28-148">`x / y`: Dělení</span><span class="sxs-lookup"><span data-stu-id="83e28-148">`x / y`: Division</span></span>
    - <span data-ttu-id="83e28-149">`x % y`: Zbytek</span><span class="sxs-lookup"><span data-stu-id="83e28-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="83e28-150">Additive</span><span class="sxs-lookup"><span data-stu-id="83e28-150">Additive</span></span>
    - <span data-ttu-id="83e28-151">`x + y`: Sčítání, řetězení řetězců, kombinování delegátů</span><span class="sxs-lookup"><span data-stu-id="83e28-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="83e28-152">`x – y`: Odčítání, odebrání delegátů</span><span class="sxs-lookup"><span data-stu-id="83e28-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="83e28-153">SHIFT</span><span class="sxs-lookup"><span data-stu-id="83e28-153">Shift</span></span>
    - <span data-ttu-id="83e28-154">`x << y`: Posun doleva</span><span class="sxs-lookup"><span data-stu-id="83e28-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="83e28-155">`x >> y`: Posun doprava</span><span class="sxs-lookup"><span data-stu-id="83e28-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="83e28-156">Relační a typové zkoušky</span><span class="sxs-lookup"><span data-stu-id="83e28-156">Relational and type testing</span></span>
    - <span data-ttu-id="83e28-157">`x < y`: Menší než</span><span class="sxs-lookup"><span data-stu-id="83e28-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="83e28-158">`x > y`: Větší než</span><span class="sxs-lookup"><span data-stu-id="83e28-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="83e28-159">`x <= y`: Menší nebo rovno</span><span class="sxs-lookup"><span data-stu-id="83e28-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="83e28-160">`x >= y`: Větší nebo rovno</span><span class="sxs-lookup"><span data-stu-id="83e28-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="83e28-161">`x is T`: Vrátí `true` Pokud `x` je `T`, `false` jinak</span><span class="sxs-lookup"><span data-stu-id="83e28-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="83e28-162">`x as T`: Vrátí `x` zadán jako `T`, nebo `null` Pokud `x` není `T`</span><span class="sxs-lookup"><span data-stu-id="83e28-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="83e28-163">Rovnost</span><span class="sxs-lookup"><span data-stu-id="83e28-163">Equality</span></span>
    - <span data-ttu-id="83e28-164">`x == y`: Rovno</span><span class="sxs-lookup"><span data-stu-id="83e28-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="83e28-165">`x != y`: Nerovná se</span><span class="sxs-lookup"><span data-stu-id="83e28-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="83e28-166">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="83e28-166">Logical AND</span></span>
    - <span data-ttu-id="83e28-167">`x & y`: Celočíselné bitové a logických logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="83e28-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="83e28-168">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="83e28-168">Logical XOR</span></span>
    - <span data-ttu-id="83e28-169">`x ^ y`: Bitový operátor XOR celého čísla, logická hodnota operátoru XOR</span><span class="sxs-lookup"><span data-stu-id="83e28-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="83e28-170">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="83e28-170">Logical OR</span></span>
    - <span data-ttu-id="83e28-171">`x | y`: Bitový operátor OR celého čísla, logická hodnota operátoru OR</span><span class="sxs-lookup"><span data-stu-id="83e28-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="83e28-172">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="83e28-172">Conditional AND</span></span>
    - <span data-ttu-id="83e28-173">`x && y`: Vyhodnotí `y` pouze tehdy, pokud `x` není `false`</span><span class="sxs-lookup"><span data-stu-id="83e28-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="83e28-174">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="83e28-174">Conditional OR</span></span>
    - <span data-ttu-id="83e28-175">`x || y`: Vyhodnotí `y` pouze tehdy, pokud `x` není `true`</span><span class="sxs-lookup"><span data-stu-id="83e28-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="83e28-176">Nulové sloučení</span><span class="sxs-lookup"><span data-stu-id="83e28-176">Null coalescing</span></span>
    - <span data-ttu-id="83e28-177">`x ?? y`: Vyhodnotí jako `y` Pokud `x` má hodnotu null, `x` jinak</span><span class="sxs-lookup"><span data-stu-id="83e28-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="83e28-178">Podmiňovací operátor</span><span class="sxs-lookup"><span data-stu-id="83e28-178">Conditional</span></span>
    - <span data-ttu-id="83e28-179">`x ? y : z`: Vyhodnotí `y` Pokud `x` je `true`, `z` Pokud `x` je `false`</span><span class="sxs-lookup"><span data-stu-id="83e28-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="83e28-180">Přiřazení nebo anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="83e28-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="83e28-181">`x = y`: Přiřazení</span><span class="sxs-lookup"><span data-stu-id="83e28-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="83e28-182">`x op= y`: Složené přiřazení. podporované operátory jsou</span><span class="sxs-lookup"><span data-stu-id="83e28-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="83e28-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="83e28-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="83e28-184">`(T x) => y`: Anonymní funkce (výraz lambda)</span><span class="sxs-lookup"><span data-stu-id="83e28-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="83e28-185">[Předchozí](types-and-variables.md)
>[další](statements.md)</span><span class="sxs-lookup"><span data-stu-id="83e28-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>