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
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="889d5-103">Kurz: Vytvoření poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="889d5-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="889d5-104">Mechanismus zprostředkovatele typu v jazyce F# je významnou součástí jeho podpory pro programování bohaté na informace.</span><span class="sxs-lookup"><span data-stu-id="889d5-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="889d5-105">Tento kurz vysvětluje, jak vytvořit vlastní poskytovatele typů tím, že vás provede vývojem několika poskytovatelů jednoduchých typů pro ilustraci základních konceptů.</span><span class="sxs-lookup"><span data-stu-id="889d5-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="889d5-106">Další informace o mechanismu poskytovatele typu ve f#, naleznete v [tématu Type Providers](index.md).</span><span class="sxs-lookup"><span data-stu-id="889d5-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="889d5-107">Ekosystém F# obsahuje řadu poskytovatelů typů pro běžně používané internetové a podnikové datové služby.</span><span class="sxs-lookup"><span data-stu-id="889d5-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="889d5-108">Například:</span><span class="sxs-lookup"><span data-stu-id="889d5-108">For example:</span></span>

- <span data-ttu-id="889d5-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) zahrnuje zprostředkovatele typů pro formáty dokumentů JSON, XML, CSV a HTML.</span><span class="sxs-lookup"><span data-stu-id="889d5-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="889d5-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje silný typ přístupu k databázím SQL prostřednictvím mapování objektů a F# LINQ dotazy proti těmto zdrojům dat.</span><span class="sxs-lookup"><span data-stu-id="889d5-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="889d5-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) má sadu poskytovatelů typu pro kontrolu dat v době kompilace vkládání T-SQL v F#.</span><span class="sxs-lookup"><span data-stu-id="889d5-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="889d5-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sada poskytovatelů typů pro použití pouze s programováním rozhraní .NET Framework pro přístup k datovým službám SQL, Entity Framework, OData a WSDL.</span><span class="sxs-lookup"><span data-stu-id="889d5-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="889d5-113">V případě potřeby můžete vytvořit vlastní poskytovatele typů nebo můžete odkazovat na poskytovatele typů, které vytvořili jiní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="889d5-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="889d5-114">Vaše organizace může mít například datovou službu, která poskytuje velký a rostoucí počet pojmenovaných datových sad, z nichž každá má vlastní stabilní schéma dat.</span><span class="sxs-lookup"><span data-stu-id="889d5-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="889d5-115">Můžete vytvořit poskytovatele typu, který čte schémata a prezentuje aktuální sady dat programátorovi silným způsobem.</span><span class="sxs-lookup"><span data-stu-id="889d5-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="889d5-116">Než začnete</span><span class="sxs-lookup"><span data-stu-id="889d5-116">Before You Start</span></span>

<span data-ttu-id="889d5-117">Mechanismus poskytovatele typu je primárně určen pro vkládání stabilní data a informační prostory služby do prostředí programování F#.</span><span class="sxs-lookup"><span data-stu-id="889d5-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="889d5-118">Tento mechanismus není určen pro vkládání informačních prostorů, jejichž schéma se změní během provádění programu způsoby, které jsou relevantní pro logiku programu.</span><span class="sxs-lookup"><span data-stu-id="889d5-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="889d5-119">Mechanismus také není určen pro metaprogramování v rámci jazyka, i když tato doména obsahuje některé platné použití.</span><span class="sxs-lookup"><span data-stu-id="889d5-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="889d5-120">Tento mechanismus byste měli použít pouze v případě potřeby a kde vývoj poskytovatele typu poskytuje velmi vysokou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="889d5-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="889d5-121">Měli byste se vyhnout psaní poskytovatele typu, kde schéma není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="889d5-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="889d5-122">Podobně byste se měli vyhnout psaní poskytovatele typu, kde by stačila běžná (nebo dokonce existující) knihovna .NET.</span><span class="sxs-lookup"><span data-stu-id="889d5-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="889d5-123">Než začnete, můžete se zeptat na následující otázky:</span><span class="sxs-lookup"><span data-stu-id="889d5-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="889d5-124">Máte schéma pro váš zdroj informací?</span><span class="sxs-lookup"><span data-stu-id="889d5-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="889d5-125">Pokud ano, jaké je mapování do systému typu F# a .NET?</span><span class="sxs-lookup"><span data-stu-id="889d5-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="889d5-126">Můžete použít existující (dynamicky zadávaný) rozhraní API jako výchozí bod pro implementaci?</span><span class="sxs-lookup"><span data-stu-id="889d5-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="889d5-127">Budete mít vy a vaše organizace dostatek využití poskytovatele typu, aby se psaní stálo za to?</span><span class="sxs-lookup"><span data-stu-id="889d5-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="889d5-128">Vyhovovala by normální knihovna .NET vašim potřebám?</span><span class="sxs-lookup"><span data-stu-id="889d5-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="889d5-129">O kolik se vaše schéma změní?</span><span class="sxs-lookup"><span data-stu-id="889d5-129">How much will your schema change?</span></span>

- <span data-ttu-id="889d5-130">Změní se během kódování?</span><span class="sxs-lookup"><span data-stu-id="889d5-130">Will it change during coding?</span></span>

- <span data-ttu-id="889d5-131">Změní se mezi relacemi kódování?</span><span class="sxs-lookup"><span data-stu-id="889d5-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="889d5-132">Změní se během provádění programu?</span><span class="sxs-lookup"><span data-stu-id="889d5-132">Will it change during program execution?</span></span>

<span data-ttu-id="889d5-133">Zprostředkovatelé typů jsou nejvhodnější pro situace, kdy je schéma stabilní za běhu a během životnosti zkompilovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="889d5-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="889d5-134">Poskytovatel jednoduchého typu</span><span class="sxs-lookup"><span data-stu-id="889d5-134">A Simple Type Provider</span></span>

