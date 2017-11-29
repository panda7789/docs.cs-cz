---
title: "Funkce jako hodnoty první třídy (F#)"
description: "Zjistěte, jak funkce zvýší na první třídy stav v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="b77fb-104">Funkce jako hodnoty první třídy</span><span class="sxs-lookup"><span data-stu-id="b77fb-104">Functions as First-Class Values</span></span>

<span data-ttu-id="b77fb-105">Charakteristickým znakem funkčních programovacích jazyků je povýšení funkcí do stavu první kategorie.</span><span class="sxs-lookup"><span data-stu-id="b77fb-105">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="b77fb-106">Měli byste být schopni s funkcí provádět to, co můžete provádět s hodnotami ostatních předdefinovaných typů, a rovněž byste měli být schopni tak činit se srovnatelnou mírou úsilí.</span><span class="sxs-lookup"><span data-stu-id="b77fb-106">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="b77fb-107">Typická opatření stavu první kategorie zahrnují:</span><span class="sxs-lookup"><span data-stu-id="b77fb-107">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="b77fb-108">Můžete vázat na identifikátory funkce?</span><span class="sxs-lookup"><span data-stu-id="b77fb-108">Can you bind functions to identifiers?</span></span> <span data-ttu-id="b77fb-109">To znamená můžete je přiřadit jim názvy?</span><span class="sxs-lookup"><span data-stu-id="b77fb-109">That is, can you give them names?</span></span>

- <span data-ttu-id="b77fb-110">Můžete ukládat funkcí v datové struktury, například v seznamu?</span><span class="sxs-lookup"><span data-stu-id="b77fb-110">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="b77fb-111">Můžete předat jako argument ve volání funkce funkci?</span><span class="sxs-lookup"><span data-stu-id="b77fb-111">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="b77fb-112">Může vrátit funkce z volání funkce?</span><span class="sxs-lookup"><span data-stu-id="b77fb-112">Can you return a function from a function call?</span></span>

<span data-ttu-id="b77fb-113">Posledních dvou míry definovat, co se označují jako *vyšší pořadí operací* nebo *vyšší pořadí funkce*.</span><span class="sxs-lookup"><span data-stu-id="b77fb-113">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="b77fb-114">Funkce vyššího řádu přijímají funkce jako argumenty a vrací funkce jako hodnotu volání funkce.</span><span class="sxs-lookup"><span data-stu-id="b77fb-114">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="b77fb-115">Tyto operace podporují stěžejní části funkčního programování, jako jsou funkce mapování a skládání funkcí.</span><span class="sxs-lookup"><span data-stu-id="b77fb-115">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="b77fb-116">Přiřazení názvu hodnotě</span><span class="sxs-lookup"><span data-stu-id="b77fb-116">Give the Value a Name</span></span>

