---
title: 'Kurz: Vytvoření zprostředkovatele typů (F #)'
description: 'Naučte se vytvářet vlastní F # – zprostředkovatelé typů v F # 3.0 prověřením několik poskytovatelů jednoduchý typ pro ilustraci se základními koncepty.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: cea71a2b71f660971c1b2dde702c9b489be48cee
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="c7fd4-103">Kurz: Vytvoření zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="c7fd4-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="c7fd4-104">Typ zprostředkovatele mechanismus v F # je významnou část podporuje programování bohaté informace.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="c7fd4-105">Tento kurz vysvětluje, jak vytvořit vlastní typ zprostředkovatele jste s návodem vývoj několik poskytovatelů jednoduchý typ pro ilustraci se základními koncepty.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="c7fd4-106">Další informace o typu poskytovatele mechanismus v F # najdete v tématu [zprostředkovatelů typů](index.md).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="c7fd4-107">Ekosystému F # obsahuje řadu typ zprostředkovatele pro běžně používané služby dat na Internet a enterprise.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="c7fd4-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-108">For example:</span></span>

- <span data-ttu-id="c7fd4-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) obsahuje typ zprostředkovatele pro JSON, XML, CSV a HTML dokumentu formáty.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="c7fd4-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje dotazy pro tyto zdroje dat silného typu přístup k databázím SQL prostřednictvím objektu mapování a F # LINQ.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="c7fd4-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) má sadu typ zprostředkovatele pro kompilaci zaškrtnutí vložení T-SQL v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="c7fd4-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sada zprostředkovatelů typů pro použití pouze s programováním rozhraní .NET Framework pro přístup ke službám dat SQL, rozhraní Entity Framework, OData a WSDL.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="c7fd4-113">V případě potřeby můžete vytvořit vlastní typ zprostředkovatele nebo typ zprostředkovatele, ostatní vytvořené, můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="c7fd4-114">Vaše organizace může mít například služba data, která poskytuje velké a rostoucí počet sad dat s názvem, každou s vlastním schématem stabilní data.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="c7fd4-115">Můžete vytvořit typ zprostředkovatele, který čte schémata a zobrazí aktuální sady dat programátorů způsobem silného typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="c7fd4-116">Než začnete</span><span class="sxs-lookup"><span data-stu-id="c7fd4-116">Before You Start</span></span>

<span data-ttu-id="c7fd4-117">Tento typ poskytovatele mechanismus je primárně určený pro vložení stabilní data a informace prostory služby do programovací prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="c7fd4-118">Tento mechanismus není určená pro vložení mezery informace jejichž schématu se změní při spuštění programu způsoby, které jsou relevantní pro logiku programu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="c7fd4-119">Navíc tento mechanismus není určená pro intra jazyk meta-programování, i když tuto doménu obsahuje některé platné používá.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="c7fd4-120">Tento mechanismus byste měli použít pouze v případě potřeby a kde vývoj zprostředkovatele typů výsledkem velmi vysokou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="c7fd4-121">Vyhněte se zápis typ zprostředkovatele, kde není k dispozici schéma.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="c7fd4-122">Podobně, neměli byste zápis zprostředkovatele typů, kde je běžný (nebo i existující) by stačit knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="c7fd4-123">Než začnete, může odpovědět na tyto otázky:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="c7fd4-124">Máte schéma pro zdroj informace?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="c7fd4-125">Pokud ano, co je mapování do F # a systém typů .NET?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="c7fd4-126">Můžete použít existující API (dynamicky zadávaných) jako výchozí bod týkající se vaší implementace?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="c7fd4-127">Bude vám a vaší organizaci mít dostatek používá typ zprostředkovatele, který má smysl zkontrolujte jejich zápisu?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="c7fd4-128">Běžné knihovny .NET by vyhovovala vašim potřebám?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="c7fd4-129">Kolik změní schéma?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-129">How much will your schema change?</span></span>

- <span data-ttu-id="c7fd4-130">Se změní při kódování?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-130">Will it change during coding?</span></span>

- <span data-ttu-id="c7fd4-131">Se změní mezi kódování relace?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="c7fd4-132">Se změní při spuštění programu?</span><span class="sxs-lookup"><span data-stu-id="c7fd4-132">Will it change during program execution?</span></span>

<span data-ttu-id="c7fd4-133">Zprostředkovatelé typů jsou nejvhodnější pro situacích, kde je stabilní za běhu a po dobu životnosti zkompilovaný kód schématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>


## <a name="a-simple-type-provider"></a><span data-ttu-id="c7fd4-134">Jednoduchý typ zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c7fd4-134">A Simple Type Provider</span></span>

