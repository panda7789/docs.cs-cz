---
title: Funkce (F#)
description: 'Informace o funkcích v F # a jak F # podporuje běžné konstrukce funkčního programování.'
ms.date: 05/16/2016
ms.openlocfilehash: 717eba7e69398048d229173e07ccc376797171bb
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703749"
---
# <a name="functions"></a><span data-ttu-id="15361-103">Funkce</span><span class="sxs-lookup"><span data-stu-id="15361-103">Functions</span></span>

<span data-ttu-id="15361-104">Funkce je základní jednotkou spuštění programu v jakémkoli programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="15361-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="15361-105">Stejně jako v jiných jazycích má název funkce jazyka F #, mohou mít parametry a argumenty vzít a má tělo.</span><span class="sxs-lookup"><span data-stu-id="15361-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="15361-106">F # podporuje také konstrukcí funkčního programování, jako je zpracování funkce jako hodnoty, použití nepojmenované funkce ve výrazech, složení funkcí k vytvoření nové funkce, curryfikované funkce a implicitní definice funkce prostřednictvím částečnou použití argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="15361-107">Definování funkcí s použitím `let` – klíčové slovo, nebo v případě, funkce je rekurzivní, `let rec` – kombinace klíčových slov.</span><span class="sxs-lookup"><span data-stu-id="15361-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="15361-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15361-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="15361-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15361-109">Remarks</span></span>

<span data-ttu-id="15361-110">*Název funkce* je identifikátor, který představuje funkci.</span><span class="sxs-lookup"><span data-stu-id="15361-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="15361-111">*Seznam parametrů* se skládá z po sobě jdoucích parametry, které jsou odděleny mezer.</span><span class="sxs-lookup"><span data-stu-id="15361-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="15361-112">Explicitní typ pro každý parametr, můžete určit, jak je popsáno v oddílu parametry.</span><span class="sxs-lookup"><span data-stu-id="15361-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="15361-113">Pokud nezadáte konkrétní argument typu, kompilátor se pokusí odvodit typ z těla funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="15361-114">*Tělo funkce* se skládá z výrazu.</span><span class="sxs-lookup"><span data-stu-id="15361-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="15361-115">Výraz, který tvoří tělo funkce je obvykle ze složeného výrazu, který se skládá z počet výrazů, které přineslo výsledný výraz, který je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="15361-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="15361-116">*Návratový typ* dvojtečku následovanou typ a je volitelný.</span><span class="sxs-lookup"><span data-stu-id="15361-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="15361-117">Pokud explicitně nezadáte typ vrácené hodnoty, kompilátor Určuje typ návratové hodnoty z: výsledný výraz.</span><span class="sxs-lookup"><span data-stu-id="15361-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="15361-118">Definice jednoduchý funkce vypadá přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="15361-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="15361-119">V předchozím příkladu je název funkce `f`, má argument hodnotu `x`, která má typ `int`, je tělo funkce `x + 1`, a návratová hodnota je typu `int`.</span><span class="sxs-lookup"><span data-stu-id="15361-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="15361-120">Funkce mohou být označeny `inline`.</span><span class="sxs-lookup"><span data-stu-id="15361-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="15361-121">Informace o `inline`, naleznete v tématu [vložené funkce](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="15361-121">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="15361-122">Rozsah</span><span class="sxs-lookup"><span data-stu-id="15361-122">Scope</span></span>

<span data-ttu-id="15361-123">Na libovolné úrovni oboru, než je rozsah modulu není chybu pro opětovné použití názvu hodnotě nebo funkci.</span><span class="sxs-lookup"><span data-stu-id="15361-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="15361-124">Pokud je znovu použít název, název deklarován později zastiňuje název deklarovaný dříve.</span><span class="sxs-lookup"><span data-stu-id="15361-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="15361-125">V oboru nejvyšší úrovně v modulu, musí být jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="15361-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="15361-126">Například následující kód vygeneruje chybu, když se objeví v oboru modulu, ale ne v případě, že se zobrazí uvnitř funkce:</span><span class="sxs-lookup"><span data-stu-id="15361-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="15361-127">Ale následující kód je přijatelné na libovolné úrovni rozsahu:</span><span class="sxs-lookup"><span data-stu-id="15361-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="15361-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="15361-128">Parameters</span></span>

<span data-ttu-id="15361-129">Názvy parametrů jsou uvedeny za názvem funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="15361-130">Typ pro parametr, můžete určit, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15361-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="15361-131">Pokud chcete zadat typ, následuje název parametru a od názvu oddělené dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="15361-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="15361-132">Vynecháte-li typ pro parametr, typ parametru je odvozen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="15361-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="15361-133">Například v následující definici funkce, argument `x` odvodit typ `int` protože 1 je typu `int`.</span><span class="sxs-lookup"><span data-stu-id="15361-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="15361-134">Však kompilátor se pokusí provést funkci co je to možné.</span><span class="sxs-lookup"><span data-stu-id="15361-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="15361-135">Například vezměte na vědomí následující kód:</span><span class="sxs-lookup"><span data-stu-id="15361-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="15361-136">Funkce vytvoří řazenou kolekci členů ze jedním argumentem libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="15361-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="15361-137">Protože není zadaný typ, funkci lze použít s žádným typem argumentu.</span><span class="sxs-lookup"><span data-stu-id="15361-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="15361-138">Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="15361-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="15361-139">Těla funkcí</span><span class="sxs-lookup"><span data-stu-id="15361-139">Function Bodies</span></span>

<span data-ttu-id="15361-140">Tělo funkce může obsahovat definice lokální proměnné a funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="15361-141">Tyto proměnné a funkce jsou v rozsahu aktuální funkce, ale ne mimo tělo.</span><span class="sxs-lookup"><span data-stu-id="15361-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="15361-142">Až budete mít povolenou možností nenáročném syntaxi, musíte použít odsazení označuje, že definice v těle funkce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15361-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="15361-143">Další informace najdete v tématu [pravidla formátování kódu](../code-formatting-guidelines.md) a [podrobná syntaxe](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="15361-143">For more information, see [Code Formatting Guidelines](../code-formatting-guidelines.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="15361-144">Návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="15361-144">Return Values</span></span>

<span data-ttu-id="15361-145">Kompilátor používá k určení návratovou hodnotu a typ výsledný výraz v těle funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="15361-146">Kompilátor může odvodit typ výrazu konečné z předchozích výrazů.</span><span class="sxs-lookup"><span data-stu-id="15361-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="15361-147">Ve funkci `cylinderVolume`, jak je znázorněno v předchozí části, typ `pi` se určí na základě typu literál `3.14159` bude `float`.</span><span class="sxs-lookup"><span data-stu-id="15361-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="15361-148">Kompilátor používá typ `pi` určit typ výrazu `h * pi * r * r` bude `float`.</span><span class="sxs-lookup"><span data-stu-id="15361-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="15361-149">Proto celkové návratový typ funkce je `float`.</span><span class="sxs-lookup"><span data-stu-id="15361-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="15361-150">K určení návratovou hodnotu explicitně, napište kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15361-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="15361-151">Kód je uvedená výše, použije kompilátor **float** na celou funkci; Pokud jste v úmyslu použít typům parametrů, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="15361-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="15361-152">Volání funkce</span><span class="sxs-lookup"><span data-stu-id="15361-152">Calling a Function</span></span>

<span data-ttu-id="15361-153">Volání funkce tak, že zadáte název funkce, za nímž následuje mezera a potom všechny argumenty oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="15361-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="15361-154">Například volání funkce **cylinderVolume** a výsledek přiřaďte hodnotu **. denní obj.**, napište následující kód:</span><span class="sxs-lookup"><span data-stu-id="15361-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="15361-155">Částečné použití argumentů</span><span class="sxs-lookup"><span data-stu-id="15361-155">Partial Application of Arguments</span></span>

<span data-ttu-id="15361-156">Pokud zadáte méně než zadaný počet argumentů, vytvoříte novou funkci, která očekává zbývajících argumentů.</span><span class="sxs-lookup"><span data-stu-id="15361-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="15361-157">Tento způsob zpracování argumentů se označuje jako *curryfikace* a je znakem funkčních programovacích jazyků, jako je F #.</span><span class="sxs-lookup"><span data-stu-id="15361-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="15361-158">Předpokládejme například, že pracujete s dvou velikostech kanálu: jeden má poloměr **2.0** a druhý má poloměr **3.0**.</span><span class="sxs-lookup"><span data-stu-id="15361-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="15361-159">Můžete například vytvořit funkce, které určují objem kanálu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15361-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="15361-160">Další argument by pak poskytnete podle potřeby pro různé délky kanálu pro dvě různé velikosti:</span><span class="sxs-lookup"><span data-stu-id="15361-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="15361-161">Rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="15361-161">Recursive Functions</span></span>

<span data-ttu-id="15361-162">*Rekurzivní funkce* jsou funkce, které volání sebe sama.</span><span class="sxs-lookup"><span data-stu-id="15361-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="15361-163">Vyžadují, abyste určili **rec** následující klíčové slovo **nechat** – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="15361-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="15361-164">Volání rekurzivní funkce v rámci těla funkce stejně, jako by volání jakékoli volání funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="15361-165">Následující rekurzivní funkce vypočítá *n*<sup>th</sup> Fibonacciho číslo.</span><span class="sxs-lookup"><span data-stu-id="15361-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="15361-166">Pořadí Fibonacciho číslo bylo zjištěno od antiquity a je pořadí, ve kterém je každý po sobě jdoucí čísla součtu předchozích dvou čísel v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="15361-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="15361-167">Některé rekurzivní funkce mohou přetečení zásobníku programu nebo provést neefektivně, pokud nenapíšete je s opatrností a s povědomí o speciální techniky, jako je například používání průběžné součty a pokračování.</span><span class="sxs-lookup"><span data-stu-id="15361-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="15361-168">Hodnoty funkcí</span><span class="sxs-lookup"><span data-stu-id="15361-168">Function Values</span></span>

<span data-ttu-id="15361-169">V jazyce F # všechny funkce jsou považovány za hodnot. ve skutečnosti jsou označovány jako *funkce hodnoty*.</span><span class="sxs-lookup"><span data-stu-id="15361-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="15361-170">Protože funkce jsou hodnoty, se může sloužit jako argumenty dalších funkcí nebo v jiném kontextu použití hodnot.</span><span class="sxs-lookup"><span data-stu-id="15361-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="15361-171">Tady je příklad, který přijímá hodnotu funkce jako argument funkce:</span><span class="sxs-lookup"><span data-stu-id="15361-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="15361-172">Určení typu hodnota funkce s použitím `->` token.</span><span class="sxs-lookup"><span data-stu-id="15361-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="15361-173">Na levé straně tohoto tokenu je typ argumentu a na pravé straně je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="15361-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="15361-174">V předchozím příkladu `apply1` je funkce, která má funkci `transform` jako argument, ve kterém `transform` je funkce, která přebírá celé číslo a vrátí jinou celé číslo.</span><span class="sxs-lookup"><span data-stu-id="15361-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="15361-175">Následující kód ukazuje, jak používat `apply1`:</span><span class="sxs-lookup"><span data-stu-id="15361-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="15361-176">Hodnota `result` bude 101 po spuštění předchozího kódu.</span><span class="sxs-lookup"><span data-stu-id="15361-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="15361-177">Více argumentů jsou odděleny po sobě jdoucích `->` tokeny, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15361-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="15361-178">Výsledkem je 200.</span><span class="sxs-lookup"><span data-stu-id="15361-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="15361-179">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="15361-179">Lambda Expressions</span></span>

<span data-ttu-id="15361-180">A *výraz lambda* je nepojmenovaný funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="15361-181">V předchozích příkladech místo definování pojmenované funkce **přírůstek** a **mul**, můžete použít výrazy lambda následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15361-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="15361-182">Můžete definovat pomocí výrazů lambda `fun` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="15361-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="15361-183">Výraz lambda se podobá definici funkce, s výjimkou, že místo `=` token, `->` token se používá k oddělení seznamu argumentů z těla funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="15361-184">Stejně jako v definici normální funkce typy argumentů lze odvodit nebo zadat explicitně a návratový typ výrazu lambda je odvozen z typu posledního výrazu v textu.</span><span class="sxs-lookup"><span data-stu-id="15361-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="15361-185">Další informace najdete v tématu [výrazy Lambda: `fun` – klíčové slovo](../functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="15361-185">For more information, see [Lambda Expressions: The `fun` Keyword](../functions/lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="15361-186">Skládání a paralelní zpracování funkcí</span><span class="sxs-lookup"><span data-stu-id="15361-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="15361-187">Funkce jazyka F # se může skládat z dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="15361-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="15361-188">Složení dvou funkcí **function1** a **function2** je další funkci, která představuje použití **function1** a potom aplikaci **function2**:</span><span class="sxs-lookup"><span data-stu-id="15361-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="15361-189">Výsledkem je 202.</span><span class="sxs-lookup"><span data-stu-id="15361-189">The result is 202.</span></span>

<span data-ttu-id="15361-190">Paralelní zpracování volání funkce umožňuje být zřetězen dohromady jako následných operací.</span><span class="sxs-lookup"><span data-stu-id="15361-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="15361-191">Paralelní zpracování funguje takto:</span><span class="sxs-lookup"><span data-stu-id="15361-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="15361-192">Výsledkem je znovu 202.</span><span class="sxs-lookup"><span data-stu-id="15361-192">The result is again 202.</span></span>

<span data-ttu-id="15361-193">Operátory složení dvou funkcí používají a vrací funkci. operátory kanálu oproti tomu funkce a argument a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15361-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="15361-194">Následující příklad kódu ukazuje rozdíl mezi operátory kanálu a skládání tím, že zobrazuje rozdíly v podpisech funkcí a využití.</span><span class="sxs-lookup"><span data-stu-id="15361-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

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

## <a name="overloading-functions"></a><span data-ttu-id="15361-195">Přetížení funkcí</span><span class="sxs-lookup"><span data-stu-id="15361-195">Overloading Functions</span></span>

<span data-ttu-id="15361-196">Můžete použít přetížení metody typu, ale není funkce.</span><span class="sxs-lookup"><span data-stu-id="15361-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="15361-197">Další informace najdete v tématu [metody](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="15361-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15361-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15361-198">See also</span></span>

- [<span data-ttu-id="15361-199">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="15361-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="15361-200">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="15361-200">F# Language Reference</span></span>](../index.md)
