---
title: 'Kurz: Vytvoření zprostředkovatele typů (F #)'
description: 'Zjistěte, jak vytvořit vlastní poskytovatelé typu jazyka F # v jazyce F # 3.0 prozkoumáním několik jednoduchý typ zprostředkovatelů pro ilustraci základních konceptů.'
ms.date: 05/16/2016
ms.openlocfilehash: 3c998377b2c3a408d536ef416f3799bf7f04b6bd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036610"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="96639-103">Kurz: Vytvoření zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="96639-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="96639-104">Mechanismus poskytovatele typu v jazyce F # je podstatnou část jeho podpory pro bohaté programování informace.</span><span class="sxs-lookup"><span data-stu-id="96639-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="96639-105">Tento kurz vysvětluje, jak vytvořit vlastní typ zprostředkovatele provede vás vývoj několik jednoduchý typ zprostředkovatelů pro ilustraci základních konceptů.</span><span class="sxs-lookup"><span data-stu-id="96639-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="96639-106">Další informace o mechanismu poskytovatele typu v jazyce F # najdete v tématu [poskytovatelů typů](index.md).</span><span class="sxs-lookup"><span data-stu-id="96639-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="96639-107">Ekosystém F # obsahuje celou řadu poskytovatelů typů pro běžně používané internetové a firemní datové služby.</span><span class="sxs-lookup"><span data-stu-id="96639-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="96639-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="96639-108">For example:</span></span>

- <span data-ttu-id="96639-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) zahrnuje poskytovatelů typů pro formáty dokumentů JSON, XML, CSV nebo HTML.</span><span class="sxs-lookup"><span data-stu-id="96639-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="96639-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje silného typu přístup do databáze SQL pomocí mapování objektů a F # LINQ dotazy na tyto datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="96639-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="96639-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sadu poskytovatelů typů pro kompilaci změnami vkládání T-SQL v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="96639-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="96639-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sadu poskytovatelů typů pro použití pouze s programování rozhraní .NET Framework pro přístup k datové služby typu SQL, Entity Framework, OData a WSDL.</span><span class="sxs-lookup"><span data-stu-id="96639-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="96639-113">V případě potřeby můžete vytvořit vlastní poskytovatele typů nebo můžete odkazovat na zprostředkovateli typů, které jste vytvořili ostatní.</span><span class="sxs-lookup"><span data-stu-id="96639-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="96639-114">Vaše organizace může mít například datové služby, které poskytuje jejichž počet pojmenovaných datových sad, každou s vlastní stabilní schéma dat.</span><span class="sxs-lookup"><span data-stu-id="96639-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="96639-115">Můžete vytvořit poskytovatele typu, který schémata přečte a nabídne aktuální datové sady na programátorovi, tak silného typu.</span><span class="sxs-lookup"><span data-stu-id="96639-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="96639-116">Než začnete</span><span class="sxs-lookup"><span data-stu-id="96639-116">Before You Start</span></span>

<span data-ttu-id="96639-117">Mechanismus poskytovatel typu je primárně určený pro vkládání stabilní data a služby informačních prostorů do programovací prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="96639-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="96639-118">Tento mechanismus není určená pro vkládání informačních prostorů změní jehož schéma během provádění programu způsoby, které jsou relevantní pro aplikaci logiky.</span><span class="sxs-lookup"><span data-stu-id="96639-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="96639-119">Navíc mechanismu, který není určená pro meta programovací uvnitř jazyk i v případě, že této doména obsahuje mezi platné použití.</span><span class="sxs-lookup"><span data-stu-id="96639-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="96639-120">Tento mechanismus byste měli použít pouze v případě potřeby a kde vývoj poskytovatele typu poskytuje velmi vysokou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="96639-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="96639-121">Měli byste se vyhnout, zápis poskytovatele typu, kde není k dispozici schéma.</span><span class="sxs-lookup"><span data-stu-id="96639-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="96639-122">Podobně, měli byste se vyhnout zápis poskytovatele typu, kde běžný (nebo dokonce existující) bude stačit knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="96639-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="96639-123">Než začnete, může odpovědět na tyto otázky:</span><span class="sxs-lookup"><span data-stu-id="96639-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="96639-124">Máte schéma zdroje informací?</span><span class="sxs-lookup"><span data-stu-id="96639-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="96639-125">Pokud ano, co je mapování do F # a systém typů .NET?</span><span class="sxs-lookup"><span data-stu-id="96639-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="96639-126">Můžete použít existující rozhraní API (dynamicky zadávaných) jako výchozí bod pro implementaci?</span><span class="sxs-lookup"><span data-stu-id="96639-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="96639-127">Vy a vaše organizace mají dostatek používá zprostředkovatele typu tak, aby psali vhodné?</span><span class="sxs-lookup"><span data-stu-id="96639-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="96639-128">By běžné knihovny .NET vašim potřebám?</span><span class="sxs-lookup"><span data-stu-id="96639-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="96639-129">Jak moc se změní schéma?</span><span class="sxs-lookup"><span data-stu-id="96639-129">How much will your schema change?</span></span>

- <span data-ttu-id="96639-130">Se změní při psaní kódu?</span><span class="sxs-lookup"><span data-stu-id="96639-130">Will it change during coding?</span></span>

- <span data-ttu-id="96639-131">Se změní mezi kódování relace?</span><span class="sxs-lookup"><span data-stu-id="96639-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="96639-132">Se změní při provádění programu?</span><span class="sxs-lookup"><span data-stu-id="96639-132">Will it change during program execution?</span></span>

<span data-ttu-id="96639-133">Poskytovatelé typů jsou nejvhodnější pro situacích, kde je schéma stabilní za běhu a po celou dobu životnosti zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="96639-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="96639-134">Jednoduchý typ poskytovatele</span><span class="sxs-lookup"><span data-stu-id="96639-134">A Simple Type Provider</span></span>

