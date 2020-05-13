---
title: Pravidla návrhu komponent jazyka F#
description: 'Přečtěte si pokyny pro zápis komponent F #, které jsou určené pro využití jinými volajícími.'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209133"
---
# <a name="f-component-design-guidelines"></a>Pravidla návrhu komponent jazyka F#

Tento dokument je sada pokynů pro návrh komponent pro programování v jazyce F # na základě pokynů pro návrh součástí F #, v14, Microsoft Research a verze, která byla původně založena a udržována společností F # Software Foundation.

Tento dokument předpokládá, že máte zkušenosti s programováním v jazyce F #. Mnoho je od komunity F # pro své příspěvky a užitečnou zpětnou vazbu k různým verzím tohoto průvodce.

## <a name="overview"></a>Přehled

Tento dokument popisuje některé problémy související s návrhem a kódováním komponenty F #. Komponenta může znamenat některý z následujících prvků:

* Vrstva v projektu F #, která obsahuje externí uživatele v rámci daného projektu.
* Knihovna určená pro použití v kódu F # napříč hranicemi sestavení.
* Knihovna určená pro využití jakýmkoli jazykem .NET napříč hranicemi sestavení.
* Knihovna určená k distribuci prostřednictvím úložiště balíčků, například [NuGet](https://nuget.org).

Techniky popsané v tomto článku se řídí [pěti zásadami dobrého kódu F #](index.md#five-principles-of-good-f-code)a využívají jak to vhodné, tak i programování objektů.

Bez ohledu na metodologii Návrhář komponent a knihoven čelí řadě praktických a prosaicch problémů při pokusu o vytvoření rozhraní API, které je nejsnáze použitelné pro vývojáře. Conscientious použití pokynů pro [Návrh knihovny .NET](../../standard/design-guidelines/index.md) vám umožní vytvořit konzistentní sadu rozhraní API, která jsou příjemný pro využívání.

## <a name="general-guidelines"></a>Obecné pokyny

Existuje několik univerzálních pokynů, které se vztahují na knihovny F # bez ohledu na zamýšlenou cílovou skupinu pro danou knihovnu.

### <a name="learn-the-net-library-design-guidelines"></a>Seznamte se s pokyny pro návrh knihovny .NET.

Bez ohledu na druh kódování F #, které provádíte, je důležité mít praktické znalosti s [pokyny pro návrh knihovny .NET](../../standard/design-guidelines/index.md). Většina ostatních programátorů F # a .NET bude tyto pokyny znát a očekává, že kód .NET bude v souladu s nimi.

Pokyny k návrhu knihovny .NET poskytují obecné pokyny týkající se pojmenovávání, navrhování tříd a rozhraní, návrh členů (vlastnosti, metody, události atd.) a další informace a jsou užitečné první směrové reference pro celou řadu pokynů k návrhu.

### <a name="add-xml-documentation-comments-to-your-code"></a>Přidání dokumentačních komentářů XML do kódu

Dokumentace XML na veřejných rozhraních API zajišťuje, že uživatelé mohou při použití těchto typů a členů získat skvělé technologie IntelliSense a QuickInfo a povolit vytváření souborů dokumentace pro knihovnu. V [dokumentaci XML](../language-reference/xml-documentation.md) o různých značkách XML, které lze použít pro další značky v komentářích xmldoc.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

Můžete použít buď krátký formát komentáře XML ( `/// comment` ), nebo standardní komentáře XML ( `///<summary>comment</summary>` ).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Zvažte použití explicitních podpisových souborů (. fsi) pro stabilní rozhraní API knihoven a komponent.

Použití explicitních signatur souborů v knihovně F # poskytuje stručné shrnutí veřejného rozhraní API, které pomáhá zajistit, že znáte plný veřejný povrch vaší knihovny a poskytuje čisté oddělení mezi veřejnou dokumentací a interními podrobnostmi implementace. Soubory signatury přidávají tření ke změně veřejného rozhraní API tím, že vyžadují změny provedené v souborech implementace i signatury. V důsledku toho by se soubory signatury měly obvykle zavádět jenom v případě, že se rozhraní API stane solidified a už se neočekává, že se významně změní.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Vždy dodržujte osvědčené postupy pro používání řetězců v rozhraní .NET

Dodržujte [osvědčené postupy pro používání řetězců v](../../standard/base-types/best-practices-strings.md) doprovodnéch materiálech k rozhraní .NET. Konkrétně vždy explicitně uveďte *kulturní záměr* v převodu a porovnávání řetězců (kde je to možné).

## <a name="guidelines-for-f-facing-libraries"></a>Pokyny pro knihovny orientované na F #

Tato část obsahuje doporučení pro vývoj veřejných knihoven založených na jazyce F #. To znamená, že knihovny zveřejňují veřejná rozhraní API, které mají být spotřebovány vývojáři jazyka F #. Existuje celá řada doporučení pro návrh knihoven, která se týkají konkrétně F #. Pokud nejsou k dispozici konkrétní doporučení, jsou pokyny pro návrh knihovny .NET základní doprovodné materiály.

### <a name="naming-conventions"></a>Zásady vytváření názvů

#### <a name="use-net-naming-and-capitalization-conventions"></a>Používání konvencí pojmenování a psaní velkých písmen v .NET

Následující tabulka sleduje konvence pojmenování a psaní velkých písmen v .NET. K dispozici jsou malé dodatky, které obsahují také konstrukce F #.

| Konstrukce | Obchodní případ | Část | Příklady | Poznámky |
|-----------|------|------|----------|-------|
| Konkrétní typy | PascalCase | Podstatné jméno/přídavné jméno | List, Double, Complex | Konkrétní typy jsou struktury, třídy, výčty, delegáti, záznamy a sjednocení. I když názvy typů jsou tradičně malé písmeno v OCaml, F # přijalo schéma pojmenování .NET pro typy.
| knihovny DLL           | PascalCase |                 | Fabrikam. Core. dll |  |
| Sjednocení značek     | PascalCase | Podstatné jméno | Nějaké, přidání, úspěch | Ve veřejných rozhraních API nepoužívejte předponu. Volitelně můžete použít předponu, pokud interní, například`type Teams = TAlpha | TBeta | TDelta.` |
| Událost          | PascalCase | Příkaz | ValueChanged / ValueChanging |  |
| Výjimky     | PascalCase |      | WebException | Název by měl končit "výjimkou". |
| Pole          | PascalCase | Podstatné jméno | Current  | |
| Typy rozhraní |  PascalCase | Podstatné jméno/přídavné jméno | IDisposable | Název by měl začínat na "I". |
| Metoda |  PascalCase |  Příkaz | ToString | |
| Obor názvů | PascalCase | | Microsoft. FSharp. Core | Obecně používejte `<Organization>.<Technology>[.<Subnamespace>]` , ale odřaďte organizaci, pokud je technologie nezávislá na organizaci. |
| Parametry | camelCase | Podstatné jméno |  typeName, Transform, rozsah | |
| Povolit hodnoty (interní) | camelCase nebo PascalCase | Podstatné jméno/příkaz |  GetValue, myTable |
| Povolit hodnoty (externí) | camelCase nebo PascalCase | Podstatné jméno/příkaz  | List. map, dates. Today | hodnoty manuálních vazeb jsou často veřejné, pokud následují tradiční vzory návrhu funkcí. Nicméně obecně používejte PascalCase, pokud je možné identifikátor použít z jiných jazyků .NET. |
| Vlastnost  | PascalCase  | Podstatné jméno/přídavné jméno  | IsEndOfFile, BackColor  | Logické vlastnosti obecně používají hodnotu a můžou být kladné, jako v IsEndOfFile, ne IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Vyhnout se zkratkám

Pokyny rozhraní .NET nebrání použití zkratek (například "použít `OnButtonClick` místo `OnBtnClick` "). Společné zkratky, například `Async` pro "asynchronní", jsou tolerovány. Tento návod se někdy ignoruje pro funkční programování; například `List.iter` používá zkratku pro "ITER". Z tohoto důvodu je použití zkratek v programovacím jazyce F # do-F # tolerováno, ale při návrhu veřejné součásti by se však mělo obecně vyhnout.

#### <a name="avoid-casing-name-collisions"></a>Vyhnout se kolizí názvů malých a velkých písmen

Pokyny pro rozhraní .NET říkají, že samotný velká a malá písmena nelze použít k rozlišení kolizí názvů, protože některé jazyky klienta (například Visual Basic) rozlišují malá a velká písmena.

#### <a name="use-acronyms-where-appropriate"></a>Použijte akronymy tam, kde je to vhodné

Akronymy jako XML nejsou zkratky a jsou široce používány v knihovnách .NET v netučném formátu (XML). Měly by se používat jenom známé, široce rozpoznané zkratky.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Použití PascalCase pro názvy obecných parametrů

Použijte PascalCase pro názvy obecných parametrů ve veřejných rozhraních API, včetně pro knihovny založené na F #. Konkrétně použijte názvy jako,, `T` `U` `T1` , `T2` pro libovolný obecný parametr a, pokud jsou specifické názvy, potom pro knihovny pro jazyk F # použijte názvy, například, `Key` , (nikoli například `Value` `Arg` `TKey` ).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Pro veřejné funkce a hodnoty v modulech F # použijte buď PascalCase, nebo camelCase.

camelCase se používá pro veřejné funkce, které jsou navržené tak, aby se používaly jako nekvalifikované (například `invalidArg` ), a pro "standardní funkce shromažďování" (například list. map). V obou těchto případech se názvy funkcí chovají podobně jako klíčová slova v jazyce.

### <a name="object-type-and-module-design"></a>Návrh objektu, typu a modulu

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Použijte obory názvů nebo moduly, které obsahují vaše typy a moduly.

Každý soubor F # v komponentě by měl začínat buď deklarací oboru názvů, nebo deklarací modulu.

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

* Obory názvů můžou zahrnovat víc souborů.
* Obory názvů nemůžou obsahovat funkce F #, pokud nejsou v rámci vnitřního modulu.
* Kód pro daný modul musí být obsažen v rámci jednoho souboru.
* Moduly nejvyšší úrovně můžou obsahovat funkce jazyka F # bez nutnosti interního modulu.

Volba mezi oborem názvů nebo modulem na nejvyšší úrovni má vliv na zkompilované formy kódu, a proto ovlivní zobrazení z jiných jazyků .NET by mělo být vaše rozhraní API nakonec spotřebováno mimo kód F #.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Použití metod a vlastností pro vnitřní operace s typy objektů

Při práci s objekty je vhodné zajistit, aby se funkce spotřebních funkcí implementovaly jako metody a vlastnosti tohoto typu.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

Hromadná funkčnost daného člena nemusí být nutně implementovaná v tomto členu, ale spotřební část této funkce by měla být.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Použití tříd k zapouzdření proměnlivého stavu

V F # stačí, když tento stav není zapouzdřený jinou jazykovou konstrukcí, jako je například uzavření, výraz sekvence nebo asynchronní výpočty.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Seskupení souvisejících operací pomocí rozhraní

Použijte typy rozhraní, které reprezentují sadu operací. Jedná se o preferované možnosti, jako jsou například řazené kolekce členů funkcí nebo záznamů funkcí.

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

V upřednostňovaném pořadí:

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

Rozhraní jsou koncepty první třídy v rozhraní .NET, které můžete použít k dosažení, k čemu by vám funktory normálně dodávat. Kromě toho mohou být použity ke kódování existenční typů do programu, které záznamy funkcí nemůžou.

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a>Použití modulu k seskupení funkcí, které fungují na kolekcích

Při definování typu kolekce zvažte poskytnutí standardní sady operací jako `CollectionType.map` a `CollectionType.iter` ) pro nové typy kolekcí.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Pokud tento modul zahrnete, použijte standardní zásady vytváření názvů pro funkce, které najdete v FSharp. Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Použití modulu k seskupení funkcí pro běžné a kanonické funkce, zejména v případě matematických a DSL knihoven

Například `Microsoft.FSharp.Core.Operators` je automaticky otevřená kolekce funkcí na nejvyšší úrovni (například `abs` a `sin` ) poskytovaná FSharp. Core. dll.

Knihovna statistik může také obsahovat modul s funkcemi `erf` a `erfc` , kde je tento modul navržený tak, aby byl explicitně nebo automaticky otevřen.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Zvažte použití RequireQualifiedAccess a pečlivé použití atributů AutoOpen.

Přidání `[<RequireQualifiedAccess>]` atributu do modulu znamená, že modul nemůže být otevřen a že odkazy na prvky modulu vyžadují explicitní kvalifikovaný přístup. `Microsoft.FSharp.Collections.List`Modul má například tento atribut.

To je užitečné v případě, že funkce a hodnoty v modulu mají názvy, které jsou pravděpodobně v konfliktu s názvy v jiných modulech. Vyžadování kvalifikovaného přístupu může značně prodloužit dlouhodobou udržovatelnost a možnost využití knihovny.

Přidání `[<AutoOpen>]` atributu do modulu znamená, že se modul otevře při otevření nadřazeného oboru názvů. `[<AutoOpen>]`Atribut může být použit také na sestavení, aby označoval modul, který je automaticky otevřen při odkazování na sestavení.

Například statistická knihovna **MathsHeaven. Statistics** může obsahovat `module MathsHeaven.Statistics.Operators` obsahující funkce `erf` a `erfc` . Je vhodné označit tento modul jako `[<AutoOpen>]` . To znamená, `open MathsHeaven.Statistics` že tento modul také otevřete a přenesete názvy `erf` a `erfc` do rozsahu. Jiné vhodné použití `[<AutoOpen>]` je pro moduly obsahující rozšiřující metody.

Nadměrné `[<AutoOpen>]` využití potenciálních zákazníků pro zneužitelné obory názvů a atribut by měl být použit s péčí. Pro konkrétní knihovny v konkrétních doménách může rozumné využití `[<AutoOpen>]` vést k lepší použitelnosti.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Zvažte možnost definovat členy operátoru pro třídy, kde je vhodné použít dobře známé operátory

Někdy se třídy používají k modelování matematických konstrukcí, jako jsou vektory. V případě, že doménová model obsahuje známé operátory, je třeba je definovat jako členy, kteří jsou pro tuto třídu vnitřní.

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Tyto pokyny odpovídají obecným pokynům rozhraní .NET pro tyto typy. V kódování F # ale může být také důležité, protože tyto typy je možné používat ve spojení s funkcemi F # a s omezeními členů, jako je list. sumBy –.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Zvažte použití zkompilovaného typu k poskytnutí. Popisný název pro ostatní uživatele jazyka .NET

Někdy můžete chtít pojmenovat něco v jednom stylu pro příjemce F # (například statického člena v malých písmenech, aby se zobrazilo, jako by šlo o funkci vázanou na modul), ale měl jiný styl pro název při kompilaci do sestavení. Atribut můžete použít `[<CompiledName>]` k poskytnutí jiného stylu pro kód, který nespotřebovává kód jazyka F #.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Pomocí `[<CompiledName>]` můžete použít konvence vytváření názvů .NET pro uživatele, kteří nejsou v jazyce F #.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Použití přetížení metody pro členské funkce, pokud to uděláte, poskytuje jednodušší rozhraní API.

Přetížení metody je výkonný nástroj pro zjednodušení rozhraní API, které může potřebovat provést podobné funkce, ale s různými možnostmi nebo argumenty.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

V F # je častější přetížení na základě počtu argumentů, nikoli typů argumentů.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Skryje reprezentace typů záznamů a sjednocení, pokud je návrh těchto typů nejspíš vyvíjejí.

Vyhněte se odhalení konkrétních reprezentace objektů. Například konkrétní reprezentace hodnot není zjištěna <xref:System.DateTime> externím a veřejným rozhraním API návrhu knihovny .NET. V době běhu zná modul CLR (Common Language Runtime) potvrzenou implementaci, která bude použita v celém spuštění. Zkompilovaný kód však sám nevyužívá závislosti na konkrétní reprezentace.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Nepoužívejte dědičnost implementace pro rozšiřitelnost.

V F # se dědičnost implementace používá zřídka. Kromě toho jsou Hierarchie dědičnosti často složité a obtížně se mění, když dorazíte na nové požadavky. Implementace dědičnosti v F # stále existuje kvůli kompatibilitě a vzácným případům, kde se jedná o nejlepší řešení problému, ale při navrhování polymorfismu, jako je například implementace rozhraní, byste měli v programech F # vyzkoušet alternativní techniky.

### <a name="function-and-member-signatures"></a>Signatury funkcí a členů

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Použít řazené kolekce členů pro návratové hodnoty při vrácení malého počtu více nesouvisejících hodnot

Tady je dobrý příklad použití řazené kolekce členů v návratovém typu:

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

U návratových typů obsahujících mnoho komponent nebo v případě, že komponenty souvisejí s jedinou identifikovatelnou entitou, zvažte použití pojmenovaného typu namísto řazené kolekce členů.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Použití `Async<T>` pro asynchronní programování na hranicích rozhraní API F #

Pokud je k dispozici odpovídající synchronní operace s názvem, `Operation` která vrací `T` , pak by měla být asynchronní operace pojmenována, pokud se vrátí `AsyncOperation` `Async<T>` nebo `OperationAsync` vrátí `Task<T>` . Pro běžně používané typy .NET, které zpřístupňují Begin/End metody, zvažte použití `Async.FromBeginEnd` metody pro zápis rozšiřujících metod jako fasádu a poskytnutí asynchronního programovacího modelu F # těmto rozhraním API .NET.

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

Informace o vhodném použití výjimek, výsledků a možností najdete v tématu [Správa chyb](conventions.md#error-management) .

### <a name="extension-members"></a>Členové rozšíření

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Pečlivě použít členy rozšíření F # v komponentách F # až-F #

Členy rozšíření F # by obecně měly být použity pouze pro operace, které jsou v uzávěru vnitřních operací přidružených k typu ve většině jeho režimů použití. Jedním z běžných použití je poskytnout rozhraní API, která jsou idiomatickou na F # pro různé typy rozhraní .NET:

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Použití rozlišených sjednocení namísto hierarchií tříd pro data strukturovaná v stromové struktuře

Struktury podobné stromu jsou rekurzivně definovány. To je nevhodné při dědění, ale elegantní s rozlišenými Sjednoceními.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Představují-li data ve stromové struktuře s rozlišenými Sjednoceními, také vám umožní těžit z úplnosti v porovnávání vzorů.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Použití `[<RequireQualifiedAccess>]` na typech sjednocení, jejichž názvy případů nejsou dostatečně jedinečné

Můžete se setkat s doménou, ve které je stejný název nejlepším názvem pro různé věci, jako jsou například rozlišené případy sjednocení. Můžete použít k jednoznačnému rozlišení `[<RequireQualifiedAccess>]` názvů případů, aby nedocházelo k matoucím chybám kvůli stínům, které jsou závislé na řazení `open` příkazů.

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Skryje reprezentace rozlišených sjednocení pro binární kompatibilní rozhraní API, pokud je návrh těchto typů nejspíš vyvíjejí.

Typy sjednocení spoléhají na formuláře porovnávání vzorů F # pro stručný programovací model. Jak už bylo uvedeno dříve, měli byste se vyhnout odhalení konkrétních reprezentace dat, pokud je návrh těchto typů pravděpodobně vyvíjejí.

Například reprezentace rozlišeného sjednocení může být skrytá pomocí soukromé nebo interní deklarace nebo pomocí souboru signatury.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Pokud nerozlišujete rozlišené sjednocení, může se stát, že budete mít zavedenou verzi vaší knihovny bez přerušení uživatelského kódu. Místo toho zvažte odhalení jednoho nebo více aktivních vzorů, které umožní porovnávání vzorů přes hodnoty vašeho typu.

Aktivní vzory poskytují alternativní způsob, jak poskytnout spotřebitelům F # s porovnáváním vzorů, přičemž se vyhnete vystavování typů sjednocení F #.

### <a name="inline-functions-and-member-constraints"></a>Vložené funkce a omezení členů

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Definování obecných číselných algoritmů pomocí vložených funkcí s implicitními omezeními členů a staticky vyřešenými obecnými typy

Omezení aritmetických členů a porovnání F # jsou standardem pro programování v jazyce F #. Zvažte například následující kód:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Typ této funkce je následující:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Toto je vhodná funkce pro veřejné rozhraní API v matematické knihovně.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Nepoužívejte omezení členů pro simulaci tříd typů a ztraceného psaní

Je možné simulovat "ztracené psaní" pomocí omezení členů F #. Nicméně členové, kteří používají toto by, by neměly být obecně použity v návrzích knihovny F # do-F #. Důvodem je to, že návrhy knihovny založené na neznámých nebo nestandardních implicitních omezeních mají za následek neflexibilní a vázané na jeden konkrétní model rozhraní.

Kromě toho existuje dobrý šanci, že těžké použití omezení členů tímto způsobem může vést k velmi dlouhé době kompilace.

### <a name="operator-definitions"></a>Definice operátorů

#### <a name="avoid-defining-custom-symbolic-operators"></a>Vyhněte se definování vlastních symbolických operátorů

Vlastní operátory jsou v některých situacích nezbytné a jsou vysoce užitečná pro Zápisová zařízení v rámci velkého těla implementačního kódu. Pro nové uživatele knihovny jsou pojmenované funkce často snáze používány. Kromě toho mohou být vlastní symbolické operátory obtížné dokumentovat a uživatelé naleznou snadnější vyhledávání v nápovědě k operátorům z důvodu stávajících omezení v prostředí IDE a vyhledávacích strojích.

V důsledku toho je nejlepší publikovat vaše funkce jako pojmenované funkce a členy a dále vystavit operátory pro tuto funkci pouze v případě, že tyto výhody převáží dokumentaci a náklady na vnímání.

### <a name="units-of-measure"></a>Měrné jednotky

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Pečlivě používejte měrné jednotky pro přidání bezpečnosti typů v kódu F #.

Další informace o zadávání pro měrné jednotky se vymažou při prohlížení jinými jazyky .NET. Mějte na paměti, že komponenty, nástroje a reflexe rozhraní .NET uvidí typy – jednotky sítě SAN. Například příjemci C# uvidí `float` místo `float<kg>` .

### <a name="type-abbreviations"></a>Zkratky typů

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Používejte pečlivě zkratky typů pro zjednodušení kódu F #.

Komponenty, nástroje a reflexe rozhraní .NET nebudou pro typy zobrazovat zkrácené názvy. Významným využitím zkratek typu může být taky, že doména vypadá složitější než ve skutečnosti, což by mohlo Zaměňujte uživatele.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Vyhněte se zkratkám typu pro veřejné typy, jejichž členy a vlastnosti by měly být vnitřně odlišné od těch, které jsou k dispozici pro zkrácený typ.

V tomto případě typ, který se zkracuje, je příliš velký o reprezentace vlastního typu, který je definován. Místo toho zvažte zabalení zkratky v typu třídy nebo samostatného sjednocení sjednocení (nebo, pokud je zásadní výkon, zvažte použití typu struktury k zabalení zkratky).

Například se nachází na definování násobného mapování jako speciálního případu mapy F #, například:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Nicméně logické operace zápisu tečky na tomto typu nejsou stejné jako operace na mapě – například je vhodné, aby bylo mapování operátoru vyhledávání přijatelné. [key] vrátí prázdný seznam, pokud klíč není ve slovníku, namísto vyvolání výjimky.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Pokyny pro knihovny pro použití z jiných jazyků .NET

Při navrhování knihoven pro použití z jiných jazyků .NET je důležité dodržovat [pokyny pro návrh knihovny .NET](../../standard/design-guidelines/index.md). V tomto dokumentu jsou tyto knihovny označeny jako Vanilla knihovny .NET, na rozdíl od knihoven F #, které používají konstrukce F # bez omezení. Návrh vanillach knihoven .NET znamená, že rozhraní API pro známé a idiomatickou, která jsou konzistentní se zbytkem .NET Framework tím, že minimalizují použití konstrukcí specifických pro jazyk F # ve veřejném rozhraní API. Pravidla jsou vysvětlena v následujících částech.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Obor názvů a typ – návrh (pro knihovny používané z jiných jazyků rozhraní .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Použití konvencí vytváření názvů .NET pro veřejné rozhraní API vašich komponent

Věnujte zvláštní pozornost použití zkrácených názvů a pokynů pro psaní velkých písmen .NET.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Použití oborů názvů, typů a členů jako primární struktury organizace pro vaše komponenty

Všechny soubory obsahující veřejné funkce by měly začínat `namespace` deklarací a v oborech názvů by měly být jenom veřejné entity s přístupem. Nepoužívejte moduly F #.

Používejte neveřejné moduly pro uchování implementačního kódu, typů nástrojů a funkcí nástrojů.

Statické typy by měly být upřednostňovány přes moduly, protože umožňují budoucí vývoj rozhraní API k použití přetížení a dalších konceptů návrhu rozhraní .NET API, které nesmí být použity v modulech jazyka F #.

Například místo následujícího veřejného rozhraní API:

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

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Použití typů záznamů jazyka F # v rozhraních API Vanilla .NET, pokud se návrh typů nevyvíjí

Typy záznamů F # jsou zkompilovány do jednoduché třídy .NET. Ty jsou vhodné pro některé jednoduché a stabilní typy v rozhraních API. Zvažte použití `[<NoEquality>]` atributů a `[<NoComparison>]` pro potlačení automatické generace rozhraní. Nepoužívejte také proměnlivá pole záznamů v rozhraních API Vanilla .NET, protože tyto položky zveřejňují veřejné pole. Vždy zvažte, zda by třída poskytovala pružnější možnost pro budoucí vývoj rozhraní API.

Například následující kód F # zveřejňuje veřejné rozhraní API pro příjemce v jazyce C#:

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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Skrýt reprezentace typů sjednocení F # v rozhraních API Vanilla .NET

Typy sjednocení jazyka f # se běžně nepoužívají napříč hranicemi součástí, dokonce i pro kódování F # až-F #. Jsou to skvělé implementační zařízení, když se interně používá v rámci komponent a knihoven.

Při návrhu rozhraní Vanilla .NET API zvažte skrytí reprezentace typu sjednocení pomocí soukromé deklarace nebo souboru signatury.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Můžete také rozšířit typy, které používají reprezentace sjednocení interně se členy, aby poskytovaly požadované. Rozhraní API pro NET.

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Návrh grafického uživatelského rozhraní a dalších komponent pomocí vzorů návrhu rozhraní

V rozhraní .NET je k dispozici mnoho různých platforem, jako jsou WinForms, WPF a ASP.NET. Pokud navrhujete komponenty pro použití v těchto rozhraních, měli byste použít konvence pojmenování a návrhu pro každý z nich. Například pro programování v WPF můžete pro třídy, které navrhujete, přijmout vzory návrhu WPF. Pro modely v programování uživatelského rozhraní použijte vzory návrhu, jako jsou události a kolekce založené na oznámeních, jako jsou ty, které se nacházejí v <xref:System.Collections.ObjectModel> .

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Návrh objektů a členů (pro knihovny používané z jiných jazyků rozhraní .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Použití atributu CLIEvent k vystavení událostí .NET

Sestavte a `DelegateEvent` s konkrétním typem delegáta .NET, který přebírá objekt a `EventArgs` (spíše než `Event` a, který pouze používá `FSharpHandler` typ ve výchozím nastavení), aby byly události publikovány známým způsobem pro jiné jazyky rozhraní .NET.

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

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a>Zveřejňujte asynchronní operace jako metody, které vracejí úlohy .NET.

Úlohy se používají v rozhraní .NET ke znázornění aktivních asynchronních výpočtů. Úlohy jsou všeobecně méně kompozice než objekty F # `Async<T>` , protože představují "již prováděné" úlohy a nemohou být složeny způsobem, který provádí paralelní složení nebo které skrývají šíření signálů zrušení a dalších kontextových parametrů.

Nicméně navzdory tomu metody, které vracejí úkoly, jsou standardní reprezentace asynchronního programování v rozhraní .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Často také budete chtít přijmout explicitní token zrušení:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Použití typů delegátů .NET namísto typů funkcí F #

Zde "typy funkcí F #" znamenají "šipky" jako `int -> int` .

Místo toho:

```fsharp
member this.Transform(f: int->int) =
    ...
```

Postupujte takto:

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

Typ funkce F # se zobrazí jako `class FSharpFunc<T,U>` jiné jazyky .NET a je méně vhodný pro jazykové funkce a nástroje, které rozumí typům delegátů. Při vytváření vyšších objednávek, které cílí na .NET Framework 3,5 nebo vyšší, `System.Func` jsou delegáti a držitelé rozhraní `System.Action` API správná rozhraní API k publikování, aby mohli vývojáři rozhraní .NET spotřebovávat tato rozhraní API, a to s nízkým třením. (Při cílení na .NET Framework 2,0 jsou typy delegátů definované systémem omezenější; zvažte použití předdefinovaných typů delegátů, jako je `System.Converter<T,U>` nebo definování konkrétního typu delegáta.)

Na překlopení nejsou Delegáti .NET pro knihovny orientované na F # přirozené (viz další část knihoven s podporou jazyka F #). V důsledku toho je společná implementační strategie při vývoji metod vyšších pořadí pro knihovny Vanilla .NET určena k vytváření všech implementací pomocí typů funkcí jazyka F # a následnému vytvoření veřejného rozhraní API pomocí delegátů jako tenké fasády základem aktuální implementace F #.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Použijte vzor TryGetValue místo vrácení hodnot možností F # a preferovat přetížení metody, aby se jako argumenty použily hodnoty možností jazyka F #.

Běžné vzory použití pro typ možnosti jazyka F # v rozhraních API jsou lépe implementované v rozhraních API Vanilla .NET pomocí standardních technik návrhu .NET. Místo vrácení hodnoty možnosti jazyka F # zvažte použití návratového typu bool plus výstupní parametr jako ve vzoru "TryGetValue". A místo toho, aby jako parametry používaly hodnoty možností jazyka F #, zvažte použití přetížení metod nebo nepovinných argumentů.

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Použijte rozhraní .NET Collection Types IEnumerable \< T \> a \< klíč IDictionary, hodnotu \> parametrů a návratové hodnoty.

Vyhněte se použití konkrétního typu kolekce, jako jsou pole .NET `T[]` , typy F # `list<T>` `Map<Key,Value>` a `Set<T>` a konkrétní typy kolekcí .NET, jako `Dictionary<Key,Value>` je například. Pokyny pro návrh knihovny .NET mají dobré rady týkající se použití různých typů kolekcí, jako je `IEnumerable<T>` . Některé použití polí ( `T[]` ) je v některých případech přijatelné z důvodů výkonu. Pamatujte, že `seq<T>` je to pouze alias F # pro `IEnumerable<T>` , a proto SEQ je často vhodný typ pro rozhraní .NET API Vanilla.

Místo seznamů F #:

```fsharp
member this.PrintNames(names: string list) =
    ...
```

Použijte sekvence F #:

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Použijte typ jednotky jako jediný vstupní typ metody pro definování metody s nulovým argumentem nebo jako jediný návratový typ pro definování metody vracející typ void.

Vyhněte se jiným použití typu jednotky. Jsou dobré:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

Toto je chybné:

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Kontrolovat hodnoty null v hranicích rozhraní .NET API Vanilla

Implementační kód F # má za následek méně hodnot null, z důvodu neměnných vzorů návrhu a omezení použití literálů null pro typy F #. Jiné jazyky rozhraní .NET často používají hodnotu null jako hodnotu mnohem častěji. Z tohoto důvodu kód F #, který vystavuje rozhraní Vanilla .NET API, by měl kontrolovat parametry pro hodnotu null na hranici rozhraní API a zabránit přetečení těchto hodnot do kódu implementace F #. `isNull`Lze použít funkci nebo porovnávání vzorů pro `null` vzor.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Nepoužívejte řazené kolekce členů jako návratové hodnoty.

Místo toho preferovat vrácení pojmenovaného typu, který uchovává agregovaná data, nebo použití parametrů out k vrácení více hodnot. I když existují řazené kolekce členů a struktury v rozhraní .NET (včetně podpory jazyka C# pro řazené kolekce členů struktury), většinou neposkytují ideální a očekávané rozhraní API pro vývojáře na platformě .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Vyhněte se použití procesu curryfikace parametrů

Místo toho použijte konvence volání rozhraní .NET `Method(arg1,arg2,…,argN)` .

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Tip: Pokud navrhujete knihovny pro použití z libovolného jazyka .NET, nemusíte ve skutečnosti provádět nějaké experimentální prostředí C# a Visual Basic, aby se zajistilo, že se vaše knihovny "chovají" v těchto jazycích. Můžete také použít nástroje, jako je například reflektor .NET a Visual Studio Prohlížeč objektů, abyste zajistili, že se knihovny a dokumentace zobrazují podle očekávání vývojářům.

## <a name="appendix"></a>Příloha

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Komplexní příklad návrhu kódu F # pro použití v jiných jazycích .NET

Vezměte v úvahu následující třídu:

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

Odvozený typ F # této třídy je následující:

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

Pojďme se podívat, jak se tento typ F # zobrazuje programátorovi pomocí jiného jazyka .NET. Například přibližný podpis C# "signatura" je následující:

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

Existují některé důležité body, které si všimněte, jak jazyk F # představuje konstrukce. Příklad:

* Metadata, jako jsou názvy argumentů, byla zachována.

* Metody F #, které přijímají dva argumenty, se stanou metodami jazyka C#, které přijímají dva argumenty.

* Funkce a seznamy se stanou odkazy na odpovídající typy v knihovně F #.

Následující kód ukazuje, jak upravit tento kód, aby se tyto věci zohlednily.

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

Odvozený typ F # kódu je následující:

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

Signatura jazyka C# je teď následující:

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

Tyto opravy pro přípravu tohoto typu pro použití jako součást knihovny .NET Vanilla jsou následující:

* Bylo upraveno několik názvů: `Point1` , `n` , `l` a `f` `RadialPoint` `count` `factor` `transform` v uvedeném pořadí.

* Byl použit návratový typ `seq<RadialPoint>` místo `RadialPoint list` pomocí změny konstrukce seznamu pomocí `[ ... ]` pro konstrukci sekvence pomocí `IEnumerable<RadialPoint>` .

* Místo typu funkce F # se použil typ delegáta .NET `System.Func` .

Díky tomu se nicero, že se spotřebuje v kódu C#.
