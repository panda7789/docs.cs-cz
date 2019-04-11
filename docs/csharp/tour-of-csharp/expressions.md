---
title: C#Výrazy – připravuje C# jazyka
description: výrazy, operandy a operátory jsou stavební bloky C# jazyka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4ffe947a4cb8c36a5925a4b3846486e44a9d8ec4
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480752"
---
# <a name="expressions"></a><span data-ttu-id="322d1-103">Výrazy</span><span class="sxs-lookup"><span data-stu-id="322d1-103">Expressions</span></span>

<span data-ttu-id="322d1-104">*Výrazy* se vytvářejí na základě *operandy* a *operátory*.</span><span class="sxs-lookup"><span data-stu-id="322d1-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="322d1-105">Operátory výrazu označují operace, které chcete použít pro operandy.</span><span class="sxs-lookup"><span data-stu-id="322d1-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="322d1-106">Příklady operátorů `+`, `-`, `*`, `/`, a `new`.</span><span class="sxs-lookup"><span data-stu-id="322d1-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="322d1-107">Příklady operandy: literály, pole, místní proměnné a výrazy.</span><span class="sxs-lookup"><span data-stu-id="322d1-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="322d1-108">Pokud výraz obsahuje více operátorů *prioritu* operátorů určuje pořadí, ve kterém jsou jednotlivé operátory vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="322d1-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="322d1-109">Například výraz `x + y * z` se vyhodnotí jako `x + (y * z)` protože `*` má vyšší prioritu než operátor `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="322d1-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="322d1-110">Dojde-li operand mezi dva operátory se stejnou prioritou, *asociativita* operátorů určuje pořadí, ve kterém jsou operace prováděny:</span><span class="sxs-lookup"><span data-stu-id="322d1-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="322d1-111">S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádějí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="322d1-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="322d1-112">Například `x + y + z` se vyhodnotí jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="322d1-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="322d1-113">Operátory přiřazení a podmiňovací operátor (`?:`) jsou *asociativní zprava*, což znamená, že operace se provádějí zprava doleva.</span><span class="sxs-lookup"><span data-stu-id="322d1-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="322d1-114">Například `x = y = z` se vyhodnotí jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="322d1-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="322d1-115">Přednost a asociativita operátorů lze ovládat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="322d1-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="322d1-116">Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidá výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a pak vynásobí výsledků `z`.</span><span class="sxs-lookup"><span data-stu-id="322d1-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="322d1-117">Většina operátory mohou být *přetížené*.</span><span class="sxs-lookup"><span data-stu-id="322d1-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="322d1-118">Přetížení operátoru umožňuje uživatelem definovaný operátor implementace pro operace, kde jeden nebo oba operandy jsou třídy nebo struktury typu uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="322d1-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="322d1-119">Shrnuje následující C#pro operátory, výpis operátor kategorií v pořadí podle priority od nejvyšší k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="322d1-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="322d1-120">Operátory ve stejné kategorii mají stejnou prioritu.</span><span class="sxs-lookup"><span data-stu-id="322d1-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="322d1-121">V rámci každé kategorie je seznamem výrazů v dané kategorii spolu s popis tohoto typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="322d1-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="322d1-122">Primární</span><span class="sxs-lookup"><span data-stu-id="322d1-122">Primary</span></span>
  - `x.m`<span data-ttu-id="322d1-123">: Přístup ke členům</span><span class="sxs-lookup"><span data-stu-id="322d1-123">: Member access</span></span>
  - `x(...)`<span data-ttu-id="322d1-124">: Vyvolání metod a delegátů</span><span class="sxs-lookup"><span data-stu-id="322d1-124">: Method and delegate invocation</span></span>
  - `x[...]`<span data-ttu-id="322d1-125">: Přístup k poli a indexeru</span><span class="sxs-lookup"><span data-stu-id="322d1-125">: Array and indexer access</span></span>
  - `x++`<span data-ttu-id="322d1-126">: Postinkrementace</span><span class="sxs-lookup"><span data-stu-id="322d1-126">: Post-increment</span></span>
  - `x--`<span data-ttu-id="322d1-127">: Postdekrementace</span><span class="sxs-lookup"><span data-stu-id="322d1-127">: Post-decrement</span></span>
  - `new T(...)`<span data-ttu-id="322d1-128">: Vytvoření objektu a delegátu</span><span class="sxs-lookup"><span data-stu-id="322d1-128">: Object and delegate creation</span></span>
  - `new T(...){...}`<span data-ttu-id="322d1-129">: Vytvoření objektu s inicializátorem</span><span class="sxs-lookup"><span data-stu-id="322d1-129">: Object creation with initializer</span></span>
  - `new {...}`<span data-ttu-id="322d1-130">:  Inicializátor anonymních objektů</span><span class="sxs-lookup"><span data-stu-id="322d1-130">:  Anonymous object initializer</span></span>
  - `new T[...]`<span data-ttu-id="322d1-131">: Vytvoření pole</span><span class="sxs-lookup"><span data-stu-id="322d1-131">: Array creation</span></span>
  - `typeof(T)`<span data-ttu-id="322d1-132">: Získat <xref:System.Type> objekt pro</span><span class="sxs-lookup"><span data-stu-id="322d1-132">: Obtain <xref:System.Type> object for</span></span> `T`
  - `checked(x)`<span data-ttu-id="322d1-133">: Vyhodnocení výrazu ve zkontrolovaném kontextu</span><span class="sxs-lookup"><span data-stu-id="322d1-133">: Evaluate expression in checked context</span></span>
  - `unchecked(x)`<span data-ttu-id="322d1-134">: Vyhodnocení výrazu v nezkontrolovaném kontextu</span><span class="sxs-lookup"><span data-stu-id="322d1-134">: Evaluate expression in unchecked context</span></span>
  - `default(T)`<span data-ttu-id="322d1-135">: Získat výchozí hodnotu typu</span><span class="sxs-lookup"><span data-stu-id="322d1-135">: Obtain default value of type</span></span> `T`
  - `delegate {...}`<span data-ttu-id="322d1-136">: Anonymní funkce (anonymní metoda)</span><span class="sxs-lookup"><span data-stu-id="322d1-136">: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="322d1-137">Unární</span><span class="sxs-lookup"><span data-stu-id="322d1-137">Unary</span></span>
  - `+x`<span data-ttu-id="322d1-138">: Identita</span><span class="sxs-lookup"><span data-stu-id="322d1-138">: Identity</span></span>
  - `-x`<span data-ttu-id="322d1-139">: Negace</span><span class="sxs-lookup"><span data-stu-id="322d1-139">: Negation</span></span>
  - `!x`<span data-ttu-id="322d1-140">: Logická negace</span><span class="sxs-lookup"><span data-stu-id="322d1-140">: Logical negation</span></span>
  - `~x`<span data-ttu-id="322d1-141">: Bitová negace.</span><span class="sxs-lookup"><span data-stu-id="322d1-141">: Bitwise negation</span></span>
  - `++x`<span data-ttu-id="322d1-142">: Preinkrementace</span><span class="sxs-lookup"><span data-stu-id="322d1-142">: Pre-increment</span></span>
  - `--x`<span data-ttu-id="322d1-143">: Predekrementace</span><span class="sxs-lookup"><span data-stu-id="322d1-143">: Pre-decrement</span></span>
  - `(T)x`<span data-ttu-id="322d1-144">: Explicitně převést `x` na typ</span><span class="sxs-lookup"><span data-stu-id="322d1-144">: Explicitly convert `x` to type</span></span> `T`
  - `await x`<span data-ttu-id="322d1-145">: Asynchronně počkejte `x` k dokončení</span><span class="sxs-lookup"><span data-stu-id="322d1-145">: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="322d1-146">Násobení</span><span class="sxs-lookup"><span data-stu-id="322d1-146">Multiplicative</span></span>
  - `x * y`<span data-ttu-id="322d1-147">: Násobení</span><span class="sxs-lookup"><span data-stu-id="322d1-147">: Multiplication</span></span>
  - `x / y`<span data-ttu-id="322d1-148">: Dělení</span><span class="sxs-lookup"><span data-stu-id="322d1-148">: Division</span></span>
  - `x % y`<span data-ttu-id="322d1-149">: Zbytek</span><span class="sxs-lookup"><span data-stu-id="322d1-149">: Remainder</span></span>
