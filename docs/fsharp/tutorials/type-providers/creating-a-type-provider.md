---
title: "Tutoriál: Vytvoření zprostředkovatele typů (F#)"
description: "Naučte se vytvářet vlastní F # – zprostředkovatelé typů v F # 3.0 prověřením několik poskytovatelů jednoduchý typ pro ilustraci se základními koncepty."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: 58003c88baf0f8aeea1a511334b99bd0295f8bf1
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="tutorial-creating-a-type-provider"></a>Kurz: Vytvoření zprostředkovatele typů

> [!NOTE]
Tento průvodce byl vytvořen pro F # 3.0 a budou aktualizovány.

Typ zprostředkovatele mechanismus v F # 3.0 je významnou část podporuje programování bohaté informace. Tento kurz vysvětluje, jak vytvořit vlastní typ zprostředkovatele jste s návodem vývoj několik poskytovatelů jednoduchý typ pro ilustraci se základními koncepty. Další informace o typu poskytovatele mechanismus v F # najdete v tématu [zprostředkovatelů typů](index.md).

F # 3.0 obsahuje několik předdefinovaných typ zprostředkovatele pro běžně používané Internet a enterprise dat služby. Tyto zprostředkovatele typu udělte přístup jednoduché a běžné relační databáze SQL a OData a WSDL služby založené na síti. Tito zprostředkovatelé také podporují použití dotazy LINQ F # pro tyto zdroje dat.

V případě potřeby můžete vytvořit vlastní typ zprostředkovatele nebo typ zprostředkovatele, ostatní vytvořené, můžete odkazovat. Vaše organizace může mít například služba data, která poskytuje velké a rostoucí počet sad dat s názvem, každou s vlastním schématem stabilní data. Můžete vytvořit typ zprostředkovatele, který čte schémata a zobrazí aktuální sady dat programátorů způsobem silného typu.


## <a name="before-you-start"></a>Než začnete
Tento typ poskytovatele mechanismus je primárně určený pro vložení stabilní data a informace prostory služby do programovací prostředí F #.

Tento mechanismus není určená pro vložení mezery informace jejichž schématu se změní při spuštění programu způsoby, které jsou relevantní pro logiku programu. Navíc tento mechanismus není určená pro intra jazyk meta-programování, i když tuto doménu obsahuje některé platné používá. Tento mechanismus byste měli použít pouze v případě potřeby a kde vývoj zprostředkovatele typů výsledkem velmi vysokou hodnotu.

Vyhněte se zápis typ zprostředkovatele, kde není k dispozici schéma. Podobně, neměli byste zápis zprostředkovatele typů, kde je běžný (nebo i existující) by stačit knihovny .NET.

Než začnete, může odpovědět na tyto otázky:


- Máte schéma pro zdroj informace? Pokud ano, co je mapování do F # a systém typů .NET?

- Můžete použít existující API (dynamicky zadávaných) jako výchozí bod týkající se vaší implementace?

- Bude vám a vaší organizaci mít dostatek používá typ zprostředkovatele, který má smysl zkontrolujte jejich zápisu? Běžné knihovny .NET by vyhovovala vašim potřebám?

- Kolik změní schéma?

- Se změní při kódování?

- Se změní mezi kódování relace?

- Se změní při spuštění programu?

Zprostředkovatelé typů jsou nejvhodnější pro situacích, kde je stabilní za běhu a po dobu životnosti zkompilovaný kód schématu.


