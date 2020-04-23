---
title: Pravidla formátování kódu F#
description: Naučte se pokyny pro formátování kódu F#.
ms.date: 11/04/2019
ms.openlocfilehash: dd48380a90ee92b2c1edaaabc116fa1cd8010390
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102486"
---
# <a name="f-code-formatting-guidelines"></a>Pravidla formátování kódu F#

Tento článek nabízí pokyny pro formátování kódu tak, aby váš kód F#je:

* Čitelnější
* V souladu s konvencemi použitými nástroji pro formátování v sadě Visual Studio a dalšími editory
* Podobně jako u jiných kódů online

Tyto pokyny jsou [založeny](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) na komplexní průvodce F # Formátování konvence [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Obecná pravidla pro odsazení

F# používá významné prázdné místo ve výchozím nastavení. Následující pokyny mají poskytnout vodítko, jak žonglovat s některými výzvami, které to může vést.

### <a name="using-spaces"></a>Použití mezer

Pokud je vyžadováno odsazení, je nutné použít mezery, nikoli tabulátory. Je vyžadována alespoň jedna mezera. Vaše organizace může vytvořit standardy kódování, které určují počet mezer, které se mají použít pro odsazení; typické jsou dvě, tři nebo čtyři mezery odsazení na každé úrovni, kde dochází k odsazení.

**Doporučujeme čtyři mezery za odsazení.**

To znamená, že odsazení programů je subjektivní záležitostí. Varianty jsou v pořádku, ale první pravidlo, které byste měli dodržovat, je *konzistence odsazení*. Zvolte obecně přijímaný styl odsazení a používejte jej systematicky v celém základu kódu.

## <a name="formatting-white-space"></a>Formátování prázdného místa

F# je citlivé na prázdné místo. Ačkoli většina sémantiky z prázdného místa jsou pokryty správné odsazení, existují některé další věci, aby zvážila.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Formátování operátorů v aritmetických výrazech

Vždy používejte prázdné místo kolem binárních aritmetické výrazy:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Unární `-` operátory by měly být vždy okamžitě následovány hodnotou, kterou negující:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Přidání prázdného znaku `-` za operátor může vést k nejasnostem pro ostatní.

Stručně řečeno, je důležité vždy:

* Surround binární operátory s bílým prostorem
* Nikdy nemít koncové prázdné místo za unární operátor

Binární aritmetické operátor vodítko je obzvláště důležité. Pokud neobklopí binární `-` operátor, v kombinaci s určitými možnostmi formátování, `-`může vést k jeho interpretaci jako unární .

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Obklíčení vlastní definice operátora mezerami

K obklopení definice operátora vždy používejte prázdné místo:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Pro všechny vlastní operátor, který začíná `*` a který má více než jeden znak, je třeba přidat prázdné místo na začátek definice, aby se zabránilo nejednoznačnosti kompilátoru. Z tohoto důvodu doporučujeme jednoduše obklopit definice všech operátorů s jedním znakem prázdného místa.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Šipky parametrů prostorové funkce s bílým prostorem

Při definování podpisu funkce použijte prázdné místo `->` kolem symbolu:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Argumenty prostorové funkce s mezerami

Při definování funkce použijte prázdné místo kolem každého argumentu.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a>Umístit parametry na nový řádek pro dlouhé definice členů

Pokud máte velmi dlouhou definici člena, umístěte parametry na nové řádky a odsaďte je o jeden obor.

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

To platí i pro konstruktory:

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>Zadání poznámky

#### <a name="right-pad-function-argument-type-annotations"></a>Poznámky typu argumentu funkce pravého panelu

Při definování argumentů s textovými poznámkami použijte `:` za symbolem prázdné místo:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Surround návratové poznámky s mezerami

V anotaci let-bound funkce nebo typu hodnoty (návratový typ v případě `:` funkce) použijte prázdné místo před a za symbolem:

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>Formátování prázdných řádků

