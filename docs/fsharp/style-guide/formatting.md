---
title: Pravidla formátování kódu F#
description: 'Přečtěte si pokyny pro formátování kódu F #.'
ms.date: 11/04/2019
ms.openlocfilehash: dc871b0a8461ed93550ab02cc2c66b143285a3e3
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720147"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="ddb71-103">Pravidla formátování kódu F#</span><span class="sxs-lookup"><span data-stu-id="ddb71-103">F# code formatting guidelines</span></span>

<span data-ttu-id="ddb71-104">Tento článek obsahuje pokyny, jak formátovat kód tak, aby kód F # byl:</span><span class="sxs-lookup"><span data-stu-id="ddb71-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="ddb71-105">Čitelnější</span><span class="sxs-lookup"><span data-stu-id="ddb71-105">More legible</span></span>
* <span data-ttu-id="ddb71-106">V souladu s konvencemi použitými nástroji formátování v aplikaci Visual Studio a dalšími editory</span><span class="sxs-lookup"><span data-stu-id="ddb71-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="ddb71-107">Podobně jako u jiného kódu online</span><span class="sxs-lookup"><span data-stu-id="ddb71-107">Similar to other code online</span></span>

<span data-ttu-id="ddb71-108">Tyto pokyny jsou založené na [komplexní příručce k konvencím formátování F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) podle [Anh-Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="ddb71-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="ddb71-109">Obecná pravidla pro odsazení</span><span class="sxs-lookup"><span data-stu-id="ddb71-109">General rules for indentation</span></span>

<span data-ttu-id="ddb71-110">Jazyk F # ve výchozím nastavení používá významné prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="ddb71-110">F# uses significant white space by default.</span></span> <span data-ttu-id="ddb71-111">Následující pokyny jsou určené k tomu, aby poskytovaly pokyny, jak juggle některé problémy, které může způsobit.</span><span class="sxs-lookup"><span data-stu-id="ddb71-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="ddb71-112">Použití mezer</span><span class="sxs-lookup"><span data-stu-id="ddb71-112">Using spaces</span></span>

<span data-ttu-id="ddb71-113">Pokud je požadováno odsazení, je nutné použít mezery, nikoli tabulátory.</span><span class="sxs-lookup"><span data-stu-id="ddb71-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="ddb71-114">Vyžaduje se aspoň jedna mezera.</span><span class="sxs-lookup"><span data-stu-id="ddb71-114">At least one space is required.</span></span> <span data-ttu-id="ddb71-115">Vaše organizace může vytvořit standardy kódování, které určují počet mezer, které se mají použít pro odsazení; dva, tři nebo čtyři mezery odsazení na každé úrovni, kde dochází k odsazení, je typický.</span><span class="sxs-lookup"><span data-stu-id="ddb71-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="ddb71-116">**Pro odsazení doporučujeme čtyři mezery.**</span><span class="sxs-lookup"><span data-stu-id="ddb71-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="ddb71-117">To znamená, že odsazení programů je subjektivní.</span><span class="sxs-lookup"><span data-stu-id="ddb71-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="ddb71-118">Variace jsou OK, ale první pravidlo, které byste měli dodržovat, je *konzistence odsazení*.</span><span class="sxs-lookup"><span data-stu-id="ddb71-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="ddb71-119">Vyberte všeobecně přijatý styl odsazení a používejte ho systematicky v rámci vašeho základu kódu.</span><span class="sxs-lookup"><span data-stu-id="ddb71-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="ddb71-120">Formátování mezer</span><span class="sxs-lookup"><span data-stu-id="ddb71-120">Formatting white space</span></span>

<span data-ttu-id="ddb71-121">Jazyk F # rozlišuje prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="ddb71-121">F# is white space sensitive.</span></span> <span data-ttu-id="ddb71-122">I když je většina sémantických míst z prázdných znaků krytá správným odsazením, je potřeba zvážit několik dalších věcí.</span><span class="sxs-lookup"><span data-stu-id="ddb71-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="ddb71-123">Formátování operátorů v aritmetických výrazech</span><span class="sxs-lookup"><span data-stu-id="ddb71-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="ddb71-124">Vždy používat prázdné znaky kolem binárních aritmetických výrazů:</span><span class="sxs-lookup"><span data-stu-id="ddb71-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="ddb71-125">Unární `-` operátory by vždy měly hned za hodnotou, že se jedná o negaci:</span><span class="sxs-lookup"><span data-stu-id="ddb71-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="ddb71-126">Přidání prázdného znaku poté, co `-` operátor může způsobit nejasnost pro ostatní.</span><span class="sxs-lookup"><span data-stu-id="ddb71-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="ddb71-127">V souhrnu je důležité vždycky:</span><span class="sxs-lookup"><span data-stu-id="ddb71-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="ddb71-128">Obklopit binární operátory s prázdným znakem</span><span class="sxs-lookup"><span data-stu-id="ddb71-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="ddb71-129">Po unárním operátoru nikdy nemá koncový znak mezer.</span><span class="sxs-lookup"><span data-stu-id="ddb71-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="ddb71-130">Základní pravidlo pro binární aritmetické operátory je obzvláště důležité.</span><span class="sxs-lookup"><span data-stu-id="ddb71-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="ddb71-131">Neúspěšné vytvoření binárního `-` operátoru při kombinaci s určitými možnostmi formátování by mohlo vést k interpretaci jako unárního `-` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="ddb71-132">Ohraničení vlastní definice operátoru s mezerami</span><span class="sxs-lookup"><span data-stu-id="ddb71-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="ddb71-133">Pro obklopení definice operátoru vždy použít prázdné znaky:</span><span class="sxs-lookup"><span data-stu-id="ddb71-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="ddb71-134">Pro libovolný vlastní operátor, který začíná `*` a, který má více než jeden znak, je nutné přidat prázdné znaky na začátek definice, aby nedocházelo k nejednoznačnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ddb71-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="ddb71-135">Z tohoto důvodu doporučujeme jednoduše obklopit definice všech operátorů jediným prázdným znakem.</span><span class="sxs-lookup"><span data-stu-id="ddb71-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="ddb71-136">Obklopit šipky parametrů funkce s mezerami</span><span class="sxs-lookup"><span data-stu-id="ddb71-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="ddb71-137">Při definování signatury funkce použijte prázdné znaky kolem `->` symbolu:</span><span class="sxs-lookup"><span data-stu-id="ddb71-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="ddb71-138">Uzavřít argumenty funkce s mezerami</span><span class="sxs-lookup"><span data-stu-id="ddb71-138">Surround function arguments with white space</span></span>

<span data-ttu-id="ddb71-139">Při definování funkce použijte prázdné znaky kolem každého argumentu.</span><span class="sxs-lookup"><span data-stu-id="ddb71-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a><span data-ttu-id="ddb71-140">Umístit parametry na nový řádek pro dlouhé definice</span><span class="sxs-lookup"><span data-stu-id="ddb71-140">Place parameters on a new line for long definitions</span></span>

<span data-ttu-id="ddb71-141">Pokud máte hodně dlouhé definice funkce, umístěte parametry na nové řádky a odsadíte je tak, aby odpovídaly úrovni odsazení následného parametru.</span><span class="sxs-lookup"><span data-stu-id="ddb71-141">If you have a very long function definition, place the parameters on new lines and indent them to match the indentation level of the subsequent parameter.</span></span>

```fsharp
module M =
    let LongFunctionWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        =
        // ... the body of the method follows
```

<span data-ttu-id="ddb71-142">To platí také pro členy, konstruktory a parametry pomocí řazených kolekcí členů:</span><span class="sxs-lookup"><span data-stu-id="ddb71-142">This also applies to members, constructors, and parameters using tuples:</span></span>

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method

type TC(aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

<span data-ttu-id="ddb71-143">Pokud jsou parametry currified nebo existuje explicitní anotace návratového typu, je vhodnější umístit `=` znak na nový řádek:</span><span class="sxs-lookup"><span data-stu-id="ddb71-143">If the parameters are currified or there's an explicit return type annotation, it is preferable to place the `=` character on a new line:</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                            : AReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                =
        // ... the body of the method
```

<span data-ttu-id="ddb71-144">Toto je způsob, jak se vyhnout příliš dlouhým řádkům (v případě, že návratový typ může mít dlouhý název) a že při přidávání parametrů je menší ŠKODA na řádku.</span><span class="sxs-lookup"><span data-stu-id="ddb71-144">This is a way to avoid too long lines (in case return type might have long name) and have less line-damage when adding parameters.</span></span>

### <a name="type-annotations"></a><span data-ttu-id="ddb71-145">Anotace typu</span><span class="sxs-lookup"><span data-stu-id="ddb71-145">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="ddb71-146">Poznámky k typu argumentu funkce pravého panelu</span><span class="sxs-lookup"><span data-stu-id="ddb71-146">Right-pad function argument type annotations</span></span>

<span data-ttu-id="ddb71-147">Při definování argumentů s anotacemi typu použijte prázdné místo za `:` symbolem:</span><span class="sxs-lookup"><span data-stu-id="ddb71-147">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="ddb71-148">Obklopit anotace návratového typu s prázdným znakem</span><span class="sxs-lookup"><span data-stu-id="ddb71-148">Surround return type annotations with white space</span></span>

<span data-ttu-id="ddb71-149">V anotaci nebo typu hodnoty (návratový typ v případě funkce) použijte prázdné znaky před a za `:` symbolem:</span><span class="sxs-lookup"><span data-stu-id="ddb71-149">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="ddb71-150">Formátování prázdných řádků</span><span class="sxs-lookup"><span data-stu-id="ddb71-150">Formatting blank lines</span></span>

* <span data-ttu-id="ddb71-151">Samostatné definice funkcí a tříd na nejvyšší úrovni se dvěma prázdnými řádky.</span><span class="sxs-lookup"><span data-stu-id="ddb71-151">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="ddb71-152">Definice metod uvnitř třídy jsou oddělené jedním prázdným řádkem.</span><span class="sxs-lookup"><span data-stu-id="ddb71-152">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="ddb71-153">Můžete použít nadbytečné prázdné řádky k oddělení skupin souvisejících funkcí.</span><span class="sxs-lookup"><span data-stu-id="ddb71-153">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="ddb71-154">Prázdné řádky mohou být vynechány mezi svazků souvisejících LINERS (například sadou fiktivních implementací).</span><span class="sxs-lookup"><span data-stu-id="ddb71-154">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="ddb71-155">Používejte prázdné řádky ve funkcích a používejte k označení logických oddílů.</span><span class="sxs-lookup"><span data-stu-id="ddb71-155">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="ddb71-156">Formátování komentářů</span><span class="sxs-lookup"><span data-stu-id="ddb71-156">Formatting comments</span></span>

<span data-ttu-id="ddb71-157">Obecně preferovat více komentářů s dvojitým lomítkem přes komentáře bloku ve stylu ML.</span><span class="sxs-lookup"><span data-stu-id="ddb71-157">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="ddb71-158">Vložené komentáře by měly být velkými písmeny první písmeno.</span><span class="sxs-lookup"><span data-stu-id="ddb71-158">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="ddb71-159">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="ddb71-159">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="ddb71-160">Použití camelCase pro hodnoty a funkce vázané na výrazy vázané na výrazy a vzory</span><span class="sxs-lookup"><span data-stu-id="ddb71-160">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="ddb71-161">Je běžný a přijatý styl F # pro použití camelCase pro všechny názvy svázané jako lokální proměnné nebo v porovnání vzorů a definicích funkcí.</span><span class="sxs-lookup"><span data-stu-id="ddb71-161">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="ddb71-162">Místně vázané funkce ve třídách by měly také používat camelCase.</span><span class="sxs-lookup"><span data-stu-id="ddb71-162">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="ddb71-163">Použití camelCase pro veřejné funkce vázané na modul</span><span class="sxs-lookup"><span data-stu-id="ddb71-163">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="ddb71-164">Když je funkce vázaná na modul součástí veřejného rozhraní API, měla by používat camelCase:</span><span class="sxs-lookup"><span data-stu-id="ddb71-164">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="ddb71-165">Použití camelCase pro interní a privátní hodnoty a funkce vázané na modul</span><span class="sxs-lookup"><span data-stu-id="ddb71-165">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="ddb71-166">Použijte camelCase pro hodnoty vázané na modul, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="ddb71-166">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="ddb71-167">Funkce ad hoc ve skriptech</span><span class="sxs-lookup"><span data-stu-id="ddb71-167">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="ddb71-168">Hodnoty, které tvoří interní implementaci modulu nebo typu</span><span class="sxs-lookup"><span data-stu-id="ddb71-168">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="ddb71-169">Použití camelCase pro parametry</span><span class="sxs-lookup"><span data-stu-id="ddb71-169">Use camelCase for parameters</span></span>

<span data-ttu-id="ddb71-170">Všechny parametry by měly používat camelCase v souladu s konvencemi vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="ddb71-170">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="ddb71-171">Použití PascalCase pro moduly</span><span class="sxs-lookup"><span data-stu-id="ddb71-171">Use PascalCase for modules</span></span>

<span data-ttu-id="ddb71-172">Všechny moduly (na nejvyšší úrovni, interní, privátní, vnořený) by měly používat PascalCase.</span><span class="sxs-lookup"><span data-stu-id="ddb71-172">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="ddb71-173">Použití PascalCase pro deklarace typu, členy a popisky</span><span class="sxs-lookup"><span data-stu-id="ddb71-173">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="ddb71-174">Třídy, rozhraní, struktury, výčty, delegáti, záznamy a rozlišené sjednocení by měly být pojmenovány pomocí PascalCase.</span><span class="sxs-lookup"><span data-stu-id="ddb71-174">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="ddb71-175">Členy v rámci typů a popisků pro záznamy a rozlišené sjednocení by měly také používat PascalCase.</span><span class="sxs-lookup"><span data-stu-id="ddb71-175">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="ddb71-176">Použití PascalCase pro vnitřní konstrukce pro .NET</span><span class="sxs-lookup"><span data-stu-id="ddb71-176">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="ddb71-177">PascalCase musí používat i obory názvů, výjimky, události a názvy projektů a `.dll` názvů.</span><span class="sxs-lookup"><span data-stu-id="ddb71-177">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="ddb71-178">Nejenom to dělá, že se spotřeba z jiných jazyků .NET u spotřebitelů stane přirozenější, je taky v souladu se zásadami vytváření názvů .NET, u kterých se pravděpodobně setkáte.</span><span class="sxs-lookup"><span data-stu-id="ddb71-178">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="ddb71-179">Vyhněte se podtržítkům v názvech</span><span class="sxs-lookup"><span data-stu-id="ddb71-179">Avoid underscores in names</span></span>

<span data-ttu-id="ddb71-180">Historické knihovny F # v minulosti používaly v názvech podtržítka.</span><span class="sxs-lookup"><span data-stu-id="ddb71-180">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="ddb71-181">Nejedná se ale o již široce přijatelné částečně, protože je v konfliktu se zásadami vytváření názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="ddb71-181">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="ddb71-182">V takovém případě některé programátory F # používají v historických případech silně podtržítka a jsou důležité tolerance a respektování.</span><span class="sxs-lookup"><span data-stu-id="ddb71-182">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="ddb71-183">Uvědomte si však, že styl je často nepodobný jiným uživatelům, kteří mají možnost zvolit, zda se má použít.</span><span class="sxs-lookup"><span data-stu-id="ddb71-183">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="ddb71-184">Jedna výjimka zahrnuje spolupráci s nativními komponentami, kde jsou podtržítka společná.</span><span class="sxs-lookup"><span data-stu-id="ddb71-184">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="ddb71-185">Použití standardních operátorů jazyka F #</span><span class="sxs-lookup"><span data-stu-id="ddb71-185">Use standard F# operators</span></span>

<span data-ttu-id="ddb71-186">Následující operátory jsou definovány ve standardní knihovně F # a měly by být použity namísto definování ekvivalentů.</span><span class="sxs-lookup"><span data-stu-id="ddb71-186">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="ddb71-187">Použití těchto operátorů se doporučuje, protože je v úmyslu zvýšit čitelnost a idiomatickou kódu.</span><span class="sxs-lookup"><span data-stu-id="ddb71-187">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="ddb71-188">Vývojáři s pozadím v OCaml nebo jiným funkčním programovacím jazykem můžou být zvyklí na různé idiomy.</span><span class="sxs-lookup"><span data-stu-id="ddb71-188">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="ddb71-189">Následující seznam shrnuje doporučené operátory jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="ddb71-189">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="ddb71-190">Použijte syntaxi prefixu pro obecné typy ( `Foo<T>` ) v Předvolby na syntaxi přípony ( `T Foo` ).</span><span class="sxs-lookup"><span data-stu-id="ddb71-190">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="ddb71-191">Jazyk F # dědí jak styl přípona ML generických typů (například), `int list` tak i prefixový styl .NET (například `list<int>` ).</span><span class="sxs-lookup"><span data-stu-id="ddb71-191">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="ddb71-192">Preferovat styl rozhraní .NET, s výjimkou pěti specifických typů:</span><span class="sxs-lookup"><span data-stu-id="ddb71-192">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="ddb71-193">V seznamech F # použijte příponový tvar `int list` namísto `list<int>` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-193">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="ddb71-194">V případě možností jazyka F # použijte formát přípony: `int option` místo `option<int>` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-194">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="ddb71-195">Pro možnost hodnota F # použijte formát přípony: `int voption` místo `voption<int>` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-195">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="ddb71-196">V případě polí F # použijte syntaktický název `int[]` místo `int array` nebo `array<int>` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-196">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="ddb71-197">Pro referenční buňky použijte `int ref` místo `ref<int>` nebo `Ref<int>` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-197">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="ddb71-198">U všech ostatních typů použijte formulář předpony.</span><span class="sxs-lookup"><span data-stu-id="ddb71-198">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="ddb71-199">Formátování řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="ddb71-199">Formatting tuples</span></span>

<span data-ttu-id="ddb71-200">Vytvoření instance řazené kolekce členů by mělo být v závorkách a oddělovači v ní by měl následovat jedna mezera, například: `(1, 2)` , `(x, y, z)` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-200">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="ddb71-201">Při porovnávání vzorů řazených kolekcí členů je obvykle přijatelné vynechat závorky:</span><span class="sxs-lookup"><span data-stu-id="ddb71-201">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="ddb71-202">V případě, že řazená kolekce členů je návratovou hodnotou funkce, je také obvykle přijato, aby se vynechal závorky:</span><span class="sxs-lookup"><span data-stu-id="ddb71-202">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="ddb71-203">V souhrnu dáváte přednost vytváření instancí řazené kolekce členů v závorkách, ale při použití řazených kolekcí členů nebo návratové hodnoty je považována za jemné, aby nedošlo k závorce.</span><span class="sxs-lookup"><span data-stu-id="ddb71-203">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="ddb71-204">Formátování deklarací rozlišených sjednocení</span><span class="sxs-lookup"><span data-stu-id="ddb71-204">Formatting discriminated union declarations</span></span>

<span data-ttu-id="ddb71-205">Odsadit `|` v definici typu o čtyři mezery:</span><span class="sxs-lookup"><span data-stu-id="ddb71-205">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="ddb71-206">Formátování rozlišených sjednocení</span><span class="sxs-lookup"><span data-stu-id="ddb71-206">Formatting discriminated unions</span></span>

<span data-ttu-id="ddb71-207">Instance rozlišených sjednocení, která se rozdělí mezi více řádků, by měla obsahovat obsažená data nový obor s odsazením:</span><span class="sxs-lookup"><span data-stu-id="ddb71-207">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="ddb71-208">Pravá kulatá závorka může být také na novém řádku:</span><span class="sxs-lookup"><span data-stu-id="ddb71-208">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="ddb71-209">Formátování deklarací záznamů</span><span class="sxs-lookup"><span data-stu-id="ddb71-209">Formatting record declarations</span></span>

<span data-ttu-id="ddb71-210">Odsadit `{` v definici typu o čtyři mezery a začněte seznam polí na stejném řádku:</span><span class="sxs-lookup"><span data-stu-id="ddb71-210">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="ddb71-211">Umístění počátečního tokenu na nový řádek a uzavírací token na novém řádku je vhodnější, pokud deklarujete implementace rozhraní nebo členy záznamu:</span><span class="sxs-lookup"><span data-stu-id="ddb71-211">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="ddb71-212">Formátování záznamů</span><span class="sxs-lookup"><span data-stu-id="ddb71-212">Formatting records</span></span>

<span data-ttu-id="ddb71-213">Krátké záznamy můžete zapsat na jeden řádek:</span><span class="sxs-lookup"><span data-stu-id="ddb71-213">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="ddb71-214">Záznamy, které mají delší dobu, by měly používat nové řádky pro popisky:</span><span class="sxs-lookup"><span data-stu-id="ddb71-214">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="ddb71-215">Umístění otevřeného tokenu na nový řádek, obsah se na kartách na jednom rozsahu a uzavírací token na novém řádku je vhodnější, pokud jste:</span><span class="sxs-lookup"><span data-stu-id="ddb71-215">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="ddb71-216">Přesouvání záznamů kolem kódu s různými rozsahy odsazení</span><span class="sxs-lookup"><span data-stu-id="ddb71-216">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="ddb71-217">Rozpotrubním do funkce</span><span class="sxs-lookup"><span data-stu-id="ddb71-217">Piping them into a function</span></span>

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

<span data-ttu-id="ddb71-218">Stejná pravidla platí pro prvky list a Array.</span><span class="sxs-lookup"><span data-stu-id="ddb71-218">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="ddb71-219">Formátování výrazů záznamu kopírování a aktualizace</span><span class="sxs-lookup"><span data-stu-id="ddb71-219">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="ddb71-220">Výraz záznamu kopie a aktualizace je stále záznam, takže podobné pokyny platí.</span><span class="sxs-lookup"><span data-stu-id="ddb71-220">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="ddb71-221">Krátké výrazy se můžou vejít na jeden řádek:</span><span class="sxs-lookup"><span data-stu-id="ddb71-221">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="ddb71-222">Delší výrazy by měly používat nové řádky:</span><span class="sxs-lookup"><span data-stu-id="ddb71-222">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="ddb71-223">Stejně jako u pokynů k záznamům můžete chtít pro složené závorky vyhradit samostatné řádky a odsadit jeden obor vpravo pomocí výrazu.</span><span class="sxs-lookup"><span data-stu-id="ddb71-223">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="ddb71-224">V některých zvláštních případech, jako je například zabalení hodnoty s volitelnou bez závorek, může být nutné zachovat složené závorky na jednom řádku:</span><span class="sxs-lookup"><span data-stu-id="ddb71-224">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="ddb71-225">Formátování seznamů a polí</span><span class="sxs-lookup"><span data-stu-id="ddb71-225">Formatting lists and arrays</span></span>

<span data-ttu-id="ddb71-226">Zápis `x :: l` s mezerami kolem `::` operátoru ( `::` je vpony operátor, takže je uzavřený mezerami).</span><span class="sxs-lookup"><span data-stu-id="ddb71-226">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="ddb71-227">Seznam a pole deklarované na jednom řádku by měly mít mezeru za levou závorkou a před pravou závorkou:</span><span class="sxs-lookup"><span data-stu-id="ddb71-227">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="ddb71-228">Vždy používejte alespoň jednu mezeru mezi dvěma různými operátory podobnými závorce.</span><span class="sxs-lookup"><span data-stu-id="ddb71-228">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="ddb71-229">Například ponechte mezeru mezi `[` a a `{` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-229">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="ddb71-230">Pro seznamy nebo pole řazených kolekcí členů platí stejné zásady.</span><span class="sxs-lookup"><span data-stu-id="ddb71-230">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="ddb71-231">Seznamy a pole, které jsou rozdělené mezi více řádků, následují podobně jako záznamy:</span><span class="sxs-lookup"><span data-stu-id="ddb71-231">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="ddb71-232">A stejně jako u záznamů deklarujete levou a pravou hranatou závorku na vlastním řádku, čímž usnadníte přesouvání kódu a natékání do funkcí.</span><span class="sxs-lookup"><span data-stu-id="ddb71-232">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="ddb71-233">Při generování polí a seznamů programově je vhodnější `->` , `do ... yield` když je hodnota vždy vygenerována:</span><span class="sxs-lookup"><span data-stu-id="ddb71-233">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="ddb71-234">Starší verze jazyka F # je vyžadována `yield` v situacích, kdy mohou být data generována podmíněně, nebo mohou být vyhodnoceny po sobě jdoucí výrazy.</span><span class="sxs-lookup"><span data-stu-id="ddb71-234">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="ddb71-235">Preferovat vynechání těchto `yield` klíčových slov, pokud není nutné kompilovat se starší jazykovou verzí F #:</span><span class="sxs-lookup"><span data-stu-id="ddb71-235">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="ddb71-236">V některých případech `do...yield` může pomoci při čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="ddb71-236">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="ddb71-237">V takovém případě by se měly vzít v úvahu i tyto případy.</span><span class="sxs-lookup"><span data-stu-id="ddb71-237">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="ddb71-238">Formátování výrazů if</span><span class="sxs-lookup"><span data-stu-id="ddb71-238">Formatting if expressions</span></span>

<span data-ttu-id="ddb71-239">Odsazení podmíněných hodnot závisí na velikosti výrazů, které je tvoří.</span><span class="sxs-lookup"><span data-stu-id="ddb71-239">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="ddb71-240">Pokud `cond` `e1` jsou a `e2` jsou krátké, stačí je napsat na jeden řádek:</span><span class="sxs-lookup"><span data-stu-id="ddb71-240">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="ddb71-241">Pokud buď `cond` , `e1` nebo `e2` jsou delší, ale ne víceřádkové:</span><span class="sxs-lookup"><span data-stu-id="ddb71-241">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="ddb71-242">Pokud je některý z těchto výrazů víceřádkový:</span><span class="sxs-lookup"><span data-stu-id="ddb71-242">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="ddb71-243">Více podmíněných s `elif` a `else` jsou odsazeny ve stejném oboru jako `if` :</span><span class="sxs-lookup"><span data-stu-id="ddb71-243">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="ddb71-244">Konstrukce pro porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="ddb71-244">Pattern matching constructs</span></span>

<span data-ttu-id="ddb71-245">Použijte `|` pro každou klauzuli shody bez odsazení.</span><span class="sxs-lookup"><span data-stu-id="ddb71-245">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="ddb71-246">Pokud je výraz krátký, můžete zvážit použití jednoho řádku, pokud je každý dílčí výraz také jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="ddb71-246">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="ddb71-247">Pokud je výraz napravo od šipky porovnávání se vzorci příliš velký, přesuňte jej na následující řádek, který byl odsazen o jeden krok z `match` / `|` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-247">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="ddb71-248">Porovnávání vzorů anonymních funkcí, které začínají `function` na, by nemělo být obvykle příliš daleko odsazené.</span><span class="sxs-lookup"><span data-stu-id="ddb71-248">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="ddb71-249">Například odsazení jednoho oboru je následující:</span><span class="sxs-lookup"><span data-stu-id="ddb71-249">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="ddb71-250">Porovnávání vzorů ve funkcích definovaných nástrojem `let` nebo `let rec` by mělo být odsazené o čtyři mezery po začátku `let` , i když `function` se používá klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="ddb71-250">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="ddb71-251">Nedoporučujeme zarovnávat šipky.</span><span class="sxs-lookup"><span data-stu-id="ddb71-251">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="ddb71-252">Výrazy try/with formátování</span><span class="sxs-lookup"><span data-stu-id="ddb71-252">Formatting try/with expressions</span></span>

<span data-ttu-id="ddb71-253">Porovnávání vzorů u typu výjimky by mělo být odsazeno na stejné úrovni jako `with` .</span><span class="sxs-lookup"><span data-stu-id="ddb71-253">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="ddb71-254">Formátování aplikace parametrů funkce</span><span class="sxs-lookup"><span data-stu-id="ddb71-254">Formatting function parameter application</span></span>

<span data-ttu-id="ddb71-255">Obecně platí, že většina parametrů funkce je provedena na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="ddb71-255">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="ddb71-256">Pokud chcete použít parametry pro funkci na novém řádku, odsadit je podle jednoho oboru.</span><span class="sxs-lookup"><span data-stu-id="ddb71-256">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="ddb71-257">Stejné pokyny platí pro výrazy lambda jako argumenty funkce.</span><span class="sxs-lookup"><span data-stu-id="ddb71-257">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="ddb71-258">Pokud tělo výrazu lambda, tělo může mít jiný řádek, který je odsazený o jeden obor.</span><span class="sxs-lookup"><span data-stu-id="ddb71-258">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="ddb71-259">Pokud je však tělo výrazu lambda více než jeden řádek, zvažte jejich vyhodnocování do samostatné funkce namísto použití konstruktoru víceřádkové konstrukce jako jediného argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="ddb71-259">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="ddb71-260">Formátování operátorů vpony</span><span class="sxs-lookup"><span data-stu-id="ddb71-260">Formatting infix operators</span></span>

<span data-ttu-id="ddb71-261">Jednotlivé operátory oddělte mezerami.</span><span class="sxs-lookup"><span data-stu-id="ddb71-261">Separate operators by spaces.</span></span> <span data-ttu-id="ddb71-262">Zjevnou výjimkou z tohoto pravidla `!` jsou `.` operátory a.</span><span class="sxs-lookup"><span data-stu-id="ddb71-262">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="ddb71-263">Výrazy vpony jsou v pořádku až seznamu na stejném sloupci:</span><span class="sxs-lookup"><span data-stu-id="ddb71-263">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="ddb71-264">Formátování operátorů kanálu</span><span class="sxs-lookup"><span data-stu-id="ddb71-264">Formatting pipeline operators</span></span>

<span data-ttu-id="ddb71-265">`|>`Operátory kanálu by se měly přecházet pod výrazy, na kterých pracují.</span><span class="sxs-lookup"><span data-stu-id="ddb71-265">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="ddb71-266">Formátování modulů</span><span class="sxs-lookup"><span data-stu-id="ddb71-266">Formatting modules</span></span>

<span data-ttu-id="ddb71-267">Kód v místním modulu musí být odsazený relativně vzhledem k modulu, ale kód v modulu nejvyšší úrovně by neměl být odsazený.</span><span class="sxs-lookup"><span data-stu-id="ddb71-267">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="ddb71-268">Elementy oboru názvů není nutné odsazovat.</span><span class="sxs-lookup"><span data-stu-id="ddb71-268">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="ddb71-269">Formátování výrazů objektů a rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddb71-269">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="ddb71-270">Výrazy objektu a rozhraní by měly být zarovnány stejným způsobem jako `member` odsaditelné po čtyřech mezerách.</span><span class="sxs-lookup"><span data-stu-id="ddb71-270">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="ddb71-271">Formátování mezer ve výrazech</span><span class="sxs-lookup"><span data-stu-id="ddb71-271">Formatting white space in expressions</span></span>

<span data-ttu-id="ddb71-272">Vyhněte se nadbytečnému prázdnému místu ve výrazech jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="ddb71-272">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="ddb71-273">Pojmenované argumenty by neměly mít také prostor kolem `=` :</span><span class="sxs-lookup"><span data-stu-id="ddb71-273">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="ddb71-274">Formátování atributů</span><span class="sxs-lookup"><span data-stu-id="ddb71-274">Formatting attributes</span></span>

<span data-ttu-id="ddb71-275">[Atributy](../language-reference/attributes.md) jsou umístěné nad konstrukcí:</span><span class="sxs-lookup"><span data-stu-id="ddb71-275">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="ddb71-276">Formátování atributů u parametrů</span><span class="sxs-lookup"><span data-stu-id="ddb71-276">Formatting attributes on parameters</span></span>

<span data-ttu-id="ddb71-277">Atributy lze také umístit do parametrů.</span><span class="sxs-lookup"><span data-stu-id="ddb71-277">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="ddb71-278">V takovém případě umístěte na stejný řádek jako parametr a před název:</span><span class="sxs-lookup"><span data-stu-id="ddb71-278">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="ddb71-279">Formátování více atributů</span><span class="sxs-lookup"><span data-stu-id="ddb71-279">Formatting multiple attributes</span></span>

<span data-ttu-id="ddb71-280">Je-li pro konstrukci, která není parametrem, použita více atributů, měly by být umístěny tak, že na každý řádek je jeden atribut:</span><span class="sxs-lookup"><span data-stu-id="ddb71-280">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="ddb71-281">Při použití na parametr se musí nacházet na stejném řádku a oddělené `;` oddělovačem.</span><span class="sxs-lookup"><span data-stu-id="ddb71-281">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="ddb71-282">Formátování literálů</span><span class="sxs-lookup"><span data-stu-id="ddb71-282">Formatting literals</span></span>

<span data-ttu-id="ddb71-283">[Literály F #](../language-reference/literals.md) používající `Literal` atribut by měly umístit atribut na svůj vlastní řádek a používat PascalCase pojmenování:</span><span class="sxs-lookup"><span data-stu-id="ddb71-283">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="ddb71-284">Vyhněte se umístění atributu na stejný řádek jako hodnota.</span><span class="sxs-lookup"><span data-stu-id="ddb71-284">Avoid placing the attribute on the same line as the value.</span></span>

## <a name="formatting-computation-expression-operations"></a><span data-ttu-id="ddb71-285">Formátování operací výpočetního výrazu</span><span class="sxs-lookup"><span data-stu-id="ddb71-285">Formatting computation expression operations</span></span>

<span data-ttu-id="ddb71-286">Při vytváření vlastních operací pro [výpočetní výrazy](../language-reference/computation-expressions.md) se doporučuje používat CamelCase pojmenování:</span><span class="sxs-lookup"><span data-stu-id="ddb71-286">When creating custom operations for [computation expressions](../language-reference/computation-expressions.md) it is recommended to use camelCase naming:</span></span>

```fsharp
type MathBuilder () =
    member _.Yield _ = 0

    [<CustomOperation("addOne")>]
    member _.AddOne (state: int) =
        state + 1

    [<CustomOperation("subtractOne")>]
    member _.SubtractOne (state: int) =
        state - 1

    [<CustomOperation("divideBy")>]
    member _.DivideBy (state: int, divisor: int) =
        state / divisor

    [<CustomOperation("multiplyBy")>]
    member _.MultiplyBy (state: int, factor: int) =
        state * factor

let math = MathBuilder()

// 10
let myNumber =
    math {
        addOne
        addOne
        addOne

        subtractOne

        divideBy 2

        multiplyBy 10
    }
```

<span data-ttu-id="ddb71-287">Použitá konvence vytváření názvů by nakonec měla být řízena doménou, ve které se modeluje.</span><span class="sxs-lookup"><span data-stu-id="ddb71-287">The naming convention used should ultimately be driven by the domain being modeled.</span></span>
<span data-ttu-id="ddb71-288">Pokud je idiomatickou použít jinou konvenci, měla by se místo toho použít tato konvence.</span><span class="sxs-lookup"><span data-stu-id="ddb71-288">If it is idiomatic to use a different convention, that convention should be used instead.</span></span>
