---
title: 'Pokyny pro návrh součást F #'
description: 'Přečtěte si pokyny pro tvorbu F # součásti určené pro používání jiných volající.'
ms.date: 05/14/2018
ms.openlocfilehash: 7859baac76be01b2cfbdc8602b6cc417cfe5106f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="f-component-design-guidelines"></a>Pokyny pro návrh součást F #

Tento dokument je sada pokynů pro návrh součásti pro F # programování, podle F # součást pokynů pro návrh, v14, Microsoft Research a [jinou verzi](https://fsharp.org/specs/component-design-guidelines/) původně kurátorované a udržované pomocí Foundation softwaru F #.

Tento dokument předpokládá, že jste se seznámili s F # – programování. Mnoho díky komunity F # pro své příspěvky a užitečné zpětnou vazbu na různé verze tohoto průvodce.

## <a name="overview"></a>Přehled

Tento dokument vypadá na některé problémy, týkající se návrhu součást F # a kódování. Součást může zahrnovat následující:

* Vrstvy v projektu F #, který má externí uživatelé v rámci daného projektu.
* Knihovna určená pro používání F # – kód napříč hranicemi sestavení.
* Knihovna určená pro používání kterémkoli jazyce platformy .NET napříč hranicemi sestavení.
* Knihovnu určených pro distribuci přes úložiště balíčků, jako například [NuGet](https://nuget.org).

Postupujte podle technik popsaných v tomto článku [pět principů dobrý F # – kód](index.md#five-principles-of-good-f-code)a proto využívat oba funkční a objekt programování podle potřeby.

Bez ohledu na to metodika součásti a knihovny návrháře otočená řadu praktických a prosaic problémů při pokusu vytvořit rozhraní API, které je snadno použitelný pro vývojáře. Odepření aplikaci [pokynů pro návrh knihovny .NET](../../standard/design-guidelines/index.md) bude řídit k vytvoření konzistentního sadu rozhraní API, která jsou příjemný využívat.

## <a name="general-guidelines"></a>Obecné pokyny

Existuje několik universal pokyny, které platí pro F # knihovny, bez ohledu na to, cílová pro knihovnu.

### <a name="learn-the-net-library-design-guidelines"></a>Další pokyny pro návrh knihovny .NET

Bez ohledu na druh F # kódování vedete, je vhodné mít praktické znalosti [pokynů pro návrh knihovny .NET](../../standard/design-guidelines/index.md). Většina jiných F # .NET programátorům bude se seznamte s těmito pokyny a očekávat kód .NET tak, aby odpovídala je.

Pokyny pro návrh knihovny .NET obsahují obecné pokyny týkající se pojmenování, navrhování třídy a rozhraní, návrh člen (vlastnosti, metody, události atd.) a další a jsou užitečné první bod odkazu pro celou řadu pokyny k návrhu.

### <a name="add-xml-documentation-comments-to-your-code"></a>Přidání dokumentační komentáře XML do vašeho kódu

Dokumentace XML na veřejné rozhraní API Ujistěte se, že se uživatelé dostanou skvělé funkce Intellisense a Quickinfo při používání tyto typy a členy a povolit vytváření dokumentace souborů pro knihovnu. Najdete v článku [dokumentace XML](../language-reference/xml-documentation.md) o různé značky xml, které lze použít pro další značek v rámci xmldoc komentáře.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

Můžete použít buď krátkých úseků XML – komentáře (`/// comment`), nebo standardní komentáře XML (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Zvažte použití explicitního signatury (.fsi) pro stabilní knihovny a součást rozhraní API

Pomocí souborů explicitní podpisy knihovny F # obsahuje stručné shrnutí veřejné rozhraní API, které oba pomáhá zajistit, že jste vědět úplné veřejný prostor knihovny, stejně jako poskytuje čistou oddělení mezi veřejné dokumentaci a interní Podrobnosti implementace. Všimněte si, že soubory podpisu přidat třecí změnou veřejné rozhraní API, tím, že změny v rámci implementace i podpis souborů. V důsledku toho signatury obvykle pouze třeba zavést když má stát zpevněné rozhraní API a už očekává se významně změní.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Vždy použijte osvědčené postupy pro používání řetězců v .NET

Postupujte podle [osvědčené postupy pro používání řetězců v .NET](../../standard/base-types/best-practices-strings.md) pokyny. Konkrétně vždy explicitně stavu *kulturního záměr* v převodu a porovnávání řetězců (v případě potřeby).

## <a name="guidelines-for-f-facing-libraries"></a>Pokyny pro F #-facing knihovny

Tato část nabízí doporučení pro vývoj veřejné F #-facing knihovny; To znamená, knihovny vystavení veřejná rozhraní API, které jsou určené pro F # vývojáři. Existuje mnoho různých z knihovny návrhu doporučení platí konkrétně pro F #. Chybí konkrétní doporučení, které následují jsou pokynů pro návrh knihovny .NET záložní pokyny.

### <a name="naming-conventions"></a>Zásady vytváření názvů

#### <a name="use-net-naming-and-capitalization-conventions"></a>Použít konvence pojmenování a velkých písmen v rozhraní .NET

V následující tabulce dodržovat konvence pojmenování a velkých písmen v rozhraní .NET. Existují malé dodatky zahrnout také konstrukce jazyka F #.

| Konstrukce | Případ | Část | Příklady | Poznámky |
|-----------|------|------|----------|-------|
| Konkrétní typy | PascalCase | Podstatné jméno / tvary přídavných jmen | Seznam, Double, komplexní | Konkrétní typy jsou struktury, třídy, výčty, delegáti, záznamy a sjednocení. Názvy typů si tradičně malá písmena v OCaml, F # přijal schéma pojmenování .NET pro typy.
| knihovny DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| Union – značky     | PascalCase | podstatné jméno | Některé, přidat, úspěch | Nepoužívejte předponu veřejné rozhraní API. Volitelně použijte předponu při interní, například ", zadejte týmy = TAlpha | TBeta | TDelta. ". |
| Událost          | PascalCase | Příkaz | ValueChanged / ValueChanging |  |
| Výjimky     | PascalCase |      | Výjimku WebException | Název musí končit "Výjimky". |
| Pole          | PascalCase | podstatné jméno | CurrentName  | |
| Typy rozhraní |  PascalCase | Podstatné jméno / tvary přídavných jmen | Rozhraní IDisposable | Název by měla začínat znakem "I". |
| Metoda |  PascalCase |  Příkaz | ToString | |
| Obor názvů | PascalCase | | Microsoft.FSharp.Core | Obecně používat `<Organization>.<Technology>[.<Subnamespace>]`, ale vyřadit organizace, pokud se tato technologie je nezávislá organizace. |
| Parametry | camelCase | podstatné jméno |  typeName, transformace, rozsahu | |
| let – hodnoty (interní) | camelCase nebo PascalCase | Podstatné jméno / operaci |  getValue myTable |
| let – hodnoty (externí) | camelCase nebo PascalCase | Podstatné jméno/operaci  | List.map –, Dates.Today | vázané na umožňují hodnoty jsou často při veřejné následující vzory návrhu tradiční funkční. Obecně použití však PascalCase identifikátor lze z jinými jazyky rozhraní .NET. |
| Vlastnost  | PascalCase  | Podstatné jméno / tvary přídavných jmen  | IsEndOfFile, barva pozadí  | Logická hodnota vlastnosti obecně použití je a a musí být kladná, stejně jako IsEndOfFile, není IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Vyhněte se zkratky

Pokyny pro rozhraní .NET omezit používání zkratky (například "použít `OnButtonClick` místo `OnBtnClick`"). Běžné zkratky, jako například `Async` pro "Asynchronního", jsou tolerovat. Tyto obecné zásady se někdy ignoruje při funkční programování; například `List.iter` používá zkratkou pro "iteraci". Z tohoto důvodu pomocí zkratky obvykle tolerovat ve větší míře v jazyce F #-na-F # – programování, ale stále obecně je nutno v návrhu veřejné součásti.

#### <a name="avoid-casing-name-collisions"></a>Vyhněte se velká a malá písmena kolize názvů

Pokyny pro rozhraní .NET Řekněme, že velká a malá písmena samostatně nelze použít k rozlišení kolize názvů, protože některé jazyky klienta (například Visual Basic) jsou velká a malá písmena.

#### <a name="use-acronyms-where-appropriate"></a>Použijte režim, kde je to vhodné

Režim například XML nejsou zkratky a jsou široce používaných v knihovny .NET v nezačínající formuláře (Xml). Měli použít pouze známé, široce uznávané režim.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Použití PascalCase pro obecný parametr názvy

Použít PascalCase pro obecný parametr názvy v veřejná rozhraní API, včetně pro F #-facing knihovny. Konkrétně použít názvy jako `T`, `U`, `T1`, `T2` pro libovolný obecné parametry, když konkrétní názvy smysl, pak pro F # – přístupných knihovny používat názvy jako `Key`, `Value`, `Arg`(ale ne například `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Použít PascalCase nebo camelCase pro veřejné funkce a hodnoty v modulech F #

camelCase se používá pro veřejné funkce, které jsou určeny k použití nekvalifikované (například `invalidArg`) a pro "funkce standardního shromažďování" (například list.map –). V obou těchto případech názvy funkcí mnohem fungovat stejně jako klíčová slova v jazyce.

### <a name="object-type-and-module-design"></a>Objekt, typ a modul návrhu

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Použití oborů názvů nebo moduly obsahovat typy a modulů

Každý soubor F # součásti by měl začínat obráceným deklaraci oboru názvů nebo deklaraci modulu.

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

Rozdíly mezi použitím modulů a obory názvů pro uspořádání kódu na nejvyšší úrovni jsou následující:

* Obory názvů může mít rozsah více souborů
* Obory názvů nesmí obsahovat F # funkce, které nejsou v rámci vnitřní modulu
* Kód pro jakékoli dané modul musí být obsaženy v rámci jednoho souboru
* Moduly nejvyšší úrovně může obsahovat funkce F # bez nutnosti vnitřní modulu

Volba mezi nejvyšší úrovně oboru názvů nebo modul ovlivňuje formuláři zkompilovaný kód a proto ovlivní zobrazení jinými jazyky rozhraní .NET by měl vaše rozhraní API nakonec využijí mimo F # – kód.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Použití metod a vlastností pro operace vnitřní pro typy objektů

Při práci s objekty, je nejvhodnější zajistit, že použití funkce je implementovaná jako metody a vlastnosti typu.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

Hromadné funkce pro daný člen nemusí nutně implementaci do tohoto člena, ale musí být použití část této funkce.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Použití tříd pro zapouzdření měnitelný stavu

V F # to jenom je potřeba udělat kde, není stav již zapouzdřené pomocí jiný jazyk konstrukce, například uzavření, pořadí výraz nebo asynchronní výpočty.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Použít rozhraní k seskupení operací souvisejících s

Použijte rozhraní typy, které představují sadu operací. Toto je upřednostňovaný k jiné možnosti, například řazené kolekce členů funkcí nebo záznamy funkcí.

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

V preference na:

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

Rozhraní jsou prvotřídní koncepty v rozhraní .NET, který můžete použít k dosažení co Functors by za normálních okolností získáte. Kromě toho se můžete použitá ke kódování existenční typy do programu, který nelze záznamy funkcí.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Pomocí modulu do funkce skupin, které jednají na kolekce

Při definování typu kolekce, vezměte v úvahu poskytuje standardní sadu operací, jako `CollectionType.map` a `CollectionType.iter`) pro nové typy kolekcí.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Pokud zahrnete takové modul, postupujte podle standardní zásady vytváření názvů pro funkce v FSharp.Core nalezen.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Pomocí modulu do funkcí skupiny pro běžné, kanonické funkce, zejména v matematické a DSL knihovny

Například `Microsoft.FSharp.Core.Operators` je automaticky otevřenou kolekci nejvyšší úrovně funkcí (jako je `abs` a `sin`) poskytované FSharp.Core.dll.

Podobně knihovnu statistiky mohou zahrnovat modul s funkcí `erf` a `erfc`, kde se tento modul slouží k explicitně nebo automaticky otevřít.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Zvažte použití RequireQualifiedAccess a pečlivě použití AutoOpen atributů

Přidávání `[<RequireQualifiedAccess>]` atribut na modul označuje, že modul nemusí otevřít a že vyžadují explicitní odkazy na elementy modulu kvalifikovaný přístup. Například `Microsoft.FSharp.Collections.List` modul má tento atribut.

To je užitečné, když funkce a hodnoty v modulu mají názvy, které mohou v konfliktu s názvy v dalších modulů. Vyžadování kvalifikovaný přístup může výrazně zvýšit dlouhodobé udržovatelnosti a evolvability knihovny.

Přidávání `[<AutoOpen>]` atribut na modul znamená modul se otevře, když je otevřen obsahující obor názvů. `[<AutoOpen>]` Atribut může také použít k sestavení udávajících modul, který se automaticky otevře při odkazování na sestavení.

Například knihovnu statistiky **MathsHeaven.Statistics** může obsahovat `module MathsHeaven.Statistics.Operators` obsahující funkce `erf` a `erfc`. Je možné logicky označit tento modul jako `[<AutoOpen>]`. To znamená `open MathsHeaven.Statistics` rovněž otevřete tento modul a převést názvy `erf` a `erfc` do oboru. Použití jiné dobré `[<AutoOpen>]` je pro moduly, který obsahuje rozšiřující metody.

Nadměrné použití z `[<AutoOpen>]` za následek znečištěného obory názvů a atribut by měl použít dát pozor. Pro konkrétní knihovny v konkrétní domény, rozumné využívání `[<AutoOpen>]` může vést k lepší použitelnost.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Vezměte v úvahu definování operátor členy na třídy, kde je odpovídající pomocí známých operátorů

Třídy se někdy používají pro modelování matematickém konstrukce, jako je například vektory. Pokud má doména modelovaných dobře známé operátory, je definují jako členy do třídy vnitřní je užitečné.

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

V tomto návodu odpovídá obecné pokyny .NET pro tyto typy. Však může být v F # kódování jako to umožňuje tyto typy použije ve spojení s F # funkce a metody s omezeními člena, jako je například list.sumby – kromě důležité.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Zvažte použití compiledname – k poskytování. NET popisný název pro ostatní příjemce jazyk rozhraní .NET

V některých případech můžete chtít název něco v jeden styl pro spotřebitele F # (například statický člen v malá písmena, takže se objeví jako by šlo vázané na modulu funkce), ale mají jiný styl pro název, když je přeložen do sestavení. Můžete použít `[<CompiledName>]` atribut zajistit jiný styl pro jiný F # – kód využívání sestavení.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Pomocí `[<CompiledName>]`, můžete použít zásady vytváření názvů .NET pro jiný F # spotřebiteli sestavení.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Použijte přetížení metody pro členské funkce, pokud Důvodem jsou jednodušší rozhraní API

Přetěžování metody je výkonný nástroj pro zjednodušenou rozhraní API, které můžete využít podobné funkce, ale s různými možnostmi nebo argumenty.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

V jazyce F # je dnes běžné k přetížení na počet argumentů než typy argumentů.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Skrýt reprezentace záznam a typy union, pokud tyto typy v návrhu je pravděpodobné, vyvíjí

Vyhněte se odhalil konkrétní reprezentace objektů. Například konkrétní reprezentace <xref:System.DateTime> hodnoty není zjištěné při externí, veřejné rozhraní API návrhu knihovny .NET. V době běhu modul Common Language Runtime zná potvrdit implementace, která se použije v průběhu provádění. Ale zkompilovaný kód není sám vyzvedávat závislosti na konkrétní reprezentace.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Vyhněte se použití implementace dědičnosti rozšíření

V F # je používána zřídka implementace dědičnosti. Kromě toho hierarchie dědičnosti jsou často složitá a obtížná změnit příchod nové požadavky. Implementace dědičnosti stále existuje v jazyce F # pro kompatibilitu a výjimečných případech, kdy je nejlepší řešení problémů, ale alternativní techniky se má hledat v programů F # při návrhu polymorfismus, jako je například implementaci rozhraní.

### <a name="function-and-member-signatures"></a>Funkce a člen podpisy

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Při vrácení malý počet nesouvisejícími více hodnot použijte řazených kolekcí členů pro vrácené hodnoty

Tady je dobrým příkladem použití řazené kolekce členů v návratový typ:

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

Návratové typy obsahující mnoho součásti nebo kde komponenty se vztahují k jedné osobní entity, zvažte použití pojmenovaného typu místo řazené kolekce členů.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Použití `Async<T>` pro asynchronní programování v F # API hranice

Pokud je odpovídající synchronní operace s názvem `Operation` , který vrací `T`, pak by měl být pojmenován asynchronní operace `AsyncOperation` vrátí-li `Async<T>` nebo `OperationAsync` vrátí-li `Task<T>`. Běžně používané typy .NET, které zveřejňují začátek/konec metody, zvažte použití `Async.FromBeginEnd` zápis metody rozšíření jako průčelí za k poskytování F # asynchronní programovací model těchto rozhraní API technologie .NET.

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Výjimky

Výjimky jsou výjimečných v rozhraní .NET; To znamená že nedojde často za běhu. Pokud tomu tak je, je cenné informace, které obsahují. Výjimky jsou základní prvotřídní konceptu .NET; proto IT způsobem, které příslušné aplikace výjimky by měla být použity jako součást návrhu rozhraní součásti.

#### <a name="follow-the-net-guidelines-for-exceptions"></a>Postupujte podle pokynů .NET pro výjimky

[Pokynů pro návrh knihovny .NET](../../standard/design-guidelines/exceptions.md) poskytnout vynikající Rady ohledně použití výjimek v kontextu všechny .NET – programování. Některé z těchto pokynů jsou následující:

* Nepoužívejte výjimky pro normálního toku řízení. I když tato technika se často používá v jazycích, jako je například OCaml, jsou náchylné chyb a může být neefektivní na rozhraní .NET. Místo toho zvažte vrácení `None` hodnota označující selhání, které je běžné nebo se očekává výskyt možnosti.

* Dokument výjimky vyvolané vaše komponenty pro při volání funkce používána nesprávně.

* Pokud je to možné, využívejte stávající výjimky z oborů názvů systému. Vyhněte se <xref:System.ApplicationException>, ačkoli.

* Nevyvolá výjimku <xref:System.Exception> když bude řídicí kód uživatele. To zahrnuje zabraňující použití `failwith`, `failwithf`, které jsou užitečné funkce pro použití ve vytváření skriptů a pro kód ve vývoji, ale měla by být odebrána z knihovny kódu F # považuje vyvolání konkrétnější typ výjimky.

* Použití `nullArg`, `invalidArg`, a `invalidOp` jako mechanizmus pro throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, a <xref:System.InvalidOperationException> při vhodné.

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a>Vezměte v úvahu při selhání není výjimečných scénář pomocí hodnoty možnosti pro návratové typy

Rozhraní .NET přístup k výjimkám je, že by měl být "výjimečných;" To znamená že má vzniknout poměrně málo. Některé operace (například vyhledávání tabulku) však mohou selhat často. Hodnoty možnosti F # jsou vynikající způsob představují návratové typy z těchto operací. Tyto operace obvykle začínají předponou názvu "zkuste":

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a>Rozšíření členy

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Pečlivě použít F # rozšíření členy v jazyce F #-na-F # součásti

F # rozšíření členy obecně lze používat pouze pro operace, které jsou v uzavření vnitřní operace, které souvisí s typem ve většině režimech použití. Jeden běžné slouží k poskytování rozhraní API, která jsou více idiomatickou k F # pro různé typy .NET:

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>Sjednocení typů

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Použití rozlišovaná sjednocení místo hierarchie tříd pro stromovou strukturou data

Jako stromové struktury jsou rekurzivně definované. Toto je nevhodných s použitím dědičnosti, ale elegantní s Rozlišované sjednocení.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Představující stromu jako data s Rozlišované sjednocení také umožňuje využívat úplnosti v porovnávání vzorů.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Použití `[<RequireQualifiedAccess>]` na union typy, jejichž případu názvy nejsou dostatečně jedinečné

V doméně, kde se stejným názvem je nejlepší název pro různé akce, jako je například Rozlišované sjednocení případech může najít sami. Můžete použít `[<RequireQualifiedAccess>]` kvůli zajištění jednoznačnosti rozlišování názvů, aby se zabránilo spouštění matoucí chyby kvůli stínový provoz závisí na pořadí `open` příkazy

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Skrýt reprezentace rozlišovaná sjednocení pro binární kompatibilní rozhraní API, pokud je pravděpodobné, vyvíjí návrhu z těchto typů

Sjednocení typů spoléhají na F # porovnávání formuláře pro stručného programovací model. Jak je uvedeno nahoře, neměli byste odhalil reprezentace konkrétní data, pokud je pravděpodobné, vyvíjí návrh tyto typy.

Například reprezentace rozlišovaná sjednocení může být skryté pomocí deklaraci soukromý nebo interní nebo podpis souboru.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Pokud odhalit rozlišovaná sjednocení bez, může být obtížné verze knihovnu, aniž by vás uživatelského kódu. Místo toho zvažte odhalil jeden nebo více aktivní vzorky tak, aby povolovala porovnávání se přes hodnoty stejného typu.

Aktivní vzorky zadejte jiný způsob, jak poskytnout příjemci knihovny F # pro porovnávání a snižuje přímo vystavení sjednocení typů F #.

### <a name="inline-functions-and-member-constraints"></a>Vložené funkce a omezení člena

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Definujte obecné číselné algoritmy vložené funkce pomocí omezení předpokládané člen a statisticky obecné typy

Aritmetické člen omezení a omezení porovnání F # jsou standard pro F # – programování. Zvažte například následující kód:

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

Toto je vhodné funkce pro veřejné rozhraní API v matematickém knihovně.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Vyhněte se použití omezení člen simulace typu třídy a kachní zadáním

Je možné k simulaci "divokou zadáním" použití omezení člen F #. Však členy, které pomocí tohoto objektu není v obecné je třeba používat v F #-na-návrhů knihovny F #. Je to proto, že knihovna návrhy založené na neznámého nebo nestandardní implicitní omezení můžou vést k uživatelského kódu se pevná a vázané na jednu konkrétní framework vzor.

Kromě toho je dobré pravděpodobné, že výrazně využívá člen omezení tímto způsobem může mít za následek kompilace velmi dlouhé časy.

### <a name="operator-definitions"></a>Definice – operátor

#### <a name="avoid-defining-custom-symbolic-operators"></a>Vyhněte se definování vlastní symbolický operátory

Vlastní operátory je nezbytné v některých situacích a jsou velmi užitečné konvenční zařízení v rámci rozsáhlý soubor implementaci kódu. Pro nové uživatele knihovny se často funkce s názvem snadněji používat. Kromě toho může být obtížné dokumentu vlastní symbolický operátory a uživatelé najít obtížné vyhledat nápovědu k operátory z důvodu omezení existující v IDE a vyhledávacího.

V důsledku toho je nejvhodnější publikovat vaše funkce jako funkce s názvem a členy a pouze v případě, že konvenční výhody převáží nad dokumentace a kognitivní náklady toho, aby kromě vystavit operátory pro tuto funkci.

### <a name="units-of-measure"></a>Měrné jednotky

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Pečlivě použijte měrné jednotky pro zabezpečení přidané typů v F # – kód

Další informace o zadáte pro jednotky míry se vymaže při prohlížení jinými jazyky rozhraní .NET. Pamatujte, že součásti rozhraní .NET, nástroje a reflexe uvidí typy sítí SAN jednotky. Například C# uživatelé uvidí `float` místo `float<kg>`.

### <a name="type-abbreviations"></a>Zkratky typů

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Pečlivě použití zkratky typů ke zjednodušení F # – kód

Součásti rozhraní .NET, nástroje a reflexe neuvidí zkrácené názvy typů. Významné používání zkratky typů provést také domény zobrazí složitější než ve skutečnosti je, která by mohla matou příjemci.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Vyhněte se zkratky typů pro veřejné typy, jejíž členové a vlastnosti by měla být vnitřně liší od těch, které jsou k dispozici na typ se používá zkratka

V takovém případě zjistí typ se používá zkratka příliš mnoho o reprezentace skutečný typ definovaný. Místo toho zvažte zabalení zkratka v typu třídy nebo jeden případ rozlišovaná sjednocení (nebo, když výkonu je nezbytné, zvažte použití typu Struktura zabalit zkratku).

Je třeba tempting k definování více mapy ve speciálním případě F # mapy, například:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Ale logické tečkami operace u tohoto typu nejsou stejná jako operace na mapě – například je možné logicky, aby operátor vyhledávání map. [klíče] vrátí prázdný seznam, pokud není klíč ve slovníku místo vyvolání k výjimce.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Pokyny pro knihovny pro použití jiných jazyků .NET

Při navrhování knihovny pro použití jiných jazyků .NET, je potřeba dodržovat [pokynů pro návrh knihovny .NET](../../standard/design-guidelines/index.md). V tomto dokumentu tyto knihovny jsou označeny jako vanilla knihovny .NET, a F #-facing knihovny, které používají F # vytvoří bez omezení. Navrhování vanilla knihovny .NET znamená poskytující známé a idiomatickou rozhraní API konzistentní se zbytkem rozhraní .NET Framework pomocí minimalizace použití F # – konkrétní konstrukce v veřejné rozhraní API. Pravidla jsou vysvětlené v následujících částech.

### <a name="namespace-and-type-sesign-for-libraries-for-use-from-other-net-languages"></a>Namespace a typ sesign (pro knihovny pro použití jiných jazyků .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Použít zásady vytváření názvů .NET pro veřejné rozhraní API komponent

Věnujte zvláštní pozornost použití zkrácené názvy a podle pokynů .NET malá a velká písmena.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Obory názvů, typy a členy použít jako primární organizační struktury komponent

Všechny soubory obsahující veřejný funkce by měl začínat obráceným `namespace` deklarace a pouze veřejné entity v oborech názvů by měl být typy. Nepoužívejte F # moduly.

Použijte moduly neveřejný pro implementaci kódu, nástroj typy a funkce nástroj.

Statické typy by měly být upřednostňované přes moduly, protože umožňují pro budoucí vývoj rozhraní API používat přetížení a další koncepty .NET API návrhu, které nesmí být použity v F # moduly.

Například místo následující veřejné rozhraní API:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Místo toho zvažte:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Pokud nebude momentální návrh typy používat typy záznamů F # ve vanilla rozhraní API technologie .NET

Typy záznamů F # zkompilovat na třídu jednoduché rozhraní .NET. Toto jsou vhodné pro některé typy jednoduchý, stabilní rozhraní API. Měli byste zvážit použití `[<NoEquality>]` a `[<NoComparison>]` atributy potlačit automatické generování rozhraní. Také Vyhněte se používání měnitelný záznam pole v vanilla rozhraní API technologie .NET jako tyto zpřístupňuje veřejné pole. Vždy zvažte, zda by třída poskytují flexibilnější možnost pro budoucí vývoj rozhraní API.

Například následující kód F # zpřístupní veřejné rozhraní API k příjemce C#:

F #:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Skrýt reprezentace typů F # union v vanilla rozhraní API technologie .NET

Sjednocení typů F # nejsou obvykle používány napříč hranicemi součásti i pro F #-na-F # kódování. Jsou zařízení s vynikající implementace, pokud se používá interně v rámci komponenty a knihovny.

Při navrhování vanilla .NET API, vezměte v úvahu skrytí reprezentaci typu union pomocí deklaraci privátní nebo soubor podpisu.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Může také posílení typů, které používají znázornění union interně se členy k poskytování požadované. Rozhraní API NET přístupem.

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Návrh grafického uživatelského rozhraní a další součásti pomocí vzory návrhu architektury

Mnoho různých rozhraní nejsou k dispozici v rámci .NET, například WinForms, WPF a ASP.NET. Konvence pojmenování a návrhu pro každý by měl použít, pokud navrhujete komponenty pro použití v tyto architektury. Například pro WPF programování, přijímat WPF vzory návrhu pro třídy, které jsou návrhu. Pro modely v programování uživatelské rozhraní, použijte vzory návrhu, jako jsou události a kolekce založené na oznámení jsou uvedené v <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Objekt a člen návrhu (pro knihovny pro použití jiných jazyků .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Vystavení události .NET pomocí clievent – atribut

Vytvořit `DelegateEvent` s konkrétní .NET delegovat typ, který přebírá objekt a `EventArgs` (místo `Event`, který právě používá `FSharpHandler` typu ve výchozím nastavení), aby se události publikují v známé způsob, jak jinými jazyky rozhraní .NET.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Vystavit asynchronních operací v metody, které vrací úlohy rozhraní .NET

Úlohy se používají v rozhraní .NET představují active asynchronní výpočty. Úlohy jsou v obecné složení méně než F # `Async<T>` objekty, protože představují "již provádění" úlohy a nemůže obsahovat současně způsoby, provést paralelní složení, nebo které skrýt šíření zrušení signály a jiných Kontextové parametry.

Bez ohledu na to, jsou metody, které vrací úlohy standardní reprezentace asynchronní programování v rozhraní .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Často budete také chtít přijímat token explicitní zrušení:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Použití delegáta typy .NET místo funkce typů F #

Zde "typů F # funkce" znamená "šipku" typy jako `int -> int`.

Místo:

```fsharp
member this.Transform(f:int->int) =
    ...
```

postupujte takto:

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

Typ funkce F # se zobrazí jako `class FSharpFunc<T,U>` do jiných jazyků .NET a je méně vhodný pro jazykové funkce a nástrojů, které pochopit typů delegátů. Při vytváření vyšší pořadí metodu cílení na rozhraní .NET Framework 3.5 nebo vyšší, `System.Func` a `System.Action` Delegáti jsou správné rozhraní API pro publikování a umožňuje vývojářům rozhraní .NET způsobem nízkým třením využívají tato rozhraní API. (Při cílení na rozhraní .NET Framework 2.0, jsou typy definované v systému delegáta omezenější, zvažte použití delegáta předdefinované typy jako `System.Converter<T,U>` nebo definování typu konkrétní delegáta.)

Na straně překlopit .NET delegáti nejsou přirozené pro F # – čelí knihovny (viz další část v F # – čelí knihovny). V důsledku toho je společné strategie implementace při vývoji vyšší pořadí metody pro vanilla knihovny .NET k vytváření všech implementace pomocí funkce typů F # a pak vytvořte veřejné rozhraní API použití delegátů jako dynamické průčelí za na skutečné F # implementace.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Použití vzoru TryGetValue místo vrácení hodnoty možnosti F # a dáváte přednost přetěžování metody k pořízení F # hodnoty možnosti jako argumenty

Běžné způsoby použití typu možnosti F # rozhraní API jsou lepší implementované v vanilla rozhraní API technologie .NET pomocí standardní .NET návrh techniky. Místo vrací hodnotu možnosti F #, zvažte použití návratový typ bool plus výstupní parametr jako vzor "TryGetValue". A místo trvá F # hodnoty možnosti jako parametry, zvažte použití metody přetížení nebo volitelné argumenty.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Použití rozhraní .NET kolekce typy rozhraní IEnumerable\<T\> a IDictionary\<klíče, hodnota\> pro parametry a návratové hodnoty

Nepoužívejte typech konkrétní kolekce například pole .NET `T[]`, typů F # `list<T>`, `Map<Key,Value>` a `Set<T>`, a .NET collection konkrétní typy, jako `Dictionary<Key,Value>`. Pokyny pro návrh knihovny .NET mají dobrou Rady týkající se použití různé typy kolekcí, jako je `IEnumerable<T>`. Některé použití polí (`T[]`) je přijatelné v některých případech z důvodů výkonu. Všimněte si, že zejména `seq<T>` je právě F # alias pro `IEnumerable<T>`, a proto je seq často příslušného typu pro vanilla .NET API.

Místo toho jazyka F # uvádí:

```fsharp
member this.PrintNames(names : string list) =
    ...
```

Pomocí F # pořadí:

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Použijte typ jednotky jako pouze vstupní typ metody definovat metodu argumentu nula, nebo jako jediný návratový typ definovat metodu vrácení void

Vyhněte se ostatní používá typ jednotky. Jsou to funkční:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

To je chybný.:

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Zkontrolujte hodnoty null na hranicích vanilla rozhraní API .NET

F # – kód implementace obvykle obsahují méně hodnoty null, z důvodu vzory návrhu neměnné a omezení použití null literálů pro typy F #. Jinými jazyky rozhraní .NET často používají jako hodnota null mnohem častěji. Z toho důvodu F # kód, který je vystavení vanilla .NET API Zkontrolujte parametry pro hodnotu null na hranici rozhraní API a zabránit tyto hodnoty toku hlubší do kódu implementace F #. `isNull` Funkce nebo na porovnávání vzorů `null` vzor lze použít.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Nepoužívejte řazených kolekcí členů jako návratové hodnoty

Místo toho raději vrácení pojmenovaného typu, který obsahuje agregovaná data, nebo pomocí výstupní parametry vrátit více hodnot. I když existují řazených kolekcí členů a struktura řazených kolekcí členů v rozhraní .NET (včetně C# jazyková podpora pro řazené kolekce členů struktury), nejčastěji není zadá ideální a očekávaná rozhraní API pro vývojáře .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Nepoužívejte currying parametrů

Místo toho použijte rozhraní .NET konvence volání ``Method(arg1,arg2,…,argN)``.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Tip: Pokud navrhujete knihovny pro použití v kterémkoli jazyce platformy .NET, nejsou žádné nenahrazuje ve skutečnosti to některé experimentální C# a Visual Basic programování zajistit, aby knihovnách "chování právo" z těchto jazyků. Nástroje, jako je rozhraní .NET Reflector a prohlížeče objektů Visual Studio můžete také zajistit, aby knihovny a jejich dokumentace zobrazily podle očekávání pro vývojáře.

## <a name="appendix"></a>Příloha

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Příklad začátku do konce navrhování F # – kód pro použití jinými jazyky rozhraní .NET

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

Odvozené F # typ této třídy je následující:

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

Podívejme se na tom, jak se vyskytuje tento typ F # pro programátory, použití jiného jazyka .NET. Přibližná jazyka C# "podpis" je například takto:

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

Existují některé důležité body Všimněte o jak F # představuje konstrukce sem. Příklad:

* Metadata, jako jsou názvy argumentu bylo zachováno.

* F # metod, které berou dva argumenty stát C# metod, které berou dva argumenty.

* Funkce a seznamy budou odkazy na odpovídající typy v knihovně F #.

Následující kód ukazuje, jak upravit tento kód vzít v úvahu tyto věci.

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

Odvozené F # typ kódu vypadá takto:

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

Podpis C# je teď následujícím způsobem:

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

Opravy provedené připravit tento typ pro použití jako součást vanilla knihovny .NET jsou následující:

* Upravit několik názvů: `Point1`, `n`, `l`, a `f` aktivovala `RadialPoint`, `count`, `factor`, a `transform`, v uvedeném pořadí.

* Použít návratovým typem `seq<RadialPoint>` místo `RadialPoint list` změnou seznamu konstrukce pomocí `[ ... ]` pořadí vytváření pomocí `IEnumerable<RadialPoint>`.

* Použít typ formátu .NET delegáta `System.Func` místo typ funkce F #.

Díky tomu je mnohem nicer využívat v kódu jazyka C#.