* Oddělte definice funkcí nejvyšší úrovně a tříd dvěma prázdnými řádky.
* Definice metod uvnitř třídy jsou odděleny jedním prázdným řádkem.
* Extra prázdné řádky mohou být použity (střídmě) k oddělení skupin souvisejících funkcí. Prázdné řádky mohou být vynechány mezi hromadou souvisejících one-liners (například sada fiktivní implementace).
* K označení logických oddílů používejte prázdné řádky ve funkcích střídmě.

## <a name="formatting-comments"></a>Formátování komentářů

Obecně preferují více double-lomítko komentáře přes ML-styl bloku komentáře.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Vsazené komentáře by měly první písmeno uvázat velkými písmeny.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Zásady vytváření názvů

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Použití camelCase pro hodnoty a funkce vázané na třídu, výraza a vzor

Je běžné a přijaté F# styl používat camelCase pro všechny názvy vázané jako místní proměnné nebo ve vzorových shod ách a definicích funkcí.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Místně vázané funkce ve třídách by měly také používat camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Použití camelCase pro veřejné funkce vázané na modul

Pokud je funkce vázaná na modul součástí veřejného rozhraní API, měla by používat camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Použití camelCase pro interní a soukromé modul-vázané hodnoty a funkce

Použijte camelCase pro hodnoty vázané na soukromé moduly, včetně následujících:

* Ad hoc funkce ve skriptech

* Hodnoty tvořící interní implementaci modulu nebo typu

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Použití camelCase pro parametry

Všechny parametry by měly používat camelCase v souladu s konvencemi pojmenování .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Použití PascalCase pro moduly

Všechny moduly (nejvyšší úrovně, interní, soukromé, vnořené) by měly používat PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Použití PascalCase pro deklarace typu, členy a popisky

Třídy, rozhraní, struktury, výčty, delegáty, záznamy a discriminated sjednocení by měly být pojmenovány s PascalCase. Členové v rámci typů a popisků pro záznamy a diskriminované sjednocení by také měly používat PascalCase.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Použití PascalCase pro konstrukce vnitřní .NET

Obory názvů, výjimky, události`.dll` a názvy projektů/ projektů by měly také používat PascalCase. Nejen, že to, aby spotřeba z jiných jazyků .NET cítit přirozenější pro spotřebitele, je také konzistentní s .NET konvence pojmenování, které se pravděpodobně setkáte.

### <a name="avoid-underscores-in-names"></a>Vyhněte se podtržítkům v názvech

Historicky některé knihovny F# používají podtržítka v názvech. To však již není široce přijímané, částečně proto, že je v konfliktu s konvencemi pojmenování .NET. To znamená, že někteří programátoři F# používají silně podtržítka, částečně z historických důvodů, a tolerance a respekt je důležité. Uvědomte si však, že styl je často nelíbí jiní, kteří mají na výběr o tom, zda jej použít.

Jedna výjimka zahrnuje spolupráci s nativními součástmi, kde jsou běžné podtržítka.

### <a name="use-standard-f-operators"></a>Použití standardních operátorů Jazyka F#

Následující operátory jsou definovány ve standardní knihovně F# a měly by být použity namísto definování ekvivalentů. Pomocí těchto operátorů se doporučuje, protože má tendenci kód čitelnější a idiomatický. Vývojáři se zázemím v OCamlu nebo jiném funkčním programovacím jazyce mohou být zvyklí na různé idiomy. Následující seznam shrnuje doporučené operátory F#.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Použijte syntaxi předpony`Foo<T>`pro obecné typy (`T Foo`) v předu přechodové syntaxi ( )

F# zdědí jak postfix ML styl pojmenování `int list`obecných typů (například) stejně `list<int>`jako předpona .NET styl (například). Preferujte styl .NET, s výjimkou pěti konkrétních typů:

1. Pro seznamy F# použijte formulář `int list` přípony: spíše než `list<int>`.
2. Pro možnosti Jazyka F# použijte `int option` formulář `option<int>`přípony: nikoli .
3. Pro možnosti hodnoty F# použijte `int voption` formulář `voption<int>`přípony: spíše než .
4. Pro pole F# použijte syntaktický název `int[]` spíše než `int array` nebo `array<int>`.
5. Pro referenční buňky použijte `int ref` spíše než `ref<int>` nebo `Ref<int>`.