<span data-ttu-id="889d5-135">Tato ukázka je Samples.HelloWorldTypeProvider, podobně `examples` jako ukázky v adresáři [f# typ zprostředkovatele SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="889d5-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="889d5-136">Zprostředkovatel zpřístupní "místo typu", které obsahuje 100 vymazaných typů, jak ukazuje následující kód pomocí `Type1`syntaxe podpisu F# a vynecháním podrobností pro všechny kromě .</span><span class="sxs-lookup"><span data-stu-id="889d5-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="889d5-137">Další informace o vymýšcených typů naleznete [v tématu Podrobnosti o schovaných typech v](#details-about-erased-provided-types) tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="889d5-138">Všimněte si, že sada typů a členů zadaných je staticky známa.</span><span class="sxs-lookup"><span data-stu-id="889d5-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="889d5-139">Tento příklad nevyužívá schopnost zprostředkovatelů poskytovat typy, které závisí na schématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="889d5-140">Implementace poskytovatele typu je popsána v následujícím kódu a podrobnosti jsou popsány v dalších částech tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="889d5-141">Mezi tímto kódem a online ukázkami mohou být rozdíly.</span><span class="sxs-lookup"><span data-stu-id="889d5-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="889d5-142">Chcete-li použít tohoto zprostředkovatele, otevřete samostatnou instanci sady Visual Studio, vytvořte skript Jazyka F# a pak přidejte odkaz na zprostředkovatele ze skriptu pomocí #r jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="889d5-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="889d5-143">Pak vyhledejte typy `Samples.HelloWorldTypeProvider` v oboru názvů, který vygeneroval poskytovatel typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="889d5-144">Před překompilováním zprostředkovatele se ujistěte, že jste zavřeli všechny instance sady Visual Studio a F# Interactive, které používají knihovnu DLL zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="889d5-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="889d5-145">V opačném případě dojde k chybě sestavení, protože výstupní dll bude uzamčen.</span><span class="sxs-lookup"><span data-stu-id="889d5-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="889d5-146">Chcete-li ladit tohoto zprostředkovatele pomocí tiskových příkazů, vytvořte skript, který zpřístupňuje problém s poskytovatelem, a potom použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="889d5-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="889d5-147">Chcete-li tohoto zprostředkovatele ladit pomocí sady Visual Studio, otevřete příkazový řádek pro vývojáře pro sady Visual Studio s pověřeními pro správu a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="889d5-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="889d5-148">Alternativně otevřete Visual Studio, otevřete nabídku Ladění, `Debug/Attach to process…` `devenv` zvolte a připojte se k jinému procesu, ve kterém upravujete skript.</span><span class="sxs-lookup"><span data-stu-id="889d5-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="889d5-149">Pomocí této metody můžete snadněji cílit na konkrétní logiku v poskytovateli typu interaktivním zadáváním výrazů do druhé instance (s úplným technologiem IntelliSense a dalšími funkcemi).</span><span class="sxs-lookup"><span data-stu-id="889d5-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="889d5-150">Můžete zakázat pouze můj kód ladění lépe identifikovat chyby v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="889d5-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="889d5-151">Informace o povolení nebo zakázání této funkce naleznete v [tématu Navigace prostřednictvím kódu pomocí ladicího programu](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="889d5-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="889d5-152">Také můžete nastavit zachycení výjimky první šance `Debug` otevřením `Exceptions` nabídky a výběrem kláves Ctrl+Alt+E pro otevření dialogového `Exceptions` okna.</span><span class="sxs-lookup"><span data-stu-id="889d5-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="889d5-153">V tomto dialogovém `Common Language Runtime Exceptions`okně `Thrown` zaškrtněte v části zaškrtněte políčko.</span><span class="sxs-lookup"><span data-stu-id="889d5-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="889d5-154">Implementace poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="889d5-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="889d5-155">Tato část vás provede hlavní části implementace poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="889d5-156">Nejprve definujete typ pro samotného zprostředkovatele vlastního typu:</span><span class="sxs-lookup"><span data-stu-id="889d5-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="889d5-157">Tento typ musí být veřejný a musíte jej označit atributem [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) tak, aby kompilátor rozpoznal poskytovatele typu, když samostatný projekt F# odkazuje na sestavení, které obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="889d5-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="889d5-158">Parametr *config* je volitelný a pokud je k dispozici, obsahuje kontextové informace o konfiguraci instance poskytovatele typu, kterou vytvoří kompilátor F#.</span><span class="sxs-lookup"><span data-stu-id="889d5-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="889d5-159">Dále implementovat rozhraní [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)</span><span class="sxs-lookup"><span data-stu-id="889d5-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="889d5-160">V tomto případě použijete `TypeProviderForNamespaces` typ `ProvidedTypes` z rozhraní API jako základní typ.</span><span class="sxs-lookup"><span data-stu-id="889d5-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="889d5-161">Tento typ pomocníka může poskytnout omezenou kolekci dychtivě zapředpokladužené obory názvů, z nichž každý přímo obsahuje konečný počet pevných, dychtivě poskytované typy.</span><span class="sxs-lookup"><span data-stu-id="889d5-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="889d5-162">V tomto kontextu zprostředkovatel *elantně* generuje typy i v případě, že nejsou potřeba nebo použity.</span><span class="sxs-lookup"><span data-stu-id="889d5-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="889d5-163">Dále definujte místní soukromé hodnoty, které určují obor názvů pro zadané typy, a najděte samotné sestavení zprostředkovatele typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="889d5-164">Toto sestavení se později používá jako logický nadřazený typ vymýšcených typů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="889d5-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="889d5-165">Dále vytvořte funkci, která poskytne každý typ Type1... Typ100.</span><span class="sxs-lookup"><span data-stu-id="889d5-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="889d5-166">Tato funkce je podrobněji vysvětlena dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="889d5-167">Dále vygenerujte 100 zadaných typů:</span><span class="sxs-lookup"><span data-stu-id="889d5-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="889d5-168">Dále přidejte typy jako zadaný obor názvů:</span><span class="sxs-lookup"><span data-stu-id="889d5-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="889d5-169">Nakonec přidejte atribut sestavení, který označuje, že vytváříte knihovnu DLL poskytovatele typu:</span><span class="sxs-lookup"><span data-stu-id="889d5-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="889d5-170">Poskytování jednoho typu a jeho členů</span><span class="sxs-lookup"><span data-stu-id="889d5-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="889d5-171">Funkce `makeOneProvidedType` provádí skutečnou práci poskytování jednoho z typů.</span><span class="sxs-lookup"><span data-stu-id="889d5-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="889d5-172">Tento krok vysvětluje implementaci této funkce.</span><span class="sxs-lookup"><span data-stu-id="889d5-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="889d5-173">Nejprve vytvořte zadaný typ (například Type1, když n = 1 nebo Type57, když n = 57).</span><span class="sxs-lookup"><span data-stu-id="889d5-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="889d5-174">Měli byste si uvědomit následující body:</span><span class="sxs-lookup"><span data-stu-id="889d5-174">You should note the following points:</span></span>

- <span data-ttu-id="889d5-175">Tento typ je zadaný vymazán.</span><span class="sxs-lookup"><span data-stu-id="889d5-175">This provided type is erased.</span></span>  <span data-ttu-id="889d5-176">Protože označujete, že `obj`základní typ je , instance se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v kompilovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="889d5-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="889d5-177">Když zadáte nevnořený typ, musíte zadat sestavení a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="889d5-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="889d5-178">Pro vymýšcené typy sestavení by měla být sestavení poskytovatele typu samotné.</span><span class="sxs-lookup"><span data-stu-id="889d5-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="889d5-179">Dále přidejte dokumentaci XML k typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="889d5-180">Tato dokumentace je zpožděna, to znamená vypočítané na vyžádání, pokud to kompilátor hostitele potřebuje.</span><span class="sxs-lookup"><span data-stu-id="889d5-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="889d5-181">Dále přidáte poskytnutou statickou vlastnost k typu:</span><span class="sxs-lookup"><span data-stu-id="889d5-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="889d5-182">Získání této vlastnosti bude vždy vyhodnotit řetězec "Hello!".</span><span class="sxs-lookup"><span data-stu-id="889d5-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="889d5-183">Pro `GetterCode` vlastnost používá c) nabídku, která představuje kód, který kompilátor hostitele generuje pro získání vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="889d5-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="889d5-184">Další informace o nabídkách naleznete v [tématu Nabídky kódu (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="889d5-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="889d5-185">Přidejte do vlastnosti dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="889d5-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="889d5-186">Nyní připojte poskytnutou vlastnost k zadanému typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="889d5-187">Je nutné připojit zadaný člen k jednomu a pouze jednomu typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="889d5-188">V opačném případě člen nikdy nebude přístupný.</span><span class="sxs-lookup"><span data-stu-id="889d5-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="889d5-189">Nyní vytvořte za předpokladu, konstruktor, který nepřebírá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="889d5-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="889d5-190">Pro `InvokeCode` konstruktor vrátí c) nabídku, která představuje kód, který generuje kompilátor hostitele při volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="889d5-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="889d5-191">Můžete například použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="889d5-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="889d5-192">Instance zadaného typu bude vytvořena s podkladovými daty "Data objektu".</span><span class="sxs-lookup"><span data-stu-id="889d5-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="889d5-193">Kód v uvozovkách obsahuje převod na [obj,](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) protože tento typ je vymazání tohoto zadaného typu (jak jste zadali při deklarovaném zadaném typu).</span><span class="sxs-lookup"><span data-stu-id="889d5-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="889d5-194">Přidejte dokumentaci XML do konstruktoru a přidejte zadaný konstruktor do zadaného typu:</span><span class="sxs-lookup"><span data-stu-id="889d5-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="889d5-195">Vytvořte druhý předpokladem konstruktoru, který má jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="889d5-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="889d5-196">Pro `InvokeCode` konstruktor opět vrátí c) nabídku, která představuje kód, který kompilátor hostitele vygenerovaný pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="889d5-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="889d5-197">Můžete například použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="889d5-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="889d5-198">Instance poskytnutého typu je vytvořena s podkladovými daty "deset".</span><span class="sxs-lookup"><span data-stu-id="889d5-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="889d5-199">Možná jste si již `InvokeCode` všimli, že funkce vrací nabídku.</span><span class="sxs-lookup"><span data-stu-id="889d5-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="889d5-200">Vstup do této funkce je seznam výrazů, jeden na parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="889d5-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="889d5-201">V tomto případě je k dispozici výraz, `args.[0]`který představuje hodnotu jednoho parametru v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="889d5-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="889d5-202">Kód pro volání konstruktoru vynutí vrácenou hodnotu vymývaného typu `obj`.</span><span class="sxs-lookup"><span data-stu-id="889d5-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="889d5-203">Po přidání druhého poskytnutého konstruktoru do typu vytvoříte zajišťovnou vlastnost instance:</span><span class="sxs-lookup"><span data-stu-id="889d5-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="889d5-204">Získání této vlastnosti vrátí délku řetězce, což je reprezentace objektu.</span><span class="sxs-lookup"><span data-stu-id="889d5-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="889d5-205">Vlastnost `GetterCode` vrátí nabídku F#, která určuje kód, který generuje kompilátor hostitele získat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="889d5-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="889d5-206">Podobně `InvokeCode`, `GetterCode` funkce vrátí nabídku.</span><span class="sxs-lookup"><span data-stu-id="889d5-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="889d5-207">Kompilátor hostitele volá tuto funkci se seznamem argumentů.</span><span class="sxs-lookup"><span data-stu-id="889d5-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="889d5-208">V tomto případě argumenty zahrnují pouze jeden výraz, který představuje instanci, na které `args.[0]`je volán getter, ke kterému můžete přistupovat pomocí .</span><span class="sxs-lookup"><span data-stu-id="889d5-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="889d5-209">Implementace `GetterCode` pak splices do nabídky výsledků na vymažený typ `obj`a přetypování se používá k uspokojení mechanismu kompilátoru pro kontrolu typů, které je objekt řetězec.</span><span class="sxs-lookup"><span data-stu-id="889d5-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="889d5-210">Další část `makeOneProvidedType` poskytuje metodu instance s jedním parametrem.</span><span class="sxs-lookup"><span data-stu-id="889d5-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="889d5-211">Nakonec vytvořte vnořený typ, který obsahuje 100 vnořených vlastností.</span><span class="sxs-lookup"><span data-stu-id="889d5-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="889d5-212">Vytvoření tohoto vnořeného typu a jeho vlastnosti je zpožděn, to znamená, vypočítané na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="889d5-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="889d5-213">Podrobnosti o vymýšce poskytnutých typů</span><span class="sxs-lookup"><span data-stu-id="889d5-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="889d5-214">Příklad v této části obsahuje pouze *vymažené poskytnuté typy*, které jsou zvláště užitečné v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="889d5-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="889d5-215">Při psaní zprostředkovatele pro informační prostor, který obsahuje pouze data a metody.</span><span class="sxs-lookup"><span data-stu-id="889d5-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="889d5-216">Při psaní zprostředkovatele, kde přesné sémantiku typu runtime nejsou důležité pro praktické použití informačního prostoru.</span><span class="sxs-lookup"><span data-stu-id="889d5-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="889d5-217">Při psaní zprostředkovatele pro informační prostor, který je tak velký a propojený, že není technicky proveditelné generovat skutečné typy .NET pro informační prostor.</span><span class="sxs-lookup"><span data-stu-id="889d5-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="889d5-218">V tomto příkladu je každý zadaný `obj`typ vymazán na typ a všechna `obj` použití typu se zobrazí jako typ v kompilovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="889d5-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="889d5-219">Ve skutečnosti základní objekty v těchto příkladech jsou řetězce, `System.Object` ale typ se zobrazí jako v kódu kompilace .NET.</span><span class="sxs-lookup"><span data-stu-id="889d5-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="889d5-220">Stejně jako u všech použití vymazání typu můžete použít explicitní zabalení, rozbalení a odtypování k rozvrácení smazaných typů.</span><span class="sxs-lookup"><span data-stu-id="889d5-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="889d5-221">V tomto případě přetypová výjimka, která není platná může mít za následek při použití objektu.</span><span class="sxs-lookup"><span data-stu-id="889d5-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="889d5-222">Za běhu zprostředkovatele můžete definovat svůj vlastní typ privátní reprezentace pomoci chránit před falešnými reprezentace.</span><span class="sxs-lookup"><span data-stu-id="889d5-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="889d5-223">Nelze definovat vymýšlí typy v F# sám.</span><span class="sxs-lookup"><span data-stu-id="889d5-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="889d5-224">Smažte pouze poskytnuté typy.</span><span class="sxs-lookup"><span data-stu-id="889d5-224">Only provided types may be erased.</span></span> <span data-ttu-id="889d5-225">Je nutné pochopit důsledky, praktické a sémantické, pomocí vymažené typy pro poskytovatele typu nebo zprostředkovatele, který poskytuje vymýšlé typy.</span><span class="sxs-lookup"><span data-stu-id="889d5-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="889d5-226">Vymýšcený typ nemá žádný skutečný typ .NET.</span><span class="sxs-lookup"><span data-stu-id="889d5-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="889d5-227">Proto nelze provést přesné reflexe nad typem a může rozvrátit vymažené typy, pokud používáte přetypování za běhu a další techniky, které spoléhají na sémantiku typu přesný běh.</span><span class="sxs-lookup"><span data-stu-id="889d5-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="889d5-228">Subverze vymýšlé typy často vede k typu přetypovací výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="889d5-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="889d5-229">Volba reprezentací pro vymývané typy zadaných.</span><span class="sxs-lookup"><span data-stu-id="889d5-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="889d5-230">Pro některá použití vymývaných typů není vyžadována žádná reprezentace.</span><span class="sxs-lookup"><span data-stu-id="889d5-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="889d5-231">Například vymýšlý zadaný typ může obsahovat pouze statické vlastnosti a členy a žádné konstruktory a žádné metody nebo vlastnosti by vrátit instanci typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="889d5-232">Pokud můžete dosáhnout instance vymývaného zadaného typu, je třeba zvážit následující otázky:</span><span class="sxs-lookup"><span data-stu-id="889d5-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="889d5-233">**Jaké je vymazání poskytnutého typu?**</span><span class="sxs-lookup"><span data-stu-id="889d5-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="889d5-234">Vymazání zadaného typu je způsob, jakým se typ zobrazí v kompilovaném kódu .NET.</span><span class="sxs-lookup"><span data-stu-id="889d5-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="889d5-235">Vymazání zadaného vymazaného typu třídy je vždy prvním nesmazatým základním typem v řetězci dědičnosti typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="889d5-236">Vymazání zadaného typu vymazaného `System.Object`rozhraní je vždy .</span><span class="sxs-lookup"><span data-stu-id="889d5-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="889d5-237">**Jaké jsou reprezentace poskytnutého typu?**</span><span class="sxs-lookup"><span data-stu-id="889d5-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="889d5-238">Sada možných objektů pro vymývaný typ zadaný se nazývá jeho reprezentace.</span><span class="sxs-lookup"><span data-stu-id="889d5-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="889d5-239">V příkladu v tomto dokumentu jsou reprezentace všech vymýšlených zadaných typů `Type1..Type100` vždy objekty řetězce.</span><span class="sxs-lookup"><span data-stu-id="889d5-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="889d5-240">Všechna vyobrazení poskytnutého typu musí být kompatibilní s výmazem uvedeného typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="889d5-241">(V opačném případě bude buď kompilátor F# udělit chybu pro použití poskytovatele typu, nebo bude vygenerován neověřitelný kód .NET, který není platný.</span><span class="sxs-lookup"><span data-stu-id="889d5-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="889d5-242">Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)</span><span class="sxs-lookup"><span data-stu-id="889d5-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="889d5-243">Můžete zvolit reprezentaci pro poskytnuté objekty pomocí některého z následujících přístupů, které jsou velmi časté:</span><span class="sxs-lookup"><span data-stu-id="889d5-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="889d5-244">Pokud jednoduše poskytujete obálku silného typu přes existující typ .NET, často má smysl, aby váš typ vymazal na tento typ, používal instance tohoto typu jako reprezentace nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="889d5-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="889d5-245">Tento přístup je vhodný, pokud většina existujících metod na tomto typu stále smysl při použití verze silného typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="889d5-246">Pokud chcete vytvořit rozhraní API, které se výrazně liší od všech existujících rozhraní API .NET, má smysl vytvořit typy runtime, které budou vymazání typu a reprezentace pro poskytnuté typy.</span><span class="sxs-lookup"><span data-stu-id="889d5-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="889d5-247">Příklad v tomto dokumentu používá řetězce jako reprezentace zadaných objektů.</span><span class="sxs-lookup"><span data-stu-id="889d5-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="889d5-248">Často může být vhodné použít jiné objekty pro reprezentace.</span><span class="sxs-lookup"><span data-stu-id="889d5-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="889d5-249">Můžete například použít slovník jako vak vlastností:</span><span class="sxs-lookup"><span data-stu-id="889d5-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="889d5-250">Jako alternativu můžete definovat typ v zprostředkovateli typu, který bude použit za běhu k vytvoření reprezentace, spolu s jedním nebo více operací runtime:</span><span class="sxs-lookup"><span data-stu-id="889d5-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="889d5-251">Za předpokladu, že členové pak mohou vytvářet instance tohoto typu objektu:</span><span class="sxs-lookup"><span data-stu-id="889d5-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="889d5-252">V takovém případě můžete (volitelně) použít tento typ jako výmaz typu `baseType` zadáním `ProvidedTypeDefinition`tohoto typu jako při vytváření :</span><span class="sxs-lookup"><span data-stu-id="889d5-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="889d5-253">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="889d5-253">Key Lessons</span></span>

