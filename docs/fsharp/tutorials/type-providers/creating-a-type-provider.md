---
title: 'Kurz: Vytvoření poskytovatele typu'
description: Naučte se, jak vytvořit vlastní zprostředkovatele typu F# v F# 3.0 zkoumáním několika jednoduchých poskytovatelů typů pro ilustraci základních konceptů.
ms.date: 11/04/2019
ms.openlocfilehash: 3b8145d4c2d8bf96b6dcf66de02e9f2d83927d74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186126"
---
# <a name="tutorial-create-a-type-provider"></a>Kurz: Vytvoření poskytovatele typu

Mechanismus zprostředkovatele typu v jazyce F# je významnou součástí jeho podpory pro programování bohaté na informace. Tento kurz vysvětluje, jak vytvořit vlastní poskytovatele typů tím, že vás provede vývojem několika poskytovatelů jednoduchých typů pro ilustraci základních konceptů. Další informace o mechanismu poskytovatele typu ve f#, naleznete v [tématu Type Providers](index.md).

Ekosystém F# obsahuje řadu poskytovatelů typů pro běžně používané internetové a podnikové datové služby. Například:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) zahrnuje zprostředkovatele typů pro formáty dokumentů JSON, XML, CSV a HTML.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje silný typ přístupu k databázím SQL prostřednictvím mapování objektů a F# LINQ dotazy proti těmto zdrojům dat.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) má sadu poskytovatelů typu pro kontrolu dat v době kompilace vkládání T-SQL v F#.

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sada poskytovatelů typů pro použití pouze s programováním rozhraní .NET Framework pro přístup k datovým službám SQL, Entity Framework, OData a WSDL.

V případě potřeby můžete vytvořit vlastní poskytovatele typů nebo můžete odkazovat na poskytovatele typů, které vytvořili jiní uživatelé. Vaše organizace může mít například datovou službu, která poskytuje velký a rostoucí počet pojmenovaných datových sad, z nichž každá má vlastní stabilní schéma dat. Můžete vytvořit poskytovatele typu, který čte schémata a prezentuje aktuální sady dat programátorovi silným způsobem.

## <a name="before-you-start"></a>Než začnete

Mechanismus poskytovatele typu je primárně určen pro vkládání stabilní data a informační prostory služby do prostředí programování F#.

Tento mechanismus není určen pro vkládání informačních prostorů, jejichž schéma se změní během provádění programu způsoby, které jsou relevantní pro logiku programu. Mechanismus také není určen pro metaprogramování v rámci jazyka, i když tato doména obsahuje některé platné použití. Tento mechanismus byste měli použít pouze v případě potřeby a kde vývoj poskytovatele typu poskytuje velmi vysokou hodnotu.

Měli byste se vyhnout psaní poskytovatele typu, kde schéma není k dispozici. Podobně byste se měli vyhnout psaní poskytovatele typu, kde by stačila běžná (nebo dokonce existující) knihovna .NET.

Než začnete, můžete se zeptat na následující otázky:

- Máte schéma pro váš zdroj informací? Pokud ano, jaké je mapování do systému typu F# a .NET?

- Můžete použít existující (dynamicky zadávaný) rozhraní API jako výchozí bod pro implementaci?

- Budete mít vy a vaše organizace dostatek využití poskytovatele typu, aby se psaní stálo za to? Vyhovovala by normální knihovna .NET vašim potřebám?

- O kolik se vaše schéma změní?

- Změní se během kódování?

- Změní se mezi relacemi kódování?

- Změní se během provádění programu?

Zprostředkovatelé typů jsou nejvhodnější pro situace, kdy je schéma stabilní za běhu a během životnosti zkompilovaného kódu.

## <a name="a-simple-type-provider"></a>Poskytovatel jednoduchého typu

