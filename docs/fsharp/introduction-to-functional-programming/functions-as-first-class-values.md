---
title: Funkce jako hodnoty první třídy (F#)
description: 'Zjistěte, jak se funkce převedou do stavu první kategorie v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 45b65ab2454a592d38c80fd367e7243635614727
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44048231"
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="6129e-103">Funkce jako hodnoty první třídy</span><span class="sxs-lookup"><span data-stu-id="6129e-103">Functions as First-Class Values</span></span>

<span data-ttu-id="6129e-104">Charakteristickým znakem funkčních programovacích jazyků je povýšení funkcí do stavu první kategorie.</span><span class="sxs-lookup"><span data-stu-id="6129e-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="6129e-105">Měli byste být schopni s funkcí provádět to, co můžete provádět s hodnotami ostatních předdefinovaných typů, a rovněž byste měli být schopni tak činit se srovnatelnou mírou úsilí.</span><span class="sxs-lookup"><span data-stu-id="6129e-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="6129e-106">Typická opatření stavu první kategorie zahrnují:</span><span class="sxs-lookup"><span data-stu-id="6129e-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="6129e-107">Lze vázat na identifikátory funkce?</span><span class="sxs-lookup"><span data-stu-id="6129e-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="6129e-108">To znamená můžete je přiřadit názvy?</span><span class="sxs-lookup"><span data-stu-id="6129e-108">That is, can you give them names?</span></span>

- <span data-ttu-id="6129e-109">Můžete ukládat funkce v datové struktury, jako například v seznamu?</span><span class="sxs-lookup"><span data-stu-id="6129e-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="6129e-110">Můžete předat funkci jako argument ve volání funkce?</span><span class="sxs-lookup"><span data-stu-id="6129e-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="6129e-111">Může vrátit funkce z volání funkce?</span><span class="sxs-lookup"><span data-stu-id="6129e-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="6129e-112">Poslední dvě opatření definují to, co jsou označovány jako *operace vyššího řádu* nebo *funkce vyššího řádu*.</span><span class="sxs-lookup"><span data-stu-id="6129e-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="6129e-113">Funkce vyššího řádu přijímají funkce jako argumenty a vrací funkce jako hodnotu volání funkce.</span><span class="sxs-lookup"><span data-stu-id="6129e-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="6129e-114">Tyto operace podporují stěžejní části funkčního programování, jako jsou funkce mapování a skládání funkcí.</span><span class="sxs-lookup"><span data-stu-id="6129e-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="6129e-115">Přiřazení názvu hodnotě</span><span class="sxs-lookup"><span data-stu-id="6129e-115">Give the Value a Name</span></span>

<span data-ttu-id="6129e-116">Pokud je funkce hodnotou první kategorie, je třeba ji pojmenovat, stejně jako lze pojmenovat celá čísla, řetězce a další předdefinované typy.</span><span class="sxs-lookup"><span data-stu-id="6129e-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="6129e-117">Na to je podle literatury o funkčním programování odkazováno jako na vázání identifikátoru na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6129e-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="6129e-118">Jazyk F # používá [ `let` vazby](../language-reference/functions/let-bindings.md) pro vázání názvů a hodnot: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="6129e-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="6129e-119">Následující kód ukazuje dva příklady.</span><span class="sxs-lookup"><span data-stu-id="6129e-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="6129e-120">Funkci lze pojmenovat stejně snadno.</span><span class="sxs-lookup"><span data-stu-id="6129e-120">You can name a function just as easily.</span></span> <span data-ttu-id="6129e-121">Následující příklad definuje funkci nazvanou `squareIt` svázáním identifikátoru `squareIt` k [výraz lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="6129e-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="6129e-122">Funkce `squareIt` má jeden parametr `n` a vrací druhou mocninu tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="6129e-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="6129e-123">Jazyk F# poskytuje pro dosažení stejného výsledku s kratším zápisem následující stručnější syntaxi.</span><span class="sxs-lookup"><span data-stu-id="6129e-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="6129e-124">Následující příklady používají pro zvýraznění podobností mezi deklaracemi funkcí a deklaracemi dalších typů hodnot převážně první styl, `let <function-name> = <lambda-expression>`.</span><span class="sxs-lookup"><span data-stu-id="6129e-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="6129e-125">Všechny pojmenované funkce lze ale také zapsat pomocí stručnější syntaxe.</span><span class="sxs-lookup"><span data-stu-id="6129e-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="6129e-126">Některé příklady jsou zapsány oběma způsoby.</span><span class="sxs-lookup"><span data-stu-id="6129e-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="6129e-127">Uložení hodnoty do datové struktury</span><span class="sxs-lookup"><span data-stu-id="6129e-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="6129e-128">Hodnota první kategorie může být uložena v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="6129e-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="6129e-129">Následující kód ukazuje příklady, které ukládají hodnoty v seznamech a řazených kolekcích členů.</span><span class="sxs-lookup"><span data-stu-id="6129e-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="6129e-130">Za účelem ověření, že název funkce uložený v řazené kolekci členů povede ve skutečnosti k vyhodnocení funkce, používá následující příklad operátory `fst` a `snd` pro získání prvního a druhého prvku z řazené kolekce členů `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="6129e-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="6129e-131">První prvek v řazené kolekci členů je `squareIt` a druhý prvek je `num`.</span><span class="sxs-lookup"><span data-stu-id="6129e-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="6129e-132">Identifikátor `num` je v předchozím příkladu svázán s celým číslem 10, platným argumentem pro funkci `squareIt`.</span><span class="sxs-lookup"><span data-stu-id="6129e-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="6129e-133">Druhý výraz použije první prvek v řazené kolekci členů na druhý prvek řazené kolekce členů: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="6129e-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="6129e-134">Podobně jako lze identifikátor `num` zaměnit s celým číslem 10, lze zaměnit identifikátor `squareIt` s výrazem lambda `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="6129e-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="6129e-135">Předání hodnoty jako argumentu</span><span class="sxs-lookup"><span data-stu-id="6129e-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="6129e-136">Pokud hodnota patří k hodnotám stavu první kategorie jazyka, lze ji předat jako argument funkce.</span><span class="sxs-lookup"><span data-stu-id="6129e-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="6129e-137">Je například běžné předávat jako argumenty celá čísla a řetězce.</span><span class="sxs-lookup"><span data-stu-id="6129e-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="6129e-138">Následující kód ukazuje předání celých čísel a řetězců jako argumentů v jazyce F#.</span><span class="sxs-lookup"><span data-stu-id="6129e-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="6129e-139">Pokud jsou funkce ve stavu hodnoty první kategorie, musíte být schopni je stejným způsobem předat jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="6129e-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="6129e-140">Zapamatujte si, že se jedná o první charakteristiku funkcí vyššího řádu.</span><span class="sxs-lookup"><span data-stu-id="6129e-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="6129e-141">V následujícím příkladu má funkce `applyIt` dva parametry, `op` a `arg`.</span><span class="sxs-lookup"><span data-stu-id="6129e-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="6129e-142">Pokud do parametru `op` předáte funkci, která má jeden parametr, a odpovídající argument funkce předáte do parametru `arg`, funkce vrátí výsledek použití parametru `op` do parametru `arg`.</span><span class="sxs-lookup"><span data-stu-id="6129e-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="6129e-143">V následujícím příkladu jsou oba argumenty – argument funkce a argument celého čísla – odeslány stejným způsobem, a to použitím jejich názvů.</span><span class="sxs-lookup"><span data-stu-id="6129e-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="6129e-144">Možnost odeslat funkci jako argument do jiné funkce je základem společných abstrakcí ve funkčních programovacích jazycích, jako jsou například operace mapování nebo filtrování.</span><span class="sxs-lookup"><span data-stu-id="6129e-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="6129e-145">Například operace mapování je funkce vyššího řádu, která zachytává výpočet sdílený funkcemi, jež prochází seznamem, u každého prvku provedou nějakou operaci a poté vrátí seznam výsledků.</span><span class="sxs-lookup"><span data-stu-id="6129e-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="6129e-146">Může být například třeba zvýšit každý prvek v seznamu celých čísel o jedna, každý prvek umocnit na druhou nebo převést každý prvek seznamu řetězců na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6129e-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="6129e-147">Rekurzivní proces, který prochází seznam a vytváří seznam výsledků k vrácení, je část výpočtu náchylná k chybám.</span><span class="sxs-lookup"><span data-stu-id="6129e-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="6129e-148">Tato část je zachycena ve funkci mapování.</span><span class="sxs-lookup"><span data-stu-id="6129e-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="6129e-149">Jediné, co je třeba napsat pro konkrétní aplikaci, je funkce, kterou chcete použít na každý jednotlivý prvek seznamu (sčítání, umocňování, změna velikosti písmen).</span><span class="sxs-lookup"><span data-stu-id="6129e-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="6129e-150">Tato funkce je předána jako argument funkci mapování, stejně jako je v předchozím příkladu prvek `squareIt` předán do funkce `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="6129e-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="6129e-151">Jazyk F # poskytuje metody mapování pro většinu typů kolekcí, včetně [uvádí](../language-reference/lists.md), [pole](../language-reference/arrays.md), a [pořadí](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="6129e-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="6129e-152">Následující příklady používají seznamy.</span><span class="sxs-lookup"><span data-stu-id="6129e-152">The following examples use lists.</span></span> <span data-ttu-id="6129e-153">Syntaxe je `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="6129e-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="6129e-154">Další informace najdete v tématu [uvádí](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="6129e-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="6129e-155">Vrácení hodnoty z volání funkce</span><span class="sxs-lookup"><span data-stu-id="6129e-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="6129e-156">Pokud je funkce v jazyce ve stavu hodnoty první kategorie, musí být možné ji vrátit jako hodnotu volání funkce, stejně tak jako jsou vraceny další typy, jako například celá čísla a řetězce.</span><span class="sxs-lookup"><span data-stu-id="6129e-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="6129e-157">Následující volání funkce vrací celá čísla a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="6129e-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="6129e-158">Následující volání funkce vrací řetězec.</span><span class="sxs-lookup"><span data-stu-id="6129e-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="6129e-159">Následující volání funkce, deklarované na jednom řádku, vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6129e-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="6129e-160">Zobrazená hodnota je `True`.</span><span class="sxs-lookup"><span data-stu-id="6129e-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="6129e-161">Schopnost vracet funkci jako hodnotu volání funkce je druhým charakteristickým znakem funkcí vyššího řádu.</span><span class="sxs-lookup"><span data-stu-id="6129e-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="6129e-162">V následujícím příkladu je `checkFor` definováno jako funkce, která převezme jeden argument, `item`, a jako hodnotu vrátí novou funkci.</span><span class="sxs-lookup"><span data-stu-id="6129e-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="6129e-163">Vrácená funkce převezme seznam jako argument `lst` a v argumentu `item` vyhledá prvek `lst`.</span><span class="sxs-lookup"><span data-stu-id="6129e-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="6129e-164">Pokud je prvek `item` nalezen, funkce vrací hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="6129e-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="6129e-165">Pokud není prvek `item` nalezen, funkce vrací hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="6129e-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="6129e-166">Stejně jako v předchozí části, následující kód používá poskytnutou funkci seznamu [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)pro prohledání seznamu.</span><span class="sxs-lookup"><span data-stu-id="6129e-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="6129e-167">Následující kód používá pro vytvoření nové funkce funkci `checkFor`, která přijímá jeden argument – seznam – a vyhledá v něm číslo 7.</span><span class="sxs-lookup"><span data-stu-id="6129e-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="6129e-168">Následující příklad používá pro deklaraci funkce `compose`, která vrací složení dvou argumentů funkce, stav první kategorie funkcí jazyka F#.</span><span class="sxs-lookup"><span data-stu-id="6129e-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

>[!NOTE]
<span data-ttu-id="6129e-169">Ještě kratší verzi naleznete v následující části „Curryfikované funkce“.</span><span class="sxs-lookup"><span data-stu-id="6129e-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="6129e-170">Následující kód předá funkci `compose` dvě funkce jako argumenty, obě přijímající jediný argument stejného typu.</span><span class="sxs-lookup"><span data-stu-id="6129e-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="6129e-171">Vrácená hodnota je nová funkce, která je složením obou argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="6129e-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

>[!NOTE]
<span data-ttu-id="6129e-172">Jazyk F# obsahuje dva operátory skládající funkce, `<<` a `>>`.</span><span class="sxs-lookup"><span data-stu-id="6129e-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="6129e-173">Například `let squareAndDouble2 = doubleIt << squareIt` je ekvivalentní zápisu `let squareAndDouble = compose doubleIt squareIt` z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="6129e-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="6129e-174">Následující příklad vrácení funkce jako hodnoty volání funkce vytvoří jednoduchou hádací hru.</span><span class="sxs-lookup"><span data-stu-id="6129e-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="6129e-175">Pro tvorbu hry je třeba zavolat funkci `makeGame` s hodnotou, kterou má někdo uhodnout, předanou do argumentu `target`.</span><span class="sxs-lookup"><span data-stu-id="6129e-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="6129e-176">Vrácená hodnota z funkce `makeGame` je funkce, která přijímá jeden argument (odhad) a hlásí, zda je odhad správný.</span><span class="sxs-lookup"><span data-stu-id="6129e-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="6129e-177">Následující kód volá funkci `makeGame` předávající hodnotu `7` do argumentu `target`.</span><span class="sxs-lookup"><span data-stu-id="6129e-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="6129e-178">Identifikátor `playGame` je vázán na vrácený výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="6129e-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="6129e-179">Proto funkce `playGame` přijímá jako svůj argument hodnotu funkce `guess`.</span><span class="sxs-lookup"><span data-stu-id="6129e-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="6129e-180">Curryfikované funkce</span><span class="sxs-lookup"><span data-stu-id="6129e-180">Curried Functions</span></span>

<span data-ttu-id="6129e-181">Mnoho příkladů v předchozí části lze zapsat s využitím implicitního *curryfikace* v deklaracích funkcí F #.</span><span class="sxs-lookup"><span data-stu-id="6129e-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="6129e-182">Curryfikace je proces, jenž transformuje funkci, která má více než jeden parametr do řady vložených funkcí, z nichž každá má jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="6129e-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="6129e-183">V jazyce F# jsou funkce, které mají více než jeden parametr, ze své podstaty curryfikovány.</span><span class="sxs-lookup"><span data-stu-id="6129e-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="6129e-184">Například funkci `compose` z předchozí části lze zapsat pomocí následujícího stručného stylu se třemi parametry.</span><span class="sxs-lookup"><span data-stu-id="6129e-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="6129e-185">Výsledkem je ale funkce jednoho parametru, jež vrací funkci jednoho parametru, která zase vrací jinou funkci jednoho parametru tak, jak je vidět ve funkci `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="6129e-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="6129e-186">K této funkci lze přistupovat několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="6129e-186">You can access this function in several ways.</span></span> <span data-ttu-id="6129e-187">Každý z následujících příkladů vrátí a zobrazí číslo 18.</span><span class="sxs-lookup"><span data-stu-id="6129e-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="6129e-188">Funkci `compose4` lze v jakémkoli příkladě nahradit funkcí `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="6129e-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="6129e-189">Pro ověření, zda funkce stále pracuje stejně jako dříve, lze opětovně vyzkoušet původní testovací případy.</span><span class="sxs-lookup"><span data-stu-id="6129e-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

>[!NOTE]
<span data-ttu-id="6129e-190">Curryfikaci lze omezit uzavřením parametrů do řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="6129e-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="6129e-191">Další informace najdete v části "Vzory parametrů" v [parametry a argumenty](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="6129e-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="6129e-192">Následující příklad používá implicitní curryfikaci pro zápis kratší verze funkce `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="6129e-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="6129e-193">Podrobné informace o tom, jak funkce `makeGame` konstruuje a vrací funkci `game`, jsou v tomto formátu méně explicitní, ale pomocí původních testovacích případů lze ověřit, že je výsledek stejný.</span><span class="sxs-lookup"><span data-stu-id="6129e-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="6129e-194">Další informace o procesu curryfikace naleznete v části "Částečné použití argumentů" v [funkce](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="6129e-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="6129e-195">Definice identifikátoru a funkce jsou zaměnitelné</span><span class="sxs-lookup"><span data-stu-id="6129e-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="6129e-196">Název proměnné `num` je v předchozích příkladech vyhodnocen jako celé číslo 10 a není žádným překvapením, že pokud je proměnná `num` platná, číslo 10 je také platné.</span><span class="sxs-lookup"><span data-stu-id="6129e-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="6129e-197">Totéž platí i pro identifikátory funkcí a jejich hodnoty: kdekoli lze použít název funkce, lze také použít výraz lambda, se kterým je funkce svázána.</span><span class="sxs-lookup"><span data-stu-id="6129e-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="6129e-198">Následující příklad definuje funkci `Boolean` s názvem `isNegative`, poté použije název funkce a následně místo něj použije její definici.</span><span class="sxs-lookup"><span data-stu-id="6129e-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="6129e-199">Všechny tři následující příklady vracejí hodnotu `False` a zobrazují ji.</span><span class="sxs-lookup"><span data-stu-id="6129e-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="6129e-200">Pro provedení dalšího kroku nahraďte hodnotu, ke které je svázán identifikátor `applyIt`, hodnotou `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="6129e-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="6129e-201">Funkce jsou hodnoty první třídy v F\#</span><span class="sxs-lookup"><span data-stu-id="6129e-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="6129e-202">Příklady v předchozích částech ukazují, že funkce jazyka F# splňují kritéria pro hodnoty první kategorie:</span><span class="sxs-lookup"><span data-stu-id="6129e-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="6129e-203">Identifikátor lze svázat s definicí funkce.</span><span class="sxs-lookup"><span data-stu-id="6129e-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="6129e-204">Funkci lze uložit v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="6129e-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="6129e-205">Funkci lze předat jako argument.</span><span class="sxs-lookup"><span data-stu-id="6129e-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="6129e-206">Funkci lze vrátit jako hodnotu volání funkce.</span><span class="sxs-lookup"><span data-stu-id="6129e-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="6129e-207">Další informace o jazyce F #, najdete v článku [referenční dokumentace jazyka F #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="6129e-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="6129e-208">Příklad</span><span class="sxs-lookup"><span data-stu-id="6129e-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="6129e-209">Popis</span><span class="sxs-lookup"><span data-stu-id="6129e-209">Description</span></span>

<span data-ttu-id="6129e-210">Následující kód obsahuje všechny příklady v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="6129e-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="6129e-211">Kód</span><span class="sxs-lookup"><span data-stu-id="6129e-211">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="6129e-212">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6129e-212">See also</span></span>

- [<span data-ttu-id="6129e-213">Seznamy</span><span class="sxs-lookup"><span data-stu-id="6129e-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="6129e-214">Řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="6129e-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="6129e-215">Funkce</span><span class="sxs-lookup"><span data-stu-id="6129e-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="6129e-216">`let` Vazby</span><span class="sxs-lookup"><span data-stu-id="6129e-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="6129e-217">Výrazy lambda: `fun` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="6129e-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
