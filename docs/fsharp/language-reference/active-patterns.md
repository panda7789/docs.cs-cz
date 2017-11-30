---
title: "Aktivní vzorky (F#)"
description: "Další informace o použití aktivní vzorky k definování pojmenované oddíly, které rozdělit vstupní data v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 11a724ff-f9ff-4056-b5e0-87e9ed986f4a
ms.openlocfilehash: 845184e6150cf0b93393038ca3d39f0e6d898a2e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="active-patterns"></a><span data-ttu-id="3fca6-104">Aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="3fca6-104">Active Patterns</span></span>

<span data-ttu-id="3fca6-105">*Aktivní vzorky* umožňují definovat pojmenované oddíly, které rozdělit vstupních dat, takže můžete použít tyto názvy v vzor odpovídající výrazu stejným způsobem jako pro rozlišovaná sjednocení.</span><span class="sxs-lookup"><span data-stu-id="3fca6-105">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="3fca6-106">Aktivní vzorky můžete rozložit data způsobem přizpůsobené pro každý oddíl.</span><span class="sxs-lookup"><span data-stu-id="3fca6-106">You can use active patterns to decompose data in a customized manner for each partition.</span></span>


## <a name="syntax"></a><span data-ttu-id="3fca6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fca6-107">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="3fca6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fca6-108">Remarks</span></span>
<span data-ttu-id="3fca6-109">V předchozích syntaxi identifikátory jsou názvy pro oddíly vstupních dat, která je reprezentována *argumenty*, nebo jinými slovy, názvy pro podmnožiny sadu všechny hodnoty argumentů.</span><span class="sxs-lookup"><span data-stu-id="3fca6-109">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="3fca6-110">V definici – aktivní vzor může být až sedm oddíly.</span><span class="sxs-lookup"><span data-stu-id="3fca6-110">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="3fca6-111">*Výraz* popisuje, do kterého chcete rozložit data formuláře.</span><span class="sxs-lookup"><span data-stu-id="3fca6-111">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="3fca6-112">Definici – aktivní vzor můžete definovat pravidla pro zjišťování, který pojmenovaný oddíl hodnoty zadané jako argumenty patří.</span><span class="sxs-lookup"><span data-stu-id="3fca6-112">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="3fca6-113">(| A |) symboly jsou označovány jako *banánů klipů* a je volána funkce vytvořené tento typ umožňují vazby *active pro rozpoznávání*.</span><span class="sxs-lookup"><span data-stu-id="3fca6-113">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="3fca6-114">Jako příklad zvažte následující aktivní vzor s parametrem.</span><span class="sxs-lookup"><span data-stu-id="3fca6-114">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="3fca6-115">Aktivní vzor můžete použít ve tvaru odpovídající výrazu, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3fca6-115">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="3fca6-116">Výstup tohoto programu je následující:</span><span class="sxs-lookup"><span data-stu-id="3fca6-116">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="3fca6-117">Jiný aktivní vzorky slouží k rozložit datových typů v několika způsoby, například když stejné základní data mají různé možné reprezentace.</span><span class="sxs-lookup"><span data-stu-id="3fca6-117">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="3fca6-118">Například `Color` objekt může rozložit na reprezentaci RGB nebo reprezentaci HSB.</span><span class="sxs-lookup"><span data-stu-id="3fca6-118">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="3fca6-119">Výstup programu výše je následující:</span><span class="sxs-lookup"><span data-stu-id="3fca6-119">The output of the above program is as follows:</span></span>