<span data-ttu-id="b77fb-117">Pokud je funkce hodnotou první kategorie, je třeba ji pojmenovat, stejně jako lze pojmenovat celá čísla, řetězce a další předdefinované typy.</span><span class="sxs-lookup"><span data-stu-id="b77fb-117">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="b77fb-118">Na to je podle literatury o funkčním programování odkazováno jako na vázání identifikátoru na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b77fb-118">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="b77fb-119">F # používá [ `let` vazby](../language-reference/functions/let-bindings.md) k vytvoření vazby. názvy hodnot: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-119">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="b77fb-120">Následující kód ukazuje dva příklady.</span><span class="sxs-lookup"><span data-stu-id="b77fb-120">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="b77fb-121">Funkci lze pojmenovat stejně snadno.</span><span class="sxs-lookup"><span data-stu-id="b77fb-121">You can name a function just as easily.</span></span> <span data-ttu-id="b77fb-122">V následujícím příkladu definuje funkci s názvem `squareIt` pomocí vytvoření vazby identifikátor `squareIt` k [výrazu lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-122">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="b77fb-123">Funkce `squareIt` má jeden parametr `n` a vrací druhou mocninu tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="b77fb-123">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="b77fb-124">Jazyk F# poskytuje pro dosažení stejného výsledku s kratším zápisem následující stručnější syntaxi.</span><span class="sxs-lookup"><span data-stu-id="b77fb-124">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="b77fb-125">Následující příklady používají pro zvýraznění podobností mezi deklaracemi funkcí a deklaracemi dalších typů hodnot převážně první styl, `let <function-name> = <lambda-expression>`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-125">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="b77fb-126">Všechny pojmenované funkce lze ale také zapsat pomocí stručnější syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b77fb-126">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="b77fb-127">Některé příklady jsou zapsány oběma způsoby.</span><span class="sxs-lookup"><span data-stu-id="b77fb-127">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="b77fb-128">Uložení hodnoty do datové struktury</span><span class="sxs-lookup"><span data-stu-id="b77fb-128">Store the Value in a Data Structure</span></span>

<span data-ttu-id="b77fb-129">Hodnota první kategorie může být uložena v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="b77fb-129">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="b77fb-130">Následující kód ukazuje příklady, které ukládají hodnoty v seznamech a řazených kolekcích členů.</span><span class="sxs-lookup"><span data-stu-id="b77fb-130">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="b77fb-131">Za účelem ověření, že název funkce uložený v řazené kolekci členů povede ve skutečnosti k vyhodnocení funkce, používá následující příklad operátory `fst` a `snd` pro získání prvního a druhého prvku z řazené kolekce členů `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-131">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="b77fb-132">První prvek v řazené kolekci členů je `squareIt` a druhý prvek je `num`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-132">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="b77fb-133">Identifikátor `num` je v předchozím příkladu svázán s celým číslem 10, platným argumentem pro funkci `squareIt`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-133">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="b77fb-134">Druhý výraz použije první prvek v řazené kolekci členů na druhý prvek řazené kolekce členů: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-134">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="b77fb-135">Podobně jako lze identifikátor `num` zaměnit s celým číslem 10, lze zaměnit identifikátor `squareIt` s výrazem lambda `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-135">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="b77fb-136">Předání hodnoty jako argumentu</span><span class="sxs-lookup"><span data-stu-id="b77fb-136">Pass the Value as an Argument</span></span>

<span data-ttu-id="b77fb-137">Pokud hodnota patří k hodnotám stavu první kategorie jazyka, lze ji předat jako argument funkce.</span><span class="sxs-lookup"><span data-stu-id="b77fb-137">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="b77fb-138">Je například běžné předávat jako argumenty celá čísla a řetězce.</span><span class="sxs-lookup"><span data-stu-id="b77fb-138">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="b77fb-139">Následující kód ukazuje předání celých čísel a řetězců jako argumentů v jazyce F#.</span><span class="sxs-lookup"><span data-stu-id="b77fb-139">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="b77fb-140">Pokud jsou funkce ve stavu hodnoty první kategorie, musíte být schopni je stejným způsobem předat jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="b77fb-140">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="b77fb-141">Zapamatujte si, že se jedná o první charakteristiku funkcí vyššího řádu.</span><span class="sxs-lookup"><span data-stu-id="b77fb-141">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="b77fb-142">V následujícím příkladu má funkce `applyIt` dva parametry, `op` a `arg`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-142">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="b77fb-143">Pokud do parametru `op` předáte funkci, která má jeden parametr, a odpovídající argument funkce předáte do parametru `arg`, funkce vrátí výsledek použití parametru `op` do parametru `arg`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-143">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="b77fb-144">V následujícím příkladu jsou oba argumenty – argument funkce a argument celého čísla – odeslány stejným způsobem, a to použitím jejich názvů.</span><span class="sxs-lookup"><span data-stu-id="b77fb-144">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="b77fb-145">Možnost odeslat funkci jako argument do jiné funkce je základem společných abstrakcí ve funkčních programovacích jazycích, jako jsou například operace mapování nebo filtrování.</span><span class="sxs-lookup"><span data-stu-id="b77fb-145">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="b77fb-146">Například operace mapování je funkce vyššího řádu, která zachytává výpočet sdílený funkcemi, jež prochází seznamem, u každého prvku provedou nějakou operaci a poté vrátí seznam výsledků.</span><span class="sxs-lookup"><span data-stu-id="b77fb-146">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="b77fb-147">Může být například třeba zvýšit každý prvek v seznamu celých čísel o jedna, každý prvek umocnit na druhou nebo převést každý prvek seznamu řetězců na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="b77fb-147">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="b77fb-148">Rekurzivní proces, který prochází seznam a vytváří seznam výsledků k vrácení, je část výpočtu náchylná k chybám.</span><span class="sxs-lookup"><span data-stu-id="b77fb-148">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="b77fb-149">Tato část je zachycena ve funkci mapování.</span><span class="sxs-lookup"><span data-stu-id="b77fb-149">That part is captured in the mapping function.</span></span> <span data-ttu-id="b77fb-150">Jediné, co je třeba napsat pro konkrétní aplikaci, je funkce, kterou chcete použít na každý jednotlivý prvek seznamu (sčítání, umocňování, změna velikosti písmen).</span><span class="sxs-lookup"><span data-stu-id="b77fb-150">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="b77fb-151">Tato funkce je předána jako argument funkci mapování, stejně jako je v předchozím příkladu prvek `squareIt` předán do funkce `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-151">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="b77fb-152">F # poskytuje metody mapy pro většinu typy kolekcí, včetně [uvádí](../language-reference/lists.md), [pole](../language-reference/arrays.md), a [pořadí](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="b77fb-152">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="b77fb-153">Následující příklady používají seznamy.</span><span class="sxs-lookup"><span data-stu-id="b77fb-153">The following examples use lists.</span></span> <span data-ttu-id="b77fb-154">Syntaxe je `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-154">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="b77fb-155">Další informace najdete v tématu [uvádí](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="b77fb-155">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="b77fb-156">Vrácení hodnoty z volání funkce</span><span class="sxs-lookup"><span data-stu-id="b77fb-156">Return the Value from a Function Call</span></span>

<span data-ttu-id="b77fb-157">Pokud je funkce v jazyce ve stavu hodnoty první kategorie, musí být možné ji vrátit jako hodnotu volání funkce, stejně tak jako jsou vraceny další typy, jako například celá čísla a řetězce.</span><span class="sxs-lookup"><span data-stu-id="b77fb-157">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="b77fb-158">Následující volání funkce vrací celá čísla a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="b77fb-158">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="b77fb-159">Následující volání funkce vrací řetězec.</span><span class="sxs-lookup"><span data-stu-id="b77fb-159">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="b77fb-160">Následující volání funkce, deklarované na jednom řádku, vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b77fb-160">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="b77fb-161">Zobrazená hodnota je `True`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-161">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="b77fb-162">Schopnost vracet funkci jako hodnotu volání funkce je druhým charakteristickým znakem funkcí vyššího řádu.</span><span class="sxs-lookup"><span data-stu-id="b77fb-162">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="b77fb-163">V následujícím příkladu je `checkFor` definováno jako funkce, která převezme jeden argument, `item`, a jako hodnotu vrátí novou funkci.</span><span class="sxs-lookup"><span data-stu-id="b77fb-163">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="b77fb-164">Vrácená funkce převezme seznam jako argument `lst` a v argumentu `item` vyhledá prvek `lst`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-164">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="b77fb-165">Pokud je prvek `item` nalezen, funkce vrací hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-165">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="b77fb-166">Pokud není prvek `item` nalezen, funkce vrací hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-166">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="b77fb-167">Jako v předchozí části, následující kód používá funkci zadaný seznam, [list.EXISTS –](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), aby v seznamu Hledat.</span><span class="sxs-lookup"><span data-stu-id="b77fb-167">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="b77fb-168">Následující kód používá pro vytvoření nové funkce funkci `checkFor`, která přijímá jeden argument – seznam – a vyhledá v něm číslo 7.</span><span class="sxs-lookup"><span data-stu-id="b77fb-168">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="b77fb-169">Následující příklad používá pro deklaraci funkce `compose`, která vrací složení dvou argumentů funkce, stav první kategorie funkcí jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="b77fb-169">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="b77fb-170">Ještě kratší verzi naleznete v následující části „Curryfikované funkce“.</span><span class="sxs-lookup"><span data-stu-id="b77fb-170">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="b77fb-171">Následující kód předá funkci `compose` dvě funkce jako argumenty, obě přijímající jediný argument stejného typu.</span><span class="sxs-lookup"><span data-stu-id="b77fb-171">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="b77fb-172">Vrácená hodnota je nová funkce, která je složením obou argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="b77fb-172">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="b77fb-173">Jazyk F# obsahuje dva operátory skládající funkce, `<<` a `>>`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-173">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="b77fb-174">Například `let squareAndDouble2 = doubleIt << squareIt` je ekvivalentní zápisu `let squareAndDouble = compose doubleIt squareIt` z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="b77fb-174">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="b77fb-175">Následující příklad vrácení funkce jako hodnoty volání funkce vytvoří jednoduchou hádací hru.</span><span class="sxs-lookup"><span data-stu-id="b77fb-175">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="b77fb-176">Pro tvorbu hry je třeba zavolat funkci `makeGame` s hodnotou, kterou má někdo uhodnout, předanou do argumentu `target`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-176">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="b77fb-177">Vrácená hodnota z funkce `makeGame` je funkce, která přijímá jeden argument (odhad) a hlásí, zda je odhad správný.</span><span class="sxs-lookup"><span data-stu-id="b77fb-177">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="b77fb-178">Následující kód volá funkci `makeGame` předávající hodnotu `7` do argumentu `target`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-178">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="b77fb-179">Identifikátor `playGame` je vázán na vrácený výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="b77fb-179">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="b77fb-180">Proto funkce `playGame` přijímá jako svůj argument hodnotu funkce `guess`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-180">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="b77fb-181">Curryfikované funkce</span><span class="sxs-lookup"><span data-stu-id="b77fb-181">Curried Functions</span></span>

<span data-ttu-id="b77fb-182">Mnoho příkladů v předchozí části lze zapsat více výstižně díky implicitní *currying* v deklaracích funkce F #.</span><span class="sxs-lookup"><span data-stu-id="b77fb-182">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="b77fb-183">Curryfikace je proces, jenž transformuje funkci, která má více než jeden parametr do řady vložených funkcí, z nichž každá má jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="b77fb-183">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="b77fb-184">V jazyce F# jsou funkce, které mají více než jeden parametr, ze své podstaty curryfikovány.</span><span class="sxs-lookup"><span data-stu-id="b77fb-184">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="b77fb-185">Například funkci `compose` z předchozí části lze zapsat pomocí následujícího stručného stylu se třemi parametry.</span><span class="sxs-lookup"><span data-stu-id="b77fb-185">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="b77fb-186">Výsledkem je ale funkce jednoho parametru, jež vrací funkci jednoho parametru, která zase vrací jinou funkci jednoho parametru tak, jak je vidět ve funkci `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-186">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="b77fb-187">K této funkci lze přistupovat několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="b77fb-187">You can access this function in several ways.</span></span> <span data-ttu-id="b77fb-188">Každý z následujících příkladů vrátí a zobrazí číslo 18.</span><span class="sxs-lookup"><span data-stu-id="b77fb-188">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="b77fb-189">Funkci `compose4` lze v jakémkoli příkladě nahradit funkcí `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-189">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="b77fb-190">Pro ověření, zda funkce stále pracuje stejně jako dříve, lze opětovně vyzkoušet původní testovací případy.</span><span class="sxs-lookup"><span data-stu-id="b77fb-190">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="b77fb-191">Curryfikaci lze omezit uzavřením parametrů do řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="b77fb-191">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="b77fb-192">Další informace najdete v tématu "Parametr vzory" v [parametry a argumenty](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b77fb-192">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="b77fb-193">Následující příklad používá implicitní curryfikaci pro zápis kratší verze funkce `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-193">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="b77fb-194">Podrobné informace o tom, jak funkce `makeGame` konstruuje a vrací funkci `game`, jsou v tomto formátu méně explicitní, ale pomocí původních testovacích případů lze ověřit, že je výsledek stejný.</span><span class="sxs-lookup"><span data-stu-id="b77fb-194">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="b77fb-195">Další informace o currying, najdete v části "Částečné aplikace argumenty" v [funkce](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="b77fb-195">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="b77fb-196">Definice identifikátoru a funkce jsou zaměnitelné</span><span class="sxs-lookup"><span data-stu-id="b77fb-196">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="b77fb-197">Název proměnné `num` je v předchozích příkladech vyhodnocen jako celé číslo 10 a není žádným překvapením, že pokud je proměnná `num` platná, číslo 10 je také platné.</span><span class="sxs-lookup"><span data-stu-id="b77fb-197">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="b77fb-198">Totéž platí i pro identifikátory funkcí a jejich hodnoty: kdekoli lze použít název funkce, lze také použít výraz lambda, se kterým je funkce svázána.</span><span class="sxs-lookup"><span data-stu-id="b77fb-198">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="b77fb-199">Následující příklad definuje funkci `Boolean` s názvem `isNegative`, poté použije název funkce a následně místo něj použije její definici.</span><span class="sxs-lookup"><span data-stu-id="b77fb-199">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="b77fb-200">Všechny tři následující příklady vracejí hodnotu `False` a zobrazují ji.</span><span class="sxs-lookup"><span data-stu-id="b77fb-200">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="b77fb-201">Pro provedení dalšího kroku nahraďte hodnotu, ke které je svázán identifikátor `applyIt`, hodnotou `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="b77fb-201">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="b77fb-202">Funkce jsou v jazyce F# hodnotami první kategorie</span><span class="sxs-lookup"><span data-stu-id="b77fb-202">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="b77fb-203">Příklady v předchozích částech ukazují, že funkce jazyka F# splňují kritéria pro hodnoty první kategorie:</span><span class="sxs-lookup"><span data-stu-id="b77fb-203">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="b77fb-204">Identifikátor lze svázat s definicí funkce.</span><span class="sxs-lookup"><span data-stu-id="b77fb-204">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="b77fb-205">Funkci lze uložit v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="b77fb-205">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="b77fb-206">Funkci lze předat jako argument.</span><span class="sxs-lookup"><span data-stu-id="b77fb-206">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="b77fb-207">Funkci lze vrátit jako hodnotu volání funkce.</span><span class="sxs-lookup"><span data-stu-id="b77fb-207">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="b77fb-208">Další informace o F # najdete v tématu [referenční dokumentace jazyka F #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="b77fb-208">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="b77fb-209">Příklad</span><span class="sxs-lookup"><span data-stu-id="b77fb-209">Example</span></span>

### <a name="description"></a><span data-ttu-id="b77fb-210">Popis</span><span class="sxs-lookup"><span data-stu-id="b77fb-210">Description</span></span>

<span data-ttu-id="b77fb-211">Následující kód obsahuje všechny příklady v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="b77fb-211">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="b77fb-212">Kód</span><span class="sxs-lookup"><span data-stu-id="b77fb-212">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="b77fb-213">Viz také</span><span class="sxs-lookup"><span data-stu-id="b77fb-213">See Also</span></span>

[<span data-ttu-id="b77fb-214">Seznamy</span><span class="sxs-lookup"><span data-stu-id="b77fb-214">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="b77fb-215">Řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="b77fb-215">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="b77fb-216">Funkce</span><span class="sxs-lookup"><span data-stu-id="b77fb-216">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="b77fb-217">`let`Vazby</span><span class="sxs-lookup"><span data-stu-id="b77fb-217">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="b77fb-218">Výrazy lambda: `fun` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="b77fb-218">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
