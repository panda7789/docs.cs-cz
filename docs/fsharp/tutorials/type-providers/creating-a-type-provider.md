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
ms.openlocfilehash: a2db07c4f5688aece212681af40d69c377f6fa4a
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="tutorial-creating-a-type-provider"></a><span data-ttu-id="7da92-104">Kurz: Vytvoření zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="7da92-104">Tutorial: Creating a Type Provider</span></span>

<span data-ttu-id="7da92-105">Typ zprostředkovatele mechanismus v F # je významnou část podporuje programování bohaté informace.</span><span class="sxs-lookup"><span data-stu-id="7da92-105">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="7da92-106">Tento kurz vysvětluje, jak vytvořit vlastní typ zprostředkovatele jste s návodem vývoj několik poskytovatelů jednoduchý typ pro ilustraci se základními koncepty.</span><span class="sxs-lookup"><span data-stu-id="7da92-106">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="7da92-107">Další informace o typu poskytovatele mechanismus v F # najdete v tématu [zprostředkovatelů typů](index.md).</span><span class="sxs-lookup"><span data-stu-id="7da92-107">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="7da92-108">Ekosystému F # obsahuje řadu typ zprostředkovatele pro běžně používané služby dat na Internet a enterprise.</span><span class="sxs-lookup"><span data-stu-id="7da92-108">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="7da92-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7da92-109">For example:</span></span>

- <span data-ttu-id="7da92-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) obsahuje typ zprostředkovatele pro JSON, XML, CSV a HTML dokumentu formáty</span><span class="sxs-lookup"><span data-stu-id="7da92-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats</span></span>