Pro všechny ostatní typy použijte formulář předpony.

## <a name="formatting-tuples"></a>Formátování řazených kolekcí členů

Kontinalizovat n-tice by měla být závorka a za vymezujícími čárky v ní by měla následovat jedna mezera, například: `(1, 2)`, `(x, y, z)`.

Běžně se přijímá vynechat závorky v porovnávání vzorů řazených kolekcí členů:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Je také běžně přijímán vynechat závorky, pokud n-tice je vrácená hodnota funkce:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

V souhrnu upřednostňujte instance n-tice v závorce, ale při použití řazených kolekcí členů pro porovnávání vzorků nebo vrácené hodnoty se považuje za vpořádku, aby se zabránilo závorkám.

## <a name="formatting-discriminated-union-declarations"></a>Formátování discriminated unie prohlášení

Odsazení `|` v definici typu čtyřmi mezerami:

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

## <a name="formatting-discriminated-unions"></a>Formátování diskriminovaných sjednocení

Instanci s discriminated sjednocení, které se rozdělí na více řádků by měl dát obsažená data nový obor s odsazení:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Uzavírací závorky mohou být také na novém řádku:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Formátování deklarací záznamů

Odsazení `{` v definici typu čtyřmi mezerami a zahájení seznamu polí na stejném řádku:

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

Umístění počátečního tokenu na nový řádek a uzavírací token na nový řádek je vhodnější, pokud deklarujete implementace rozhraní nebo členy v záznamu:

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

## <a name="formatting-records"></a>Formátování záznamů

Krátké záznamy mohou být zapsány v jednom řádku:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Záznamy, které jsou delší, by měly pro popisky používat nové řádky:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Umístění počátečního tokenu na nový řádek, obsah s kartami přes jeden obor a uzavírací token na novém řádku je vhodnější, pokud jste:

* Přesouvání záznamů v kódu s různými obory odsazení
* Jejich potrubí do funkce

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

Stejná pravidla platí pro prvky seznamu a pole.

## <a name="formatting-copy-and-update-record-expressions"></a>Formátování výrazů záznamů kopírování a aktualizace

Výraz záznamu kopírování a aktualizace je stále záznam, takže platí podobné pokyny.

Krátké výrazy se vejdou na jeden řádek:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Delší výrazy by měly používat nové řádky:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

A stejně jako vodítko záznamu můžete chtít vyhradit samostatné řádky pro závorky a odsazení jednoho oboru vpravo s výrazem. V některých zvláštních případech, například zabalení hodnoty s volitelným bez závorek, může být nutné zachovat ortézu na jednom řádku:

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

## <a name="formatting-lists-and-arrays"></a>Formátování seznamů a polí

Pište `x :: l` s mezerami kolem operátoru `::` (`::` je infix operátor, tedy obklopen mezerami).

Seznam a pole deklarovaná na jednom řádku by měla mít mezeru za otevírací závorkou a před uzavírací závorkou:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Vždy používejte alespoň jednu mezeru mezi dvěma odlišnými operátory složených závorek. Ponechte například mezeru `[` mezi `{`a a .

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

Stejné pokyny platí pro seznamy nebo pole řazených kolekcí členů.

Seznamy a pole, které se rozdělí na více řádků, se řídí podobným pravidlem jako záznamy:

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

A stejně jako u záznamů, deklarování otevírací a uzavírací závorky na vlastní lince usnadní přesun kódu a potrubí do funkcí.

Při programovém generování polí a `->` seznamů upřednostňujte při `do ... yield` vždy generování hodnoty:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

Starší verze jazyka F# vyžaduje `yield` zadání v situacích, kdy data mohou být generovány podmíněně nebo mohou být po sobě jdoucí výrazy, které mají být vyhodnoceny. Preferujte vynechání `yield` těchto klíčových slov, pokud není nutné zkompilovat se starší jazykovou verzí Jazyka F#:

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

V některých `do...yield` případech může pomoci v čitelnosti. Tyto případy, i když subjektivní, by měly být vzaty v úvahu.

## <a name="formatting-if-expressions"></a>Formátování, pokud výrazy