<span data-ttu-id="889d5-254">V předchozí části bylo vysvětleno, jak vytvořit jednoduchého zprostředkovatele vymývání typu, který poskytuje řadu typů, vlastností a metod.</span><span class="sxs-lookup"><span data-stu-id="889d5-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="889d5-255">Tato část také vysvětluje koncept vymazání typu, včetně některých výhod a nevýhod poskytování vymazaných typů od poskytovatele typu a popisované reprezentace vymazaných typů.</span><span class="sxs-lookup"><span data-stu-id="889d5-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="889d5-256">Zprostředkovatel typu, který používá statické parametry</span><span class="sxs-lookup"><span data-stu-id="889d5-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="889d5-257">Možnost parametrizovat poskytovatele typů statickými daty umožňuje mnoho zajímavých scénářů, a to i v případech, kdy zprostředkovatel nepotřebuje přístup k žádným místním nebo vzdáleným datům.</span><span class="sxs-lookup"><span data-stu-id="889d5-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="889d5-258">V této části se dozvíte některé základní techniky pro sestavení takového poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="889d5-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="889d5-259">Typ kontrolovaný zprostředkovatel regex</span><span class="sxs-lookup"><span data-stu-id="889d5-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="889d5-260">Představte si, že chcete implementovat poskytovatele typu pro <xref:System.Text.RegularExpressions.Regex> regulární výrazy, které zabalí knihovny .NET v rozhraní, které poskytuje následující záruky kompilace:</span><span class="sxs-lookup"><span data-stu-id="889d5-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="889d5-261">Ověření, zda je regulární výraz platný.</span><span class="sxs-lookup"><span data-stu-id="889d5-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="889d5-262">Poskytuje pojmenované vlastnosti na shody, které jsou založeny na názvy skupin v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="889d5-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="889d5-263">Tato část ukazuje, jak pomocí poskytovatelů `RegexTyped` typů vytvořit typ, který vzor regulárního výrazu parametrizuje k poskytování těchto výhod.</span><span class="sxs-lookup"><span data-stu-id="889d5-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="889d5-264">Kompilátor ohlásí chybu, pokud zadaný vzorek není platný, a poskytovatel typu může extrahovat skupiny ze vzoru, takže k nim můžete přistupovat pomocí pojmenovaných vlastností na shodách.</span><span class="sxs-lookup"><span data-stu-id="889d5-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="889d5-265">Při návrhu poskytovatele typu byste měli zvážit, jak by jeho vystavené rozhraní API mělo vypadat koncovým uživatelům a jak se tento návrh přeloží do kódu .NET.</span><span class="sxs-lookup"><span data-stu-id="889d5-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="889d5-266">Následující příklad ukazuje, jak pomocí takového rozhraní API získat součásti směrového kódu oblasti:</span><span class="sxs-lookup"><span data-stu-id="889d5-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="889d5-267">Následující příklad ukazuje, jak poskytovatel typu překládá tato volání:</span><span class="sxs-lookup"><span data-stu-id="889d5-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="889d5-268">Je třeba počítat s následujícím:</span><span class="sxs-lookup"><span data-stu-id="889d5-268">Note the following points:</span></span>

