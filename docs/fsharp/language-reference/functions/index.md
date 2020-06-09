---
title: Funkce
description: 'Přečtěte si o funkcích v F # a o tom, jak F # podporuje běžné konstrukce funkčního programování.'
ms.date: 05/16/2016
ms.openlocfilehash: e49183e0634dee1750757abadbfe9e9c824f51a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596471"
---
# <a name="functions"></a><span data-ttu-id="f3a5f-103">Funkce</span><span class="sxs-lookup"><span data-stu-id="f3a5f-103">Functions</span></span>

<span data-ttu-id="f3a5f-104">Funkce jsou základní jednotkou spuštění programu v jakémkoli programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="f3a5f-105">Stejně jako v jiných jazycích má funkce jazyka F # název, může mít parametry a přebírat argumenty a má tělo.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="f3a5f-106">Jazyk F # také podporuje konstrukce funkčního programování, jako je zpracování funkcí jako hodnot, použití nepojmenovaných funkcí ve výrazech, složení funkcí pro vytváření nových funkcí, funkcí curryfikované a implicitní definice funkcí pomocí částečného použití argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="f3a5f-107">Funkce definujete pomocí `let` klíčového slova, nebo pokud je funkce rekurzivní, `let rec` kombinace klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3a5f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3a5f-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="f3a5f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3a5f-109">Remarks</span></span>