Odsazení podmínek závisí na velikosti výrazů, které je tvoří. Pokud `cond` `e1` , `e2` a jsou krátké, jednoduše je napište na jeden řádek:

```fsharp
if cond then e1 else e2
```

Pokud `cond`buď `e1` `e2` , nebo jsou delší, ale ne víceřádkové:

```fsharp
if cond
then e1
else e2
```

Pokud některý z výrazů jsou víceřádkové:

```fsharp
if cond then
    e1
else
    e2
```

Více podmínek `elif` `else` s a jsou odsazeny ve stejném oboru jako `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Konstrukce odpovídající vzorek

Použijte `|` pro každou klauzuli shody bez odsazení. Pokud je výraz krátký, můžete zvážit použití jednoho řádku, pokud je každý dílčí výraz také jednoduchý.

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

Pokud je výraz vpravo od šipky pro porovnávání vzorků příliš velký, přesuňte `match` / `|`jej na následující řádek, odsazený o jeden krok od .

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Porovnávání vzorů anonymních `function`funkcí počínaje písmenem a) by obecně nemělo být odsazeno příliš daleko. Například odsazení jednoho oboru následujícím je v pořádku:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Porovnávání vzorů ve `let` `let rec` funkcích definovaných nebo by `let`mělo být `function` odsazeno čtyři mezery po spuštění , i když je použito klíčové slovo:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nedoporučujeme zarovnávat šipky.

## <a name="formatting-trywith-expressions"></a>Formátování try/s výrazy

Porovnávání vzorů u typu výjimky by mělo `with`být odsazeno na stejné úrovni jako .

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

## <a name="formatting-function-parameter-application"></a>Aplikace parametru funkce formátování

Obecně platí, že většina aplikace parametrů funkce se provádí na stejném řádku.

Pokud chcete použít parametry na funkci na novém řádku, odsaďte je jedním oborem.

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

Stejné pokyny platí pro lambda výrazy jako argumenty funkce. Pokud tělo výrazu lambda, tělo může mít jiný řádek, odsazené podle jednoho oboru

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

Pokud je však tělo výrazu lambda více než jeden řádek, zvažte jeho započítávání do samostatné funkce, nikoli víceřádkovou konstrukci použitou jako jeden argument pro funkci.

### <a name="formatting-infix-operators"></a>Formátování infix operátorů

Oddělte operátory mezerami. Zřejmé výjimky z tohoto `!` `.` pravidla jsou a operátory.

Výrazy infix jsou v pořádku pro sestavu ve stejném sloupci:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formátování operátorů kanálu

Operátory kanálu `|>` by měly přejít pod výrazy, na kterých pracují.

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

### <a name="formatting-modules"></a>Formátovací moduly

Kód v místním modulu musí být odsazen vzhledem k modulu, ale kód v modulu nejvyšší úrovně by neměl být odsazen. Prvky oboru názvů nemusí být odsazeny.

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

### <a name="formatting-object-expressions-and-interfaces"></a>Formátování výrazů a rozhraní objektů

Objektové výrazy a rozhraní by měly `member` být zarovnány stejným způsobem jako odsazení za čtyřmi mezerami.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formátování prázdného místa ve výrazech

Vyhněte se cizí prázdné místo ve výrazech F#.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Pojmenované argumenty by také neměly mít prostor obklopující `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Formátování atributů

[Atributy](../language-reference/attributes.md) jsou umístěny nad konstrukcí:

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

### <a name="formatting-attributes-on-parameters"></a>Formátování atributů parametrů

Atributy lze také umístit na parametry. V tomto případě umístěte na stejný řádek jako parametr a před název:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Formátování více atributů

Pokud je na konstrukci, která není parametrem, použito více atributů, měly by být umístěny tak, aby byl jeden atribut na řádek:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Při použití na parametr musí být na stejném řádku `;` a odděleny oddělovačem.

## <a name="formatting-literals"></a>Formátování literál

[F# literály](../language-reference/literals.md) `Literal` pomocí atributu by měl umístit atribut na vlastní řádek a používat PascalCase pojmenování:

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Vyhněte se umístění atributu na stejný řádek jako hodnota.