- <span data-ttu-id="7da92-111">[SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje dotazy pro tyto zdroje dat silného typu přístup k databázím SQL prostřednictvím objektu mapování a F # LINQ.</span><span class="sxs-lookup"><span data-stu-id="7da92-111">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="7da92-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) obsahuje sadu zprostředkovatelů typu pro model com relačních operátorů čas zaškrtnutí vložení T-SQL v jazyce F #</span><span class="sxs-lookup"><span data-stu-id="7da92-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for com,pile-time checked embedding of T-SQL in F#</span></span>

- <span data-ttu-id="7da92-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sada zprostředkovatelů typů pro použití pouze s programováním rozhraní .NET Framework pro přístup ke službám dat SQL, rozhraní Entity Framework, OData a WSDL.</span><span class="sxs-lookup"><span data-stu-id="7da92-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="7da92-114">V případě potřeby můžete vytvořit vlastní typ zprostředkovatele nebo typ zprostředkovatele, ostatní vytvořené, můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="7da92-114">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="7da92-115">Vaše organizace může mít například služba data, která poskytuje velké a rostoucí počet sad dat s názvem, každou s vlastním schématem stabilní data.</span><span class="sxs-lookup"><span data-stu-id="7da92-115">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="7da92-116">Můžete vytvořit typ zprostředkovatele, který čte schémata a zobrazí aktuální sady dat programátorů způsobem silného typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-116">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="7da92-117">Než začnete</span><span class="sxs-lookup"><span data-stu-id="7da92-117">Before You Start</span></span>

<span data-ttu-id="7da92-118">Tento typ poskytovatele mechanismus je primárně určený pro vložení stabilní data a informace prostory služby do programovací prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="7da92-118">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="7da92-119">Tento mechanismus není určená pro vložení mezery informace jejichž schématu se změní při spuštění programu způsoby, které jsou relevantní pro logiku programu.</span><span class="sxs-lookup"><span data-stu-id="7da92-119">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="7da92-120">Navíc tento mechanismus není určená pro intra jazyk meta-programování, i když tuto doménu obsahuje některé platné používá.</span><span class="sxs-lookup"><span data-stu-id="7da92-120">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="7da92-121">Tento mechanismus byste měli použít pouze v případě potřeby a kde vývoj zprostředkovatele typů výsledkem velmi vysokou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7da92-121">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="7da92-122">Vyhněte se zápis typ zprostředkovatele, kde není k dispozici schéma.</span><span class="sxs-lookup"><span data-stu-id="7da92-122">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="7da92-123">Podobně, neměli byste zápis zprostředkovatele typů, kde je běžný (nebo i existující) by stačit knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="7da92-123">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="7da92-124">Než začnete, může odpovědět na tyto otázky:</span><span class="sxs-lookup"><span data-stu-id="7da92-124">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="7da92-125">Máte schéma pro zdroj informace?</span><span class="sxs-lookup"><span data-stu-id="7da92-125">Do you have a schema for your information source?</span></span> <span data-ttu-id="7da92-126">Pokud ano, co je mapování do F # a systém typů .NET?</span><span class="sxs-lookup"><span data-stu-id="7da92-126">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="7da92-127">Můžete použít existující API (dynamicky zadávaných) jako výchozí bod týkající se vaší implementace?</span><span class="sxs-lookup"><span data-stu-id="7da92-127">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="7da92-128">Bude vám a vaší organizaci mít dostatek používá typ zprostředkovatele, který má smysl zkontrolujte jejich zápisu?</span><span class="sxs-lookup"><span data-stu-id="7da92-128">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="7da92-129">Běžné knihovny .NET by vyhovovala vašim potřebám?</span><span class="sxs-lookup"><span data-stu-id="7da92-129">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="7da92-130">Kolik změní schéma?</span><span class="sxs-lookup"><span data-stu-id="7da92-130">How much will your schema change?</span></span>

- <span data-ttu-id="7da92-131">Se změní při kódování?</span><span class="sxs-lookup"><span data-stu-id="7da92-131">Will it change during coding?</span></span>

- <span data-ttu-id="7da92-132">Se změní mezi kódování relace?</span><span class="sxs-lookup"><span data-stu-id="7da92-132">Will it change between coding sessions?</span></span>

- <span data-ttu-id="7da92-133">Se změní při spuštění programu?</span><span class="sxs-lookup"><span data-stu-id="7da92-133">Will it change during program execution?</span></span>

<span data-ttu-id="7da92-134">Zprostředkovatelé typů jsou nejvhodnější pro situacích, kde je stabilní za běhu a po dobu životnosti zkompilovaný kód schématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-134">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>


## <a name="a-simple-type-provider"></a><span data-ttu-id="7da92-135">Jednoduchý typ zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="7da92-135">A Simple Type Provider</span></span>

<span data-ttu-id="7da92-136">Tato ukázka je podobná ukázky Samples.HelloWorldTypeProvider `examples` adresář [F # typ poskytovatele sady SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="7da92-136">This sample is Samples.HelloWorldTypeProvider similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="7da92-137">Zprostředkovatel zpřístupní "typ prostor", který obsahuje 100 vymazaných typů, jak ukazuje následující kód pomocí syntaxe podpis F # a vynechat podrobnosti pro všechny kromě `Type1`.</span><span class="sxs-lookup"><span data-stu-id="7da92-137">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="7da92-138">Další informace o typech vymazaných najdete v tématu [podrobnosti o vymazat zadané typy](#details-about-erased-provided-types) dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-138">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="7da92-139">Všimněte si, že se staticky označuje sadu typy a členy zadané.</span><span class="sxs-lookup"><span data-stu-id="7da92-139">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="7da92-140">V tomto příkladu není využít možnost zprostředkovatelů zadejte typy, které jsou závislé na schéma.</span><span class="sxs-lookup"><span data-stu-id="7da92-140">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="7da92-141">Implementace zprostředkovatele typu popsané v následujícím kódu a podrobnosti jsou popsané v dalších částech tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-141">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>


>[!WARNING] 
<span data-ttu-id="7da92-142">Mohou existovat rozdíly mezi tento kód a online ukázky.</span><span class="sxs-lookup"><span data-stu-id="7da92-142">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="7da92-143">Pro tohoto zprostředkovatele použijte otevřete samostatnou instanci sady Visual Studio 2012, vytvořit skript F # a potom přidejte odkaz na poskytovateli z vašeho skriptu pomocí #r jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="7da92-143">To use this provider, open a separate instance of Visual Studio 2012, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="7da92-144">Poté vyhledejte typy v části `Samples.HelloWorldTypeProvider` obor názvů, který generuje typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-144">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="7da92-145">Než můžete znovu zkompiluje zprostředkovatele, ujistěte se, uzavřít všechny instance Visual Studio a F # interaktivní, které používají zprostředkovatele knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="7da92-145">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="7da92-146">Chyby sestavení, jinak hodnota dojde, protože zamkne výstupní knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="7da92-146">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="7da92-147">Chcete-li ladit tento zprostředkovatel pomocí tiskové příkazy, zkontrolujte skript, který zveřejňuje potížím s poskytovatelem a pak použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="7da92-147">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="7da92-148">Chcete-li ladit tento zprostředkovatel pomocí sady Visual Studio, otevřete příkazový řádek sady Visual Studio s přihlašovacími údaji správce a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7da92-148">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="7da92-149">Jako alternativu, otevřete Visual Studio, otevřete nabídku ladění, zvolte `Debug/Attach to process…`a připojte k jiné `devenv` procesu, kde provádíte změny vašeho skriptu.</span><span class="sxs-lookup"><span data-stu-id="7da92-149">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="7da92-150">Pomocí této metody můžete snadno vybrat konkrétní logiku ve zprostředkovateli typu interaktivně zadáním výrazy do druhé instance (s plnou technologie IntelliSense a další funkce).</span><span class="sxs-lookup"><span data-stu-id="7da92-150">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="7da92-151">Pouze můj kód ladění lépe identifikovat chyby v generovaného kódu můžete zakázat.</span><span class="sxs-lookup"><span data-stu-id="7da92-151">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="7da92-152">Informace o tom, jak povolit nebo zakázat tuto funkci najdete v tématu [procházení kódu s ladicím programem](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="7da92-152">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="7da92-153">Navíc můžete také nastavit první odpovídající výjimce zachytávání otevřením `Debug` nabídky a pak vyberete `Exceptions` nebo výběrem klávesy Ctrl + Alt + E otevřete `Exceptions` dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7da92-153">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="7da92-154">V tomto dialogu pod `Common Language Runtime Exceptions`, vyberte `Thrown` zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="7da92-154">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>


### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="7da92-155">Implementace zprostředkovatele typu</span><span class="sxs-lookup"><span data-stu-id="7da92-155">Implementation of the Type Provider</span></span>

<span data-ttu-id="7da92-156">Tato část vás provede procesem na hlavní části implementace typ zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-156">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="7da92-157">Nejprve definovat typ pro vlastní typ zprostředkovatele sám sebe:</span><span class="sxs-lookup"><span data-stu-id="7da92-157">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="7da92-158">Tento typ musí být veřejné a označte ji s [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) tak, aby kompilátor rozpozná typ zprostředkovatele, když samostatného projektu F # odkazuje na sestavení, které obsahuje typ atributu.</span><span class="sxs-lookup"><span data-stu-id="7da92-158">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="7da92-159">*Konfigurace* parametr je volitelný a pokud existuje, obsahuje kontextové konfigurační informace pro instanci zprostředkovatele typu, která vytvoří kompilátor jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="7da92-159">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="7da92-160">V dalším kroku implementujete [itypeprovider –](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7da92-160">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="7da92-161">V takovém případě použijete `TypeProviderForNamespaces` typu z `ProvidedTypes` rozhraní API jako základní typ.</span><span class="sxs-lookup"><span data-stu-id="7da92-161">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="7da92-162">Tento typ pomocné rutiny můžete poskytnout soubor konečné například zadaný obory názvů, z nichž každý přímo obsahuje omezený počet pevné, například zadané typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-162">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="7da92-163">V tomto kontextu zprostředkovatele *například* generuje typy, i když nejsou potřeba nebo použít.</span><span class="sxs-lookup"><span data-stu-id="7da92-163">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="7da92-164">V dalším kroku definovat místní privátní hodnoty, které určují obor názvů pro zadané typy a najít sestavení zprostředkovatele typu sám sebe.</span><span class="sxs-lookup"><span data-stu-id="7da92-164">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="7da92-165">Toto sestavení se později používá jako logické nadřazený typ vymazaných typů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7da92-165">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="7da92-166">Dál vytvořte funkci zajistit každý typ Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="7da92-166">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="7da92-167">Tato funkce je podrobně popsány dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-167">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="7da92-168">Dále generovat 100 zadané typy:</span><span class="sxs-lookup"><span data-stu-id="7da92-168">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="7da92-169">V dalším kroku přidejte typy jako zadaný obor názvů:</span><span class="sxs-lookup"><span data-stu-id="7da92-169">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="7da92-170">Nakonec přidejte atribut sestavení, který označuje, že vytváříte zprostředkovatele typů knihovny DLL:</span><span class="sxs-lookup"><span data-stu-id="7da92-170">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="7da92-171">Poskytuje jeden typ a její členy</span><span class="sxs-lookup"><span data-stu-id="7da92-171">Providing One Type And Its Members</span></span>

<span data-ttu-id="7da92-172">`makeOneProvidedType` Funkce neodpovídá skutečné pracovní poskytnout jeden z typů.</span><span class="sxs-lookup"><span data-stu-id="7da92-172">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="7da92-173">Tento krok popisuje implementace této funkce.</span><span class="sxs-lookup"><span data-stu-id="7da92-173">This step explains the implementation of this function.</span></span> <span data-ttu-id="7da92-174">Nejprve vytvořte zadaný typ (například Type1, když n = 1, nebo Type57, když n = 57).</span><span class="sxs-lookup"><span data-stu-id="7da92-174">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="7da92-175">Nezapomeňte přitom následující body:</span><span class="sxs-lookup"><span data-stu-id="7da92-175">You should note the following points:</span></span>

- <span data-ttu-id="7da92-176">To, pokud je typ vymazat.</span><span class="sxs-lookup"><span data-stu-id="7da92-176">This provided type is erased.</span></span>  <span data-ttu-id="7da92-177">Protože jste označení, že je základní typ `obj`, instancí se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7da92-177">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="7da92-178">Když zadáte typu-nested, musíte zadat sestavení a oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7da92-178">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="7da92-179">Pro vymazaných typy sestavení by měla být sestavení zprostředkovatele typu sám sebe.</span><span class="sxs-lookup"><span data-stu-id="7da92-179">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="7da92-180">Dál přidejte dokumentace XML typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-180">Next, add XML documentation to the type.</span></span> <span data-ttu-id="7da92-181">Tato dokumentace je zpožděno, to znamená, počítaný na vyžádání, pokud se vyžaduje kompilátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="7da92-181">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="7da92-182">Dále přidejte zadané statické vlastnosti typu:</span><span class="sxs-lookup"><span data-stu-id="7da92-182">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="7da92-183">Získání této vlastnosti bude vždy vyhodnocena jako text "Hello!".</span><span class="sxs-lookup"><span data-stu-id="7da92-183">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="7da92-184">`GetterCode` Pro vlastnost používá F # uvozovky, která představuje kód, který kompilátoru hostitele generuje pro získání vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7da92-184">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="7da92-185">Další informace o uvozovky najdete v tématu [uvozovky kódu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="7da92-185">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="7da92-186">Přidejte dokumentace XML pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7da92-186">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="7da92-187">Zadaná vlastnost nyní připojte zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-187">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="7da92-188">Zadaný člen musíte přiřadit pouze jeden typ.</span><span class="sxs-lookup"><span data-stu-id="7da92-188">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="7da92-189">V opačném člen nikdy budou přístupné.</span><span class="sxs-lookup"><span data-stu-id="7da92-189">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="7da92-190">Teď vytvořte zadaný konstruktoru, které nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="7da92-190">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="7da92-191">`InvokeCode` Pro konstruktor vrátí F # uvozovky, která představuje kód, který kompilátoru hostitele generuje při volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7da92-191">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="7da92-192">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="7da92-192">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="7da92-193">Instanci zadaného typu se vytvoří základní daty "Data objektu".</span><span class="sxs-lookup"><span data-stu-id="7da92-193">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="7da92-194">Uvozovkách kód obsahuje převod na [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) vzhledem k tomu, že je tento typ vymazání to zadaný typ (jaký jste uvedli, když deklarovat zadaného typu).</span><span class="sxs-lookup"><span data-stu-id="7da92-194">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="7da92-195">Přidejte dokumentace XML pro konstruktor a přidejte zadaný konstruktor na zadaný typ:</span><span class="sxs-lookup"><span data-stu-id="7da92-195">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="7da92-196">Vytvořte druhý zadaný konstruktor, který přijímá jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="7da92-196">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="7da92-197">`InvokeCode` Pro konstruktor znovu vrátí F # uvozovky, která představuje kód, který kompilátoru hostitele generuje pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="7da92-197">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="7da92-198">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="7da92-198">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="7da92-199">Pomocí zadaných dat "10" se vytvoří instanci zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-199">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="7da92-200">Může mít už k tomu, který `InvokeCode` funkce vrátí uvozovek.</span><span class="sxs-lookup"><span data-stu-id="7da92-200">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="7da92-201">Vstup pro tuto funkci je seznam výrazů, jeden pro každý parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7da92-201">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="7da92-202">V takovém případě je k dispozici v výraz, který představuje hodnotu jeden parametr `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="7da92-202">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="7da92-203">Kód pro volání konstruktoru převede návratovou hodnotu vymazaných typu `obj`.</span><span class="sxs-lookup"><span data-stu-id="7da92-203">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="7da92-204">Po přidání druhého zadaný konstruktor typu, můžete vytvořit zadanou instanci vlastnost:</span><span class="sxs-lookup"><span data-stu-id="7da92-204">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="7da92-205">Získávání tato vlastnost vrátí délku řetězce, který je objekt reprezentace.</span><span class="sxs-lookup"><span data-stu-id="7da92-205">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="7da92-206">`GetterCode` Vlastnost vrací uvozovek F #, která určuje kód, který generuje kompilátoru hostitele GET pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7da92-206">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="7da92-207">Jako `InvokeCode`, `GetterCode` funkce vrátí uvozovek.</span><span class="sxs-lookup"><span data-stu-id="7da92-207">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="7da92-208">Kompilátor hostitele volání této funkce se seznamem argumentů.</span><span class="sxs-lookup"><span data-stu-id="7da92-208">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="7da92-209">V takovém případě argumenty, které zahrnují jenom jeden výraz, který představuje instanci, na kterém je volána metoda getter, kterým můžete přistupovat pomocí `args.[0]`. Implementace `GetterCode` pak splices do uvozovek výsledek vymazaných typu `obj`, a pro uspokojení kompilátoru mechanismus pro kontrolu typy, že objekt je řetězec se používá přetypování.</span><span class="sxs-lookup"><span data-stu-id="7da92-209">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="7da92-210">V další části `makeOneProvidedType` poskytuje metodu instance jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="7da92-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="7da92-211">Nakonec vytvořte vnořené typu, který obsahuje 100 vnořené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7da92-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="7da92-212">Vnořené vytvoření tohoto typu a jeho vlastnosti je zpožděno, to znamená, počítaný na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="7da92-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="7da92-213">Podrobnosti o vymazaných zadané typy</span><span class="sxs-lookup"><span data-stu-id="7da92-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="7da92-214">Příklad v této části se poskytuje pouze *vymazat zadané typy*, které jsou obzvláště užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="7da92-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="7da92-215">Když píšete zprostředkovatele pro informace prostor, který obsahuje pouze data a metody.</span><span class="sxs-lookup"><span data-stu-id="7da92-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="7da92-216">Když píšete poskytovatele, kde nejsou důležité pro praktické využití místa na informace sémantiku přesné runtime-type.</span><span class="sxs-lookup"><span data-stu-id="7da92-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="7da92-217">Když píšete zprostředkovatele pro informace prostor, který je tak velký a vzájemně propojena, že není technicky možné vygenerovat skutečné typů .NET pro prostor informace.</span><span class="sxs-lookup"><span data-stu-id="7da92-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="7da92-218">V tomto příkladu každý zadaný typ vymazáním na typ `obj`, a všechny používá typu se zobrazí jako typ `obj` v zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7da92-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="7da92-219">Ve skutečnosti objekty v těchto příkladech jsou řetězce, ale typ se zobrazí jako `System.Object` v rozhraní .NET zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7da92-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="7da92-220">I s všechna použití typ vymazání, můžete použít explicitní zabalení, rozbalení a přetypování k podkopat vymazat typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="7da92-221">Výjimky pro přetypování, který není platný v takovém případě může způsobit, když objekt se používá.</span><span class="sxs-lookup"><span data-stu-id="7da92-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="7da92-222">Modul runtime zprostředkovatele můžete definovat vlastní typ privátní reprezentace k ochraně proti false reprezentace.</span><span class="sxs-lookup"><span data-stu-id="7da92-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="7da92-223">Nelze definovat vymazaných typy v jazyku F # sám sebe.</span><span class="sxs-lookup"><span data-stu-id="7da92-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="7da92-224">Pouze zadané typy může vymazat.</span><span class="sxs-lookup"><span data-stu-id="7da92-224">Only provided types may be erased.</span></span> <span data-ttu-id="7da92-225">Je potřeba pochopit následky, oba praktická a sémantické některou vymazat vymazaných typy pro váš typ zprostředkovatele nebo zprostředkovatele, který poskytuje typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="7da92-226">Typ vymazaných nemá skutečné typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7da92-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="7da92-227">Proto nemůžete udělat přesný odraz přes typ a může podkopat vymazaných typy, pokud používáte přetypování runtime a další metody, které jsou závislé na Sémantika typu přesný runtime.</span><span class="sxs-lookup"><span data-stu-id="7da92-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="7da92-228">Subversion vymazaných typů často výsledkem typ přetypování výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="7da92-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>


### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="7da92-229">Výběr reprezentace pro vymazat zadané typy</span><span class="sxs-lookup"><span data-stu-id="7da92-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="7da92-230">U některých používá vymazaných zadaný typů žádné reprezentace se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="7da92-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="7da92-231">Například vymazaných zadaný typ může obsahovat pouze statické vlastnosti a členy a žádné konstruktory, a žádné metody nebo vlastnosti by vrátit instanci typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="7da92-232">Pokud se lze připojit vymazaných instancí zadaný typ, musíte zvážit následující otázky:</span><span class="sxs-lookup"><span data-stu-id="7da92-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="7da92-233">**Co je zadaný typ vymazání?**</span><span class="sxs-lookup"><span data-stu-id="7da92-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="7da92-234">Vymazání poskytnutý typ je, jak zobrazuje typ v zkompilovaný kód .NET.</span><span class="sxs-lookup"><span data-stu-id="7da92-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="7da92-235">Vymazání typu zadaný vymazaných třídy je vždy první-vymazat základní typ v řetězu dědičnosti typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="7da92-236">Vymazání typ zadaný vymazaných rozhraní je vždy `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="7da92-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="7da92-237">**Jaké jsou reprezentace zadaného typu?**</span><span class="sxs-lookup"><span data-stu-id="7da92-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="7da92-238">Sady možné objektů pro vymazaných zadaný typ se nazývají její reprezentace.</span><span class="sxs-lookup"><span data-stu-id="7da92-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="7da92-239">V příkladu v tomto dokumentu reprezentace všech vymazaných zadané typy `Type1..Type100` jsou vždy řetězcových objektů.</span><span class="sxs-lookup"><span data-stu-id="7da92-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="7da92-240">Všechny reprezentace zadaného typu musí být kompatibilní s vymazání zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="7da92-241">(Jinak, kompilátor jazyka F # zobrazí chybu pro použití poskytovatele typu, nebo vygeneruje neověřitelný kód rozhraní .NET, který není platný.</span><span class="sxs-lookup"><span data-stu-id="7da92-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="7da92-242">Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)</span><span class="sxs-lookup"><span data-stu-id="7da92-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="7da92-243">Pomocí některé z následujících dvou přístupů Oboje je velmi běžné si můžete vybrat reprezentaci pro zadané objekty:</span><span class="sxs-lookup"><span data-stu-id="7da92-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="7da92-244">Pokud zadáváte jednoduše silného typu obálku přes existující typ rozhraní .NET, často má smysl pro typ vašeho chcete vymazat tento typ, použijte instance tohoto typu jako reprezentace nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="7da92-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="7da92-245">Tento přístup je vhodné, když většina stávajících metod daný typ stále mít smysl, pokud používáte verzi silného.</span><span class="sxs-lookup"><span data-stu-id="7da92-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="7da92-246">Pokud chcete vytvořit rozhraní API, které se liší výrazně z jakéhokoli existující rozhraní API .NET, má smysl vytvoření runtime typů, které budou typ vymazání a reprezentace pro zadané typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="7da92-247">V příkladu v tomto dokumentu používá řetězce jako reprezentace zadaných objektů.</span><span class="sxs-lookup"><span data-stu-id="7da92-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="7da92-248">Často může být vhodné k použití pro vyjádření jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="7da92-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="7da92-249">Můžete například použít slovník jako kontejner objektů:</span><span class="sxs-lookup"><span data-stu-id="7da92-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="7da92-250">Jako alternativu může definovat typu ve zprostředkovateli typ, který se použije v době běhu k reprezentaci, společně s jednu nebo více operací modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="7da92-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="7da92-251">Zadaný členy pak můžete vytvořit instance tohoto typu objektu:</span><span class="sxs-lookup"><span data-stu-id="7da92-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="7da92-252">V takovém případě může (volitelně) použijete tento typ jako typ vymazání zadáním tohoto typu, jako `baseType` při sestavování `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="7da92-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="7da92-253">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="7da92-253">Key Lessons</span></span>

<span data-ttu-id="7da92-254">V předchozí části Vysvětlení najdete postup vytvoření jednoduchého zprostředkovatele typu mazání, která poskytuje celou řadu typů, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="7da92-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="7da92-255">Tato část také vysvětlené koncept typ vymazání, včetně některé z výhod a nevýhod poskytnout vymazaných typy z typu poskytovatele a popsané reprezentace vymazaných typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>


## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="7da92-256">Typ zprostředkovatele, který používá statické parametry</span><span class="sxs-lookup"><span data-stu-id="7da92-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="7da92-257">Schopnost Parametrizace zprostředkovatelů typů pomocí statických dat umožňuje mnoho scénářů zajímavé, i v případech, kdy zprostředkovatel nepotřebuje přístup k žádným datům místní nebo vzdálené.</span><span class="sxs-lookup"><span data-stu-id="7da92-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="7da92-258">V této části se dozvíte některé základní postupy pro uvedení společně takové zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>


### <a name="type-checked-regex-provider"></a><span data-ttu-id="7da92-259">Zaškrtnutí Regex – zprostředkovatel typu</span><span class="sxs-lookup"><span data-stu-id="7da92-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="7da92-260">Představte si, že chcete implementovat typ zprostředkovatele pro regulární výrazy, který zabalí .NET `System.Text.RegularExpressions.Regex` knihovny v rozhraní, které poskytuje následující záruky kompilace:</span><span class="sxs-lookup"><span data-stu-id="7da92-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET `System.Text.RegularExpressions.Regex` libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="7da92-261">Ověřuje, zda je platný regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="7da92-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="7da92-262">Poskytuje pojmenované vlastnosti na odpovídající položky, které jsou založeny na názvy všech skupin v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="7da92-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="7da92-263">V této části se dozvíte, jak vytvořit pomocí zprostředkovatelů typů `RegExProviderType` zadejte, že poskytne tyto výhody parameterizes regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="7da92-263">This section shows you how to use type providers to create a `RegExProviderType` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="7da92-264">Kompilátor nahlásí chybu, pokud zadanému vzoru není platný, a typ zprostředkovatele můžete rozbalit skupiny z vzoru tak, aby je můžete přistupovat pomocí vlastnosti shoduje s názvem.</span><span class="sxs-lookup"><span data-stu-id="7da92-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="7da92-265">Při návrhu zprostředkovatele typ měli zvážit, jak by měla vypadat jeho zveřejněné rozhraní API pro koncové uživatele a jak se tento návrh přeloží pro kód .NET.</span><span class="sxs-lookup"><span data-stu-id="7da92-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="7da92-266">Následující příklad ukazuje, jak používat takové rozhraní API jak získat komponenty kód oblasti:</span><span class="sxs-lookup"><span data-stu-id="7da92-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="7da92-267">Následující příklad ukazuje, jak zprostředkovatel typu překládá těchto volání:</span><span class="sxs-lookup"><span data-stu-id="7da92-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="7da92-268">Vezměte na vědomí následující body:</span><span class="sxs-lookup"><span data-stu-id="7da92-268">Note the following points:</span></span>

- <span data-ttu-id="7da92-269">Představuje typ standardní Regex parametrizované `RegexTyped` typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="7da92-270">`RegexTyped` Konstruktor výsledkem volání konstruktoru Regex předávání v statický typ argumentu pro vzoru.</span><span class="sxs-lookup"><span data-stu-id="7da92-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="7da92-271">Výsledky `Match` metoda jsou reprezentované pomocí standardní `System.Text.RegularExpressions.Match` typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-271">The results of the `Match` method are represented by the standard `System.Text.RegularExpressions.Match` type.</span></span>

- <span data-ttu-id="7da92-272">Každou skupinu s názvem výsledkem zadané vlastnosti a přístupu k vlastnosti výsledkem použití indexer na shodu `Groups` kolekce.</span><span class="sxs-lookup"><span data-stu-id="7da92-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="7da92-273">Následující kód je základní logiku pro implementaci takové zprostředkovatele a v tomto příkladu vynechá přidání všech členů na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="7da92-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="7da92-274">Informace o každý přidaný člen najdete v příslušné části dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="7da92-275">Pro kód úplné stažení ukázky z [F # 3.0 ukázka Pack](https://fsharp3sample.codeplex.com) na webu Codeplex.</span><span class="sxs-lookup"><span data-stu-id="7da92-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

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

<span data-ttu-id="7da92-276">Vezměte na vědomí následující body:</span><span class="sxs-lookup"><span data-stu-id="7da92-276">Note the following points:</span></span>

- <span data-ttu-id="7da92-277">Typ zprostředkovatele přebírá dva parametry statické: `pattern`, což je povinný a `options`, (protože je výchozí hodnota je zadáno) jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="7da92-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="7da92-278">Po argumentů statické jsou zadány, můžete vytvořit instanci regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="7da92-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="7da92-279">Tato instance bude vyvolána výjimka, pokud regulární výraz je poškozený a tato chyba bude ohlášena uživatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="7da92-280">V rámci `DefineStaticParameters` zpětné volání, můžete definovat typ, který bude vrácen po jsou zadané argumenty.</span><span class="sxs-lookup"><span data-stu-id="7da92-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="7da92-281">Tento kód nastaví `HideObjectMethods` na hodnotu true, aby prostředí IntelliSense zůstane efektivní.</span><span class="sxs-lookup"><span data-stu-id="7da92-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="7da92-282">Tento atribut způsobí, že `Equals`, `GetHashCode`, `Finalize`, a `GetType` členy do potlačit ze seznamů IntelliSense pro zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="7da92-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="7da92-283">Používáte `obj` jako základní typ metody, ale budete používat `Regex` objektu jako runtime reprezentaci tohoto typu, jako další příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="7da92-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="7da92-284">Volání `Regex` vyvolá konstruktor `System.ArgumentException` při regulární výraz není platný.</span><span class="sxs-lookup"><span data-stu-id="7da92-284">The call to the `Regex` constructor throws a `System.ArgumentException` when a regular expression isn’t valid.</span></span> <span data-ttu-id="7da92-285">Kompilátor zachytí výjimku a oznámí chybovou zprávu pro uživatele v době kompilace nebo v editoru Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7da92-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="7da92-286">Tato výjimka umožňuje regulární výrazy, které má být ověřen bez spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="7da92-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="7da92-287">Typ definovaný nad není ještě užitečné, protože neobsahuje žádné smysluplný metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7da92-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="7da92-288">Nejprve přidejte statického `IsMatch` metoda:</span><span class="sxs-lookup"><span data-stu-id="7da92-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="7da92-289">Předchozí kód definuje metodu `IsMatch`, která přebírá řetězec jako vstup a vrátí `bool`.</span><span class="sxs-lookup"><span data-stu-id="7da92-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="7da92-290">Pouze složité část je použití `args` argument v rámci `InvokeCode` definice.</span><span class="sxs-lookup"><span data-stu-id="7da92-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="7da92-291">V tomto příkladu `args` je seznam uvozovky zastupující argumenty této metodě.</span><span class="sxs-lookup"><span data-stu-id="7da92-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="7da92-292">Pokud je metoda metody instance, představuje první argument `this` argument.</span><span class="sxs-lookup"><span data-stu-id="7da92-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="7da92-293">Ale pro statickou metodu argumenty jsou všechny právě explicitní argumenty pro metodu.</span><span class="sxs-lookup"><span data-stu-id="7da92-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="7da92-294">Všimněte si, že typ uvozovkách hodnoty by měl odpovídat zadaný návratový typ (v tomto případě `bool`).</span><span class="sxs-lookup"><span data-stu-id="7da92-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="7da92-295">Také Upozorňujeme, že tento kód používá `AddXmlDoc` metoda a ujistěte se také, že zadaná metoda je užitečná dokumentaci k nástroji, kterou můžete zadat pomocí IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7da92-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="7da92-296">Dále přidejte metodu Match instance.</span><span class="sxs-lookup"><span data-stu-id="7da92-296">Next, add an instance Match method.</span></span> <span data-ttu-id="7da92-297">Však tato metoda by měla vrátit hodnotu zadaný `Match` zadejte tak, aby se dalo přistupovat skupiny způsobem silného typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="7da92-298">Proto je nejdřív deklarovat `Match` typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="7da92-299">Protože tento typ závisí na vzor, který byl zadán jako statické argument, musí být tento typ vnořen v definici parametrizované typu:</span><span class="sxs-lookup"><span data-stu-id="7da92-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="7da92-300">Potom přidáte jednu vlastnost typu shodu pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="7da92-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="7da92-301">V době běhu je vyjádřené shody `System.Text.RegularExpressions.Match` hodnotu, takže musíte použít uvozovky, která definuje vlastnost `System.Text.RegularExpressions.Match.Groups` indexované vlastnosti získat relevantní skupiny.</span><span class="sxs-lookup"><span data-stu-id="7da92-301">At runtime, a match is represented as a `System.Text.RegularExpressions.Match` value, so the quotation that defines the property must use the `System.Text.RegularExpressions.Match.Groups` indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="7da92-302">Znovu si všimněte, že přidáváte dokumentace XML do zadané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7da92-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="7da92-303">Také Upozorňujeme, že vlastnost může číst, pokud `GetterCode` funkce je k dispozici, a vlastnost lze zapisovat, pokud `SetterCode` funkce je k dispozici, proto výsledné vlastnost je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="7da92-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="7da92-304">Nyní můžete vytvořit metody instance, která vrátí hodnotu tohoto `Match` typu:</span><span class="sxs-lookup"><span data-stu-id="7da92-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="7da92-305">Vzhledem k tomu, že vytváříte metodu instance `args.[0]` představuje `RegexTyped` instanci, na kterém metoda je volána, a `args.[1]` je vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="7da92-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="7da92-306">Nakonec zadejte konstruktor, aby bylo možné vytvořit instancí zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="7da92-307">Konstruktor vymaže jenom k vytvoření standardní instance .NET Regex, která je znovu zabalená na objekt, protože `obj` je výmaz zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="7da92-308">S touto změnou využití ukázkové rozhraní API, které zadaná v dřívější tématu funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="7da92-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="7da92-309">Následující kód je úplný a poslední:</span><span class="sxs-lookup"><span data-stu-id="7da92-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="7da92-310">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="7da92-310">Key Lessons</span></span>

<span data-ttu-id="7da92-311">V této části Vysvětlení způsobu vytváření typ zprostředkovatele, který funguje na jeho statické parametry.</span><span class="sxs-lookup"><span data-stu-id="7da92-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="7da92-312">Zprostředkovatel zkontroluje statický parametr a poskytuje operace založené na jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7da92-312">The provider checks the static parameter and provides operations based on its value.</span></span>


## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="7da92-313">Typ zprostředkovatele, který je zálohovaný díky místní Data</span><span class="sxs-lookup"><span data-stu-id="7da92-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="7da92-314">Často můžete chtít zprostředkovatelů typů k dispozici rozhraní API podle pouze statické parametry, ale také informace z místní nebo vzdálené systémy.</span><span class="sxs-lookup"><span data-stu-id="7da92-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="7da92-315">Tato část popisuje typ zprostředkovatele, které jsou založeny na místní data, jako je například místní datové soubory.</span><span class="sxs-lookup"><span data-stu-id="7da92-315">This section discusses type providers that are based on local data, such as local data files.</span></span>


### <a name="simple-csv-file-provider"></a><span data-ttu-id="7da92-316">Jednoduché CSV – zprostředkovatel souboru</span><span class="sxs-lookup"><span data-stu-id="7da92-316">Simple CSV File Provider</span></span>

<span data-ttu-id="7da92-317">Jako jednoduchý příklad zvažte zprostředkovatele typů pro přístup k vědeckých dat ve formátu hodnoty oddělené čárkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="7da92-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="7da92-318">V této části se předpokládá, že soubory CSV obsahovat řádek záhlaví, za nímž následuje data s plovoucí desetinnou, jak ukazuje následující tabulka:</span><span class="sxs-lookup"><span data-stu-id="7da92-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>


```
|Distance (meter)|Time (second)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|
```

<span data-ttu-id="7da92-319">V této části ukazuje, jak poskytnout typ, který vám pomůže získat řádky s `Distance` vlastnost typu `float<meter>` a `Time` vlastnost typu `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="7da92-319">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="7da92-320">Pro jednoduchost jsou provedeny následující předpoklady:</span><span class="sxs-lookup"><span data-stu-id="7da92-320">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="7da92-321">Názvy záhlaví jsou buď bez měrné jednotky nebo tvar "Název" (jednotky) a nesmí obsahovat čárky.</span><span class="sxs-lookup"><span data-stu-id="7da92-321">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="7da92-322">Všechny jednotky systém mezinárodní (SI), jako jsou jednotky [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames – modul (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modul definuje.</span><span class="sxs-lookup"><span data-stu-id="7da92-322">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="7da92-323">Jednotky jsou všechny jednoduché (například monitorovat) místo složené (například, měření za sekundu).</span><span class="sxs-lookup"><span data-stu-id="7da92-323">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="7da92-324">Všechny sloupce obsahují data s plovoucí desetinnou.</span><span class="sxs-lookup"><span data-stu-id="7da92-324">All columns contain floating point data.</span></span>

<span data-ttu-id="7da92-325">Obsáhlejší zprostředkovatele by povolte tato omezení.</span><span class="sxs-lookup"><span data-stu-id="7da92-325">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="7da92-326">Prvním krokem je znovu vzít v úvahu, jak by měla vypadat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7da92-326">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="7da92-327">Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="7da92-327">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="7da92-328">V takovém případě by měl kompilátor převést těchto volání na něco podobného jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7da92-328">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new MiniCsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="7da92-329">Optimální překlad bude vyžadovat typ zprostředkovatele, který má definovat reálné číslo `CsvFile` typu v sestavení typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-329">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="7da92-330">Zprostředkovatelé typů často závisí na několik pomocná typy a metody můžete zabalit důležité logiku.</span><span class="sxs-lookup"><span data-stu-id="7da92-330">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="7da92-331">Protože míry jsou vymazány za běhu, můžete použít `float[]` jako typ vymazaných pro řádek.</span><span class="sxs-lookup"><span data-stu-id="7da92-331">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="7da92-332">Kompilátor počítat různé sloupce s typy jinou míru.</span><span class="sxs-lookup"><span data-stu-id="7da92-332">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="7da92-333">Například z prvního sloupce v našem příkladu má typ `float<meter>`, a druhá má `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="7da92-333">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="7da92-334">Však může zůstat vymazaných reprezentace poměrně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="7da92-334">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="7da92-335">Následující kód ukazuje základní implementaci.</span><span class="sxs-lookup"><span data-stu-id="7da92-335">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="7da92-336">Vezměte na vědomí následující body o implementaci:</span><span class="sxs-lookup"><span data-stu-id="7da92-336">Note the following points about the implementation:</span></span>

- <span data-ttu-id="7da92-337">Přetížené konstruktory povolit původní soubor nebo ten, který má stejné schéma čtení.</span><span class="sxs-lookup"><span data-stu-id="7da92-337">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="7da92-338">Tento vzor je běžné při zapisovat zprostředkovatele typů pro místní nebo vzdálené datové zdroje, a tento vzor umožňuje místního souboru, který se má použít jako šablonu pro vzdálená data.</span><span class="sxs-lookup"><span data-stu-id="7da92-338">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="7da92-339">Můžete použít [typeproviderconfig –](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) hodnotu, která je v předaný konstruktoru zprostředkovatele typ k vyřešení relativních názvů souborů.</span><span class="sxs-lookup"><span data-stu-id="7da92-339">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="7da92-340">Můžete použít `AddDefinitionLocation` metoda zadat umístění zadané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7da92-340">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="7da92-341">Proto pokud používáte `Go To Definition` u zadané vlastnosti, otevře se soubor CSV v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7da92-341">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="7da92-342">Můžete použít `ProvidedMeasureBuilder` typ k vyhledání jednotek SI a ke generování odpovídajícího `float<_>` typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-342">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="7da92-343">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="7da92-343">Key Lessons</span></span>

<span data-ttu-id="7da92-344">Tato část vysvětluje vytvoření zprostředkovatele typů pro místní zdroj dat s jednoduché schéma, které se nachází v samotném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7da92-344">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>


## <a name="going-further"></a><span data-ttu-id="7da92-345">Budete pokračovat</span><span class="sxs-lookup"><span data-stu-id="7da92-345">Going Further</span></span>

<span data-ttu-id="7da92-346">Následující části obsahují návrhy pro další studie.</span><span class="sxs-lookup"><span data-stu-id="7da92-346">The following sections include suggestions for further study.</span></span>


### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="7da92-347">Podívejte se na zkompilovaný kód pro vymazaných typy</span><span class="sxs-lookup"><span data-stu-id="7da92-347">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="7da92-348">Získáte představu, jak použití zprostředkovatele typu odpovídá kód, který je vygenerované, podívejte se na následující funkce pomocí `HelloWorldTypeProvider` používané v tomto tématu výše.</span><span class="sxs-lookup"><span data-stu-id="7da92-348">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="7da92-349">Zde je výsledný kód decompiled pomocí ildasm.exe bitové kopie:</span><span class="sxs-lookup"><span data-stu-id="7da92-349">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="7da92-350">Jak ukazuje příklad, všechny zmínky o typ `Type1` a `InstanceProperty` vlastnost byl vymazán, a operace pouze na typy runtime související se situací.</span><span class="sxs-lookup"><span data-stu-id="7da92-350">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>


### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="7da92-351">Návrh a konvence pojmenování pro zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="7da92-351">Design and Naming Conventions for Type Providers</span></span>
<span data-ttu-id="7da92-352">Sledujte následující konvence při vytváření zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-352">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="7da92-353">**Zprostředkovatelé pro připojení protokoly** obecně názvy většina zprostředkovatele – knihovny DLL pro data a služby připojení protokoly, jako je například OData nebo SQL připojení, končit `TypeProvider` nebo `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="7da92-353">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="7da92-354">Například použijte název knihovny DLL, která se podobá následující řetězec:</span><span class="sxs-lookup"><span data-stu-id="7da92-354">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="7da92-355">Ujistěte se, že vaše zadané typy jsou členy odpovídající oboru názvů a připojení protokolu, který jste implementovali:</span><span class="sxs-lookup"><span data-stu-id="7da92-355">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="7da92-356">**Nástroje zprostředkovatele pro obecné kódování**.</span><span class="sxs-lookup"><span data-stu-id="7da92-356">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="7da92-357">Nástroj Typ zprostředkovatele, například pro regulární výrazy typ zprostředkovatele, může být součástí základní knihovny, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="7da92-357">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="7da92-358">V takovém případě zadaný typ objeví v odpovídajícím bodě podle normální .NET návrhu konvence:</span><span class="sxs-lookup"><span data-stu-id="7da92-358">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="7da92-359">**Zdroje dat typu singleton**.</span><span class="sxs-lookup"><span data-stu-id="7da92-359">**Singleton Data Sources**.</span></span> <span data-ttu-id="7da92-360">Někteří poskytovatelé typ připojení ke zdroji dat jeden vyhrazený a zadejte jenom data.</span><span class="sxs-lookup"><span data-stu-id="7da92-360">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="7da92-361">V takovém případě by měl vyřadit `TypeProvider` přípona a používat běžné konvence pro pojmenování .NET:</span><span class="sxs-lookup"><span data-stu-id="7da92-361">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="7da92-362">Další informace najdete v tématu `GetConnection` návrh názvů, který je popsán dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-362">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>


### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="7da92-363">Vzory návrhu pro zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="7da92-363">Design Patterns for Type Providers</span></span>

<span data-ttu-id="7da92-364">Následující části popisují vzorů návrhu, které můžete použít při vytváření zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-364">The following sections describe design patterns you can use when authoring type providers.</span></span>


#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="7da92-365">Vzor návrhu GetConnection</span><span class="sxs-lookup"><span data-stu-id="7da92-365">The GetConnection Design Pattern</span></span>
<span data-ttu-id="7da92-366">Většina zprostředkovatelů typů zasílány používat `GetConnection` vzor, který je používán typ zprostředkovatele v FSharp.Data.TypeProviders.dll, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="7da92-366">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="7da92-367">Zprostředkovatelé typů zálohován vzdálených dat a služby</span><span class="sxs-lookup"><span data-stu-id="7da92-367">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="7da92-368">Než vytvoříte typ zprostředkovatele, který je zálohovaný díky vzdálených dat a služby, musíte zvážit řadu problémů, které jsou obsaženy v připojených programování.</span><span class="sxs-lookup"><span data-stu-id="7da92-368">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="7da92-369">Tyto problémy patří následující aspekty:</span><span class="sxs-lookup"><span data-stu-id="7da92-369">These issues include the following considerations:</span></span>

- <span data-ttu-id="7da92-370">Schéma mapování</span><span class="sxs-lookup"><span data-stu-id="7da92-370">schema mapping</span></span>

- <span data-ttu-id="7da92-371">liveness a zneplatnění případě změny schématu</span><span class="sxs-lookup"><span data-stu-id="7da92-371">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="7da92-372">ukládání do mezipaměti schématu</span><span class="sxs-lookup"><span data-stu-id="7da92-372">schema caching</span></span>

- <span data-ttu-id="7da92-373">asynchronní implementace operací přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="7da92-373">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="7da92-374">Podpora dotazů, včetně dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="7da92-374">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="7da92-375">pověření a ověřování</span><span class="sxs-lookup"><span data-stu-id="7da92-375">credentials and authentication</span></span>

<span data-ttu-id="7da92-376">V tomto tématu není prozkoumat tyto další problémy.</span><span class="sxs-lookup"><span data-stu-id="7da92-376">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="7da92-377">Další techniky pro vytváření obsahu</span><span class="sxs-lookup"><span data-stu-id="7da92-377">Additional Authoring Techniques</span></span>

<span data-ttu-id="7da92-378">Když píšete vlastní typ zprostředkovatele, můžete použít následující další techniky.</span><span class="sxs-lookup"><span data-stu-id="7da92-378">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="7da92-379">Vytváření typů a členů na vyžádání</span><span class="sxs-lookup"><span data-stu-id="7da92-379">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="7da92-380">Rozhraní API ProvidedType má odložené verzích přidávat členy.</span><span class="sxs-lookup"><span data-stu-id="7da92-380">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="7da92-381">Tyto verze se používají k vytvoření prostorů na vyžádání typů.</span><span class="sxs-lookup"><span data-stu-id="7da92-381">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="7da92-382">Typy polí a konkretizací obecného typu</span><span class="sxs-lookup"><span data-stu-id="7da92-382">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="7da92-383">Zkontrolujte zadané členy (jehož podpisy zahrnují typy polí, typy byref a instancí možnosti obecné typy) s použitím normální `MakeArrayType`, `MakePointerType`, a `MakeGenericType` na jakoukoli instanci System.Type, včetně `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="7da92-383">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of System.Type, including `ProvidedTypeDefinitions`.</span></span>

<span data-ttu-id="7da92-384">Poznámka: V některých případech budete možná muset použít Pomocník `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="7da92-384">NOTE: In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="7da92-385">Najdete v dokumentaci typ zprostředkovatele SDK další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="7da92-385">See the Type Provider SDK documentation for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="7da92-386">Poskytnutí jednotek měr poznámky</span><span class="sxs-lookup"><span data-stu-id="7da92-386">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="7da92-387">Rozhraní API ProvidedTypes poskytuje pomocné rutiny pro zajištění měr poznámky.</span><span class="sxs-lookup"><span data-stu-id="7da92-387">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="7da92-388">Chcete-li například zadat typ `float<kg>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="7da92-388">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="7da92-389">K poskytování typ `Nullable<decimal<kg/m^2>>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="7da92-389">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="7da92-390">Přístup k projektu místní nebo skriptu místní prostředky</span><span class="sxs-lookup"><span data-stu-id="7da92-390">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="7da92-391">Je možné přidělit každou instanci zprostředkovatele typů `TypeProviderConfig` hodnotu během vytváření.</span><span class="sxs-lookup"><span data-stu-id="7da92-391">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="7da92-392">Tato hodnota obsahuje "řešení složka" pro poskytovatele (který je složka projektu kompilace nebo adresář, který obsahuje skript), seznam odkazovaná sestavení a další informace.</span><span class="sxs-lookup"><span data-stu-id="7da92-392">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="7da92-393">Zneplatnění</span><span class="sxs-lookup"><span data-stu-id="7da92-393">Invalidation</span></span>

<span data-ttu-id="7da92-394">Zprostředkovatelé může být spojeno zneplatnění signály oznámit služba jazyka F #, který možná změnil předpoklady schématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-394">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="7da92-395">Když dojde k zneplatnění, typecheck je znovu, pokud zprostředkovatel je hostované v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7da92-395">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="7da92-396">Tento signál se ignoruje, pokud zprostředkovatel je hostovaná v F # interaktivní nebo kompilátoru F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="7da92-396">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="7da92-397">Ukládání do mezipaměti informace o schématu</span><span class="sxs-lookup"><span data-stu-id="7da92-397">Caching Schema Information</span></span>

<span data-ttu-id="7da92-398">Zprostředkovatelé musí mezipaměti často přístup k informacím o schématu.</span><span class="sxs-lookup"><span data-stu-id="7da92-398">Providers must often cache access to schema information.</span></span> <span data-ttu-id="7da92-399">Data uložená v mezipaměti by měly být uložené pomocí názvu souboru, který je přiřazen jako statický parametr nebo jako uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="7da92-399">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="7da92-400">Je například ukládání do mezipaměti schématu `LocalSchemaFile` ve zprostředkovatelích typu v parametru `FSharp.Data.TypeProviders` sestavení.</span><span class="sxs-lookup"><span data-stu-id="7da92-400">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="7da92-401">Při provádění těchto poskytovatelů přesměruje tento statický parametr typ zprostředkovatele, který má používat informace o schématu do zadaného místního souboru místo přístup ke zdroji dat přes síť.</span><span class="sxs-lookup"><span data-stu-id="7da92-401">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="7da92-402">Pokud chcete použít informace uložené v mezipaměti schématu, musíte taky nastavit statický parametr `ForceUpdate` k `false`.</span><span class="sxs-lookup"><span data-stu-id="7da92-402">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="7da92-403">Podobným způsobem můžete použít k povolení přístupu k datům online a offline.</span><span class="sxs-lookup"><span data-stu-id="7da92-403">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="7da92-404">Základní sestavení</span><span class="sxs-lookup"><span data-stu-id="7da92-404">Backing Assembly</span></span>

<span data-ttu-id="7da92-405">Při sestavování `.dll` nebo `.exe` souboru, soubor .dll zálohování pro generovaný typy je staticky propojené do výsledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="7da92-405">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="7da92-406">Tento odkaz se vytvoří zkopírováním definic typů Intermediate Language (IL) a všechny spravované prostředky z základní sestavení do konečné sestavení.</span><span class="sxs-lookup"><span data-stu-id="7da92-406">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="7da92-407">Při použití F # interaktivní, soubor .dll zálohování nebude zkopírován a místo toho je načíst přímo do procesu F # interaktivní.</span><span class="sxs-lookup"><span data-stu-id="7da92-407">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="7da92-408">Výjimky a Diagnostika z zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="7da92-408">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="7da92-409">Všechny používá všech členů ze zadané typy může vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="7da92-409">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="7da92-410">Ve všech případech Pokud zprostředkovatel typu, vyvolá výjimku, kompilátoru hostitele atributy chyba na konkrétní typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-410">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="7da92-411">Typ zprostředkovatele výjimky by nikdy vést k chybám interní kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7da92-411">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="7da92-412">Zprostředkovatelé typů nemůžete hlásit upozornění.</span><span class="sxs-lookup"><span data-stu-id="7da92-412">Type providers can't report warnings.</span></span>

- <span data-ttu-id="7da92-413">Pokud zprostředkovatele typů hostovaný v kompilátoru F #, F # vývojového prostředí nebo F # interaktivní, jsou zachyceny všechny výjimky z tohoto zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-413">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="7da92-414">Vlastnosti zprávy je vždy text chyby a zobrazí se žádné trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7da92-414">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="7da92-415">Pokud se chystáte způsobí výjimku, můžete vyvolat následující příklady: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="7da92-415">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="7da92-416">Poskytnutí generovaného typy</span><span class="sxs-lookup"><span data-stu-id="7da92-416">Providing Generated Types</span></span>

<span data-ttu-id="7da92-417">Pokud má tento dokument vysvětlené jak zadejte vymazaných typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-417">So far, this document has explained how provide erased types.</span></span> <span data-ttu-id="7da92-418">Mechanismus zprostředkovatele typu v F # můžete také použít k poskytnutí generovaného typů, které jsou přidány jako skutečné definice typů .NET do programu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="7da92-418">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="7da92-419">Můžete musí odkazovat na generovaného poskytnout typy pomocí definice typu.</span><span class="sxs-lookup"><span data-stu-id="7da92-419">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<" https://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="7da92-420">Kód pomocného objektu ProvidedTypes 0,2, který je součástí verze F # 3.0 má omezenou podporu pro zajištění generovaného typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-420">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="7da92-421">Pro definici typu generované musí platit následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="7da92-421">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="7da92-422">`isErased` musí být nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="7da92-422">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="7da92-423">Vygenerovaný typ musí být přidán do nově vytvořený `ProvidedAssembly()`, který představuje kontejner pro generovaný kód fragmenty.</span><span class="sxs-lookup"><span data-stu-id="7da92-423">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="7da92-424">Zprostředkovatel musí mít sestavení, který má soubor .dll .NET skutečné zálohování s odpovídající soubor DLL na disku.</span><span class="sxs-lookup"><span data-stu-id="7da92-424">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>


## <a name="rules-and-limitations"></a><span data-ttu-id="7da92-425">Pravidla a omezení</span><span class="sxs-lookup"><span data-stu-id="7da92-425">Rules and Limitations</span></span>

<span data-ttu-id="7da92-426">Když píšete zprostředkovatelů typů, uvědomte si následující pravidla a omezení.</span><span class="sxs-lookup"><span data-stu-id="7da92-426">When you write type providers, keep the following rules and limitations in mind.</span></span>


### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="7da92-427">Zadané typy musí být dosažitelný</span><span class="sxs-lookup"><span data-stu-id="7da92-427">Provided types must be reachable</span></span>

<span data-ttu-id="7da92-428">Všechny zadané typy by měly být dostupné z typů-nested.</span><span class="sxs-lookup"><span data-stu-id="7da92-428">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="7da92-429">-Nested typy jsou uvedeny ve volání `TypeProviderForNamespaces` konstruktoru nebo volání `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="7da92-429">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="7da92-430">Například, pokud zprostředkovatel poskytuje typu `StaticClass.P : T`, ujistěte se, že je T-nested typ nebo vnořené v rámci jedné.</span><span class="sxs-lookup"><span data-stu-id="7da92-430">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="7da92-431">Například někteří poskytovatelé mít statická třída jako `DataTypes` obsahující tyto `T1, T2, T3, ...` typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-431">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="7da92-432">Chyba, jinak hodnota říká, že našel se odkaz na typ T v sestavení A, ale typ nebyl nalezen v této sestavě.</span><span class="sxs-lookup"><span data-stu-id="7da92-432">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="7da92-433">Pokud tato chyba se zobrazí, ověřte, že všechny podtypů lze přejít z typy zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-433">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="7da92-434">Poznámka: Tyto `T1, T2, T3...` typy jsou označovány jako *na průběžně* typy.</span><span class="sxs-lookup"><span data-stu-id="7da92-434">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="7da92-435">Nezapomeňte zahrnout je přístupné oboru názvů nebo nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="7da92-435">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="7da92-436">Omezení typu mechanismu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="7da92-436">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="7da92-437">Typ zprostředkovatele mechanismus v F # má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="7da92-437">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="7da92-438">Základní infrastruktury pro zprostředkovatelů typů v jazyce F # nepodporuje zadaný obecné typy nebo, pokud obecné metody.</span><span class="sxs-lookup"><span data-stu-id="7da92-438">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="7da92-439">Tento mechanismus nepodporuje vnořené typy s statické parametry.</span><span class="sxs-lookup"><span data-stu-id="7da92-439">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="7da92-440">Tipy pro vývoj</span><span class="sxs-lookup"><span data-stu-id="7da92-440">Development Tips</span></span>

<span data-ttu-id="7da92-441">Následující tipy mohou být užitečné během procesu vývoje.</span><span class="sxs-lookup"><span data-stu-id="7da92-441">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="7da92-442">Spustit dvě instance sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7da92-442">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="7da92-443">Můžete vytvořit typ zprostředkovatele v jedné instance a testování zprostředkovatele v dalších, protože test IDE bude trvat zámek na soubor .dll, který zabrání se znovu sestavit typ zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-443">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="7da92-444">Proto je třeba nejprve zavřít druhou instanci sady Visual Studio, zatímco zprostředkovatele je vytvořen v první instance, a pak musí znovu otevřete druhou instanci po zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="7da92-444">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="7da92-445">Ladění zprostředkovatelů typů pomocí volání fsc.exe</span><span class="sxs-lookup"><span data-stu-id="7da92-445">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="7da92-446">Zprostředkovatelé typů můžete vyvolat pomocí následující nástroje:</span><span class="sxs-lookup"><span data-stu-id="7da92-446">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="7da92-447">FSC.exe (příkazového řádku kompilátor jazyka F #)</span><span class="sxs-lookup"><span data-stu-id="7da92-447">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="7da92-448">fsi.exe (F # interaktivní kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="7da92-448">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="7da92-449">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="7da92-449">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="7da92-450">Zprostředkovatelé typů můžete ladit často snadno pomocí fsc.exe na soubor skriptu test (například script.fsx).</span><span class="sxs-lookup"><span data-stu-id="7da92-450">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="7da92-451">Ladicí program z příkazového řádku můžete spustit.</span><span class="sxs-lookup"><span data-stu-id="7da92-451">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="7da92-452">Protokolování tiskových stdout můžete použít.</span><span class="sxs-lookup"><span data-stu-id="7da92-452">You can use print-to-stdout logging.</span></span>


## <a name="see-also"></a><span data-ttu-id="7da92-453">Viz také</span><span class="sxs-lookup"><span data-stu-id="7da92-453">See Also</span></span>

* [<span data-ttu-id="7da92-454">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="7da92-454">Type Providers</span></span>](index.md)

* [<span data-ttu-id="7da92-455">Typ poskytovatele sady SDK</span><span class="sxs-lookup"><span data-stu-id="7da92-455">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)

