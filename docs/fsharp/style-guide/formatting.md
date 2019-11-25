---
title: Pravidla formátování kódu F#
description: Přečtěte si pokyny F# pro formátování kódu.
ms.date: 11/04/2019
ms.openlocfilehash: 895c8211731b47bd4c59d762d5806cfc1bfe232d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089317"
---
# <a name="f-code-formatting-guidelines"></a>Pravidla formátování kódu F#

Tento článek obsahuje pokyny, jak formátovat kód tak, aby byl váš F# kód:

* Obecně zobrazené jako čitelnější
* Je v souladu s konvencemi použitými nástroji formátování v aplikaci Visual Studio a dalšími editory
* Podobně jako u jiného kódu online

Tyto pokyny jsou založené na [komplexní příručce k F# formátování konvencí](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) [Anh-Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Obecná pravidla pro odsazení

F#ve výchozím nastavení používá významné prázdné znaky. Následující pokyny jsou určené k tomu, aby poskytovaly pokyny, jak juggle některé problémy, které může způsobit.

### <a name="using-spaces"></a>Použití mezer

Pokud je požadováno odsazení, je nutné použít mezery, nikoli tabulátory. Vyžaduje se aspoň jedna mezera. Vaše organizace může vytvořit standardy kódování, které určují počet mezer, které se mají použít pro odsazení; dvě, tři nebo čtyři mezery odsazení na každé úrovni, kde dochází k odsazení, je typický.

**Pro odsazení doporučujeme 4 mezery.**

To znamená, že odsazení programů je subjektivní. Variace jsou OK, ale první pravidlo, které byste měli dodržovat, je *konzistence odsazení*. Vyberte všeobecně přijatý styl odsazení a používejte ho systematicky v rámci vašeho základu kódu.

## <a name="formatting-white-space"></a>Formátování mezer

F#je mezera bez rozlišení. I když je většina sémantických míst z prázdných znaků krytá správným odsazením, je potřeba zvážit několik dalších věcí.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Formátování operátorů v aritmetických výrazech

Vždy používat prázdné znaky kolem binárních aritmetických výrazů:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Unární operátory `-` by měly vždy mít hodnotu, na kterou se negace okamžitě sleduje:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Přidání prázdného znaku za operátorem `-` může vést k nejasnostem pro ostatní.

V souhrnu je důležité vždycky:

* Obklopit binární operátory s prázdným znakem
* Po unárním operátoru nikdy nemá koncový znak mezer.

Základní pravidlo pro binární aritmetické operátory je obzvláště důležité. Selhání při obklopení binárního operátoru `-`, pokud se kombinace s určitými možnostmi formátování může vést k interpretaci jako unární `-`.

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Ohraničení vlastní definice operátoru s mezerami

Pro obklopení definice operátoru vždy použít prázdné znaky:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Pro jakýkoli vlastní operátor, který začíná na `*` a který má více než jeden znak, je nutné přidat prázdné znaky na začátek definice, aby nedocházelo k nejednoznačnosti kompilátoru. Z tohoto důvodu doporučujeme jednoduše obklopit definice všech operátorů jediným prázdným znakem.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Obklopit šipky parametrů funkce s mezerami

Při definování signatury funkce použijte prázdné místo kolem symbolu `->`:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Uzavřít argumenty funkce s mezerami

Při definování funkce použijte prázdné znaky kolem každého argumentu.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-very-long-member-definitions"></a>Umístit parametry na nový řádek pro velmi dlouhé definice členů

Pokud máte hodně dlouhé definice členů, umístěte parametry na nové řádky a odsadíte je jeden obor.

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

To platí také pro konstruktory:

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>Anotace typu

#### <a name="right-pad-function-argument-type-annotations"></a>Poznámky k typu argumentu funkce pravého panelu

Při definování argumentů s anotacemi typu použijte prázdné místo za symbolem `:`:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Obklopit anotace návratového typu s prázdným znakem

V poznámce v funkci nebo v anotaci typu hodnoty (návratový typ v případě funkce) použijte prázdné místo před a za `:` symbolem:

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

* Samostatné definice funkcí a tříd na nejvyšší úrovni se dvěma prázdnými řádky.
* Definice metod uvnitř třídy jsou oddělené jedním prázdným řádkem.
* Můžete použít nadbytečné prázdné řádky k oddělení skupin souvisejících funkcí. Prázdné řádky mohou být vynechány mezi svazků souvisejících LINERS (například sadou fiktivních implementací).
* Používejte prázdné řádky ve funkcích a používejte k označení logických oddílů.

## <a name="formatting-comments"></a>Formátování komentářů

Obecně preferovat více komentářů s dvojitým lomítkem přes komentáře bloku ve stylu ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Vložené komentáře by měly být velkými písmeny první písmeno.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Zásady vytváření názvů

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Použití camelCase pro hodnoty a funkce vázané na výrazy vázané na výraz a na vzor

Je běžné a přijatelné F# styly pro použití CamelCase pro všechny názvy, které jsou svázané jako lokální proměnné nebo v porovnání vzorů a definic funkcí.

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

Když je funkce vázaná na modul součástí veřejného rozhraní API, měla by používat camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Použití camelCase pro interní a privátní hodnoty a funkce vázané na modul

Použijte camelCase pro hodnoty vázané na modul, včetně následujících:

* Funkce ad hoc ve skriptech

* Hodnoty, které tvoří interní implementaci modulu nebo typu

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Použití camelCase pro parametry

Všechny parametry by měly používat camelCase v souladu s konvencemi vytváření názvů .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Použití PascalCase pro moduly

Všechny moduly (na nejvyšší úrovni, interní, privátní, vnořený) by měly používat PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Použití PascalCase pro deklarace typu, členy a popisky

Třídy, rozhraní, struktury, výčty, delegáti, záznamy a rozlišené sjednocení by měly být pojmenovány pomocí PascalCase. Členy v rámci typů a popisků pro záznamy a rozlišené sjednocení by měly také používat PascalCase.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Použití PascalCase pro vnitřní konstrukce pro .NET

Obory názvů, výjimky, události a názvy projektů a`.dll` by měly také používat PascalCase. Nejenom to dělá, že se spotřeba z jiných jazyků .NET u spotřebitelů stane přirozenější, je taky v souladu se zásadami vytváření názvů .NET, u kterých se pravděpodobně setkáte.

### <a name="avoid-underscores-in-names"></a>Vyhněte se podtržítkům v názvech

Historicky některé F# knihovny používaly v názvech podtržítka. Nejedná se ale o již široce přijatelné částečně, protože je v konfliktu se zásadami vytváření názvů .NET. V takovém případě F# někteří programátoři v rámci historických důvodů používají podtržítka, částečně a tolerance a respektování jsou důležité. Uvědomte si však, že styl je často nepodobný jiným uživatelům, kteří mají možnost zvolit, zda se má použít.

Některé výjimky zahrnují spolupráci s nativními komponentami, kde podtržítka jsou velmi společná.

### <a name="use-standard-f-operators"></a>Použití standardních F# operátorů

Následující operátory jsou definovány ve F# standardní knihovně a měly by být použity místo definování ekvivalentů. Použití těchto operátorů se doporučuje, protože je v úmyslu zvýšit čitelnost a idiomatickou kódu. Vývojáři s pozadím v OCaml nebo jiným funkčním programovacím jazykem můžou být zvyklí na různé idiomy. Následující seznam shrnuje doporučené F# operátory.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Použijte syntaxi prefixu pro obecné typy (`Foo<T>`) v Předvolby na syntaxi přípony (`T Foo`).

F#dědí jak styl přípona ML obecných typů pojmenování (například `int list`), tak i prefix .NET (například `list<int>`). Preferovat styl rozhraní .NET, s výjimkou pěti specifických typů:

1. Pro F# seznamy použijte formát přípony: `int list` místo `list<int>`.
2. Pro F# možnosti použijte formát přípony: `int option` místo `option<int>`.
3. Pro F# možnosti hodnoty použijte formát přípony: `int voption` místo `voption<int>`.
4. Pro F# pole použijte syntaktický název `int[]` místo `int array` nebo `array<int>`.
5. U referenčních buněk použijte `int ref` místo `ref<int>` nebo `Ref<int>`.

U všech ostatních typů použijte formulář předpony.

## <a name="formatting-tuples"></a>Formátování řazených kolekcí členů

Instance řazené kolekce členů by měla být v závorkách a oddělovací čárky v rámci by měly být následovány jedním mezerou, například: `(1, 2)`, `(x, y, z)`.

Při porovnávání vzorů řazených kolekcí členů je obvykle přijatelné vynechat závorky:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

V případě, že řazená kolekce členů je návratovou hodnotou funkce, je také obvykle přijato, aby se vynechal závorky:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

V souhrnu dáváte přednost vytváření instancí řazené kolekce členů v závorkách, ale při použití řazených kolekcí členů nebo návratové hodnoty je považována za jemné, aby nedošlo k závorce.

## <a name="formatting-discriminated-union-declarations"></a>Formátování deklarací rozlišených sjednocení

Odsadit `|` v definici typu o 4 mezery:

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

## <a name="formatting-discriminated-unions"></a>Formátování rozlišených sjednocení

Instance rozlišených sjednocení, která se rozdělí mezi více řádků, by měla obsahovat obsažená data nový obor s odsazením:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Pravá kulatá závorka může být také na novém řádku:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Formátování deklarací záznamů

Odsadit `{` v definici typu o 4 mezery a spusťte seznam polí na stejném řádku:

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

Umístění počátečního tokenu na nový řádek a uzavírací token na novém řádku je vhodnější, pokud deklarujete implementace rozhraní nebo členy záznamu:

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

## <a name="formatting-records"></a>Formátování záznamů

Krátké záznamy můžete zapsat na jeden řádek:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Záznamy, které mají delší dobu, by měly používat nové řádky pro popisky:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Umístění otevřeného tokenu na nový řádek, obsah se na kartách na jednom rozsahu a uzavírací token na novém řádku je vhodnější, pokud jste:

* Přesouvání záznamů kolem kódu s různými rozsahy odsazení
* Rozpotrubním do funkce

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

Stejná pravidla platí pro prvky list a Array.

## <a name="formatting-copy-and-update-record-expressions"></a>Formátování výrazů záznamu kopírování a aktualizace

Výraz záznamu kopie a aktualizace je stále záznam, takže podobné pokyny platí.

Krátké výrazy se můžou vejít na jeden řádek:

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

Stejně jako u pokynů k záznamům můžete chtít pro složené závorky vyhradit samostatné řádky a odsadit jeden obor vpravo pomocí výrazu. Všimněte si, že v některých zvláštních případech, jako je například zabalení hodnoty s volitelnou bez závorek, bude pravděpodobně nutné zachovat složené závorky na jednom řádku:

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

Zápis `x :: l` s mezerami kolem operátoru `::` (`::` je vpony operátor, takže je uzavřený mezerami).

Seznam a pole deklarované na jednom řádku by měly mít mezeru za levou závorkou a před pravou závorkou:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Vždy používejte alespoň jednu mezeru mezi dvěma různými operátory podobnými závorce. Ponechte například mezeru mezi `[` a `{`.

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

Pro seznamy nebo pole řazených kolekcí členů platí stejné zásady.

Seznamy a pole, které jsou rozdělené mezi více řádků, následují podobně jako záznamy:

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

A stejně jako u záznamů deklarujete levou a pravou hranatou závorku na vlastním řádku, čímž usnadníte přesouvání kódu a natékání do funkcí.

Při generování polí a seznamů programově preferovat `->` přes `do ... yield` při každém vygenerování hodnoty:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

Starší verze F# jazyka požadovaly určení `yield` v situacích, kdy mohou být data vygenerována podmíněně, nebo mohou být vyhodnoceny po sobě jdoucí výrazy. Preferovat vynechání těchto klíčových slov `yield`, pokud není nutné kompilovat F# se starší jazykovou verzí:

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

V některých případech může `do...yield` pomoci při čitelnosti. V takovém případě by se měly vzít v úvahu i tyto případy.

## <a name="formatting-if-expressions"></a>Formátování výrazů if

Odsazení podmíněných hodnot závisí na velikosti výrazů, které je tvoří. Pokud `cond`, `e1` a `e2` jsou krátké, stačí je napsat na jeden řádek:

```fsharp
if cond then e1 else e2
```

Pokud je `cond`, `e1` nebo `e2` delší, ale ne víceřádkové:

```fsharp
if cond
then e1
else e2
```

Pokud je některý z těchto výrazů víceřádkový:

```fsharp
if cond then
    e1
else
    e2
```

Více podmíněných typů s `elif` a `else` jsou odsazeny ve stejném oboru jako `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Konstrukce pro porovnávání vzorů

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

Pokud je výraz napravo od šipky porovnávání se vzorci příliš velký, přesuňte jej na následující řádek, odsadíte jeden krok z `match`/`|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Porovnávání vzorů anonymních funkcí, počínaje `function`, by nemělo být obvykle příliš daleko odsazené. Například odsazení jednoho oboru je následující:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Porovnávání vzorů ve funkcích definovaných `let` nebo `let rec` by mělo být po začátku `let`odsazené o 4 mezery, i když se používá klíčové slovo `function`:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nedoporučujeme zarovnávat šipky.

## <a name="formatting-trywith-expressions"></a>Výrazy try/with formátování

Porovnávání vzorů u typu výjimky by mělo být odsazeno na stejné úrovni jako `with`.

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

## <a name="formatting-function-parameter-application"></a>Formátování aplikace parametrů funkce

Obecně platí, že většina parametrů funkce je provedena na stejném řádku.

Pokud chcete použít parametry pro funkci na novém řádku, odsadit je podle jednoho oboru.

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

Stejné pokyny platí pro výrazy lambda jako argumenty funkce. Pokud tělo výrazu lambda, tělo může mít jiný řádek, který je odsazený o jeden obor.

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

Pokud je však tělo výrazu lambda více než jeden řádek, zvažte jejich vyhodnocování do samostatné funkce namísto použití konstruktoru víceřádkové konstrukce jako jediného argumentu funkce.

### <a name="formatting-infix-operators"></a>Formátování operátorů vpony

Jednotlivé operátory oddělte mezerami. Zřejmou výjimkou z tohoto pravidla jsou operátory `!` a `.`.

Výrazy vpony jsou v pořádku až seznamu na stejném sloupci:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formátování operátorů kanálu

`|>` operátory kanálu by měly přecházet pod výrazy, na kterých pracují.

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

### <a name="formatting-modules"></a>Formátování modulů

Kód v místním modulu musí být odsazený relativně vzhledem k modulu, ale kód v modulu nejvyšší úrovně by neměl být odsazený. Elementy oboru názvů není nutné odsazovat.

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

### <a name="formatting-object-expressions-and-interfaces"></a>Formátování výrazů objektů a rozhraní

Výrazy objektu a rozhraní by měly být zarovnány stejným způsobem s `member` odsazovat po 4 mezerách.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formátování mezer ve výrazech

Vyhněte se nadbytečnému F# prázdnému prostoru ve výrazech.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Pojmenované argumenty by neměly mít také prostor obklopující `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Formátování atributů

[Atributy](../language-reference/attributes.md) jsou umístěné nad konstrukcí:

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

### <a name="formatting-attributes-on-parameters"></a>Formátování atributů u parametrů

Atributy mohou být také umístěny v parametrech. V takovém případě umístěte na stejný řádek jako parametr a před název:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Formátování více atributů

Je-li pro konstrukci, která není parametrem, použita více atributů, měly by být umístěny tak, že na každý řádek je jeden atribut:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Při použití na parametr se musí nacházet na stejném řádku a oddělené oddělovačem `;`.

## <a name="formatting-literals"></a>Formátování literálů

literály používající atribut `Literal` by měly umístit atribut na svůj vlastní řádek a používat PascalCase pojmenování: [ F# ](../language-reference/literals.md)

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Vyhněte se umístění atributu na stejný řádek jako hodnota.
