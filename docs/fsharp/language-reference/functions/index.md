---
title: Funkce (F#)
description: "Informace o funkcích v F # a jak F # podporuje společné funkční programovací konstrukce."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6dea2c3e-2f9d-4c9d-97a2-d8f9a72b6f4c
ms.openlocfilehash: adb2b0b3680c97582dfefda41c43735f9f09e6c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="functions"></a><span data-ttu-id="15a7d-104">Funkce</span><span class="sxs-lookup"><span data-stu-id="15a7d-104">Functions</span></span>

<span data-ttu-id="15a7d-105">Funkce jsou základní jednotkou spouštění programu v žádný programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="15a7d-105">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="15a7d-106">Funkce F # jako v jiných jazycích, má název, může mít parametry a argumenty proveďte a má text.</span><span class="sxs-lookup"><span data-stu-id="15a7d-106">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="15a7d-107">F # podporuje také funkční programovací konstrukce, jako je například replikace funkce jako hodnoty, pomocí nepojmenované funkcí na výrazy, složení funkcí k vytvoření nové funkce, curryfikované funkce a implicitní definici funkce prostřednictvím s částečným aplikace argumenty funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-107">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="15a7d-108">Definování funkcí s použitím `let` – klíčové slovo, nebo, pokud je funkce rekurzivní, `let rec` – kombinace klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="15a7d-108">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>


## <a name="syntax"></a><span data-ttu-id="15a7d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15a7d-109">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="15a7d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15a7d-110">Remarks</span></span>
<span data-ttu-id="15a7d-111">*Název funkce* je identifikátor, který představuje funkci.</span><span class="sxs-lookup"><span data-stu-id="15a7d-111">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="15a7d-112">*Seznam parametrů* se skládá z následných parametry, které jsou oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="15a7d-112">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="15a7d-113">Explicitní typ pro všechny parametry, můžete zadat, jak je popsáno v části parametry.</span><span class="sxs-lookup"><span data-stu-id="15a7d-113">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="15a7d-114">Pokud nezadáte argument konkrétní typ, pokusí se kompilátor odvození typu z tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-114">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="15a7d-115">*Tělo funkce* se skládá z výrazu.</span><span class="sxs-lookup"><span data-stu-id="15a7d-115">The *function-body* consists of an expression.</span></span> <span data-ttu-id="15a7d-116">Výraz, který tvoří tělo funkce se obvykle ze složeného výrazu skládající se z počet výrazů, které případech v posledním výrazu, který je návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15a7d-116">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="15a7d-117">*Návratový typ* typu následovaný dvojtečkou a je volitelné.</span><span class="sxs-lookup"><span data-stu-id="15a7d-117">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="15a7d-118">Pokud nezadáte žádný typ vrácené hodnoty explicitně, kompilátor určuje návratový typ z výsledný výraz.</span><span class="sxs-lookup"><span data-stu-id="15a7d-118">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="15a7d-119">Definice jednoduché funkce vypadá přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="15a7d-119">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="15a7d-120">V předchozím příkladu název funkce je `f`, argument je `x`, která má typ `int`, je tělo funkce `x + 1`, a vrácená hodnota je typu `int`.</span><span class="sxs-lookup"><span data-stu-id="15a7d-120">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="15a7d-121">Funkce mohou být označeny `inline`.</span><span class="sxs-lookup"><span data-stu-id="15a7d-121">Functions can be marked `inline`.</span></span> <span data-ttu-id="15a7d-122">Informace o `inline`, najdete v části [vložené funkce](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="15a7d-122">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>


## <a name="scope"></a><span data-ttu-id="15a7d-123">Rozsah</span><span class="sxs-lookup"><span data-stu-id="15a7d-123">Scope</span></span>
<span data-ttu-id="15a7d-124">Všechny úrovni oboru, než je rozsah modulu není chybu opakovaně použít název hodnotu nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-124">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="15a7d-125">Pokud jste znovu použít název, stín později deklarovaný název název předtím deklarován.</span><span class="sxs-lookup"><span data-stu-id="15a7d-125">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="15a7d-126">V oboru nejvyšší úrovně v modulu, musí být jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="15a7d-126">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="15a7d-127">Například následující kód vytvoří chybu, když se objeví v modulu oboru, ale ne v případě, že se zobrazí uvnitř funkce:</span><span class="sxs-lookup"><span data-stu-id="15a7d-127">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="15a7d-128">Ale následující kód je přijatelné žádné úrovni oboru:</span><span class="sxs-lookup"><span data-stu-id="15a7d-128">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]
    
#### <a name="parameters"></a><span data-ttu-id="15a7d-129">Parametry</span><span class="sxs-lookup"><span data-stu-id="15a7d-129">Parameters</span></span>
<span data-ttu-id="15a7d-130">Názvy parametrů jsou uvedeny po název funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-130">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="15a7d-131">Typ parametru, můžete určit, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15a7d-131">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="15a7d-132">Pokud zadáte typu, odpovídá názvu parametru a je oddělené od názvu dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="15a7d-132">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="15a7d-133">Pokud typ pro parametr vynecháte, je kompilátorem odvodit typ parametru.</span><span class="sxs-lookup"><span data-stu-id="15a7d-133">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="15a7d-134">Například v následující definice funkce argument `x` je odvodit být typu `int` protože 1 je typu `int`.</span><span class="sxs-lookup"><span data-stu-id="15a7d-134">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="15a7d-135">Kompilátor se však pokusí tomu, aby fungoval jako obecný nejblíže.</span><span class="sxs-lookup"><span data-stu-id="15a7d-135">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="15a7d-136">Například vezměte na vědomí následující kód:</span><span class="sxs-lookup"><span data-stu-id="15a7d-136">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="15a7d-137">Funkce vytvoří řazenou kolekci členů z jeden argument libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="15a7d-137">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="15a7d-138">Protože není zadán typ, funkci lze použít s žádným typem argument.</span><span class="sxs-lookup"><span data-stu-id="15a7d-138">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="15a7d-139">Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="15a7d-139">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>


## <a name="function-bodies"></a><span data-ttu-id="15a7d-140">Těla funkcí</span><span class="sxs-lookup"><span data-stu-id="15a7d-140">Function Bodies</span></span>
<span data-ttu-id="15a7d-141">Tělo funkce může obsahovat definice místní proměnné a funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-141">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="15a7d-142">Tyto proměnné a funkce jsou v oboru v těle aktuální funkce ale není mimo něj.</span><span class="sxs-lookup"><span data-stu-id="15a7d-142">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="15a7d-143">Pokud máte možnost prostá syntaxe povolena, je nutné použít odsazení označuje, že definice v tělo funkce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15a7d-143">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="15a7d-144">Další informace najdete v tématu [pravidla formátování kódu](../code-formatting-guidelines.md) a [podrobná syntaxe](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="15a7d-144">For more information, see [Code Formatting Guidelines](../code-formatting-guidelines.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>


## <a name="return-values"></a><span data-ttu-id="15a7d-145">Návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="15a7d-145">Return Values</span></span>
<span data-ttu-id="15a7d-146">Kompilátor používá k určení návratovou hodnotu a typu výsledný výraz v tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-146">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="15a7d-147">Kompilátor může odvodit typ výsledný výraz z předchozí výrazy.</span><span class="sxs-lookup"><span data-stu-id="15a7d-147">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="15a7d-148">Ve funkci `cylinderVolume`, uvedené v předchozí části, typ `pi` se určí na základě typu literálové `3.14159` být `float`.</span><span class="sxs-lookup"><span data-stu-id="15a7d-148">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="15a7d-149">Kompilátor používá typ `pi` určit typ výrazu `h * pi * r * r` být `float`.</span><span class="sxs-lookup"><span data-stu-id="15a7d-149">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="15a7d-150">Proto je celkové návratový typ funkce `float`.</span><span class="sxs-lookup"><span data-stu-id="15a7d-150">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="15a7d-151">Pokud chcete explicitně zadat návratovou hodnotu, zápisu kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15a7d-151">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="15a7d-152">Jak je kód je uvedeno výše, kompilátor použije **float** celou funkci; Pokud jste na mysli ji použít také typy parametrů, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="15a7d-152">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="15a7d-153">Volání funkce</span><span class="sxs-lookup"><span data-stu-id="15a7d-153">Calling a Function</span></span>
<span data-ttu-id="15a7d-154">Volat funkce tak, že zadáte název funkce následované mezerou a potom všechny argumenty, které jsou oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="15a7d-154">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="15a7d-155">Chcete-li například volání funkce **cylinderVolume** a výsledek přiřadit hodnotu **. denní obj.**, zápis následující kód:</span><span class="sxs-lookup"><span data-stu-id="15a7d-155">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="15a7d-156">Částečné použití argumentů</span><span class="sxs-lookup"><span data-stu-id="15a7d-156">Partial Application of Arguments</span></span>
<span data-ttu-id="15a7d-157">Pokud zadáte menší než zadaný počet argumentů, vytvoříte nové funkce, která očekává zbývající argumenty.</span><span class="sxs-lookup"><span data-stu-id="15a7d-157">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="15a7d-158">Zpracování argumentů tato metoda se označuje jako *currying* a tohoto funkční programovací jazyky jako F #.</span><span class="sxs-lookup"><span data-stu-id="15a7d-158">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="15a7d-159">Předpokládejme například, že pracujete s dvěma velikosti kanálu: jeden má okruhu **2.0** a dalších má okruhu **3.0**.</span><span class="sxs-lookup"><span data-stu-id="15a7d-159">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="15a7d-160">Můžete vytvořit funkce, které určit objem kanálu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15a7d-160">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="15a7d-161">By pak zadáte další argument podle potřeby pro různých délek kanálu pro dva různé velikosti:</span><span class="sxs-lookup"><span data-stu-id="15a7d-161">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]
    
## <a name="recursive-functions"></a><span data-ttu-id="15a7d-162">Rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="15a7d-162">Recursive Functions</span></span>
<span data-ttu-id="15a7d-163">*Rekurzivní funkce* jsou funkce, které volání sebe sama.</span><span class="sxs-lookup"><span data-stu-id="15a7d-163">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="15a7d-164">Potřebují, zda jste zadali **rec** následující – klíčové slovo **let** – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="15a7d-164">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="15a7d-165">Vyvolání funkce rekurzivní z v textu funkce stejně, jako by vyvolání jakékoli volání funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-165">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="15a7d-166">Následující funkce rekurzivní vypočítá  *n* tý Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="15a7d-166">The following recursive function computes the *n*th Fibonacci number.</span></span> <span data-ttu-id="15a7d-167">Pořadí Fibonacciho číslo je známo, od antiquity a je pořadí, ve kterém všechna po sobě jdoucí čísla je součet hodnot předchozích dvou čísel v pořadí.</span><span class="sxs-lookup"><span data-stu-id="15a7d-167">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="15a7d-168">Některé funkce rekurzivní může přetečení zásobníku program nebo proveďte neefektivnímu v případě, že jste Nezapisovat je dát pozor a povědomí o speciální technik, jako je například použití akumulátorů a pokračování.</span><span class="sxs-lookup"><span data-stu-id="15a7d-168">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>


## <a name="function-values"></a><span data-ttu-id="15a7d-169">Hodnoty funkcí</span><span class="sxs-lookup"><span data-stu-id="15a7d-169">Function Values</span></span>
<span data-ttu-id="15a7d-170">V jazyce F # všechny funkce jsou považovány za hodnoty; ve skutečnosti se označují jako *funkce hodnoty*.</span><span class="sxs-lookup"><span data-stu-id="15a7d-170">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="15a7d-171">Protože funkce jsou hodnoty, použitím jako argumenty dalších funkcí, nebo v jiných kontextech kde se používají.</span><span class="sxs-lookup"><span data-stu-id="15a7d-171">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="15a7d-172">Tady je příklad, který přebírá hodnotu funkce jako argument funkce:</span><span class="sxs-lookup"><span data-stu-id="15a7d-172">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="15a7d-173">Zadejte typ hodnoty funkce pomocí `->` tokenu.</span><span class="sxs-lookup"><span data-stu-id="15a7d-173">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="15a7d-174">Na levé straně tohoto tokenu je typ argumentu a na pravé straně je návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15a7d-174">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="15a7d-175">V předchozím příkladu `apply1` je funkce, která přebírá funkci `transform` jako argument, kde `transform` je funkce, která přebírá celé číslo a vrátí jiné číslo.</span><span class="sxs-lookup"><span data-stu-id="15a7d-175">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="15a7d-176">Následující kód ukazuje, jak používat `apply1`:</span><span class="sxs-lookup"><span data-stu-id="15a7d-176">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="15a7d-177">Hodnota `result` bude 101 po spuštění předchozí kód.</span><span class="sxs-lookup"><span data-stu-id="15a7d-177">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="15a7d-178">Více argumentů jsou odděleny následných `->` tokeny, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15a7d-178">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="15a7d-179">Výsledkem je 200.</span><span class="sxs-lookup"><span data-stu-id="15a7d-179">The result is 200.</span></span>


## <a name="lambda-expressions"></a><span data-ttu-id="15a7d-180">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="15a7d-180">Lambda Expressions</span></span>
<span data-ttu-id="15a7d-181">A *výrazu lambda* nepojmenované funkcí.</span><span class="sxs-lookup"><span data-stu-id="15a7d-181">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="15a7d-182">V předchozích příkladech místo definice funkce s názvem **přírůstek** a **mul**, může použití výrazů lambda následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15a7d-182">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="15a7d-183">Můžete definovat pomocí výrazů lambda `fun` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="15a7d-183">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="15a7d-184">Výraz lambda vypadá takto: definice funkce, vyjma toho, že místo `=` token, `->` token slouží k oddělení od tělo funkce seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="15a7d-184">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="15a7d-185">V definici regulární funkce lze odvodit nebo explicitně zadané typy argumentů a návratový typ výrazu lambda je odvozen od typu poslední výrazu v textu.</span><span class="sxs-lookup"><span data-stu-id="15a7d-185">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="15a7d-186">Další informace najdete v tématu [výrazy Lambda: `fun` – klíčové slovo](../functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="15a7d-186">For more information, see [Lambda Expressions: The `fun` Keyword](../functions/lambda-expressions-the-fun-keyword.md).</span></span>


## <a name="function-composition-and-pipelining"></a><span data-ttu-id="15a7d-187">Skládání a paralelní zpracování funkcí</span><span class="sxs-lookup"><span data-stu-id="15a7d-187">Function Composition and Pipelining</span></span>
<span data-ttu-id="15a7d-188">Funkce v jazyce F # se může skládat z dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="15a7d-188">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="15a7d-189">Složení dvě funkce **function1** a **funkce2** je jiné funkce, která představuje použití **function1** a potom aplikaci **funkce2**:</span><span class="sxs-lookup"><span data-stu-id="15a7d-189">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="15a7d-190">Výsledkem je 202.</span><span class="sxs-lookup"><span data-stu-id="15a7d-190">The result is 202.</span></span>

<span data-ttu-id="15a7d-191">Použití kanálů umožňuje funkce volání společně jako po sobě jdoucích operací.</span><span class="sxs-lookup"><span data-stu-id="15a7d-191">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="15a7d-192">Paralelní zpracování funguje takto:</span><span class="sxs-lookup"><span data-stu-id="15a7d-192">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="15a7d-193">Výsledkem je znovu 202.</span><span class="sxs-lookup"><span data-stu-id="15a7d-193">The result is again 202.</span></span>

<span data-ttu-id="15a7d-194">Operátory složení trvat dvě funkce a vrátit funkci; naopak operátorů kanálů funkci a argument a vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15a7d-194">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="15a7d-195">Následující příklad kódu ukazuje rozdíl mezi operátory kanálu a složení zobrazením rozdíly v signatury funkce a využití.</span><span class="sxs-lookup"><span data-stu-id="15a7d-195">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="15a7d-196">Přetížení funkcí</span><span class="sxs-lookup"><span data-stu-id="15a7d-196">Overloading Functions</span></span>
<span data-ttu-id="15a7d-197">Můžete použít přetížení metody typu, ale není funkce.</span><span class="sxs-lookup"><span data-stu-id="15a7d-197">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="15a7d-198">Další informace najdete v tématu [metody](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="15a7d-198">For more information, see [Methods](../members/methods.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="15a7d-199">Viz také</span><span class="sxs-lookup"><span data-stu-id="15a7d-199">See Also</span></span>
[<span data-ttu-id="15a7d-200">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="15a7d-200">Values</span></span>](../values/index.md)

[<span data-ttu-id="15a7d-201">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="15a7d-201">F# Language Reference</span></span>](../index.md)
