---
title: 'F # – kód formátování pokyny'
description: 'Přečtěte si pokyny pro formátování kódu F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 1433b6891a6a0ddcdc082c141365ae54fa40c27b
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="f-code-formatting-guidelines"></a>F # – kód formátování pokyny

Tento článek obsahuje pokyny k formátování kódu tak, aby váš kód F # je:

* Obecně zobrazit jako zlepšení čitelnosti
* V souladu s konvence používaný službou formátování nástroje v sadě Visual Studio a dalšími editory
* Podobně jako ostatní kód online

Tyto pokyny jsou založené na [komplexní pokyny k formátování konvence F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) podle [Anh hnoje Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Obecná pravidla pro odsazení

F # ve výchozím nastavení používá významný mezerový znak. Následující pokyny jsou určeny k obsahují pokyny, jak přehlednější některé běžné problémy, které to použít.

### <a name="using-spaces"></a>Použití prostorů

Pokud je požadována odsazení, je nutné použít mezery, tabulátory není. Je vyžadován alespoň jeden prostor. Vaše organizace můžete vytvořit kódování standardy k určení počtu prostory pro odsazení; dva, tři nebo čtyři prostory odsazení na každé úrovni, kde dochází k odsazení je typické.

**Doporučujeme 4 mezer na odsazení.**

Ale nutné dodat, odsazení programů je subjektivní věci. Rozdíly jsou OK, ale je první pravidlo, postupujte podle *konzistence odsazení*. Zvolte obecně přijatelné styl odsazení a systematičtěji ji použít v celé vaší základu kódu.

## <a name="formatting-discriminated-union-declarations"></a>Formátování rozlišované deklarace sjednocení

Odsazení `|` v definici typu 4 mezerami:

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

Vytvořenou instanci Rozlišované sjednocení, který rozdělit do více řádků měl dát dat obsažených nový obor s odsazení:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Pravá závorka může být také na nový řádek:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a>Formátování řazených kolekcí členů

Vytváření instancí řazené kolekce členů musí být v závorkách a rozdělujících čárkami v rámci by měl následovat a jedna mezera, například: `(1, 2)`, `(x, y, z)`.

Běžně přijatý výjimka je vynechejte závorkách vzor odpovídajícím řazené kolekce členů:

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a>Formátování záznamů

Krátký záznamy lze zapsat na jednom řádku:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Záznamy, které jsou delší měli použít pro štítky nové řádky:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Uvedení token otevírání na stejném řádku a token uzavírací na nový řádek je také vhodná:

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

Stejná pravidla použít u elementů na seznamu a pole.

## <a name="formatting-lists-and-arrays"></a>Formátování seznamy a pole

Zápis `x :: l` prostory kolem `::` – operátor (`::` je zaváděcí operátor, proto ohraničeny znaky) a `[1; 2; 3]` (`;` je oddělovač, proto následované mezerou).

Používejte vždy alespoň jedna mezera mezi dva odlišné operátory složené závorce jako. Například nechte mezeru mezi `[` a `{`.

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

Seznamy a polí, která rozdělit do více řádků postupujte stejně jako záznamy podobné pravidlo:

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

## <a name="formatting-if-expressions"></a>Formátování v případě výrazy

Odsazení podmíněné příkazy závisí na velikosti výrazy, které tvoří jejich. Pokud `cond`, `e1` a `e2` jsou malé, jednoduše zapíše je na jednom řádku:

```fsharp
if cond then e1 else e2
```

Pokud `e1` a `cond` jsou malé, ale `e2` velký:

```fsharp
if cond then e1
else
    e2
```

Pokud `e1` a `cond` jsou velké a `e2` je malá:

```fsharp
if cond then
    e1
else e2
```

Pokud jsou všechny výrazy velké:

```fsharp
if cond then
    e1
else
    e2
```

Více podmíněné příkazy s `elif` a `else` odsazeny stejný obor jako `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Vzor odpovídající konstrukce

Použití `|` pro každou klauzuli shoda s žádné odsazení. Je-li výraz krátký, můžete použít jeden řádek.

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

// OK
match l with [] -> false | _ :: _ -> true
```

Pokud ve výrazu na pravé straně šipku pro porovnávání je příliš velký, ho přesunout do následujícího řádku, zobrazují odsazené jeden krok z `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Vzor odpovídající anonymní funkcí, spouštění podle `function`, obecně by neměl příliš daleko odsazení. Například následující odsazení jeden obor je v pořádku:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Ve funkcích definované porovnávání vzorů `let` nebo `let rec` by měla být zobrazují odsazené 4 mezery po spuštění systému `let`i v případě `function` – klíčové slovo se používá:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Nedoporučujeme zarovnání šipky.

## <a name="formatting-trywith-expressions"></a>Formátování try / s výrazy

Pro porovnávání na typ výjimky by měla být odsazeny na stejné úrovni jako `with`.

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

## <a name="formatting-function-parameter-application"></a>Formátování aplikace parametr – funkce

Obecně platí většina aplikací parametr funkce se provádí na stejném řádku.

Pokud chcete použít parametry pro funkci na nový řádek, odsazení je jeden obor.

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

Argumenty anonymní funkce může být buď na další řádek, nebo se nepropojená `fun` na ose argument:

```fsharp
// OK
let printListWithOffset a list1 =
    List.iter (fun elem ->
        printfn "%d" (a + elem)) list1

// OK, but prefer previous
let printListWithOffset a list1 =
    List.iter (
        fun elem ->
            printfn "%d" (a + elem)) list1
```

### <a name="formatting-infix-operators"></a>Formátování zaváděcí operátory

Samostatné operátory mezerami. Zřejmé výjimkou tohoto pravidla jsou `!` a `.` operátory.

Zaváděcí výrazy řazení na stejný sloupec je OK:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formátování operátorů kanálů

Kanál `|>` operátory má zobrazit pod pracují na výrazy.

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

Kód v místním modulu musí odsazeny relativně k modulu, ale nesmí být odsazeny kód v modul nejvyšší úrovně. Namespace prvky nemají odsazení.

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

### <a name="formatting-object-expressions-and-interfaces"></a>Formátování objektové výrazy a rozhraní

Objektové výrazy a rozhraní by mělo být zarovnáno stejně jako s `member` se odsazeny po 4 mezery.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a>Formátování prázdné znaky na výrazy

Nepoužívejte nadbytečné prázdné znaky na výrazy F #.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Pojmenované argumenty by neměl mít také, které obaluje místa `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-blank-lines"></a>Formátování prázdné řádky

* Samostatné nejvyšší úrovně funkce – třída definice a dva prázdné řádky.
* Metoda definice uvnitř třídy jsou odděleny jeden prázdný řádek.
* Prázdné řádky může šetřit () k oddělení skupin souvisejících funkcí. Prázdné řádky může být vynechán mezi spoustu související one-liners (například sada fiktivní implementace).
* Pomocí prázdné řádky ve funkcích, doporučujeme, označte logické oddíly.

## <a name="formatting-comments"></a>Formátování komentáře

Obecně přednost více komentáře dvojitou lomítko přes komentáře bloku stylu ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    Generally avoid these kinds of comments.
*)
```

Vložené komentáře by měl počáteční písmeno.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Zásady vytváření názvů

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Použití camelCase vázané na třídu, vázané na výrazu a vzor vázané hodnoty a funkce

Je běžné a přijaté F # stylu camelCase používat pro všechny názvy vázána jako místní proměnné nebo v vzor shody a definice funkcí.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Funkce místně vázané ve třídách měli použít také camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Použít camelCase pro interní a privátní hodnoty vázané na modul a funkce

Použijte camelCase pro soukromé hodnoty vázané na modul, včetně následujících:

* Ad hoc funkce ve skriptech

* Hodnoty, které tvoří interní implementace modul nebo typ

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Použití camelCase parametrů

Všechny parametry by měli používat camelCase v souladu s zásady vytváření názvů .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Použití PascalCase pro moduly

Všechny moduly (nejvyšší úrovně, interní, privátní, vnořené) by měli používat PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Použít PascalCase pro typ deklarace, členů a popisky

Třídy, rozhraní, struktury, výčty, delegáti, záznamy a rozlišovaná sjednocení by měly název s PascalCase. Členové v rámci typy a popisky pro záznamy a rozlišovaná sjednocení by měl používat také PascalCase.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Použít PascalCase pro konstrukce vnitřní na rozhraní .NET

Obory názvů, výjimky, události a projekt nebo`.dll` názvy měli použít také PascalCase. Nejen nemá to zkontrolujte spotřeby z jinými jazyky rozhraní .NET působí přirozenější k příjemce, je také konzistentní s zásady vytváření názvů .NET, kterými se můžete setkat.

### <a name="avoid-underscores-in-names"></a>Vyhněte se podtržítka v názvech

V minulosti používat některé knihovny F # v názvech podtržítka. Ale toto je přijatá už široce, částečně, protože ho je v konfliktu s zásady vytváření názvů .NET. Ale nutné dodat, některé programátory F # pomocí podtržítka výraznou, částečně historických důvodů a proti chybám a ohledu je důležité. Ale Upozorňujeme, že styl je často disliked jiní uživatelé, kteří mají vybrat o tom, jestli ho použít.

Některé výjimky zahrnuje spolupráce s nativním součásti, kde jsou velmi běžné podtržítka.

### <a name="use-standard-f-operators"></a>Použijte standardní operátory F #

Následující operátory jsou definovány v standardní knihovny F # a místo definování ekvivalenty měla být použita. Pomocí těchto operátorů se nedoporučuje, protože je obvykle, aby byl kód čitelnější a idiomatickou. Vývojářům pozadí v OCaml nebo jiné funkční programovací jazyk může být uzpůsobené pro různé idioms. Následující seznam shrnuje doporučené operátory F #.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Throwing away a value
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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Použijte předponu syntaxi pro obecné typy (`Foo<T>`) přednostně syntaxe operátory (`T Foo`)

F # dědí oba operátory ML styl pojmenování obecné typy (například `int list`) a také předponu styl .NET (například `list<int>`). Dáváte přednost styl rozhraní .NET, s výjimkou čtyři konkrétní typy:

1. Pro F # uvádí, použijte formát operátory: `int list` místo `list<int>`.
2. Pro možnosti F #, použijte formát operátory: `int option` místo `option<int>`.
3. Pro F # pole, použijte syntaxi název `int[]` místo `int array` nebo `array<int>`.
4. Referenční buňky, použijte `int ref` místo `ref<int>` nebo `Ref<int>`.

Pro všechny ostatní typy použijte předponu formulář.