<span data-ttu-id="c7fd4-135">Tato ukázka je Samples.HelloWorldTypeProvider, podobně jako ukázky `examples` adresář [F # typ poskytovatele sady SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="c7fd4-136">Zprostředkovatel zpřístupní "typ prostor", který obsahuje 100 vymazaných typů, jak ukazuje následující kód pomocí syntaxe podpis F # a vynechat podrobnosti pro všechny kromě `Type1`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="c7fd4-137">Další informace o typech vymazaných najdete v tématu [podrobnosti o vymazat zadané typy](#details-about-erased-provided-types) dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="c7fd4-138">Všimněte si, že se staticky označuje sadu typy a členy zadané.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="c7fd4-139">V tomto příkladu není využít možnost zprostředkovatelů zadejte typy, které jsou závislé na schéma.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="c7fd4-140">Implementace zprostředkovatele typu popsané v následujícím kódu a podrobnosti jsou popsané v dalších částech tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>


>[!WARNING] 
<span data-ttu-id="c7fd4-141">Mohou existovat rozdíly mezi tento kód a online ukázky.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="c7fd4-142">Pro tohoto zprostředkovatele použijte otevřete samostatné instanci sady Visual Studio, vytvořit skript F # a potom přidejte odkaz na poskytovateli z vašeho skriptu pomocí #r jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="c7fd4-143">Poté vyhledejte typy v části `Samples.HelloWorldTypeProvider` obor názvů, který generuje typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="c7fd4-144">Než můžete znovu zkompiluje zprostředkovatele, ujistěte se, uzavřít všechny instance Visual Studio a F # interaktivní, které používají zprostředkovatele knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="c7fd4-145">Chyby sestavení, jinak hodnota dojde, protože zamkne výstupní knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="c7fd4-146">Chcete-li ladit tento zprostředkovatel pomocí tiskové příkazy, zkontrolujte skript, který zveřejňuje potížím s poskytovatelem a pak použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="c7fd4-147">Chcete-li ladit tento zprostředkovatel pomocí sady Visual Studio, otevřete příkazový řádek sady Visual Studio s přihlašovacími údaji správce a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-147">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="c7fd4-148">Jako alternativu, otevřete Visual Studio, otevřete nabídku ladění, zvolte `Debug/Attach to process…`a připojte k jiné `devenv` procesu, kde provádíte změny vašeho skriptu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="c7fd4-149">Pomocí této metody můžete snadno vybrat konkrétní logiku ve zprostředkovateli typu interaktivně zadáním výrazy do druhé instance (s plnou technologie IntelliSense a další funkce).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="c7fd4-150">Pouze můj kód ladění lépe identifikovat chyby v generovaného kódu můžete zakázat.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="c7fd4-151">Informace o tom, jak povolit nebo zakázat tuto funkci najdete v tématu [procházení kódu s ladicím programem](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="c7fd4-152">Navíc můžete také nastavit první odpovídající výjimce zachytávání otevřením `Debug` nabídky a pak vyberete `Exceptions` nebo výběrem klávesy Ctrl + Alt + E otevřete `Exceptions` dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="c7fd4-153">V tomto dialogu pod `Common Language Runtime Exceptions`, vyberte `Thrown` zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>


### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="c7fd4-154">Implementace zprostředkovatele typu</span><span class="sxs-lookup"><span data-stu-id="c7fd4-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="c7fd4-155">Tato část vás provede procesem na hlavní části implementace typ zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="c7fd4-156">Nejprve definovat typ pro vlastní typ zprostředkovatele sám sebe:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="c7fd4-157">Tento typ musí být veřejné a označte ji s [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) tak, aby kompilátor rozpozná typ zprostředkovatele, když samostatného projektu F # odkazuje na sestavení, které obsahuje typ atributu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="c7fd4-158">*Konfigurace* parametr je volitelný a pokud existuje, obsahuje kontextové konfigurační informace pro instanci zprostředkovatele typu, která vytvoří kompilátor jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="c7fd4-159">V dalším kroku implementujete [itypeprovider –](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="c7fd4-160">V takovém případě použijete `TypeProviderForNamespaces` typu z `ProvidedTypes` rozhraní API jako základní typ.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="c7fd4-161">Tento typ pomocné rutiny můžete poskytnout soubor konečné například zadaný obory názvů, z nichž každý přímo obsahuje omezený počet pevné, například zadané typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="c7fd4-162">V tomto kontextu zprostředkovatele *například* generuje typy, i když nejsou potřeba nebo použít.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="c7fd4-163">V dalším kroku definovat místní privátní hodnoty, které určují obor názvů pro zadané typy a najít sestavení zprostředkovatele typu sám sebe.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="c7fd4-164">Toto sestavení se později používá jako logické nadřazený typ vymazaných typů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="c7fd4-165">Dál vytvořte funkci zajistit každý typ Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="c7fd4-166">Tato funkce je podrobně popsány dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="c7fd4-167">Dále generovat 100 zadané typy:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="c7fd4-168">V dalším kroku přidejte typy jako zadaný obor názvů:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="c7fd4-169">Nakonec přidejte atribut sestavení, který označuje, že vytváříte zprostředkovatele typů knihovny DLL:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="c7fd4-170">Poskytuje jeden typ a její členy</span><span class="sxs-lookup"><span data-stu-id="c7fd4-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="c7fd4-171">`makeOneProvidedType` Funkce neodpovídá skutečné pracovní poskytnout jeden z typů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="c7fd4-172">Tento krok popisuje implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="c7fd4-173">Nejprve vytvořte zadaný typ (například Type1, když n = 1, nebo Type57, když n = 57).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="c7fd4-174">Nezapomeňte přitom následující body:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-174">You should note the following points:</span></span>

- <span data-ttu-id="c7fd4-175">To, pokud je typ vymazat.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-175">This provided type is erased.</span></span>  <span data-ttu-id="c7fd4-176">Protože jste označení, že je základní typ `obj`, instancí se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="c7fd4-177">Když zadáte typu-nested, musíte zadat sestavení a oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="c7fd4-178">Pro vymazaných typy sestavení by měla být sestavení zprostředkovatele typu sám sebe.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="c7fd4-179">Dál přidejte dokumentace XML typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="c7fd4-180">Tato dokumentace je zpožděno, to znamená, počítaný na vyžádání, pokud se vyžaduje kompilátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="c7fd4-181">Dále přidejte zadané statické vlastnosti typu:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="c7fd4-182">Získání této vlastnosti bude vždy vyhodnocena jako text "Hello!".</span><span class="sxs-lookup"><span data-stu-id="c7fd4-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="c7fd4-183">`GetterCode` Pro vlastnost používá F # uvozovky, která představuje kód, který kompilátoru hostitele generuje pro získání vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="c7fd4-184">Další informace o uvozovky najdete v tématu [uvozovky kódu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="c7fd4-185">Přidejte dokumentace XML pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="c7fd4-186">Zadaná vlastnost nyní připojte zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="c7fd4-187">Zadaný člen musíte přiřadit pouze jeden typ.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="c7fd4-188">V opačném člen nikdy budou přístupné.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="c7fd4-189">Teď vytvořte zadaný konstruktoru, které nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="c7fd4-190">`InvokeCode` Pro konstruktor vrátí F # uvozovky, která představuje kód, který kompilátoru hostitele generuje při volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="c7fd4-191">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="c7fd4-192">Instanci zadaného typu se vytvoří základní daty "Data objektu".</span><span class="sxs-lookup"><span data-stu-id="c7fd4-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="c7fd4-193">Uvozovkách kód obsahuje převod na [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) vzhledem k tomu, že je tento typ vymazání to zadaný typ (jaký jste uvedli, když deklarovat zadaného typu).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="c7fd4-194">Přidejte dokumentace XML pro konstruktor a přidejte zadaný konstruktor na zadaný typ:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="c7fd4-195">Vytvořte druhý zadaný konstruktor, který přijímá jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="c7fd4-196">`InvokeCode` Pro konstruktor znovu vrátí F # uvozovky, která představuje kód, který kompilátoru hostitele generuje pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="c7fd4-197">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="c7fd4-198">Pomocí zadaných dat "10" se vytvoří instanci zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="c7fd4-199">Může mít už k tomu, který `InvokeCode` funkce vrátí uvozovek.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="c7fd4-200">Vstup pro tuto funkci je seznam výrazů, jeden pro každý parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="c7fd4-201">V takovém případě je k dispozici v výraz, který představuje hodnotu jeden parametr `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="c7fd4-202">Kód pro volání konstruktoru převede návratovou hodnotu vymazaných typu `obj`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="c7fd4-203">Po přidání druhého zadaný konstruktor typu, můžete vytvořit zadanou instanci vlastnost:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="c7fd4-204">Získávání tato vlastnost vrátí délku řetězce, který je objekt reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="c7fd4-205">`GetterCode` Vlastnost vrací uvozovek F #, která určuje kód, který generuje kompilátoru hostitele GET pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="c7fd4-206">Jako `InvokeCode`, `GetterCode` funkce vrátí uvozovek.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="c7fd4-207">Kompilátor hostitele volání této funkce se seznamem argumentů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="c7fd4-208">V takovém případě argumenty, které zahrnují jenom jeden výraz, který představuje instanci, na kterém je volána metoda getter, kterým můžete přistupovat pomocí `args.[0]`. Implementace `GetterCode` pak splices do uvozovek výsledek vymazaných typu `obj`, a pro uspokojení kompilátoru mechanismus pro kontrolu typy, že objekt je řetězec se používá přetypování.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="c7fd4-209">V další části `makeOneProvidedType` poskytuje metodu instance jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-209">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="c7fd4-210">Nakonec vytvořte vnořené typu, který obsahuje 100 vnořené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-210">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="c7fd4-211">Vnořené vytvoření tohoto typu a jeho vlastnosti je zpožděno, to znamená, počítaný na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-211">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="c7fd4-212">Podrobnosti o vymazaných zadané typy</span><span class="sxs-lookup"><span data-stu-id="c7fd4-212">Details about Erased Provided Types</span></span>

<span data-ttu-id="c7fd4-213">Příklad v této části se poskytuje pouze *vymazat zadané typy*, které jsou obzvláště užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-213">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="c7fd4-214">Když píšete zprostředkovatele pro informace prostor, který obsahuje pouze data a metody.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-214">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="c7fd4-215">Když píšete poskytovatele, kde nejsou důležité pro praktické využití místa na informace sémantiku přesné runtime-type.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-215">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="c7fd4-216">Když píšete zprostředkovatele pro informace prostor, který je tak velký a vzájemně propojena, že není technicky možné vygenerovat skutečné typů .NET pro prostor informace.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-216">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="c7fd4-217">V tomto příkladu každý zadaný typ vymazáním na typ `obj`, a všechny používá typu se zobrazí jako typ `obj` v zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-217">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="c7fd4-218">Ve skutečnosti objekty v těchto příkladech jsou řetězce, ale typ se zobrazí jako `System.Object` v rozhraní .NET zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-218">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="c7fd4-219">I s všechna použití typ vymazání, můžete použít explicitní zabalení, rozbalení a přetypování k podkopat vymazat typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-219">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="c7fd4-220">Výjimky pro přetypování, který není platný v takovém případě může způsobit, když objekt se používá.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-220">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="c7fd4-221">Modul runtime zprostředkovatele můžete definovat vlastní typ privátní reprezentace k ochraně proti false reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-221">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="c7fd4-222">Nelze definovat vymazaných typy v jazyku F # sám sebe.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-222">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="c7fd4-223">Pouze zadané typy může vymazat.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-223">Only provided types may be erased.</span></span> <span data-ttu-id="c7fd4-224">Je potřeba pochopit následky, oba praktická a sémantické některou vymazat vymazaných typy pro váš typ zprostředkovatele nebo zprostředkovatele, který poskytuje typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-224">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="c7fd4-225">Typ vymazaných nemá skutečné typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-225">An erased type has no real .NET type.</span></span> <span data-ttu-id="c7fd4-226">Proto nemůžete udělat přesný odraz přes typ a může podkopat vymazaných typy, pokud používáte přetypování runtime a další metody, které jsou závislé na Sémantika typu přesný runtime.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-226">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="c7fd4-227">Subversion vymazaných typů často výsledkem typ přetypování výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-227">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>


### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="c7fd4-228">Výběr reprezentace pro vymazat zadané typy</span><span class="sxs-lookup"><span data-stu-id="c7fd4-228">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="c7fd4-229">U některých používá vymazaných zadaný typů žádné reprezentace se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-229">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="c7fd4-230">Například vymazaných zadaný typ může obsahovat pouze statické vlastnosti a členy a žádné konstruktory, a žádné metody nebo vlastnosti by vrátit instanci typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-230">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="c7fd4-231">Pokud se lze připojit vymazaných instancí zadaný typ, musíte zvážit následující otázky:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-231">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="c7fd4-232">**Co je zadaný typ vymazání?**</span><span class="sxs-lookup"><span data-stu-id="c7fd4-232">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="c7fd4-233">Vymazání poskytnutý typ je, jak zobrazuje typ v zkompilovaný kód .NET.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-233">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="c7fd4-234">Vymazání typu zadaný vymazaných třídy je vždy první-vymazat základní typ v řetězu dědičnosti typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-234">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="c7fd4-235">Vymazání typ zadaný vymazaných rozhraní je vždy `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-235">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="c7fd4-236">**Jaké jsou reprezentace zadaného typu?**</span><span class="sxs-lookup"><span data-stu-id="c7fd4-236">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="c7fd4-237">Sady možné objektů pro vymazaných zadaný typ se nazývají její reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-237">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="c7fd4-238">V příkladu v tomto dokumentu reprezentace všech vymazaných zadané typy `Type1..Type100` jsou vždy řetězcových objektů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-238">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="c7fd4-239">Všechny reprezentace zadaného typu musí být kompatibilní s vymazání zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-239">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="c7fd4-240">(Jinak, kompilátor jazyka F # zobrazí chybu pro použití poskytovatele typu, nebo vygeneruje neověřitelný kód rozhraní .NET, který není platný.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-240">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="c7fd4-241">Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)</span><span class="sxs-lookup"><span data-stu-id="c7fd4-241">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="c7fd4-242">Pomocí některé z následujících dvou přístupů Oboje je velmi běžné si můžete vybrat reprezentaci pro zadané objekty:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-242">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="c7fd4-243">Pokud zadáváte jednoduše silného typu obálku přes existující typ rozhraní .NET, často má smysl pro typ vašeho chcete vymazat tento typ, použijte instance tohoto typu jako reprezentace nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-243">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="c7fd4-244">Tento přístup je vhodné, když většina stávajících metod daný typ stále mít smysl, pokud používáte verzi silného.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-244">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="c7fd4-245">Pokud chcete vytvořit rozhraní API, které se liší výrazně z jakéhokoli existující rozhraní API .NET, má smysl vytvoření runtime typů, které budou typ vymazání a reprezentace pro zadané typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-245">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="c7fd4-246">V příkladu v tomto dokumentu používá řetězce jako reprezentace zadaných objektů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-246">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="c7fd4-247">Často může být vhodné k použití pro vyjádření jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-247">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="c7fd4-248">Můžete například použít slovník jako kontejner objektů:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-248">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="c7fd4-249">Jako alternativu může definovat typu ve zprostředkovateli typ, který se použije v době běhu k reprezentaci, společně s jednu nebo více operací modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-249">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="c7fd4-250">Zadaný členy pak můžete vytvořit instance tohoto typu objektu:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-250">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="c7fd4-251">V takovém případě může (volitelně) použijete tento typ jako typ vymazání zadáním tohoto typu, jako `baseType` při sestavování `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-251">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="c7fd4-252">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="c7fd4-252">Key Lessons</span></span>

<span data-ttu-id="c7fd4-253">V předchozí části Vysvětlení najdete postup vytvoření jednoduchého zprostředkovatele typu mazání, která poskytuje celou řadu typů, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-253">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="c7fd4-254">Tato část také vysvětlené koncept typ vymazání, včetně některé z výhod a nevýhod poskytnout vymazaných typy z typu poskytovatele a popsané reprezentace vymazaných typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-254">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>


## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="c7fd4-255">Typ zprostředkovatele, který používá statické parametry</span><span class="sxs-lookup"><span data-stu-id="c7fd4-255">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="c7fd4-256">Schopnost Parametrizace zprostředkovatelů typů pomocí statických dat umožňuje mnoho scénářů zajímavé, i v případech, kdy zprostředkovatel nepotřebuje přístup k žádným datům místní nebo vzdálené.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-256">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="c7fd4-257">V této části se dozvíte některé základní postupy pro uvedení společně takové zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-257">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>


### <a name="type-checked-regex-provider"></a><span data-ttu-id="c7fd4-258">Zaškrtnutí Regex – zprostředkovatel typu</span><span class="sxs-lookup"><span data-stu-id="c7fd4-258">Type Checked Regex Provider</span></span>

<span data-ttu-id="c7fd4-259">Představte si, že chcete implementovat typ zprostředkovatele pro regulární výrazy, který zabalí .NET <xref:System.Text.RegularExpressions.Regex> knihovny v rozhraní, které poskytuje následující záruky kompilace:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-259">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="c7fd4-260">Ověřuje, zda je platný regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-260">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="c7fd4-261">Poskytuje pojmenované vlastnosti na odpovídající položky, které jsou založeny na názvy všech skupin v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-261">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="c7fd4-262">V této části se dozvíte, jak vytvořit pomocí zprostředkovatelů typů `RegexTyped` zadejte, že poskytne tyto výhody parameterizes regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-262">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="c7fd4-263">Kompilátor nahlásí chybu, pokud zadanému vzoru není platný, a typ zprostředkovatele můžete rozbalit skupiny z vzoru tak, aby je můžete přistupovat pomocí vlastnosti shoduje s názvem.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-263">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="c7fd4-264">Při návrhu zprostředkovatele typ měli zvážit, jak by měla vypadat jeho zveřejněné rozhraní API pro koncové uživatele a jak se tento návrh přeloží pro kód .NET.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-264">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="c7fd4-265">Následující příklad ukazuje, jak používat takové rozhraní API jak získat komponenty kód oblasti:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-265">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="c7fd4-266">Následující příklad ukazuje, jak zprostředkovatel typu překládá těchto volání:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-266">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="c7fd4-267">Vezměte na vědomí následující body:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-267">Note the following points:</span></span>

- <span data-ttu-id="c7fd4-268">Představuje typ standardní Regex parametrizované `RegexTyped` typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-268">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="c7fd4-269">`RegexTyped` Konstruktor výsledkem volání konstruktoru Regex předávání v statický typ argumentu pro vzoru.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-269">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="c7fd4-270">Výsledky `Match` metoda jsou reprezentované pomocí standardní <xref:System.Text.RegularExpressions.Match> typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-270">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="c7fd4-271">Každou skupinu s názvem výsledkem zadané vlastnosti a přístupu k vlastnosti výsledkem použití indexer na shodu `Groups` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-271">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="c7fd4-272">Následující kód je základní logiku pro implementaci takové zprostředkovatele a v tomto příkladu vynechá přidání všech členů na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-272">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="c7fd4-273">Informace o každý přidaný člen najdete v příslušné části dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-273">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="c7fd4-274">Pro kód úplné stažení ukázky z [F # 3.0 ukázka Pack](https://fsharp3sample.codeplex.com) na webu Codeplex.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-274">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

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

<span data-ttu-id="c7fd4-275">Vezměte na vědomí následující body:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-275">Note the following points:</span></span>

- <span data-ttu-id="c7fd4-276">Typ zprostředkovatele přebírá dva parametry statické: `pattern`, což je povinný a `options`, (protože je výchozí hodnota je zadáno) jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-276">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="c7fd4-277">Po argumentů statické jsou zadány, můžete vytvořit instanci regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-277">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="c7fd4-278">Tato instance bude vyvolána výjimka, pokud regulární výraz je poškozený a tato chyba bude ohlášena uživatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-278">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="c7fd4-279">V rámci `DefineStaticParameters` zpětné volání, můžete definovat typ, který bude vrácen po jsou zadané argumenty.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-279">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="c7fd4-280">Tento kód nastaví `HideObjectMethods` na hodnotu true, aby prostředí IntelliSense zůstane efektivní.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-280">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="c7fd4-281">Tento atribut způsobí, že `Equals`, `GetHashCode`, `Finalize`, a `GetType` členy do potlačit ze seznamů IntelliSense pro zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-281">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="c7fd4-282">Používáte `obj` jako základní typ metody, ale budete používat `Regex` objektu jako runtime reprezentaci tohoto typu, jako další příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-282">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="c7fd4-283">Volání `Regex` vyvolá konstruktor <xref:System.ArgumentException> při regulární výraz není platný.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-283">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="c7fd4-284">Kompilátor zachytí výjimku a oznámí chybovou zprávu pro uživatele v době kompilace nebo v editoru Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-284">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="c7fd4-285">Tato výjimka umožňuje regulární výrazy, které má být ověřen bez spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-285">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="c7fd4-286">Typ definovaný nad není ještě užitečné, protože neobsahuje žádné smysluplný metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-286">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="c7fd4-287">Nejprve přidejte statického `IsMatch` metoda:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-287">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="c7fd4-288">Předchozí kód definuje metodu `IsMatch`, která přebírá řetězec jako vstup a vrátí `bool`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-288">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="c7fd4-289">Pouze složité část je použití `args` argument v rámci `InvokeCode` definice.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-289">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="c7fd4-290">V tomto příkladu `args` je seznam uvozovky zastupující argumenty této metodě.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-290">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="c7fd4-291">Pokud je metoda metody instance, představuje první argument `this` argument.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-291">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="c7fd4-292">Ale pro statickou metodu argumenty jsou všechny právě explicitní argumenty pro metodu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-292">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="c7fd4-293">Všimněte si, že typ uvozovkách hodnoty by měl odpovídat zadaný návratový typ (v tomto případě `bool`).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-293">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="c7fd4-294">Také Upozorňujeme, že tento kód používá `AddXmlDoc` metoda a ujistěte se také, že zadaná metoda je užitečná dokumentaci k nástroji, kterou můžete zadat pomocí IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-294">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="c7fd4-295">Dále přidejte metodu Match instance.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-295">Next, add an instance Match method.</span></span> <span data-ttu-id="c7fd4-296">Však tato metoda by měla vrátit hodnotu zadaný `Match` zadejte tak, aby se dalo přistupovat skupiny způsobem silného typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-296">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="c7fd4-297">Proto je nejdřív deklarovat `Match` typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-297">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="c7fd4-298">Protože tento typ závisí na vzor, který byl zadán jako statické argument, musí být tento typ vnořen v definici parametrizované typu:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-298">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="c7fd4-299">Potom přidáte jednu vlastnost typu shodu pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-299">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="c7fd4-300">V době běhu je vyjádřené shody <xref:System.Text.RegularExpressions.Match> hodnotu, takže musíte použít uvozovky, která definuje vlastnost <xref:System.Text.RegularExpressions.Match.Groups> indexované vlastnosti získat relevantní skupiny.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-300">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="c7fd4-301">Znovu si všimněte, že přidáváte dokumentace XML do zadané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-301">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="c7fd4-302">Také Upozorňujeme, že vlastnost může číst, pokud `GetterCode` funkce je k dispozici, a vlastnost lze zapisovat, pokud `SetterCode` funkce je k dispozici, proto výsledné vlastnost je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-302">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="c7fd4-303">Nyní můžete vytvořit metody instance, která vrátí hodnotu tohoto `Match` typu:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-303">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="c7fd4-304">Vzhledem k tomu, že vytváříte metodu instance `args.[0]` představuje `RegexTyped` instanci, na kterém metoda je volána, a `args.[1]` je vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-304">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="c7fd4-305">Nakonec zadejte konstruktor, aby bylo možné vytvořit instancí zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-305">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="c7fd4-306">Konstruktor vymaže jenom k vytvoření standardní instance .NET Regex, která je znovu zabalená na objekt, protože `obj` je výmaz zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-306">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="c7fd4-307">S touto změnou využití ukázkové rozhraní API, které zadaná v dřívější tématu funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-307">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="c7fd4-308">Následující kód je úplný a poslední:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-308">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="c7fd4-309">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="c7fd4-309">Key Lessons</span></span>

<span data-ttu-id="c7fd4-310">V této části Vysvětlení způsobu vytváření typ zprostředkovatele, který funguje na jeho statické parametry.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-310">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="c7fd4-311">Zprostředkovatel zkontroluje statický parametr a poskytuje operace založené na jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-311">The provider checks the static parameter and provides operations based on its value.</span></span>


## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="c7fd4-312">Typ zprostředkovatele, který je zálohovaný díky místní Data</span><span class="sxs-lookup"><span data-stu-id="c7fd4-312">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="c7fd4-313">Často můžete chtít zprostředkovatelů typů k dispozici rozhraní API podle pouze statické parametry, ale také informace z místní nebo vzdálené systémy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-313">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="c7fd4-314">Tato část popisuje typ zprostředkovatele, které jsou založeny na místní data, jako je například místní datové soubory.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-314">This section discusses type providers that are based on local data, such as local data files.</span></span>


### <a name="simple-csv-file-provider"></a><span data-ttu-id="c7fd4-315">Jednoduché CSV – zprostředkovatel souboru</span><span class="sxs-lookup"><span data-stu-id="c7fd4-315">Simple CSV File Provider</span></span>

<span data-ttu-id="c7fd4-316">Jako jednoduchý příklad zvažte zprostředkovatele typů pro přístup k vědeckých dat ve formátu hodnoty oddělené čárkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-316">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="c7fd4-317">V této části se předpokládá, že soubory CSV obsahovat řádek záhlaví, za nímž následuje data s plovoucí desetinnou, jak ukazuje následující tabulka:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-317">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>


|<span data-ttu-id="c7fd4-318">Vzdálenost (monitorování)</span><span class="sxs-lookup"><span data-stu-id="c7fd4-318">Distance (meter)</span></span>|<span data-ttu-id="c7fd4-319">Čas (sekundy)</span><span class="sxs-lookup"><span data-stu-id="c7fd4-319">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="c7fd4-320">50.0</span><span class="sxs-lookup"><span data-stu-id="c7fd4-320">50.0</span></span>|<span data-ttu-id="c7fd4-321">3.7</span><span class="sxs-lookup"><span data-stu-id="c7fd4-321">3.7</span></span>|
|<span data-ttu-id="c7fd4-322">100.0</span><span class="sxs-lookup"><span data-stu-id="c7fd4-322">100.0</span></span>|<span data-ttu-id="c7fd4-323">5.2</span><span class="sxs-lookup"><span data-stu-id="c7fd4-323">5.2</span></span>|
|<span data-ttu-id="c7fd4-324">150.0</span><span class="sxs-lookup"><span data-stu-id="c7fd4-324">150.0</span></span>|<span data-ttu-id="c7fd4-325">6.4</span><span class="sxs-lookup"><span data-stu-id="c7fd4-325">6.4</span></span>|

<span data-ttu-id="c7fd4-326">V této části ukazuje, jak poskytnout typ, který vám pomůže získat řádky s `Distance` vlastnost typu `float<meter>` a `Time` vlastnost typu `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-326">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="c7fd4-327">Pro jednoduchost jsou provedeny následující předpoklady:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-327">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="c7fd4-328">Názvy záhlaví jsou buď bez měrné jednotky nebo tvar "Název" (jednotky) a nesmí obsahovat čárky.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-328">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="c7fd4-329">Všechny jednotky systém mezinárodní (SI), jako jsou jednotky [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames – modul (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modul definuje.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-329">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="c7fd4-330">Jednotky jsou všechny jednoduché (například monitorovat) místo složené (například, měření za sekundu).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-330">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="c7fd4-331">Všechny sloupce obsahují data s plovoucí desetinnou.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-331">All columns contain floating point data.</span></span>

<span data-ttu-id="c7fd4-332">Obsáhlejší zprostředkovatele by povolte tato omezení.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-332">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="c7fd4-333">Prvním krokem je znovu vzít v úvahu, jak by měla vypadat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-333">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="c7fd4-334">Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-334">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="c7fd4-335">V takovém případě by měl kompilátor převést těchto volání na něco podobného jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-335">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="c7fd4-336">Optimální překlad bude vyžadovat typ zprostředkovatele, který má definovat reálné číslo `CsvFile` typu v sestavení typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-336">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="c7fd4-337">Zprostředkovatelé typů často závisí na několik pomocná typy a metody můžete zabalit důležité logiku.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-337">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="c7fd4-338">Protože míry jsou vymazány za běhu, můžete použít `float[]` jako typ vymazaných pro řádek.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-338">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="c7fd4-339">Kompilátor počítat různé sloupce s typy jinou míru.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-339">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="c7fd4-340">Například z prvního sloupce v našem příkladu má typ `float<meter>`, a druhá má `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-340">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="c7fd4-341">Však může zůstat vymazaných reprezentace poměrně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-341">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="c7fd4-342">Následující kód ukazuje základní implementaci.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-342">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="c7fd4-343">Vezměte na vědomí následující body o implementaci:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-343">Note the following points about the implementation:</span></span>

- <span data-ttu-id="c7fd4-344">Přetížené konstruktory povolit původní soubor nebo ten, který má stejné schéma čtení.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-344">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="c7fd4-345">Tento vzor je běžné při zapisovat zprostředkovatele typů pro místní nebo vzdálené datové zdroje, a tento vzor umožňuje místního souboru, který se má použít jako šablonu pro vzdálená data.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-345">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="c7fd4-346">Můžete použít [typeproviderconfig –](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) hodnotu, která je v předaný konstruktoru zprostředkovatele typ k vyřešení relativních názvů souborů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-346">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="c7fd4-347">Můžete použít `AddDefinitionLocation` metoda zadat umístění zadané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-347">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="c7fd4-348">Proto pokud používáte `Go To Definition` u zadané vlastnosti, otevře se soubor CSV v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-348">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="c7fd4-349">Můžete použít `ProvidedMeasureBuilder` typ k vyhledání jednotek SI a ke generování odpovídajícího `float<_>` typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-349">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="c7fd4-350">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="c7fd4-350">Key Lessons</span></span>

<span data-ttu-id="c7fd4-351">Tato část vysvětluje vytvoření zprostředkovatele typů pro místní zdroj dat s jednoduché schéma, které se nachází v samotném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-351">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>


## <a name="going-further"></a><span data-ttu-id="c7fd4-352">Budete pokračovat</span><span class="sxs-lookup"><span data-stu-id="c7fd4-352">Going Further</span></span>

<span data-ttu-id="c7fd4-353">Následující části obsahují návrhy pro další studie.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-353">The following sections include suggestions for further study.</span></span>


### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="c7fd4-354">Podívejte se na zkompilovaný kód pro vymazaných typy</span><span class="sxs-lookup"><span data-stu-id="c7fd4-354">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="c7fd4-355">Získáte představu, jak použití zprostředkovatele typu odpovídá kód, který je vygenerované, podívejte se na následující funkce pomocí `HelloWorldTypeProvider` používané v tomto tématu výše.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-355">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="c7fd4-356">Zde je výsledný kód decompiled pomocí ildasm.exe bitové kopie:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-356">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="c7fd4-357">Jak ukazuje příklad, všechny zmínky o typ `Type1` a `InstanceProperty` vlastnost byl vymazán, a operace pouze na typy runtime související se situací.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-357">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>


### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="c7fd4-358">Návrh a konvence pojmenování pro zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="c7fd4-358">Design and Naming Conventions for Type Providers</span></span>
<span data-ttu-id="c7fd4-359">Sledujte následující konvence při vytváření zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-359">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="c7fd4-360">**Zprostředkovatelé pro připojení protokoly** obecně názvy většina zprostředkovatele – knihovny DLL pro data a služby připojení protokoly, jako je například OData nebo SQL připojení, končit `TypeProvider` nebo `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-360">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="c7fd4-361">Například použijte název knihovny DLL, která se podobá následující řetězec:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-361">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="c7fd4-362">Ujistěte se, že vaše zadané typy jsou členy odpovídající oboru názvů a připojení protokolu, který jste implementovali:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-362">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="c7fd4-363">**Nástroje zprostředkovatele pro obecné kódování**.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-363">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="c7fd4-364">Nástroj Typ zprostředkovatele, například pro regulární výrazy typ zprostředkovatele, může být součástí základní knihovny, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-364">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="c7fd4-365">V takovém případě zadaný typ objeví v odpovídajícím bodě podle normální .NET návrhu konvence:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-365">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="c7fd4-366">**Zdroje dat typu singleton**.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-366">**Singleton Data Sources**.</span></span> <span data-ttu-id="c7fd4-367">Někteří poskytovatelé typ připojení ke zdroji dat jeden vyhrazený a zadejte jenom data.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-367">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="c7fd4-368">V takovém případě by měl vyřadit `TypeProvider` přípona a používat běžné konvence pro pojmenování .NET:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-368">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="c7fd4-369">Další informace najdete v tématu `GetConnection` návrh názvů, který je popsán dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-369">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>


### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="c7fd4-370">Vzory návrhu pro zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="c7fd4-370">Design Patterns for Type Providers</span></span>

<span data-ttu-id="c7fd4-371">Následující části popisují vzorů návrhu, které můžete použít při vytváření zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-371">The following sections describe design patterns you can use when authoring type providers.</span></span>


#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="c7fd4-372">Vzor návrhu GetConnection</span><span class="sxs-lookup"><span data-stu-id="c7fd4-372">The GetConnection Design Pattern</span></span>
<span data-ttu-id="c7fd4-373">Většina zprostředkovatelů typů zasílány používat `GetConnection` vzor, který je používán typ zprostředkovatele v FSharp.Data.TypeProviders.dll, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-373">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="c7fd4-374">Zprostředkovatelé typů zálohován vzdálených dat a služby</span><span class="sxs-lookup"><span data-stu-id="c7fd4-374">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="c7fd4-375">Než vytvoříte typ zprostředkovatele, který je zálohovaný díky vzdálených dat a služby, musíte zvážit řadu problémů, které jsou obsaženy v připojených programování.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-375">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="c7fd4-376">Tyto problémy patří následující aspekty:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-376">These issues include the following considerations:</span></span>

- <span data-ttu-id="c7fd4-377">Schéma mapování</span><span class="sxs-lookup"><span data-stu-id="c7fd4-377">schema mapping</span></span>

- <span data-ttu-id="c7fd4-378">liveness a zneplatnění případě změny schématu</span><span class="sxs-lookup"><span data-stu-id="c7fd4-378">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="c7fd4-379">ukládání do mezipaměti schématu</span><span class="sxs-lookup"><span data-stu-id="c7fd4-379">schema caching</span></span>

- <span data-ttu-id="c7fd4-380">asynchronní implementace operací přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="c7fd4-380">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="c7fd4-381">Podpora dotazů, včetně dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="c7fd4-381">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="c7fd4-382">pověření a ověřování</span><span class="sxs-lookup"><span data-stu-id="c7fd4-382">credentials and authentication</span></span>

<span data-ttu-id="c7fd4-383">V tomto tématu není prozkoumat tyto další problémy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-383">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="c7fd4-384">Další techniky pro vytváření obsahu</span><span class="sxs-lookup"><span data-stu-id="c7fd4-384">Additional Authoring Techniques</span></span>

<span data-ttu-id="c7fd4-385">Když píšete vlastní typ zprostředkovatele, můžete použít následující další techniky.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-385">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="c7fd4-386">Vytváření typů a členů na vyžádání</span><span class="sxs-lookup"><span data-stu-id="c7fd4-386">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="c7fd4-387">Rozhraní API ProvidedType má odložené verzích přidávat členy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-387">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="c7fd4-388">Tyto verze se používají k vytvoření prostorů na vyžádání typů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-388">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="c7fd4-389">Typy polí a konkretizací obecného typu</span><span class="sxs-lookup"><span data-stu-id="c7fd4-389">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="c7fd4-390">Zkontrolujte zadané členy (jehož podpisy zahrnují typy polí, typy byref a instancí možnosti obecné typy) s použitím normální `MakeArrayType`, `MakePointerType`, a `MakeGenericType` na jakoukoli instanci systému <xref:System.Type>, včetně `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-390">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="c7fd4-391">V některých případech možná budete muset použít Pomocník `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-391">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="c7fd4-392">Najdete v článku [dokumentaci k sadě SDK typ zprostředkovatele](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-392">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="c7fd4-393">Poskytnutí jednotek měr poznámky</span><span class="sxs-lookup"><span data-stu-id="c7fd4-393">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="c7fd4-394">Rozhraní API ProvidedTypes poskytuje pomocné rutiny pro zajištění měr poznámky.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-394">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="c7fd4-395">Chcete-li například zadat typ `float<kg>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-395">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="c7fd4-396">K poskytování typ `Nullable<decimal<kg/m^2>>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-396">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="c7fd4-397">Přístup k projektu místní nebo skriptu místní prostředky</span><span class="sxs-lookup"><span data-stu-id="c7fd4-397">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="c7fd4-398">Je možné přidělit každou instanci zprostředkovatele typů `TypeProviderConfig` hodnotu během vytváření.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-398">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="c7fd4-399">Tato hodnota obsahuje "řešení složka" pro poskytovatele (který je složka projektu kompilace nebo adresář, který obsahuje skript), seznam odkazovaná sestavení a další informace.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-399">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="c7fd4-400">Zneplatnění</span><span class="sxs-lookup"><span data-stu-id="c7fd4-400">Invalidation</span></span>

<span data-ttu-id="c7fd4-401">Zprostředkovatelé může být spojeno zneplatnění signály oznámit služba jazyka F #, který možná změnil předpoklady schématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-401">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="c7fd4-402">Když dojde k zneplatnění, typecheck je znovu, pokud zprostředkovatel je hostované v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-402">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="c7fd4-403">Tento signál se ignoruje, pokud zprostředkovatel je hostovaná v F # interaktivní nebo kompilátoru F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-403">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="c7fd4-404">Ukládání do mezipaměti informace o schématu</span><span class="sxs-lookup"><span data-stu-id="c7fd4-404">Caching Schema Information</span></span>

<span data-ttu-id="c7fd4-405">Zprostředkovatelé musí mezipaměti často přístup k informacím o schématu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-405">Providers must often cache access to schema information.</span></span> <span data-ttu-id="c7fd4-406">Data uložená v mezipaměti by měly být uložené pomocí názvu souboru, který je přiřazen jako statický parametr nebo jako uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-406">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="c7fd4-407">Je například ukládání do mezipaměti schématu `LocalSchemaFile` ve zprostředkovatelích typu v parametru `FSharp.Data.TypeProviders` sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-407">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="c7fd4-408">Při provádění těchto poskytovatelů přesměruje tento statický parametr typ zprostředkovatele, který má používat informace o schématu do zadaného místního souboru místo přístup ke zdroji dat přes síť.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-408">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="c7fd4-409">Pokud chcete použít informace uložené v mezipaměti schématu, musíte taky nastavit statický parametr `ForceUpdate` k `false`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-409">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="c7fd4-410">Podobným způsobem můžete použít k povolení přístupu k datům online a offline.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-410">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="c7fd4-411">Základní sestavení</span><span class="sxs-lookup"><span data-stu-id="c7fd4-411">Backing Assembly</span></span>

<span data-ttu-id="c7fd4-412">Při sestavování `.dll` nebo `.exe` souboru, soubor .dll zálohování pro generovaný typy je staticky propojené do výsledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-412">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="c7fd4-413">Tento odkaz se vytvoří zkopírováním definic typů Intermediate Language (IL) a všechny spravované prostředky z základní sestavení do konečné sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-413">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="c7fd4-414">Při použití F # interaktivní, soubor .dll zálohování nebude zkopírován a místo toho je načíst přímo do procesu F # interaktivní.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-414">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="c7fd4-415">Výjimky a Diagnostika z zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="c7fd4-415">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="c7fd4-416">Všechny používá všech členů ze zadané typy může vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-416">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="c7fd4-417">Ve všech případech Pokud zprostředkovatel typu, vyvolá výjimku, kompilátoru hostitele atributy chyba na konkrétní typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-417">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="c7fd4-418">Typ zprostředkovatele výjimky by nikdy vést k chybám interní kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-418">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="c7fd4-419">Zprostředkovatelé typů nemůžete hlásit upozornění.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-419">Type providers can't report warnings.</span></span>

- <span data-ttu-id="c7fd4-420">Pokud zprostředkovatele typů hostovaný v kompilátoru F #, F # vývojového prostředí nebo F # interaktivní, jsou zachyceny všechny výjimky z tohoto zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-420">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="c7fd4-421">Vlastnosti zprávy je vždy text chyby a zobrazí se žádné trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-421">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="c7fd4-422">Pokud se chystáte způsobí výjimku, můžete vyvolat následující příklady: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-422">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="c7fd4-423">Poskytnutí generovaného typy</span><span class="sxs-lookup"><span data-stu-id="c7fd4-423">Providing Generated Types</span></span>

<span data-ttu-id="c7fd4-424">Tento dokument, pokud má vysvětlené jak poskytnout vymazaných typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-424">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="c7fd4-425">Mechanismus zprostředkovatele typu v F # můžete také použít k poskytnutí generovaného typů, které jsou přidány jako skutečné definice typů .NET do programu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-425">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="c7fd4-426">Můžete musí odkazovat na generovaného poskytnout typy pomocí definice typu.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-426">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="c7fd4-427">Kód pomocného objektu ProvidedTypes 0,2, který je součástí verze F # 3.0 má omezenou podporu pro zajištění generovaného typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-427">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="c7fd4-428">Pro definici typu generované musí platit následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-428">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="c7fd4-429">`isErased` musí být nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-429">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="c7fd4-430">Vygenerovaný typ musí být přidán do nově vytvořený `ProvidedAssembly()`, který představuje kontejner pro generovaný kód fragmenty.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-430">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="c7fd4-431">Zprostředkovatel musí mít sestavení, který má soubor .dll .NET skutečné zálohování s odpovídající soubor DLL na disku.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-431">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>


## <a name="rules-and-limitations"></a><span data-ttu-id="c7fd4-432">Pravidla a omezení</span><span class="sxs-lookup"><span data-stu-id="c7fd4-432">Rules and Limitations</span></span>

<span data-ttu-id="c7fd4-433">Když píšete zprostředkovatelů typů, uvědomte si následující pravidla a omezení.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-433">When you write type providers, keep the following rules and limitations in mind.</span></span>


### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="c7fd4-434">Zadané typy musí být dosažitelný</span><span class="sxs-lookup"><span data-stu-id="c7fd4-434">Provided types must be reachable</span></span>

<span data-ttu-id="c7fd4-435">Všechny zadané typy by měly být dostupné z typů-nested.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-435">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="c7fd4-436">-Nested typy jsou uvedeny ve volání `TypeProviderForNamespaces` konstruktoru nebo volání `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-436">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="c7fd4-437">Například, pokud zprostředkovatel poskytuje typu `StaticClass.P : T`, ujistěte se, že je T-nested typ nebo vnořené v rámci jedné.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-437">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="c7fd4-438">Například někteří poskytovatelé mít statická třída jako `DataTypes` obsahující tyto `T1, T2, T3, ...` typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-438">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="c7fd4-439">Chyba, jinak hodnota říká, že našel se odkaz na typ T v sestavení A, ale typ nebyl nalezen v této sestavě.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-439">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="c7fd4-440">Pokud tato chyba se zobrazí, ověřte, že všechny podtypů lze přejít z typy zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-440">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="c7fd4-441">Poznámka: Tyto `T1, T2, T3...` typy jsou označovány jako *na průběžně* typy.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-441">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="c7fd4-442">Nezapomeňte zahrnout je přístupné oboru názvů nebo nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-442">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="c7fd4-443">Omezení typu mechanismu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="c7fd4-443">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="c7fd4-444">Typ zprostředkovatele mechanismus v F # má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-444">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="c7fd4-445">Základní infrastruktury pro zprostředkovatelů typů v jazyce F # nepodporuje zadaný obecné typy nebo, pokud obecné metody.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-445">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="c7fd4-446">Tento mechanismus nepodporuje vnořené typy s statické parametry.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-446">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="c7fd4-447">Tipy pro vývoj</span><span class="sxs-lookup"><span data-stu-id="c7fd4-447">Development Tips</span></span>

<span data-ttu-id="c7fd4-448">Následující tipy mohou být užitečné během procesu vývoje.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-448">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="c7fd4-449">Spustit dvě instance sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7fd4-449">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="c7fd4-450">Můžete vytvořit typ zprostředkovatele v jedné instance a testování zprostředkovatele v dalších, protože test IDE bude trvat zámek na soubor .dll, který zabrání se znovu sestavit typ zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-450">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="c7fd4-451">Proto je třeba nejprve zavřít druhou instanci sady Visual Studio, zatímco zprostředkovatele je vytvořen v první instance, a pak musí znovu otevřete druhou instanci po zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-451">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="c7fd4-452">Ladění zprostředkovatelů typů pomocí volání fsc.exe</span><span class="sxs-lookup"><span data-stu-id="c7fd4-452">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="c7fd4-453">Zprostředkovatelé typů můžete vyvolat pomocí následující nástroje:</span><span class="sxs-lookup"><span data-stu-id="c7fd4-453">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="c7fd4-454">FSC.exe (příkazového řádku kompilátor jazyka F #)</span><span class="sxs-lookup"><span data-stu-id="c7fd4-454">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="c7fd4-455">fsi.exe (F # interaktivní kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="c7fd4-455">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="c7fd4-456">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="c7fd4-456">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="c7fd4-457">Zprostředkovatelé typů můžete ladit často snadno pomocí fsc.exe na soubor skriptu test (například script.fsx).</span><span class="sxs-lookup"><span data-stu-id="c7fd4-457">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="c7fd4-458">Ladicí program z příkazového řádku můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-458">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="c7fd4-459">Protokolování tiskových stdout můžete použít.</span><span class="sxs-lookup"><span data-stu-id="c7fd4-459">You can use print-to-stdout logging.</span></span>


## <a name="see-also"></a><span data-ttu-id="c7fd4-460">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7fd4-460">See Also</span></span>

* [<span data-ttu-id="c7fd4-461">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="c7fd4-461">Type Providers</span></span>](index.md)

* [<span data-ttu-id="c7fd4-462">Typ poskytovatele sady SDK</span><span class="sxs-lookup"><span data-stu-id="c7fd4-462">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)