Tato ukázka je Samples.HelloWorldTypeProvider, podobně `examples` jako ukázky v adresáři [f# typ zprostředkovatele SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Zprostředkovatel zpřístupní "místo typu", které obsahuje 100 vymazaných typů, jak ukazuje následující kód pomocí `Type1`syntaxe podpisu F# a vynecháním podrobností pro všechny kromě . Další informace o vymýšcených typů naleznete [v tématu Podrobnosti o schovaných typech v](#details-about-erased-provided-types) tomto tématu.

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

Všimněte si, že sada typů a členů zadaných je staticky známa. Tento příklad nevyužívá schopnost zprostředkovatelů poskytovat typy, které závisí na schématu. Implementace poskytovatele typu je popsána v následujícím kódu a podrobnosti jsou popsány v dalších částech tohoto tématu.

> [!WARNING]
> Mezi tímto kódem a online ukázkami mohou být rozdíly.

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

Chcete-li použít tohoto zprostředkovatele, otevřete samostatnou instanci sady Visual Studio, vytvořte skript Jazyka F# a pak přidejte odkaz na zprostředkovatele ze skriptu pomocí #r jak ukazuje následující kód:

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

Pak vyhledejte typy `Samples.HelloWorldTypeProvider` v oboru názvů, který vygeneroval poskytovatel typu.

Před překompilováním zprostředkovatele se ujistěte, že jste zavřeli všechny instance sady Visual Studio a F# Interactive, které používají knihovnu DLL zprostředkovatele. V opačném případě dojde k chybě sestavení, protože výstupní dll bude uzamčen.

Chcete-li ladit tohoto zprostředkovatele pomocí tiskových příkazů, vytvořte skript, který zpřístupňuje problém s poskytovatelem, a potom použijte následující kód:

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Chcete-li tohoto zprostředkovatele ladit pomocí sady Visual Studio, otevřete příkazový řádek pro vývojáře pro sady Visual Studio s pověřeními pro správu a spusťte následující příkaz:

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Alternativně otevřete Visual Studio, otevřete nabídku Ladění, `Debug/Attach to process…` `devenv` zvolte a připojte se k jinému procesu, ve kterém upravujete skript. Pomocí této metody můžete snadněji cílit na konkrétní logiku v poskytovateli typu interaktivním zadáváním výrazů do druhé instance (s úplným technologiem IntelliSense a dalšími funkcemi).

Můžete zakázat pouze můj kód ladění lépe identifikovat chyby v generovaném kódu. Informace o povolení nebo zakázání této funkce naleznete v [tématu Navigace prostřednictvím kódu pomocí ladicího programu](/visualstudio/debugger/navigating-through-code-with-the-debugger). Také můžete nastavit zachycení výjimky první šance `Debug` otevřením `Exceptions` nabídky a výběrem kláves Ctrl+Alt+E pro otevření dialogového `Exceptions` okna. V tomto dialogovém `Common Language Runtime Exceptions`okně `Thrown` zaškrtněte v části zaškrtněte políčko.

### <a name="implementation-of-the-type-provider"></a>Implementace poskytovatele typu

Tato část vás provede hlavní části implementace poskytovatele typu. Nejprve definujete typ pro samotného zprostředkovatele vlastního typu:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Tento typ musí být veřejný a musíte jej označit atributem [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) tak, aby kompilátor rozpoznal poskytovatele typu, když samostatný projekt F# odkazuje na sestavení, které obsahuje typ. Parametr *config* je volitelný a pokud je k dispozici, obsahuje kontextové informace o konfiguraci instance poskytovatele typu, kterou vytvoří kompilátor F#.

Dále implementovat rozhraní [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) V tomto případě použijete `TypeProviderForNamespaces` typ `ProvidedTypes` z rozhraní API jako základní typ. Tento typ pomocníka může poskytnout omezenou kolekci dychtivě zapředpokladužené obory názvů, z nichž každý přímo obsahuje konečný počet pevných, dychtivě poskytované typy. V tomto kontextu zprostředkovatel *elantně* generuje typy i v případě, že nejsou potřeba nebo použity.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Dále definujte místní soukromé hodnoty, které určují obor názvů pro zadané typy, a najděte samotné sestavení zprostředkovatele typu. Toto sestavení se později používá jako logický nadřazený typ vymýšcených typů, které jsou k dispozici.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Dále vytvořte funkci, která poskytne každý typ Type1... Typ100. Tato funkce je podrobněji vysvětlena dále v tomto tématu.

```fsharp
let makeOneProvidedType (n:int) = …
```

Dále vygenerujte 100 zadaných typů:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Dále přidejte typy jako zadaný obor názvů:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Nakonec přidejte atribut sestavení, který označuje, že vytváříte knihovnu DLL poskytovatele typu:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Poskytování jednoho typu a jeho členů

Funkce `makeOneProvidedType` provádí skutečnou práci poskytování jednoho z typů.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Tento krok vysvětluje implementaci této funkce. Nejprve vytvořte zadaný typ (například Type1, když n = 1 nebo Type57, když n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Měli byste si uvědomit následující body:

- Tento typ je zadaný vymazán.  Protože označujete, že `obj`základní typ je , instance se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v kompilovaném kódu.

- Když zadáte nevnořený typ, musíte zadat sestavení a obor názvů. Pro vymýšcené typy sestavení by měla být sestavení poskytovatele typu samotné.

Dále přidejte dokumentaci XML k typu. Tato dokumentace je zpožděna, to znamená vypočítané na vyžádání, pokud to kompilátor hostitele potřebuje.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Dále přidáte poskytnutou statickou vlastnost k typu:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Získání této vlastnosti bude vždy vyhodnotit řetězec "Hello!". Pro `GetterCode` vlastnost používá c) nabídku, která představuje kód, který kompilátor hostitele generuje pro získání vlastnosti. Další informace o nabídkách naleznete v [tématu Nabídky kódu (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Přidejte do vlastnosti dokumentaci XML.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Nyní připojte poskytnutou vlastnost k zadanému typu. Je nutné připojit zadaný člen k jednomu a pouze jednomu typu. V opačném případě člen nikdy nebude přístupný.

```fsharp
t.AddMember staticProp
```

Nyní vytvořte za předpokladu, konstruktor, který nepřebírá žádné parametry.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

Pro `InvokeCode` konstruktor vrátí c) nabídku, která představuje kód, který generuje kompilátor hostitele při volání konstruktoru. Můžete například použít následující konstruktor:

```fsharp
new Type10()
```

Instance zadaného typu bude vytvořena s podkladovými daty "Data objektu". Kód v uvozovkách obsahuje převod na [obj,](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) protože tento typ je vymazání tohoto zadaného typu (jak jste zadali při deklarovaném zadaném typu).

Přidejte dokumentaci XML do konstruktoru a přidejte zadaný konstruktor do zadaného typu:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Vytvořte druhý předpokladem konstruktoru, který má jeden parametr:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

Pro `InvokeCode` konstruktor opět vrátí c) nabídku, která představuje kód, který kompilátor hostitele vygenerovaný pro volání metody. Můžete například použít následující konstruktor:

```fsharp
new Type10("ten")
```

Instance poskytnutého typu je vytvořena s podkladovými daty "deset". Možná jste si již `InvokeCode` všimli, že funkce vrací nabídku. Vstup do této funkce je seznam výrazů, jeden na parametr konstruktoru. V tomto případě je k dispozici výraz, `args.[0]`který představuje hodnotu jednoho parametru v aplikaci . Kód pro volání konstruktoru vynutí vrácenou hodnotu vymývaného typu `obj`. Po přidání druhého poskytnutého konstruktoru do typu vytvoříte zajišťovnou vlastnost instance:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Získání této vlastnosti vrátí délku řetězce, což je reprezentace objektu. Vlastnost `GetterCode` vrátí nabídku F#, která určuje kód, který generuje kompilátor hostitele získat vlastnost. Podobně `InvokeCode`, `GetterCode` funkce vrátí nabídku. Kompilátor hostitele volá tuto funkci se seznamem argumentů. V tomto případě argumenty zahrnují pouze jeden výraz, který představuje instanci, na které `args.[0]`je volán getter, ke kterému můžete přistupovat pomocí . Implementace `GetterCode` pak splices do nabídky výsledků na vymažený typ `obj`a přetypování se používá k uspokojení mechanismu kompilátoru pro kontrolu typů, které je objekt řetězec. Další část `makeOneProvidedType` poskytuje metodu instance s jedním parametrem.

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

Nakonec vytvořte vnořený typ, který obsahuje 100 vnořených vlastností. Vytvoření tohoto vnořeného typu a jeho vlastnosti je zpožděn, to znamená, vypočítané na vyžádání.

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a>Podrobnosti o vymýšce poskytnutých typů

Příklad v této části obsahuje pouze *vymažené poskytnuté typy*, které jsou zvláště užitečné v následujících situacích:

- Při psaní zprostředkovatele pro informační prostor, který obsahuje pouze data a metody.

- Při psaní zprostředkovatele, kde přesné sémantiku typu runtime nejsou důležité pro praktické použití informačního prostoru.

- Při psaní zprostředkovatele pro informační prostor, který je tak velký a propojený, že není technicky proveditelné generovat skutečné typy .NET pro informační prostor.

V tomto příkladu je každý zadaný `obj`typ vymazán na typ a všechna `obj` použití typu se zobrazí jako typ v kompilovaném kódu. Ve skutečnosti základní objekty v těchto příkladech jsou řetězce, `System.Object` ale typ se zobrazí jako v kódu kompilace .NET. Stejně jako u všech použití vymazání typu můžete použít explicitní zabalení, rozbalení a odtypování k rozvrácení smazaných typů. V tomto případě přetypová výjimka, která není platná může mít za následek při použití objektu. Za běhu zprostředkovatele můžete definovat svůj vlastní typ privátní reprezentace pomoci chránit před falešnými reprezentace. Nelze definovat vymýšlí typy v F# sám. Smažte pouze poskytnuté typy. Je nutné pochopit důsledky, praktické a sémantické, pomocí vymažené typy pro poskytovatele typu nebo zprostředkovatele, který poskytuje vymýšlé typy. Vymýšcený typ nemá žádný skutečný typ .NET. Proto nelze provést přesné reflexe nad typem a může rozvrátit vymažené typy, pokud používáte přetypování za běhu a další techniky, které spoléhají na sémantiku typu přesný běh. Subverze vymýšlé typy často vede k typu přetypovací výjimky za běhu.

### <a name="choosing-representations-for-erased-provided-types"></a>Volba reprezentací pro vymývané typy zadaných.

Pro některá použití vymývaných typů není vyžadována žádná reprezentace. Například vymýšlý zadaný typ může obsahovat pouze statické vlastnosti a členy a žádné konstruktory a žádné metody nebo vlastnosti by vrátit instanci typu. Pokud můžete dosáhnout instance vymývaného zadaného typu, je třeba zvážit následující otázky:

**Jaké je vymazání poskytnutého typu?**

- Vymazání zadaného typu je způsob, jakým se typ zobrazí v kompilovaném kódu .NET.

- Vymazání zadaného vymazaného typu třídy je vždy prvním nesmazatým základním typem v řetězci dědičnosti typu.

- Vymazání zadaného typu vymazaného `System.Object`rozhraní je vždy .

**Jaké jsou reprezentace poskytnutého typu?**

- Sada možných objektů pro vymývaný typ zadaný se nazývá jeho reprezentace. V příkladu v tomto dokumentu jsou reprezentace všech vymýšlených zadaných typů `Type1..Type100` vždy objekty řetězce.

Všechna vyobrazení poskytnutého typu musí být kompatibilní s výmazem uvedeného typu. (V opačném případě bude buď kompilátor F# udělit chybu pro použití poskytovatele typu, nebo bude vygenerován neověřitelný kód .NET, který není platný. Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)

Můžete zvolit reprezentaci pro poskytnuté objekty pomocí některého z následujících přístupů, které jsou velmi časté:

- Pokud jednoduše poskytujete obálku silného typu přes existující typ .NET, často má smysl, aby váš typ vymazal na tento typ, používal instance tohoto typu jako reprezentace nebo obojí. Tento přístup je vhodný, pokud většina existujících metod na tomto typu stále smysl při použití verze silného typu.

- Pokud chcete vytvořit rozhraní API, které se výrazně liší od všech existujících rozhraní API .NET, má smysl vytvořit typy runtime, které budou vymazání typu a reprezentace pro poskytnuté typy.

Příklad v tomto dokumentu používá řetězce jako reprezentace zadaných objektů. Často může být vhodné použít jiné objekty pro reprezentace. Můžete například použít slovník jako vak vlastností:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Jako alternativu můžete definovat typ v zprostředkovateli typu, který bude použit za běhu k vytvoření reprezentace, spolu s jedním nebo více operací runtime:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Za předpokladu, že členové pak mohou vytvářet instance tohoto typu objektu:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

V takovém případě můžete (volitelně) použít tento typ jako výmaz typu `baseType` zadáním `ProvidedTypeDefinition`tohoto typu jako při vytváření :

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Klíčové lekce

V předchozí části bylo vysvětleno, jak vytvořit jednoduchého zprostředkovatele vymývání typu, který poskytuje řadu typů, vlastností a metod. Tato část také vysvětluje koncept vymazání typu, včetně některých výhod a nevýhod poskytování vymazaných typů od poskytovatele typu a popisované reprezentace vymazaných typů.

## <a name="a-type-provider-that-uses-static-parameters"></a>Zprostředkovatel typu, který používá statické parametry

Možnost parametrizovat poskytovatele typů statickými daty umožňuje mnoho zajímavých scénářů, a to i v případech, kdy zprostředkovatel nepotřebuje přístup k žádným místním nebo vzdáleným datům. V této části se dozvíte některé základní techniky pro sestavení takového poskytovatele.

### <a name="type-checked-regex-provider"></a>Typ kontrolovaný zprostředkovatel regex

Představte si, že chcete implementovat poskytovatele typu pro <xref:System.Text.RegularExpressions.Regex> regulární výrazy, které zabalí knihovny .NET v rozhraní, které poskytuje následující záruky kompilace:

- Ověření, zda je regulární výraz platný.

- Poskytuje pojmenované vlastnosti na shody, které jsou založeny na názvy skupin v regulárním výrazu.

Tato část ukazuje, jak pomocí poskytovatelů `RegexTyped` typů vytvořit typ, který vzor regulárního výrazu parametrizuje k poskytování těchto výhod. Kompilátor ohlásí chybu, pokud zadaný vzorek není platný, a poskytovatel typu může extrahovat skupiny ze vzoru, takže k nim můžete přistupovat pomocí pojmenovaných vlastností na shodách. Při návrhu poskytovatele typu byste měli zvážit, jak by jeho vystavené rozhraní API mělo vypadat koncovým uživatelům a jak se tento návrh přeloží do kódu .NET. Následující příklad ukazuje, jak pomocí takového rozhraní API získat součásti směrového kódu oblasti:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Následující příklad ukazuje, jak poskytovatel typu překládá tato volání:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Je třeba počítat s následujícím:

- Standardní typ Regex představuje `RegexTyped` parametrizovaný typ.

- Výsledkem `RegexTyped` konstruktoru je volání konstruktoru Regex, který předá argument statického typu pro vzorek.

- Výsledky `Match` metody jsou reprezentovány standardním <xref:System.Text.RegularExpressions.Match> typem.

- Každá pojmenovaná skupina má za následek poskytnutou vlastnost a přístup k vlastnosti `Groups` má za následek použití indexeru v kolekci shody.

Následující kód je jádrem logiky k implementaci takového zprostředkovatele a tento příklad vynese přidání všech členů do zadaného typu. Informace o jednotlivých přidaných členech naleznete v příslušné části dále v tomto tématu. Úplný kód naznejte, stáhněte si ukázku z [ukázkového balíčku F# 3.0](https://archive.codeplex.com/?p=fsharp3sample) na webu CodePlex.

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

Je třeba počítat s následujícím:

- Zprostředkovatel typu přebírá dva statické `pattern`parametry: , což `options`je povinné a , které jsou volitelné (protože je k dispozici výchozí hodnota).

- Po dodání statických argumentů vytvoříte instanci regulárního výrazu. Tato instance vyvolá výjimku, pokud je poškozen regex a tato chyba bude hlášena uživatelům.

- V `DefineStaticParameters` rámci zpětného volání definujete typ, který bude vrácen po zadání argumentů.

- Tento kód `HideObjectMethods` se nastaví na hodnotu true tak, aby prostředí Technologie IntelliSense zůstalo zjednodušené. Tento atribut `Equals`způsobí, `Finalize`že `GetType` , `GetHashCode`, a členy, které mají být potlačeny ze seznamů IntelliSense pro zadaný objekt.

- Použijete `obj` jako základní typ metody, ale budete `Regex` používat objekt jako runtime reprezentace tohoto typu, jak ukazuje následující příklad.

- Volání konstruktoru `Regex` vyvolá, <xref:System.ArgumentException> když regulární výraz není platný. Kompilátor zachytí tuto výjimku a hlásí chybovou zprávu uživateli v době kompilace nebo v editoru Sady Visual Studio. Tato výjimka umožňuje regulární výrazy, které mají být ověřeny bez spuštění aplikace.

Výše definovaný typ ještě není užitečný, protože neobsahuje žádné smysluplné metody nebo vlastnosti. Nejprve přidejte `IsMatch` statickou metodu:

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

Předchozí kód definuje metodu `IsMatch`, která přebírá řetězec `bool`jako vstup a vrací . Jedinou choulostivou `args` částí `InvokeCode` je použití argumentu v rámci definice. V tomto `args` příkladu je seznam nabídek, který představuje argumenty této metody. Pokud metoda je metoda instance, první `this` argument představuje argument. Však pro statickou metodu argumenty jsou všechny pouze explicitní argumenty metody. Všimněte si, že typ kótované hodnoty by měl `bool`odpovídat zadanému typu vrácení (v tomto případě). Všimněte si také, `AddXmlDoc` že tento kód používá metodu, aby se ujistil, že zadaná metoda má také užitečnou dokumentaci, kterou můžete zadat prostřednictvím technologie IntelliSense.

Dále přidejte metodu instance Match. Tato metoda by však měla vrátit `Match` hodnotu zadaného typu tak, aby skupiny lze přistupovat silným způsobem. Proto nejprve deklarovat `Match` typ. Vzhledem k tomu, že tento typ závisí na vzoru, který byl zadán jako statický argument, musí být tento typ vnořen do definice parametrizovaného typu:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Potom přidáte jednu vlastnost do typu Shoda pro každou skupinu. Za běhu je shoda reprezentována <xref:System.Text.RegularExpressions.Match> jako hodnota, takže nabídka, která <xref:System.Text.RegularExpressions.Match.Groups> definuje vlastnost, musí použít indexovnou vlastnost k získání příslušné skupiny.

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

Všimněte si, že přidáváte dokumentaci XML do poskytnuté vlastnosti. Všimněte si také, že `GetterCode` vlastnost lze číst, pokud je k `SetterCode` dispozici funkce a vlastnost může být zapsána, pokud je k dispozici funkce, takže výsledná vlastnost je jen pro čtení.

Nyní můžete vytvořit metodu instance, která `Match` vrací hodnotu tohoto typu:

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

Protože vytváříte metodu `args.[0]` instance, `RegexTyped` představuje instanci, na `args.[1]` které je metoda volána, a je vstupním argumentem.

Nakonec zadejte konstruktor tak, aby instance zadaný typ lze vytvořit.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Konstruktor pouze vymaže vytvoření standardní instance .NET Regex, která je `obj` opět zabalena do objektu, protože je vymazání zadaného typu. S tímto způsobem funguje ukázkové využití rozhraní API, které bylo zadáno dříve v tématu. Následující kód je úplný a konečný:

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a>Klíčové lekce

Tato část vysvětluje, jak vytvořit zprostředkovatele typu, který pracuje na jeho statické parametry. Zprostředkovatel zkontroluje statický parametr a poskytuje operace na základě jeho hodnoty.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Zprostředkovatel typu, který je podpořen místními daty

Často můžete chtít, aby poskytovatelé typů prezentovali rozhraní API nejen na základě statických parametrů, ale také informací z místních nebo vzdálených systémů. Tato část popisuje poskytovatele typů, kteří jsou založeni na místních datech, jako jsou například místní datové soubory.

### <a name="simple-csv-file-provider"></a>Jednoduchý poskytovatel souborů CSV

Jako jednoduchý příklad zvažte zprostředkovatele typu pro přístup k vědeckým datům ve formátu CSV (Comma Separated Value). Tato část předpokládá, že soubory CSV obsahují řádek záhlaví následovaný daty s plovoucí desetinnou táhou, jak ukazuje následující tabulka:

|Vzdálenost (metr)|Čas (druhý)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

Tato část ukazuje, jak zadat typ, který můžete `Distance` použít `float<meter>` k `Time` získání řádků `float<second>`s vlastností typu a vlastností typu . Pro jednoduchost jsou provedeny následující předpoklady:

- Názvy hlaviček jsou buď bez jednotky, nebo mají tvar "Název (jednotka)" a neobsahují čárky.

- Jednotky jsou všechny jednotky System International (SI), které definují modul [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#).](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)

- Jednotky jsou jednoduché (například metr) spíše než složené (například metr/s).

- Všechny sloupce obsahují data s plovoucí desetinnou tácem.

Úplnější poskytovatel by tato omezení uvolnil.

Opět prvním krokem je zvážit, jak by mělo rozhraní API vypadat. Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

V takovém případě by měl kompilátor převést tato volání na něco jako v následujícím příkladu:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

Optimální překlad bude vyžadovat, aby poskytovatel `CsvFile` typu definoval skutečný typ v sestavení poskytovatele typu. Poskytovatelé typů často spoléhají na několik pomocné typy a metody zabalit důležitou logiku. Vzhledem k tomu, že jsou míry `float[]` vymazány za běhu, můžete použít jako vymýšcený typ pro řádek. Kompilátor bude považovat různé sloupce za různé typy měr. Například první sloupec v našem `float<meter>`příkladu má `float<second>`typ a druhý má . Vymazání reprezentace však může zůstat poměrně jednoduché.

Následující kód ukazuje jádro implementace.

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

Všimněte si následujících bodů o implementaci:

- Přetížené konstruktory umožňují čtení původního souboru nebo souboru, který má stejné schéma. Tento vzor je běžné při psaní poskytovatele typu pro místní nebo vzdálené zdroje dat a tento vzor umožňuje místní soubor, který má být použit jako šablona pro vzdálená data.

- Můžete použít [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) hodnotu, která je předána do konstruktoru poskytovatele typu k vyřešení relativní názvy souborů.

- Metodu `AddDefinitionLocation` můžete použít k definování umístění poskytnutých vlastností. Proto pokud použijete `Go To Definition` na zapředpokladu vlastnost, soubor CSV se otevře v sadě Visual Studio.

- Typ můžete `ProvidedMeasureBuilder` použít k vyhledat jednotky SI `float<_>` a generovat příslušné typy.

### <a name="key-lessons"></a>Klíčové lekce

Tato část vysvětluje, jak vytvořit zprostředkovatele typu pro místní zdroj dat s jednoduchým schématem, které je obsaženo v samotném zdroji dat.

## <a name="going-further"></a>Chystáte se dále

Následující části obsahují návrhy na další studium.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Podívejte se na zkompilovaný kód pro vymývané typy

Chcete-li získat určitou představu o tom, jak použití poskytovatele typu odpovídá kódu, který je `HelloWorldTypeProvider` emitován, podívejte se na následující funkci pomocí, která se používá dříve v tomto tématu.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Zde je obrázek výsledného kódu dekompilované pomocí ildasm.exe:

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

Jak ukazuje příklad, všechny zmínky `Type1` o `InstanceProperty` typu a vlastnosti byly vymazány, takže pouze operace na typy runtime zapojeny.

### <a name="design-and-naming-conventions-for-type-providers"></a>Konvence návrhu a pojmenování pro poskytovatele typů

Při vytváření zprostředkovatelů typu dodržujte následující konvence.

**Zprostředkovatelé pro protokoly připojení** Obecně platí, že názvy většiny zprostředkovatelských knihoven DLL pro protokoly připojení k `TypeProvider` `TypeProviders`datům a službám, jako jsou připojení OData nebo SQL, by měly končit v aplikaci nebo . Použijte například název dll, který se podobá následujícímu řetězci:

`Fabrikam.Management.BasicTypeProviders.dll`

Ujistěte se, že vaše poskytnuté typy jsou členy odpovídajícího oboru názvů a označte protokol připojení, který jste implementovali:

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Poskytovatelé veřejných služeb pro obecné kódování**.  Pro poskytovatele typu nástroje, například pro regulární výrazy, může být poskytovatel typu součástí základní knihovny, jak ukazuje následující příklad:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

V tomto případě by zadaný typ se zobrazí v příslušném bodě podle běžných konvencí návrhu .NET:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Singleton zdroje dat**. Někteří poskytovatelé typů se připojují k jedinému vyhrazenému zdroji dat a poskytují pouze data. V takovém případě byste `TypeProvider` měli upustit příponu a použít normální konvence pro pojmenování .NET:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Další informace naleznete `GetConnection` v konvenci návrhu, která je popsána dále v tomto tématu.

### <a name="design-patterns-for-type-providers"></a>Návrhové vzory pro poskytovatele typů

Následující části popisují návrhové vzory, které můžete použít při vytváření poskytovatelů typů.

#### <a name="the-getconnection-design-pattern"></a>Vzor návrhu GetConnection

Většina poskytovatelů typu by `GetConnection` měla být zapsána tak, aby používala vzorek, který používají zprostředkovatelé typu v souboru FSharp.Data.TypeProviders.dll, jak ukazuje následující příklad:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Poskytovatelé typů podporovaní vzdálenými daty a službami

Před vytvořením poskytovatele typu, který je podporován vzdálenými daty a službami, je třeba zvážit řadu problémů, které jsou vlastní připojenému programování. Mezi tyto problémy patří následující aspekty:

- mapování schématu

- živost a zneplatnění v přítomnosti změny schématu

- ukládání do mezipaměti schématu

- asynchronní implementace operací přístupu k datům

- podpůrné dotazy, včetně dotazů LINQ

- pověření a ověřování

Toto téma není prozkoumat tyto problémy dále.

### <a name="additional-authoring-techniques"></a>Další vývojové techniky

Při psaní vlastní zprostředkovatelé typu, můžete použít následující další techniky.

### <a name="creating-types-and-members-on-demand"></a>Vytváření typů a členů na vyžádání

Rozhraní API ProvidedType má zpožděné verze AddMember.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Tyto verze se používají k vytvoření prostorů na vyžádání typů.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Poskytování typů polí a instancí obecného typu

Zadaným členům (jejichž podpisy zahrnují typy polí, typy odkazových čar a instance `MakeArrayType` `MakePointerType`obecných `MakeGenericType` typů) <xref:System.Type>pomocí `ProvidedTypeDefinitions`normálního , a na libovolné instanci aplikace , včetně .

> [!NOTE]
> V některých případech může být možné `ProvidedTypeBuilder.MakeGenericType`použít pomocníka v .  Další podrobnosti naleznete v dokumentaci k [spoje poskytovatele typu.](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)

### <a name="providing-unit-of-measure-annotations"></a>Poskytování poznámky měrné jednotky

Rozhraní API ProvidedTypes poskytuje pomocné soubory pro poskytování poznámky měření. Chcete-li například `float<kg>`zadat typ , použijte následující kód:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Chcete-li `Nullable<decimal<kg/m^2>>`zadat typ , použijte následující kód:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Přístup k místním nebo scriptovým místním zdrojům projektu

Každá instance poskytovatele typu může `TypeProviderConfig` být poskytnuta hodnota během výstavby. Tato hodnota obsahuje "složku rozlišení" pro zprostředkovatele (to znamená složku projektu pro kompilaci nebo adresář, který obsahuje skript), seznam odkazovaných sestavení a další informace.

### <a name="invalidation"></a>Neplatnost

Zprostředkovatelé mohou vyvolat signály zneplatnění upozornit službu jazyka F#, že předpoklady schématu může změnit. Dojde-li k neplatnosti, přeškrtne se kontrola typu, pokud je zprostředkovatel hostován v sadě Visual Studio. Tento signál bude ignorován, pokud je zprostředkovatel hostován v F# Interactive nebo kompilátorem F# (fsc.exe).

### <a name="caching-schema-information"></a>Informace o schématu ukládání do mezipaměti

Zprostředkovatelé musí často ukládat přístup k informacím o schématu. Data uložená v mezipaměti by měla být uložena pomocí názvu souboru, který je uveden jako statický parametr nebo jako uživatelská data. Příkladem ukládání do mezipaměti schématu `LocalSchemaFile` je parametr v zprostředkovatelích typu v `FSharp.Data.TypeProviders` sestavení. Při implementaci těchto zprostředkovatelů tento statický parametr nasměruje poskytovatele typu použít informace o schématu v zadaném místním souboru namísto přístupu ke zdroji dat v síti. Chcete-li použít informace o schématu uloženém v `ForceUpdate` `false`mezipaměti, musíte také nastavit statický parametr na . Podobnou techniku můžete použít k povolení přístupu k datům online a offline.

### <a name="backing-assembly"></a>Sestava zálohování

Při kompilaci `.dll` `.exe` nebo souboru je záložní soubor DLL pro generované typy staticky propojen do výsledného sestavení. Toto propojení je vytvořeno zkopírováním definic typů zprostředkujícíjazyk (IL) a všechny spravované prostředky z doprovodné sestavení do konečného sestavení. Při použití F# Interactive, záložní soubor DLL není zkopírován a je místo toho načten přímo do f# interaktivní proces.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Výjimky a diagnostika od poskytovatelů typů

Všechna použití všech členů z poskytnutých typů může vyvolat výjimky. Ve všech případech pokud poskytovatel typu vyvolá výjimku, kompilátor hostitele atributy chyby na konkrétní poskytovatele typu.

- Výjimky zprostředkovatele typu by nikdy neměly vést k chybám interního kompilátoru.

- Poskytovatelé typů nemohou hlásit upozornění.

- Pokud je poskytovatel typu hostován v kompilátoru F#, vývojovém prostředí F# nebo F# Interactive, jsou zachyceny všechny výjimky z tohoto zprostředkovatele. Message Vlastnost je vždy text chyby a žádné trasování zásobníku se zobrazí. Pokud se chystáte vyvolat výjimku, můžete vyvolat následující `System.NotSupportedException` `System.IO.IOException`příklady: , , `System.Exception`.

#### <a name="providing-generated-types"></a>Poskytování generovaných typů

Zatím tento dokument vysvětlil, jak poskytnout vymýšce typy. Mechanismus zprostředkovatele typu v f# můžete také použít k poskytnutí generovaných typů, které jsou přidány jako skutečné definice typu .NET do programu uživatelů. Musíte odkazovat na generované poskytované typy pomocí definice typu.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Pomocný kód ProvidedTypes-0.2, který je součástí verze F# 3.0, má pouze omezenou podporu pro poskytování generovaných typů. Následující příkazy musí být true pro definici generovaného typu:

- `isErased`musí být `false`nastavena na .

- Generovaný typ musí být přidán `ProvidedAssembly()`do nově vytvořeného typu , který představuje kontejner pro generované fragmenty kódu.

- Zprostředkovatel musí mít sestavení, které má skutečný záložní soubor .NET .dll s odpovídajícím souborem DLL na disku.

## <a name="rules-and-limitations"></a>Pravidla a omezení

Při psaní poskytovatelů typu mějte na paměti následující pravidla a omezení.

### <a name="provided-types-must-be-reachable"></a>Za předpokladu, že typy musí být dosažitelné

Všechny poskytnuté typy by měly být dosažitelné z nevnořených typů. Nevnořené typy jsou uvedeny `TypeProviderForNamespaces` ve volání konstruktoru nebo volání `AddNamespace`. Například pokud poskytovatel poskytuje `StaticClass.P : T`typ , musíte zajistit, že T je buď nevnořený typ nebo vnořené pod jeden.

Například někteří zprostředkovatelé mají statickou třídu, jako `DataTypes` je například, které obsahují tyto `T1, T2, T3, ...` typy. V opačném případě chyba říká, že byl nalezen odkaz na typ T v sestavě A, ale typ nebyl v této sestavě nalezen. Pokud se zobrazí tato chyba, ověřte, zda jsou všechny podtypy dosažitelné z typů zprostředkovatele. Poznámka: `T1, T2, T3...` Tyto typy se označují jako *průběžně.* Nezapomeňte je umístit do přístupného oboru názvů nebo do nadřazeného typu.

### <a name="limitations-of-the-type-provider-mechanism"></a>Omezení mechanismu poskytovatele typu

Mechanismus zprostředkovatele typu v F# má následující omezení:

- Základní infrastruktura pro poskytovatele typů v F# nepodporuje poskytované obecné typy nebo poskytnuté obecné metody.

- Mechanismus nepodporuje vnořené typy se statickými parametry.

## <a name="development-tips"></a>Tipy pro vývoj

Během procesu vývoje mohou být užitečné následující tipy:

### <a name="run-two-instances-of-visual-studio"></a>Spuštění dvou instancí sady Visual Studio

Můžete vyvinout poskytovatele typu v jedné instanci a otestovat zprostředkovatele v druhé, protože testovací ide bude mít zámek na soubor .dll, který zabraňuje poskytovatele typu znovu sestavit. Proto je nutné zavřít druhou instanci sady Visual Studio, zatímco zprostředkovatel je vytvořen v první instanci a potom je nutné znovu otevřít druhou instanci po vytvořeno zprostředkovatele.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Zprostředkovatelé typu ladění pomocí vyvolání fsc.exe

Zprostředkovatele typů můžete vyvolat pomocí následujících nástrojů:

- fsc.exe (Kompilátor příkazového řádku F#)

- fsi.exe (Interaktivní kompilátor F#

- devenv.exe (Visual Studio)

Zprostředkovatele typů můžete často ladit nejsnadněji pomocí souboru fsc.exe v souboru testovacího skriptu (například script.fsx). Ladicí program můžete spustit z příkazového řádku.

```console
devenv /debugexe fsc.exe script.fsx
```

  Můžete použít protokolování print-to-stdout.

## <a name="see-also"></a>Viz také

- [Zprostředkovatelé typů](index.md)
- [Sada Zprostředkovatel typu SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