## <a name="a-simple-type-provider"></a>Jednoduchý typ zprostředkovatele
Tato ukázka je Samples.HelloWorldTypeProvider v `SampleProviders\Providers` adresář [F # 3.0 ukázka Pack](http://fsharp3sample.codeplex.com) na webu Codeplex. Zprostředkovatel zpřístupní "typ prostor", který obsahuje 100 vymazaných typů, jak ukazuje následující kód pomocí syntaxe podpis F # a vynechat podrobnosti pro všechny kromě `Type1`. Další informace o typech vymazaných najdete v tématu [podrobnosti o vymazat zadané typy](#details-about-erased-provided-types) dál v tomto tématu.

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

    /// This is an instance property.
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

Všimněte si, že se staticky označuje sadu typy a členy zadané. V tomto příkladu není využít možnost zprostředkovatelů zadejte typy, které jsou závislé na schéma. Implementace zprostředkovatele typu popsané v následujícím kódu a podrobnosti jsou popsané v dalších částech tohoto tématu.


>[!WARNING] 
Může mít některé malé pojmenování rozdíly mezi tento kód a online ukázky.

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open Samples.FSharp.ProvidedTypes
open Microsoft.FSharp.Core.CompilerServices
open Microsoft.FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces()

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

Pro tohoto zprostředkovatele použijte otevřete samostatnou instanci sady Visual Studio 2012, vytvořit skript F # a potom přidejte odkaz na poskytovateli z vašeho skriptu pomocí #r jako následující kód:

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

Poté vyhledejte typy v části `Samples.HelloWorldTypeProvider` obor názvů, který generuje typ poskytovatele.

Než můžete znovu zkompiluje zprostředkovatele, ujistěte se, uzavřít všechny instance Visual Studio a F # interaktivní, které používají zprostředkovatele knihovny DLL. Chyby sestavení, jinak hodnota dojde, protože zamkne výstupní knihovnu DLL.

Chcete-li ladit tento zprostředkovatel pomocí tiskové příkazy, zkontrolujte skript, který zveřejňuje potížím s poskytovatelem a pak použijte následující kód:

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Chcete-li ladit tento zprostředkovatel pomocí sady Visual Studio, otevřete příkazový řádek sady Visual Studio s přihlašovacími údaji správce a spusťte následující příkaz:

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Jako alternativu, otevřete Visual Studio, otevřete nabídku ladění, zvolte `Debug/Attach to process…`a připojte k jiné `devenv` procesu, kde provádíte změny vašeho skriptu. Pomocí této metody můžete snadno vybrat konkrétní logiku ve zprostředkovateli typu interaktivně zadáním výrazy do druhé instance (s plnou technologie IntelliSense a další funkce).

Pouze můj kód ladění lépe identifikovat chyby v generovaného kódu můžete zakázat. Informace o tom, jak povolit nebo zakázat tuto funkci najdete v tématu [procházení kódu s ladicím programem](/visualstudio/debugger/navigating-through-code-with-the-debugger). Navíc můžete také nastavit první odpovídající výjimce zachytávání otevřením `Debug` nabídky a pak vyberete `Exceptions` nebo výběrem klávesy Ctrl + Alt + E otevřete `Exceptions` dialogové okno. V tomto dialogu pod `Common Language Runtime Exceptions`, vyberte `Thrown` zaškrtávací políčko.


### <a name="implementation-of-the-type-provider"></a>Implementace zprostředkovatele typu
Tato část vás provede procesem na hlavní části implementace typ zprostředkovatele. Nejprve definovat typ pro vlastní typ zprostředkovatele sám sebe:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Tento typ musí být veřejné a označte ji s [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) tak, aby kompilátor rozpozná typ zprostředkovatele, když samostatného projektu F # odkazuje na sestavení, které obsahuje typ atributu. *Konfigurace* parametr je volitelný a pokud existuje, obsahuje kontextové konfigurační informace pro instanci zprostředkovatele typu, která vytvoří kompilátor jazyka F #.

V dalším kroku implementujete [itypeprovider –](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) rozhraní. V takovém případě použijete `TypeProviderForNamespaces` typu z `ProvidedTypes` rozhraní API jako základní typ. Tento typ pomocné rutiny můžete poskytnout soubor konečné například zadaný obory názvů, z nichž každý přímo obsahuje omezený počet pevné, například zadané typy. V tomto kontextu zprostředkovatele *například* generuje typy, i když nejsou potřeba nebo použít.

```fsharp
inherit TypeProviderForNamespaces()
```

V dalším kroku definovat místní privátní hodnoty, které určují obor názvů pro zadané typy a najít sestavení zprostředkovatele typu sám sebe. Toto sestavení se později používá jako logické nadřazený typ vymazaných typů, které jsou k dispozici.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Dál vytvořte funkci zajistit každý typ Type1... Type100. Tato funkce je podrobně popsány dále v tomto tématu.

```fsharp
let makeOneProvidedType (n:int) = …
```

Dále generovat 100 zadané typy:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

V dalším kroku přidejte typy jako zadaný obor názvů:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Nakonec přidejte atribut sestavení, který označuje, že vytváříte zprostředkovatele typů knihovny DLL:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>Poskytuje jeden typ a její členy
`makeOneProvidedType` Funkce neodpovídá skutečné pracovní poskytnout jeden z typů.

```fsharp
let makeOneProvidedType (n:int) = 
…
```

Tento krok popisuje implementace této funkce. Nejprve vytvořte zadaný typ (například Type1, když n = 1, nebo Type57, když n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly,namespaceName,
"Type" + string n,
baseType = Some typeof<obj>)
```

Nezapomeňte přitom následující body:


- To, pokud je typ vymazat.  Protože jste označení, že je základní typ `obj`, instancí se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v zkompilovaný kód.
<br />

- Když zadáte typu-nested, musíte zadat sestavení a oboru názvů. Pro vymazaných typy sestavení by měla být sestavení zprostředkovatele typu sám sebe.
<br />

Dál přidejte dokumentace XML typu. Tato dokumentace je zpožděno, to znamená, počítaný na vyžádání, pokud se vyžaduje kompilátor hostitele.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Dále přidejte zadané statické vlastnosti typu:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ "Hello!" @@>))
```

Získání této vlastnosti bude vždy vyhodnocena jako text "Hello!". `GetterCode` Pro vlastnost používá F # uvozovky, která představuje kód, který kompilátoru hostitele generuje pro získání vlastnosti. Další informace o uvozovky najdete v tématu [uvozovky kódu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

Přidejte dokumentace XML pro vlastnost.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Zadaná vlastnost nyní připojte zadaného typu. Zadaný člen musíte přiřadit pouze jeden typ. V opačném člen nikdy budou přístupné.

```fsharp
t.AddMember staticProp
```

Teď vytvořte zadaný konstruktoru, které nepřijímá žádné parametry.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
InvokeCode= (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode` Pro konstruktor vrátí F # uvozovky, která představuje kód, který kompilátoru hostitele generuje při volání konstruktoru. Například můžete použít následující konstruktor:

```fsharp
new Type10()
```

Instanci zadaného typu se vytvoří základní daty "Data objektu". Uvozovkách kód obsahuje převod na [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) vzhledem k tomu, že je tento typ vymazání to zadaný typ (jaký jste uvedli, když deklarovat zadaného typu).

Přidejte dokumentace XML pro konstruktor a přidejte zadaný konstruktor na zadaný typ:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Vytvořte druhý zadaný konstruktor, který přijímá jeden parametr:

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
InvokeCode= (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode` Pro konstruktor znovu vrátí F # uvozovky, která představuje kód, který kompilátoru hostitele generuje pro volání metody. Například můžete použít následující konstruktor:

```fsharp
new Type10("ten")
```

Pomocí zadaných dat "10" se vytvoří instanci zadaného typu. Může mít už k tomu, který `InvokeCode` funkce vrátí uvozovek. Vstup pro tuto funkci je seznam výrazů, jeden pro každý parametr konstruktoru. V takovém případě je k dispozici v výraz, který představuje hodnotu jeden parametr `args.[0]`. Kód pro volání konstruktoru převede návratovou hodnotu vymazaných typu `obj`. Po přidání druhého zadaný konstruktor typu, můžete vytvořit zadanou instanci vlastnost:

```fsharp
let instanceProp = 
ProvidedProperty(propertyName = "InstanceProperty", 
propertyType = typeof<int>, 
GetterCode= (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Získávání tato vlastnost vrátí délku řetězce, který je objekt reprezentace. `GetterCode` Vlastnost vrací uvozovek F #, která určuje kód, který generuje kompilátoru hostitele GET pro vlastnost. Jako `InvokeCode`, `GetterCode` funkce vrátí uvozovek. Kompilátor hostitele volání této funkce se seznamem argumentů. V takovém případě argumenty, které zahrnují jenom jeden výraz, který představuje instanci, na kterém je volána metoda getter, kterým můžete přistupovat pomocí `args.[0]`. Implementace `GetterCode` pak splices do uvozovek výsledek vymazaných typu `obj`, a pro uspokojení kompilátoru mechanismus pro kontrolu typy, že objekt je řetězec se používá přetypování. V další části `makeOneProvidedType` poskytuje metodu instance jeden parametr.

```fsharp
let instanceMeth = 
ProvidedMethod(methodName = "InstanceMethod", 
parameters = [ProvidedParameter("x",typeof<int>)], 
returnType = typeof<char>, 
InvokeCode = (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

Nakonec vytvořte vnořené typu, který obsahuje 100 vnořené vlastnosti. Vnořené vytvoření tohoto typu a jeho vlastnosti je zpožděno, to znamená, počítaný na vyžádání.

```fsharp
t.AddMembersDelayed(fun () -> 
let nestedType = ProvidedTypeDefinition("NestedType",
Some typeof<obj>

)

nestedType.AddMembersDelayed (fun () -> 
let staticPropsInNestedType = 
[ for i in 1 .. 100 do
let valueOfTheProperty = "I am string "  + string i

let p = ProvidedProperty(propertyName = "StaticProperty" + string i, 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ valueOfTheProperty @@>))

p.AddXmlDocDelayed(fun () -> 
sprintf "This is StaticProperty%d on NestedType" i)

yield p ]
staticPropsInNestedType)

[nestedType])

// The result of makeOneProvidedType is the type.
t
```

### <a name="details-about-erased-provided-types"></a>Podrobnosti o vymazaných zadané typy
Příklad v této části se poskytuje pouze *vymazat zadané typy*, které jsou obzvláště užitečná v následujících situacích:


- Když píšete zprostředkovatele pro informace prostor, který obsahuje pouze data a metody.
<br />

- Když píšete poskytovatele, kde nejsou důležité pro praktické využití místa na informace sémantiku přesné runtime-type.
<br />

- Když píšete zprostředkovatele pro informace prostor, který je tak velký a vzájemně propojena, že není technicky možné vygenerovat skutečné typů .NET pro prostor informace.
<br />

V tomto příkladu každý zadaný typ vymazáním na typ `obj`, a všechny používá typu se zobrazí jako typ `obj` v zkompilovaný kód. Ve skutečnosti objekty v těchto příkladech jsou řetězce, ale typ se zobrazí jako `System.Object` v rozhraní .NET zkompilovaný kód. I s všechna použití typ vymazání, můžete použít explicitní zabalení, rozbalení a přetypování k podkopat vymazat typy. Výjimky pro přetypování, který není platný v takovém případě může způsobit, když objekt se používá. Modul runtime zprostředkovatele můžete definovat vlastní typ privátní reprezentace k ochraně proti false reprezentace. Nelze definovat vymazaných typy v jazyku F # sám sebe. Pouze zadané typy může vymazat. Je potřeba pochopit následky, oba praktická a sémantické některou vymazat vymazaných typy pro váš typ zprostředkovatele nebo zprostředkovatele, který poskytuje typy. Typ vymazaných nemá skutečné typ rozhraní .NET. Proto nemůžete udělat přesný odraz přes typ a může podkopat vymazaných typy, pokud používáte přetypování runtime a další metody, které jsou závislé na Sémantika typu přesný runtime. Subversion vymazaných typů často výsledkem typ přetypování výjimky za běhu.


### <a name="choosing-representations-for-erased-provided-types"></a>Výběr reprezentace pro vymazat zadané typy
U některých používá vymazaných zadaný typů žádné reprezentace se vyžaduje. Například vymazaných zadaný typ může obsahovat pouze statické vlastnosti a členy a žádné konstruktory, a žádné metody nebo vlastnosti by vrátit instanci typu. Pokud se lze připojit vymazaných instancí zadaný typ, musíte zvážit následující otázky:


- Co je zadaný typ vymazání?
<br />
  - Vymazání poskytnutý typ je, jak zobrazuje typ v zkompilovaný kód .NET.
<br />

  - Vymazání typu zadaný vymazaných třídy je vždy první-vymazat základní typ v řetězu dědičnosti typu.
<br />

  - Vymazání typ zadaný vymazaných rozhraní je vždy `System.Object`.
<br />

- Jaké jsou reprezentace zadaného typu?
<br />
  - Sady možné objektů pro vymazaných zadaný typ se nazývají její reprezentace. V příkladu v tomto dokumentu reprezentace všech vymazaných zadané typy `Type1..Type100` jsou vždy řetězcových objektů.
<br />

Všechny reprezentace zadaného typu musí být kompatibilní s vymazání zadaného typu. (Jinak, kompilátor jazyka F # zobrazí chybu pro použití poskytovatele typu, nebo vygeneruje neověřitelný kód rozhraní .NET, který není platný. Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)

Pomocí některé z následujících dvou přístupů Oboje je velmi běžné si můžete vybrat reprezentaci pro zadané objekty:


- Pokud zadáváte jednoduše silného typu obálku přes existující typ rozhraní .NET, často má smysl pro typ vašeho chcete vymazat tento typ, použijte instance tohoto typu jako reprezentace nebo obojí. Tento přístup je vhodné, když většina stávajících metod daný typ stále mít smysl, pokud používáte verzi silného.
<br />

- Pokud chcete vytvořit rozhraní API, které se liší výrazně z jakéhokoli existující rozhraní API .NET, má smysl vytvoření runtime typů, které budou typ vymazání a reprezentace pro zadané typy.
<br />

V příkladu v tomto dokumentu používá řetězce jako reprezentace zadaných objektů. Často může být vhodné k použití pro vyjádření jiné objekty. Můžete například použít slovník jako kontejner objektů:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Jako alternativu může definovat typu ve zprostředkovateli typ, který se použije v době běhu k reprezentaci, společně s jednu nebo více operací modulu runtime:

```fsharp
type DataObject() =
let data = Dictionary<string,obj>()
member x.RuntimeOperation() = data.Count
```

Zadaný členy pak můžete vytvořit instance tohoto typu objektu:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

V takovém případě může (volitelně) použijete tento typ jako typ vymazání zadáním tohoto typu, jako `baseType` při sestavování `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

`Key Lessons`

V předchozí části Vysvětlení najdete postup vytvoření jednoduchého zprostředkovatele typu mazání, která poskytuje celou řadu typů, vlastnosti a metody. Tato část také vysvětlené koncept typ vymazání, včetně některé z výhod a nevýhod poskytnout vymazaných typy z typu poskytovatele a popsané reprezentace vymazaných typy.


## <a name="a-type-provider-that-uses-static-parameters"></a>Typ zprostředkovatele, který používá statické parametry
Schopnost Parametrizace zprostředkovatelů typů pomocí statických dat umožňuje mnoho scénářů zajímavé, i v případech, kdy zprostředkovatel nepotřebuje přístup k žádným datům místní nebo vzdálené. V této části se dozvíte některé základní postupy pro uvedení společně takové zprostředkovatele.


### <a name="type-checked-regex-provider"></a>Zaškrtnutí Regex – zprostředkovatel typu
Představte si, že chcete implementovat typ zprostředkovatele pro regulární výrazy, který zabalí .NET `System.Text.RegularExpressions.Regex` knihovny v rozhraní, které poskytuje následující záruky kompilace:


- Ověřuje, zda je platný regulární výraz.
<br />

- Poskytuje pojmenované vlastnosti na odpovídající položky, které jsou založeny na názvy všech skupin v regulárním výrazu.
<br />

V této části se dozvíte, jak vytvořit pomocí zprostředkovatelů typů `RegExProviderType` zadejte, že poskytne tyto výhody parameterizes regulární výraz. Kompilátor nahlásí chybu, pokud zadanému vzoru není platný, a typ zprostředkovatele můžete rozbalit skupiny z vzoru tak, aby je můžete přistupovat pomocí vlastnosti shoduje s názvem. Při návrhu zprostředkovatele typ měli zvážit, jak by měla vypadat jeho zveřejněné rozhraní API pro koncové uživatele a jak se tento návrh přeloží pro kód .NET. Následující příklad ukazuje, jak používat takové rozhraní API jak získat komponenty kód oblasti:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Následující příklad ukazuje, jak zprostředkovatel typu překládá těchto volání:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Vezměte na vědomí následující body:


- Představuje typ standardní Regex parametrizované `RegexTyped` typu.
<br />

- `RegexTyped` Konstruktor výsledkem volání konstruktoru Regex předávání v statický typ argumentu pro vzoru.
<br />

- Výsledky `Match` metoda jsou reprezentované pomocí standardní `System.Text.RegularExpressions.Match` typu.
<br />

- Každou skupinu s názvem výsledkem zadané vlastnosti a přístupu k vlastnosti výsledkem použití indexer na shodu `Groups` kolekce.
<br />

Následující kód je základní logiku pro implementaci takové zprostředkovatele a v tomto příkladu vynechá přidání všech členů na zadaný typ. Informace o každý přidaný člen najdete v příslušné části dále v tomto tématu. Pro kód úplné stažení ukázky z [F # 3.0 ukázka Pack](http://fsharp3sample.codeplex.com) na webu Codeplex.

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
let ty = ProvidedTypeDefinition(
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

Vezměte na vědomí následující body:


- Typ zprostředkovatele přebírá dva parametry statické: `pattern`, což je povinný a `options`, (protože je výchozí hodnota je zadáno) jsou volitelné.
<br />

- Po argumentů statické jsou zadány, můžete vytvořit instanci regulární výraz. Tato instance bude vyvolána výjimka, pokud regulární výraz je poškozený a tato chyba bude ohlášena uživatele.
<br />

- V rámci `DefineStaticParameters` zpětné volání, můžete definovat typ, který bude vrácen po jsou zadané argumenty.
<br />

- Tento kód nastaví `HideObjectMethods` na hodnotu true, aby prostředí IntelliSense zůstane efektivní. Tento atribut způsobí, že `Equals`, `GetHashCode`, `Finalize`, a `GetType` členy do potlačit ze seznamů IntelliSense pro zadaný objekt.
<br />

- Používáte `obj` jako základní typ metody, ale budete používat `Regex` objektu jako runtime reprezentaci tohoto typu, jako další příklad ukazuje.
<br />

- Volání `Regex` vyvolá konstruktor `System.ArgumentException` při regulární výraz není platný. Kompilátor zachytí výjimku a oznámí chybovou zprávu pro uživatele v době kompilace nebo v editoru Visual Studio. Tato výjimka umožňuje regulární výrazy, které má být ověřen bez spuštění aplikace.
<br />

Typ definovaný nad není ještě užitečné, protože neobsahuje žádné smysluplný metody nebo vlastnosti. Nejprve přidejte statického `IsMatch` metoda:

```fsharp
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

Předchozí kód definuje metodu `IsMatch`, která přebírá řetězec jako vstup a vrátí `bool`. Pouze složité část je použití `args` argument v rámci `InvokeCode` definice. V tomto příkladu `args` je seznam uvozovky zastupující argumenty této metodě. Pokud je metoda metody instance, představuje první argument `this` argument. Ale pro statickou metodu argumenty jsou všechny právě explicitní argumenty pro metodu. Všimněte si, že typ uvozovkách hodnoty by měl odpovídat zadaný návratový typ (v tomto případě `bool`). Také Upozorňujeme, že tento kód používá `AddXmlDoc` metoda a ujistěte se také, že zadaná metoda je užitečná dokumentaci k nástroji, kterou můžete zadat pomocí IntelliSense.

Dále přidejte metodu Match instance. Však tato metoda by měla vrátit hodnotu zadaný `Match` zadejte tak, aby se dalo přistupovat skupiny způsobem silného typu. Proto je nejdřív deklarovat `Match` typu. Protože tento typ závisí na vzor, který byl zadán jako statické argument, musí být tento typ vnořen v definici parametrizované typu:

```fsharp
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

ty.AddMember matchTy
```

Potom přidáte jednu vlastnost typu shodu pro každou skupinu. V době běhu je vyjádřené shody `System.Text.RegularExpressions.Match` hodnotu, takže musíte použít uvozovky, která definuje vlastnost `System.Text.RegularExpressions.Match.Groups` indexované vlastnosti získat relevantní skupiny.

```fsharp
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember prop
```

Znovu si všimněte, že přidáváte dokumentace XML do zadané vlastnosti. Také Upozorňujeme, že vlastnost může číst, pokud `GetterCode` funkce je k dispozici, a vlastnost lze zapisovat, pokud `SetterCode` funkce je k dispozici, proto výsledné vlastnost je jen pro čtení.

Nyní můžete vytvořit metody instance, která vrátí hodnotu tohoto `Match` typu:

```fsharp
let matchMethod = 
ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

Vzhledem k tomu, že vytváříte metodu instance `args.[0]` představuje `RegexTyped` instanci, na kterém metoda je volána, a `args.[1]` je vstupní argument.

Nakonec zadejte konstruktor, aby bylo možné vytvořit instancí zadaného typu.

```fsharp
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)
ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Konstruktor vymaže jenom k vytvoření standardní instance .NET Regex, která je znovu zabalená na objekt, protože `obj` je výmaz zadaného typu. S touto změnou využití ukázkové rozhraní API, které zadaná v dřívější tématu funguje podle očekávání. Následující kód je úplný a poslední:

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



let ty = ProvidedTypeDefinition(
thisAssembly, 
rootNamespace, 
typeName, 
baseType = Some baseTy)

ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

// Provide strongly typed version of Regex.IsMatch static method.
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

ty.AddMember isMatch

// Provided type for matches
// Again, erase to obj even though the representation will always be a Match
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

// Nest the match type within parameterized Regex type.
ty.AddMember matchTy

// Add group properties to match type
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember(prop)

// Provide strongly typed version of Regex.Match instance method.
let matchMeth = ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

ty.AddMember matchMeth

// Declare a constructor.
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

// Add documentation to the constructor.
ctor.AddXmlDoc "Initializes a regular expression instance"

ty.AddMember ctor

ty
| _ -> failwith "unexpected parameter values")) 

do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

`Key Lessons`

V této části Vysvětlení způsobu vytváření typ zprostředkovatele, který funguje na jeho statické parametry. Zprostředkovatel zkontroluje statický parametr a poskytuje operace založené na jeho hodnotu.


## <a name="a-type-provider-that-is-backed-by-local-data"></a>Typ zprostředkovatele, který je zálohovaný díky místní Data
Často můžete chtít zprostředkovatelů typů k dispozici rozhraní API podle pouze statické parametry, ale také informace z místní nebo vzdálené systémy. Tato část popisuje typ zprostředkovatele, které jsou založeny na místní data, jako je například místní datové soubory.


### <a name="simple-csv-file-provider"></a>Jednoduché CSV – zprostředkovatel souboru
Jako jednoduchý příklad zvažte zprostředkovatele typů pro přístup k vědeckých dat ve formátu hodnoty oddělené čárkami (CSV). V této části se předpokládá, že soubory CSV obsahovat řádek záhlaví, za nímž následuje data s plovoucí desetinnou, jak ukazuje následující tabulka:



|Vzdálenost (monitorování)|Čas (sekundy)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|
V této části ukazuje, jak poskytnout typ, který vám pomůže získat řádky s `Distance` vlastnost typu `float<meter>` a `Time` vlastnost typu `float<second>`. Pro jednoduchost jsou provedeny následující předpoklady:


- Názvy záhlaví jsou buď bez měrné jednotky nebo tvar "Název" (jednotky) a nesmí obsahovat čárky.
<br />

- Všechny jednotky systém mezinárodní (SI), jako jsou jednotky [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames – modul (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modul definuje.
<br />

- Jednotky jsou všechny jednoduché (například monitorovat) místo složené (například, měření za sekundu).
<br />

- Všechny sloupce obsahují data s plovoucí desetinnou.
<br />

Obsáhlejší zprostředkovatele by povolte tato omezení.

Prvním krokem je znovu vzít v úvahu, jak by měla vypadat rozhraní API. Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

V takovém případě by měl kompilátor převést těchto volání na něco podobného jako v následujícím příkladu:

```fsharp
let info = new MiniCsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

Optimální překlad bude vyžadovat typ zprostředkovatele, který má definovat reálné číslo `CsvFile` typu v sestavení typ poskytovatele. Zprostředkovatelé typů často závisí na několik pomocná typy a metody můžete zabalit důležité logiku. Protože míry jsou vymazány za běhu, můžete použít `float[]` jako typ vymazaných pro řádek. Kompilátor počítat různé sloupce s typy jinou míru. Například z prvního sloupce v našem příkladu má typ `float<meter>`, a druhá má `float<second>`. Však může zůstat vymazaných reprezentace poměrně jednoduché.

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
inherit TypeProviderForNamespaces()

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

let prop = ProvidedProperty(fieldName, fieldTy, 
GetterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

// Add metadata that defines the property's location in the referenced file.
prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
rowTy.AddMember(prop) 

// Define the provided type, erasing to CsvFile.
let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

// Add a parameterless constructor that loads the file that was used to define the schema.
let ctor0 = ProvidedConstructor([], 
InvokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
ty.AddMember ctor0

// Add a constructor that takes the file name to load.
let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
InvokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
ty.AddMember ctor1

// Add a more strongly typed Data property, which uses the existing property at runtime.
let prop = ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
GetterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
ty.AddMember prop

// Add the row type as a nested type.
ty.AddMember rowTy
ty)

// Add the type to the namespace.
do this.AddNamespace(ns, [csvTy])
```

Vezměte na vědomí následující body o implementaci:


- Přetížené konstruktory povolit původní soubor nebo ten, který má stejné schéma čtení. Tento vzor je běžné při zapisovat zprostředkovatele typů pro místní nebo vzdálené datové zdroje, a tento vzor umožňuje místního souboru, který se má použít jako šablonu pro vzdálená data.
<br />  Můžete použít [typeproviderconfig –](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) hodnotu, která je v předaný konstruktoru zprostředkovatele typ k vyřešení relativních názvů souborů.
<br />

- Můžete použít `AddDefinitionLocation` metoda zadat umístění zadané vlastnosti. Proto pokud používáte `Go To Definition` u zadané vlastnosti, otevře se soubor CSV v sadě Visual Studio.
<br />

- Můžete použít `ProvidedMeasureBuilder` typ k vyhledání jednotek SI a ke generování odpovídajícího `float<_>` typy.
<br />

`Key Lessons`

Tato část vysvětluje vytvoření zprostředkovatele typů pro místní zdroj dat s jednoduché schéma, které se nachází v samotném zdroji dat.


## <a name="going-further"></a>Budete pokračovat
Následující části obsahují návrhy pro další studie.


### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Podívejte se na zkompilovaný kód pro vymazaných typy
Získáte představu, jak použití zprostředkovatele typu odpovídá kód, který je vygenerované, podívejte se na následující funkce pomocí `HelloWorldTypeProvider` používané v tomto tématu výše.

```fsharp
let function1 () = 
let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
obj1.InstanceProperty
```

Zde je výsledný kód decompiled pomocí ildasm.exe bitové kopie:

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

Jak ukazuje příklad, všechny zmínky o typ `Type1` a `InstanceProperty` vlastnost byl vymazán, a operace pouze na typy runtime související se situací.


### <a name="design-and-naming-conventions-for-type-providers"></a>Návrh a konvence pojmenování pro zprostředkovatelů typů
Sledujte následující konvence při vytváření zprostředkovatele typu.


- `Providers for Connectivity Protocols`
<br />  Obecně platí, názvy většina zprostředkovatele – knihovny DLL pro data a služby připojení protokoly, jako je například OData nebo SQL připojení, musí končit `TypeProvider` nebo `TypeProviders`. Například použijte název knihovny DLL, která se podobá následující řetězec:
<br />

```
  Fabrikam.Management.BasicTypeProviders.dll
```

  Ujistěte se, že vaše zadané typy jsou členy odpovídající oboru názvů a připojení protokolu, který jste implementovali:
<br />

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

- `Utility Providers for General Coding`
<br />  Nástroj Typ zprostředkovatele, například pro regulární výrazy typ zprostředkovatele, může být součástí základní knihovny, jak ukazuje následující příklad:
<br />

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

  V takovém případě zadaný typ objeví v odpovídajícím bodě podle normální .NET návrhu konvence:
<br />

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

- `Singleton Data Sources`
<br />  Někteří poskytovatelé typ připojení ke zdroji dat jeden vyhrazený a zadejte jenom data. V takovém případě by měl vyřadit `TypeProvider` přípona a používat běžné konvence pro pojmenování .NET:
<br />

```fsharp
  #r "Fabrikam.Data.Freebase.dll"
  
  let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

  Další informace najdete v tématu `GetConnection` návrh názvů, který je popsán dále v tomto tématu.
<br />


### <a name="design-patterns-for-type-providers"></a>Vzory návrhu pro zprostředkovatelů typů
Následující části popisují vzorů návrhu, které můžete použít při vytváření zprostředkovatele typu.


#### <a name="the-getconnection-design-pattern"></a>Vzor návrhu GetConnection
Většina zprostředkovatelů typů zasílány používat `GetConnection` vzor, který je používán typ zprostředkovatele v FSharp.Data.TypeProviders.dll, jak ukazuje následující příklad:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Zprostředkovatelé typů zálohován vzdálených dat a služby
Než vytvoříte typ zprostředkovatele, který je zálohovaný díky vzdálených dat a služby, musíte zvážit řadu problémů, které jsou obsaženy v připojených programování. Tyto problémy patří následující aspekty:


- Schéma mapování
<br />

- liveness a zneplatnění případě změny schématu
<br />

- ukládání do mezipaměti schématu
<br />

- asynchronní implementace operací přístupu k datům
<br />

- Podpora dotazů, včetně dotazů LINQ
<br />

- pověření a ověřování
<br />

V tomto tématu není prozkoumat tyto další problémy.


### <a name="additional-authoring-techniques"></a>Další techniky pro vytváření obsahu
Když píšete vlastní typ zprostředkovatele, můžete použít následující další techniky.


- `Creating Types and Members On-Demand`
<br />  Rozhraní API ProvidedType má odložené verzích přidávat členy.
<br />

```fsharp
  type ProvidedType =
  member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
  member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

  Tyto verze se používají k vytvoření prostorů na vyžádání typů.
<br />

- `Providing Array, ByRef, and Pointer types`
<br />  Zkontrolujte zadané členy (jehož podpisy zahrnují typy polí, typy byref a instancí možnosti obecné typy) s použitím normální `MakeArrayType`, `MakePointerType`, a `MakeGenericType` na jakoukoli instanci System.Type, včetně `ProvidedTypeDefinitions`.
<br />

- `Providing Unit of Measure Annotations`
<br />  Rozhraní API ProvidedTypes poskytuje pomocné rutiny pro zajištění měr poznámky. Chcete-li například zadat typ `float<kg>`, použijte následující kód:
<br />

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  K poskytování typ `Nullable<decimal<kg/m^2>>`, použijte následující kód:
<br />

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

- `Accessing Project-Local or Script-Local Resources`
<br />  Je možné přidělit každou instanci zprostředkovatele typů `TypeProviderConfig` hodnotu během vytváření. Tato hodnota obsahuje "řešení složka" pro poskytovatele (který je složka projektu kompilace nebo adresář, který obsahuje skript), seznam odkazovaná sestavení a další informace.
<br />

- `Invalidation`
<br />  Zprostředkovatelé může být spojeno zneplatnění signály oznámit služba jazyka F #, který možná změnil předpoklady schématu. Když dojde k zneplatnění, typecheck je znovu, pokud zprostředkovatel je hostované v sadě Visual Studio. Tento signál se ignoruje, pokud zprostředkovatel je hostovaná v F # interaktivní nebo kompilátoru F # (fsc.exe).
<br />

- `Caching Schema Information`
<br />  Zprostředkovatelé musí mezipaměti často přístup k informacím o schématu. Data uložená v mezipaměti by měly být uložené pomocí názvu souboru, který je přiřazen jako statický parametr nebo jako uživatelská data. Je například ukládání do mezipaměti schématu `LocalSchemaFile` ve zprostředkovatelích typu v parametru `FSharp.Data.TypeProviders` sestavení. Při provádění těchto poskytovatelů přesměruje tento statický parametr typ zprostředkovatele, který má používat informace o schématu do zadaného místního souboru místo přístup ke zdroji dat přes síť. Pokud chcete použít informace uložené v mezipaměti schématu, musíte taky nastavit statický parametr `ForceUpdate` k `false`. Podobným způsobem můžete použít k povolení přístupu k datům online a offline.
<br />

- `Backing Assembly`
<br />  Při kompilaci souboru .dll nebo .exe, je soubor .dll zálohování pro generovaný typy staticky propojené do výsledné sestavení. Tento odkaz se vytvoří zkopírováním definic typů Intermediate Language (IL) a všechny spravované prostředky z základní sestavení do konečné sestavení. Při použití F # interaktivní, soubor .dll zálohování nebude zkopírován a místo toho je načíst přímo do procesu F # interaktivní.
<br />

- `Exceptions and Diagnostics from Type Providers`
<br />  Všechny používá všech členů ze zadané typy může vyvolat výjimky. Ve všech případech Pokud zprostředkovatel typu, vyvolá výjimku, kompilátoru hostitele atributy chyba na konkrétní typ poskytovatele.
<br />
  - Typ zprostředkovatele výjimky by nikdy vést k chybám interní kompilátoru.
<br />

  - Zprostředkovatelé typů nemůžete hlásit upozornění.
<br />

  - Pokud zprostředkovatele typů hostovaný v kompilátoru F #, F # vývojového prostředí nebo F # interaktivní, jsou zachyceny všechny výjimky z tohoto zprostředkovatele. Vlastnosti zprávy je vždy text chyby a zobrazí se žádné trasování zásobníku. Pokud se chystáte způsobí výjimku, můžete vyvolat následující příklady:
<br />
    - `System.NotSupportedException`
<br />

    - `System.IO.IOException`
<br />

    - `System.Exception`
<br />


#### <a name="providing-generated-types"></a>Poskytnutí generovaného typy
Pokud má tento dokument vysvětlené jak zadejte vymazaných typy. Mechanismus zprostředkovatele typu v F # můžete také použít k poskytnutí generovaného typů, které jsou přidány jako skutečné definice typů .NET do programu uživatelů. Můžete musí odkazovat na generovaného poskytnout typy pomocí definice typu.

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<" http://services.odata.org/Northwind/Northwind.svc/">
```

Kód pomocného objektu ProvidedTypes 0,2, který je součástí verze F # 3.0 má omezenou podporu pro zajištění generovaného typy. Pro definici typu generované musí platit následující příkazy:


- IsErased musí být nastavena na `false`.
<br />

- Zprostředkovatel musí mít sestavení, který má soubor .dll .NET skutečné zálohování s odpovídající soubor DLL na disku.
<br />

Musíte také zavolat `ConvertToGenerated` pro zadaný kořenový typ jejichž vnořené typy formuláři uzavřené sadu generovaného typů. Toto volání vysílá definici daný zadaný typ a jeho definice vnořené typy v sestavení a upraví `Assembly` vlastnosti všech definic zadaný typ vrátit této položky assembly. Sestavení jsou vydávány pouze v případě, že je získat přístup k vlastnosti sestavení pro kořenové typ poprvé. Kompilátor hostitele F # přístup k této vlastnosti, pokud ho zpracuje deklarace tvoří typu pro typ.


## <a name="rules-and-limitations"></a>Pravidla a omezení
Když píšete zprostředkovatelů typů, uvědomte si následující pravidla a omezení.


- `Provided types must be reachable.`
<br />  Všechny zadané typy by měly být dostupné z typů-nested. -Nested typy jsou uvedeny ve volání `TypeProviderForNamespaces` konstruktoru nebo volání `AddNamespace`. Například, pokud zprostředkovatel poskytuje typu `StaticClass.P : T`, ujistěte se, že je T-nested typ nebo vnořené v rámci jedné.
<br />  Například někteří poskytovatelé mít statická třída jako `DataTypes` obsahující tyto `T1, T2, T3, ...` typy. Chyba, jinak hodnota říká, že našel se odkaz na typ T v sestavení A, ale typ nebyl nalezen v této sestavě. Pokud tato chyba se zobrazí, ověřte, že všechny podtypů lze přejít z typy zprostředkovatele. Poznámka: Tyto `T1, T2, T3...` typy jsou označovány jako *na průběžně* typy. Nezapomeňte zahrnout je přístupné oboru názvů nebo nadřazený typ.
<br />

- `Limitations of the Type Provider Mechanism`
<br />  Typ zprostředkovatele mechanismus v F # má následující omezení:
<br />
  - Základní infrastruktury pro zprostředkovatelů typů v jazyce F # nepodporuje zadaný obecné typy nebo, pokud obecné metody.
<br />

  - Tento mechanismus nepodporuje vnořené typy s statické parametry.
<br />

- `Limitations of the ProvidedTypes Support Code`
<br />  `ProvidedTypes` Podporu kódu má následující pravidla a omezení:
<br />
  1. Zadané vlastnosti s indexované mechanismy získání a nastavení nejsou implementované.
<br />

  2. Nejsou implementované zadané události.
<br />

  3. Zadané typy a objekty informace slouží pouze pro tento typ poskytovatele mechanismus v jazyce F #. Nejsou více obecně použitelné jako objekty System.Type.
<br />

  4. Konstrukce, které můžete použít v uvozovky, které definují implementacím metoda mají několik omezení. Může být zdrojový kód pro ProvidedTypes -*verze* zobrazíte konstrukce, které jsou podporovány v uvozovky.
<br />

- `Type providers must generate output assemblies that are .dll files, not .exe files.`
<br />


## <a name="development-tips"></a>Tipy pro vývoj
Následující tipy mohou být užitečné během procesu vývoje.


- `Run Two Instances of Visual Studio.`Můžete vytvořit typ zprostředkovatele v jedné instance a testování zprostředkovatele v dalších, protože test IDE bude trvat zámek na soubor .dll, který zabrání se znovu sestavit typ zprostředkovatele. Proto je třeba nejprve zavřít druhou instanci sady Visual Studio, zatímco zprostředkovatele je vytvořen v první instance, a pak musí znovu otevřete druhou instanci po zprostředkovatele.
<br />

- `Debug type providers by using invocations of fsc.exe.`Zprostředkovatelé typů můžete vyvolat pomocí následující nástroje:
<br />
  - FSC.exe (příkazového řádku kompilátor jazyka F #)
<br />

  - fsi.exe (F # interaktivní kompilátoru)
<br />

  - devenv.exe (Visual Studio)
<br />

  Zprostředkovatelé typů můžete ladit často snadno pomocí fsc.exe na soubor skriptu test (například script.fsx). Ladicí program z příkazového řádku můžete spustit.
<br />

```
  devenv /debugexe fsc.exe script.fsx
```

  Protokolování tiskových stdout můžete použít.
<br />


## <a name="see-also"></a>Viz také
[Zprostředkovatelé typů](index.md)
