---
title: 'Kurz: vytvoření poskytovatele typu'
description: 'Naučte se vytvářet vlastní poskytovatele typu F # v F # 3,0 prozkoumáním několika poskytovatelů jednoduchých typů pro ilustraci základních konceptů.'
ms.date: 11/04/2019
ms.openlocfilehash: 67ebd91007ff814370573ebc1a65b2c7a8399f7d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202134"
---
# <a name="tutorial-create-a-type-provider"></a>Kurz: vytvoření poskytovatele typu

Mechanismus poskytovatele typu v jazyce F # je důležitou součástí své podpory pro bohatou programování informací. V tomto kurzu se dozvíte, jak vytvořit vlastní poskytovatele typů prostřednictvím vývoje několika jednoduchých zprostředkovatelů typů pro ilustraci základních konceptů. Další informace o mechanismu poskytovatele typu v F # naleznete v tématu [Poskytovatelé typů](index.md).

Ekosystém F # obsahuje rozsah zprostředkovatelů typů pro běžně používané internetovou a podnikovou datovou službu. Příklad:

- [FSharp. data](https://fsharp.github.io/FSharp.Data/) zahrnují poskytovatele typů pro formáty dokumentů JSON, XML, CSV a HTML.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje přístup silného typu k databázím SQL prostřednictvím mapování objektů a dotazů F # LINQ na tyto zdroje dat.

- [FSharp. data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) má sadu poskytovatelů typů pro kontrolované vkládání T-SQL do jazyka F # v době kompilace.

- [FSharp. data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sada zprostředkovatelů typů pro použití s .NET Framework programováním pro přístup k datovým službám SQL, Entity Framework, OData a WSDL.

V případě potřeby můžete vytvořit vlastní poskytovatele typu nebo můžete odkazovat na poskytovatele typu, který vytvořili jiní uživatelé. Vaše organizace může mít například datovou službu, která poskytuje velký a rostoucí počet pojmenovaných datových sad, z nichž každá má vlastní stabilní schéma dat. Můžete vytvořit poskytovatele typu, který přečte schémata a prezentuje aktuální datové sady programátorovi pomocí silného typu.

## <a name="before-you-start"></a>Než začnete

Mechanismus poskytovatele typů je navržený hlavně pro vkládání stabilních informací a informací o službách do programovacího prostředí F #.

Tento mechanismus není určený pro vkládání prostorů s informacemi, jejichž změny schématu během provádění programu jsou důležité pro programovou logiku. Mechanismus není navržený pro účely meta programování v rámci jazyka, a to i v případě, že doména obsahuje nějaká platná použití. Tento mechanismus byste měli použít pouze v případě potřeby a tam, kde vývoj poskytovatele typu poskytuje velmi vysokou hodnotu.

Měli byste se vyhnout psaní poskytovatele typu, pokud není k dispozici schéma. Podobně byste se měli vyhnout psaní poskytovatele typu, kde by měla být obvyklá (nebo dokonce stávající) knihovna .NET.

Než začnete, můžete se zeptat na tyto otázky:

- Máte schéma pro svůj zdroj informací? Pokud ano, co je mapování na systém typů F # a .NET?

- Můžete použít existující (dynamicky typované) rozhraní API jako výchozí bod pro vaši implementaci?

- Budete vy a vaše organizace mít k dispozici dostatek využití poskytovatele typu, abyste ho mohli využít k psaní? Bude normální knihovna .NET vyhovovat vašim potřebám?

- Kolik schématu se změní?

- Změní se během kódování?

- Změní se mezi relacemi kódování?

- Změní se během provádění programu?

Poskytovatelé typů jsou nejvhodnější pro situace, kdy je schéma stabilní za běhu a během životnosti zkompilovaného kódu.

## <a name="a-simple-type-provider"></a>Jednoduchý poskytovatel typu

Tato ukázka je Samples. HelloWorldTypeProvider, podobně jako ukázky v `examples` adresáři sady [SDK poskytovatele typu F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Zprostředkovatel zpřístupňuje "typ prostoru", který obsahuje 100 vymazaných typů, jak následující kód ukazuje použití syntaxe signatury F # a vynechání podrobností pro všechny s výjimkou `Type1` . Další informace o vymazaných typech najdete v [podrobnostech o vymazaných poskytovaných typech](#details-about-erased-provided-types) dále v tomto tématu.

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

Všimněte si, že sada typů a zadaných členů je staticky známá. Tento příklad nevyužívá možnost poskytovatelů k poskytování typů, které jsou závislé na schématu. Implementace poskytovatele typu je popsaná v následujícím kódu a podrobnosti jsou uvedené v dalších částech tohoto tématu.

> [!WARNING]
> Mohou existovat rozdíly mezi tímto kódem a online ukázkami.

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

Chcete-li použít tohoto poskytovatele, otevřete samostatnou instanci aplikace Visual Studio, vytvořte skript F # a pak přidejte odkaz na poskytovatele ze skriptu pomocí #r, jak ukazuje následující kód:

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

Pak hledejte typy pod `Samples.HelloWorldTypeProvider` oborem názvů, který poskytovatel typu vygeneroval.

Než znovu zkompilujete poskytovatele, ujistěte se, že jste uzavřeli všechny instance aplikace Visual Studio a F# Interactive, které používají knihovnu DLL zprostředkovatele. V opačném případě dojde k chybě sestavení, protože výstupní knihovna DLL bude uzamčena.

Chcete-li ladit tohoto poskytovatele pomocí příkazů Print, vytvořte skript, který zveřejňuje problém se zprostředkovatelem, a poté použijte následující kód:

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Pokud chcete tohoto poskytovatele ladit pomocí sady Visual Studio, otevřete Developer Command Prompt pro Visual Studio s přihlašovacími údaji správce a spusťte následující příkaz:

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Jako alternativu otevřete aplikaci Visual Studio, otevřete nabídku ladění, vyberte možnost `Debug/Attach to process…` a připojte se k jinému `devenv` procesu, ve kterém jste skript upravovali. Pomocí této metody můžete snadněji cílit specifickou logiku v poskytovateli typu pomocí interaktivního psaní výrazů do druhé instance (s plnou IntelliSense a dalšími funkcemi).

Můžete zakázat ladění Pouze můj kód pro lepší identifikaci chyb v generovaném kódu. Informace o tom, jak povolit nebo zakázat tuto funkci, naleznete v tématu [navigace prostřednictvím kódu pomocí ladicího programu](/visualstudio/debugger/navigating-through-code-with-the-debugger). Také můžete nastavit, aby se při zachycení výjimky s první pravděpodobností nastavila `Debug` Nabídka a pak vybrat nebo kliknutím na klávesovou zkratku `Exceptions` CTRL + ALT + E otevřít `Exceptions` dialogové okno. V tomto dialogovém okně zaškrtněte políčko v části `Common Language Runtime Exceptions` `Thrown` .

### <a name="implementation-of-the-type-provider"></a>Implementace poskytovatele typu

V této části se seznámíte s hlavními částmi implementace poskytovatele typu. Nejprve definujte typ samotného vlastního poskytovatele typu:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Tento typ musí být veřejný a musí být označen atributem [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) , aby kompilátor rozpoznal poskytovatele typu, když se na sestavení, které obsahuje daný typ, odkazuje v případě samostatného projektu F #. Parametr *Konfigurace* je nepovinný, a pokud je k dispozici, obsahuje kontextové informace o konfiguraci pro instanci zprostředkovatele typu, kterou vytvoří kompilátor F #.

Dále implementujete rozhraní [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) . V takovém případě použijete `TypeProviderForNamespaces` typ z `ProvidedTypes` rozhraní API jako základní typ. Tento typ pomocníka může poskytnout konečnou kolekci oborů názvů eagerly, z nichž každá z nich přímo obsahuje konečný počet pevných eagerly poskytovaných typů. V tomto kontextu zprostředkovatel *eagerly* generuje typy i v případě, že nejsou požadovány nebo použity.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Dále definujte místní soukromé hodnoty, které určují obor názvů pro poskytnuté typy a vyhledejte samotné sestavení poskytovatele typu. Toto sestavení je použito později jako logický nadřazený typ vymazaných typů, které jsou k dispozici.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Dále vytvořte funkci, která poskytne každému z typů typ1... Type100. Tato funkce je podrobněji vysvětlena dále v tomto tématu.

```fsharp
let makeOneProvidedType (n:int) = …
```

Dále vygenerujte poskytnuté typy 100:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Dále přidejte typy jako poskytnutý obor názvů:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Nakonec přidejte atribut Assembly, který označuje, že vytváříte knihovnu DLL typu zprostředkovatele:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Poskytování jednoho typu a jeho členů

`makeOneProvidedType`Funkce provede skutečnou práci jednoho z typů.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Tento krok vysvětluje implementaci této funkce. Nejprve vytvořte poskytnutý typ (například typ1, pokud n = 1 nebo Type57, pokud n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Všimněte si, že byste měli mít na paměti následující body:

- Tento poskytnutý typ se vymaže.  Vzhledem k tomu, že označíte, že základní typ je `obj` , instance se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v kompilovaném kódu.

- Pokud zadáte nevnořený typ, je nutné zadat sestavení a obor názvů. U vymazaných typů by sestavení mělo být samotné sestavení poskytovatele typu.

Dále přidejte dokumentaci XML k typu. Tato dokumentace je zpožděná, to znamená, že je vypočítaná na vyžádání, pokud ji hostitel kompilátor potřebuje.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Dále přidáte poskytnutou statickou vlastnost do tohoto typu:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Získání této vlastnosti se vždy vyhodnotí jako řetězec "Hello!". `GetterCode`Pro vlastnost používá uvozovku F #, která představuje kód, který kompilátor hostitele generuje pro získání vlastnosti. Další informace o nabídkách naleznete v tématu [Code quotes (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Přidejte do vlastnosti dokumentaci XML.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Nyní připojí poskytnutou vlastnost k poskytnutému typu. Zadaný člen musíte připojit k jednomu typu a pouze k jednomu typu. V opačném případě nebude člen nikdy přístupný.

```fsharp
t.AddMember staticProp
```

Nyní vytvořte poskytnutý konstruktor, který nepřijímá žádné parametry.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode`Konstruktor for vrátí nabídku F #, která představuje kód, který kompilátor hostitele generuje při volání konstruktoru. Například můžete použít následující konstruktor:

```fsharp
new Type10()
```

Instance poskytnutého typu bude vytvořena pomocí podkladových dat "data objektů". Kód v uvozovkách obsahuje převod na [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) , protože tento typ je vymazání tohoto poskytnutého typu (jak jste určili při deklaraci poskytnutého typu).

Přidejte do konstruktoru dokumentaci XML a přidejte poskytnutý konstruktor k poskytnutému typu:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Vytvořte druhý poskytnutý konstruktor, který přijímá jeden parametr:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode`Pro konstruktor znovu vrátí uvozovku F #, která představuje kód, který kompilátor hostitele vygeneroval pro volání metody. Například můžete použít následující konstruktor:

```fsharp
new Type10("ten")
```

Instance poskytnutého typu se vytvoří se základními daty "deset". Je možné, že již jste si všimli, že `InvokeCode` funkce vrací citaci. Vstup této funkce je seznam výrazů, jeden pro každý parametr konstruktoru. V tomto případě je v nástroji k dispozici výraz, který představuje hodnotu jednoho parametru `args.[0]` . Kód pro volání konstruktoru převede návratovou hodnotu na vymazaný typ `obj` . Po přidání druhého poskytnutého konstruktoru do typu vytvoříte vlastnost poskytnuté instance:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Získání této vlastnosti vrátí délku řetězce, což je objekt reprezentace. `GetterCode`Vlastnost vrátí uvozovku jazyka F #, která určuje kód, který kompilátor hostitele vygeneruje, aby získal vlastnost. Například `InvokeCode` `GetterCode` funkce vrátí citát. Kompilátor hostitele volá tuto funkci se seznamem argumentů. V tomto případě argumenty obsahují pouze jeden výraz, který představuje instanci, na kterou je volána metoda getter, ke které můžete přistupovat pomocí `args.[0]` . Implementace potom se `GetterCode` do výsledné nabídky na vymazaném typu zaznamená `obj` a přetypování se používá k uspokojení mechanismu kompilátoru pro kontrolu typů, které jsou v objektu řetězce. Další část sady `makeOneProvidedType` poskytuje metodu instance s jedním parametrem.

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

Nakonec vytvořte vnořený typ, který obsahuje 100 vnořených vlastností. Vytváření tohoto vnořeného typu a jeho vlastností je zpožděné, tj. počítané na vyžádání.

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

### <a name="details-about-erased-provided-types"></a>Podrobnosti o vymazaných poskytnutých typech

Příklad v této části poskytuje pouze *smazány poskytnuté typy*, které jsou zvláště užitečné v následujících situacích:

- Při psaní poskytovatele pro informační prostor, který obsahuje pouze data a metody.

- Při psaní poskytovatele, kde je správná Sémantika typu za běhu není kritická pro praktické použití informačního prostoru.

- Při psaní poskytovatele pro informační prostor, který je tak velký a propojuje, že není technicky proveditelné generovat reálné typy .NET pro informační prostor.

V tomto příkladu je každý poskytnutý typ smazán na typ `obj` a všechna použití tohoto typu se zobrazí jako typ `obj` v kompilovaném kódu. Základní objekty v těchto příkladech jsou ve skutečnosti řetězce, ale typ se zobrazí jako `System.Object` v kompilovaném kódu .NET. Stejně jako u všech použití typu vymazání lze použít explicitní zabalení, rozbalení a přetypování k převedení smazáných typů. V takovém případě výjimka přetypování, která není platná, může být výsledkem použití objektu. Modul runtime zprostředkovatele může definovat svůj vlastní typ soukromé reprezentace, který bude pomáhat chránit před falešnými reprezentacemi. V samotném jazyce F # nelze definovat smazáné typy. Vymazat lze pouze poskytnuté typy. Je nutné porozumět vlivům, které jsou praktické i sémantické, pro použití buď vymazaných typů pro poskytovatele typu, nebo poskytovatele, který poskytuje vymazatelné typy. Vymazaný typ nemá žádný skutečný typ .NET. Proto nemůžete provést přesnou reflexi pro daný typ a můžete převádět vymazané typy, pokud používáte přetypování za běhu a další techniky, které spoléhají na přesnou sémantiku typu modulu runtime. Podverze vymazaných typů často vede k výjimkám přetypování typů za běhu.

### <a name="choosing-representations-for-erased-provided-types"></a>Volba reprezentace pro vymazané poskytnuté typy

Pro některá použití vymazaných poskytnutých typů není žádná reprezentace nutná. Například vymazaný poskytnutý typ může obsahovat pouze statické vlastnosti a členy a žádné konstruktory a žádné metody nebo vlastnosti by nevracely instanci typu. Pokud máte přístup k instancím vymazaného poskytnutého typu, je třeba vzít v úvahu následující otázky:

**Jaký je vymazání poskytnutého typu?**

- Vymazání poskytnutého typu je způsob, jakým se typ objevuje v kompilovaném kódu .NET.

- Vymazání poskytnutého typu vymazání třídy je vždy prvním nesmazáným základním typem v řetězci dědičnosti daného typu.

- Mazání zadaného typu mazání vymazaného rozhraní je vždy `System.Object` .

**Jaké jsou reprezentace poskytnutého typu?**

- Sada možných objektů pro vymazaný poskytnutý typ se nazývá reprezentace. V příkladu v tomto dokumentu jsou reprezentace všech vymazaných poskytnutých typů `Type1..Type100` vždy řetězcové objekty.

Všechny reprezentace poskytnutého typu musí být kompatibilní s vymazáním poskytnutého typu. (Jinak buď kompilátor F # poskytne chybu pro použití poskytovatele typu, nebo neověřený kód .NET, který není platný, bude vygenerován. Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)

Můžete zvolit reprezentace pro poskytnuté objekty pomocí některého z následujících přístupů, z nichž obě jsou velmi běžné:

- Pokud jednoduše poskytujete obálku silného typu přes existující typ rozhraní .NET, často to dává smysl pro typ, který se má na tento typ vymazat, použít instance daného typu jako reprezentace nebo obojí. Tento přístup je vhodný v případě, že většina existujících metod tohoto typu stále dává smysl při použití silně typované verze.

- Pokud chcete vytvořit rozhraní API, které se významně liší od jakékoli existující rozhraní .NET API, má smysl vytvořit běhové typy, které budou typem vymazání a reprezentace pro poskytnuté typy.

Příklad v tomto dokumentu používá jako reprezentace poskytovaných objektů řetězce. Často může být vhodné použít pro reprezentace jiné objekty. Jako kontejner objektů a dat můžete například použít slovník:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Alternativně můžete definovat typ v poskytovateli typu, který bude použit za běhu za účelem vytvoření reprezentace, společně s jednou nebo více běhovými operacemi:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Dodané členy pak mohou vytvořit instance tohoto typu objektu:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

V takovém případě můžete (volitelně) použít tento typ jako typ mazání zadáním tohoto typu jako `baseType` při sestavování `ProvidedTypeDefinition` :

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Nejdůležitější lekce

Předchozí část vysvětluje, jak vytvořit jednoduchý poskytovatel typu mazání, který poskytuje rozsah typů, vlastností a metod. Tato část také vysvětluje koncept typu vymazání, včetně některých výhod a nevýhod poskytování vymazaných typů od poskytovatele typu a popisuje reprezentace vymazaných typů.

## <a name="a-type-provider-that-uses-static-parameters"></a>Zprostředkovatel typu, který používá statické parametry

Možnost parametrizovat zprostředkovatele typů pomocí statických dat umožňuje mnoho zajímavých scénářů, i když zprostředkovatel nepotřebuje přístup k místním nebo vzdáleným datům. V této části se seznámíte s některými základními postupy pro dohromady tohoto poskytovatele.

### <a name="type-checked-regex-provider"></a>Typ kontrolovaného regulárního výrazu

Představte si, že chcete implementovat poskytovatele typu pro regulární výrazy, které zabalí <xref:System.Text.RegularExpressions.Regex> knihovny .NET v rozhraní, které poskytuje následující záruky při kompilaci:

- Ověřuje se, jestli je regulární výraz platný.

- Poskytování pojmenovaných vlastností na shodách, které jsou založeny na libovolných názvech skupin v regulárním výrazu.

V této části se dozvíte, jak použít poskytovatele typů k vytvoření `RegexTyped` typu, který parameterizes vzor regulárního výrazu k poskytnutí těchto výhod. Kompilátor ohlásí chybu, pokud zadaný vzor není platný a poskytovatel typu může extrahovat skupiny ze vzoru, abyste k nim měli přístup pomocí pojmenovaných vlastností na shodách. Při návrhu poskytovatele typu byste měli vzít v úvahu, jak by jeho vystavené rozhraní API mělo vypadat koncovým uživatelům a jak se tento návrh převede na kód .NET. Následující příklad ukazuje, jak použít takové rozhraní API k získání komponent kódu oblasti:

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

- Standardní typ regulárního výrazu představuje parametrizovaný `RegexTyped` typ.

- `RegexTyped`Konstruktor má za následek volání konstruktoru regulárního výrazu, který předává argument statického typu pro daný vzor.

- Výsledky `Match` metody jsou reprezentovány standardním <xref:System.Text.RegularExpressions.Match> typem.

- Každá pojmenovaná skupina má za následek zadanou vlastnost a přístup k ní má za následek použití indexeru v `Groups` kolekci shody.

Následující kód je základem logiky pro implementaci takového poskytovatele a tento příklad vynechává přidání všech členů k poskytnutému typu. Informace o jednotlivých přidaných členech naleznete v příslušné části dále v tomto tématu. Pro úplný kód stáhněte ukázku z [ukázkového balíčku F # 3,0](https://archive.codeplex.com/?p=fsharp3sample) na webu CodePlex.

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

- Poskytovatel typu používá dva statické parametry: `pattern` , který je povinný a `options` , které jsou volitelné (protože je k dispozici výchozí hodnota).

- Po zadání statických argumentů vytvoříte instanci regulárního výrazu. Tato instance vyvolá výjimku, pokud je regulární výraz poškozen a tato chyba bude hlášena uživatelům.

- V rámci `DefineStaticParameters` zpětného volání definujete typ, který bude vrácen po zadání argumentů.

- Tento kód `HideObjectMethods` je nastaven na hodnotu true, aby prostředí IntelliSense zůstalo zjednodušené. Tento atribut způsobí `Equals` , že `GetHashCode` Členové,, a jsou `Finalize` `GetType` potlačeny ze seznamů IntelliSense pro zadaný objekt.

- Použijete `obj` jako základní typ metody, ale použijete `Regex` objekt jako běhovou reprezentaci tohoto typu, jak ukazuje následující příklad.

- Volání `Regex` konstruktoru vyvolá výjimku, <xref:System.ArgumentException> Pokud regulární výraz není platný. Kompilátor zachytí tuto výjimku a oznámí uživateli chybovou zprávu v době kompilace nebo v editoru sady Visual Studio. Tato výjimka umožňuje ověřovat regulární výrazy bez spuštění aplikace.

Výše definovaný typ ještě není užitečný, protože neobsahuje žádné smysluplné metody nebo vlastnosti. Nejdřív přidejte statickou `IsMatch` metodu:

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

Předchozí kód definuje metodu `IsMatch` , která přebírá řetězec jako vstup a vrací `bool` . Jediná část štychu je použití `args` argumentu v rámci `InvokeCode` definice. V tomto příkladu `args` je seznam nabídek, které představují argumenty této metody. Pokud je metoda metodou instance, představuje první argument `this` argument. Nicméně pro statickou metodu jsou argumenty pouze explicitní argumenty metody. Všimněte si, že typ hodnoty v uvozovkách by měl odpovídat zadanému návratový typ (v tomto případě `bool` ). Všimněte si také, že tento kód používá metodu k ujištění, `AddXmlDoc` že poskytnutá metoda má také užitečnou dokumentaci, kterou lze dodávat prostřednictvím technologie IntelliSense.

Dále přidejte metodu shody instance. Tato metoda však by měla vracet hodnotu poskytnutého `Match` typu tak, aby k nim bylo možné získat pøístup v silně typovaném způsobem. Proto je třeba nejprve deklarovat `Match` typ. Vzhledem k tomu, že tento typ závisí na vzoru, který byl zadán jako statický argument, tento typ musí být vnořen v rámci definice parametrizovaného typu:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Pak pro každou skupinu přidejte jednu vlastnost k typu shody. V době běhu je shoda vyjádřena jako <xref:System.Text.RegularExpressions.Match> hodnota, takže citace, která definuje vlastnost, musí použít <xref:System.Text.RegularExpressions.Match.Groups> indexovanou vlastnost k získání příslušné skupiny.

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

Znovu si všimněte, že přidáváte dokumentaci XML do poskytnuté vlastnosti. Všimněte si také, že vlastnost může být přečtena `GetterCode` , pokud je k dispozici funkce a vlastnost může být zapsána `SetterCode` , pokud je k dispozici funkce, takže výsledná vlastnost je určena pouze pro čtení.

Nyní můžete vytvořit metodu instance, která vrací hodnotu tohoto `Match` typu:

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

Vzhledem k tomu, že vytváříte metodu instance, `args.[0]` představuje `RegexTyped` instanci, na které je metoda volána, a `args.[1]` je vstupním argumentem.

Nakonec poskytněte konstruktor, aby bylo možné vytvořit instance poskytnutého typu.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Konstruktor se pouze vymaže pro vytvoření standardní instance jazyka .NET, která je opět zabalena do objektu, protože `obj` je vymazání poskytnutého typu. V důsledku této změny funguje ukázkové použití rozhraní API, které je uvedené dříve v tématu, funguje podle očekávání. Následující kód je kompletní a konečný:

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

### <a name="key-lessons"></a>Nejdůležitější lekce

Tato část vysvětluje, jak vytvořit poskytovatele typu, který pracuje na jeho statických parametrech. Poskytovatel kontroluje statický parametr a poskytuje operace na základě jeho hodnoty.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Poskytovatel typu, který je zálohovaný místními daty

Často můžete chtít, aby poskytovatelé typů mohli prezentovat rozhraní API, a to na základě nejen statických parametrů, ale také informací z místních nebo vzdálených systémů. Tato část pojednává o poskytovatelích typů, které jsou založeny na místních datech, například v místních datových souborech.

### <a name="simple-csv-file-provider"></a>Jednoduchý poskytovatel souborů CSV

Jednoduchým příkladem je zvážit poskytovatele typu pro přístup k vědeckým datům ve formátu CSV (čárkami oddělených hodnot). V této části se předpokládá, že soubory CSV obsahují řádek záhlaví následovaný daty s plovoucí desetinnou čárkou, jak ukazuje následující tabulka:

|Vzdálenost (měřič)|Čas (sekundy)|
|----------------|-------------|
|50,0|3.7|
|100,0|5,2|
|150,0|6.4|

V této části se dozvíte, jak poskytnout typ, který lze použít k získání řádků s `Distance` vlastností typu `float<meter>` a `Time` vlastností typu `float<second>` . Pro zjednodušení jsou provedeny následující předpoklady:

- Názvy hlaviček jsou buď menší než jednotka, nebo mají formát "název (jednotka)" a neobsahují čárky.

- Jednotky jsou všechny jednotky systému, které jsou mezinárodní (SI), jako modul [Microsoft. FSharp. data. UnitSystems. si. UnitNames Module (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) , který definuje.

- Jednotky jsou všechny jednoduché (například měřič), nikoli složené (například měřič za sekundu).

- Všechny sloupce obsahují data s plovoucí desetinnou čárkou.

Doplněný poskytovatel by tato omezení vyvolal.

V prvním kroku se můžete podívat, jak by mělo rozhraní API vypadat. Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

V tomto případě by měl kompilátor převést tato volání na něco podobného jako v následujícím příkladu:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

Optimální překlad bude vyžadovat poskytovatele typu k definování reálného `CsvFile` typu v sestavení poskytovatele typu. Poskytovatelé typů často spoléhají na několik pomocných typů a metod pro zabalení důležité logiky. Vzhledem k tomu, že měření se vymažou za běhu, můžete `float[]` pro řádek použít jako vymazaný typ. Kompilátor bude zacházet s různými sloupci s různými typy měr. Například první sloupec v našem příkladu má typ `float<meter>` a druhý má `float<second>` . Smazáná reprezentace ale může zůstat poměrně jednoduchá.

Následující kód ukazuje základní implementaci.

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

Všimněte si následujících bodů implementace:

- Přetížené konstruktory umožňují načíst buď původní soubor, nebo jeden, který má stejné schéma. Tento model je běžný při psaní poskytovatele typu pro místní nebo vzdálené zdroje dat. Tento model umožňuje použít jako šablonu pro vzdálená data místní soubor.

- Můžete použít hodnotu [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) , která je předána konstruktoru poskytovatele typu k překladu relativních názvů souborů.

- Můžete použít `AddDefinitionLocation` metodu k definování umístění poskytovaných vlastností. Proto pokud použijete `Go To Definition` na poskytnutou vlastnost, soubor CSV se otevře v aplikaci Visual Studio.

- Typ můžete použít `ProvidedMeasureBuilder` k vyhledání jednotek si a k vygenerování relevantních `float<_>` typů.

### <a name="key-lessons"></a>Nejdůležitější lekce

Tato část vysvětluje, jak vytvořit poskytovatele typu pro místní zdroj dat pomocí jednoduchého schématu, které je obsaženo v samotném zdroji dat.

## <a name="going-further"></a>Dál

Následující části obsahují návrhy pro další studii.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Podívejte se na zkompilovaný kód pro vymazané typy.

Chcete-li poskytnout určitou představu o tom, jak použití poskytovatele typu odpovídá kódu, který je generován, podívejte se na následující funkci pomocí `HelloWorldTypeProvider` , kterou jste použili dříve v tomto tématu.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Tady je obrázek výsledného kódu, který se dekompiluje pomocí programu Ildasm. exe:

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

Jak ukazuje příklad, všechny zmínky o typu `Type1` a `InstanceProperty` vlastnost byly smazány, přičemž se zabývají pouze operace s typy modulu runtime.

### <a name="design-and-naming-conventions-for-type-providers"></a>Návrhy a zásady vytváření názvů pro poskytovatele typů

Při vytváření poskytovatelů typů Sledujte následující konvence.

**Poskytovatelé protokolů připojení** Obecně platí, že názvy většiny knihoven DLL pro protokoly připojení dat a služeb, jako jsou například připojení OData nebo SQL, by měly končit `TypeProvider` nebo `TypeProviders` . Například použijte název knihovny DLL, který se podobá následujícímu řetězci:

`Fabrikam.Management.BasicTypeProviders.dll`

Zajistěte, aby poskytnuté typy byly členy odpovídajícího oboru názvů, a označte protokol připojení, který jste implementovali:

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Poskytovatelé nástrojů pro obecné kódování**.  Pro poskytovatele typu nástrojů, jako je například pro regulární výrazy, může být poskytovatel typu součástí základní knihovny, jak ukazuje následující příklad:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

V tomto případě se poskytnutý typ zobrazí v odpovídajícím bodě podle normálních konvencí pro návrh .NET:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Nejednoznačné zdroje dat**. Někteří poskytovatelé typů se připojují k jednomu vyhrazenému zdroji dat a poskytují pouze data. V takovém případě byste měli vyřadit `TypeProvider` příponu a používat normální konvence pro pojmenování .NET:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Další informace najdete v tématu `GetConnection` konvence návrhu, která je popsána dále v tomto tématu.

### <a name="design-patterns-for-type-providers"></a>Vzory návrhu pro poskytovatele typů

Následující části popisují vzory návrhu, které můžete použít při vytváření poskytovatelů typů.

#### <a name="the-getconnection-design-pattern"></a>Vzor návrhu GetConnection

Většina poskytovatelů typů by měla být napsána tak, aby používala `GetConnection` vzor, který používají poskytovatelé typů v FSharp. data. TypeProviders. dll, jak ukazuje následující příklad:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Poskytovatelé typů zálohovaných vzdálenými daty a službami

Předtím, než vytvoříte poskytovatele typu, který je zajištěný pomocí vzdálených dat a služeb, je třeba vzít v úvahu řadu problémů, které jsou součástí připojeného programování. Mezi tyto problémy patří následující aspekty:

- mapování schématu

- živý a neplatnost v přítomnosti změny schématu

- ukládání schématu do mezipaměti

- asynchronní implementace operací přístupu k datům

- podpůrné dotazy, včetně dotazů LINQ

- přihlašovací údaje a ověřování

V tomto tématu se tyto problémy podrobněji nezobrazují.

### <a name="additional-authoring-techniques"></a>Další techniky vytváření obsahu

Při psaní vlastních zprostředkovatelů typů je vhodné použít následující další techniky.

### <a name="creating-types-and-members-on-demand"></a>Vytváření typů a členů na vyžádání

Rozhraní ProvidedType API má opožděné verze AddMember.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Tyto verze slouží k vytvoření prostorů typu na vyžádání.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Poskytování typů polí a vytváření instancí obecných typů

Zadali jste členy (jejichž signatury zahrnují typy polí, typy ByRef a instance obecných typů) pomocí normálního typu `MakeArrayType` , `MakePointerType` , a `MakeGenericType` na všech instancích <xref:System.Type> , včetně `ProvidedTypeDefinitions` .

> [!NOTE]
> V některých případech může být nutné použít pomocníka v nástroji `ProvidedTypeBuilder.MakeGenericType` .  Další podrobnosti najdete v [dokumentaci k sadě SDK pro poskytovatele typů](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) .

### <a name="providing-unit-of-measure-annotations"></a>Poskytování poznámek k měrné jednotce

Rozhraní ProvidedTypes API poskytuje nápovědu pro poskytování poznámek k měření. Chcete-li například poskytnout typ `float<kg>` , použijte následující kód:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Chcete-li zadat typ `Nullable<decimal<kg/m^2>>` , použijte následující kód:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Přístup k místním prostředkům na úrovni projektu nebo na skript

Každé instanci poskytovatele typu lze předávat `TypeProviderConfig` hodnotu během konstrukce. Tato hodnota obsahuje "složku řešení" pro poskytovatele (to znamená složku projektu pro kompilaci nebo adresář, který obsahuje skript), seznam odkazovaných sestavení a další informace.

### <a name="invalidation"></a>Zneplatnění

Poskytovatelé můžou vyvolávat neplatné signály, které upozorňují na službu jazyka F #, že se předpoklady schématu změnily. Pokud dojde k neplatnosti, typecheck se provede, pokud je poskytovatel hostován v aplikaci Visual Studio. Tento signál bude ignorován, pokud je poskytovatel hostován v F# Interactive nebo kompilátorem jazyka F # (FSC. exe).

### <a name="caching-schema-information"></a>Ukládání informací o schématu do mezipaměti

Poskytovatelé musí často přistupovat k informacím o schématu v mezipaměti. Data uložená v mezipaměti by se měla ukládat pomocí názvu souboru, který je zadaný jako statický parametr nebo jako uživatelská data. Příkladem ukládání schématu do mezipaměti je `LocalSchemaFile` parametr zprostředkovatelů typů v `FSharp.Data.TypeProviders` sestavení. V rámci implementace těchto zprostředkovatelů tento statický parametr přesměrovává poskytovatele typu na použití informací o schématu v zadaném místním souboru místo přístupu ke zdroji dat přes síť. Chcete-li použít informace o schématu uložené v mezipaměti, je nutné také nastavit statický parametr `ForceUpdate` na `false` . Podobnou techniku můžete použít k povolení přístupu k online a offline datům.

### <a name="backing-assembly"></a>Záložní sestavení

Při kompilaci `.dll` `.exe` souboru nebo je soubor back. dll pro vygenerované typy staticky propojen do výsledného sestavení. Tento odkaz je vytvořen zkopírováním definic typu Intermediate Language (IL) a všech spravovaných prostředků ze záložního sestavení do konečného sestavení. Když použijete F# Interactive, soubor back. dll se nezkopíruje a místo toho se načte přímo do procesu F# Interactive.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Výjimky a diagnostika od zprostředkovatelů typů

Všechna použití všech členů ze zadaných typů mohou vyvolat výjimky. Ve všech případech, pokud poskytovatel typu vyvolá výjimku, kompilátor hostitele zavolá chybu na konkrétního poskytovatele typu.

- Výjimky poskytovatele typu by nikdy neměly vést k vnitřním chybám kompilátoru.

- Zprostředkovatelé typů nemůžou oznamovat upozornění.

- Když je poskytovatel typu hostován v kompilátoru F #, ve vývojovém prostředí F # nebo F# Interactive, jsou zachyceny všechny výjimky od tohoto poskytovatele. Vlastnost Message je vždycky text chyby a nezobrazí se žádné trasování zásobníku. Pokud budete vyvolávat výjimku, můžete vyvolat následující příklady: `System.NotSupportedException` , `System.IO.IOException` , `System.Exception` .

#### <a name="providing-generated-types"></a>Poskytování generovaných typů

V tomto dokumentu se zatím vyvolalo, jak poskytnout vymazatelné typy. Můžete také použít mechanismus poskytovatele typu v jazyce F # k poskytnutí generovaných typů, které jsou přidány jako reálné definice typu .NET do programu uživatelé. Musíte odkazovat na generované poskytnuté typy pomocí definice typu.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Pomocný kód ProvidedTypes-0,2, který je součástí verze F # 3,0, má pouze omezené podpory pro poskytování generovaných typů. Následující příkazy musí být pro definici generovaného typu pravdivé:

- `isErased`musí být nastaven na hodnotu `false` .

- Vygenerovaný typ musí být přidán do nově vytvořeného typu `ProvidedAssembly()` , který představuje kontejner pro vygenerované fragmenty kódu.

- Poskytovatel musí mít sestavení, které má aktuální soubor .NET. dll s odpovídajícím souborem. dll na disku.

## <a name="rules-and-limitations"></a>Pravidla a omezení

Při psaní poskytovatelů typů mějte na paměti následující pravidla a omezení.

### <a name="provided-types-must-be-reachable"></a>Poskytnuté typy musí být dosažitelné.

Všechny poskytnuté typy by měly být dosažitelné z nevnořených typů. Nevnořené typy jsou uvedeny ve volání `TypeProviderForNamespaces` konstruktoru nebo volání metody `AddNamespace` . Například pokud poskytovatel poskytuje typ `StaticClass.P : T` , je nutné zajistit, že T je buď nevnořený typ, nebo je vnořen do jednoho.

Někteří poskytovatelé mají například statickou třídu `DataTypes` , například obsahující tyto `T1, T2, T3, ...` typy. V opačném případě chyba říká, že byl nalezen odkaz na typ T v sestavení A, ale tento typ se v tomto sestavení nenašel. Pokud se zobrazí tato chyba, ověřte, zda jsou všechny podtypy dostupné z typů poskytovatele. Poznámka: tyto `T1, T2, T3...` typy jsou označovány jako *průběžné* typy. Nezapomeňte je umístit do přístupného oboru názvů nebo nadřazeného typu.

### <a name="limitations-of-the-type-provider-mechanism"></a>Omezení mechanismu poskytovatele typu

Mechanismus poskytovatele typu v jazyce F # má následující omezení:

- Základní infrastruktura pro poskytovatele typů v jazyce F # nepodporuje poskytnuté obecné typy ani poskytnuté obecné metody.

- Mechanismus nepodporuje vnořené typy se statickými parametry.

## <a name="development-tips"></a>Tipy pro vývoj

Následující tipy mohou být užitečné během procesu vývoje:

### <a name="run-two-instances-of-visual-studio"></a>Spuštění dvou instancí sady Visual Studio

Můžete vyvíjet poskytovatele typu v jedné instanci a otestovat poskytovatele v druhé, protože testovací prostředí IDE povede zámek na soubor. dll, který brání opětovnému sestavení poskytovatele typu. Proto je nutné zavřít druhou instanci sady Visual Studio, když je poskytovatel sestaven v první instanci a poté po sestavení poskytovatele znovu otevřít druhou instanci.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Poskytovatelé typu ladění pomocí volání FSC. exe

Zprostředkovatele typů můžete vyvolat pomocí následujících nástrojů:

- FSC. exe (kompilátor příkazového řádku jazyka F #)

- FSI. exe (kompilátor F# Interactive)

- devenv. exe (Visual Studio)

Můžete často ladit poskytovatele typu, a to pomocí FSC. exe v souboru testovacího skriptu (například Script. FSX). Ladicí program můžete spustit z příkazového řádku.

```console
devenv /debugexe fsc.exe script.fsx
```

  Můžete použít protokolování pro tisk do STDOUT.

## <a name="see-also"></a>Viz také

- [Zprostředkovatelé typů](index.md)
- [Sada SDK typu zprostředkovatele](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