* <span data-ttu-id="322d1-150">Additive</span><span class="sxs-lookup"><span data-stu-id="322d1-150">Additive</span></span>
  - `x + y`<span data-ttu-id="322d1-151">: Sčítání, řetězení řetězců, kombinování delegátů</span><span class="sxs-lookup"><span data-stu-id="322d1-151">: Addition, string concatenation, delegate combination</span></span>
  - `x – y`<span data-ttu-id="322d1-152">: Odčítání, odebrání delegátů</span><span class="sxs-lookup"><span data-stu-id="322d1-152">: Subtraction, delegate removal</span></span>
* <span data-ttu-id="322d1-153">SHIFT</span><span class="sxs-lookup"><span data-stu-id="322d1-153">Shift</span></span>
  - `x << y`<span data-ttu-id="322d1-154">: Posun doleva</span><span class="sxs-lookup"><span data-stu-id="322d1-154">: Shift left</span></span>
  - `x >> y`<span data-ttu-id="322d1-155">: Posun doprava</span><span class="sxs-lookup"><span data-stu-id="322d1-155">: Shift right</span></span>
* <span data-ttu-id="322d1-156">Relační a typové zkoušky</span><span class="sxs-lookup"><span data-stu-id="322d1-156">Relational and type testing</span></span>
  - `x < y`<span data-ttu-id="322d1-157">: Menší než</span><span class="sxs-lookup"><span data-stu-id="322d1-157">: Less than</span></span>
  - `x > y`<span data-ttu-id="322d1-158">: Větší než</span><span class="sxs-lookup"><span data-stu-id="322d1-158">: Greater than</span></span>
  - `x <= y`<span data-ttu-id="322d1-159">: Menší nebo rovno</span><span class="sxs-lookup"><span data-stu-id="322d1-159">: Less than or equal</span></span>
  - `x >= y`<span data-ttu-id="322d1-160">: Větší nebo rovno</span><span class="sxs-lookup"><span data-stu-id="322d1-160">: Greater than or equal</span></span>
  - `x is T`<span data-ttu-id="322d1-161">: Vrátí `true` Pokud `x` je `T`, `false` jinak</span><span class="sxs-lookup"><span data-stu-id="322d1-161">: Return `true` if `x` is a `T`, `false` otherwise</span></span>
  - `x as T`<span data-ttu-id="322d1-162">: Vrátí `x` zadán jako `T`, nebo `null` Pokud `x` není</span><span class="sxs-lookup"><span data-stu-id="322d1-162">: Return `x` typed as `T`, or `null` if `x` is not a</span></span> `T`
