---
title: F#pravidla formátování kódu
description: Přečtěte si pokyny pro formátování F# kódu.
ms.date: 11/26/2018
ms.openlocfilehash: 993ba8d42570d92789a9fc1967b8185b45643d56
ms.sourcegitcommit: 2151690e10d91545e2c20d6b5ad222c162b6b83d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2018
ms.locfileid: "43858002"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="39bb0-103">F#pravidla formátování kódu</span><span class="sxs-lookup"><span data-stu-id="39bb0-103">F# code formatting guidelines</span></span>

<span data-ttu-id="39bb0-104">Tento článek nabízí pokyny k formátování kódu tak, aby vaše F# kód je:</span><span class="sxs-lookup"><span data-stu-id="39bb0-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="39bb0-105">Obecně zobrazit jako čitelnější</span><span class="sxs-lookup"><span data-stu-id="39bb0-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="39bb0-106">Je v souladu s konvencí použil(a) formátování nástroje v sadě Visual Studio a ostatní editory</span><span class="sxs-lookup"><span data-stu-id="39bb0-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="39bb0-107">Podobně jako další kód online</span><span class="sxs-lookup"><span data-stu-id="39bb0-107">Similar to other code online</span></span>

<span data-ttu-id="39bb0-108">Tyto pokyny jsou založeny na [komplexní pokyny k F# konvence formátování](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) podle [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="39bb0-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="39bb0-109">Obecná pravidla pro odsazení</span><span class="sxs-lookup"><span data-stu-id="39bb0-109">General rules for indentation</span></span>

<span data-ttu-id="39bb0-110">F#ve výchozím nastavení používá významných mezer.</span><span class="sxs-lookup"><span data-stu-id="39bb0-110">F# uses significant white space by default.</span></span> <span data-ttu-id="39bb0-111">Následující pokyny jsou určeny a přidal se návod, jak některé běžné problémy, které to může často znamenat výrazný přehlednější.</span><span class="sxs-lookup"><span data-stu-id="39bb0-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="39bb0-112">Použití prostorů</span><span class="sxs-lookup"><span data-stu-id="39bb0-112">Using spaces</span></span>

<span data-ttu-id="39bb0-113">Když odsazení se vyžaduje, je nutné použít prostory, ne karty.</span><span class="sxs-lookup"><span data-stu-id="39bb0-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="39bb0-114">Vyžaduje se alespoň jedna mezera.</span><span class="sxs-lookup"><span data-stu-id="39bb0-114">At least one space is required.</span></span> <span data-ttu-id="39bb0-115">Vaše organizace může vytvořit kódování standardy, chcete-li určit počet mezer pro odsazení; dvě, tři nebo čtyři mezery odsazení na všech úrovních, kde dochází k odsazení je obvyklé.</span><span class="sxs-lookup"><span data-stu-id="39bb0-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="39bb0-116">**Doporučujeme 4 mezery za odsazení.**</span><span class="sxs-lookup"><span data-stu-id="39bb0-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="39bb0-117">Ale nutné dodat, odsazení programů, což je subjektivní.</span><span class="sxs-lookup"><span data-stu-id="39bb0-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="39bb0-118">Variace se OK, ale je první pravidlo, měli byste postupovat podle *konzistence odsazení*.</span><span class="sxs-lookup"><span data-stu-id="39bb0-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="39bb0-119">Zvolte obecně přijímané styl odsazení a systematicky používat v rámci vašeho základu kódu.</span><span class="sxs-lookup"><span data-stu-id="39bb0-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="39bb0-120">Formátování prázdných znaků</span><span class="sxs-lookup"><span data-stu-id="39bb0-120">Formatting white space</span></span>

<span data-ttu-id="39bb0-121">F#rozlišuje prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="39bb0-121">F# is white space sensitive.</span></span> <span data-ttu-id="39bb0-122">I když většina sémantiku než prázdné znaky jsou předmětem správné odsazení, existují některé věci k uvážení.</span><span class="sxs-lookup"><span data-stu-id="39bb0-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="39bb0-123">Formátování operátory v aritmetických výrazech</span><span class="sxs-lookup"><span data-stu-id="39bb0-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="39bb0-124">Vždy používejte mezery kolem binárních aritmetických výrazů:</span><span class="sxs-lookup"><span data-stu-id="39bb0-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="39bb0-125">Unární `-` operátory by měly mít vždy hodnotu jsou negace bezprostředně následuje po:</span><span class="sxs-lookup"><span data-stu-id="39bb0-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="39bb0-126">Prázdný znak po přidání `-` operátor může vést k záměně pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="39bb0-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="39bb0-127">Stručně řečeno je potřeba vždy:</span><span class="sxs-lookup"><span data-stu-id="39bb0-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="39bb0-128">Před a za binární operátory s prázdné znaky</span><span class="sxs-lookup"><span data-stu-id="39bb0-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="39bb0-129">Nikdy nemůžete mít prázdný znak za unární operátor</span><span class="sxs-lookup"><span data-stu-id="39bb0-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="39bb0-130">Obecné zásady binární aritmetického operátoru je obzvláště důležité.</span><span class="sxs-lookup"><span data-stu-id="39bb0-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="39bb0-131">Selhání před a za binární soubor `-` operátor v kombinaci s určitým možnostmi formátování, může vést k interpretaci jako unární `-`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="39bb0-132">Definice vlastního operátoru prázdnými znaky před a za</span><span class="sxs-lookup"><span data-stu-id="39bb0-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="39bb0-133">Vždy použijte prázdné znaky před a za definici operátoru:</span><span class="sxs-lookup"><span data-stu-id="39bb0-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="39bb0-134">Pro všechny vlastní operátor, který začíná `*`, budete muset přidat mezery na začátku definice, aby se zabránilo nejednoznačnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="39bb0-134">For any custom operator that starts with `*`, you'll need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="39bb0-135">Z toho důvodu se doporučuje, jednoduše uzavřete definice všechny operátory s jeden prázdný znak.</span><span class="sxs-lookup"><span data-stu-id="39bb0-135">Because of this, it's recommended that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="39bb0-136">Funkce šipky parametr prázdnými znaky před a za</span><span class="sxs-lookup"><span data-stu-id="39bb0-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="39bb0-137">Při definování podpis funkce, použijte prázdný prostor kolem `->` symbolů:</span><span class="sxs-lookup"><span data-stu-id="39bb0-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="39bb0-138">Formátování prázdných řádků</span><span class="sxs-lookup"><span data-stu-id="39bb0-138">Formatting blank lines</span></span>

* <span data-ttu-id="39bb0-139">Samostatné nejvyšší úrovně funkce a třídy definice se dvěma prázdné řádky.</span><span class="sxs-lookup"><span data-stu-id="39bb0-139">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="39bb0-140">Definice metody uvnitř třídy jsou odděleny jeden prázdný řádek.</span><span class="sxs-lookup"><span data-stu-id="39bb0-140">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="39bb0-141">Prázdné řádky může použít k oddělení skupin souvisejících funkcí (střídmě).</span><span class="sxs-lookup"><span data-stu-id="39bb0-141">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="39bb0-142">Můžete vynechat prázdné řádky mezi spoustu související one-liners (například sadu fiktivní implementace).</span><span class="sxs-lookup"><span data-stu-id="39bb0-142">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="39bb0-143">Pomocí prázdné řádky ve službě functions opatrně, označte logické oddíly.</span><span class="sxs-lookup"><span data-stu-id="39bb0-143">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="39bb0-144">Formátování komentáře</span><span class="sxs-lookup"><span data-stu-id="39bb0-144">Formatting comments</span></span>

<span data-ttu-id="39bb0-145">Obecně přednost více komentářů dvěma lomítky přes ML – vizuální styl blok komentáře.</span><span class="sxs-lookup"><span data-stu-id="39bb0-145">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="39bb0-146">Vložené komentáře by měl velké první písmeno první písmeno.</span><span class="sxs-lookup"><span data-stu-id="39bb0-146">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="39bb0-147">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="39bb0-147">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="39bb0-148">Hodnoty vázané na třídu, vázané na výrazu a vzor vázané a funkcí pomocí camelCase</span><span class="sxs-lookup"><span data-stu-id="39bb0-148">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="39bb0-149">Je běžné a přijatou F# stylu camelCase používat pro všechny názvy vázaný jako lokální proměnné nebo v porovnávání vzorů a definice funkce.</span><span class="sxs-lookup"><span data-stu-id="39bb0-149">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="39bb0-150">Místně vázaných funkcí v třídách použít i pro camelCase.</span><span class="sxs-lookup"><span data-stu-id="39bb0-150">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="39bb0-151">Pro veřejné funkce vázané na modul pomocí camelCase</span><span class="sxs-lookup"><span data-stu-id="39bb0-151">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="39bb0-152">Pokud modul vázané funkce je součástí veřejného rozhraní API, měla by používat camelCase:</span><span class="sxs-lookup"><span data-stu-id="39bb0-152">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="39bb0-153">Pomocí camelCase pro interní a privátní hodnoty vázané na modul a funkce</span><span class="sxs-lookup"><span data-stu-id="39bb0-153">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="39bb0-154">Pomocí camelCase pro soukromé hodnoty vázané na modul, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="39bb0-154">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="39bb0-155">Funkce ad hoc ve skriptech</span><span class="sxs-lookup"><span data-stu-id="39bb0-155">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="39bb0-156">Hodnoty, které tvoří vnitřní implementace modulem nebo typem.</span><span class="sxs-lookup"><span data-stu-id="39bb0-156">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="39bb0-157">Pro parametry pomocí camelCase</span><span class="sxs-lookup"><span data-stu-id="39bb0-157">Use camelCase for parameters</span></span>

<span data-ttu-id="39bb0-158">Všechny parametry používali camelCase v souladu s zásady vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="39bb0-158">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="39bb0-159">Pro moduly pomocí PascalCase</span><span class="sxs-lookup"><span data-stu-id="39bb0-159">Use PascalCase for modules</span></span>

<span data-ttu-id="39bb0-160">Všechny moduly (nejvyšší úrovně, interní, privátní, vnořené) používejte PascalCase.</span><span class="sxs-lookup"><span data-stu-id="39bb0-160">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="39bb0-161">Pomocí PascalCase u deklarace typu, členů a popisků</span><span class="sxs-lookup"><span data-stu-id="39bb0-161">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="39bb0-162">Třídy, rozhraní, struktury, výčty, delegáti, záznamů a rozlišovaná sjednocení by měl název pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="39bb0-162">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="39bb0-163">Členy v rámci typů a popisků záznamů a rozlišovaná sjednocení také používali PascalCase.</span><span class="sxs-lookup"><span data-stu-id="39bb0-163">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="39bb0-164">Pro konstruktory, které jsou přirozené pro .NET pomocí PascalCase</span><span class="sxs-lookup"><span data-stu-id="39bb0-164">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="39bb0-165">Obory názvů, výjimky, události a projekt /`.dll` názvy mělo používat taky pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="39bb0-165">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="39bb0-166">Nejen tím neodstraní, ale využití z jiných jazyků .NET působit přirozeně více uživatelům, je také v souladu s konvence pojmenování .NET, které budete pravděpodobně dojde k.</span><span class="sxs-lookup"><span data-stu-id="39bb0-166">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="39bb0-167">Vyhněte se podtržítka v názvech</span><span class="sxs-lookup"><span data-stu-id="39bb0-167">Avoid underscores in names</span></span>

<span data-ttu-id="39bb0-168">V minulosti některé F# knihovny použili v názvech podtržítka.</span><span class="sxs-lookup"><span data-stu-id="39bb0-168">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="39bb0-169">Ale to je přijat už široce, částečně proto, že je v konfliktu s zásady vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="39bb0-169">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="39bb0-170">Nicméně některé F# programátoři používají podtržítka silně, částečně z historických důvodů a odolnosti proti chybám a ohledu je důležité.</span><span class="sxs-lookup"><span data-stu-id="39bb0-170">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="39bb0-171">Nezapomínejte, že styl je často disliked jinými uživateli, kteří rozhodnout o tom, jestli ji používat.</span><span class="sxs-lookup"><span data-stu-id="39bb0-171">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="39bb0-172">Některé výjimky zahrnuje spolupráce s nativními komponentami, kde jsou velmi běžné podtržítka.</span><span class="sxs-lookup"><span data-stu-id="39bb0-172">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="39bb0-173">Pomocí standardních F# operátory</span><span class="sxs-lookup"><span data-stu-id="39bb0-173">Use standard F# operators</span></span>

<span data-ttu-id="39bb0-174">Následující operátory jsou definovány v F# standardní knihovny a musí být použity místo definování ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="39bb0-174">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="39bb0-175">Jak je obvykle, aby byl kód čitelnější a idiomatickou, doporučuje se použití těchto operátorů.</span><span class="sxs-lookup"><span data-stu-id="39bb0-175">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="39bb0-176">Vývojáři a má zázemí ve OCaml nebo jiných funkcionálním programovacím jazyce může být na různých idiomy zvyklí.</span><span class="sxs-lookup"><span data-stu-id="39bb0-176">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="39bb0-177">Následující seznam shrnuje doporučené F# operátory.</span><span class="sxs-lookup"><span data-stu-id="39bb0-177">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="39bb0-178">Použijte předponu syntaxi pro obecné typy (`Foo<T>`) před syntaxe přípony (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="39bb0-178">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="39bb0-179">F#dědí obě přípony ML styl pojmenování obecných typů (například `int list`) stejně jako předpona .NET stylu (například `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="39bb0-179">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="39bb0-180">Preferovat stylu .NET, s výjimkou čtyři konkrétní typy:</span><span class="sxs-lookup"><span data-stu-id="39bb0-180">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="39bb0-181">Pro F# seznamy, použijte příponový tvar: `int list` spíše než `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-181">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="39bb0-182">Pro F# možnosti použít příponový tvar: `int option` spíše než `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-182">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="39bb0-183">Pro F# pole, použijte syntaxi název `int[]` spíše než `int array` nebo `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-183">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="39bb0-184">Odkazové buňky pomocí `int ref` spíše než `ref<int>` nebo `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-184">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="39bb0-185">Pro všechny ostatní typy použijte prefixová podoba.</span><span class="sxs-lookup"><span data-stu-id="39bb0-185">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="39bb0-186">Formátování řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="39bb0-186">Formatting tuples</span></span>

<span data-ttu-id="39bb0-187">Vytvoření instance řazené kolekce členů musí být v závorce a oddělovací čárky v rámci by měl následovat jednu mezeru, například: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-187">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="39bb0-188">Běžně přijetím vynechejte závorky v porovnávání vzorů řazených kolekcí členů:</span><span class="sxs-lookup"><span data-stu-id="39bb0-188">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="39bb0-189">Formátování rozlišované deklarace sjednocení</span><span class="sxs-lookup"><span data-stu-id="39bb0-189">Formatting discriminated union declarations</span></span>

<span data-ttu-id="39bb0-190">Odsadit `|` v definici typu 4 mezerami:</span><span class="sxs-lookup"><span data-stu-id="39bb0-190">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="39bb0-191">Formátování rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="39bb0-191">Formatting discriminated unions</span></span>

<span data-ttu-id="39bb0-192">Instance rozlišovaná sjednocení, které rozdělit mezi několik řádků by měla poskytnout dat obsažených nový obor s odsazením:</span><span class="sxs-lookup"><span data-stu-id="39bb0-192">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="39bb0-193">Pravá závorka může být také na nový řádek:</span><span class="sxs-lookup"><span data-stu-id="39bb0-193">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="39bb0-194">Formátování záznam deklarace</span><span class="sxs-lookup"><span data-stu-id="39bb0-194">Formatting record declarations</span></span>

<span data-ttu-id="39bb0-195">Odsadit `{` v typu definice 4 mezery a spustit v seznamu polí na stejný řádek:</span><span class="sxs-lookup"><span data-stu-id="39bb0-195">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="39bb0-196">Uvedení na stejném řádku a pravou token na nový řádek levou token je také dobře, ale mějte na paměti, že budete muset použít [podrobná syntaxe](../language-reference/verbose-syntax.md) se členy ( `with` – klíčové slovo):</span><span class="sxs-lookup"><span data-stu-id="39bb0-196">Placing the opening token on the same line and the closing token on a new line is also fine, but be aware that you need to use the [verbose syntax](../language-reference/verbose-syntax.md) to define members (the `with` keyword):</span></span>

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address: string
    City: string
    Zip: string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
```

## <a name="formatting-records"></a><span data-ttu-id="39bb0-197">Formátování záznamů</span><span class="sxs-lookup"><span data-stu-id="39bb0-197">Formatting records</span></span>

<span data-ttu-id="39bb0-198">Krátký záznamy je možné psát v jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="39bb0-198">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="39bb0-199">Záznamy, které jsou delší používali nové řádky popisků:</span><span class="sxs-lookup"><span data-stu-id="39bb0-199">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="39bb0-200">Uvedení na stejném řádku a pravou token na nový řádek levou token je také pořádku:</span><span class="sxs-lookup"><span data-stu-id="39bb0-200">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

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

<span data-ttu-id="39bb0-201">Stejná pravidla platí i pro seznam a pole prvků.</span><span class="sxs-lookup"><span data-stu-id="39bb0-201">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="39bb0-202">Formátování seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="39bb0-202">Formatting lists and arrays</span></span>

<span data-ttu-id="39bb0-203">Zápis `x :: l` s mezery kolem `::` – operátor (`::` je operátor vpony, proto obklopené mezerami) a `[1; 2; 3]` (`;` je oddělovač, proto následovanými mezerou).</span><span class="sxs-lookup"><span data-stu-id="39bb0-203">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="39bb0-204">Používejte vždy alespoň jednu mezeru mezi dva odlišné operátory podobném složenou závorku.</span><span class="sxs-lookup"><span data-stu-id="39bb0-204">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="39bb0-205">Například, ponechte mezeru mezi `[` a `{`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-205">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="39bb0-206">Seznamy a pole, která se rozdělit mezi několik řádků postupujte stejně jako záznamy podobné pravidlo:</span><span class="sxs-lookup"><span data-stu-id="39bb0-206">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

## <a name="formatting-if-expressions"></a><span data-ttu-id="39bb0-207">Formátování if výrazy</span><span class="sxs-lookup"><span data-stu-id="39bb0-207">Formatting if expressions</span></span>

<span data-ttu-id="39bb0-208">Odsazení podmíněné výrazy závisí na velikosti výrazy, které společně tvoří.</span><span class="sxs-lookup"><span data-stu-id="39bb0-208">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="39bb0-209">Pokud `cond`, `e1` a `e2` jsou krátký, napište jednoduše na jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="39bb0-209">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="39bb0-210">Pokud `cond`, `e1` nebo `e2` delší dobu, ale ne více řádky:</span><span class="sxs-lookup"><span data-stu-id="39bb0-210">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="39bb0-211">Pokud je některý z výrazů více řádky:</span><span class="sxs-lookup"><span data-stu-id="39bb0-211">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="39bb0-212">Více podmíněné výrazy s `elif` a `else` odsazeny ve stejném oboru jako `if`:</span><span class="sxs-lookup"><span data-stu-id="39bb0-212">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="39bb0-213">Odpovídající vzor konstrukce</span><span class="sxs-lookup"><span data-stu-id="39bb0-213">Pattern matching constructs</span></span>

<span data-ttu-id="39bb0-214">Použití `|` pro každou klauzuli shoda s žádné odsazení.</span><span class="sxs-lookup"><span data-stu-id="39bb0-214">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="39bb0-215">Pokud výraz je krátký, můžete použít jeden řádek, pokud každý dílčí výraz je také jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="39bb0-215">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="39bb0-216">Výraz na pravé straně porovnávání vzorů šipky je příliš velká, tento soubor přesune do následujícího řádku, odsazený jeden krok z `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-216">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="39bb0-217">Vzorovou shodu anonymní funkcí, které se spouští podle `function`, obecně by neměl příliš daleko odsazení.</span><span class="sxs-lookup"><span data-stu-id="39bb0-217">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="39bb0-218">Například následující odsazení jeden rozsah je v pořádku:</span><span class="sxs-lookup"><span data-stu-id="39bb0-218">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="39bb0-219">Porovnávání vzorů v funkce určené `let` nebo `let rec` po spuštění by měl být odsazený 4 mezer `let`i v případě `function` – klíčové slovo se používá:</span><span class="sxs-lookup"><span data-stu-id="39bb0-219">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="39bb0-220">Nedoporučujeme zarovnání šipky.</span><span class="sxs-lookup"><span data-stu-id="39bb0-220">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="39bb0-221">Formátování try / with výrazy</span><span class="sxs-lookup"><span data-stu-id="39bb0-221">Formatting try/with expressions</span></span>

<span data-ttu-id="39bb0-222">Vzorec pro porovnávání na typ výjimky by měly odsazena na stejné úrovni jako `with`.</span><span class="sxs-lookup"><span data-stu-id="39bb0-222">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="39bb0-223">Formátování aplikace parametr – funkce</span><span class="sxs-lookup"><span data-stu-id="39bb0-223">Formatting function parameter application</span></span>

<span data-ttu-id="39bb0-224">Obecně platí většina aplikací parametr funkce se provádí na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="39bb0-224">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="39bb0-225">Pokud budete chtít použít parametry pro funkci na novém řádku, odsazení je jeden obor.</span><span class="sxs-lookup"><span data-stu-id="39bb0-225">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="39bb0-226">Podle stejných pravidel platí pro výrazy lambda jako argumenty funkce.</span><span class="sxs-lookup"><span data-stu-id="39bb0-226">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="39bb0-227">Pokud hlavní část výrazu lambda, text může mít jiný řádek odsazeny o jeden obor</span><span class="sxs-lookup"><span data-stu-id="39bb0-227">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="39bb0-228">Nicméně pokud hlavní část výrazu lambda je více než jeden řádek, vezměte v úvahu řešení ho do samostatné funkce a nenechat konstrukci Víceřádkový použít jako jediný argument pro funkci.</span><span class="sxs-lookup"><span data-stu-id="39bb0-228">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="39bb0-229">Formátování infixové operátory</span><span class="sxs-lookup"><span data-stu-id="39bb0-229">Formatting infix operators</span></span>

<span data-ttu-id="39bb0-230">Samostatné operátory mezerami.</span><span class="sxs-lookup"><span data-stu-id="39bb0-230">Separate operators by spaces.</span></span> <span data-ttu-id="39bb0-231">Ze zřejmých výjimky z tohoto pravidla jsou `!` a `.` operátory.</span><span class="sxs-lookup"><span data-stu-id="39bb0-231">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="39bb0-232">Výrazy vpony je OK lineup na stejný sloupec:</span><span class="sxs-lookup"><span data-stu-id="39bb0-232">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="39bb0-233">Formátování operátorů kanálů</span><span class="sxs-lookup"><span data-stu-id="39bb0-233">Formatting pipeline operators</span></span>

<span data-ttu-id="39bb0-234">Kanál `|>` operátory by měly patřit pod pracují na výrazy.</span><span class="sxs-lookup"><span data-stu-id="39bb0-234">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="39bb0-235">Formátovací moduly</span><span class="sxs-lookup"><span data-stu-id="39bb0-235">Formatting modules</span></span>

<span data-ttu-id="39bb0-236">Kód v místním modulu musí odsazený relativně k modulu, ale neměli odsazeny kódu v nejvyšší úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="39bb0-236">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="39bb0-237">Prvky Namespace, není potřeba odsazeny.</span><span class="sxs-lookup"><span data-stu-id="39bb0-237">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="39bb0-238">Formátování objektové výrazy a rozhraní</span><span class="sxs-lookup"><span data-stu-id="39bb0-238">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="39bb0-239">Objektové výrazy a rozhraní zarovnání stejným způsobem s `member` se odsazena po 4 mezer.</span><span class="sxs-lookup"><span data-stu-id="39bb0-239">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="39bb0-240">Formátování prázdných ve výrazech</span><span class="sxs-lookup"><span data-stu-id="39bb0-240">Formatting white space in expressions</span></span>

<span data-ttu-id="39bb0-241">Vyhněte se nadbytečné prázdné místo v F# výrazy.</span><span class="sxs-lookup"><span data-stu-id="39bb0-241">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="39bb0-242">Pojmenované argumenty neměli také místa okolo `=`:</span><span class="sxs-lookup"><span data-stu-id="39bb0-242">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="39bb0-243">Atributy formátování</span><span class="sxs-lookup"><span data-stu-id="39bb0-243">Formatting attributes</span></span>

<span data-ttu-id="39bb0-244">[Atributy](../language-reference/attributes.md) jsou umístěny nad konstrukce:</span><span class="sxs-lookup"><span data-stu-id="39bb0-244">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="39bb0-245">Formátování atributy pro parametry</span><span class="sxs-lookup"><span data-stu-id="39bb0-245">Formatting attributes on parameters</span></span>

<span data-ttu-id="39bb0-246">Atributy mohou být také míst na parametry.</span><span class="sxs-lookup"><span data-stu-id="39bb0-246">Attributes can also be places on parameters.</span></span> <span data-ttu-id="39bb0-247">V takovém případě umístěte klikněte na stejném řádku jako parametr a před názvem:</span><span class="sxs-lookup"><span data-stu-id="39bb0-247">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="39bb0-248">Formátování více atributů</span><span class="sxs-lookup"><span data-stu-id="39bb0-248">Formatting multiple attributes</span></span>

<span data-ttu-id="39bb0-249">Při více atributy jsou použity konstrukce, která se nejedná o parametr, by měla být umístěna tak, že je jeden atribut na řádek:</span><span class="sxs-lookup"><span data-stu-id="39bb0-249">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="39bb0-250">Při použití parametru, musí být na stejném řádku a oddělené `;` oddělovač.</span><span class="sxs-lookup"><span data-stu-id="39bb0-250">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="39bb0-251">Formátování literály</span><span class="sxs-lookup"><span data-stu-id="39bb0-251">Formatting literals</span></span>

<span data-ttu-id="39bb0-252">[F#literály](../language-reference/literals.md) pomocí `Literal` atribut by měl by měl umístit atribut na samostatném řádku a pomocí camelCase pojmenování:</span><span class="sxs-lookup"><span data-stu-id="39bb0-252">[F# literals](../language-reference/literals.md) using the `Literal` attribute should should place the attribute on its own line and use camelCase naming:</span></span>

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="39bb0-253">Předejde atribut na stejný řádek jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="39bb0-253">Avoid placing the attribute on the same line as the value.</span></span>