```
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

<span data-ttu-id="3fca6-120">V kombinaci tyto dva způsoby použití aktivní vzorky umožňují oddílu a rozložit data na příslušný formulář a proveďte příslušné výpočtů na příslušná data ve formuláři nejvhodnější pro výpočet.</span><span class="sxs-lookup"><span data-stu-id="3fca6-120">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="3fca6-121">Výsledné výrazy odpovídající vzor povolit zápis v pohodlný způsob, který je velmi čitelný, výrazně zjednodušení potenciálně složité větvení a kód analýzy dat dat.</span><span class="sxs-lookup"><span data-stu-id="3fca6-121">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>


## <a name="partial-active-patterns"></a><span data-ttu-id="3fca6-122">Částečné aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="3fca6-122">Partial Active Patterns</span></span>
<span data-ttu-id="3fca6-123">V některých případech budete muset oddílu jenom část vstupní místa.</span><span class="sxs-lookup"><span data-stu-id="3fca6-123">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="3fca6-124">V takovém případě napíšete sady částečné vzorů, které odpovídat některých vstupních hodnot, ale nezdaří tak, aby odpovídaly ostatní vstupy.</span><span class="sxs-lookup"><span data-stu-id="3fca6-124">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="3fca6-125">Aktivní vzorky, které vždy nevytváří hodnotu, se nazývají *částečné aktivní vzorky*; mají návratovou hodnotu, která je typu možnost.</span><span class="sxs-lookup"><span data-stu-id="3fca6-125">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="3fca6-126">K definování částečné – aktivní vzor, se na konci seznam vzorů uvnitř klipů banánů použít zástupný znak (_).</span><span class="sxs-lookup"><span data-stu-id="3fca6-126">To define a partial active pattern, you use a wildcard character (_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="3fca6-127">Následující kód ukazuje použití částečné aktivní vzor.</span><span class="sxs-lookup"><span data-stu-id="3fca6-127">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="3fca6-128">Výstup v předchozím příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3fca6-128">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="3fca6-129">Při použití částečné aktivní vzorky, někdy jednotlivé možnosti může být nesouvislé, nebo vzájemně vylučují, ale jejich nemusí být.</span><span class="sxs-lookup"><span data-stu-id="3fca6-129">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="3fca6-130">V následujícím příkladu hranaté vzor a vzor datové krychle nejsou nesouvislý, protože jsou některé čísla čtverce a datové krychle, jako je například 64.</span><span class="sxs-lookup"><span data-stu-id="3fca6-130">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="3fca6-131">Následující program vytiskne všechny celá čísla až 1000000, které jsou čtverce a datové krychle.</span><span class="sxs-lookup"><span data-stu-id="3fca6-131">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="3fca6-132">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3fca6-132">The output is as follows:</span></span>

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="3fca6-133">Parametrizované aktivní vzorky</span><span class="sxs-lookup"><span data-stu-id="3fca6-133">Parameterized Active Patterns</span></span>
<span data-ttu-id="3fca6-134">Aktivní vzorky vždy provést alespoň jeden argument pro položku se shodoval, ale v takovém případě název se může trvat i, další argumenty *parametrizované – aktivní vzor* platí.</span><span class="sxs-lookup"><span data-stu-id="3fca6-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="3fca6-135">Další argumenty povolit obecné vzor nutné zadat.</span><span class="sxs-lookup"><span data-stu-id="3fca6-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="3fca6-136">Aktivní vzorky, které často Analýza řetězců pomocí regulárních výrazů příklady regulární výraz jako další parametr jako v následujícím kódu, který také používá částečné aktivní vzor `Integer` definované v předchozím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3fca6-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="3fca6-137">V tomto příkladu jsou uvedeny přizpůsobení obecné ParseRegex aktivní vzor řetězce, které použití regulárních výrazů pro různých formátů data.</span><span class="sxs-lookup"><span data-stu-id="3fca6-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="3fca6-138">Aktivní vzor celé číslo se používá k převod odpovídající řetězců na celá čísla, které lze předat do konstruktoru data a času.</span><span class="sxs-lookup"><span data-stu-id="3fca6-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="3fca6-139">Výstup předchozí kód je následující:</span><span class="sxs-lookup"><span data-stu-id="3fca6-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="3fca6-140">Aktivní vzorky nejsou omezeny pouze na vzor odpovídající výrazy, můžete také použít na umožňují vazby.</span><span class="sxs-lookup"><span data-stu-id="3fca6-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="3fca6-141">Výstup předchozí kód je následující:</span><span class="sxs-lookup"><span data-stu-id="3fca6-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="3fca6-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fca6-142">See Also</span></span>
[<span data-ttu-id="3fca6-143">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="3fca6-143">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="3fca6-144">Výrazy shody</span><span class="sxs-lookup"><span data-stu-id="3fca6-144">Match Expressions</span></span>](match-expressions.md)