<span data-ttu-id="96639-135">Tato ukázka je Samples.HelloWorldTypeProvider, podobně jako na ukázky v `examples` adresáři [F # typ poskytovatele sady SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="96639-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="96639-136">Zprostředkovatel zpřístupní "typ mezerou", který obsahuje 100 vymazaného typy, jak ukazuje následující kód pomocí syntaxe podpis F # a vynechání podrobnosti pro všechny s výjimkou `Type1`.</span><span class="sxs-lookup"><span data-stu-id="96639-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="96639-137">Další informace o typech vymazaného, naleznete v tématu [podrobnosti o vymaže poskytuje typy](#details-about-erased-provided-types) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="96639-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="96639-138">Všimněte si, že se staticky označuje sadu typů a členů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="96639-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="96639-139">V tomto příkladu není využít schopnost poskytovatele poskytují typy, které jsou závislé na schématu.</span><span class="sxs-lookup"><span data-stu-id="96639-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="96639-140">Implementace zprostředkovatele typu je popsaný v následujícím kódu a podrobnosti jsou popsané v předchozích částech tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="96639-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

>[!WARNING]
<span data-ttu-id="96639-141">Mohou existovat rozdíly mezi tímto kódem a online ukázky.</span><span class="sxs-lookup"><span data-stu-id="96639-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="96639-142">K používání tohoto poskytovatele, otevřete samostatnou instanci sady Visual Studio, vytvořit skript F # a potom přidejte odkaz na poskytovateli ze skriptu pomocí #r jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="96639-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="96639-143">Hledat typy pod `Samples.HelloWorldTypeProvider` obor názvů, který vygeneruje poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="96639-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="96639-144">Předtím, než je provedena rekompilace poskytovateli, ujistěte se, že neukončíte všechny instance sady Visual Studio a jazyka F # Interactive, které používají zprostředkovatele knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="96639-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="96639-145">Chyba sestavení, jinak dojde k vzhledem k tomu, že výstupní knihovnu DLL se uzamkne.</span><span class="sxs-lookup"><span data-stu-id="96639-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="96639-146">Ladění tohoto zprostředkovatele pomocí příkazů tisku, skript, který zpřístupňuje potížím s poskytovatelem a pak použít následující kód:</span><span class="sxs-lookup"><span data-stu-id="96639-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="96639-147">Chcete-li ladit tento zprostředkovatel pomocí sady Visual Studio, otevřete příkazový řádek sady Visual Studio s přihlašovacími údaji správce a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="96639-147">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="96639-148">Jako alternativu, otevřete sadu Visual Studio, otevřete nabídku ladění, zvolte `Debug/Attach to process…`a připojte k jiné `devenv` procesu, kde upravujete vašeho skriptu.</span><span class="sxs-lookup"><span data-stu-id="96639-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="96639-149">Pomocí této metody můžete snadněji zaměřit konkrétní logický typ zprostředkovatele interaktivně zadáním výrazy do druhé instance (s plnou podporou technologie IntelliSense a dalších funkcí).</span><span class="sxs-lookup"><span data-stu-id="96639-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="96639-150">Můžete zakázat pouze můj kód, ladění, abyste lépe identifikovat chyby v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="96639-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="96639-151">Informace o tom, jak povolit nebo zakázat tuto funkci najdete v tématu [procházení kódu s ladicím programem](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="96639-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="96639-152">Navíc můžete také nastavit první odpovídající výjimce zachytávání tak, že otevřete `Debug` nabídky a následným výběrem možnosti `Exceptions` nebo zadáním pomocí kláves Ctrl + Alt + E otevřete `Exceptions` dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="96639-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="96639-153">V tomto dialogovém okně v části `Common Language Runtime Exceptions`, vyberte `Thrown` zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="96639-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="96639-154">Implementace zprostředkovatele typu</span><span class="sxs-lookup"><span data-stu-id="96639-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="96639-155">Tato část vás provede hlavní části implementaci zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="96639-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="96639-156">Nejprve definujte typ pro vlastní typ zprostředkovatele, sama:</span><span class="sxs-lookup"><span data-stu-id="96639-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="96639-157">Tento typ musí být veřejné a je třeba označit ji [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) tak, aby kompilátor rozpozná poskytovatele typu při samostatného projektu F # odkazuje na sestavení obsahující typ atributu.</span><span class="sxs-lookup"><span data-stu-id="96639-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="96639-158">*Config* parametr je nepovinný a pokud jsou k dispozici, obsahuje kontextové konfigurační informace pro instanci typu zprostředkovatele, který vytváří kompilátor F #.</span><span class="sxs-lookup"><span data-stu-id="96639-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="96639-159">V dalším kroku implementujete [itypeprovider –](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96639-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="96639-160">V tomto případě použijete `TypeProviderForNamespaces` typ `ProvidedTypes` rozhraní API jako základní typ.</span><span class="sxs-lookup"><span data-stu-id="96639-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="96639-161">Typ této pomocné rutiny můžete uvést omezená kolekce například zobrazeném obory názvů, z nichž každý přímo obsahuje konečný počet opravili, například poskytované typy.</span><span class="sxs-lookup"><span data-stu-id="96639-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="96639-162">V tomto kontextu, zprostředkovatel *například* generuje typy, i když nejsou potřeba nebo použít.</span><span class="sxs-lookup"><span data-stu-id="96639-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="96639-163">V dalším kroku definujte místní soukromé hodnoty, které určují obor názvů pro poskytnutých typů a najít sestavení zprostředkovatele na typ, samotný.</span><span class="sxs-lookup"><span data-stu-id="96639-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="96639-164">Toto sestavení se později používá jako logický nadřazený typ vymazaného typů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="96639-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="96639-165">Dále vytvořte funkce se každý typ Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="96639-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="96639-166">Tato funkce je vysvětlené podrobněji dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="96639-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="96639-167">Dále vygenerujte 100 poskytnutých typů:</span><span class="sxs-lookup"><span data-stu-id="96639-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="96639-168">V dalším kroku přidejte typy jako zadaný obor názvů:</span><span class="sxs-lookup"><span data-stu-id="96639-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="96639-169">Nakonec přidejte atribut sestavení, která označuje, že při vytváření poskytovatele typu knihovny DLL:</span><span class="sxs-lookup"><span data-stu-id="96639-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="96639-170">Poskytuje jeden typ a její členy</span><span class="sxs-lookup"><span data-stu-id="96639-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="96639-171">`makeOneProvidedType` Funkce odvádí skutečnou práci poskytnout jeden z typů.</span><span class="sxs-lookup"><span data-stu-id="96639-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="96639-172">Tento krok popisuje implementaci této funkce.</span><span class="sxs-lookup"><span data-stu-id="96639-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="96639-173">Nejprve vytvořte poskytnutého typu (například Type1, když n = 1, nebo Type57, když n = 57).</span><span class="sxs-lookup"><span data-stu-id="96639-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="96639-174">Nezapomeňte přitom následující body:</span><span class="sxs-lookup"><span data-stu-id="96639-174">You should note the following points:</span></span>

- <span data-ttu-id="96639-175">To za předpokladu, že typ se vymažou.</span><span class="sxs-lookup"><span data-stu-id="96639-175">This provided type is erased.</span></span>  <span data-ttu-id="96639-176">Protože určujete, že je základní typ `obj`, instance se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="96639-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="96639-177">Když zadáte nevnořeném typu, je nutné zadat sestavení a oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="96639-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="96639-178">Pro mazání typy by měl být sestavení sestavení zprostředkovatele na typ, samotný.</span><span class="sxs-lookup"><span data-stu-id="96639-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="96639-179">V dalším kroku přidáte dokumentace XML typu.</span><span class="sxs-lookup"><span data-stu-id="96639-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="96639-180">Tato dokumentace je zpoždění, to znamená, vyžaduje kompilátor hostitele, je-li vypočítat na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="96639-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="96639-181">Dále přidáte zadaná statická vlastnost typu:</span><span class="sxs-lookup"><span data-stu-id="96639-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="96639-182">Získání této vlastnosti bude vždy vyhodnocena jako řetězec "Hello!".</span><span class="sxs-lookup"><span data-stu-id="96639-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="96639-183">`GetterCode` Pro vlastnost používá F # v citaci, která představuje kód, který kompilátor hostitele generuje pro získání vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="96639-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="96639-184">Další informace o nabídkách najdete v tématu [uvozovky kódu (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="96639-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="96639-185">Přidáte vlastnost dokumentace XML.</span><span class="sxs-lookup"><span data-stu-id="96639-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="96639-186">Zadaná vlastnost je teď možné připojte ke poskytnutého typu.</span><span class="sxs-lookup"><span data-stu-id="96639-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="96639-187">Zadaný člen musí připojit k jeden a pouze jeden typ.</span><span class="sxs-lookup"><span data-stu-id="96639-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="96639-188">V opačném případě člen již nikdy nebude přístupná.</span><span class="sxs-lookup"><span data-stu-id="96639-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="96639-189">Teď vytvořte zadaný konstruktor, který nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="96639-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="96639-190">`InvokeCode` Pro konstruktor vrátí F # v citaci, která představuje kód, který kompilátor hostitele generuje při volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="96639-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="96639-191">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="96639-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="96639-192">Instance zadaného typu se vytvoří s podkladová data "Data objektu".</span><span class="sxs-lookup"><span data-stu-id="96639-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="96639-193">Kód v uvozovkách zahrnuje převod na [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) vzhledem k tomu, že je tento typ vymazání tento poskytnutý typ (protože jste zadali, pokud jste deklarovali poskytnutého typu).</span><span class="sxs-lookup"><span data-stu-id="96639-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="96639-194">Přidejte dokumentace XML do konstruktoru a přidejte zadaný konstruktor pro zadaný typ:</span><span class="sxs-lookup"><span data-stu-id="96639-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="96639-195">Vytvořte druhý zadaný konstruktor, který přijímá jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="96639-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="96639-196">`InvokeCode` Pro konstruktor vrátí znovu F # v citaci, která představuje kód generovaný kompilátorem hostitele pro volání do metody.</span><span class="sxs-lookup"><span data-stu-id="96639-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="96639-197">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="96639-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="96639-198">S podkladová data "10" je vytvořena instance zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="96639-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="96639-199">Jste si už všimli, `InvokeCode` funkce vrátí do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="96639-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="96639-200">Vstup pro tuto funkci je seznamem výrazů, jeden pro každý parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="96639-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="96639-201">V tomto případě je k dispozici ve výrazu, který představuje hodnotu jednoho parametru `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="96639-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="96639-202">Kód pro volání konstruktoru převede návratovou hodnotu na typ vymazaného `obj`.</span><span class="sxs-lookup"><span data-stu-id="96639-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="96639-203">Poté, co přidáte druhý zadaný konstruktor pro typ, vytvoříte zadanou instanci vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="96639-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="96639-204">Získávání tato vlastnost vrátí délku řetězce, který je reprezentace objektu.</span><span class="sxs-lookup"><span data-stu-id="96639-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="96639-205">`GetterCode` Vlastnost vrací nabídky F #, která určuje kód, který generuje kompilátor hostitele GET pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="96639-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="96639-206">Stejně jako `InvokeCode`, `GetterCode` funkce vrátí do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="96639-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="96639-207">Kompilátor hostitele volání této funkce se seznamem argumentů.</span><span class="sxs-lookup"><span data-stu-id="96639-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="96639-208">V takovém případě argumenty zahrnout pouze jediný výraz, který představuje instanci, na kterém je volána metoda getter, kterým můžete přistupovat pomocí `args.[0]`. Provádění `GetterCode` klikněte do nabídky výsledek mazání zadejte splices `obj`, a tím se uspokojí kompilátoru mechanismus pro kontrolu typů, že objekt je řetězec se používá přetypování.</span><span class="sxs-lookup"><span data-stu-id="96639-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="96639-209">V další části `makeOneProvidedType` poskytuje metodu instance s jedním parametrem.</span><span class="sxs-lookup"><span data-stu-id="96639-209">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="96639-210">Nakonec vytvořte vnořený typ, který obsahuje 100 vnořené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="96639-210">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="96639-211">Vytvoření tohoto vnořený typ a jeho vlastnosti je zpoždění, to znamená, vypočítat na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="96639-211">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="96639-212">Podrobnosti o vymazaných poskytnutých typů</span><span class="sxs-lookup"><span data-stu-id="96639-212">Details about Erased Provided Types</span></span>

<span data-ttu-id="96639-213">Příklad v této části uvádí pouze *vymaže poskytnutých typů*, které jsou obzvláště užitečná v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="96639-213">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="96639-214">Když vytváříte zprostředkovatele pro informační prostor, který obsahuje pouze data a metody.</span><span class="sxs-lookup"><span data-stu-id="96639-214">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="96639-215">Když vytváříte poskytovatele, kde sémantiku přesný typ modulu runtime nejsou zásadně důležité pro praktické využití místa na informace.</span><span class="sxs-lookup"><span data-stu-id="96639-215">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="96639-216">Když vytváříte zprostředkovatele pro informační prostor, který je tak velký a propojených, že není technicky možné generovat skutečné typy .NET pro informační prostor.</span><span class="sxs-lookup"><span data-stu-id="96639-216">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="96639-217">V tomto příkladu každý zadaný typ se vymažou na typ `obj`, a zobrazí se všechna použití typu jako typ `obj` v zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="96639-217">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="96639-218">Ve skutečnosti příslušné objekty v těchto příkladech jsou řetězce, ale zobrazí se jako typ `System.Object` v .NET zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="96639-218">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="96639-219">I s všechna použití typ vymazání, můžete použít explicitní zabalení, rozbalení a přetypování na pokazit vymazány typy.</span><span class="sxs-lookup"><span data-stu-id="96639-219">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="96639-220">V takovém případě může dojít k výjimce přetypování, který není platný při použití objektu.</span><span class="sxs-lookup"><span data-stu-id="96639-220">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="96639-221">Zprostředkovatel modulu runtime můžete definovat vlastní privátní reprezentace typ a pomáhá chránit před false reprezentace.</span><span class="sxs-lookup"><span data-stu-id="96639-221">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="96639-222">Nejde definovat vymazaného typy v jazyce F # samotný.</span><span class="sxs-lookup"><span data-stu-id="96639-222">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="96639-223">Pouze poskytnutých typů mohou být vymazány.</span><span class="sxs-lookup"><span data-stu-id="96639-223">Only provided types may be erased.</span></span> <span data-ttu-id="96639-224">Je třeba porozumět následky, obě praktických a sémantické, buď pomocí vymaže vymazaného typy pro poskytovatele typu nebo zprostředkovatele, který obsahuje typy.</span><span class="sxs-lookup"><span data-stu-id="96639-224">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="96639-225">Mazání typ nemá žádný skutečný typ .NET.</span><span class="sxs-lookup"><span data-stu-id="96639-225">An erased type has no real .NET type.</span></span> <span data-ttu-id="96639-226">Proto není přesný odraz přes typ a může pokazit vymazaného typy, pokud použijete přetypování modulu runtime a další techniky, které jsou závislé na přesné modulu runtime typu sémantiku.</span><span class="sxs-lookup"><span data-stu-id="96639-226">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="96639-227">Subversion vymazaného typy často výsledkem přetypování typu výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="96639-227">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="96639-228">Výběr reprezentace pro vymazání poskytované typy</span><span class="sxs-lookup"><span data-stu-id="96639-228">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="96639-229">Pro některá použití vymazaných poskytnutých typů žádné reprezentace je povinný.</span><span class="sxs-lookup"><span data-stu-id="96639-229">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="96639-230">Například vymazaného zadaný typ může obsahovat pouze statické vlastnosti a členů a žádné konstruktory a žádné vlastnosti nebo metody vrátí instanci typu.</span><span class="sxs-lookup"><span data-stu-id="96639-230">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="96639-231">Pokud instance vymazaného může dosáhnout zadaný typ, musíte zvážit následující otázky:</span><span class="sxs-lookup"><span data-stu-id="96639-231">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="96639-232">**Co je mazání poskytnutého typu?**</span><span class="sxs-lookup"><span data-stu-id="96639-232">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="96639-233">Mazání poskytnutého typu je, jak se typ vyskytuje v kompilovaného kódu .NET.</span><span class="sxs-lookup"><span data-stu-id="96639-233">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="96639-234">Mazání typu zadaný vymazaného třídy je vždy první-vymaže základním typem v řetězu dědičnosti typu.</span><span class="sxs-lookup"><span data-stu-id="96639-234">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="96639-235">Mazání vymazaného poskytnutého rozhraní typu je vždy `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="96639-235">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="96639-236">**Co jsou reprezentace poskytnutého typu?**</span><span class="sxs-lookup"><span data-stu-id="96639-236">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="96639-237">Sadu možných objektů pro mazání zadaný typ, se nazývají její reprezentace.</span><span class="sxs-lookup"><span data-stu-id="96639-237">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="96639-238">V příkladu v tomto dokumentu, všechny k dispozici vymazaného reprezentace typů `Type1..Type100` jsou vždy řetězcových objektů.</span><span class="sxs-lookup"><span data-stu-id="96639-238">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="96639-239">Všechny reprezentace poskytnutého typu musí být kompatibilní s mazání poskytnutého typu.</span><span class="sxs-lookup"><span data-stu-id="96639-239">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="96639-240">(V opačném případě kompilátor jazyka F # vám poskytne chybu pro používání poskytovatele typu, nebo se vygeneruje neověřitelného kódu .NET, která není platná.</span><span class="sxs-lookup"><span data-stu-id="96639-240">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="96639-241">Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)</span><span class="sxs-lookup"><span data-stu-id="96639-241">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="96639-242">Reprezentace zadaných objektů můžete pomocí některé z následujících dvou přístupů, které jsou běžně:</span><span class="sxs-lookup"><span data-stu-id="96639-242">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="96639-243">Pokud zadáváte jednoduše obálky se silným typem přes existující typ formátu .NET, často má smysl pro váš typ chcete smazat tento typ, použijte instance tohoto typu jako reprezentace nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="96639-243">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="96639-244">Tento přístup je vhodné, pokud většina existující metody na typu stále dávat smysl, jestli používáte verzi silného typu.</span><span class="sxs-lookup"><span data-stu-id="96639-244">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="96639-245">Pokud chcete vytvořit rozhraní API, které se liší výrazně z libovolného existujícího rozhraní API .NET, je vhodné vytvořit typy modulu runtime, které budou typu mazání a reprezentací pro poskytnutých typů.</span><span class="sxs-lookup"><span data-stu-id="96639-245">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="96639-246">V příkladu v tomto dokumentu používá řetězce jako reprezentace zadaných objektů.</span><span class="sxs-lookup"><span data-stu-id="96639-246">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="96639-247">Často může být vhodné k použití jiných objektů pro vyjádření.</span><span class="sxs-lookup"><span data-stu-id="96639-247">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="96639-248">Například můžete použít slovník jako kontejner objektů:</span><span class="sxs-lookup"><span data-stu-id="96639-248">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="96639-249">Jako alternativu můžete definovat typ ve zprostředkovateli typu, který se použije v době běhu k reprezentaci, spolu s jednu nebo více operací modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="96639-249">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="96639-250">Pokud členové pak lze vytvořit instance tohoto typu objektu:</span><span class="sxs-lookup"><span data-stu-id="96639-250">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="96639-251">V takovém případě může (volitelně) použijete tento typ jako typ vymazání tak, že zadáte tento typ jako `baseType` při vytváření `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="96639-251">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="96639-252">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="96639-252">Key Lessons</span></span>

<span data-ttu-id="96639-253">V předchozím oddílu bylo vysvětleno, jak vytvořit jednoduchý mazání typ zprostředkovatele, který poskytuje celou řadu typy, vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="96639-253">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="96639-254">Tato část také vysvětlení konceptu mazání typu, včetně některých výhod a nevýhod poskytující vymazaného typy od zprostředkovatele typu a popsaných reprezentace vymazaného typy.</span><span class="sxs-lookup"><span data-stu-id="96639-254">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="96639-255">Typ zprostředkovatele, který používá statické parametry</span><span class="sxs-lookup"><span data-stu-id="96639-255">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="96639-256">Schopnost parametrizovat poskytovatelů typů ve statických dat umožňuje řadu zajímavých scénářů, dokonce i v případech, kdy zprostředkovatel nepotřebuje přístup k žádným datům místního nebo vzdáleného.</span><span class="sxs-lookup"><span data-stu-id="96639-256">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="96639-257">V této části se dozvíte některé základní postupy pro takový zprostředkovatel sestavení.</span><span class="sxs-lookup"><span data-stu-id="96639-257">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="96639-258">Typ zaškrtnutí poskytovatele regulární výraz</span><span class="sxs-lookup"><span data-stu-id="96639-258">Type Checked Regex Provider</span></span>

<span data-ttu-id="96639-259">Představte si, že chcete implementovat poskytovatel typů pro regulární výrazy, které zabaluje rozhraní .NET <xref:System.Text.RegularExpressions.Regex> knihovny v rozhraní, které poskytuje následující záruky za kompilace:</span><span class="sxs-lookup"><span data-stu-id="96639-259">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="96639-260">Ověřuje se, zda je platný regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="96639-260">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="96639-261">Poskytuje pojmenované vlastnosti na shody, které jsou založeny na všechny názvy skupin v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="96639-261">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="96639-262">Tato část ukazuje, jak vytvořit pomocí zprostředkovatelů typů `RegexTyped` zadejte, že vzor regulárního výrazu parametrizuje poskytuje tyto výhody.</span><span class="sxs-lookup"><span data-stu-id="96639-262">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="96639-263">Kompilátor oznámí chybu, pokud zadaný vzor není platný a poskytovatele typu může extrahovat skupiny ze vzorku tak, aby vám můžou k nim přistupovat pomocí vlastnosti shody s názvem.</span><span class="sxs-lookup"><span data-stu-id="96639-263">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="96639-264">Při návrhu poskytovatele typů, byste měli zvážit, jak by měl vypadat jeho vystavené rozhraní API pro koncové uživatele a jak se tento návrh přeloží do kódu .NET.</span><span class="sxs-lookup"><span data-stu-id="96639-264">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="96639-265">Následující příklad ukazuje, jak získat komponenty směrové číslo oblasti pomocí těchto rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="96639-265">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="96639-266">Následující příklad ukazuje, jak se zprostředkovatel typu přeloží těchto volání:</span><span class="sxs-lookup"><span data-stu-id="96639-266">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="96639-267">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="96639-267">Note the following points:</span></span>

- <span data-ttu-id="96639-268">Představuje standardní typ regulární výraz parametrizovaný `RegexTyped` typu.</span><span class="sxs-lookup"><span data-stu-id="96639-268">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="96639-269">`RegexTyped` Konstruktor výsledkem je volání konstruktoru Regex předání argumentu statického typu pro vzor.</span><span class="sxs-lookup"><span data-stu-id="96639-269">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="96639-270">Výsledky `Match` metody jsou reprezentovány standardní <xref:System.Text.RegularExpressions.Match> typu.</span><span class="sxs-lookup"><span data-stu-id="96639-270">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="96639-271">Každou pojmenovanou skupinu výsledkem zadaná vlastnost a přístupem k vlastnosti výsledkem použití indexer na shodu `Groups` kolekce.</span><span class="sxs-lookup"><span data-stu-id="96639-271">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="96639-272">Následující kód je základní logiku pro implementaci těchto zprostředkovatele a v tomto příkladu vynechá přidání všem členům poskytnutého typu.</span><span class="sxs-lookup"><span data-stu-id="96639-272">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="96639-273">Informace o každý přidaný člen najdete v příslušné části dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="96639-273">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="96639-274">Celý kód lze stáhnout ukázku z [F # 3.0 ukázkového balíčku](https://fsharp3sample.codeplex.com) na webu Codeplex.</span><span class="sxs-lookup"><span data-stu-id="96639-274">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

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

<span data-ttu-id="96639-275">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="96639-275">Note the following points:</span></span>

- <span data-ttu-id="96639-276">Zprostředkovatel typu přebírá dva parametry statické: `pattern`, což je povinné a `options`, (protože výchozí hodnota je zadáno) jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="96639-276">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="96639-277">Po statické argumenty jsou dodávány, vytvoříte instanci regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="96639-277">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="96639-278">Tato instance vyvolá výjimku, pokud regulární výraz je poškozený a ohlásí tuto chybu pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="96639-278">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="96639-279">V rámci `DefineStaticParameters` zpětné volání, definujte typ, který bude vrácen, jakmile jsou zadané argumenty.</span><span class="sxs-lookup"><span data-stu-id="96639-279">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="96639-280">Tento kód nastaví `HideObjectMethods` na hodnotu true, tak, aby zůstane zjednodušené prostředí IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="96639-280">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="96639-281">Způsobí, že tento atribut `Equals`, `GetHashCode`, `Finalize`, a `GetType` členy mají být potlačena ze seznamů technologie IntelliSense pro zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="96639-281">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="96639-282">Použijete `obj` jako základní typ pro metodu, ale budete používat `Regex` objektu jako modul runtime reprezentaci tohoto typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="96639-282">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="96639-283">Volání `Regex` vyvolá konstruktor <xref:System.ArgumentException> kdy regulární výraz není platný.</span><span class="sxs-lookup"><span data-stu-id="96639-283">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="96639-284">Kompilátor tuto výjimku zachytí a ohlásí chybovou zprávu uživateli v době kompilace nebo v editoru sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96639-284">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="96639-285">Tato výjimka umožňuje regulárních výrazů má být ověřen bez spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="96639-285">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="96639-286">Typ definovaný výše není ještě užitečné, protože neobsahuje žádné smysluplné metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="96639-286">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="96639-287">Nejprve přidejte statickou `IsMatch` metody:</span><span class="sxs-lookup"><span data-stu-id="96639-287">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="96639-288">Předcházející kód definuje metodu `IsMatch`, který přijímá řetězec jako vstup a vrátí `bool`.</span><span class="sxs-lookup"><span data-stu-id="96639-288">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="96639-289">Pouze velmi obtížné část je použití `args` argument v rámci `InvokeCode` definice.</span><span class="sxs-lookup"><span data-stu-id="96639-289">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="96639-290">V tomto příkladu `args` je seznam nabídek, které představuje argumenty pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="96639-290">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="96639-291">Pokud je metoda metodou instance, představuje první argument `this` argument.</span><span class="sxs-lookup"><span data-stu-id="96639-291">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="96639-292">Pro statické metody, jsou argumenty všechny pouze explicitní argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="96639-292">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="96639-293">Všimněte si, že by měl odpovídat typu hodnoty v uvozovkách zadaný návratový typ (v tomto případě `bool`).</span><span class="sxs-lookup"><span data-stu-id="96639-293">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="96639-294">Všimněte si také, tento kód používá `AddXmlDoc` metodu, abyste měli jistotu, že zadaná metoda má také užitečná dokumentace, které můžete zadat pomocí IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="96639-294">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="96639-295">V dalším kroku přidáte instanci metody shoda.</span><span class="sxs-lookup"><span data-stu-id="96639-295">Next, add an instance Match method.</span></span> <span data-ttu-id="96639-296">Nicméně tato metoda by měla vrátit hodnotu zadaný `Match` tak, aby skupiny je přístupná v podobě silného typu.</span><span class="sxs-lookup"><span data-stu-id="96639-296">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="96639-297">Proto nejprve deklarujte `Match` typu.</span><span class="sxs-lookup"><span data-stu-id="96639-297">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="96639-298">Protože tento typ závisí na vzor, který byl zadán jako statický argument, tento typ musí být vnořen v rámci definice typ s parametry:</span><span class="sxs-lookup"><span data-stu-id="96639-298">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="96639-299">Pak přidejte jednu vlastnost typ shody pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="96639-299">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="96639-300">Za běhu, je reprezentována shoda <xref:System.Text.RegularExpressions.Match> hodnoty, takže musíte použít uvozovky, který definuje vlastnost <xref:System.Text.RegularExpressions.Match.Groups> indexovanou vlastnost zobrazíte příslušné skupiny.</span><span class="sxs-lookup"><span data-stu-id="96639-300">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="96639-301">Znovu si všimněte, že přidáváte dokumentace XML do zadané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="96639-301">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="96639-302">Všimněte si také, vlastnost může číst, pokud `GetterCode` funkce je k dispozici, a vlastnost je možné zapisovat, pokud `SetterCode` funkce je k dispozici, takže výsledné vlastnost je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="96639-302">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="96639-303">Nyní můžete vytvořit metodu instance, která vrací hodnotu tohoto `Match` typu:</span><span class="sxs-lookup"><span data-stu-id="96639-303">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="96639-304">Protože vytváříte metodu instance `args.[0]` představuje `RegexTyped` instanci, na kterém je volána metoda, a `args.[1]` je vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="96639-304">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="96639-305">A konečně Poskytněte konstruktor tak, že můžete vytvořit instance zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="96639-305">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="96639-306">Konstruktor vymaže pouze k vytvoření instance regulární výraz .NET standard, která je znovu zabalená do objektu, protože `obj` je mazání poskytnutého typu.</span><span class="sxs-lookup"><span data-stu-id="96639-306">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="96639-307">Díky této změně použití ukázkové rozhraní API, uvedenou výše v tomto tématu funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="96639-307">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="96639-308">Následující kód je kompletní a poslední:</span><span class="sxs-lookup"><span data-stu-id="96639-308">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="96639-309">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="96639-309">Key Lessons</span></span>

<span data-ttu-id="96639-310">Tato část bylo vysvětleno, jak vytvořit typ zprostředkovatele, který funguje na jeho statické parametry.</span><span class="sxs-lookup"><span data-stu-id="96639-310">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="96639-311">Zprostředkovatel ověří statický parametr a poskytuje operace na základě jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="96639-311">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="96639-312">Typ zprostředkovatele, který se zálohuje pomocí místních dat</span><span class="sxs-lookup"><span data-stu-id="96639-312">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="96639-313">Často můžete poskytovatelů typů zobrazíte rozhraní API založené na pouze statické parametry, ale také informace z místních nebo vzdálených systémů.</span><span class="sxs-lookup"><span data-stu-id="96639-313">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="96639-314">Tato část popisuje poskytovatelů typů, které jsou založeny na místní data, jako jsou místní datové soubory.</span><span class="sxs-lookup"><span data-stu-id="96639-314">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="96639-315">Zprostředkovatel souborů jednoduché sdíleného svazku clusteru</span><span class="sxs-lookup"><span data-stu-id="96639-315">Simple CSV File Provider</span></span>

<span data-ttu-id="96639-316">Jako jednoduchý příklad zvažte poskytovatele typu pro přístup k vědeckých dat ve formátu hodnota oddělených čárkami (CSV).</span><span class="sxs-lookup"><span data-stu-id="96639-316">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="96639-317">V této části se předpokládá, že soubory CSV obsahovat řádek záhlaví, za nímž následuje data s plovoucí desetinnou, jak ukazuje následující tabulka:</span><span class="sxs-lookup"><span data-stu-id="96639-317">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="96639-318">Distance (měření)</span><span class="sxs-lookup"><span data-stu-id="96639-318">Distance (meter)</span></span>|<span data-ttu-id="96639-319">Čas (sekundy)</span><span class="sxs-lookup"><span data-stu-id="96639-319">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="96639-320">50.0</span><span class="sxs-lookup"><span data-stu-id="96639-320">50.0</span></span>|<span data-ttu-id="96639-321">3.7</span><span class="sxs-lookup"><span data-stu-id="96639-321">3.7</span></span>|
|<span data-ttu-id="96639-322">100.0</span><span class="sxs-lookup"><span data-stu-id="96639-322">100.0</span></span>|<span data-ttu-id="96639-323">5.2</span><span class="sxs-lookup"><span data-stu-id="96639-323">5.2</span></span>|
|<span data-ttu-id="96639-324">150.0</span><span class="sxs-lookup"><span data-stu-id="96639-324">150.0</span></span>|<span data-ttu-id="96639-325">6.4</span><span class="sxs-lookup"><span data-stu-id="96639-325">6.4</span></span>|

<span data-ttu-id="96639-326">Tato část ukazuje, jak zadat typ, který vám umožní získat řádky s `Distance` vlastnost typu `float<meter>` a `Time` vlastnost typu `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="96639-326">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="96639-327">Pro jednoduchost jsou provedeny následující předpoklady:</span><span class="sxs-lookup"><span data-stu-id="96639-327">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="96639-328">Názvy záhlaví jsou buď jednotky bez nebo mít formát _služba ._protokol "Název" (jednotky) a neobsahují čárky.</span><span class="sxs-lookup"><span data-stu-id="96639-328">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="96639-329">Jednotky jsou všechny jednotky systém mezinárodní (SI) [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames – modul (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modul definuje.</span><span class="sxs-lookup"><span data-stu-id="96639-329">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="96639-330">Jednotky jsou všechny jednoduché (například měřit) spíše než složený (například měřiče za sekundu).</span><span class="sxs-lookup"><span data-stu-id="96639-330">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="96639-331">Všechny sloupce obsahují s plovoucí desetinnou čárkou datového bodu.</span><span class="sxs-lookup"><span data-stu-id="96639-331">All columns contain floating point data.</span></span>

<span data-ttu-id="96639-332">Úplnější poskytovatele by povolte těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="96639-332">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="96639-333">Prvním krokem je opět vzít v úvahu, jak by měl vypadat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="96639-333">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="96639-334">Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="96639-334">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="96639-335">V takovém případě by měl kompilátor převést těchto volání na něco jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="96639-335">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="96639-336">Optimální převod bude vyžadovat poskytovatele typu pro definování reálné `CsvFile` typ v sestavení poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="96639-336">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="96639-337">Zprostředkovatelé typů se často spoléhat na několik pomocné rutiny typy a metody k zabalení důležité logiku.</span><span class="sxs-lookup"><span data-stu-id="96639-337">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="96639-338">Míry jsou vymazány za běhu, takže můžete využívat `float[]` vymazaného typ pro řádek.</span><span class="sxs-lookup"><span data-stu-id="96639-338">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="96639-339">Kompilátor bude považovat různé sloupce s typy jiné míry.</span><span class="sxs-lookup"><span data-stu-id="96639-339">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="96639-340">Například první sloupec v našem příkladu má typ `float<meter>`, a druhý `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="96639-340">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="96639-341">Mazání reprezentace však může zůstat úplně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="96639-341">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="96639-342">Následující kód ukazuje základní implementaci.</span><span class="sxs-lookup"><span data-stu-id="96639-342">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="96639-343">Mějte na paměti následující skutečnosti o implementaci:</span><span class="sxs-lookup"><span data-stu-id="96639-343">Note the following points about the implementation:</span></span>

- <span data-ttu-id="96639-344">Přetížené konstruktory povolit původní soubor nebo ten, který má stejné schéma pro čtení.</span><span class="sxs-lookup"><span data-stu-id="96639-344">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="96639-345">Tento model je běžná v případě, že napíšete poskytovatele typu pro místní nebo vzdálené datové zdroje a tento model umožňuje místní soubor, který se použije jako šablonu pro vzdálená data.</span><span class="sxs-lookup"><span data-stu-id="96639-345">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="96639-346">Můžete použít [typeproviderconfig –](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) hodnotu, která je předán konstruktor zprostředkovatele typu k překladu názvů relativní souboru.</span><span class="sxs-lookup"><span data-stu-id="96639-346">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="96639-347">Můžete použít `AddDefinitionLocation` metodu pro určení umístění zadané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="96639-347">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="96639-348">Proto pokud používáte `Go To Definition` zadané vlastnosti, otevře se soubor CSV v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96639-348">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="96639-349">Můžete použít `ProvidedMeasureBuilder` typu k vyhledání jednotek SI a ke generování příslušného `float<_>` typy.</span><span class="sxs-lookup"><span data-stu-id="96639-349">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="96639-350">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="96639-350">Key Lessons</span></span>

<span data-ttu-id="96639-351">Tato část bylo vysvětleno, jak vytvořit poskytovatele typů pro místní zdroj dat s jednoduché schéma, které je obsažen ve zdroji dat, samotného.</span><span class="sxs-lookup"><span data-stu-id="96639-351">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="96639-352">Když budete pokračovat</span><span class="sxs-lookup"><span data-stu-id="96639-352">Going Further</span></span>

<span data-ttu-id="96639-353">Následující části obsahují návrhy pro další studie.</span><span class="sxs-lookup"><span data-stu-id="96639-353">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="96639-354">Podívejte se na zkompilovaný kód pro mazání typy</span><span class="sxs-lookup"><span data-stu-id="96639-354">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="96639-355">Abyste získali představu o tom, jak pomocí poskytovatele typu odpovídá kód, který je vygenerován, podívejte se na následující funkci pomocí `HelloWorldTypeProvider` , který se používá dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="96639-355">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="96639-356">Tady je obrázek výsledný kód decompiled pomocí ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="96639-356">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="96639-357">Jak ukazuje příklad, všechny zmínky typu `Type1` a `InstanceProperty` vlastnost byly vymazány, byste museli opustit pouze operace u typů modulu runtime používané.</span><span class="sxs-lookup"><span data-stu-id="96639-357">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="96639-358">Návrh a vytváření názvů pro zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="96639-358">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="96639-359">Prohlédněte si následující konvence při vytváření poskytovatelů typů.</span><span class="sxs-lookup"><span data-stu-id="96639-359">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="96639-360">**Poskytovatelé připojení protokolů** obecně by měly končit názvy zprostředkovatelů většinu knihoven DLL pro data a služby připojení protokolů, jako je připojení OData nebo SQL `TypeProvider` nebo `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="96639-360">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="96639-361">Například použijte název knihovny DLL, která se podobá následující řetězec:</span><span class="sxs-lookup"><span data-stu-id="96639-361">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="96639-362">Zkontrolujte, jestli jsou členové odpovídající obor názvů poskytnutých typů a označení připojení protokol, který jste implementovali:</span><span class="sxs-lookup"><span data-stu-id="96639-362">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="96639-363">**Nástroje zprostředkovatele pro obecné kódování**.</span><span class="sxs-lookup"><span data-stu-id="96639-363">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="96639-364">Pro nástroj poskytovatele typu jako, který je pro regulární výrazy poskytovatele typu, může být součástí základní knihovny, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="96639-364">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="96639-365">V takovém případě poskytnutého typu objevuje v odpovídajícím bodě podle normální návrhu konvence .NET:</span><span class="sxs-lookup"><span data-stu-id="96639-365">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="96639-366">**Zdroje dat typu singleton**.</span><span class="sxs-lookup"><span data-stu-id="96639-366">**Singleton Data Sources**.</span></span> <span data-ttu-id="96639-367">Někteří poskytovatelé typ připojení ke zdroji dat jeden vyhrazený a poskytují pouze data.</span><span class="sxs-lookup"><span data-stu-id="96639-367">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="96639-368">V takovém případě měl snížit `TypeProvider` přípony a použít běžné konvence pro pojmenování .NET:</span><span class="sxs-lookup"><span data-stu-id="96639-368">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="96639-369">Další informace najdete v tématu `GetConnection` návrh konvence, která je popsána dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="96639-369">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="96639-370">Způsoby návrhu pro zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="96639-370">Design Patterns for Type Providers</span></span>

<span data-ttu-id="96639-371">Následující části popisují vzorů návrhu, které můžete použít při vytváření poskytovatelů typů.</span><span class="sxs-lookup"><span data-stu-id="96639-371">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="96639-372">Vzor návrhu GetConnection</span><span class="sxs-lookup"><span data-stu-id="96639-372">The GetConnection Design Pattern</span></span>

<span data-ttu-id="96639-373">Většina poskytovatelů typů by měly být napsány k použití `GetConnection` vzor, který používá typ zprostředkovatele v FSharp.Data.TypeProviders.dll, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="96639-373">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="96639-374">Zprostředkovatelé typů se opírá o vzdáleným datům a službám</span><span class="sxs-lookup"><span data-stu-id="96639-374">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="96639-375">Než vytvoříte poskytovatele typu, který je zajištěná vzdáleným datům a službám, je nutné zvážit řadu problémů, které vyplývají z připojených programování.</span><span class="sxs-lookup"><span data-stu-id="96639-375">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="96639-376">Tyto problémy v úvahu následující aspekty:</span><span class="sxs-lookup"><span data-stu-id="96639-376">These issues include the following considerations:</span></span>

- <span data-ttu-id="96639-377">mapování schématu</span><span class="sxs-lookup"><span data-stu-id="96639-377">schema mapping</span></span>

- <span data-ttu-id="96639-378">aktivity a zneplatnění za přítomnosti změny schématu</span><span class="sxs-lookup"><span data-stu-id="96639-378">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="96639-379">schéma, ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="96639-379">schema caching</span></span>

- <span data-ttu-id="96639-380">implementace asynchronní operací přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="96639-380">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="96639-381">Podpora dotazů, včetně dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="96639-381">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="96639-382">pověření a ověřování</span><span class="sxs-lookup"><span data-stu-id="96639-382">credentials and authentication</span></span>

<span data-ttu-id="96639-383">Toto téma není prozkoumat tyto problémy dále.</span><span class="sxs-lookup"><span data-stu-id="96639-383">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="96639-384">Další postupy pro vytváření obsahu</span><span class="sxs-lookup"><span data-stu-id="96639-384">Additional Authoring Techniques</span></span>

<span data-ttu-id="96639-385">Při psaní vlastních poskytovatelů typů, můžete použít následující další techniky.</span><span class="sxs-lookup"><span data-stu-id="96639-385">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="96639-386">Vytváření typů a členů na vyžádání</span><span class="sxs-lookup"><span data-stu-id="96639-386">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="96639-387">Rozhraní API ProvidedType má zpoždění verzích přidávat členy.</span><span class="sxs-lookup"><span data-stu-id="96639-387">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="96639-388">Tyto verze se používají k vytvoření mezer na vyžádání z typů.</span><span class="sxs-lookup"><span data-stu-id="96639-388">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="96639-389">Poskytuje typy polí a vytváření instancí obecného typu</span><span class="sxs-lookup"><span data-stu-id="96639-389">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="96639-390">Zkontrolujte zadaný členy (jehož podpisy zahrnují vytváření instancí obecné typy, typy polí a typy byref) s použitím normální `MakeArrayType`, `MakePointerType`, a `MakeGenericType` na jakoukoli instanci <xref:System.Type>, včetně `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="96639-390">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="96639-391">V některých případech bude pravděpodobně nutné použít Pomocník `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="96639-391">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="96639-392">Najdete v článku [dokumentace k sadě SDK zprostředkovatele typu](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="96639-392">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="96639-393">Poskytuje jednotka měření poznámky</span><span class="sxs-lookup"><span data-stu-id="96639-393">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="96639-394">Rozhraní API pro ProvidedTypes poskytuje pomocné rutiny pro poskytování míru poznámky.</span><span class="sxs-lookup"><span data-stu-id="96639-394">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="96639-395">Například zadejte typ `float<kg>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="96639-395">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="96639-396">K poskytování typ `Nullable<decimal<kg/m^2>>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="96639-396">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="96639-397">Přístup k prostředkům místních pro projekt nebo místní skript</span><span class="sxs-lookup"><span data-stu-id="96639-397">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="96639-398">Mohou být zadány všechny instance poskytovatele typu `TypeProviderConfig` hodnota během konstrukce.</span><span class="sxs-lookup"><span data-stu-id="96639-398">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="96639-399">Tato hodnota obsahuje poskytovatele (to znamená, složky projektu pro sestavení nebo adresáře, který obsahuje skript), seznam odkazovaných sestavení a další informace o složce"řešení".</span><span class="sxs-lookup"><span data-stu-id="96639-399">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="96639-400">Zrušení</span><span class="sxs-lookup"><span data-stu-id="96639-400">Invalidation</span></span>

<span data-ttu-id="96639-401">Poskytovatelé může vyvolat zneplatnění signály upozornit službu jazyka F #, která mohlo dojít ke změně schématu předpoklady.</span><span class="sxs-lookup"><span data-stu-id="96639-401">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="96639-402">Pokud dojde k zrušení, typecheck je znovu, pokud zprostředkovatel je hostovaná v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96639-402">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="96639-403">Tento signál budou ignorovány, pokud zprostředkovatel je hostovaný v jazyce F # Interactive nebo kompilátorem F # (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="96639-403">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="96639-404">Ukládání do mezipaměti informace o schématu</span><span class="sxs-lookup"><span data-stu-id="96639-404">Caching Schema Information</span></span>

<span data-ttu-id="96639-405">Poskytovatelé musí často ukládat do mezipaměti přístup k informacím o schématu.</span><span class="sxs-lookup"><span data-stu-id="96639-405">Providers must often cache access to schema information.</span></span> <span data-ttu-id="96639-406">Data uložená v mezipaměti ukládat pomocí názvu souboru, který je přiřazen jako statický parametr nebo jako uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="96639-406">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="96639-407">Je například ukládání do mezipaměti schématu `LocalSchemaFile` parametr ve zprostředkovateli typů v `FSharp.Data.TypeProviders` sestavení.</span><span class="sxs-lookup"><span data-stu-id="96639-407">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="96639-408">Při provádění těchto zprostředkovatelů tento statický parametr nařídí zprostředkovateli typu použít informace o schématu v zadaném souboru místní místo přístup ke zdroji dat přes síť.</span><span class="sxs-lookup"><span data-stu-id="96639-408">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="96639-409">Pokud chcete používat informace uložené v mezipaměti schématu, musíte taky nastavit statický parametr `ForceUpdate` k `false`.</span><span class="sxs-lookup"><span data-stu-id="96639-409">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="96639-410">Podobný postup můžete použít k povolení přístupu k datům online i offline.</span><span class="sxs-lookup"><span data-stu-id="96639-410">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="96639-411">Základní sestavení</span><span class="sxs-lookup"><span data-stu-id="96639-411">Backing Assembly</span></span>

<span data-ttu-id="96639-412">Pokud kompilujete `.dll` nebo `.exe` soubor, záložní soubor .dll pro generované typy je staticky propojené do výsledného sestavení.</span><span class="sxs-lookup"><span data-stu-id="96639-412">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="96639-413">Tento odkaz se vytvoří tak, že zkopírujete definice typu Intermediate Language (IL) a všechny spravované prostředky z zálohování sestavení do konečného sestavení.</span><span class="sxs-lookup"><span data-stu-id="96639-413">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="96639-414">Při použití jazyka F # Interactive, záložní soubor DLL není zkopírován a místo toho načtení přímo do procesu F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="96639-414">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="96639-415">Výjimky a Diagnostika ze zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="96639-415">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="96639-416">Všechny výskyty všechny členy z poskytnutých typů může vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="96639-416">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="96639-417">Ve všech případech Pokud zprostředkovatel typu vyvolá výjimku, kompilátor hostitele atributy chyby na konkrétní typ poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="96639-417">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="96639-418">Typ zprostředkovatele výjimky by nikdy výsledkem vnitřních chybách kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="96639-418">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="96639-419">Zprostředkovatelé typů nejde hlásit upozornění.</span><span class="sxs-lookup"><span data-stu-id="96639-419">Type providers can't report warnings.</span></span>

- <span data-ttu-id="96639-420">Pokud zprostředkovatele typů je hostovaný v kompilátoru F #, F #. vývojové prostředí nebo F # Interactive, jsou zachyceny všechny výjimky z tohoto zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="96639-420">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="96639-421">Vlastnost Message je vždy text chyby a zobrazí se žádná trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="96639-421">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="96639-422">Pokud se chystáte vytvořit výjimku, může vyvolat následující příklady: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="96639-422">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="96639-423">Poskytuje generované typy</span><span class="sxs-lookup"><span data-stu-id="96639-423">Providing Generated Types</span></span>

<span data-ttu-id="96639-424">Tento dokument má zatím vysvětlil, jak poskytnout vymazaného typy.</span><span class="sxs-lookup"><span data-stu-id="96639-424">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="96639-425">Zajistit generované typy, které se přidají jako skutečné definice typů .NET do programu uživatelů můžete také použít mechanismus poskytovatele typu v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="96639-425">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="96639-426">Musíte odkazovat na vygenerované poskytované typy pomocí definice typu.</span><span class="sxs-lookup"><span data-stu-id="96639-426">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="96639-427">Kód ProvidedTypes-0.2 pomocné rutiny, která je součástí verze F # 3.0 má omezenou podporu pro poskytování generované typy.</span><span class="sxs-lookup"><span data-stu-id="96639-427">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="96639-428">Generovaný typ definice musí platit následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="96639-428">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="96639-429">`isErased` musí být nastaveno na `false`.</span><span class="sxs-lookup"><span data-stu-id="96639-429">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="96639-430">Generovaný typ musí být přidán do nově vytvořeného `ProvidedAssembly()`, která představuje kontejner pro fragmenty generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="96639-430">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="96639-431">Poskytovatel musí mít sestavení, který má skutečné záložní soubor .dll .NET s odpovídající soubor DLL na disku.</span><span class="sxs-lookup"><span data-stu-id="96639-431">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="96639-432">Pravidla a omezení</span><span class="sxs-lookup"><span data-stu-id="96639-432">Rules and Limitations</span></span>

<span data-ttu-id="96639-433">Při zápisu poskytovatelů typů, uvědomte si následující pravidla a omezení.</span><span class="sxs-lookup"><span data-stu-id="96639-433">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="96639-434">Poskytnutých typů musí být dosažitelná</span><span class="sxs-lookup"><span data-stu-id="96639-434">Provided types must be reachable</span></span>

<span data-ttu-id="96639-435">Všechny za předpokladu, že typy by měly být dosažitelný z jiných vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="96639-435">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="96639-436">Vnořené typy jsou uvedeny ve volání `TypeProviderForNamespaces` konstruktoru nebo volání `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="96639-436">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="96639-437">Například, pokud zprostředkovatel poskytuje typ `StaticClass.P : T`, ujistěte se, že je T nevnořeném typu nebo vnořené v části o jednu.</span><span class="sxs-lookup"><span data-stu-id="96639-437">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="96639-438">Například někteří poskytovatelé, jako mají statickou třídu `DataTypes` , které obsahují tyto `T1, T2, T3, ...` typy.</span><span class="sxs-lookup"><span data-stu-id="96639-438">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="96639-439">V opačném případě chyba říká, že byl nalezen odkaz na typ T v sestavení A, ale typ nebyl nalezen v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="96639-439">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="96639-440">Pokud tato chyba se zobrazí, ověřte, že všechny podtypy dosažitelný z poskytovatele typů.</span><span class="sxs-lookup"><span data-stu-id="96639-440">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="96639-441">Poznámka: Tyto `T1, T2, T3...` typy jsou označovány jako *na průběžné* typy.</span><span class="sxs-lookup"><span data-stu-id="96639-441">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="96639-442">Mějte na paměti do přístupné obor názvů nebo nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="96639-442">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="96639-443">Omezení mechanismu pro zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="96639-443">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="96639-444">Mechanismus poskytovatele typu v jazyce F # má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="96639-444">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="96639-445">Základní infrastruktury pro poskytovatele typu v jazyce F # nepodporuje obecné typy nebo obecné metody k dispozici.</span><span class="sxs-lookup"><span data-stu-id="96639-445">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="96639-446">Mechanismus nepodporuje vnořené typy se statické parametry.</span><span class="sxs-lookup"><span data-stu-id="96639-446">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="96639-447">Tipy pro vývoj</span><span class="sxs-lookup"><span data-stu-id="96639-447">Development Tips</span></span>

<span data-ttu-id="96639-448">Následující tipy mohou být užitečné během procesu vývoje.</span><span class="sxs-lookup"><span data-stu-id="96639-448">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="96639-449">Spusťte dvě instance sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="96639-449">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="96639-450">Můžete vyvíjet v jedné instanci poskytovatele typu a testovat zprostředkovatele v jiném, protože testovací prostředí IDE se zámek na souboru .dll, který brání poskytovatele typu se provádělo opětovné sestavení.</span><span class="sxs-lookup"><span data-stu-id="96639-450">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="96639-451">Proto je třeba zavřít druhou instanci aplikace Visual Studio a poskytovatel je součástí první instance, a pak musíte znovu otevřete druhou instanci po sestavení zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="96639-451">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="96639-452">Ladění pomocí volání fsc.exe zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="96639-452">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="96639-453">Zprostředkovatelé typů lze vyvolat pomocí následujících nástrojů:</span><span class="sxs-lookup"><span data-stu-id="96639-453">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="96639-454">FSC.exe (příkazového řádku kompilátoru jazyka F #)</span><span class="sxs-lookup"><span data-stu-id="96639-454">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="96639-455">fsi.exe (jazyce F # Interactive kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="96639-455">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="96639-456">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="96639-456">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="96639-457">Zprostředkovatelé typů můžete ladit často nejsnadněji pomocí fsc.exe na soubor skriptu testu (například script.fsx).</span><span class="sxs-lookup"><span data-stu-id="96639-457">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="96639-458">Můžete spustit ladicí program z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="96639-458">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="96639-459">Můžete použít protokolování tiskových stdout.</span><span class="sxs-lookup"><span data-stu-id="96639-459">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="96639-460">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96639-460">See also</span></span>

- [<span data-ttu-id="96639-461">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="96639-461">Type Providers</span></span>](index.md)
- [<span data-ttu-id="96639-462">Typ poskytovatele sady SDK</span><span class="sxs-lookup"><span data-stu-id="96639-462">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