* <span data-ttu-id="322d1-163">Rovnost</span><span class="sxs-lookup"><span data-stu-id="322d1-163">Equality</span></span>
  - `x == y`<span data-ttu-id="322d1-164">: Rovno</span><span class="sxs-lookup"><span data-stu-id="322d1-164">: Equal</span></span>
  - `x != y`<span data-ttu-id="322d1-165">: Nerovná se</span><span class="sxs-lookup"><span data-stu-id="322d1-165">: Not equal</span></span>
* <span data-ttu-id="322d1-166">Logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="322d1-166">Logical AND</span></span>
  - `x & y`<span data-ttu-id="322d1-167">: Celočíselné bitové a logických logický operátor AND</span><span class="sxs-lookup"><span data-stu-id="322d1-167">: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="322d1-168">Logický operátor XOR</span><span class="sxs-lookup"><span data-stu-id="322d1-168">Logical XOR</span></span>
  - `x ^ y`<span data-ttu-id="322d1-169">: Bitový operátor XOR celého čísla, logická hodnota operátoru XOR</span><span class="sxs-lookup"><span data-stu-id="322d1-169">: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="322d1-170">Logický operátor OR</span><span class="sxs-lookup"><span data-stu-id="322d1-170">Logical OR</span></span>
  - `x | y`<span data-ttu-id="322d1-171">: Bitový operátor OR celého čísla, logická hodnota operátoru OR</span><span class="sxs-lookup"><span data-stu-id="322d1-171">: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="322d1-172">Podmiňovací operátor AND</span><span class="sxs-lookup"><span data-stu-id="322d1-172">Conditional AND</span></span>
  - `x && y`<span data-ttu-id="322d1-173">: Vyhodnotí `y` pouze tehdy, pokud `x` není</span><span class="sxs-lookup"><span data-stu-id="322d1-173">: Evaluates `y` only if `x` is not</span></span> `false`
* <span data-ttu-id="322d1-174">Podmiňovací operátor OR</span><span class="sxs-lookup"><span data-stu-id="322d1-174">Conditional OR</span></span>
  - `x || y`<span data-ttu-id="322d1-175">: Vyhodnotí `y` pouze tehdy, pokud `x` není</span><span class="sxs-lookup"><span data-stu-id="322d1-175">: Evaluates `y` only if `x` is not</span></span> `true`
* <span data-ttu-id="322d1-176">Nulové sloučení</span><span class="sxs-lookup"><span data-stu-id="322d1-176">Null coalescing</span></span>
  - `x ?? y`<span data-ttu-id="322d1-177">: Vyhodnotí jako `y` Pokud `x` má hodnotu null, `x` jinak</span><span class="sxs-lookup"><span data-stu-id="322d1-177">: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="322d1-178">Podmiňovací operátor</span><span class="sxs-lookup"><span data-stu-id="322d1-178">Conditional</span></span>
  - `x ? y : z`<span data-ttu-id="322d1-179">: Vyhodnotí `y` Pokud `x` je `true`, `z` Pokud `x` je</span><span class="sxs-lookup"><span data-stu-id="322d1-179">: Evaluates `y` if `x` is `true`, `z` if `x` is</span></span> `false`
* <span data-ttu-id="322d1-180">Přiřazení nebo anonymní funkce</span><span class="sxs-lookup"><span data-stu-id="322d1-180">Assignment or anonymous function</span></span>
  - `x = y`<span data-ttu-id="322d1-181">: Přiřazení</span><span class="sxs-lookup"><span data-stu-id="322d1-181">: Assignment</span></span>
  - `x op= y`<span data-ttu-id="322d1-182">: Složené přiřazení. podporované operátory jsou</span><span class="sxs-lookup"><span data-stu-id="322d1-182">: Compound assignment; supported operators are</span></span>
    - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
  - `(T x) => y`<span data-ttu-id="322d1-183">: Anonymní funkce (výraz lambda)</span><span class="sxs-lookup"><span data-stu-id="322d1-183">: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="322d1-184">[Předchozí](types-and-variables.md)
> [další](statements.md)</span><span class="sxs-lookup"><span data-stu-id="322d1-184">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
