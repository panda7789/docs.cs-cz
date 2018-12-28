---
title: 'Kurz: Vytvoření zprostředkovatele typů'
description: Zjistěte, jak vytvořit vlastní F# poskytovatelů v F# 3.0 prozkoumáním několik jednoduchý typ zprostředkovatelů pro ilustraci základních konceptů.
ms.date: 05/16/2016
ms.openlocfilehash: c5a68df5f0b89fe9496ad86ab88208e0ec4bcdc9
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614529"
---
# <a name="tutorial-create-a-type-provider"></a>Kurz: Vytvoření zprostředkovatele typů

Mechanismus poskytovatele typu v F# je podstatnou část jeho podpory pro bohaté programování informace. Tento kurz vysvětluje, jak vytvořit vlastní typ zprostředkovatele provede vás vývoj několik jednoduchý typ zprostředkovatelů pro ilustraci základních konceptů. Další informace o mechanismu poskytovatele typu v F#, naleznete v tématu [poskytovatelů typů](index.md).

F# Ekosystému obsahuje celou řadu poskytovatelů typů pro běžně používané internetové a firemní datové služby. Příklad:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) zahrnuje poskytovatelů typů pro formáty dokumentů JSON, XML, CSV nebo HTML.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje silného typu přístup do databáze SQL pomocí mapování objektů a F# dotazů LINQ na tyto datové zdroje.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sadu poskytovatelů typů pro kompilaci změnami vkládání T-SQL v F#.

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sadu poskytovatelů typů pro použití pouze s programování rozhraní .NET Framework pro přístup k datové služby typu SQL, Entity Framework, OData a WSDL.

V případě potřeby můžete vytvořit vlastní poskytovatele typů nebo můžete odkazovat na zprostředkovateli typů, které jste vytvořili ostatní. Vaše organizace může mít například datové služby, které poskytuje jejichž počet pojmenovaných datových sad, každou s vlastní stabilní schéma dat. Můžete vytvořit poskytovatele typu, který schémata přečte a nabídne aktuální datové sady na programátorovi, tak silného typu.

## <a name="before-you-start"></a>Než začnete

Mechanismus poskytovatel typu je primárně určený pro vkládání stabilní data a služby informačních prostorů do F# programovací prostředí.

Tento mechanismus není určená pro vkládání informačních prostorů změní jehož schéma během provádění programu způsoby, které jsou relevantní pro aplikaci logiky. Navíc mechanismu, který není určená pro meta programovací uvnitř jazyk i v případě, že této doména obsahuje mezi platné použití. Tento mechanismus byste měli použít pouze v případě potřeby a kde vývoj poskytovatele typu poskytuje velmi vysokou hodnotu.

Měli byste se vyhnout, zápis poskytovatele typu, kde není k dispozici schéma. Podobně, měli byste se vyhnout zápis poskytovatele typu, kde běžný (nebo dokonce existující) bude stačit knihovny .NET.

Než začnete, může odpovědět na tyto otázky:

- Máte schéma zdroje informací? Pokud ano, co se mapování do F# a systém typů .NET?

- Můžete použít existující rozhraní API (dynamicky zadávaných) jako výchozí bod pro implementaci?

- Vy a vaše organizace mají dostatek používá zprostředkovatele typu tak, aby psali vhodné? By běžné knihovny .NET vašim potřebám?

- Jak moc se změní schéma?

- Se změní při psaní kódu?

- Se změní mezi kódování relace?

- Se změní při provádění programu?

Poskytovatelé typů jsou nejvhodnější pro situacích, kde je schéma stabilní za běhu a po celou dobu životnosti zkompilovaný kód.

## <a name="a-simple-type-provider"></a>Jednoduchý typ poskytovatele