- <span data-ttu-id="889d5-269">Standardní typ Regex představuje `RegexTyped` parametrizovaný typ.</span><span class="sxs-lookup"><span data-stu-id="889d5-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="889d5-270">Výsledkem `RegexTyped` konstruktoru je volání konstruktoru Regex, který předá argument statického typu pro vzorek.</span><span class="sxs-lookup"><span data-stu-id="889d5-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="889d5-271">Výsledky `Match` metody jsou reprezentovány standardním <xref:System.Text.RegularExpressions.Match> typem.</span><span class="sxs-lookup"><span data-stu-id="889d5-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="889d5-272">Každá pojmenovaná skupina má za následek poskytnutou vlastnost a přístup k vlastnosti `Groups` má za následek použití indexeru v kolekci shody.</span><span class="sxs-lookup"><span data-stu-id="889d5-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="889d5-273">Následující kód je jádrem logiky k implementaci takového zprostředkovatele a tento příklad vynese přidání všech členů do zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="889d5-274">Informace o jednotlivých přidaných členech naleznete v příslušné části dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="889d5-275">Úplný kód naznejte, stáhněte si ukázku z [ukázkového balíčku F# 3.0](https://archive.codeplex.com/?p=fsharp3sample) na webu CodePlex.</span><span class="sxs-lookup"><span data-stu-id="889d5-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="889d5-276">Je třeba počítat s následujícím:</span><span class="sxs-lookup"><span data-stu-id="889d5-276">Note the following points:</span></span>

- <span data-ttu-id="889d5-277">Zprostředkovatel typu přebírá dva statické `pattern`parametry: , což `options`je povinné a , které jsou volitelné (protože je k dispozici výchozí hodnota).</span><span class="sxs-lookup"><span data-stu-id="889d5-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="889d5-278">Po dodání statických argumentů vytvoříte instanci regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="889d5-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="889d5-279">Tato instance vyvolá výjimku, pokud je poškozen regex a tato chyba bude hlášena uživatelům.</span><span class="sxs-lookup"><span data-stu-id="889d5-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="889d5-280">V `DefineStaticParameters` rámci zpětného volání definujete typ, který bude vrácen po zadání argumentů.</span><span class="sxs-lookup"><span data-stu-id="889d5-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="889d5-281">Tento kód `HideObjectMethods` se nastaví na hodnotu true tak, aby prostředí Technologie IntelliSense zůstalo zjednodušené.</span><span class="sxs-lookup"><span data-stu-id="889d5-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="889d5-282">Tento atribut `Equals`způsobí, `Finalize`že `GetType` , `GetHashCode`, a členy, které mají být potlačeny ze seznamů IntelliSense pro zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="889d5-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="889d5-283">Použijete `obj` jako základní typ metody, ale budete `Regex` používat objekt jako runtime reprezentace tohoto typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="889d5-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="889d5-284">Volání konstruktoru `Regex` vyvolá, <xref:System.ArgumentException> když regulární výraz není platný.</span><span class="sxs-lookup"><span data-stu-id="889d5-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="889d5-285">Kompilátor zachytí tuto výjimku a hlásí chybovou zprávu uživateli v době kompilace nebo v editoru Sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="889d5-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="889d5-286">Tato výjimka umožňuje regulární výrazy, které mají být ověřeny bez spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="889d5-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="889d5-287">Výše definovaný typ ještě není užitečný, protože neobsahuje žádné smysluplné metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="889d5-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="889d5-288">Nejprve přidejte `IsMatch` statickou metodu:</span><span class="sxs-lookup"><span data-stu-id="889d5-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="889d5-289">Předchozí kód definuje metodu `IsMatch`, která přebírá řetězec `bool`jako vstup a vrací .</span><span class="sxs-lookup"><span data-stu-id="889d5-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="889d5-290">Jedinou choulostivou `args` částí `InvokeCode` je použití argumentu v rámci definice.</span><span class="sxs-lookup"><span data-stu-id="889d5-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="889d5-291">V tomto `args` příkladu je seznam nabídek, který představuje argumenty této metody.</span><span class="sxs-lookup"><span data-stu-id="889d5-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="889d5-292">Pokud metoda je metoda instance, první `this` argument představuje argument.</span><span class="sxs-lookup"><span data-stu-id="889d5-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="889d5-293">Však pro statickou metodu argumenty jsou všechny pouze explicitní argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="889d5-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="889d5-294">Všimněte si, že typ kótované hodnoty by měl `bool`odpovídat zadanému typu vrácení (v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="889d5-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="889d5-295">Všimněte si také, `AddXmlDoc` že tento kód používá metodu, aby se ujistil, že zadaná metoda má také užitečnou dokumentaci, kterou můžete zadat prostřednictvím technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="889d5-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="889d5-296">Dále přidejte metodu instance Match.</span><span class="sxs-lookup"><span data-stu-id="889d5-296">Next, add an instance Match method.</span></span> <span data-ttu-id="889d5-297">Tato metoda by však měla vrátit `Match` hodnotu zadaného typu tak, aby skupiny lze přistupovat silným způsobem.</span><span class="sxs-lookup"><span data-stu-id="889d5-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="889d5-298">Proto nejprve deklarovat `Match` typ.</span><span class="sxs-lookup"><span data-stu-id="889d5-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="889d5-299">Vzhledem k tomu, že tento typ závisí na vzoru, který byl zadán jako statický argument, musí být tento typ vnořen do definice parametrizovaného typu:</span><span class="sxs-lookup"><span data-stu-id="889d5-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="889d5-300">Potom přidáte jednu vlastnost do typu Shoda pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="889d5-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="889d5-301">Za běhu je shoda reprezentována <xref:System.Text.RegularExpressions.Match> jako hodnota, takže nabídka, která <xref:System.Text.RegularExpressions.Match.Groups> definuje vlastnost, musí použít indexovnou vlastnost k získání příslušné skupiny.</span><span class="sxs-lookup"><span data-stu-id="889d5-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="889d5-302">Všimněte si, že přidáváte dokumentaci XML do poskytnuté vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="889d5-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="889d5-303">Všimněte si také, že `GetterCode` vlastnost lze číst, pokud je k `SetterCode` dispozici funkce a vlastnost může být zapsána, pokud je k dispozici funkce, takže výsledná vlastnost je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="889d5-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="889d5-304">Nyní můžete vytvořit metodu instance, která `Match` vrací hodnotu tohoto typu:</span><span class="sxs-lookup"><span data-stu-id="889d5-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="889d5-305">Protože vytváříte metodu `args.[0]` instance, `RegexTyped` představuje instanci, na `args.[1]` které je metoda volána, a je vstupním argumentem.</span><span class="sxs-lookup"><span data-stu-id="889d5-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="889d5-306">Nakonec zadejte konstruktor tak, aby instance zadaný typ lze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="889d5-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="889d5-307">Konstruktor pouze vymaže vytvoření standardní instance .NET Regex, která je `obj` opět zabalena do objektu, protože je vymazání zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="889d5-308">S tímto způsobem funguje ukázkové využití rozhraní API, které bylo zadáno dříve v tématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="889d5-309">Následující kód je úplný a konečný:</span><span class="sxs-lookup"><span data-stu-id="889d5-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="889d5-310">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="889d5-310">Key Lessons</span></span>

<span data-ttu-id="889d5-311">Tato část vysvětluje, jak vytvořit zprostředkovatele typu, který pracuje na jeho statické parametry.</span><span class="sxs-lookup"><span data-stu-id="889d5-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="889d5-312">Zprostředkovatel zkontroluje statický parametr a poskytuje operace na základě jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="889d5-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="889d5-313">Zprostředkovatel typu, který je podpořen místními daty</span><span class="sxs-lookup"><span data-stu-id="889d5-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="889d5-314">Často můžete chtít, aby poskytovatelé typů prezentovali rozhraní API nejen na základě statických parametrů, ale také informací z místních nebo vzdálených systémů.</span><span class="sxs-lookup"><span data-stu-id="889d5-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="889d5-315">Tato část popisuje poskytovatele typů, kteří jsou založeni na místních datech, jako jsou například místní datové soubory.</span><span class="sxs-lookup"><span data-stu-id="889d5-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="889d5-316">Jednoduchý poskytovatel souborů CSV</span><span class="sxs-lookup"><span data-stu-id="889d5-316">Simple CSV File Provider</span></span>

<span data-ttu-id="889d5-317">Jako jednoduchý příklad zvažte zprostředkovatele typu pro přístup k vědeckým datům ve formátu CSV (Comma Separated Value).</span><span class="sxs-lookup"><span data-stu-id="889d5-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="889d5-318">Tato část předpokládá, že soubory CSV obsahují řádek záhlaví následovaný daty s plovoucí desetinnou táhou, jak ukazuje následující tabulka:</span><span class="sxs-lookup"><span data-stu-id="889d5-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="889d5-319">Vzdálenost (metr)</span><span class="sxs-lookup"><span data-stu-id="889d5-319">Distance (meter)</span></span>|<span data-ttu-id="889d5-320">Čas (druhý)</span><span class="sxs-lookup"><span data-stu-id="889d5-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="889d5-321">50.0</span><span class="sxs-lookup"><span data-stu-id="889d5-321">50.0</span></span>|<span data-ttu-id="889d5-322">3.7</span><span class="sxs-lookup"><span data-stu-id="889d5-322">3.7</span></span>|
|<span data-ttu-id="889d5-323">100.0</span><span class="sxs-lookup"><span data-stu-id="889d5-323">100.0</span></span>|<span data-ttu-id="889d5-324">5.2</span><span class="sxs-lookup"><span data-stu-id="889d5-324">5.2</span></span>|
|<span data-ttu-id="889d5-325">150.0</span><span class="sxs-lookup"><span data-stu-id="889d5-325">150.0</span></span>|<span data-ttu-id="889d5-326">6.4</span><span class="sxs-lookup"><span data-stu-id="889d5-326">6.4</span></span>|

<span data-ttu-id="889d5-327">Tato část ukazuje, jak zadat typ, který můžete `Distance` použít `float<meter>` k `Time` získání řádků `float<second>`s vlastností typu a vlastností typu .</span><span class="sxs-lookup"><span data-stu-id="889d5-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="889d5-328">Pro jednoduchost jsou provedeny následující předpoklady:</span><span class="sxs-lookup"><span data-stu-id="889d5-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="889d5-329">Názvy hlaviček jsou buď bez jednotky, nebo mají tvar "Název (jednotka)" a neobsahují čárky.</span><span class="sxs-lookup"><span data-stu-id="889d5-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="889d5-330">Jednotky jsou všechny jednotky System International (SI), které definují modul [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#).](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)</span><span class="sxs-lookup"><span data-stu-id="889d5-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="889d5-331">Jednotky jsou jednoduché (například metr) spíše než složené (například metr/s).</span><span class="sxs-lookup"><span data-stu-id="889d5-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="889d5-332">Všechny sloupce obsahují data s plovoucí desetinnou tácem.</span><span class="sxs-lookup"><span data-stu-id="889d5-332">All columns contain floating point data.</span></span>

<span data-ttu-id="889d5-333">Úplnější poskytovatel by tato omezení uvolnil.</span><span class="sxs-lookup"><span data-stu-id="889d5-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="889d5-334">Opět prvním krokem je zvážit, jak by mělo rozhraní API vypadat.</span><span class="sxs-lookup"><span data-stu-id="889d5-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="889d5-335">Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="889d5-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="889d5-336">V takovém případě by měl kompilátor převést tato volání na něco jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="889d5-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="889d5-337">Optimální překlad bude vyžadovat, aby poskytovatel `CsvFile` typu definoval skutečný typ v sestavení poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="889d5-338">Poskytovatelé typů často spoléhají na několik pomocné typy a metody zabalit důležitou logiku.</span><span class="sxs-lookup"><span data-stu-id="889d5-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="889d5-339">Vzhledem k tomu, že jsou míry `float[]` vymazány za běhu, můžete použít jako vymýšcený typ pro řádek.</span><span class="sxs-lookup"><span data-stu-id="889d5-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="889d5-340">Kompilátor bude považovat různé sloupce za různé typy měr.</span><span class="sxs-lookup"><span data-stu-id="889d5-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="889d5-341">Například první sloupec v našem `float<meter>`příkladu má `float<second>`typ a druhý má .</span><span class="sxs-lookup"><span data-stu-id="889d5-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="889d5-342">Vymazání reprezentace však může zůstat poměrně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="889d5-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="889d5-343">Následující kód ukazuje jádro implementace.</span><span class="sxs-lookup"><span data-stu-id="889d5-343">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="889d5-344">Všimněte si následujících bodů o implementaci:</span><span class="sxs-lookup"><span data-stu-id="889d5-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="889d5-345">Přetížené konstruktory umožňují čtení původního souboru nebo souboru, který má stejné schéma.</span><span class="sxs-lookup"><span data-stu-id="889d5-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="889d5-346">Tento vzor je běžné při psaní poskytovatele typu pro místní nebo vzdálené zdroje dat a tento vzor umožňuje místní soubor, který má být použit jako šablona pro vzdálená data.</span><span class="sxs-lookup"><span data-stu-id="889d5-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="889d5-347">Můžete použít [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) hodnotu, která je předána do konstruktoru poskytovatele typu k vyřešení relativní názvy souborů.</span><span class="sxs-lookup"><span data-stu-id="889d5-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="889d5-348">Metodu `AddDefinitionLocation` můžete použít k definování umístění poskytnutých vlastností.</span><span class="sxs-lookup"><span data-stu-id="889d5-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="889d5-349">Proto pokud použijete `Go To Definition` na zapředpokladu vlastnost, soubor CSV se otevře v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="889d5-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="889d5-350">Typ můžete `ProvidedMeasureBuilder` použít k vyhledat jednotky SI `float<_>` a generovat příslušné typy.</span><span class="sxs-lookup"><span data-stu-id="889d5-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="889d5-351">Klíčové lekce</span><span class="sxs-lookup"><span data-stu-id="889d5-351">Key Lessons</span></span>

<span data-ttu-id="889d5-352">Tato část vysvětluje, jak vytvořit zprostředkovatele typu pro místní zdroj dat s jednoduchým schématem, které je obsaženo v samotném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="889d5-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="889d5-353">Chystáte se dále</span><span class="sxs-lookup"><span data-stu-id="889d5-353">Going Further</span></span>

<span data-ttu-id="889d5-354">Následující části obsahují návrhy na další studium.</span><span class="sxs-lookup"><span data-stu-id="889d5-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="889d5-355">Podívejte se na zkompilovaný kód pro vymývané typy</span><span class="sxs-lookup"><span data-stu-id="889d5-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="889d5-356">Chcete-li získat určitou představu o tom, jak použití poskytovatele typu odpovídá kódu, který je `HelloWorldTypeProvider` emitován, podívejte se na následující funkci pomocí, která se používá dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="889d5-357">Zde je obrázek výsledného kódu dekompilované pomocí ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="889d5-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="889d5-358">Jak ukazuje příklad, všechny zmínky `Type1` o `InstanceProperty` typu a vlastnosti byly vymazány, takže pouze operace na typy runtime zapojeny.</span><span class="sxs-lookup"><span data-stu-id="889d5-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="889d5-359">Konvence návrhu a pojmenování pro poskytovatele typů</span><span class="sxs-lookup"><span data-stu-id="889d5-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="889d5-360">Při vytváření zprostředkovatelů typu dodržujte následující konvence.</span><span class="sxs-lookup"><span data-stu-id="889d5-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="889d5-361">**Zprostředkovatelé pro protokoly připojení** Obecně platí, že názvy většiny zprostředkovatelských knihoven DLL pro protokoly připojení k `TypeProvider` `TypeProviders`datům a službám, jako jsou připojení OData nebo SQL, by měly končit v aplikaci nebo .</span><span class="sxs-lookup"><span data-stu-id="889d5-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="889d5-362">Použijte například název dll, který se podobá následujícímu řetězci:</span><span class="sxs-lookup"><span data-stu-id="889d5-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="889d5-363">Ujistěte se, že vaše poskytnuté typy jsou členy odpovídajícího oboru názvů a označte protokol připojení, který jste implementovali:</span><span class="sxs-lookup"><span data-stu-id="889d5-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="889d5-364">**Poskytovatelé veřejných služeb pro obecné kódování**.</span><span class="sxs-lookup"><span data-stu-id="889d5-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="889d5-365">Pro poskytovatele typu nástroje, například pro regulární výrazy, může být poskytovatel typu součástí základní knihovny, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="889d5-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="889d5-366">V tomto případě by zadaný typ se zobrazí v příslušném bodě podle běžných konvencí návrhu .NET:</span><span class="sxs-lookup"><span data-stu-id="889d5-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="889d5-367">**Singleton zdroje dat**.</span><span class="sxs-lookup"><span data-stu-id="889d5-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="889d5-368">Někteří poskytovatelé typů se připojují k jedinému vyhrazenému zdroji dat a poskytují pouze data.</span><span class="sxs-lookup"><span data-stu-id="889d5-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="889d5-369">V takovém případě byste `TypeProvider` měli upustit příponu a použít normální konvence pro pojmenování .NET:</span><span class="sxs-lookup"><span data-stu-id="889d5-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="889d5-370">Další informace naleznete `GetConnection` v konvenci návrhu, která je popsána dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="889d5-371">Návrhové vzory pro poskytovatele typů</span><span class="sxs-lookup"><span data-stu-id="889d5-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="889d5-372">Následující části popisují návrhové vzory, které můžete použít při vytváření poskytovatelů typů.</span><span class="sxs-lookup"><span data-stu-id="889d5-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="889d5-373">Vzor návrhu GetConnection</span><span class="sxs-lookup"><span data-stu-id="889d5-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="889d5-374">Většina poskytovatelů typu by `GetConnection` měla být zapsána tak, aby používala vzorek, který používají zprostředkovatelé typu v souboru FSharp.Data.TypeProviders.dll, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="889d5-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="889d5-375">Poskytovatelé typů podporovaní vzdálenými daty a službami</span><span class="sxs-lookup"><span data-stu-id="889d5-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="889d5-376">Před vytvořením poskytovatele typu, který je podporován vzdálenými daty a službami, je třeba zvážit řadu problémů, které jsou vlastní připojenému programování.</span><span class="sxs-lookup"><span data-stu-id="889d5-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="889d5-377">Mezi tyto problémy patří následující aspekty:</span><span class="sxs-lookup"><span data-stu-id="889d5-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="889d5-378">mapování schématu</span><span class="sxs-lookup"><span data-stu-id="889d5-378">schema mapping</span></span>

- <span data-ttu-id="889d5-379">živost a zneplatnění v přítomnosti změny schématu</span><span class="sxs-lookup"><span data-stu-id="889d5-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="889d5-380">ukládání do mezipaměti schématu</span><span class="sxs-lookup"><span data-stu-id="889d5-380">schema caching</span></span>

- <span data-ttu-id="889d5-381">asynchronní implementace operací přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="889d5-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="889d5-382">podpůrné dotazy, včetně dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="889d5-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="889d5-383">pověření a ověřování</span><span class="sxs-lookup"><span data-stu-id="889d5-383">credentials and authentication</span></span>

<span data-ttu-id="889d5-384">Toto téma není prozkoumat tyto problémy dále.</span><span class="sxs-lookup"><span data-stu-id="889d5-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="889d5-385">Další vývojové techniky</span><span class="sxs-lookup"><span data-stu-id="889d5-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="889d5-386">Při psaní vlastní zprostředkovatelé typu, můžete použít následující další techniky.</span><span class="sxs-lookup"><span data-stu-id="889d5-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="889d5-387">Vytváření typů a členů na vyžádání</span><span class="sxs-lookup"><span data-stu-id="889d5-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="889d5-388">Rozhraní API ProvidedType má zpožděné verze AddMember.</span><span class="sxs-lookup"><span data-stu-id="889d5-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="889d5-389">Tyto verze se používají k vytvoření prostorů na vyžádání typů.</span><span class="sxs-lookup"><span data-stu-id="889d5-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="889d5-390">Poskytování typů polí a instancí obecného typu</span><span class="sxs-lookup"><span data-stu-id="889d5-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="889d5-391">Zadaným členům (jejichž podpisy zahrnují typy polí, typy odkazových čar a instance `MakeArrayType` `MakePointerType`obecných `MakeGenericType` typů) <xref:System.Type>pomocí `ProvidedTypeDefinitions`normálního , a na libovolné instanci aplikace , včetně .</span><span class="sxs-lookup"><span data-stu-id="889d5-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="889d5-392">V některých případech může být možné `ProvidedTypeBuilder.MakeGenericType`použít pomocníka v .</span><span class="sxs-lookup"><span data-stu-id="889d5-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="889d5-393">Další podrobnosti naleznete v dokumentaci k [spoje poskytovatele typu.](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)</span><span class="sxs-lookup"><span data-stu-id="889d5-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="889d5-394">Poskytování poznámky měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="889d5-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="889d5-395">Rozhraní API ProvidedTypes poskytuje pomocné soubory pro poskytování poznámky měření.</span><span class="sxs-lookup"><span data-stu-id="889d5-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="889d5-396">Chcete-li například `float<kg>`zadat typ , použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="889d5-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="889d5-397">Chcete-li `Nullable<decimal<kg/m^2>>`zadat typ , použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="889d5-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="889d5-398">Přístup k místním nebo scriptovým místním zdrojům projektu</span><span class="sxs-lookup"><span data-stu-id="889d5-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="889d5-399">Každá instance poskytovatele typu může `TypeProviderConfig` být poskytnuta hodnota během výstavby.</span><span class="sxs-lookup"><span data-stu-id="889d5-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="889d5-400">Tato hodnota obsahuje "složku rozlišení" pro zprostředkovatele (to znamená složku projektu pro kompilaci nebo adresář, který obsahuje skript), seznam odkazovaných sestavení a další informace.</span><span class="sxs-lookup"><span data-stu-id="889d5-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="889d5-401">Neplatnost</span><span class="sxs-lookup"><span data-stu-id="889d5-401">Invalidation</span></span>

<span data-ttu-id="889d5-402">Zprostředkovatelé mohou vyvolat signály zneplatnění upozornit službu jazyka F#, že předpoklady schématu může změnit.</span><span class="sxs-lookup"><span data-stu-id="889d5-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="889d5-403">Dojde-li k neplatnosti, přeškrtne se kontrola typu, pokud je zprostředkovatel hostován v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="889d5-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="889d5-404">Tento signál bude ignorován, pokud je zprostředkovatel hostován v F# Interactive nebo kompilátorem F# (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="889d5-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="889d5-405">Informace o schématu ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="889d5-405">Caching Schema Information</span></span>

<span data-ttu-id="889d5-406">Zprostředkovatelé musí často ukládat přístup k informacím o schématu.</span><span class="sxs-lookup"><span data-stu-id="889d5-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="889d5-407">Data uložená v mezipaměti by měla být uložena pomocí názvu souboru, který je uveden jako statický parametr nebo jako uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="889d5-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="889d5-408">Příkladem ukládání do mezipaměti schématu `LocalSchemaFile` je parametr v zprostředkovatelích typu v `FSharp.Data.TypeProviders` sestavení.</span><span class="sxs-lookup"><span data-stu-id="889d5-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="889d5-409">Při implementaci těchto zprostředkovatelů tento statický parametr nasměruje poskytovatele typu použít informace o schématu v zadaném místním souboru namísto přístupu ke zdroji dat v síti.</span><span class="sxs-lookup"><span data-stu-id="889d5-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="889d5-410">Chcete-li použít informace o schématu uloženém v `ForceUpdate` `false`mezipaměti, musíte také nastavit statický parametr na .</span><span class="sxs-lookup"><span data-stu-id="889d5-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="889d5-411">Podobnou techniku můžete použít k povolení přístupu k datům online a offline.</span><span class="sxs-lookup"><span data-stu-id="889d5-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="889d5-412">Sestava zálohování</span><span class="sxs-lookup"><span data-stu-id="889d5-412">Backing Assembly</span></span>

<span data-ttu-id="889d5-413">Při kompilaci `.dll` `.exe` nebo souboru je záložní soubor DLL pro generované typy staticky propojen do výsledného sestavení.</span><span class="sxs-lookup"><span data-stu-id="889d5-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="889d5-414">Toto propojení je vytvořeno zkopírováním definic typů zprostředkujícíjazyk (IL) a všechny spravované prostředky z doprovodné sestavení do konečného sestavení.</span><span class="sxs-lookup"><span data-stu-id="889d5-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="889d5-415">Při použití F# Interactive, záložní soubor DLL není zkopírován a je místo toho načten přímo do f# interaktivní proces.</span><span class="sxs-lookup"><span data-stu-id="889d5-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="889d5-416">Výjimky a diagnostika od poskytovatelů typů</span><span class="sxs-lookup"><span data-stu-id="889d5-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="889d5-417">Všechna použití všech členů z poskytnutých typů může vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="889d5-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="889d5-418">Ve všech případech pokud poskytovatel typu vyvolá výjimku, kompilátor hostitele atributy chyby na konkrétní poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="889d5-419">Výjimky zprostředkovatele typu by nikdy neměly vést k chybám interního kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="889d5-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="889d5-420">Poskytovatelé typů nemohou hlásit upozornění.</span><span class="sxs-lookup"><span data-stu-id="889d5-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="889d5-421">Pokud je poskytovatel typu hostován v kompilátoru F#, vývojovém prostředí F# nebo F# Interactive, jsou zachyceny všechny výjimky z tohoto zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="889d5-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="889d5-422">Message Vlastnost je vždy text chyby a žádné trasování zásobníku se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="889d5-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="889d5-423">Pokud se chystáte vyvolat výjimku, můžete vyvolat následující `System.NotSupportedException` `System.IO.IOException`příklady: , , `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="889d5-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="889d5-424">Poskytování generovaných typů</span><span class="sxs-lookup"><span data-stu-id="889d5-424">Providing Generated Types</span></span>

<span data-ttu-id="889d5-425">Zatím tento dokument vysvětlil, jak poskytnout vymýšce typy.</span><span class="sxs-lookup"><span data-stu-id="889d5-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="889d5-426">Mechanismus zprostředkovatele typu v f# můžete také použít k poskytnutí generovaných typů, které jsou přidány jako skutečné definice typu .NET do programu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="889d5-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="889d5-427">Musíte odkazovat na generované poskytované typy pomocí definice typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="889d5-428">Pomocný kód ProvidedTypes-0.2, který je součástí verze F# 3.0, má pouze omezenou podporu pro poskytování generovaných typů.</span><span class="sxs-lookup"><span data-stu-id="889d5-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="889d5-429">Následující příkazy musí být true pro definici generovaného typu:</span><span class="sxs-lookup"><span data-stu-id="889d5-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="889d5-430">`isErased`musí být `false`nastavena na .</span><span class="sxs-lookup"><span data-stu-id="889d5-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="889d5-431">Generovaný typ musí být přidán `ProvidedAssembly()`do nově vytvořeného typu , který představuje kontejner pro generované fragmenty kódu.</span><span class="sxs-lookup"><span data-stu-id="889d5-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="889d5-432">Zprostředkovatel musí mít sestavení, které má skutečný záložní soubor .NET .dll s odpovídajícím souborem DLL na disku.</span><span class="sxs-lookup"><span data-stu-id="889d5-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="889d5-433">Pravidla a omezení</span><span class="sxs-lookup"><span data-stu-id="889d5-433">Rules and Limitations</span></span>

<span data-ttu-id="889d5-434">Při psaní poskytovatelů typu mějte na paměti následující pravidla a omezení.</span><span class="sxs-lookup"><span data-stu-id="889d5-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="889d5-435">Za předpokladu, že typy musí být dosažitelné</span><span class="sxs-lookup"><span data-stu-id="889d5-435">Provided types must be reachable</span></span>

<span data-ttu-id="889d5-436">Všechny poskytnuté typy by měly být dosažitelné z nevnořených typů.</span><span class="sxs-lookup"><span data-stu-id="889d5-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="889d5-437">Nevnořené typy jsou uvedeny `TypeProviderForNamespaces` ve volání konstruktoru nebo volání `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="889d5-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="889d5-438">Například pokud poskytovatel poskytuje `StaticClass.P : T`typ , musíte zajistit, že T je buď nevnořený typ nebo vnořené pod jeden.</span><span class="sxs-lookup"><span data-stu-id="889d5-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="889d5-439">Například někteří zprostředkovatelé mají statickou třídu, jako `DataTypes` je například, které obsahují tyto `T1, T2, T3, ...` typy.</span><span class="sxs-lookup"><span data-stu-id="889d5-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="889d5-440">V opačném případě chyba říká, že byl nalezen odkaz na typ T v sestavě A, ale typ nebyl v této sestavě nalezen.</span><span class="sxs-lookup"><span data-stu-id="889d5-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="889d5-441">Pokud se zobrazí tato chyba, ověřte, zda jsou všechny podtypy dosažitelné z typů zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="889d5-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="889d5-442">Poznámka: `T1, T2, T3...` Tyto typy se označují jako *průběžně.*</span><span class="sxs-lookup"><span data-stu-id="889d5-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="889d5-443">Nezapomeňte je umístit do přístupného oboru názvů nebo do nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="889d5-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="889d5-444">Omezení mechanismu poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="889d5-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="889d5-445">Mechanismus zprostředkovatele typu v F# má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="889d5-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="889d5-446">Základní infrastruktura pro poskytovatele typů v F# nepodporuje poskytované obecné typy nebo poskytnuté obecné metody.</span><span class="sxs-lookup"><span data-stu-id="889d5-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="889d5-447">Mechanismus nepodporuje vnořené typy se statickými parametry.</span><span class="sxs-lookup"><span data-stu-id="889d5-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="889d5-448">Tipy pro vývoj</span><span class="sxs-lookup"><span data-stu-id="889d5-448">Development Tips</span></span>

<span data-ttu-id="889d5-449">Během procesu vývoje mohou být užitečné následující tipy:</span><span class="sxs-lookup"><span data-stu-id="889d5-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="889d5-450">Spuštění dvou instancí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="889d5-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="889d5-451">Můžete vyvinout poskytovatele typu v jedné instanci a otestovat zprostředkovatele v druhé, protože testovací ide bude mít zámek na soubor .dll, který zabraňuje poskytovatele typu znovu sestavit.</span><span class="sxs-lookup"><span data-stu-id="889d5-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="889d5-452">Proto je nutné zavřít druhou instanci sady Visual Studio, zatímco zprostředkovatel je vytvořen v první instanci a potom je nutné znovu otevřít druhou instanci po vytvořeno zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="889d5-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="889d5-453">Zprostředkovatelé typu ladění pomocí vyvolání fsc.exe</span><span class="sxs-lookup"><span data-stu-id="889d5-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="889d5-454">Zprostředkovatele typů můžete vyvolat pomocí následujících nástrojů:</span><span class="sxs-lookup"><span data-stu-id="889d5-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="889d5-455">fsc.exe (Kompilátor příkazového řádku F#)</span><span class="sxs-lookup"><span data-stu-id="889d5-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="889d5-456">fsi.exe (Interaktivní kompilátor F#</span><span class="sxs-lookup"><span data-stu-id="889d5-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="889d5-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="889d5-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="889d5-458">Zprostředkovatele typů můžete často ladit nejsnadněji pomocí souboru fsc.exe v souboru testovacího skriptu (například script.fsx).</span><span class="sxs-lookup"><span data-stu-id="889d5-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="889d5-459">Ladicí program můžete spustit z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="889d5-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="889d5-460">Můžete použít protokolování print-to-stdout.</span><span class="sxs-lookup"><span data-stu-id="889d5-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="889d5-461">Viz také</span><span class="sxs-lookup"><span data-stu-id="889d5-461">See also</span></span>

- [<span data-ttu-id="889d5-462">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="889d5-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="889d5-463">Sada Zprostředkovatel typu SDK</span><span class="sxs-lookup"><span data-stu-id="889d5-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
