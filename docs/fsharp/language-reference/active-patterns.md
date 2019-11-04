---
title: Aktivní vzorky
description: Naučte se používat aktivní vzory k definování pojmenovaných oddílů, které rozdělují vstupní F# data v programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: f5ed4a8600cba10d23d01628aba6ca07e543c586
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425097"
---
# <a name="active-patterns"></a><span data-ttu-id="bb597-103">Aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="bb597-103">Active Patterns</span></span>

<span data-ttu-id="bb597-104">*Aktivní vzory* umožňují definovat pojmenované oddíly, které rozdělují vstupní data, abyste je mohli použít ve výrazu porovnávání vzorů stejně jako u rozlišeného sjednocení.</span><span class="sxs-lookup"><span data-stu-id="bb597-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="bb597-105">Můžete použít aktivní vzory a rozložit data vlastním způsobem pro každý oddíl.</span><span class="sxs-lookup"><span data-stu-id="bb597-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb597-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb597-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="bb597-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb597-107">Remarks</span></span>

<span data-ttu-id="bb597-108">V předchozí syntaxi jsou identifikátory názvy pro oddíly vstupních dat, která jsou reprezentována *argumenty*, nebo jinými slovy názvy pro podmnožiny sady všech hodnot argumentů.</span><span class="sxs-lookup"><span data-stu-id="bb597-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="bb597-109">V aktivní definici vzoru může být až sedm oddílů.</span><span class="sxs-lookup"><span data-stu-id="bb597-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="bb597-110">*Výraz* popisuje formulář, do kterého se mají data rozložit.</span><span class="sxs-lookup"><span data-stu-id="bb597-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="bb597-111">Pomocí aktivní definice vzoru můžete definovat pravidla pro určení, které z uvedených oddílů mají hodnoty zadané jako argumenty patřit do.</span><span class="sxs-lookup"><span data-stu-id="bb597-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="bb597-112">Symboly (| a |) jsou označovány jako *klipy banánů* a funkce vytvořená tímto typem dovolit, aby vazba byla volána jako *aktivní nástroj pro rozpoznávání*.</span><span class="sxs-lookup"><span data-stu-id="bb597-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="bb597-113">Jako příklad zvažte následující aktivní vzor s argumentem.</span><span class="sxs-lookup"><span data-stu-id="bb597-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="bb597-114">Můžete použít aktivní vzor ve výrazu pro porovnávání vzorů, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bb597-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="bb597-115">Výstup tohoto programu je následující:</span><span class="sxs-lookup"><span data-stu-id="bb597-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="bb597-116">Další možností použití aktivních vzorů je rozložit datové typy různými způsoby, například když mají stejná základní data různé možné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="bb597-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="bb597-117">Například objekt `Color` mohl být rozdělen do reprezentace v modelu RGB nebo v HSB.</span><span class="sxs-lookup"><span data-stu-id="bb597-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="bb597-118">Výstup výše uvedeného programu je následující:</span><span class="sxs-lookup"><span data-stu-id="bb597-118">The output of the above program is as follows:</span></span>

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

<span data-ttu-id="bb597-119">V kombinaci těchto dvou způsobů použití aktivních vzorů můžete rozdělit data do oddílů a rozložit je pouze do příslušné formy a provádět odpovídající výpočty pro příslušná data ve formuláři nejužitečnější pro výpočet.</span><span class="sxs-lookup"><span data-stu-id="bb597-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="bb597-120">Výsledné výrazy pro porovnávání vzorů umožňují psát data pohodlným způsobem, který je velmi čitelný a významně zjednodušuje potenciálně složitý kód pro větvení a analýzu dat.</span><span class="sxs-lookup"><span data-stu-id="bb597-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="bb597-121">Částečné aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="bb597-121">Partial Active Patterns</span></span>

<span data-ttu-id="bb597-122">V některých případech je potřeba rozdělit jenom část vstupního prostoru.</span><span class="sxs-lookup"><span data-stu-id="bb597-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="bb597-123">V takovém případě napíšete sadu částečných vzorů, které odpovídají určitým vstupům, ale neodpovídají jiným vstupům.</span><span class="sxs-lookup"><span data-stu-id="bb597-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="bb597-124">Aktivní vzory, které nevytváří vždy hodnotu, se nazývají *částečné aktivní vzory*; mají návratovou hodnotu, která je typu možnosti.</span><span class="sxs-lookup"><span data-stu-id="bb597-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="bb597-125">Chcete-li definovat částečný aktivní vzor, použijte zástupný znak (\_) na konci seznamu vzorů uvnitř klipů banánů.</span><span class="sxs-lookup"><span data-stu-id="bb597-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="bb597-126">Následující kód ilustruje použití částečného aktivního vzoru.</span><span class="sxs-lookup"><span data-stu-id="bb597-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="bb597-127">Výstup předchozího příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="bb597-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="bb597-128">Při použití částečných aktivních vzorů mohou být jednotlivé volby odděleny nebo vzájemně exkluzivní, ale nemusí být.</span><span class="sxs-lookup"><span data-stu-id="bb597-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="bb597-129">V následujícím příkladu nejsou odděleny vzorce čtverce a vzorová krychle, protože některá čísla jsou čtverce i datové krychle, například 64.</span><span class="sxs-lookup"><span data-stu-id="bb597-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="bb597-130">Následující program používá vzor a ke kombinování čtverců a vzorů krychle.</span><span class="sxs-lookup"><span data-stu-id="bb597-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="bb597-131">Vytiskněte všechna celá čísla až 1000, která jsou čtverce i datové krychle, i ty, které jsou jenom datové krychle.</span><span class="sxs-lookup"><span data-stu-id="bb597-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="bb597-132">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="bb597-132">The output is as follows:</span></span>

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

## <a name="parameterized-active-patterns"></a><span data-ttu-id="bb597-133">Parametrizované aktivní vzory</span><span class="sxs-lookup"><span data-stu-id="bb597-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="bb597-134">Aktivní vzory vždycky přebírají aspoň jeden argument pro odpovídající položku, ale můžou také použít další argumenty. v takovém případě se použije název *parametrizovaný aktivní vzor* .</span><span class="sxs-lookup"><span data-stu-id="bb597-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="bb597-135">Další argumenty umožňují specializované obecné vzory.</span><span class="sxs-lookup"><span data-stu-id="bb597-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="bb597-136">Například aktivní vzory, které používají regulární výrazy k analýze řetězců často obsahují regulární výraz jako další parametr, jak je uvedeno v následujícím kódu, který používá také částečný aktivní vzor `Integer` definován v předchozím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="bb597-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="bb597-137">V tomto příkladu jsou přidány řetězce, které používají regulární výrazy pro různé formáty data pro přizpůsobení obecného ParseRegex aktivního vzoru.</span><span class="sxs-lookup"><span data-stu-id="bb597-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="bb597-138">Celočíselný aktivní vzor slouží k převodu odpovídajících řetězců na celá čísla, která lze předat konstruktoru DateTime.</span><span class="sxs-lookup"><span data-stu-id="bb597-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="bb597-139">Výstup předchozího kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="bb597-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="bb597-140">Aktivní vzory nejsou omezené jenom na výrazy porovnávání vzorů, můžete je také použít na vazby let.</span><span class="sxs-lookup"><span data-stu-id="bb597-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="bb597-141">Výstup předchozího kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="bb597-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="bb597-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb597-142">See also</span></span>

- [<span data-ttu-id="bb597-143">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="bb597-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="bb597-144">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="bb597-144">Match Expressions</span></span>](match-expressions.md)