<span data-ttu-id="f3a5f-110">*Název funkce* je identifikátor, který představuje funkci.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="f3a5f-111">*Seznam parametrů* se skládá z dalších parametrů, které jsou odděleny mezerami.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="f3a5f-112">Můžete zadat explicitní typ pro každý parametr, jak je popsáno v oddílu Parameters.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="f3a5f-113">Pokud nezadáte konkrétní typ argumentu, kompilátor se pokusí odvodit typ z těla funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="f3a5f-114">*Tělo funkce* se skládá z výrazu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="f3a5f-115">Výraz, který tvoří tělo funkce, je typicky složený výraz sestávající z řady výrazů, který je ukončen finálním výrazem, který je návratovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="f3a5f-116">*Návratový typ* je dvojtečka následovaná typem a je volitelná.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="f3a5f-117">Pokud nezadáte typ vrácené hodnoty explicitně, kompilátor určí návratový typ z finálního výrazu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="f3a5f-118">Jednoduchá definice funkce se podobá následující:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="f3a5f-119">V předchozím příkladu je název funkce `f` , argument je `x` , který má typ `int` , tělo funkce `x + 1` a návratová hodnota je typu `int` .</span><span class="sxs-lookup"><span data-stu-id="f3a5f-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="f3a5f-120">Funkce mohou být označeny `inline` .</span><span class="sxs-lookup"><span data-stu-id="f3a5f-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="f3a5f-121">Další informace o naleznete `inline` v tématu [inline Functions](inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f3a5f-121">For information about `inline`, see [Inline Functions](inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="f3a5f-122">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f3a5f-122">Scope</span></span>

<span data-ttu-id="f3a5f-123">Na jakékoli úrovni oboru jiné než obor modulu není k dispozici chyba pro opakované použití hodnoty nebo názvu funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="f3a5f-124">Pokud použijete název znovu, název deklarovaný později vystínuje dříve deklarovaný název.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="f3a5f-125">Nicméně v oboru nejvyšší úrovně v modulu musí být názvy jedinečné.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="f3a5f-126">Například následující kód vyvolá chybu, když se zobrazí v oboru modulu, ale ne, pokud se zobrazí uvnitř funkce:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="f3a5f-127">Ale následující kód je přijatelný na libovolné úrovni oboru:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="f3a5f-128">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3a5f-128">Parameters</span></span>

<span data-ttu-id="f3a5f-129">Názvy parametrů jsou uvedeny za názvem funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="f3a5f-130">Můžete určit typ pro parametr, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="f3a5f-131">Pokud zadáte typ, následuje za názvem parametru a je oddělen od názvu dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="f3a5f-132">Pokud vynecháte typ pro parametr, typ parametru je odvozen kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="f3a5f-133">Například v následující definici funkce je argument odvozen jako typ, `x` `int` protože 1 je typu `int` .</span><span class="sxs-lookup"><span data-stu-id="f3a5f-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="f3a5f-134">Kompilátor se ale pokusí tuto funkci nastavit jako obecnou.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="f3a5f-135">Poznamenejte si například následující kód:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="f3a5f-136">Funkce vytvoří řazenou kolekci členů z jednoho argumentu libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="f3a5f-137">Vzhledem k tomu, že není zadán typ, lze funkci použít s libovolným typem argumentu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="f3a5f-138">Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="f3a5f-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="f3a5f-139">Těla funkcí</span><span class="sxs-lookup"><span data-stu-id="f3a5f-139">Function Bodies</span></span>

<span data-ttu-id="f3a5f-140">Tělo funkce může obsahovat definice místních proměnných a funkcí.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="f3a5f-141">Tyto proměnné a funkce jsou v rozsahu v těle aktuální funkce, ale nejsou mimo ni.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="f3a5f-142">Pokud máte povolenou možnost odlehčené syntaxe, je nutné použít odsazení k označení, že definice je v těle funkce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="f3a5f-143">Další informace najdete v tématu [pokyny pro formátování kódu](../../style-guide/formatting.md) a [podrobnou syntaxi](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="f3a5f-143">For more information, see [Code Formatting Guidelines](../../style-guide/formatting.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="f3a5f-144">Návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="f3a5f-144">Return Values</span></span>

<span data-ttu-id="f3a5f-145">Kompilátor používá konečný výraz v těle funkce k určení návratové hodnoty a typu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="f3a5f-146">Kompilátor může odvodit typ finálního výrazu z předchozích výrazů.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="f3a5f-147">Ve funkci `cylinderVolume` , která je uvedena v předchozí části, je typ typu `pi` určen z typu literálu, `3.14159` který má být `float` .</span><span class="sxs-lookup"><span data-stu-id="f3a5f-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="f3a5f-148">Kompilátor používá typ `pi` k určení typu výrazu, `h * pi * r * r` který má být `float` .</span><span class="sxs-lookup"><span data-stu-id="f3a5f-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="f3a5f-149">Proto je celkový návratový typ funkce `float` .</span><span class="sxs-lookup"><span data-stu-id="f3a5f-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="f3a5f-150">Chcete-li zadat návratovou hodnotu explicitně, napište kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="f3a5f-151">Jak je kód uveden výše, kompilátor použije **float** na celou funkci; Pokud je to vhodné pro použití s typy parametrů, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="f3a5f-152">Volání funkce</span><span class="sxs-lookup"><span data-stu-id="f3a5f-152">Calling a Function</span></span>

<span data-ttu-id="f3a5f-153">Zavoláte funkce zadáním názvu funkce následovaného mezerou a následnými argumenty, které jsou oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="f3a5f-154">Například pro volání funkce **cylinderVolume** a přiřazení výsledku k hodnotě **Vol**, napíšete následující kód:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="f3a5f-155">Částečné použití argumentů</span><span class="sxs-lookup"><span data-stu-id="f3a5f-155">Partial Application of Arguments</span></span>

<span data-ttu-id="f3a5f-156">Pokud zadáte méně, než je zadaný počet argumentů, vytvoříte novou funkci, která očekává zbývající argumenty.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="f3a5f-157">Tato metoda zpracování argumentů je označována jako *procesu curryfikace* a je charakteristickou funkcí programovacích jazyků, jako je F #.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="f3a5f-158">Předpokládejme například, že pracujete se dvěma velikostmi kanálu: jeden má poloměr **2,0** a druhý má poloměr **3,0**.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="f3a5f-159">Mohli byste vytvořit funkce, které určí objem kanálu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="f3a5f-160">Pak zadejte další argument potřebný pro různé délky kanálu dvou různých velikostí:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="f3a5f-161">Rekurzivní funkce</span><span class="sxs-lookup"><span data-stu-id="f3a5f-161">Recursive Functions</span></span>

<span data-ttu-id="f3a5f-162">*Rekurzivní funkce* jsou funkce, které volají samy sebe.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="f3a5f-163">Vyžadují, abyste zadali klíčové slovo **REC** za klíčovým slovem **let** .</span><span class="sxs-lookup"><span data-stu-id="f3a5f-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="f3a5f-164">Vyvolejte rekurzivní funkci z těla funkce stejně, jako byste vyvolali jakékoli volání funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="f3a5f-165">Následující rekurzivní funkce vypočítá *n*-<sup>tý</sup> Fibonacci číslo.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="f3a5f-166">Sekvenci Fibonacci Number bylo známo od poslední chvíle a je sekvence, ve které je každé z následných čísel součtem předchozích dvou čísel v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="f3a5f-167">Některé rekurzivní funkce mohou přetečení zásobníku programu nebo provádět neefektivně, pokud je nezapisujete se péči a s vědomím speciálních technik, jako je například použití akumulátorů a pokračování.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="f3a5f-168">Hodnoty funkcí</span><span class="sxs-lookup"><span data-stu-id="f3a5f-168">Function Values</span></span>

<span data-ttu-id="f3a5f-169">V F # všechny funkce jsou považovány za hodnoty; ve skutečnosti jsou známé jako *hodnoty funkcí*.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="f3a5f-170">Vzhledem k tomu, že funkce jsou hodnoty, mohou být použity jako argumenty pro jiné funkce nebo v jiných kontextech, kde jsou použity hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="f3a5f-171">Následuje příklad funkce, která přebírá hodnotu funkce jako argument:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="f3a5f-172">Zadejte typ hodnoty funkce pomocí `->` tokenu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="f3a5f-173">Na levé straně tohoto tokenu je typ argumentu a na pravé straně je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="f3a5f-174">V předchozím příkladu `apply1` je funkce, která přebírá funkci `transform` jako argument, kde `transform` je funkce, která přebírá celé číslo a vrací jiné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="f3a5f-175">Následující kód ukazuje, jak použít `apply1` :</span><span class="sxs-lookup"><span data-stu-id="f3a5f-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="f3a5f-176">Hodnota `result` bude 101 až po spuštění předchozího kódu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="f3a5f-177">Více argumentů je odděleno pomocí následných `->` tokenů, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="f3a5f-178">Výsledek je 200.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="f3a5f-179">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="f3a5f-179">Lambda Expressions</span></span>

<span data-ttu-id="f3a5f-180">*Výraz lambda* je nepojmenovaná funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="f3a5f-181">V předchozích příkladech se místo definování pojmenovaných funkcí **zvýší** a **mul**můžete použít lambda výrazy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="f3a5f-182">Lambda výrazy definujete pomocí `fun` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="f3a5f-183">Výraz lambda se podobá definici funkce, s tím rozdílem, že místo `=` tokenu se `->` token používá k oddělení seznamu argumentů od těla funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="f3a5f-184">Stejně jako v definici regulární funkce lze typy argumentů odvodit nebo zadat explicitně a návratový typ výrazu lambda je odvozený od typu posledního výrazu v těle.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="f3a5f-185">Další informace naleznete v tématu [výrazy lambda: `fun` klíčové slovo](lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="f3a5f-185">For more information, see [Lambda Expressions: The `fun` Keyword](lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="f3a5f-186">Skládání a paralelní zpracování funkcí</span><span class="sxs-lookup"><span data-stu-id="f3a5f-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="f3a5f-187">Funkce v jazyce F # mohou být tvořeny jinými funkcemi.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="f3a5f-188">Složení dvou funkcí **Function1** a **function2** je další funkce, která představuje aplikaci **Function1** , která následuje po použití **function2**:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="f3a5f-189">Výsledek je 202.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-189">The result is 202.</span></span>

<span data-ttu-id="f3a5f-190">Přesměrování umožňuje zřetězení volání funkcí jako po sobě jdoucích operací.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="f3a5f-191">Přesměrování funguje následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f3a5f-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="f3a5f-192">Výsledek je znovu 202.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-192">The result is again 202.</span></span>

<span data-ttu-id="f3a5f-193">Operátory kompozice přijímají dvě funkce a vracejí funkci. Naproti tomu operátory kanálu přebírají funkci a argument a vracejí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="f3a5f-194">Následující příklad kódu ukazuje rozdíl mezi operátory kanálu a sestavování zobrazením rozdílů v části signatury a využití funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

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

## <a name="overloading-functions"></a><span data-ttu-id="f3a5f-195">Přetížení funkcí</span><span class="sxs-lookup"><span data-stu-id="f3a5f-195">Overloading Functions</span></span>

<span data-ttu-id="f3a5f-196">Můžete přetížit metody typu, ale ne funkce.</span><span class="sxs-lookup"><span data-stu-id="f3a5f-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="f3a5f-197">Další informace naleznete v tématu [metody](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="f3a5f-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3a5f-198">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3a5f-198">See also</span></span>

- [<span data-ttu-id="f3a5f-199">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="f3a5f-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="f3a5f-200">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="f3a5f-200">F# Language Reference</span></span>](../index.md)
