---
title: F#pravidla formátování kódu
description: Přečtěte si pokyny pro formátování F# kódu.
ms.date: 02/08/2019
ms.openlocfilehash: 259d4bb2147d1fc8bc5d35d7ff2e3c34ec2185d0
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613821"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="58189-103">F#pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="58189-103">F# code formatting guidelines</span></span>

<span data-ttu-id="58189-104">Tento článek nabízí pokyny k formátování kódu tak, aby vaše F# kód je:</span><span class="sxs-lookup"><span data-stu-id="58189-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="58189-105">Obecně zobrazit jako čitelnější</span><span class="sxs-lookup"><span data-stu-id="58189-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="58189-106">Je v souladu s konvencí použil(a) formátování nástroje v sadě Visual Studio a ostatní editory</span><span class="sxs-lookup"><span data-stu-id="58189-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="58189-107">Podobně jako další kód online</span><span class="sxs-lookup"><span data-stu-id="58189-107">Similar to other code online</span></span>

<span data-ttu-id="58189-108">Tyto pokyny jsou založeny na [komplexní pokyny k F# konvence formátování](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) podle [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="58189-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="58189-109">Obecná pravidla pro odsazení</span><span class="sxs-lookup"><span data-stu-id="58189-109">General rules for indentation</span></span>

<span data-ttu-id="58189-110">F#ve výchozím nastavení používá významných mezer.</span><span class="sxs-lookup"><span data-stu-id="58189-110">F# uses significant white space by default.</span></span> <span data-ttu-id="58189-111">Následující pokyny jsou určeny a přidal se návod, jak některé běžné problémy, které to může často znamenat výrazný přehlednější.</span><span class="sxs-lookup"><span data-stu-id="58189-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="58189-112">Použití prostorů</span><span class="sxs-lookup"><span data-stu-id="58189-112">Using spaces</span></span>

<span data-ttu-id="58189-113">Když odsazení se vyžaduje, je nutné použít prostory, ne karty.</span><span class="sxs-lookup"><span data-stu-id="58189-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="58189-114">Vyžaduje se alespoň jedna mezera.</span><span class="sxs-lookup"><span data-stu-id="58189-114">At least one space is required.</span></span> <span data-ttu-id="58189-115">Vaše organizace může vytvořit kódování standardy, chcete-li určit počet mezer pro odsazení; dvě, tři nebo čtyři mezery odsazení na všech úrovních, kde dochází k odsazení je obvyklé.</span><span class="sxs-lookup"><span data-stu-id="58189-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="58189-116">**Doporučujeme 4 mezery za odsazení.**</span><span class="sxs-lookup"><span data-stu-id="58189-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="58189-117">Ale nutné dodat, odsazení programů, což je subjektivní.</span><span class="sxs-lookup"><span data-stu-id="58189-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="58189-118">Variace se OK, ale je první pravidlo, měli byste postupovat podle *konzistence odsazení*.</span><span class="sxs-lookup"><span data-stu-id="58189-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="58189-119">Zvolte obecně přijímané styl odsazení a systematicky používat v rámci vašeho základu kódu.</span><span class="sxs-lookup"><span data-stu-id="58189-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="58189-120">Formátování prázdných znaků</span><span class="sxs-lookup"><span data-stu-id="58189-120">Formatting white space</span></span>

<span data-ttu-id="58189-121">F#rozlišuje prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="58189-121">F# is white space sensitive.</span></span> <span data-ttu-id="58189-122">I když většina sémantiku než prázdné znaky jsou předmětem správné odsazení, existují některé věci k uvážení.</span><span class="sxs-lookup"><span data-stu-id="58189-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="58189-123">Formátování operátory v aritmetických výrazech</span><span class="sxs-lookup"><span data-stu-id="58189-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="58189-124">Vždy používejte mezery kolem binárních aritmetických výrazů:</span><span class="sxs-lookup"><span data-stu-id="58189-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="58189-125">Unární `-` operátory by měly mít vždy hodnotu jsou negace bezprostředně následuje po:</span><span class="sxs-lookup"><span data-stu-id="58189-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="58189-126">Prázdný znak po přidání `-` operátor může vést k záměně pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="58189-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="58189-127">Stručně řečeno je potřeba vždy:</span><span class="sxs-lookup"><span data-stu-id="58189-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="58189-128">Před a za binární operátory s prázdné znaky</span><span class="sxs-lookup"><span data-stu-id="58189-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="58189-129">Nikdy nemůžete mít prázdný znak za unární operátor</span><span class="sxs-lookup"><span data-stu-id="58189-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="58189-130">Obecné zásady binární aritmetického operátoru je obzvláště důležité.</span><span class="sxs-lookup"><span data-stu-id="58189-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="58189-131">Selhání před a za binární soubor `-` operátor v kombinaci s určitým možnostmi formátování, může vést k interpretaci jako unární `-`.</span><span class="sxs-lookup"><span data-stu-id="58189-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="58189-132">Definice vlastního operátoru prázdnými znaky před a za</span><span class="sxs-lookup"><span data-stu-id="58189-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="58189-133">Vždy použijte prázdné znaky před a za definici operátoru:</span><span class="sxs-lookup"><span data-stu-id="58189-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="58189-134">Pro všechny vlastní operátor, který začíná `*` a, který má více než jeden znak, budete muset přidat mezery na začátku definice, aby se zabránilo nejednoznačnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="58189-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="58189-135">Z tohoto důvodu doporučujeme jednoduše uzavřete definice všechny operátory s jeden prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="58189-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="58189-136">Funkce šipky parametr prázdnými znaky před a za</span><span class="sxs-lookup"><span data-stu-id="58189-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="58189-137">Při definování podpis funkce, použijte prázdný prostor kolem `->` symbolů:</span><span class="sxs-lookup"><span data-stu-id="58189-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="58189-138">Formátování prázdných řádků</span><span class="sxs-lookup"><span data-stu-id="58189-138">Formatting blank lines</span></span>

* <span data-ttu-id="58189-139">Samostatné nejvyšší úrovně funkce a třídy definice se dvěma prázdné řádky.</span><span class="sxs-lookup"><span data-stu-id="58189-139">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="58189-140">Definice metody uvnitř třídy jsou odděleny jeden prázdný řádek.</span><span class="sxs-lookup"><span data-stu-id="58189-140">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="58189-141">Prázdné řádky může použít k oddělení skupin souvisejících funkcí (střídmě).</span><span class="sxs-lookup"><span data-stu-id="58189-141">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="58189-142">Můžete vynechat prázdné řádky mezi spoustu související one-liners (například sadu fiktivní implementace).</span><span class="sxs-lookup"><span data-stu-id="58189-142">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="58189-143">Pomocí prázdné řádky ve službě functions opatrně, označte logické oddíly.</span><span class="sxs-lookup"><span data-stu-id="58189-143">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="58189-144">Formátování komentáře</span><span class="sxs-lookup"><span data-stu-id="58189-144">Formatting comments</span></span>

<span data-ttu-id="58189-145">Obecně přednost více komentářů dvěma lomítky přes ML – vizuální styl blok komentáře.</span><span class="sxs-lookup"><span data-stu-id="58189-145">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="58189-146">Vložené komentáře by měl velké první písmeno první písmeno.</span><span class="sxs-lookup"><span data-stu-id="58189-146">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="58189-147">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="58189-147">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="58189-148">Hodnoty vázané na třídu, vázané na výrazu a vzor vázané a funkcí pomocí camelCase</span><span class="sxs-lookup"><span data-stu-id="58189-148">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="58189-149">Je běžné a přijatou F# stylu camelCase používat pro všechny názvy vázaný jako lokální proměnné nebo v porovnávání vzorů a definice funkce.</span><span class="sxs-lookup"><span data-stu-id="58189-149">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="58189-150">Místně vázaných funkcí v třídách použít i pro camelCase.</span><span class="sxs-lookup"><span data-stu-id="58189-150">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="58189-151">Pro veřejné funkce vázané na modul pomocí camelCase</span><span class="sxs-lookup"><span data-stu-id="58189-151">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="58189-152">Pokud modul vázané funkce je součástí veřejného rozhraní API, měla by používat camelCase:</span><span class="sxs-lookup"><span data-stu-id="58189-152">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="58189-153">Pomocí camelCase pro interní a privátní hodnoty vázané na modul a funkce</span><span class="sxs-lookup"><span data-stu-id="58189-153">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="58189-154">Pomocí camelCase pro soukromé hodnoty vázané na modul, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="58189-154">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="58189-155">Funkce ad hoc ve skriptech</span><span class="sxs-lookup"><span data-stu-id="58189-155">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="58189-156">Hodnoty, které tvoří vnitřní implementace modulem nebo typem.</span><span class="sxs-lookup"><span data-stu-id="58189-156">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="58189-157">Pro parametry pomocí camelCase</span><span class="sxs-lookup"><span data-stu-id="58189-157">Use camelCase for parameters</span></span>

<span data-ttu-id="58189-158">Všechny parametry používali camelCase v souladu s zásady vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="58189-158">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="58189-159">Pro moduly pomocí PascalCase</span><span class="sxs-lookup"><span data-stu-id="58189-159">Use PascalCase for modules</span></span>

<span data-ttu-id="58189-160">Všechny moduly (nejvyšší úrovně, interní, privátní, vnořené) používejte PascalCase.</span><span class="sxs-lookup"><span data-stu-id="58189-160">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="58189-161">Pomocí PascalCase u deklarace typu, členů a popisků</span><span class="sxs-lookup"><span data-stu-id="58189-161">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="58189-162">Třídy, rozhraní, struktury, výčty, delegáti, záznamů a rozlišovaná sjednocení by měl název pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="58189-162">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="58189-163">Členy v rámci typů a popisků záznamů a rozlišovaná sjednocení také používali PascalCase.</span><span class="sxs-lookup"><span data-stu-id="58189-163">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="58189-164">Pro konstruktory, které jsou přirozené pro .NET pomocí PascalCase</span><span class="sxs-lookup"><span data-stu-id="58189-164">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="58189-165">Obory názvů, výjimky, události a projekt /`.dll` názvy mělo používat taky pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="58189-165">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="58189-166">Nejen tím neodstraní, ale využití z jiných jazyků .NET působit přirozeně více uživatelům, je také v souladu s konvence pojmenování .NET, které budete pravděpodobně dojde k.</span><span class="sxs-lookup"><span data-stu-id="58189-166">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="58189-167">Vyhněte se podtržítka v názvech</span><span class="sxs-lookup"><span data-stu-id="58189-167">Avoid underscores in names</span></span>

<span data-ttu-id="58189-168">V minulosti některé F# knihovny použili v názvech podtržítka.</span><span class="sxs-lookup"><span data-stu-id="58189-168">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="58189-169">Ale to je přijat už široce, částečně proto, že je v konfliktu s zásady vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="58189-169">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="58189-170">Nicméně některé F# programátoři používají podtržítka silně, částečně z historických důvodů a odolnosti proti chybám a ohledu je důležité.</span><span class="sxs-lookup"><span data-stu-id="58189-170">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="58189-171">Nezapomínejte, že styl je často disliked jinými uživateli, kteří rozhodnout o tom, jestli ji používat.</span><span class="sxs-lookup"><span data-stu-id="58189-171">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="58189-172">Některé výjimky zahrnuje spolupráce s nativními komponentami, kde jsou velmi běžné podtržítka.</span><span class="sxs-lookup"><span data-stu-id="58189-172">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="58189-173">Pomocí standardních F# operátory</span><span class="sxs-lookup"><span data-stu-id="58189-173">Use standard F# operators</span></span>

<span data-ttu-id="58189-174">Následující operátory jsou definovány v F# standardní knihovny a musí být použity místo definování ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="58189-174">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="58189-175">Jak je obvykle, aby byl kód čitelnější a idiomatickou, doporučuje se použití těchto operátorů.</span><span class="sxs-lookup"><span data-stu-id="58189-175">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="58189-176">Vývojáři a má zázemí ve OCaml nebo jiných funkcionálním programovacím jazyce může být na různých idiomy zvyklí.</span><span class="sxs-lookup"><span data-stu-id="58189-176">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="58189-177">Následující seznam shrnuje doporučené F# operátory.</span><span class="sxs-lookup"><span data-stu-id="58189-177">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="58189-178">Použijte předponu syntaxi pro obecné typy (`Foo<T>`) před syntaxe přípony (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="58189-178">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="58189-179">F#dědí obě přípony ML styl pojmenování obecných typů (například `int list`) stejně jako předpona .NET stylu (například `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="58189-179">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="58189-180">Preferovat stylu .NET, s výjimkou čtyři konkrétní typy:</span><span class="sxs-lookup"><span data-stu-id="58189-180">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="58189-181">Pro F# seznamy, použijte příponový tvar: `int list` spíše než `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="58189-181">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="58189-182">Pro F# možnosti použít příponový tvar: `int option` spíše než `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="58189-182">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="58189-183">Pro F# pole, použijte syntaxi název `int[]` spíše než `int array` nebo `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="58189-183">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="58189-184">Odkazové buňky pomocí `int ref` spíše než `ref<int>` nebo `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="58189-184">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="58189-185">Pro všechny ostatní typy použijte prefixová podoba.</span><span class="sxs-lookup"><span data-stu-id="58189-185">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="58189-186">Formátování řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="58189-186">Formatting tuples</span></span>

<span data-ttu-id="58189-187">Vytvoření instance řazené kolekce členů musí být v závorce a oddělovací čárky v rámci by měl následovat jednu mezeru, například: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="58189-187">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="58189-188">Běžně přijetím vynechejte závorky v porovnávání vzorů řazených kolekcí členů:</span><span class="sxs-lookup"><span data-stu-id="58189-188">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="58189-189">Také běžně přijetím vynechejte závorky, pokud řazené kolekce členů je návratová hodnota funkce:</span><span class="sxs-lookup"><span data-stu-id="58189-189">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="58189-190">Stručně řečeno, dáváte přednost instancí řazené kolekce členů v závorkách, ale při použití řazených kolekcí členů pro porovnávání vzorů nebo návratovou hodnotu, považuje se můžete vyhnout závorky.</span><span class="sxs-lookup"><span data-stu-id="58189-190">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="58189-191">Formátování rozlišované deklarace sjednocení</span><span class="sxs-lookup"><span data-stu-id="58189-191">Formatting discriminated union declarations</span></span>

<span data-ttu-id="58189-192">Odsadit `|` v definici typu 4 mezerami:</span><span class="sxs-lookup"><span data-stu-id="58189-192">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="58189-193">Formátování rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="58189-193">Formatting discriminated unions</span></span>

<span data-ttu-id="58189-194">Instance rozlišovaná sjednocení, které rozdělit mezi několik řádků by měla poskytnout dat obsažených nový obor s odsazením:</span><span class="sxs-lookup"><span data-stu-id="58189-194">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="58189-195">Pravá závorka může být také na nový řádek:</span><span class="sxs-lookup"><span data-stu-id="58189-195">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="58189-196">Formátování záznam deklarace</span><span class="sxs-lookup"><span data-stu-id="58189-196">Formatting record declarations</span></span>

<span data-ttu-id="58189-197">Odsadit `{` v typu definice 4 mezery a spustit v seznamu polí na stejný řádek:</span><span class="sxs-lookup"><span data-stu-id="58189-197">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="58189-198">Uvedení na nový řádek a pravou token na nový řádek levou token je vhodnější, pokud deklarujete implementace rozhraní nebo členy v záznamu:</span><span class="sxs-lookup"><span data-stu-id="58189-198">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="58189-199">Formátování záznamů</span><span class="sxs-lookup"><span data-stu-id="58189-199">Formatting records</span></span>

<span data-ttu-id="58189-200">Krátký záznamy je možné psát v jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="58189-200">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="58189-201">Záznamy, které jsou delší používali nové řádky popisků:</span><span class="sxs-lookup"><span data-stu-id="58189-201">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="58189-202">Uvedení otevírání token na nový řádek, obsah s kartami více než jeden obor a pravou token na nový řádek je vhodnější, pokud jste:</span><span class="sxs-lookup"><span data-stu-id="58189-202">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="58189-203">Záznamy pohyb v kódu s obory odlišné odsazení</span><span class="sxs-lookup"><span data-stu-id="58189-203">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="58189-204">Přesměrujete do funkce</span><span class="sxs-lookup"><span data-stu-id="58189-204">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
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

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="58189-205">Stejná pravidla platí i pro seznam a pole prvků.</span><span class="sxs-lookup"><span data-stu-id="58189-205">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="58189-206">Formátování záznam kopírování a aktualizace výrazů</span><span class="sxs-lookup"><span data-stu-id="58189-206">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="58189-207">Výrazu kopírování a aktualizace záznamu je stále záznam, takže platí podobné pokyny.</span><span class="sxs-lookup"><span data-stu-id="58189-207">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="58189-208">Krátký výrazy vejde na jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="58189-208">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="58189-209">Výrazy delší dobu používali nové řádky:</span><span class="sxs-lookup"><span data-stu-id="58189-209">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="58189-210">A jako s pokyny k záznamu, můžete chtít vyhradit samostatné řádky pro složené závorky a odsazovat jeden obor vpravo s výrazem.</span><span class="sxs-lookup"><span data-stu-id="58189-210">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="58189-211">Všimněte si, že v některých případech speciální, jako je například obtékání hodnotu s volitelným bez závorek, budete muset zachovat složenou závorku na jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="58189-211">Note that in some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="58189-212">Formátování seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="58189-212">Formatting lists and arrays</span></span>

<span data-ttu-id="58189-213">Zápis `x :: l` s mezery kolem `::` – operátor (`::` je operátor vpony, proto obklopené mezerami).</span><span class="sxs-lookup"><span data-stu-id="58189-213">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="58189-214">Seznam a pole deklarovaná na jednom řádku by měly mít mezera za levou závorku a před pravou hranatou závorku:</span><span class="sxs-lookup"><span data-stu-id="58189-214">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="58189-215">Používejte vždy alespoň jednu mezeru mezi dva odlišné operátory podobném složenou závorku.</span><span class="sxs-lookup"><span data-stu-id="58189-215">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="58189-216">Například, ponechte mezeru mezi `[` a `{`.</span><span class="sxs-lookup"><span data-stu-id="58189-216">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="58189-217">Stejné pravidlo platí pro seznamy a pole řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="58189-217">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="58189-218">Seznamy a pole, která se rozdělit mezi několik řádků postupujte stejně jako záznamy podobné pravidlo:</span><span class="sxs-lookup"><span data-stu-id="58189-218">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="58189-219">A stejně jako u záznamů, deklarace otevírací a uzavírací hranaté závorce na vlastním řádku vám usnadní přesunutí kódu kolem a zřetězení příkazů do funkcí.</span><span class="sxs-lookup"><span data-stu-id="58189-219">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="58189-220">Formátování if výrazy</span><span class="sxs-lookup"><span data-stu-id="58189-220">Formatting if expressions</span></span>

<span data-ttu-id="58189-221">Odsazení podmíněné výrazy závisí na velikosti výrazy, které společně tvoří.</span><span class="sxs-lookup"><span data-stu-id="58189-221">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="58189-222">Pokud `cond`, `e1` a `e2` jsou krátký, napište jednoduše na jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="58189-222">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="58189-223">Pokud `cond`, `e1` nebo `e2` delší dobu, ale ne více řádky:</span><span class="sxs-lookup"><span data-stu-id="58189-223">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="58189-224">Pokud je některý z výrazů více řádky:</span><span class="sxs-lookup"><span data-stu-id="58189-224">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="58189-225">Více podmíněné výrazy s `elif` a `else` odsazeny ve stejném oboru jako `if`:</span><span class="sxs-lookup"><span data-stu-id="58189-225">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="58189-226">Odpovídající vzor konstrukce</span><span class="sxs-lookup"><span data-stu-id="58189-226">Pattern matching constructs</span></span>

<span data-ttu-id="58189-227">Použití `|` pro každou klauzuli shoda s žádné odsazení.</span><span class="sxs-lookup"><span data-stu-id="58189-227">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="58189-228">Pokud výraz je krátký, můžete použít jeden řádek, pokud každý dílčí výraz je také jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="58189-228">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="58189-229">Výraz na pravé straně porovnávání vzorů šipky je příliš velká, tento soubor přesune do následujícího řádku, odsazený jeden krok z `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="58189-229">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="58189-230">Vzorovou shodu anonymní funkcí, které se spouští podle `function`, obecně by neměl příliš daleko odsazení.</span><span class="sxs-lookup"><span data-stu-id="58189-230">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="58189-231">Například následující odsazení jeden rozsah je v pořádku:</span><span class="sxs-lookup"><span data-stu-id="58189-231">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="58189-232">Porovnávání vzorů v funkce určené `let` nebo `let rec` po spuštění by měl být odsazený 4 mezer `let`i v případě `function` – klíčové slovo se používá:</span><span class="sxs-lookup"><span data-stu-id="58189-232">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="58189-233">Nedoporučujeme zarovnání šipky.</span><span class="sxs-lookup"><span data-stu-id="58189-233">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="58189-234">Formátování try / with výrazy</span><span class="sxs-lookup"><span data-stu-id="58189-234">Formatting try/with expressions</span></span>

<span data-ttu-id="58189-235">Vzorec pro porovnávání na typ výjimky by měly odsazena na stejné úrovni jako `with`.</span><span class="sxs-lookup"><span data-stu-id="58189-235">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="58189-236">Formátování aplikace parametr – funkce</span><span class="sxs-lookup"><span data-stu-id="58189-236">Formatting function parameter application</span></span>

<span data-ttu-id="58189-237">Obecně platí většina aplikací parametr funkce se provádí na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="58189-237">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="58189-238">Pokud budete chtít použít parametry pro funkci na novém řádku, odsazení je jeden obor.</span><span class="sxs-lookup"><span data-stu-id="58189-238">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="58189-239">Podle stejných pravidel platí pro výrazy lambda jako argumenty funkce.</span><span class="sxs-lookup"><span data-stu-id="58189-239">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="58189-240">Pokud hlavní část výrazu lambda, text může mít jiný řádek odsazeny o jeden obor</span><span class="sxs-lookup"><span data-stu-id="58189-240">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="58189-241">Nicméně pokud hlavní část výrazu lambda je více než jeden řádek, vezměte v úvahu řešení ho do samostatné funkce a nenechat konstrukci Víceřádkový použít jako jediný argument pro funkci.</span><span class="sxs-lookup"><span data-stu-id="58189-241">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="58189-242">Formátování infixové operátory</span><span class="sxs-lookup"><span data-stu-id="58189-242">Formatting infix operators</span></span>

<span data-ttu-id="58189-243">Samostatné operátory mezerami.</span><span class="sxs-lookup"><span data-stu-id="58189-243">Separate operators by spaces.</span></span> <span data-ttu-id="58189-244">Ze zřejmých výjimky z tohoto pravidla jsou `!` a `.` operátory.</span><span class="sxs-lookup"><span data-stu-id="58189-244">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="58189-245">Výrazy vpony je OK lineup na stejný sloupec:</span><span class="sxs-lookup"><span data-stu-id="58189-245">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="58189-246">Formátování operátorů kanálů</span><span class="sxs-lookup"><span data-stu-id="58189-246">Formatting pipeline operators</span></span>

<span data-ttu-id="58189-247">Kanál `|>` operátory by měly patřit pod pracují na výrazy.</span><span class="sxs-lookup"><span data-stu-id="58189-247">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="58189-248">Formátovací moduly</span><span class="sxs-lookup"><span data-stu-id="58189-248">Formatting modules</span></span>

<span data-ttu-id="58189-249">Kód v místním modulu musí odsazený relativně k modulu, ale neměli odsazeny kódu v nejvyšší úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="58189-249">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="58189-250">Prvky Namespace, není potřeba odsazeny.</span><span class="sxs-lookup"><span data-stu-id="58189-250">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="58189-251">Formátování objektové výrazy a rozhraní</span><span class="sxs-lookup"><span data-stu-id="58189-251">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="58189-252">Objektové výrazy a rozhraní zarovnání stejným způsobem s `member` se odsazena po 4 mezer.</span><span class="sxs-lookup"><span data-stu-id="58189-252">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="58189-253">Formátování prázdných ve výrazech</span><span class="sxs-lookup"><span data-stu-id="58189-253">Formatting white space in expressions</span></span>

<span data-ttu-id="58189-254">Vyhněte se nadbytečné prázdné místo v F# výrazy.</span><span class="sxs-lookup"><span data-stu-id="58189-254">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="58189-255">Pojmenované argumenty neměli také místa okolo `=`:</span><span class="sxs-lookup"><span data-stu-id="58189-255">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="58189-256">Atributy formátování</span><span class="sxs-lookup"><span data-stu-id="58189-256">Formatting attributes</span></span>

<span data-ttu-id="58189-257">[Atributy](../language-reference/attributes.md) jsou umístěny nad konstrukce:</span><span class="sxs-lookup"><span data-stu-id="58189-257">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="58189-258">Formátování atributy pro parametry</span><span class="sxs-lookup"><span data-stu-id="58189-258">Formatting attributes on parameters</span></span>

<span data-ttu-id="58189-259">Atributy mohou být také míst na parametry.</span><span class="sxs-lookup"><span data-stu-id="58189-259">Attributes can also be places on parameters.</span></span> <span data-ttu-id="58189-260">V takovém případě umístěte klikněte na stejném řádku jako parametr a před názvem:</span><span class="sxs-lookup"><span data-stu-id="58189-260">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="58189-261">Formátování více atributů</span><span class="sxs-lookup"><span data-stu-id="58189-261">Formatting multiple attributes</span></span>

<span data-ttu-id="58189-262">Při více atributy jsou použity konstrukce, která se nejedná o parametr, by měla být umístěna tak, že je jeden atribut na řádek:</span><span class="sxs-lookup"><span data-stu-id="58189-262">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="58189-263">Při použití parametru, musí být na stejném řádku a oddělené `;` oddělovač.</span><span class="sxs-lookup"><span data-stu-id="58189-263">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="58189-264">Formátování literály</span><span class="sxs-lookup"><span data-stu-id="58189-264">Formatting literals</span></span>

<span data-ttu-id="58189-265">[F#literály](../language-reference/literals.md) pomocí `Literal` atribut by měl umístit atribut na samostatném řádku a pomocí camelCase pojmenování:</span><span class="sxs-lookup"><span data-stu-id="58189-265">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use camelCase naming:</span></span>

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="58189-266">Předejde atribut na stejný řádek jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="58189-266">Avoid placing the attribute on the same line as the value.</span></span>
