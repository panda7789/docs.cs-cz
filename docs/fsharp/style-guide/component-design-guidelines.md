---
title: F#Pokyny k návrhu komponenty
description: Přečtěte si pokyny pro zápis F# součásti určené pro využití dalších volajícími.
ms.date: 05/14/2018
ms.openlocfilehash: c61e4cd9098388b356c71c325d66c760fa866cf0
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55066022"
---
# <a name="f-component-design-guidelines"></a>F#Pokyny k návrhu komponenty

Tento dokument je sada součástí pokyny návrhu pro F# programování, na základě F# pokyny k návrhu komponenty, v14 Microsoft Research a [jinou verzi](https://fsharp.org/specs/component-design-guidelines/) původně připravili a udržuje F# Software Foundation.

Tento dokument předpokládá, že máte zkušenosti s F# programování. Mnoho k F# komunity pro své příspěvky a užitečné zpětné vazby na různé verze tohoto průvodce.

## <a name="overview"></a>Přehled

Tento dokument vypadá na některé z problémů souvisejících s F# komponenta, návrh a psaní kódu. Komponenta může znamenat některý z následujících akcí:

* Vrstvy v vaše F# projekt, který obsahuje externí uživatele v rámci tohoto projektu.
* Knihovna určené ke spotřebě F# kódu přes hranice sestavení.
* Knihovna určena pro použití v jakémkoliv jazyce .NET přes hranice sestavení.
* Knihovny určené k distribuci přes úložiště balíčků, jako například [NuGet](https://nuget.org).

Použijte techniky popsané v tomto článku [pět zásadami dobrého F# kód](index.md#five-principles-of-good-f-code)a proto využívají obě funkční a objekt programování podle potřeby.

Bez ohledu na to metodologie komponenty a knihovny návrháře čelí celou řadu praktických a prosaic problémů při pokusu o vytvoření rozhraní API, které je snadno použitelný pro vývojáře. Odepření aplikací [pokyny k návrhu knihovny .NET](../../standard/design-guidelines/index.md) bude řídit vytváření konzistentní sadu rozhraní API, která jsou příjemný využívat.

## <a name="general-guidelines"></a>Obecné pokyny

Existuje několik univerzální pokyny, které se vztahují F# knihoven, bez ohledu na jeho zamýšlenou cílovou skupinou pro knihovnu.

### <a name="learn-the-net-library-design-guidelines"></a>Přečtěte si pokyny pro návrh knihovna .NET

Bez ohledu na typ z F# kódování provádíte, je důležité mít praktické znalosti [pokyny k návrhu knihovny .NET](../../standard/design-guidelines/index.md). Většina jiných F# a programátory na platformě .NET se seznamte s těmito pokyny a očekávají kód .NET a odpovídat na ně.

Pokyny pro návrh knihovny .NET poskytují obecné pokyny týkající se názvů, navrhování tříd a rozhraní, návrhu člena (vlastnosti, metody, události atd.) a další a jsou užitečné první bod odkazu pro širokou škálu pokyny k návrhu.

### <a name="add-xml-documentation-comments-to-your-code"></a>Přidání komentáře k dokumentaci XML do kódu

Dokumentace XML v rámci veřejných API Ujistěte se, že se uživatelé dostanou skvělé technologie Intellisense a rychlé informace, při použití těchto typů a členů a povolit vytváření dokumentace pro knihovny souborů. Zobrazit [dokumentace XML](../language-reference/xml-documentation.md) o různých značky xml, které lze použít pro další kód v rámci xmldoc komentáře.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

Můžete použít buď krátký tvar XML komentáře (`/// comment`), nebo standardní komentáře XML (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Zvažte použití explicitního podpis souborů (.fsi) pro stabilní knihovny a komponenty rozhraní API

Použití souborů explicitní podpisy v F# knihovna nabízí stručné shrnutí veřejné rozhraní API, které obě pomáhá zajistit, že znáte úplné veřejné povrchu vaše knihovna také poskytuje čisté oddělení mezi veřejné dokumentaci a interní Podrobnosti implementace. Všimněte si, že podpis souborů přidat případná problémová místa na měnící se veřejné rozhraní API, tak, že vyžaduje změny v implementaci a podpis souborů. V důsledku toho podpis souborů by měl obvykle jenom zavést při rozhraní API má stát ztuhly a již má výrazně změnit.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Vždy postupujte podle osvědčené postupy pro používání řetězců v .NET

Postupujte podle [osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md) pokyny. Konkrétně se vždy explicitně uvést *kulturní záměr* převod a porovnání řetězců (v případě potřeby).

## <a name="guidelines-for-f-facing-libraries"></a>Pokyny pro F#-směřující knihovny

Tato část nabízí doporučení pro vývoj veřejné F#-směřující knihoven; To znamená, knihovny vystavení veřejné rozhraní API, která mají být využívány službou F# vývojáři. Existuje široká škála návrh knihovny doporučení platí konkrétně pro F#. Chybí konkrétní doporučení, které následují jsou pokyny pro návrh knihovny .NET pokyny pro použití náhradní lokality.

### <a name="naming-conventions"></a>Zásady vytváření názvů

#### <a name="use-net-naming-and-capitalization-conventions"></a>Použití .NET konvence pojmenování a malá a velká písmena

V následující tabulce dodržovat konvence pojmenování a malá a velká písmena .NET. Existují malé doplňky také F# vytvoří.

| Konstrukce | případ | Část | Příklady | Poznámky |
|-----------|------|------|----------|-------|
| Konkrétní typy | PascalCase | Podstatné jméno / tvary přídavných jmen | Seznam, Double, komplexní | Konkrétní typy jsou struktury, třídy, výčty, delegáti, záznamů a sjednocení. I když jsou tradičně malá písmena v OCaml, názvy typů F# přijala schéma pojmenování .NET pro typy.
| knihovny DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| Sjednocení značky     | PascalCase | Podstatné jméno | Některé, přidat, úspěch | Nepoužívejte předponu ve veřejných rozhraní API. Volitelně použijte předponu, když je to interní, jako například `type Teams = TAlpha | TBeta | TDelta.` |
| Událost          | PascalCase | Příkaz | ValueChanged / ValueChanging |  |
| Výjimky     | PascalCase |      | WebException | Název by měl končit "Výjimek". |
| Pole          | PascalCase | Podstatné jméno | CurrentName  | |
| Typy rozhraní |  PascalCase | Podstatné jméno / tvary přídavných jmen | Rozhraní IDisposable | Název by měl začínat "I". |
| Metoda |  PascalCase |  Příkaz | ToString | |
| Obor názvů | PascalCase | | Microsoft.FSharp.Core | Obvykle používají `<Organization>.<Technology>[.<Subnamespace>]`, i když vyřadit organizace, pokud se tato technologie je nezávislé na organizaci. |
| Parametry | camelCase | Podstatné jméno |  typeName, transformace, rozsahu | |
| umožní hodnoty (interní) | camelCase nebo formátu PascalCase | Podstatné jméno / příkaz |  getValue myTable |
| umožní hodnoty (externí) | camelCase nebo formátu PascalCase | Podstatné jméno/příkaz  | List.map Dates.Today | vazbou let hodnoty jsou často veřejné, pokud následující vzory návrhu tradiční funkční. Ale obecně používejte PascalCase identifikátor lze použít v jiných jazycích rozhraní .NET. |
| Vlastnost  | PascalCase  | Podstatné jméno / tvary přídavných jmen  | IsEndOfFile, BackColor  | Logické vlastnosti obecně použití je a můžete a musí být kladná, stejně jako v IsEndOfFile, ne IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Vyhněte se zkratky

Pokyny .NET bránit použití zkratky (například "použít `OnButtonClick` spíše než `OnBtnClick`"). Běžné zkratky, jako například `Async` pro "Asynchronní", jsou tolerovat. Toto pravidlo je někdy ignorován pro funkční programování. například `List.iter` používá zkratkou pro "iterovat". Z tohoto důvodu pomocí zkratky obvykle tolerovat do značné míry v F#- na -F# programování, ale mělo by se vyhnout stále obecně veřejné součásti návrhu.

#### <a name="avoid-casing-name-collisions"></a>Vyhněte se malá a velká písmena kolize názvů

Pokyny .NET Řekněme, že malá a velká písmena samostatně nelze použít k rozlišení kolize názvů, protože některé jazyky klienta (například Visual Basic) jsou malá a velká písmena.

#### <a name="use-acronyms-where-appropriate"></a>Použití zkratky, kde je to vhodné

Zkratky, jako je například XML nejsou zkratky a běžně používané knihovny .NET v podobě nezačínající (Xml). Pouze by měla sloužit dobře známou a široce uznávané zkratky.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Použít pro obecný parametr názvy PascalCase

Pomocí PascalCase pro obecný parametr názvy ve veřejných rozhraní API, včetně F#-směřující knihovny. Zejména použijte názvy jako `T`, `U`, `T1`, `T2` pro libovolný obecných parametrů a konkrétní názvy dávat smysl, pak F#– různé knihovny používají názvy jako `Key`, `Value`, `Arg` (ale ne třeba `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Pomocí PascalCase nebo camelCase pro veřejné funkce a hodnoty v F# moduly

camelCase se používá pro veřejné funkce, které jsou určeny pro použití nekvalifikované (například `invalidArg`) a pro "funkce standardní kolekce" (například List.map). V obou těchto případech se názvy funkcí fungují podobně jako klíčová slova v jazyce.

### <a name="object-type-and-module-design"></a>Objekt, typ a modul návrhu

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Použití oboru názvů nebo moduly tak, aby obsahovala modulů a typů

Každý F# soubor v komponentě by měl začínat deklarace oboru názvů nebo modulu deklarace.

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

or

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

Rozdíly mezi použitím modulů a oborů názvů k uspořádání kódu na nejvyšší úrovni jsou následující:

* Obory názvů může zahrnovat více souborů
* Obory názvů nemůžou obsahovat F# funkce, které nejsou v rámci vnitřní modul
* Kód pro libovolný daný modul musí být obsažena v rámci jednoho souboru
* Moduly nejvyšší úrovně může obsahovat F# funkce bez nutnosti pro vnitřní modul

Volba mezi nejvyšší úrovně oboru názvů nebo modulu ovlivňuje kompilovaný formy kód a proto bude mít vliv na zobrazení z jiných jazyků .NET by vaše rozhraní API nakonec využívat mimo F# kódu.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Použijte metody a vlastnosti pro operace, které jsou přirozené pro typy objektů

Při práci s objekty, je nejvhodnější zajistit, že použitelné funkce je implementovaná jako metody a vlastnosti tohoto typu.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

Hromadné funkce pro daný člen nemusí nutně je implementovat do tohoto člena, ale by měl být použitelné částí, které tuto funkci.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Použití tříd k zapouzdření proměnlivý stav

V F#, to jenom je potřeba udělat kde, stav se už zapouzdřená pomocí konstrukce jazyka, jako je například uzávěru, výrazu pořadí nebo asynchronní výpočet.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Pomocí rozhraní můžete seskupovat související operace

Představuje sadu operací pomocí typy rozhraní. Toto je upřednostňována před další možnosti, jako je například řazených kolekcí členů, funkcí nebo záznamy o funkce.

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

V preference pro:

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

Rozhraní jsou prvotřídní koncepty v .NET, která vám umožní dosáhnout co Funktory by obvykle poskytují. Kromě toho se můžete použít ke kódování existenční typů do programu, který zaznamenává funkce nelze.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Použít modul a funkce skupiny, které fungují v kolekcích

Při definování typu kolekce vezměte v úvahu poskytuje standardní sadu operací, jako jsou `CollectionType.map` a `CollectionType.iter`) pro nové typy kolekcí.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Pokud zahrnete tyto modul, použijte standardní zásady vytváření názvů pro funkce v FSharp.Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Použít modul a funkce skupiny pro běžné, kanonické funkce, zejména v matematické a knihovny DSL

Například `Microsoft.FSharp.Core.Operators` je automaticky otevřené kolekce funkce nejvyšší úrovně (třeba `abs` a `sin`) poskytované FSharp.Core.dll.

Obdobně statistiky knihovny mohou zahrnovat modul s funkcí `erf` a `erfc`, ve kterém se tento modul slouží k explicitně nebo automaticky otevřít.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Zvažte použití RequireQualifiedAccess a pečlivě použití AutoOpen atributů

Přidávání `[<RequireQualifiedAccess>]` atribut do modulu označuje, že modul nelze otevřít, a přístup, vyžaduje explicitní odkazy na elementy modulu kvalifikovaný. Například `Microsoft.FSharp.Collections.List` modul nemá tento atribut.

To je užitečné, když funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v dalších modulů. Které vyžadují přístup pro kvalifikovaný může výrazně zvýšit dlouhodobou udržovatelnost a ovlivňujících knihovny.

Přidávání `[<AutoOpen>]` atribut do modulu znamená, že modul se otevřou při otevření nadřazeného oboru názvů. `[<AutoOpen>]` Atribut může také použít k sestavení k označení modulu, který se automaticky otevře, když na toto sestavení odkazuje.

Například knihovna statistiky **MathsHeaven.Statistics** může obsahovat `module MathsHeaven.Statistics.Operators` obsahující funkce `erf` a `erfc`. Je možné logicky označit tento modul jako `[<AutoOpen>]`. To znamená, že `open MathsHeaven.Statistics` také otevřít tento modul a převést názvy `erf` a `erfc` do oboru. Použití jiného dobré `[<AutoOpen>]` je pro moduly obsahující metody rozšíření.

Nadměrné použití z `[<AutoOpen>]` potenciálních zákazníků na znečištěné obory názvů a atribut by měla být používána opatrně. Pro konkrétní knihovny z určitých domén, rozumné využívání `[<AutoOpen>]` může mít za následek lepší použitelnost.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Definovat operátor členy ve třídách, kdy je vhodné pomocí známých operátorů

Někdy třídy se používají k modelování matematické konstrukce, jako jsou vektory. Pokud má doména modelovaných dobře známých operátorů, je definují jako členy, které jsou přirozené pro třídu je užitečné.

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Tyto doprovodné materiály odpovídá obecné pokyny .NET pro tyto typy. Však může být také důležité v F# psaní kódu, jako to umožňuje těchto typů, který se má použít ve spojení s F# funkcí a metod s omezeními členů, jako je například List.sumBy.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Zvažte použití compiledname – pro zajištění. NET – popisný název pro ostatní uživatelé jazyka .NET

Někdy můžete chtít název ve stylu jeden pro F# příjemci (třeba statický člen malými písmeny, tak že se objeví jako by šlo modulu vázané funkce), ale mají jiný styl pro název při kompilaci do sestavení. Můžete použít `[<CompiledName>]` atribut zadejte jiný styl pro jiné F# využívání sestavení kódu.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

S použitím `[<CompiledName>]`, můžete použít zásady vytváření názvů .NET pro jiné F# příjemci sestavení.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Použijte přetížení metody pro členské funkce, pokud to poskytuje rozhraní API jednodušší

Přetížení metody je výkonný nástroj pro zjednodušení rozhraní API, které může být zapotřebí provést podobné funkce, ale s jinou možností nebo argumenty.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

V F#, je běžné přetížení na počet argumentů, spíše než typy argumentů.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Skrýt reprezentace záznam a typy sjednocení, pokud návrh z těchto typů je pravděpodobně rozvoj

Zamezení odhalení konkrétní reprezentace objektů. Například konkrétní reprezentace <xref:System.DateTime> hodnoty neposkytuje externí, veřejné rozhraní API návrhu knihovny .NET. V době běhu modul Common Language Runtime ví potvrzené implementace, která se použije v průběhu provádění. Ale zkompilovaný kód nebude sám sbírání závislosti na konkrétní reprezentace.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Vyhněte se použití implementace dědičnosti pro rozšíření

V F#, implementace dědičnosti je zřídka se používá. Hierarchie dědičnosti jsou navíc často složité a těžko změnit příchod nové požadavky. Implementace dědičnosti se stále nachází v F# pro kompatibilitu a výjimečných případech, kdy je nejlepší řešení problému, ale alternativní postupy, které se má hledat v vaše F# programy při návrhu pro polymorfismus, jako je například rozhraní implementace.

### <a name="function-and-member-signatures"></a>Funkce a člen podpisy

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Použití řazených kolekcí členů pro vrácené hodnoty při vrácení malý počet víc nesouvisejících hodnot

Tady je typickým příkladem použití řazené kolekce členů v návratovém typu:

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

Návratové typy obsahující mnoho komponent, nebo pokud komponenty se vztahují k jedné entity identifikovatelné, zvažte použití pojmenovaného typu namísto řazené kolekce členů.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Použití `Async<T>` pro asynchronní programování v F# hranice rozhraní API

Pokud je odpovídající synchronní operace s názvem `Operation` , která vrací `T`, pak by měl být pojmenován asynchronní operace `AsyncOperation` vrátí-li `Async<T>` nebo `OperationAsync` vrátí-li `Task<T>`. Pro běžně používané typy .NET, která zpřístupňují metody Begin/End, zvažte použití `Async.FromBeginEnd` zápis rozšiřující metody jako adaptační vrstva poskytnout F# asynchronní programovací model pro tato rozhraní API pro .NET.

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Výjimky

Zobrazit [Správa chyb](conventions.md#error-management) Další informace o řádném používání výjimky, výsledky a možnosti.

### <a name="extension-members"></a>Členy rozšíření

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Pečlivě použít F# členy rozšíření v F#- na -F# komponenty

F#členy rozšíření by měla obecně sloužit pouze pro operace, které jsou v tomto uzávěru vnitřní operace spojené s typem ve většině režimech použití. Jeden společný slouží k poskytování rozhraní API, která jsou k více idiomatickou F# pro různé typy .NET:

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>Typy sjednocení

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Používat rozlišovaných unionů místo hierarchií tříd stromovou strukturou dat

Jako stromové struktury jsou definované rekurzivně. Toto je nevhodnou s dědičnosti, ale elegantní s rozlišovaná sjednocení.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Představující data jako stromové struktury s Rozlišované sjednocení také umožňuje využívat úplnosti v porovnávání vzorů.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Použití `[<RequireQualifiedAccess>]` na názvy případu nejsou dostatečně jedinečné typy sjednocení

Může být pro vás sami v doméně, kde je nejlepší název pro různé věci, jako je například rozlišovaného sjednocení s případy se stejným názvem. Můžete použít `[<RequireQualifiedAccess>]` k rozlišení velikosti písmen názvů, pokud se chcete vyhnout, aktivuje se matoucí chyby vzniklé v důsledku stínováním závisí na řazení `open` příkazy

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Skrýt reprezentace rozlišovaná sjednocení binární kompatibilních rozhraní API, pokud návrh z těchto typů je pravděpodobně rozvoj

Typy sjednocení se opírají o F# porovnávání vzorů formulářů stručné programovací model. Jak už bylo zmíněno dříve, měli byste se vyhnout, odhalení reprezentace konkrétní data, pokud je pravděpodobné vyvíjí, návrh tyto typy.

Například reprezentace diskriminované sjednocení může být skrytá používání soukromý nebo interní prohlášení, nebo pomocí souboru podpisu.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Pokud uvedete rozlišovaná sjednocení bez, možná bude obtížné verze knihovny bez narušení uživatelského kódu. Místo toho zvažte odhalení nejmíň jeden aktivní vzory tak, aby povolovala porovnávání vzorů přes hodnoty stejného typu.

Aktivní vzory poskytují alternativní způsob, jak poskytnout F# zákazníky prostřednictvím porovnávání vzorů při obcházení vystavení F# přímo typy sjednocení.

### <a name="inline-functions-and-member-constraints"></a>Vložené funkce a členská omezení

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Definujte obecná numerické algoritmy použití vložených funkcí s staticky řešeného obecné typy a předpokládané členská omezení

Aritmetické členská omezení a F# porovnání omezení jsou standardní pro F# programování. Zvažte například následující kód:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Typ této funkce je následujícím způsobem:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Toto je vhodná funkce pro veřejné rozhraní API v matematické knihovně.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Vyhněte se použití členská omezení pro simulaci typu třídy a duck psaní

Je možné simulovat pomocí "duck psát" F# omezeními člena. Ale členy, které pomocí tohoto objektu není v obecné je třeba použít F#- na -F# návrhy knihovny. Je to proto, že knihovna návrhy založené na neznámého nebo nestandardní implicitní omezení vést k uživatelský kód pro nepřizpůsobitelným a vázané na jednu konkrétní architekturu vzor.

Kromě toho je vhodné šance, že se hojně používají členská omezení tímto způsobem může vést k velmi dlouhé kompilace časy.

### <a name="operator-definitions"></a>Definice – operátor

#### <a name="avoid-defining-custom-symbolic-operators"></a>Vyhněte se definování vlastní symbolické operátory

Vlastní operátory jsou nezbytné v některých situacích a jsou velmi užitečné konvenční zařízení v rámci rozsáhlý implementační kód. Pro nové uživatele do knihovny jsou často pojmenované funkce usnadňuje používání. Kromě toho vlastní symbolické operátory může být obtížné dokumentů a uživatelé najdou obtížnější k vyhledání nápovědy operátorů, protože existující v integrovaném vývojovém prostředí a hledání.

V důsledku toho je nejvhodnější publikovat vaše funkce jako pojmenované funkce a členy a kromě toho zpřístupnit operátory pro tuto funkci pouze v případě, že konvenční výhody převáží nad dokumentace a kognitivní náklady s nimi.

### <a name="units-of-measure"></a>Měrné jednotky

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Pečlivě použít měrné jednotky pro přidání typovou bezpečnost v F# kódu

Další informace o psaní za jednotky měření se vymažou při prohlížení jinými jazyky rozhraní .NET. Mějte na paměti, že součásti rozhraní .NET, nástroje a reflexe se zobrazí typy sítí SAN jednotky. Například C# uživatelé uvidí `float` spíše než `float<kg>`.

### <a name="type-abbreviations"></a>Zkratky typů

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Zkratky typů pečlivě slouží ke zjednodušení F# kódu

Součásti rozhraní .NET, nástroje a reflexe nezobrazí zkrácené názvy typů. Významné použití zkratek typů lze také nastavit domény zobrazí složitější, než kolik jich je skutečně, který by mohl zaměnit příjemci.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Zkratky typů pro veřejné typy, členy a vlastnosti by měla být vnitřně liší od těch, které jsou k dispozici na na typ, který se u zkracovaného vyhnout

V takovém případě typ, který se u zkracovaného odhalí příliš mnoho o reprezentaci skutečný typ definuje. Místo toho zvažte možnost uzavřít – zkratka typu třídy nebo diskriminované sjednocení jedním případem (nebo když zásadní je výkon, zvažte použití typu Struktura zabalit zkratky).

Je třeba chtěli definovat více mapy jako speciální případ F# namapovat, například:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Ale operace logického tečkami u tohoto typu nejsou stejná jako operace na mapě – například je možné logicky, že operátor vyhledávání mapy. [klíče] vrátí prázdný seznam, pokud není klíč ve slovníku, namísto vyvolání výjimky.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Pokyny pro knihovny pro použití v jiných jazycích rozhraní .NET

Při navrhování knihoven pro použití v jiných jazycích .NET, je potřeba dodržovat [pokyny k návrhu knihovny .NET](../../standard/design-guidelines/index.md). V tomto dokumentu tyto knihovny jsou označeny jako vanilla knihovny .NET, nikoli F#-směřující knihoven, které používají F# sestaví bez omezení. Navrhování vanilla knihovny .NET znamená, že znáte a jsou idiomatickou API, konzistentní se zbytkem rozhraní .NET Framework poskytuje minimalizací použití F#-konkrétní konstrukce ve veřejném rozhraní API. Pravidla jsou vysvětlené v následujících částech.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Navrhování Namespace a typ (pro knihovny pro použití v jiných jazycích rozhraní .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Použít zásady vytváření názvů .NET pro veřejné rozhraní API součásti

Věnujte zvláštní pozornost použití zkrácené názvy a pokyny .NET malá a velká písmena.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Použijte obory názvů, typy a členy jako primární organizační struktury komponent

Všechny soubory, které obsahují veřejná funkce by měl začínat `namespace` deklaraci a jenom veřejně přístupných entity v oborech názvů by měl být typy. Nepoužívejte F# moduly.

Použijte neveřejné moduly pro uložení implementační kód, typy nástrojů a funkcí nástroje.

Statické typy by měly být upřednostňované nad modulů, protože umožňují pro budoucí vývoj rozhraní API použít přetížení a dalších konceptech rozhraní .NET API návrhu, které se nedá použít v F# moduly.

Například místo následující veřejné rozhraní API:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Zvažte místo toho:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Použití F# typy záznamů v vanilla rozhraní API pro .NET, pokud nebude vyvíjí návrhu typy

F#typy záznamů se kompilují do jednoduchého třída rozhraní .NET. Toto jsou vhodné pro některé jednoduché a stabilní typy v rozhraní API. Měli byste zvážit použití `[<NoEquality>]` a `[<NoComparison>]` atributů, které mají potlačit automatické generování rozhraní. Také Vyhněte se použití pole proměnlivé záznam v vanilla rozhraní .NET API jako tyto zpřístupňuje veřejné pole. Vždy zvažte, zda by třída poskytují pružnější možnosti pro budoucí vývoj rozhraní API.

Například následující F# kód poskytuje veřejné rozhraní API C# příjemce:

F#:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

C#:

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Skrýt reprezentace F# sjednocovacím typům v vanilla rozhraní API pro .NET

F#typy sjednocení nejsou používány často přes hranice součástí to i v případě F#- na -F# psaní kódu. Jsou zařízení s vynikající implementaci při použití interně v rámci komponenty a knihovny.

Při navrhování vanilla rozhraní API .NET, vezměte v úvahu skrytí reprezentací typu union s použitím privátní prohlášení nebo soubor s podpisem.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Může také rozšířit typy, které používají reprezentaci typu union s členy interně k poskytování požadované. NET přístupem k rozhraní API.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Návrh grafického uživatelského rozhraní a další komponenty pomocí návrhové vzory architektury

K dispozici mnoho různých rozhraní v rámci .NET, jako je ASP.NET, WinForms a WPF. Konvence pojmenování a návrh pro každý by měl použít, pokud navrhujete komponenty pro použití v tyto architektury. Například pro WPF programování, použijte WPF vzory návrhu pro třídy, kterou navrhujete. Pro modely v programování uživatelské rozhraní, použijte vzorů návrhu, jako je například události a kolekcí založených na oznámení, jako jsou ty uvedené v <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Návrh objektů a členů (pro knihovny pro použití v jiných jazycích rozhraní .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Vystavení události .NET pomocí clievent – atribut

Vytvořit `DelegateEvent` s konkrétní .NET typ, který přebírá objekt delegáta a `EventArgs` (spíše než výjimku `Event`, který právě používá `FSharpHandler` typ ve výchozím nastavení) tak, aby se události publikují známé způsobem, který jinými jazyky rozhraní .NET.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Vystavení asynchronních operací jako metody, které vracejí úlohy .NET

Úkoly se používají v .NET představující aktivní asynchronní výpočty. Úlohy jsou obecně menší složení než F# `Async<T>` objekty, protože představují "již provádění" úkoly a nemůže skládat dohromady způsoby, které provádí paralelní složení nebo které skrýt šíření zrušení signály a ostatní kontextové parametry.

Bez ohledu na to, jsou metody, které vracejí úlohy standardní reprezentace asynchronní programování v rozhraní .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Často budete také chtít přijmout explicitní rušícího tokenu:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Použití .NET typy delegátů namísto F# funkce typy

Tady "F# funkce typy" znamená "šipka" typy, jako jsou `int -> int`.

Namísto toto:

```fsharp
member this.Transform(f: int->int) =
    ...
```

postupujte takto:

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

F# Typ funkce se zobrazí jako `class FSharpFunc<T,U>` do jiných jazyků .NET a je méně vhodná pro jazykové funkce a nástroje, které rozumí typy delegátů. Při vytváření vyššího řádu metoda cílí na rozhraní .NET Framework 3.5 nebo vyšší, `System.Func` a `System.Action` Delegáti jsou správné rozhraní API pro publikování a umožňuje vývojářům .NET způsobem bezproblémové využití těchto rozhraní API. (Při cílení na rozhraní .NET Framework 2.0, jsou omezeny více typy definované v systému delegáta; zvažte použití delegáta předdefinované typy, jako `System.Converter<T,U>` nebo definování konkrétního delegáta typu.)

Na druhou stranu, nejsou přirozené pro delegáty rozhraní .NET F#-směřující knihovny (naleznete v další části F#-směřující knihovny). V důsledku toho je běžné strategie implementace při vývoji vyššího řádu metody pro vanilla knihovny .NET pro vytváření všech na implementaci pomocí F# funkce typů a pak vytvořte veřejné rozhraní API pomocí delegátů jako adaptační vrstva dynamického zajišťování imitovaná skutečné F#implementace.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Použití vzoru TryGetValue místo vrácení F# hodnot a dáváte přednost přetížení metody k pořízení F# možnost hodnoty jako argumenty

Obecné vzory pro použití F# typ možnosti v rozhraní API jsou lepší implementované v vanilla návrh rozhraní API .NET pomocí rozhraní .NET standard techniky. Místo vrácení F# hodnotu možnosti, zvažte použití návratový typ bool plus výstupní parametr jako vzor "TryGetValue". A místo pořízení F# možnost hodnoty jako parametry, zvažte použití metody přetížení nebo volitelné argumenty.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Použití rozhraní .NET kolekci typů IEnumerable\<T\> a IDictionary\<klíč, hodnota\> pro parametry a návratové hodnoty

Vyhněte se použití konkrétní kolekci typů jako je například pole .NET `T[]`, F# typy `list<T>`, `Map<Key,Value>` a `Set<T>`, a typy, jako konkrétní kolekci .NET `Dictionary<Key,Value>`. Pokyny pro návrh knihovny .NET mají dobrou Rady týkající se použití různé typy kolekcí, jako je `IEnumerable<T>`. Některé použití polí (`T[]`) přijatelná v některých případech z důvodů výkonu. Všimněte si, že zejména `seq<T>` je jenom F# alias pro `IEnumerable<T>`, a proto je sekvence často odpovídající typ pro vanilla rozhraní .NET API.

Místo F# uvádí:

```fsharp
member this.PrintNames(names: string list) =
    ...
```

Použití F# pořadí:

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Použijte typ jednotky jako pouze vstupní typ metody k definici metody argumentu nula, nebo jako jediná návratový typ pro definování metody vracející hodnotu void

Vyhněte se dalších možnostech použití typu jednotky. Toto jsou dobré:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

Toto je chybný:

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Kontrola hodnot null na hranicích vanilla rozhraní .NET API

F#implementace kódu obvykle má menší počet hodnot null, z důvodu neměnné návrhových postupů a omezení použití literály s hodnotou null pro F# typy. Jinými jazyky rozhraní .NET často použít null jako hodnotu mnohem častěji. Z tohoto důvodu F# kód, který vystavuje vanilla rozhraní .NET API by měl Zkontrolujte parametry pro hodnotu null na hranici rozhraní API a zabránit toku hlouběji do těchto hodnot F# implementační kód. `isNull` Funkce nebo porovnávání vzorů `null` vzor lze použít.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Nepoužívejte řazené kolekce členů jako návratové hodnoty

Místo toho raději vracející typ s názvem držením agregovaná data, nebo použití výstupním parametrů vrátit více hodnot. I když existují řazených kolekcí členů a strukturovaných řazených kolekcí členů v rozhraní .NET (včetně C# – jazyková podpora strukturovaných řazených kolekcí členů), se nejčastěji není poskytují ideální a očekávané rozhraní API pro vývojáře na platformě .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Nepoužívejte curryfikace parametrů

Místo toho použijte .NET konvence volání `Method(arg1,arg2,…,argN)`.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Tip: Pokud vytváříte knihovny pro použití v kterémkoli jazyce platformy .NET, pak náhradu ve skutečnosti je některé experimentální C# a programování a zkontrolujte, že knihoven "chování přímo" z těchto jazyků Visual Basic. Nástroje, jako je .NET Reflector a prohlížeče objektů služby Visual Studio můžete použít také k zajištění, že knihovny a jejich dokumentaci zobrazují podle očekávání pro vývojáře.

## <a name="appendix"></a>Příloha

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Příklad návrhu začátku do konce F# kód pro použití jinými jazyky rozhraní .NET

Vezměte v úvahu následující třídy:

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

Odvozené F# typ této třídy je následujícím způsobem:

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

Pojďme se podívat na to, jak to F# typu se zobrazí na programátorovi použít jiný jazyk .NET. Přibližná jazyka C# "podpis" je například následujícím způsobem:

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Existují některé důležité body, které Všimněte si, jak F# představuje vytvoří tady. Příklad:

* Byla zachována metadat – například názvy argumentů.

* F#metody, které přebírají dva argumenty, které se stanou C# metodám, které přebírají dva argumenty.

* Funkce a seznamy budou odkazy na odpovídající typy v F# knihovny.

Následující kód ukazuje, jak upravit tento kód vzít v úvahu Tyhle věci.

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

Odvozené F# typ kódu vypadá takto:

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

Signatura jazyka C# je teď následujícím způsobem:

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Tyto opravy provedli připravili k použití tohoto typu, jako součást vanilla knihovny .NET jsou následující:

* Upravit několik názvů: `Point1`, `n`, `l`, a `f` začal být `RadialPoint`, `count`, `factor`, a `transform`v uvedeném pořadí.

* Používá typ vrácené hodnoty `seq<RadialPoint>` místo `RadialPoint list` změnou seznamu pomocí konstrukce `[ ... ]` pořadí konstrukce pomocí `IEnumerable<RadialPoint>`.

* Používá typ delegáta .NET `System.Func` místo F# typ funkce.

Díky tomu je mnohem nicer využívat v kódu jazyka C#.
