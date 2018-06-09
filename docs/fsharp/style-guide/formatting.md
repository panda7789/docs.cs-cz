---
title: 'F # – kód formátování pokyny'
description: 'Přečtěte si pokyny pro formátování kódu F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 6c8e4059fd4bf1e7450118a6df02609217c4f4db
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231502"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="03b39-103">F # – kód formátování pokyny</span><span class="sxs-lookup"><span data-stu-id="03b39-103">F# code formatting guidelines</span></span>

<span data-ttu-id="03b39-104">Tento článek obsahuje pokyny k formátování kódu tak, aby váš kód F # je:</span><span class="sxs-lookup"><span data-stu-id="03b39-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="03b39-105">Obecně zobrazit jako zlepšení čitelnosti</span><span class="sxs-lookup"><span data-stu-id="03b39-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="03b39-106">V souladu s konvence používaný službou formátování nástroje v sadě Visual Studio a dalšími editory</span><span class="sxs-lookup"><span data-stu-id="03b39-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="03b39-107">Podobně jako ostatní kód online</span><span class="sxs-lookup"><span data-stu-id="03b39-107">Similar to other code online</span></span>

<span data-ttu-id="03b39-108">Tyto pokyny jsou založené na [komplexní pokyny k formátování konvence F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) podle [Anh hnoje Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="03b39-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="03b39-109">Obecná pravidla pro odsazení</span><span class="sxs-lookup"><span data-stu-id="03b39-109">General rules for indentation</span></span>

<span data-ttu-id="03b39-110">F # ve výchozím nastavení používá významný mezerový znak.</span><span class="sxs-lookup"><span data-stu-id="03b39-110">F# uses significant whitespace by default.</span></span> <span data-ttu-id="03b39-111">Následující pokyny jsou určeny k obsahují pokyny, jak přehlednější některé běžné problémy, které to použít.</span><span class="sxs-lookup"><span data-stu-id="03b39-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="03b39-112">Použití prostorů</span><span class="sxs-lookup"><span data-stu-id="03b39-112">Using spaces</span></span>

<span data-ttu-id="03b39-113">Pokud je požadována odsazení, je nutné použít mezery, tabulátory není.</span><span class="sxs-lookup"><span data-stu-id="03b39-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="03b39-114">Je vyžadován alespoň jeden prostor.</span><span class="sxs-lookup"><span data-stu-id="03b39-114">At least one space is required.</span></span> <span data-ttu-id="03b39-115">Vaše organizace můžete vytvořit kódování standardy k určení počtu prostory pro odsazení; dva, tři nebo čtyři prostory odsazení na každé úrovni, kde dochází k odsazení je typické.</span><span class="sxs-lookup"><span data-stu-id="03b39-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="03b39-116">**Doporučujeme 4 mezer na odsazení.**</span><span class="sxs-lookup"><span data-stu-id="03b39-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="03b39-117">Ale nutné dodat, odsazení programů je subjektivní věci.</span><span class="sxs-lookup"><span data-stu-id="03b39-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="03b39-118">Rozdíly jsou OK, ale je první pravidlo, postupujte podle *konzistence odsazení*.</span><span class="sxs-lookup"><span data-stu-id="03b39-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="03b39-119">Zvolte obecně přijatelné styl odsazení a systematičtěji ji použít v celé vaší základu kódu.</span><span class="sxs-lookup"><span data-stu-id="03b39-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-blank-lines"></a><span data-ttu-id="03b39-120">Formátování prázdné řádky</span><span class="sxs-lookup"><span data-stu-id="03b39-120">Formatting blank lines</span></span>

* <span data-ttu-id="03b39-121">Samostatné nejvyšší úrovně funkce – třída definice a dva prázdné řádky.</span><span class="sxs-lookup"><span data-stu-id="03b39-121">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="03b39-122">Metoda definice uvnitř třídy jsou odděleny jeden prázdný řádek.</span><span class="sxs-lookup"><span data-stu-id="03b39-122">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="03b39-123">Prázdné řádky může šetřit () k oddělení skupin souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="03b39-123">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="03b39-124">Prázdné řádky může být vynechán mezi spoustu související one-liners (například sada fiktivní implementace).</span><span class="sxs-lookup"><span data-stu-id="03b39-124">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="03b39-125">Pomocí prázdné řádky ve funkcích, doporučujeme, označte logické oddíly.</span><span class="sxs-lookup"><span data-stu-id="03b39-125">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="03b39-126">Formátování komentáře</span><span class="sxs-lookup"><span data-stu-id="03b39-126">Formatting comments</span></span>

<span data-ttu-id="03b39-127">Obecně přednost více komentáře dvojitou lomítko přes komentáře bloku stylu ML.</span><span class="sxs-lookup"><span data-stu-id="03b39-127">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="03b39-128">Vložené komentáře by měl počáteční písmeno.</span><span class="sxs-lookup"><span data-stu-id="03b39-128">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="03b39-129">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="03b39-129">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="03b39-130">Použití camelCase vázané na třídu, vázané na výrazu a vzor vázané hodnoty a funkce</span><span class="sxs-lookup"><span data-stu-id="03b39-130">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="03b39-131">Je běžné a přijaté F # stylu camelCase používat pro všechny názvy vázána jako místní proměnné nebo v vzor shody a definice funkcí.</span><span class="sxs-lookup"><span data-stu-id="03b39-131">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="03b39-132">Funkce místně vázané ve třídách měli použít také camelCase.</span><span class="sxs-lookup"><span data-stu-id="03b39-132">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="03b39-133">Použití camelCase pro veřejné funkce vázané na modulu</span><span class="sxs-lookup"><span data-stu-id="03b39-133">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="03b39-134">Když funkce vázané na modulu je součástí veřejné rozhraní API, měla by používat camelCase:</span><span class="sxs-lookup"><span data-stu-id="03b39-134">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="03b39-135">Použít camelCase pro interní a privátní hodnoty vázané na modul a funkce</span><span class="sxs-lookup"><span data-stu-id="03b39-135">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="03b39-136">Použijte camelCase pro soukromé hodnoty vázané na modul, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="03b39-136">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="03b39-137">Ad hoc funkce ve skriptech</span><span class="sxs-lookup"><span data-stu-id="03b39-137">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="03b39-138">Hodnoty, které tvoří interní implementace modul nebo typ</span><span class="sxs-lookup"><span data-stu-id="03b39-138">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="03b39-139">Použití camelCase parametrů</span><span class="sxs-lookup"><span data-stu-id="03b39-139">Use camelCase for parameters</span></span>

<span data-ttu-id="03b39-140">Všechny parametry by měli používat camelCase v souladu s zásady vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="03b39-140">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="03b39-141">Použití PascalCase pro moduly</span><span class="sxs-lookup"><span data-stu-id="03b39-141">Use PascalCase for modules</span></span>

<span data-ttu-id="03b39-142">Všechny moduly (nejvyšší úrovně, interní, privátní, vnořené) by měli používat PascalCase.</span><span class="sxs-lookup"><span data-stu-id="03b39-142">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="03b39-143">Použít PascalCase pro typ deklarace, členů a popisky</span><span class="sxs-lookup"><span data-stu-id="03b39-143">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="03b39-144">Třídy, rozhraní, struktury, výčty, delegáti, záznamy a rozlišovaná sjednocení by měly název s PascalCase.</span><span class="sxs-lookup"><span data-stu-id="03b39-144">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="03b39-145">Členové v rámci typy a popisky pro záznamy a rozlišovaná sjednocení by měl používat také PascalCase.</span><span class="sxs-lookup"><span data-stu-id="03b39-145">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="03b39-146">Použít PascalCase pro konstrukce vnitřní na rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="03b39-146">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="03b39-147">Obory názvů, výjimky, události a projekt nebo`.dll` názvy měli použít také PascalCase.</span><span class="sxs-lookup"><span data-stu-id="03b39-147">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="03b39-148">Nejen nemá to zkontrolujte spotřeby z jinými jazyky rozhraní .NET působí přirozenější k příjemce, je také konzistentní s zásady vytváření názvů .NET, kterými se můžete setkat.</span><span class="sxs-lookup"><span data-stu-id="03b39-148">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="03b39-149">Vyhněte se podtržítka v názvech</span><span class="sxs-lookup"><span data-stu-id="03b39-149">Avoid underscores in names</span></span>

<span data-ttu-id="03b39-150">V minulosti používat některé knihovny F # v názvech podtržítka.</span><span class="sxs-lookup"><span data-stu-id="03b39-150">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="03b39-151">Ale toto je přijatá už široce, částečně, protože ho je v konfliktu s zásady vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="03b39-151">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="03b39-152">Ale nutné dodat, některé programátory F # pomocí podtržítka výraznou, částečně historických důvodů a proti chybám a ohledu je důležité.</span><span class="sxs-lookup"><span data-stu-id="03b39-152">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="03b39-153">Ale Upozorňujeme, že styl je často disliked jiní uživatelé, kteří mají vybrat o tom, jestli ho použít.</span><span class="sxs-lookup"><span data-stu-id="03b39-153">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="03b39-154">Některé výjimky zahrnuje spolupráce s nativním součásti, kde jsou velmi běžné podtržítka.</span><span class="sxs-lookup"><span data-stu-id="03b39-154">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="03b39-155">Použijte standardní operátory F #</span><span class="sxs-lookup"><span data-stu-id="03b39-155">Use standard F# operators</span></span>

<span data-ttu-id="03b39-156">Následující operátory jsou definovány v standardní knihovny F # a místo definování ekvivalenty měla být použita.</span><span class="sxs-lookup"><span data-stu-id="03b39-156">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="03b39-157">Pomocí těchto operátorů se nedoporučuje, protože je obvykle, aby byl kód čitelnější a idiomatickou.</span><span class="sxs-lookup"><span data-stu-id="03b39-157">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="03b39-158">Vývojářům pozadí v OCaml nebo jiné funkční programovací jazyk může být uzpůsobené pro různé idioms.</span><span class="sxs-lookup"><span data-stu-id="03b39-158">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="03b39-159">Následující seznam shrnuje doporučené operátory F #.</span><span class="sxs-lookup"><span data-stu-id="03b39-159">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="03b39-160">Použijte předponu syntaxi pro obecné typy (`Foo<T>`) přednostně syntaxe operátory (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="03b39-160">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="03b39-161">F # dědí oba operátory ML styl pojmenování obecné typy (například `int list`) a také předponu styl .NET (například `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="03b39-161">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="03b39-162">Dáváte přednost styl rozhraní .NET, s výjimkou čtyři konkrétní typy:</span><span class="sxs-lookup"><span data-stu-id="03b39-162">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="03b39-163">Pro F # uvádí, použijte formát operátory: `int list` místo `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="03b39-163">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="03b39-164">Pro možnosti F #, použijte formát operátory: `int option` místo `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="03b39-164">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="03b39-165">Pro F # pole, použijte syntaxi název `int[]` místo `int array` nebo `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="03b39-165">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="03b39-166">Referenční buňky, použijte `int ref` místo `ref<int>` nebo `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="03b39-166">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="03b39-167">Pro všechny ostatní typy použijte předponu formulář.</span><span class="sxs-lookup"><span data-stu-id="03b39-167">For all other types, use the prefix form.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="03b39-168">Formátování rozlišované deklarace sjednocení</span><span class="sxs-lookup"><span data-stu-id="03b39-168">Formatting discriminated union declarations</span></span>

<span data-ttu-id="03b39-169">Odsazení `|` v definici typu 4 mezerami:</span><span class="sxs-lookup"><span data-stu-id="03b39-169">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

<span data-ttu-id="03b39-170">Vytvořenou instanci Rozlišované sjednocení, který rozdělit do více řádků měl dát dat obsažených nový obor s odsazení:</span><span class="sxs-lookup"><span data-stu-id="03b39-170">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="03b39-171">Pravá závorka může být také na nový řádek:</span><span class="sxs-lookup"><span data-stu-id="03b39-171">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a><span data-ttu-id="03b39-172">Formátování řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="03b39-172">Formatting tuples</span></span>

<span data-ttu-id="03b39-173">Vytváření instancí řazené kolekce členů musí být v závorkách a rozdělujících čárkami v rámci by měl následovat a jedna mezera, například: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="03b39-173">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="03b39-174">Běžně přijatý výjimka je vynechejte závorkách vzor odpovídajícím řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="03b39-174">A commonly accepted exception is to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a><span data-ttu-id="03b39-175">Formátování záznamů</span><span class="sxs-lookup"><span data-stu-id="03b39-175">Formatting records</span></span>

<span data-ttu-id="03b39-176">Krátký záznamy lze zapsat na jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="03b39-176">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="03b39-177">Záznamy, které jsou delší měli použít pro štítky nové řádky:</span><span class="sxs-lookup"><span data-stu-id="03b39-177">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="03b39-178">Uvedení token otevírání na stejném řádku a token uzavírací na nový řádek je také vhodná:</span><span class="sxs-lookup"><span data-stu-id="03b39-178">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
    Boss1 = "Jeffrey"
    Boss2 = "Jeffrey"
    Boss3 = "Jeffrey"
    Boss4 = "Jeffrey"
    Boss5 = "Jeffrey"
    Boss6 = "Jeffrey"
    Boss7 = "Jeffrey"
    Boss8 = "Jeffrey"
    Lackeys = ["Zippy"; "George"; "Bungle"]
}
```

<span data-ttu-id="03b39-179">Stejná pravidla použít u elementů na seznamu a pole.</span><span class="sxs-lookup"><span data-stu-id="03b39-179">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="03b39-180">Formátování seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="03b39-180">Formatting lists and arrays</span></span>

<span data-ttu-id="03b39-181">Zápis `x :: l` prostory kolem `::` – operátor (`::` je zaváděcí operátor, proto ohraničeny znaky) a `[1; 2; 3]` (`;` je oddělovač, proto následované mezerou).</span><span class="sxs-lookup"><span data-stu-id="03b39-181">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="03b39-182">Používejte vždy alespoň jedna mezera mezi dva odlišné operátory složené závorce jako.</span><span class="sxs-lookup"><span data-stu-id="03b39-182">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="03b39-183">Například nechte mezeru mezi `[` a `{`.</span><span class="sxs-lookup"><span data-stu-id="03b39-183">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="03b39-184">Seznamy a polí, která rozdělit do více řádků postupujte stejně jako záznamy podobné pravidlo:</span><span class="sxs-lookup"><span data-stu-id="03b39-184">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="03b39-185">Formátování v případě výrazy</span><span class="sxs-lookup"><span data-stu-id="03b39-185">Formatting if expressions</span></span>

<span data-ttu-id="03b39-186">Odsazení podmíněné příkazy závisí na velikosti výrazy, které tvoří jejich.</span><span class="sxs-lookup"><span data-stu-id="03b39-186">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="03b39-187">Pokud `cond`, `e1` a `e2` jsou malé, jednoduše zapíše je na jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="03b39-187">If `cond`, `e1` and `e2` are small, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="03b39-188">Pokud `e1` a `cond` jsou malé, ale `e2` velký:</span><span class="sxs-lookup"><span data-stu-id="03b39-188">If `e1` and `cond` are small, but `e2` is large:</span></span>

```fsharp
if cond then e1
else
    e2
```

<span data-ttu-id="03b39-189">Pokud `e1` a `cond` jsou velké a `e2` je malá:</span><span class="sxs-lookup"><span data-stu-id="03b39-189">If `e1` and `cond` are large and `e2` is small:</span></span>

```fsharp
if cond then
    e1
else e2
```

<span data-ttu-id="03b39-190">Pokud jsou všechny výrazy velké:</span><span class="sxs-lookup"><span data-stu-id="03b39-190">If all the expressions are large:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="03b39-191">Více podmíněné příkazy s `elif` a `else` odsazeny stejný obor jako `if`:</span><span class="sxs-lookup"><span data-stu-id="03b39-191">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="03b39-192">Vzor odpovídající konstrukce</span><span class="sxs-lookup"><span data-stu-id="03b39-192">Pattern matching constructs</span></span>

<span data-ttu-id="03b39-193">Použití `|` pro každou klauzuli shoda s žádné odsazení.</span><span class="sxs-lookup"><span data-stu-id="03b39-193">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="03b39-194">Pokud výraz krátký, můžete zvážit použití jeden řádek, pokud každý dílčím výrazu je také jednoduché.</span><span class="sxs-lookup"><span data-stu-id="03b39-194">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="03b39-195">Pokud ve výrazu na pravé straně šipku pro porovnávání je příliš velký, ho přesunout do následujícího řádku, zobrazují odsazené jeden krok z `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="03b39-195">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="03b39-196">Vzor odpovídající anonymní funkcí, spouštění podle `function`, obecně by neměl příliš daleko odsazení.</span><span class="sxs-lookup"><span data-stu-id="03b39-196">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="03b39-197">Například následující odsazení jeden obor je v pořádku:</span><span class="sxs-lookup"><span data-stu-id="03b39-197">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="03b39-198">Ve funkcích definované porovnávání vzorů `let` nebo `let rec` by měla být zobrazují odsazené 4 mezery po spuštění systému `let`i v případě `function` – klíčové slovo se používá:</span><span class="sxs-lookup"><span data-stu-id="03b39-198">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="03b39-199">Nedoporučujeme zarovnání šipky.</span><span class="sxs-lookup"><span data-stu-id="03b39-199">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="03b39-200">Formátování try / s výrazy</span><span class="sxs-lookup"><span data-stu-id="03b39-200">Formatting try/with expressions</span></span>

<span data-ttu-id="03b39-201">Pro porovnávání na typ výjimky by měla být odsazeny na stejné úrovni jako `with`.</span><span class="sxs-lookup"><span data-stu-id="03b39-201">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="03b39-202">Formátování aplikace parametr – funkce</span><span class="sxs-lookup"><span data-stu-id="03b39-202">Formatting function parameter application</span></span>

<span data-ttu-id="03b39-203">Obecně platí většina aplikací parametr funkce se provádí na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="03b39-203">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="03b39-204">Pokud chcete použít parametry pro funkci na nový řádek, odsazení je jeden obor.</span><span class="sxs-lookup"><span data-stu-id="03b39-204">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="03b39-205">Pro výrazy lambda platí stejné pokyny jako argumenty funkce.</span><span class="sxs-lookup"><span data-stu-id="03b39-205">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="03b39-206">Pokud text výrazu lambda, text může mít jiný řádku odsazeny o jeden obor</span><span class="sxs-lookup"><span data-stu-id="03b39-206">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="03b39-207">Ale pokud text výrazu lambda je více než jeden řádek, vezměte v úvahu řešení ho do samostatné funkce nemusí používat Víceřádkový konstrukt použít jako jeden argument na funkci.</span><span class="sxs-lookup"><span data-stu-id="03b39-207">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="03b39-208">Formátování zaváděcí operátory</span><span class="sxs-lookup"><span data-stu-id="03b39-208">Formatting infix operators</span></span>

<span data-ttu-id="03b39-209">Samostatné operátory mezerami.</span><span class="sxs-lookup"><span data-stu-id="03b39-209">Separate operators by spaces.</span></span> <span data-ttu-id="03b39-210">Zřejmé výjimkou tohoto pravidla jsou `!` a `.` operátory.</span><span class="sxs-lookup"><span data-stu-id="03b39-210">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="03b39-211">Zaváděcí výrazy řazení na stejný sloupec je OK:</span><span class="sxs-lookup"><span data-stu-id="03b39-211">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="03b39-212">Formátování operátorů kanálů</span><span class="sxs-lookup"><span data-stu-id="03b39-212">Formatting pipeline operators</span></span>

<span data-ttu-id="03b39-213">Kanál `|>` operátory má zobrazit pod pracují na výrazy.</span><span class="sxs-lookup"><span data-stu-id="03b39-213">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="03b39-214">Formátovací moduly</span><span class="sxs-lookup"><span data-stu-id="03b39-214">Formatting modules</span></span>

<span data-ttu-id="03b39-215">Kód v místním modulu musí odsazeny relativně k modulu, ale nesmí být odsazeny kód v modul nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="03b39-215">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="03b39-216">Namespace prvky nemají odsazení.</span><span class="sxs-lookup"><span data-stu-id="03b39-216">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="03b39-217">Formátování objektové výrazy a rozhraní</span><span class="sxs-lookup"><span data-stu-id="03b39-217">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="03b39-218">Objektové výrazy a rozhraní by mělo být zarovnáno stejně jako s `member` se odsazeny po 4 mezery.</span><span class="sxs-lookup"><span data-stu-id="03b39-218">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a><span data-ttu-id="03b39-219">Formátování prázdné znaky na výrazy</span><span class="sxs-lookup"><span data-stu-id="03b39-219">Formatting whitespace in expressions</span></span>

<span data-ttu-id="03b39-220">Nepoužívejte nadbytečné prázdné znaky na výrazy F #.</span><span class="sxs-lookup"><span data-stu-id="03b39-220">Avoid extraneous whitespace in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="03b39-221">Pojmenované argumenty by neměl mít také, které obaluje místa `=`:</span><span class="sxs-lookup"><span data-stu-id="03b39-221">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
