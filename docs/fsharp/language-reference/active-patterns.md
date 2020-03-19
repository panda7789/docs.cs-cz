---
title: Aktivní vzorky
description: Zjistěte, jak pomocí aktivních vzorů definovat pojmenované oddíly, které rozdělují vstupní data v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187062"
---
# <a name="active-patterns"></a><span data-ttu-id="ceb21-103">Aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="ceb21-103">Active Patterns</span></span>

<span data-ttu-id="ceb21-104">*Aktivní vzorky* umožňují definovat pojmenované oddíly, které rozdělují vstupní data, takže tyto názvy můžete použít ve výrazu porovnávání vzorů stejně jako pro discriminated sjednocení.</span><span class="sxs-lookup"><span data-stu-id="ceb21-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="ceb21-105">Aktivní vzorky můžete použít k rozkladu dat přizpůsobeným způsobem pro každý oddíl.</span><span class="sxs-lookup"><span data-stu-id="ceb21-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="ceb21-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ceb21-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="ceb21-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ceb21-107">Remarks</span></span>

<span data-ttu-id="ceb21-108">V předchozí syntaxi jsou identifikátory názvy oddílů vstupních dat, které jsou reprezentovány argumenty , nebo jinými slovy *názvy*podmnožiny sady všech hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="ceb21-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="ceb21-109">V definici aktivního vzoru může být až sedm oddílů.</span><span class="sxs-lookup"><span data-stu-id="ceb21-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="ceb21-110">*Výraz* popisuje formulář, do kterého chcete rozložit data.</span><span class="sxs-lookup"><span data-stu-id="ceb21-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="ceb21-111">Pomocí definice aktivního vzoru můžete definovat pravidla pro určení, ke kterému z pojmenovaných oddílů patří hodnoty uvedené jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="ceb21-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="ceb21-112">Symboly (| a |) se označují jako *banánové klipy* a funkce vytvořená tímto typem vazby let se nazývá *aktivní nástroj pro rozpoznávání*.</span><span class="sxs-lookup"><span data-stu-id="ceb21-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="ceb21-113">Jako příklad zvažte následující aktivní vzorek s argumentem.</span><span class="sxs-lookup"><span data-stu-id="ceb21-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="ceb21-114">Aktivní vzorek můžete použít ve výrazu odpovídajícího vzorku, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ceb21-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="ceb21-115">Výstup tohoto programu je následující:</span><span class="sxs-lookup"><span data-stu-id="ceb21-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="ceb21-116">Dalším použitím aktivních vzorů je rozkládat datové typy několika způsoby, například když mají stejná podkladová data různé možné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="ceb21-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="ceb21-117">`Color` Objekt může být například rozložen do reprezentace RGB nebo reprezentace HSB.</span><span class="sxs-lookup"><span data-stu-id="ceb21-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="ceb21-118">Výstup výše uvedeného programu je následující:</span><span class="sxs-lookup"><span data-stu-id="ceb21-118">The output of the above program is as follows:</span></span>

```console
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="ceb21-119">V kombinaci tyto dva způsoby použití aktivní vzorky umožňují rozdělit a rozložit data do pouze příslušné formě a provést příslušné výpočty na příslušná data ve formuláři nejvhodnější pro výpočtu.</span><span class="sxs-lookup"><span data-stu-id="ceb21-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="ceb21-120">Výsledné výrazy porovnávání vzorů umožňují zapisovat data pohodlným způsobem, který je velmi čitelný, což značně zjednodušuje potenciálně složitý kód větvení a analýzy dat.</span><span class="sxs-lookup"><span data-stu-id="ceb21-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="ceb21-121">Částečné aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="ceb21-121">Partial Active Patterns</span></span>

<span data-ttu-id="ceb21-122">Někdy je třeba rozdělit pouze část vstupního prostoru.</span><span class="sxs-lookup"><span data-stu-id="ceb21-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="ceb21-123">V takovém případě napíšete sadu částečných vzorů, z nichž každý odpovídá některé vstupy, ale nepodaří odpovídat jiné vstupy.</span><span class="sxs-lookup"><span data-stu-id="ceb21-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="ceb21-124">Aktivní vzorky, které ne vždy vytvářejí hodnotu, se nazývají *částečné aktivní vzorky*; mají vrácenou hodnotu, která je typ možnosti.</span><span class="sxs-lookup"><span data-stu-id="ceb21-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="ceb21-125">Chcete-li definovat částečný aktivní vzorek, použijte\_zástupný znak ( ) na konci seznamu vzorků uvnitř banánových klipů.</span><span class="sxs-lookup"><span data-stu-id="ceb21-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="ceb21-126">Následující kód ilustruje použití částečné aktivní vzor.</span><span class="sxs-lookup"><span data-stu-id="ceb21-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="ceb21-127">Výstup z předchozího příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="ceb21-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="ceb21-128">Při použití částečné aktivní vzory, někdy jednotlivé volby mohou být nesouvislé nebo vzájemně se vylučující, ale nemusí být.</span><span class="sxs-lookup"><span data-stu-id="ceb21-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="ceb21-129">V následujícím příkladu nejsou čtvercové a datová krychle vzorku nesouvislé, protože některá čísla jsou čtverce i krychle, například 64.</span><span class="sxs-lookup"><span data-stu-id="ceb21-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="ceb21-130">Následující program používá a vzor kombinovat čtvercové a datové krychle vzorky.</span><span class="sxs-lookup"><span data-stu-id="ceb21-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="ceb21-131">Vytiskne všechna celá čísla až do 1000, které jsou jak čtverce, tak kostky, stejně jako ty, které jsou pouze kostky.</span><span class="sxs-lookup"><span data-stu-id="ceb21-131">It prints out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="ceb21-132">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="ceb21-132">The output is as follows:</span></span>

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="ceb21-133">Parametrizované aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="ceb21-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="ceb21-134">Aktivní vzorky vždy trvat alespoň jeden argument pro položku, která odpovídá, ale mohou mít další argumenty také, v takovém případě název *parametrizovaný aktivní vzor* platí.</span><span class="sxs-lookup"><span data-stu-id="ceb21-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="ceb21-135">Další argumenty umožňují obecný vzor, který má být specializovaný.</span><span class="sxs-lookup"><span data-stu-id="ceb21-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="ceb21-136">Například aktivní vzorky, které používají regulární výrazy k analýzě řetězců, často zahrnují regulární výraz jako `Integer` další parametr, jako v následujícím kódu, který také používá částečný aktivní vzor definovaný v předchozím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ceb21-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="ceb21-137">V tomto příkladu jsou k přizpůsobení obecného aktivního vzoru ParseRegex uvedeny řetězce, které používají regulární výrazy pro různé formáty kalendářních dat.</span><span class="sxs-lookup"><span data-stu-id="ceb21-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="ceb21-138">Aktivní vzorek Integer se používá k převodu odpovídajícířetězce na celá čísla, které mohou být předány DateTime konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ceb21-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="ceb21-139">Výstup předchozího kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="ceb21-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="ceb21-140">Aktivní vzorky nejsou omezeny pouze na výrazy odpovídající vzorek, můžete je také použít na let-vazby.</span><span class="sxs-lookup"><span data-stu-id="ceb21-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="ceb21-141">Výstup předchozího kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="ceb21-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="ceb21-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="ceb21-142">See also</span></span>

- [<span data-ttu-id="ceb21-143">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="ceb21-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ceb21-144">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="ceb21-144">Match Expressions</span></span>](match-expressions.md)