Tato ukázka je Samples.HelloWorldTypeProvider, podobně jako na ukázky v `examples` adresáři [ F# typ poskytovatele sady SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Zprostředkovatel zpřístupní "typ mezerou", který obsahuje 100 vymazaného typy, jak ukazuje následující kód pomocí F# podpis syntaxi a vynechání podrobnosti pro všechny s výjimkou `Type1`. Další informace o typech vymazaného, naleznete v tématu [podrobnosti o vymaže poskytuje typy](#details-about-erased-provided-types) dále v tomto tématu.

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

Všimněte si, že se staticky označuje sadu typů a členů, které jsou k dispozici. V tomto příkladu není využít schopnost poskytovatele poskytují typy, které jsou závislé na schématu. Implementace zprostředkovatele typu je popsaný v následujícím kódu a podrobnosti jsou popsané v předchozích částech tohoto tématu.

>[!WARNING]
Mohou existovat rozdíly mezi tímto kódem a online ukázky.

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

K používání tohoto poskytovatele, otevřete samostatnou instanci sady Visual Studio, vytvořit F# skript a pak přidejte odkaz na poskytovateli z vašeho skriptu s použitím #r jak ukazuje následující kód:

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

Hledat typy pod `Samples.HelloWorldTypeProvider` obor názvů, který vygeneruje poskytovatele typu.

Předtím, než je provedena rekompilace poskytovateli, ujistěte se, že neukončíte všechny instance sady Visual Studio a F# interaktivní, která jsou pomocí zprostředkovatele knihovny DLL. Chyba sestavení, jinak dojde k vzhledem k tomu, že výstupní knihovnu DLL se uzamkne.

Ladění tohoto zprostředkovatele pomocí příkazů tisku, skript, který zpřístupňuje potížím s poskytovatelem a pak použít následující kód:

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Chcete-li ladit tento zprostředkovatel pomocí sady Visual Studio, otevřete příkazový řádek sady Visual Studio s přihlašovacími údaji správce a spusťte následující příkaz:

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Jako alternativu, otevřete sadu Visual Studio, otevřete nabídku ladění, zvolte `Debug/Attach to process…`a připojte k jiné `devenv` procesu, kde upravujete vašeho skriptu. Pomocí této metody můžete snadněji zaměřit konkrétní logický typ zprostředkovatele interaktivně zadáním výrazy do druhé instance (s plnou podporou technologie IntelliSense a dalších funkcí).

Můžete zakázat pouze můj kód, ladění, abyste lépe identifikovat chyby v generovaném kódu. Informace o tom, jak povolit nebo zakázat tuto funkci najdete v tématu [procházení kódu s ladicím programem](/visualstudio/debugger/navigating-through-code-with-the-debugger). Navíc můžete také nastavit první odpovídající výjimce zachytávání tak, že otevřete `Debug` nabídky a následným výběrem možnosti `Exceptions` nebo zadáním pomocí kláves Ctrl + Alt + E otevřete `Exceptions` dialogové okno. V tomto dialogovém okně v části `Common Language Runtime Exceptions`, vyberte `Thrown` zaškrtávací políčko.

### <a name="implementation-of-the-type-provider"></a>Implementace zprostředkovatele typu

Tato část vás provede hlavní části implementaci zprostředkovatele typu. Nejprve definujte typ pro vlastní typ zprostředkovatele, sama:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Tento typ musí být veřejné a je třeba označit ji [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) atribut tak, aby kompilátor rozpozná poskytovatele typu při samostatném F# projekt odkazuje na sestavení obsahující typ. *Config* parametr je nepovinný a pokud jsou k dispozici, obsahuje kontextové konfigurační informace pro poskytovatele typu instanci, která F# kompilátor vytvoří.

V dalším kroku implementujete [itypeprovider –](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) rozhraní. V tomto případě použijete `TypeProviderForNamespaces` typ `ProvidedTypes` rozhraní API jako základní typ. Typ této pomocné rutiny můžete uvést omezená kolekce například zobrazeném obory názvů, z nichž každý přímo obsahuje konečný počet opravili, například poskytované typy. V tomto kontextu, zprostředkovatel *například* generuje typy, i když nejsou potřeba nebo použít.

```fsharp
inherit TypeProviderForNamespaces(config)
```

V dalším kroku definujte místní soukromé hodnoty, které určují obor názvů pro poskytnutých typů a najít sestavení zprostředkovatele na typ, samotný. Toto sestavení se později používá jako logický nadřazený typ vymazaného typů, které jsou k dispozici.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Dále vytvořte funkce se každý typ Type1... Type100. Tato funkce je vysvětlené podrobněji dále v tomto tématu.

```fsharp
let makeOneProvidedType (n:int) = …
```

Dále vygenerujte 100 poskytnutých typů:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

V dalším kroku přidejte typy jako zadaný obor názvů:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Nakonec přidejte atribut sestavení, která označuje, že při vytváření poskytovatele typu knihovny DLL:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>Poskytuje jeden typ a její členy

`makeOneProvidedType` Funkce odvádí skutečnou práci poskytnout jeden z typů.

```fsharp
let makeOneProvidedType (n:int) = 
…
```

Tento krok popisuje implementaci této funkce. Nejprve vytvořte poskytnutého typu (například Type1, když n = 1, nebo Type57, když n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Nezapomeňte přitom následující body:

- To za předpokladu, že typ se vymažou.  Protože určujete, že je základní typ `obj`, instance se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v zkompilovaný kód.

- Když zadáte nevnořeném typu, je nutné zadat sestavení a oboru názvů. Pro mazání typy by měl být sestavení sestavení zprostředkovatele na typ, samotný.

V dalším kroku přidáte dokumentace XML typu. Tato dokumentace je zpoždění, to znamená, vyžaduje kompilátor hostitele, je-li vypočítat na vyžádání.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Dále přidáte zadaná statická vlastnost typu:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Získání této vlastnosti bude vždy vyhodnocena jako řetězec "Hello!". `GetterCode` Vlastnost používá F# nabídky, který představuje kód, který kompilátor hostitele generuje pro získání vlastnosti. Další informace o nabídkách najdete v tématu [uvozovky kódu (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Přidáte vlastnost dokumentace XML.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Zadaná vlastnost je teď možné připojte ke poskytnutého typu. Zadaný člen musí připojit k jeden a pouze jeden typ. V opačném případě člen již nikdy nebude přístupná.

```fsharp
t.AddMember staticProp
```

Teď vytvořte zadaný konstruktor, který nepřijímá žádné parametry.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode` Pro konstruktor vrátí F# nabídky, který představuje kód, který kompilátor hostitele generuje při volání konstruktoru. Například můžete použít následující konstruktor:

```fsharp
new Type10()
```

Instance zadaného typu se vytvoří s podkladová data "Data objektu". Kód v uvozovkách zahrnuje převod na [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) vzhledem k tomu, že je tento typ vymazání tento poskytnutý typ (protože jste zadali, pokud jste deklarovali poskytnutého typu).

Přidejte dokumentace XML do konstruktoru a přidejte zadaný konstruktor pro zadaný typ:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Vytvořte druhý zadaný konstruktor, který přijímá jeden parametr:

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode` Pro konstruktor znovu vrátí F# nabídku, která představuje kód generovaný kompilátorem hostitele pro volání metody. Například můžete použít následující konstruktor:

```fsharp
new Type10("ten")
```

S podkladová data "10" je vytvořena instance zadaného typu. Jste si už všimli, `InvokeCode` funkce vrátí do uvozovek. Vstup pro tuto funkci je seznamem výrazů, jeden pro každý parametr konstruktoru. V tomto případě je k dispozici ve výrazu, který představuje hodnotu jednoho parametru `args.[0]`. Kód pro volání konstruktoru převede návratovou hodnotu na typ vymazaného `obj`. Poté, co přidáte druhý zadaný konstruktor pro typ, vytvoříte zadanou instanci vlastnosti:

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Získávání tato vlastnost vrátí délku řetězce, který je reprezentace objektu. `GetterCode` Vrátí vlastnost F# nabídky, která určuje kód, který generuje kompilátor hostitele GET pro vlastnost. Stejně jako `InvokeCode`, `GetterCode` funkce vrátí do uvozovek. Kompilátor hostitele volání této funkce se seznamem argumentů. V takovém případě argumenty zahrnout pouze jediný výraz, který představuje instanci, na kterém je volána metoda getter, kterým můžete přistupovat pomocí `args.[0]`. Provádění `GetterCode` klikněte do nabídky výsledek mazání zadejte splices `obj`, a tím se uspokojí kompilátoru mechanismus pro kontrolu typů, že objekt je řetězec se používá přetypování. V další části `makeOneProvidedType` poskytuje metodu instance s jedním parametrem.

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

Nakonec vytvořte vnořený typ, který obsahuje 100 vnořené vlastnosti. Vytvoření tohoto vnořený typ a jeho vlastnosti je zpoždění, to znamená, vypočítat na vyžádání.

```fsharp
t.AddMembersDelayed(fun () -> 
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () -> 
    let staticPropsInNestedType = 
      [ for i in 1 .. 100 do
          let valueOfTheProperty = "I am string "  + string i

          let p = 
            ProvidedProperty(propertyName = "StaticProperty" + string i, 
              propertyType = typeof<string>, 
              isStatic = true,
              getterCode= (fun args -> <@@ valueOfTheProperty @@>))

          p.AddXmlDocDelayed(fun () -> 
              sprintf "This is StaticProperty%d on NestedType" i)

          yield p ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a>Podrobnosti o vymazaných poskytnutých typů

Příklad v této části uvádí pouze *vymaže poskytnutých typů*, které jsou obzvláště užitečná v následujících situacích:

- Když vytváříte zprostředkovatele pro informační prostor, který obsahuje pouze data a metody.

- Když vytváříte poskytovatele, kde sémantiku přesný typ modulu runtime nejsou zásadně důležité pro praktické využití místa na informace.

- Když vytváříte zprostředkovatele pro informační prostor, který je tak velký a propojených, že není technicky možné generovat skutečné typy .NET pro informační prostor.

V tomto příkladu každý zadaný typ se vymažou na typ `obj`, a zobrazí se všechna použití typu jako typ `obj` v zkompilovaný kód. Ve skutečnosti příslušné objekty v těchto příkladech jsou řetězce, ale zobrazí se jako typ `System.Object` v .NET zkompilovaný kód. I s všechna použití typ vymazání, můžete použít explicitní zabalení, rozbalení a přetypování na pokazit vymazány typy. V takovém případě může dojít k výjimce přetypování, který není platný při použití objektu. Zprostředkovatel modulu runtime můžete definovat vlastní privátní reprezentace typ a pomáhá chránit před false reprezentace. Nejde definovat vymazaného typy v F# samotný. Pouze poskytnutých typů mohou být vymazány. Je třeba porozumět následky, obě praktických a sémantické, buď pomocí vymaže vymazaného typy pro poskytovatele typu nebo zprostředkovatele, který obsahuje typy. Mazání typ nemá žádný skutečný typ .NET. Proto není přesný odraz přes typ a může pokazit vymazaného typy, pokud použijete přetypování modulu runtime a další techniky, které jsou závislé na přesné modulu runtime typu sémantiku. Subversion vymazaného typy často výsledkem přetypování typu výjimky za běhu.

### <a name="choosing-representations-for-erased-provided-types"></a>Výběr reprezentace pro vymazání poskytované typy

Pro některá použití vymazaných poskytnutých typů žádné reprezentace je povinný. Například vymazaného zadaný typ může obsahovat pouze statické vlastnosti a členů a žádné konstruktory a žádné vlastnosti nebo metody vrátí instanci typu. Pokud instance vymazaného může dosáhnout zadaný typ, musíte zvážit následující otázky:

**Co je mazání poskytnutého typu?**

- Mazání poskytnutého typu je, jak se typ vyskytuje v kompilovaného kódu .NET.

- Mazání typu zadaný vymazaného třídy je vždy první-vymaže základním typem v řetězu dědičnosti typu.

- Mazání vymazaného poskytnutého rozhraní typu je vždy `System.Object`.

**Co jsou reprezentace poskytnutého typu?**

- Sadu možných objektů pro mazání zadaný typ, se nazývají její reprezentace. V příkladu v tomto dokumentu, všechny k dispozici vymazaného reprezentace typů `Type1..Type100` jsou vždy řetězcových objektů.

Všechny reprezentace poskytnutého typu musí být kompatibilní s mazání poskytnutého typu. (V opačném případě buď F# kompilátoru vám poskytne chybu pro používání poskytovatele typu, nebo se vygeneruje neověřitelného kódu .NET, která není platná. Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)

Reprezentace zadaných objektů můžete pomocí některé z následujících dvou přístupů, které jsou běžně:

- Pokud zadáváte jednoduše obálky se silným typem přes existující typ formátu .NET, často má smysl pro váš typ chcete smazat tento typ, použijte instance tohoto typu jako reprezentace nebo obojí. Tento přístup je vhodné, pokud většina existující metody na typu stále dávat smysl, jestli používáte verzi silného typu.

- Pokud chcete vytvořit rozhraní API, které se liší výrazně z libovolného existujícího rozhraní API .NET, je vhodné vytvořit typy modulu runtime, které budou typu mazání a reprezentací pro poskytnutých typů.

V příkladu v tomto dokumentu používá řetězce jako reprezentace zadaných objektů. Často může být vhodné k použití jiných objektů pro vyjádření. Například můžete použít slovník jako kontejner objektů:

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Jako alternativu můžete definovat typ ve zprostředkovateli typu, který se použije v době běhu k reprezentaci, spolu s jednu nebo více operací modulu runtime:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Pokud členové pak lze vytvořit instance tohoto typu objektu:

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

V takovém případě může (volitelně) použijete tento typ jako typ vymazání tak, že zadáte tento typ jako `baseType` při vytváření `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Klíčové lekce

V předchozím oddílu bylo vysvětleno, jak vytvořit jednoduchý mazání typ zprostředkovatele, který poskytuje celou řadu typy, vlastnosti a metody. Tato část také vysvětlení konceptu mazání typu, včetně některých výhod a nevýhod poskytující vymazaného typy od zprostředkovatele typu a popsaných reprezentace vymazaného typy.

## <a name="a-type-provider-that-uses-static-parameters"></a>Typ zprostředkovatele, který používá statické parametry

Schopnost parametrizovat poskytovatelů typů ve statických dat umožňuje řadu zajímavých scénářů, dokonce i v případech, kdy zprostředkovatel nepotřebuje přístup k žádným datům místního nebo vzdáleného. V této části se dozvíte některé základní postupy pro takový zprostředkovatel sestavení.

### <a name="type-checked-regex-provider"></a>Typ zaškrtnutí poskytovatele regulární výraz

Představte si, že chcete implementovat poskytovatel typů pro regulární výrazy, které zabaluje rozhraní .NET <xref:System.Text.RegularExpressions.Regex> knihovny v rozhraní, které poskytuje následující záruky za kompilace:

- Ověřuje se, zda je platný regulární výraz.

- Poskytuje pojmenované vlastnosti na shody, které jsou založeny na všechny názvy skupin v regulárním výrazu.

Tato část ukazuje, jak vytvořit pomocí zprostředkovatelů typů `RegexTyped` zadejte, že vzor regulárního výrazu parametrizuje poskytuje tyto výhody. Kompilátor oznámí chybu, pokud zadaný vzor není platný a poskytovatele typu může extrahovat skupiny ze vzorku tak, aby vám můžou k nim přistupovat pomocí vlastnosti shody s názvem. Při návrhu poskytovatele typů, byste měli zvážit, jak by měl vypadat jeho vystavené rozhraní API pro koncové uživatele a jak se tento návrh přeloží do kódu .NET. Následující příklad ukazuje, jak získat komponenty směrové číslo oblasti pomocí těchto rozhraní API:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Následující příklad ukazuje, jak se zprostředkovatel typu přeloží těchto volání:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Je třeba počítat s následujícím:

- Představuje standardní typ regulární výraz parametrizovaný `RegexTyped` typu.

- `RegexTyped` Konstruktor výsledkem je volání konstruktoru Regex předání argumentu statického typu pro vzor.

- Výsledky `Match` metody jsou reprezentovány standardní <xref:System.Text.RegularExpressions.Match> typu.

- Každou pojmenovanou skupinu výsledkem zadaná vlastnost a přístupem k vlastnosti výsledkem použití indexer na shodu `Groups` kolekce.

Následující kód je základní logiku pro implementaci těchto zprostředkovatele a v tomto příkladu vynechá přidání všem členům poskytnutého typu. Informace o každý přidaný člen najdete v příslušné části dále v tomto tématu. Celý kód lze stáhnout ukázku z [ F# 3.0 balík vzorových](https://fsharp3sample.codeplex.com) na webu Codeplex.

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

- Zprostředkovatel typu přebírá dva parametry statické: `pattern`, což je povinné a `options`, (protože výchozí hodnota je zadáno) jsou volitelné.

- Po statické argumenty jsou dodávány, vytvoříte instanci regulárního výrazu. Tato instance vyvolá výjimku, pokud regulární výraz je poškozený a ohlásí tuto chybu pro uživatele.

- V rámci `DefineStaticParameters` zpětné volání, definujte typ, který bude vrácen, jakmile jsou zadané argumenty.

- Tento kód nastaví `HideObjectMethods` na hodnotu true, tak, aby zůstane zjednodušené prostředí IntelliSense. Způsobí, že tento atribut `Equals`, `GetHashCode`, `Finalize`, a `GetType` členy mají být potlačena ze seznamů technologie IntelliSense pro zadaný objekt.

- Použijete `obj` jako základní typ pro metodu, ale budete používat `Regex` objektu jako modul runtime reprezentaci tohoto typu, jak ukazuje následující příklad.

- Volání `Regex` vyvolá konstruktor <xref:System.ArgumentException> kdy regulární výraz není platný. Kompilátor tuto výjimku zachytí a ohlásí chybovou zprávu uživateli v době kompilace nebo v editoru sady Visual Studio. Tato výjimka umožňuje regulárních výrazů má být ověřen bez spuštění aplikace.

Typ definovaný výše není ještě užitečné, protože neobsahuje žádné smysluplné metody nebo vlastnosti. Nejprve přidejte statickou `IsMatch` metody:

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

Předcházející kód definuje metodu `IsMatch`, který přijímá řetězec jako vstup a vrátí `bool`. Pouze velmi obtížné část je použití `args` argument v rámci `InvokeCode` definice. V tomto příkladu `args` je seznam nabídek, které představuje argumenty pro tuto metodu. Pokud je metoda metodou instance, představuje první argument `this` argument. Pro statické metody, jsou argumenty všechny pouze explicitní argumenty metody. Všimněte si, že by měl odpovídat typu hodnoty v uvozovkách zadaný návratový typ (v tomto případě `bool`). Všimněte si také, tento kód používá `AddXmlDoc` metodu, abyste měli jistotu, že zadaná metoda má také užitečná dokumentace, které můžete zadat pomocí IntelliSense.

V dalším kroku přidáte instanci metody shoda. Nicméně tato metoda by měla vrátit hodnotu zadaný `Match` tak, aby skupiny je přístupná v podobě silného typu. Proto nejprve deklarujte `Match` typu. Protože tento typ závisí na vzor, který byl zadán jako statický argument, tento typ musí být vnořen v rámci definice typ s parametry:

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

Pak přidejte jednu vlastnost typ shody pro každou skupinu. Za běhu, je reprezentována shoda <xref:System.Text.RegularExpressions.Match> hodnoty, takže musíte použít uvozovky, který definuje vlastnost <xref:System.Text.RegularExpressions.Match.Groups> indexovanou vlastnost zobrazíte příslušné skupiny.

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

Znovu si všimněte, že přidáváte dokumentace XML do zadané vlastnosti. Všimněte si také, vlastnost může číst, pokud `GetterCode` funkce je k dispozici, a vlastnost je možné zapisovat, pokud `SetterCode` funkce je k dispozici, takže výsledné vlastnost je jen pro čtení.

Nyní můžete vytvořit metodu instance, která vrací hodnotu tohoto `Match` typu:

```fsharp
let matchMethod = 
    ProvidedMethod(
        methodName = "Match", 
        parameters = [ProvidedParameter("input", typeof<string>)], 
        returnType = matchTy, 
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

Protože vytváříte metodu instance `args.[0]` představuje `RegexTyped` instanci, na kterém je volána metoda, a `args.[1]` je vstupní argument.

A konečně Poskytněte konstruktor tak, že můžete vytvořit instance zadaného typu.

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Konstruktor vymaže pouze k vytvoření instance regulární výraz .NET standard, která je znovu zabalená do objektu, protože `obj` je mazání poskytnutého typu. Díky této změně použití ukázkové rozhraní API, uvedenou výše v tomto tématu funguje podle očekávání. Následující kód je kompletní a poslední:

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
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

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

Tato část bylo vysvětleno, jak vytvořit typ zprostředkovatele, který funguje na jeho statické parametry. Zprostředkovatel ověří statický parametr a poskytuje operace na základě jeho hodnoty.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Typ zprostředkovatele, který se zálohuje pomocí místních dat

Často můžete poskytovatelů typů zobrazíte rozhraní API založené na pouze statické parametry, ale také informace z místních nebo vzdálených systémů. Tato část popisuje poskytovatelů typů, které jsou založeny na místní data, jako jsou místní datové soubory.

### <a name="simple-csv-file-provider"></a>Zprostředkovatel souborů jednoduché sdíleného svazku clusteru

Jako jednoduchý příklad zvažte poskytovatele typu pro přístup k vědeckých dat ve formátu hodnota oddělených čárkami (CSV). V této části se předpokládá, že soubory CSV obsahovat řádek záhlaví, za nímž následuje data s plovoucí desetinnou, jak ukazuje následující tabulka:

|Distance (měření)|Čas (sekundy)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

Tato část ukazuje, jak zadat typ, který vám umožní získat řádky s `Distance` vlastnost typu `float<meter>` a `Time` vlastnost typu `float<second>`. Pro jednoduchost jsou provedeny následující předpoklady:

- Názvy záhlaví jsou buď jednotky bez nebo mít formát _služba ._protokol "Název" (jednotky) a neobsahují čárky.

- Jednotky jsou všechny jednotky mezinárodní systému (SI) [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames modulu (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modul definuje.

- Jednotky jsou všechny jednoduché (například měřit) spíše než složený (například měřiče za sekundu).

- Všechny sloupce obsahují s plovoucí desetinnou čárkou datového bodu.

Úplnější poskytovatele by povolte těchto omezení.

Prvním krokem je opět vzít v úvahu, jak by měl vypadat rozhraní API. Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

V takovém případě by měl kompilátor převést těchto volání na něco jako v následujícím příkladu:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

Optimální převod bude vyžadovat poskytovatele typu pro definování reálné `CsvFile` typ v sestavení poskytovatele typu. Zprostředkovatelé typů se často spoléhat na několik pomocné rutiny typy a metody k zabalení důležité logiku. Míry jsou vymazány za běhu, takže můžete využívat `float[]` vymazaného typ pro řádek. Kompilátor bude považovat různé sloupce s typy jiné míry. Například první sloupec v našem příkladu má typ `float<meter>`, a druhý `float<second>`. Mazání reprezentace však může zůstat úplně jednoduché.

Následující kód ukazuje základní implementaci.

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data = 
        seq { for line in File.ReadAllLines(filename) |> Seq.skip 1 do
                 yield line.Split(',') |> Array.map float }
        |> Seq.cache
    member __.Data = data

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

Mějte na paměti následující skutečnosti o implementaci:

- Přetížené konstruktory povolit původní soubor nebo ten, který má stejné schéma pro čtení. Tento model je běžná v případě, že napíšete poskytovatele typu pro místní nebo vzdálené datové zdroje a tento model umožňuje místní soubor, který se použije jako šablonu pro vzdálená data.

- Můžete použít [typeproviderconfig –](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) hodnotu, která je předán konstruktor zprostředkovatele typu k překladu názvů relativní souboru.

- Můžete použít `AddDefinitionLocation` metodu pro určení umístění zadané vlastnosti. Proto pokud používáte `Go To Definition` zadané vlastnosti, otevře se soubor CSV v sadě Visual Studio.

- Můžete použít `ProvidedMeasureBuilder` typu k vyhledání jednotek SI a ke generování příslušného `float<_>` typy.

### <a name="key-lessons"></a>Klíčové lekce

Tato část bylo vysvětleno, jak vytvořit poskytovatele typů pro místní zdroj dat s jednoduché schéma, které je obsažen ve zdroji dat, samotného.

## <a name="going-further"></a>Když budete pokračovat

Následující části obsahují návrhy pro další studie.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Podívejte se na zkompilovaný kód pro mazání typy

Abyste získali představu o tom, jak pomocí poskytovatele typu odpovídá kód, který je vygenerován, podívejte se na následující funkci pomocí `HelloWorldTypeProvider` , který se používá dříve v tomto tématu.

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Tady je obrázek výsledný kód decompiled pomocí ildasm.exe:

```
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

Jak ukazuje příklad, všechny zmínky typu `Type1` a `InstanceProperty` vlastnost byly vymazány, byste museli opustit pouze operace u typů modulu runtime používané.

### <a name="design-and-naming-conventions-for-type-providers"></a>Návrh a vytváření názvů pro zprostředkovatele typů

Prohlédněte si následující konvence při vytváření poskytovatelů typů.

**Poskytovatelé připojení protokolů** obecně by měly končit názvy zprostředkovatelů většinu knihoven DLL pro data a služby připojení protokolů, jako je připojení OData nebo SQL `TypeProvider` nebo `TypeProviders`. Například použijte název knihovny DLL, která se podobá následující řetězec:

```
  Fabrikam.Management.BasicTypeProviders.dll
```

Zkontrolujte, jestli jsou členové odpovídající obor názvů poskytnutých typů a označení připojení protokol, který jste implementovali:

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Nástroje zprostředkovatele pro obecné kódování**.  Pro nástroj poskytovatele typu jako, který je pro regulární výrazy poskytovatele typu, může být součástí základní knihovny, jako v následujícím příkladu:

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

V takovém případě poskytnutého typu objevuje v odpovídajícím bodě podle normální návrhu konvence .NET:

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

**Zdroje dat typu singleton**. Někteří poskytovatelé typ připojení ke zdroji dat jeden vyhrazený a poskytují pouze data. V takovém případě měl snížit `TypeProvider` přípony a použít běžné konvence pro pojmenování .NET:

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Další informace najdete v tématu `GetConnection` návrh konvence, která je popsána dále v tomto tématu.

### <a name="design-patterns-for-type-providers"></a>Způsoby návrhu pro zprostředkovatelů typů

Následující části popisují vzorů návrhu, které můžete použít při vytváření poskytovatelů typů.

#### <a name="the-getconnection-design-pattern"></a>Vzor návrhu GetConnection

Většina poskytovatelů typů by měly být napsány k použití `GetConnection` vzor, který používá typ zprostředkovatele v FSharp.Data.TypeProviders.dll, jak ukazuje následující příklad:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Zprostředkovatelé typů se opírá o vzdáleným datům a službám

Než vytvoříte poskytovatele typu, který je zajištěná vzdáleným datům a službám, je nutné zvážit řadu problémů, které vyplývají z připojených programování. Tyto problémy v úvahu následující aspekty:

- mapování schématu

- aktivity a zneplatnění za přítomnosti změny schématu

- schéma, ukládání do mezipaměti

- implementace asynchronní operací přístupu k datům

- Podpora dotazů, včetně dotazů LINQ

- pověření a ověřování

Toto téma není prozkoumat tyto problémy dále.

### <a name="additional-authoring-techniques"></a>Další postupy pro vytváření obsahu

Při psaní vlastních poskytovatelů typů, můžete použít následující další techniky.

### <a name="creating-types-and-members-on-demand"></a>Vytváření typů a členů na vyžádání

Rozhraní API ProvidedType má zpoždění verzích přidávat členy.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Tyto verze se používají k vytvoření mezer na vyžádání z typů.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Poskytuje typy polí a vytváření instancí obecného typu

Zkontrolujte zadaný členy (jehož podpisy zahrnují vytváření instancí obecné typy, typy polí a typy byref) s použitím normální `MakeArrayType`, `MakePointerType`, a `MakeGenericType` na jakoukoli instanci <xref:System.Type>, včetně `ProvidedTypeDefinitions`.

> [!NOTE]
> V některých případech bude pravděpodobně nutné použít Pomocník `ProvidedTypeBuilder.MakeGenericType`.  Najdete v článku [dokumentace k sadě SDK zprostředkovatele typu](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) další podrobnosti.

### <a name="providing-unit-of-measure-annotations"></a>Poskytuje jednotka měření poznámky

Rozhraní API pro ProvidedTypes poskytuje pomocné rutiny pro poskytování míru poznámky. Například zadejte typ `float<kg>`, použijte následující kód:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  K poskytování typ `Nullable<decimal<kg/m^2>>`, použijte následující kód:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Přístup k prostředkům místních pro projekt nebo místní skript

Mohou být zadány všechny instance poskytovatele typu `TypeProviderConfig` hodnota během konstrukce. Tato hodnota obsahuje poskytovatele (to znamená, složky projektu pro sestavení nebo adresáře, který obsahuje skript), seznam odkazovaných sestavení a další informace o složce"řešení".

### <a name="invalidation"></a>Zrušení

Poskytovatelé může vyvolat zneplatnění signály upozornit F# služba jazyka, které mohlo dojít ke změně schématu předpoklady. Pokud dojde k zrušení, typecheck je znovu, pokud zprostředkovatel je hostovaná v sadě Visual Studio. Tento signál se bude ignorovat, pokud je zprostředkovatel hostovaný v F# interaktivní, nebo F# kompilátor (fsc.exe).

### <a name="caching-schema-information"></a>Ukládání do mezipaměti informace o schématu

Poskytovatelé musí často ukládat do mezipaměti přístup k informacím o schématu. Data uložená v mezipaměti ukládat pomocí názvu souboru, který je přiřazen jako statický parametr nebo jako uživatelská data. Je například ukládání do mezipaměti schématu `LocalSchemaFile` parametr ve zprostředkovateli typů v `FSharp.Data.TypeProviders` sestavení. Při provádění těchto zprostředkovatelů tento statický parametr nařídí zprostředkovateli typu použít informace o schématu v zadaném souboru místní místo přístup ke zdroji dat přes síť. Pokud chcete používat informace uložené v mezipaměti schématu, musíte taky nastavit statický parametr `ForceUpdate` k `false`. Podobný postup můžete použít k povolení přístupu k datům online i offline.

### <a name="backing-assembly"></a>Základní sestavení

Pokud kompilujete `.dll` nebo `.exe` soubor, záložní soubor .dll pro generované typy je staticky propojené do výsledného sestavení. Tento odkaz se vytvoří tak, že zkopírujete definice typu Intermediate Language (IL) a všechny spravované prostředky z zálohování sestavení do konečného sestavení. Při použití F# Interactive, záložní soubor .dll není zkopírován a místo toho nahrán přímo F# interaktivní proces.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Výjimky a Diagnostika ze zprostředkovatelů typů

Všechny výskyty všechny členy z poskytnutých typů může vyvolat výjimky. Ve všech případech Pokud zprostředkovatel typu vyvolá výjimku, kompilátor hostitele atributy chyby na konkrétní typ poskytovatele.

- Typ zprostředkovatele výjimky by nikdy výsledkem vnitřních chybách kompilátoru.

- Zprostředkovatelé typů nejde hlásit upozornění.

- Když je poskytovatel typů hostované v F# kompilátoru, F# vývojové prostředí, nebo F# interaktivní, jsou zachyceny všechny výjimky z tohoto zprostředkovatele. Vlastnost Message je vždy text chyby a zobrazí se žádná trasování zásobníku. Pokud se chystáte vytvořit výjimku, může vyvolat následující příklady: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.

#### <a name="providing-generated-types"></a>Poskytuje generované typy

Tento dokument má zatím vysvětlil, jak poskytnout vymazaného typy. Můžete také použít mechanismus poskytovatele typu v F# poskytnout generované typy, které jsou přidány jako skutečné definice typů .NET do programu uživatelů. Musíte odkazovat na vygenerované poskytované typy pomocí definice typu.

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Kód pomocného objektu ProvidedTypes-0.2, který je součástí F# verzi 3.0 má omezenou podporu pro poskytování generované typy. Generovaný typ definice musí platit následující příkazy:

- `isErased` musí být nastaveno na `false`.

- Generovaný typ musí být přidán do nově vytvořeného `ProvidedAssembly()`, která představuje kontejner pro fragmenty generovaného kódu.

- Poskytovatel musí mít sestavení, který má skutečné záložní soubor .dll .NET s odpovídající soubor DLL na disku.

## <a name="rules-and-limitations"></a>Pravidla a omezení

Při zápisu poskytovatelů typů, uvědomte si následující pravidla a omezení.

### <a name="provided-types-must-be-reachable"></a>Poskytnutých typů musí být dosažitelná

Všechny za předpokladu, že typy by měly být dosažitelný z jiných vnořené typy. Vnořené typy jsou uvedeny ve volání `TypeProviderForNamespaces` konstruktoru nebo volání `AddNamespace`. Například, pokud zprostředkovatel poskytuje typ `StaticClass.P : T`, ujistěte se, že je T nevnořeném typu nebo vnořené v části o jednu.

Například někteří poskytovatelé, jako mají statickou třídu `DataTypes` , které obsahují tyto `T1, T2, T3, ...` typy. V opačném případě chyba říká, že byl nalezen odkaz na typ T v sestavení A, ale typ nebyl nalezen v tomto sestavení. Pokud tato chyba se zobrazí, ověřte, že všechny podtypy dosažitelný z poskytovatele typů. Poznámka: Tyto `T1, T2, T3...` typy jsou označovány jako *na průběžné* typy. Mějte na paměti do přístupné obor názvů nebo nadřazeného typu.

### <a name="limitations-of-the-type-provider-mechanism"></a>Omezení mechanismu pro zprostředkovatele typů

Mechanismus poskytovatele typu v F# má následující omezení:

- Základní infrastruktury pro poskytovatele typu v F# nepodporuje obecné typy nebo obecné metody k dispozici.

- Mechanismus nepodporuje vnořené typy se statické parametry.

## <a name="development-tips"></a>Tipy pro vývoj

Následující tipy mohou být užitečné během procesu vývoje:

### <a name="run-two-instances-of-visual-studio"></a>Spusťte dvě instance sady Visual Studio

Můžete vyvíjet v jedné instanci poskytovatele typu a testovat zprostředkovatele v jiném, protože testovací prostředí IDE se zámek na souboru .dll, který brání poskytovatele typu se provádělo opětovné sestavení. Proto je třeba zavřít druhou instanci aplikace Visual Studio a poskytovatel je součástí první instance, a pak musíte znovu otevřete druhou instanci po sestavení zprostředkovatele.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Ladění pomocí volání fsc.exe zprostředkovatelů typů

Zprostředkovatelé typů lze vyvolat pomocí následujících nástrojů:

- FSC.exe ( F# příkazového řádku kompilátoru)

- fsi.exe ( F# interaktivní kompilátoru)

- devenv.exe (Visual Studio)

Zprostředkovatelé typů můžete ladit často nejsnadněji pomocí fsc.exe na soubor skriptu testu (například script.fsx). Můžete spustit ladicí program z příkazového řádku.

```
  devenv /debugexe fsc.exe script.fsx
```

  Můžete použít protokolování tiskových stdout.

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé typů](index.md)
- [Typ poskytovatele sady SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)