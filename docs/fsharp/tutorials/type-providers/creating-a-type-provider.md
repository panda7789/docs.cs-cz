---
title: 'Kurz: vytvoření poskytovatele typu'
description: Naučte se, jak vytvořit F# vlastní poskytovatele typů F# v 3,0, prozkoumáním několika jednoduchých poskytovatelů typů pro ilustraci základních konceptů.
ms.date: 11/04/2019
ms.openlocfilehash: 8df893669b8ee04bad366dbe42a55c83d1f5a8fe
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968376"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="4637d-103">Kurz: vytvoření poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="4637d-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="4637d-104">Mechanismus poskytovatele typu v F# nástroji je podstatnou součástí své podpory pro bohatou programování informací.</span><span class="sxs-lookup"><span data-stu-id="4637d-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="4637d-105">V tomto kurzu se dozvíte, jak vytvořit vlastní poskytovatele typů prostřednictvím vývoje několika jednoduchých zprostředkovatelů typů pro ilustraci základních konceptů.</span><span class="sxs-lookup"><span data-stu-id="4637d-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="4637d-106">Další informace o mechanismu poskytovatele typu v F#naleznete v tématu [Poskytovatelé typů](index.md).</span><span class="sxs-lookup"><span data-stu-id="4637d-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="4637d-107">F# Ekosystém obsahuje rozsah zprostředkovatelů typů pro běžně používané internetové a podnikové datové služby.</span><span class="sxs-lookup"><span data-stu-id="4637d-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="4637d-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4637d-108">For example:</span></span>

- <span data-ttu-id="4637d-109">[FSharp. data](https://fsharp.github.io/FSharp.Data/) zahrnují poskytovatele typů pro formáty dokumentů JSON, XML, CSV a HTML.</span><span class="sxs-lookup"><span data-stu-id="4637d-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="4637d-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) poskytuje přístup se silným typem k databázím SQL prostřednictvím mapování objektů F# a dotazů LINQ na tyto zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4637d-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="4637d-111">[FSharp. data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) má sadu zprostředkovatelů typů pro kontrolované vkládání T-SQL v F#době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4637d-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="4637d-112">[FSharp. data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) je starší sada zprostředkovatelů typů pro použití s .NET Framework programováním pro přístup k datovým službám SQL, Entity Framework, OData a WSDL.</span><span class="sxs-lookup"><span data-stu-id="4637d-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="4637d-113">V případě potřeby můžete vytvořit vlastní poskytovatele typu nebo můžete odkazovat na poskytovatele typu, který vytvořili jiní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="4637d-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="4637d-114">Vaše organizace může mít například datovou službu, která poskytuje velký a rostoucí počet pojmenovaných datových sad, z nichž každá má vlastní stabilní schéma dat.</span><span class="sxs-lookup"><span data-stu-id="4637d-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="4637d-115">Můžete vytvořit poskytovatele typu, který přečte schémata a prezentuje aktuální datové sady programátorovi pomocí silného typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="4637d-116">Než začnete</span><span class="sxs-lookup"><span data-stu-id="4637d-116">Before You Start</span></span>

<span data-ttu-id="4637d-117">Mechanismus poskytovatele typů je navržený hlavně pro vkládání stabilních informací a informačních prostorů do F# programovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="4637d-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="4637d-118">Tento mechanismus není určený pro vkládání prostorů s informacemi, jejichž změny schématu během provádění programu jsou důležité pro programovou logiku.</span><span class="sxs-lookup"><span data-stu-id="4637d-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="4637d-119">Mechanismus není navržený pro účely meta programování v rámci jazyka, a to i v případě, že doména obsahuje nějaká platná použití.</span><span class="sxs-lookup"><span data-stu-id="4637d-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="4637d-120">Tento mechanismus byste měli použít pouze v případě potřeby a tam, kde vývoj poskytovatele typu poskytuje velmi vysokou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4637d-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="4637d-121">Měli byste se vyhnout psaní poskytovatele typu, pokud není k dispozici schéma.</span><span class="sxs-lookup"><span data-stu-id="4637d-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="4637d-122">Podobně byste se měli vyhnout psaní poskytovatele typu, kde by měla být obvyklá (nebo dokonce stávající) knihovna .NET.</span><span class="sxs-lookup"><span data-stu-id="4637d-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="4637d-123">Než začnete, můžete se zeptat na tyto otázky:</span><span class="sxs-lookup"><span data-stu-id="4637d-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="4637d-124">Máte schéma pro svůj zdroj informací?</span><span class="sxs-lookup"><span data-stu-id="4637d-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="4637d-125">Pokud ano, co je mapování na systém typů F# a .NET?</span><span class="sxs-lookup"><span data-stu-id="4637d-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="4637d-126">Můžete použít existující (dynamicky typované) rozhraní API jako výchozí bod pro vaši implementaci?</span><span class="sxs-lookup"><span data-stu-id="4637d-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="4637d-127">Budete vy a vaše organizace mít k dispozici dostatek využití poskytovatele typu, abyste ho mohli využít k psaní?</span><span class="sxs-lookup"><span data-stu-id="4637d-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="4637d-128">Bude normální knihovna .NET vyhovovat vašim potřebám?</span><span class="sxs-lookup"><span data-stu-id="4637d-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="4637d-129">Kolik schématu se změní?</span><span class="sxs-lookup"><span data-stu-id="4637d-129">How much will your schema change?</span></span>

- <span data-ttu-id="4637d-130">Změní se během kódování?</span><span class="sxs-lookup"><span data-stu-id="4637d-130">Will it change during coding?</span></span>

- <span data-ttu-id="4637d-131">Změní se mezi relacemi kódování?</span><span class="sxs-lookup"><span data-stu-id="4637d-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="4637d-132">Změní se během provádění programu?</span><span class="sxs-lookup"><span data-stu-id="4637d-132">Will it change during program execution?</span></span>

<span data-ttu-id="4637d-133">Poskytovatelé typů jsou nejvhodnější pro situace, kdy je schéma stabilní za běhu a během životnosti zkompilovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4637d-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="4637d-134">Jednoduchý poskytovatel typu</span><span class="sxs-lookup"><span data-stu-id="4637d-134">A Simple Type Provider</span></span>

<span data-ttu-id="4637d-135">Tato ukázka je Samples. HelloWorldTypeProvider, podobně jako ukázky v adresáři `examples` v [ F# sadě SDK typu Provider](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="4637d-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="4637d-136">Zprostředkovatel zpřístupňuje "typ prostoru", který obsahuje 100 vymazaných typů, jak ukazuje následující kód pomocí F# syntaxe signatury a vynecháním podrobností pro všechny kromě `Type1`.</span><span class="sxs-lookup"><span data-stu-id="4637d-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="4637d-137">Další informace o vymazaných typech najdete v [podrobnostech o vymazaných poskytovaných typech](#details-about-erased-provided-types) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4637d-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="4637d-138">Všimněte si, že sada typů a zadaných členů je staticky známá.</span><span class="sxs-lookup"><span data-stu-id="4637d-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="4637d-139">Tento příklad nevyužívá možnost poskytovatelů k poskytování typů, které jsou závislé na schématu.</span><span class="sxs-lookup"><span data-stu-id="4637d-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="4637d-140">Implementace poskytovatele typu je popsaná v následujícím kódu a podrobnosti jsou uvedené v dalších částech tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4637d-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="4637d-141">Mohou existovat rozdíly mezi tímto kódem a online ukázkami.</span><span class="sxs-lookup"><span data-stu-id="4637d-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="4637d-142">Chcete-li použít tohoto poskytovatele, otevřete samostatnou instanci aplikace Visual Studio, F# Vytvořte skript a přidejte odkaz na poskytovatele ze skriptu pomocí #r, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="4637d-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="4637d-143">Pak vyhledejte typy pod oborem názvů `Samples.HelloWorldTypeProvider`, který poskytovatel typu vygeneroval.</span><span class="sxs-lookup"><span data-stu-id="4637d-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="4637d-144">Než znovu zkompilujete poskytovatele, ujistěte se, že jste uzavřeli všechny instance aplikace Visual Studio a F# interaktivní, které používají knihovnu DLL zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="4637d-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="4637d-145">V opačném případě dojde k chybě sestavení, protože výstupní knihovna DLL bude uzamčena.</span><span class="sxs-lookup"><span data-stu-id="4637d-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="4637d-146">Chcete-li ladit tohoto poskytovatele pomocí příkazů Print, vytvořte skript, který zveřejňuje problém se zprostředkovatelem, a poté použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="4637d-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="4637d-147">Pokud chcete tohoto poskytovatele ladit pomocí sady Visual Studio, otevřete Developer Command Prompt pro Visual Studio s přihlašovacími údaji správce a spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4637d-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="4637d-148">Jako alternativu otevřete aplikaci Visual Studio, otevřete nabídku ladění, vyberte možnost `Debug/Attach to process…`a připojte se k jinému procesu `devenv`, ve kterém jste skript upravovali.</span><span class="sxs-lookup"><span data-stu-id="4637d-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="4637d-149">Pomocí této metody můžete snadněji cílit specifickou logiku v poskytovateli typu pomocí interaktivního psaní výrazů do druhé instance (s plnou IntelliSense a dalšími funkcemi).</span><span class="sxs-lookup"><span data-stu-id="4637d-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="4637d-150">Můžete zakázat ladění Pouze můj kód pro lepší identifikaci chyb v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="4637d-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="4637d-151">Informace o tom, jak povolit nebo zakázat tuto funkci, naleznete v tématu [navigace prostřednictvím kódu pomocí ladicího programu](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="4637d-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="4637d-152">Také můžete nastavit možnost zachycení výjimky s první pravděpodobností tak, že otevřete nabídku `Debug` a pak vyberete `Exceptions` nebo výběrem kláves CTRL + ALT + E otevřete dialogové okno `Exceptions`.</span><span class="sxs-lookup"><span data-stu-id="4637d-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="4637d-153">V tomto dialogovém okně zaškrtněte v části `Common Language Runtime Exceptions`zaškrtávací políčko `Thrown`.</span><span class="sxs-lookup"><span data-stu-id="4637d-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="4637d-154">Implementace poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="4637d-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="4637d-155">V této části se seznámíte s hlavními částmi implementace poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="4637d-156">Nejprve definujte typ samotného vlastního poskytovatele typu:</span><span class="sxs-lookup"><span data-stu-id="4637d-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="4637d-157">Tento typ musí být veřejný a musí být označen atributem [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) , aby kompilátor rozpoznal poskytovatele typu, když samostatný F# projekt odkazuje na sestavení, které obsahuje daný typ.</span><span class="sxs-lookup"><span data-stu-id="4637d-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="4637d-158">Parametr *Konfigurace* je nepovinný a pokud je k dispozici, obsahuje kontextové informace o konfiguraci pro instanci poskytovatele typu F# , kterou kompilátor vytvoří.</span><span class="sxs-lookup"><span data-stu-id="4637d-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="4637d-159">Dále implementujete rozhraní [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) .</span><span class="sxs-lookup"><span data-stu-id="4637d-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="4637d-160">V tomto případě použijete typ `TypeProviderForNamespaces` z rozhraní API `ProvidedTypes` jako základní typ.</span><span class="sxs-lookup"><span data-stu-id="4637d-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="4637d-161">Tento typ pomocníka může poskytnout konečnou kolekci oborů názvů eagerly, z nichž každá z nich přímo obsahuje konečný počet pevných eagerly poskytovaných typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="4637d-162">V tomto kontextu zprostředkovatel *eagerly* generuje typy i v případě, že nejsou požadovány nebo použity.</span><span class="sxs-lookup"><span data-stu-id="4637d-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="4637d-163">Dále definujte místní soukromé hodnoty, které určují obor názvů pro poskytnuté typy a vyhledejte samotné sestavení poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="4637d-164">Toto sestavení je použito později jako logický nadřazený typ vymazaných typů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4637d-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="4637d-165">Dále vytvořte funkci, která poskytne každému z typů typ1... Type100.</span><span class="sxs-lookup"><span data-stu-id="4637d-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="4637d-166">Tato funkce je podrobněji vysvětlena dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4637d-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="4637d-167">Dále vygenerujte poskytnuté typy 100:</span><span class="sxs-lookup"><span data-stu-id="4637d-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="4637d-168">Dále přidejte typy jako poskytnutý obor názvů:</span><span class="sxs-lookup"><span data-stu-id="4637d-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="4637d-169">Nakonec přidejte atribut Assembly, který označuje, že vytváříte knihovnu DLL typu zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="4637d-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="4637d-170">Poskytování jednoho typu a jeho členů</span><span class="sxs-lookup"><span data-stu-id="4637d-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="4637d-171">Funkce `makeOneProvidedType` provádí skutečnou práci jednoho z typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="4637d-172">Tento krok vysvětluje implementaci této funkce.</span><span class="sxs-lookup"><span data-stu-id="4637d-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="4637d-173">Nejprve vytvořte poskytnutý typ (například typ1, pokud n = 1 nebo Type57, pokud n = 57).</span><span class="sxs-lookup"><span data-stu-id="4637d-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="4637d-174">Všimněte si, že byste měli mít na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="4637d-174">You should note the following points:</span></span>

- <span data-ttu-id="4637d-175">Tento poskytnutý typ se vymaže.</span><span class="sxs-lookup"><span data-stu-id="4637d-175">This provided type is erased.</span></span>  <span data-ttu-id="4637d-176">Vzhledem k tomu, že označíte, že základní typ je `obj`, instance se zobrazí jako hodnoty typu [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) v kompilovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="4637d-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="4637d-177">Pokud zadáte nevnořený typ, je nutné zadat sestavení a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="4637d-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="4637d-178">U vymazaných typů by sestavení mělo být samotné sestavení poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="4637d-179">Dále přidejte dokumentaci XML k typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="4637d-180">Tato dokumentace je zpožděná, to znamená, že je vypočítaná na vyžádání, pokud ji hostitel kompilátor potřebuje.</span><span class="sxs-lookup"><span data-stu-id="4637d-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="4637d-181">Dále přidáte poskytnutou statickou vlastnost do tohoto typu:</span><span class="sxs-lookup"><span data-stu-id="4637d-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="4637d-182">Získání této vlastnosti se vždy vyhodnotí jako řetězec "Hello!".</span><span class="sxs-lookup"><span data-stu-id="4637d-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="4637d-183">`GetterCode` pro vlastnost používá F# citace, která představuje kód, který kompilátor hostitele generuje pro získání vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4637d-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="4637d-184">Další informace o nabídkách naleznete v tématu [Code quotes (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="4637d-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="4637d-185">Přidejte do vlastnosti dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="4637d-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="4637d-186">Nyní připojí poskytnutou vlastnost k poskytnutému typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="4637d-187">Zadaný člen musíte připojit k jednomu typu a pouze k jednomu typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="4637d-188">V opačném případě nebude člen nikdy přístupný.</span><span class="sxs-lookup"><span data-stu-id="4637d-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="4637d-189">Nyní vytvořte poskytnutý konstruktor, který nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="4637d-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="4637d-190">`InvokeCode` pro konstruktor vrací F# citát, který představuje kód, který kompilátor hostitele generuje při volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4637d-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="4637d-191">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="4637d-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="4637d-192">Instance poskytnutého typu bude vytvořena pomocí podkladových dat "data objektů".</span><span class="sxs-lookup"><span data-stu-id="4637d-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="4637d-193">Kód v uvozovkách obsahuje převod na [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) , protože tento typ je vymazání tohoto poskytnutého typu (jak jste určili při deklaraci poskytnutého typu).</span><span class="sxs-lookup"><span data-stu-id="4637d-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="4637d-194">Přidejte do konstruktoru dokumentaci XML a přidejte poskytnutý konstruktor k poskytnutému typu:</span><span class="sxs-lookup"><span data-stu-id="4637d-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="4637d-195">Vytvořte druhý poskytnutý konstruktor, který přijímá jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="4637d-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="4637d-196">`InvokeCode` pro konstruktor znovu vrátí F# citaci, která představuje kód, který kompilátor hostitele vygeneroval pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="4637d-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="4637d-197">Například můžete použít následující konstruktor:</span><span class="sxs-lookup"><span data-stu-id="4637d-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="4637d-198">Instance poskytnutého typu se vytvoří se základními daty "deset".</span><span class="sxs-lookup"><span data-stu-id="4637d-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="4637d-199">Je možné, že již jste si všimli, že funkce `InvokeCode` vrací citát.</span><span class="sxs-lookup"><span data-stu-id="4637d-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="4637d-200">Vstup této funkce je seznam výrazů, jeden pro každý parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4637d-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="4637d-201">V tomto případě je v `args.[0]`k dispozici výraz, který představuje hodnotu jednoho parametru.</span><span class="sxs-lookup"><span data-stu-id="4637d-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="4637d-202">Kód pro volání konstruktoru převede návratovou hodnotu na vymazaný typ `obj`.</span><span class="sxs-lookup"><span data-stu-id="4637d-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="4637d-203">Po přidání druhého poskytnutého konstruktoru do typu vytvoříte vlastnost poskytnuté instance:</span><span class="sxs-lookup"><span data-stu-id="4637d-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="4637d-204">Získání této vlastnosti vrátí délku řetězce, což je objekt reprezentace.</span><span class="sxs-lookup"><span data-stu-id="4637d-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="4637d-205">Vlastnost `GetterCode` vrátí F# citát, který určuje kód, který kompilátor hostitele vygeneruje, aby získal vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4637d-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="4637d-206">Podobně jako `InvokeCode`funkce `GetterCode` vrací citace.</span><span class="sxs-lookup"><span data-stu-id="4637d-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="4637d-207">Kompilátor hostitele volá tuto funkci se seznamem argumentů.</span><span class="sxs-lookup"><span data-stu-id="4637d-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="4637d-208">V tomto případě argumenty obsahují pouze jeden výraz, který představuje instanci, na kterou je volána metoda getter, ke které můžete přistupovat pomocí `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="4637d-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="4637d-209">Implementace `GetterCode` poté se do výsledné nabídky na vymazaném typu `obj`zaznamená a přetypování se používá k uspokojení mechanismu kompilátoru pro kontrolu typů, které jsou v objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="4637d-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="4637d-210">Další část `makeOneProvidedType` poskytuje metodu instance s jedním parametrem.</span><span class="sxs-lookup"><span data-stu-id="4637d-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="4637d-211">Nakonec vytvořte vnořený typ, který obsahuje 100 vnořených vlastností.</span><span class="sxs-lookup"><span data-stu-id="4637d-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="4637d-212">Vytváření tohoto vnořeného typu a jeho vlastností je zpožděné, tj. počítané na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="4637d-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="4637d-213">Podrobnosti o vymazaných poskytnutých typech</span><span class="sxs-lookup"><span data-stu-id="4637d-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="4637d-214">Příklad v této části poskytuje pouze *smazány poskytnuté typy*, které jsou zvláště užitečné v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="4637d-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="4637d-215">Při psaní poskytovatele pro informační prostor, který obsahuje pouze data a metody.</span><span class="sxs-lookup"><span data-stu-id="4637d-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="4637d-216">Při psaní poskytovatele, kde je správná Sémantika typu za běhu není kritická pro praktické použití informačního prostoru.</span><span class="sxs-lookup"><span data-stu-id="4637d-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="4637d-217">Při psaní poskytovatele pro informační prostor, který je tak velký a propojuje, že není technicky proveditelné generovat reálné typy .NET pro informační prostor.</span><span class="sxs-lookup"><span data-stu-id="4637d-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="4637d-218">V tomto příkladu je každý poskytnutý typ smazán do typu `obj`a všechna použití tohoto typu se zobrazí jako typ `obj` v kompilovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="4637d-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="4637d-219">Základní objekty v těchto příkladech jsou ve skutečnosti řetězce, ale typ se zobrazí jako `System.Object` v kompilovaném kódu .NET.</span><span class="sxs-lookup"><span data-stu-id="4637d-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="4637d-220">Stejně jako u všech použití typu vymazání lze použít explicitní zabalení, rozbalení a přetypování k převedení smazáných typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="4637d-221">V takovém případě výjimka přetypování, která není platná, může být výsledkem použití objektu.</span><span class="sxs-lookup"><span data-stu-id="4637d-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="4637d-222">Modul runtime zprostředkovatele může definovat svůj vlastní typ soukromé reprezentace, který bude pomáhat chránit před falešnými reprezentacemi.</span><span class="sxs-lookup"><span data-stu-id="4637d-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="4637d-223">Vymazáné typy nelze definovat F# samostatně.</span><span class="sxs-lookup"><span data-stu-id="4637d-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="4637d-224">Vymazat lze pouze poskytnuté typy.</span><span class="sxs-lookup"><span data-stu-id="4637d-224">Only provided types may be erased.</span></span> <span data-ttu-id="4637d-225">Je nutné porozumět vlivům, které jsou praktické i sémantické, pro použití buď vymazaných typů pro poskytovatele typu, nebo poskytovatele, který poskytuje vymazatelné typy.</span><span class="sxs-lookup"><span data-stu-id="4637d-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="4637d-226">Vymazaný typ nemá žádný skutečný typ .NET.</span><span class="sxs-lookup"><span data-stu-id="4637d-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="4637d-227">Proto nemůžete provést přesnou reflexi pro daný typ a můžete převádět vymazané typy, pokud používáte přetypování za běhu a další techniky, které spoléhají na přesnou sémantiku typu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4637d-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="4637d-228">Podverze vymazaných typů často vede k výjimkám přetypování typů za běhu.</span><span class="sxs-lookup"><span data-stu-id="4637d-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="4637d-229">Volba reprezentace pro vymazané poskytnuté typy</span><span class="sxs-lookup"><span data-stu-id="4637d-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="4637d-230">Pro některá použití vymazaných poskytnutých typů není žádná reprezentace nutná.</span><span class="sxs-lookup"><span data-stu-id="4637d-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="4637d-231">Například vymazaný poskytnutý typ může obsahovat pouze statické vlastnosti a členy a žádné konstruktory a žádné metody nebo vlastnosti by nevracely instanci typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="4637d-232">Pokud máte přístup k instancím vymazaného poskytnutého typu, je třeba vzít v úvahu následující otázky:</span><span class="sxs-lookup"><span data-stu-id="4637d-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="4637d-233">**Jaký je vymazání poskytnutého typu?**</span><span class="sxs-lookup"><span data-stu-id="4637d-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="4637d-234">Vymazání poskytnutého typu je způsob, jakým se typ objevuje v kompilovaném kódu .NET.</span><span class="sxs-lookup"><span data-stu-id="4637d-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="4637d-235">Vymazání poskytnutého typu vymazání třídy je vždy prvním nesmazáným základním typem v řetězci dědičnosti daného typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="4637d-236">Mazání zadaného typu smazáného rozhraní je vždy `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="4637d-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="4637d-237">**Jaké jsou reprezentace poskytnutého typu?**</span><span class="sxs-lookup"><span data-stu-id="4637d-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="4637d-238">Sada možných objektů pro vymazaný poskytnutý typ se nazývá reprezentace.</span><span class="sxs-lookup"><span data-stu-id="4637d-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="4637d-239">V příkladu v tomto dokumentu jsou reprezentace všech vymazaných poskytnutých typů `Type1..Type100` vždy řetězcové objekty.</span><span class="sxs-lookup"><span data-stu-id="4637d-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="4637d-240">Všechny reprezentace poskytnutého typu musí být kompatibilní s vymazáním poskytnutého typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="4637d-241">(V opačném případě F# buď kompilátor poskytne chybu pro použití poskytovatele typu, nebo neověřený kód .NET, který není platný, bude vygenerován.</span><span class="sxs-lookup"><span data-stu-id="4637d-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="4637d-242">Poskytovatel typu není platný, pokud vrací kód, který poskytuje reprezentaci, jež není platná.)</span><span class="sxs-lookup"><span data-stu-id="4637d-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="4637d-243">Můžete zvolit reprezentace pro poskytnuté objekty pomocí některého z následujících přístupů, z nichž obě jsou velmi běžné:</span><span class="sxs-lookup"><span data-stu-id="4637d-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="4637d-244">Pokud jednoduše poskytujete obálku silného typu přes existující typ rozhraní .NET, často to dává smysl pro typ, který se má na tento typ vymazat, použít instance daného typu jako reprezentace nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="4637d-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="4637d-245">Tento přístup je vhodný v případě, že většina existujících metod tohoto typu stále dává smysl při použití silně typované verze.</span><span class="sxs-lookup"><span data-stu-id="4637d-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="4637d-246">Pokud chcete vytvořit rozhraní API, které se významně liší od jakékoli existující rozhraní .NET API, má smysl vytvořit běhové typy, které budou typem vymazání a reprezentace pro poskytnuté typy.</span><span class="sxs-lookup"><span data-stu-id="4637d-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="4637d-247">Příklad v tomto dokumentu používá jako reprezentace poskytovaných objektů řetězce.</span><span class="sxs-lookup"><span data-stu-id="4637d-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="4637d-248">Často může být vhodné použít pro reprezentace jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="4637d-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="4637d-249">Jako kontejner objektů a dat můžete například použít slovník:</span><span class="sxs-lookup"><span data-stu-id="4637d-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="4637d-250">Alternativně můžete definovat typ v poskytovateli typu, který bude použit za běhu za účelem vytvoření reprezentace, společně s jednou nebo více běhovými operacemi:</span><span class="sxs-lookup"><span data-stu-id="4637d-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="4637d-251">Dodané členy pak mohou vytvořit instance tohoto typu objektu:</span><span class="sxs-lookup"><span data-stu-id="4637d-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="4637d-252">V takovém případě můžete (volitelně) použít tento typ jako typ mazání zadáním tohoto typu jako `baseType` při sestavování `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="4637d-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="4637d-253">Nejdůležitější lekce</span><span class="sxs-lookup"><span data-stu-id="4637d-253">Key Lessons</span></span>

<span data-ttu-id="4637d-254">Předchozí část vysvětluje, jak vytvořit jednoduchý poskytovatel typu mazání, který poskytuje rozsah typů, vlastností a metod.</span><span class="sxs-lookup"><span data-stu-id="4637d-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="4637d-255">Tato část také vysvětluje koncept typu vymazání, včetně některých výhod a nevýhod poskytování vymazaných typů od poskytovatele typu a popisuje reprezentace vymazaných typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="4637d-256">Zprostředkovatel typu, který používá statické parametry</span><span class="sxs-lookup"><span data-stu-id="4637d-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="4637d-257">Možnost parametrizovat zprostředkovatele typů pomocí statických dat umožňuje mnoho zajímavých scénářů, i když zprostředkovatel nepotřebuje přístup k místním nebo vzdáleným datům.</span><span class="sxs-lookup"><span data-stu-id="4637d-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="4637d-258">V této části se seznámíte s některými základními postupy pro dohromady tohoto poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="4637d-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="4637d-259">Typ kontrolovaného regulárního výrazu</span><span class="sxs-lookup"><span data-stu-id="4637d-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="4637d-260">Představte si, že chcete implementovat poskytovatele typu pro regulární výrazy, které zabalí knihovny <xref:System.Text.RegularExpressions.Regex> .NET v rozhraní, které poskytuje následující záruky při kompilaci:</span><span class="sxs-lookup"><span data-stu-id="4637d-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="4637d-261">Ověřuje se, jestli je regulární výraz platný.</span><span class="sxs-lookup"><span data-stu-id="4637d-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="4637d-262">Poskytování pojmenovaných vlastností na shodách, které jsou založeny na libovolných názvech skupin v regulárním výrazu.</span><span class="sxs-lookup"><span data-stu-id="4637d-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="4637d-263">V této části se dozvíte, jak používat poskytovatele typů k vytvoření `RegexTyped`ho typu, který parameterizes vzor regulárního výrazu k poskytnutí těchto výhod.</span><span class="sxs-lookup"><span data-stu-id="4637d-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="4637d-264">Kompilátor ohlásí chybu, pokud zadaný vzor není platný a poskytovatel typu může extrahovat skupiny ze vzoru, abyste k nim měli přístup pomocí pojmenovaných vlastností na shodách.</span><span class="sxs-lookup"><span data-stu-id="4637d-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="4637d-265">Při návrhu poskytovatele typu byste měli vzít v úvahu, jak by jeho vystavené rozhraní API mělo vypadat koncovým uživatelům a jak se tento návrh převede na kód .NET.</span><span class="sxs-lookup"><span data-stu-id="4637d-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="4637d-266">Následující příklad ukazuje, jak použít takové rozhraní API k získání komponent kódu oblasti:</span><span class="sxs-lookup"><span data-stu-id="4637d-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="4637d-267">Následující příklad ukazuje, jak poskytovatel typu překládá tato volání:</span><span class="sxs-lookup"><span data-stu-id="4637d-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="4637d-268">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="4637d-268">Note the following points:</span></span>

- <span data-ttu-id="4637d-269">Standardní typ regulárního výrazu představuje parametrizovaný typ `RegexTyped`.</span><span class="sxs-lookup"><span data-stu-id="4637d-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="4637d-270">Konstruktor `RegexTyped` má za následek volání konstruktoru regulárního výrazu, který předává argument statického typu pro daný vzor.</span><span class="sxs-lookup"><span data-stu-id="4637d-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="4637d-271">Výsledky metody `Match` jsou reprezentovány standardním typem <xref:System.Text.RegularExpressions.Match>.</span><span class="sxs-lookup"><span data-stu-id="4637d-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="4637d-272">Každá pojmenovaná skupina má za následek zadanou vlastnost a přístup k ní má za následek použití indexeru v kolekci `Groups` shody.</span><span class="sxs-lookup"><span data-stu-id="4637d-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="4637d-273">Následující kód je základem logiky pro implementaci takového poskytovatele a tento příklad vynechává přidání všech členů k poskytnutému typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="4637d-274">Informace o jednotlivých přidaných členech naleznete v příslušné části dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4637d-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="4637d-275">Úplný kód si stáhněte z [ F# ukázkového balíčku 3,0](https://archive.codeplex.com/?p=fsharp3sample) na webu CodePlex.</span><span class="sxs-lookup"><span data-stu-id="4637d-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="4637d-276">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="4637d-276">Note the following points:</span></span>

- <span data-ttu-id="4637d-277">Poskytovatel typu používá dva statické parametry: `pattern`, který je povinný a `options`, která jsou volitelná (protože je k dispozici výchozí hodnota).</span><span class="sxs-lookup"><span data-stu-id="4637d-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="4637d-278">Po zadání statických argumentů vytvoříte instanci regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="4637d-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="4637d-279">Tato instance vyvolá výjimku, pokud je regulární výraz poškozen a tato chyba bude hlášena uživatelům.</span><span class="sxs-lookup"><span data-stu-id="4637d-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="4637d-280">V rámci zpětného volání `DefineStaticParameters` definujete typ, který bude vrácen po zadání argumentů.</span><span class="sxs-lookup"><span data-stu-id="4637d-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="4637d-281">Tento kód nastaví `HideObjectMethods` na hodnotu true, aby prostředí IntelliSense zůstalo zjednodušené.</span><span class="sxs-lookup"><span data-stu-id="4637d-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="4637d-282">Tento atribut způsobí, že `Equals`, `GetHashCode`, `Finalize`a `GetType` mají být potlačeny ze seznamů IntelliSense pro zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="4637d-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="4637d-283">Použijete `obj` jako základní typ metody, ale použijete objekt `Regex` jako běhovou reprezentaci tohoto typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="4637d-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="4637d-284">Volání konstruktoru `Regex` vyvolá <xref:System.ArgumentException>, pokud regulární výraz není platný.</span><span class="sxs-lookup"><span data-stu-id="4637d-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="4637d-285">Kompilátor zachytí tuto výjimku a oznámí uživateli chybovou zprávu v době kompilace nebo v editoru sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4637d-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="4637d-286">Tato výjimka umožňuje ověřovat regulární výrazy bez spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4637d-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="4637d-287">Výše definovaný typ ještě není užitečný, protože neobsahuje žádné smysluplné metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4637d-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="4637d-288">Nejprve přidejte statickou `IsMatch` metodu:</span><span class="sxs-lookup"><span data-stu-id="4637d-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="4637d-289">Předchozí kód definuje metodu `IsMatch`, která přebírá řetězec jako vstup a vrací `bool`.</span><span class="sxs-lookup"><span data-stu-id="4637d-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="4637d-290">Jediná část štychu je použití argumentu `args` v rámci definice `InvokeCode`.</span><span class="sxs-lookup"><span data-stu-id="4637d-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="4637d-291">V tomto příkladu je `args` seznam nabídek, které představují argumenty této metody.</span><span class="sxs-lookup"><span data-stu-id="4637d-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="4637d-292">Pokud je metoda metodou instance, představuje první argument argument `this`.</span><span class="sxs-lookup"><span data-stu-id="4637d-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="4637d-293">Nicméně pro statickou metodu jsou argumenty pouze explicitní argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="4637d-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="4637d-294">Všimněte si, že typ hodnoty v uvozovkách by měl odpovídat zadanému návratový typ (v tomto případě `bool`).</span><span class="sxs-lookup"><span data-stu-id="4637d-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="4637d-295">Všimněte si také, že tento kód používá metodu `AddXmlDoc`, abyste se ujistili, že poskytnutá metoda má také užitečnou dokumentaci, kterou lze dodávat prostřednictvím technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4637d-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="4637d-296">Dále přidejte metodu shody instance.</span><span class="sxs-lookup"><span data-stu-id="4637d-296">Next, add an instance Match method.</span></span> <span data-ttu-id="4637d-297">Tato metoda však by měla vracet hodnotu poskytnutého `Match`ho typu tak, aby k nim bylo možné získat pøístup v silně typovaném typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="4637d-298">Proto nejprve deklarujete typ `Match`.</span><span class="sxs-lookup"><span data-stu-id="4637d-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="4637d-299">Vzhledem k tomu, že tento typ závisí na vzoru, který byl zadán jako statický argument, tento typ musí být vnořen v rámci definice parametrizovaného typu:</span><span class="sxs-lookup"><span data-stu-id="4637d-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="4637d-300">Pak pro každou skupinu přidejte jednu vlastnost k typu shody.</span><span class="sxs-lookup"><span data-stu-id="4637d-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="4637d-301">V době běhu je shoda vyjádřena jako hodnota <xref:System.Text.RegularExpressions.Match>, takže citace, která definuje vlastnost, musí k získání příslušné skupiny používat vlastnost <xref:System.Text.RegularExpressions.Match.Groups> Indexed.</span><span class="sxs-lookup"><span data-stu-id="4637d-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="4637d-302">Znovu si všimněte, že přidáváte dokumentaci XML do poskytnuté vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4637d-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="4637d-303">Všimněte si také, že vlastnost může být přečtena, pokud je k dispozici funkce `GetterCode` a vlastnost může být zapsána, pokud je k dispozici funkce `SetterCode`, takže výsledná vlastnost je určena pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4637d-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="4637d-304">Nyní můžete vytvořit metodu instance, která vrací hodnotu tohoto `Match` typ:</span><span class="sxs-lookup"><span data-stu-id="4637d-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="4637d-305">Vzhledem k tomu, že vytváříte metodu instance, `args.[0]` představuje instanci `RegexTyped`, na které je metoda volána, a `args.[1]` je vstupní argument.</span><span class="sxs-lookup"><span data-stu-id="4637d-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="4637d-306">Nakonec poskytněte konstruktor, aby bylo možné vytvořit instance poskytnutého typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="4637d-307">Konstruktor se pouze vymaže na vytvoření standardní instance jazyka .NET, která je opět zabalena do objektu, protože `obj` je vymazání poskytnutého typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="4637d-308">V důsledku této změny funguje ukázkové použití rozhraní API, které je uvedené dříve v tématu, funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="4637d-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="4637d-309">Následující kód je kompletní a konečný:</span><span class="sxs-lookup"><span data-stu-id="4637d-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="4637d-310">Nejdůležitější lekce</span><span class="sxs-lookup"><span data-stu-id="4637d-310">Key Lessons</span></span>

<span data-ttu-id="4637d-311">Tato část vysvětluje, jak vytvořit poskytovatele typu, který pracuje na jeho statických parametrech.</span><span class="sxs-lookup"><span data-stu-id="4637d-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="4637d-312">Poskytovatel kontroluje statický parametr a poskytuje operace na základě jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4637d-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="4637d-313">Poskytovatel typu, který je zálohovaný místními daty</span><span class="sxs-lookup"><span data-stu-id="4637d-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="4637d-314">Často můžete chtít, aby poskytovatelé typů mohli prezentovat rozhraní API, a to na základě nejen statických parametrů, ale také informací z místních nebo vzdálených systémů.</span><span class="sxs-lookup"><span data-stu-id="4637d-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="4637d-315">Tato část pojednává o poskytovatelích typů, které jsou založeny na místních datech, například v místních datových souborech.</span><span class="sxs-lookup"><span data-stu-id="4637d-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="4637d-316">Jednoduchý poskytovatel souborů CSV</span><span class="sxs-lookup"><span data-stu-id="4637d-316">Simple CSV File Provider</span></span>

<span data-ttu-id="4637d-317">Jednoduchým příkladem je zvážit poskytovatele typu pro přístup k vědeckým datům ve formátu CSV (čárkami oddělených hodnot).</span><span class="sxs-lookup"><span data-stu-id="4637d-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="4637d-318">V této části se předpokládá, že soubory CSV obsahují řádek záhlaví následovaný daty s plovoucí desetinnou čárkou, jak ukazuje následující tabulka:</span><span class="sxs-lookup"><span data-stu-id="4637d-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="4637d-319">Vzdálenost (měřič)</span><span class="sxs-lookup"><span data-stu-id="4637d-319">Distance (meter)</span></span>|<span data-ttu-id="4637d-320">Čas (sekundy)</span><span class="sxs-lookup"><span data-stu-id="4637d-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="4637d-321">50,0</span><span class="sxs-lookup"><span data-stu-id="4637d-321">50.0</span></span>|<span data-ttu-id="4637d-322">3,7</span><span class="sxs-lookup"><span data-stu-id="4637d-322">3.7</span></span>|
|<span data-ttu-id="4637d-323">100,0</span><span class="sxs-lookup"><span data-stu-id="4637d-323">100.0</span></span>|<span data-ttu-id="4637d-324">5,2</span><span class="sxs-lookup"><span data-stu-id="4637d-324">5.2</span></span>|
|<span data-ttu-id="4637d-325">150,0</span><span class="sxs-lookup"><span data-stu-id="4637d-325">150.0</span></span>|<span data-ttu-id="4637d-326">6,4</span><span class="sxs-lookup"><span data-stu-id="4637d-326">6.4</span></span>|

<span data-ttu-id="4637d-327">V této části se dozvíte, jak poskytnout typ, který lze použít k získání řádků s vlastností `Distance` typu `float<meter>` a vlastností `Time` typu `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="4637d-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="4637d-328">Pro zjednodušení jsou provedeny následující předpoklady:</span><span class="sxs-lookup"><span data-stu-id="4637d-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="4637d-329">Názvy hlaviček jsou buď menší než jednotka, nebo mají formát "název (jednotka)" a neobsahují čárky.</span><span class="sxs-lookup"><span data-stu-id="4637d-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="4637d-330">Jednotky jsou všechny jednotky systému, které jsou mezinárodní (si), jako modul [Microsoft. FSharp. data. UnitSystems. siF#. UnitNames ()](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) definuje.</span><span class="sxs-lookup"><span data-stu-id="4637d-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="4637d-331">Jednotky jsou všechny jednoduché (například měřič), nikoli složené (například měřič za sekundu).</span><span class="sxs-lookup"><span data-stu-id="4637d-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="4637d-332">Všechny sloupce obsahují data s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="4637d-332">All columns contain floating point data.</span></span>

<span data-ttu-id="4637d-333">Doplněný poskytovatel by tato omezení vyvolal.</span><span class="sxs-lookup"><span data-stu-id="4637d-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="4637d-334">V prvním kroku se můžete podívat, jak by mělo rozhraní API vypadat.</span><span class="sxs-lookup"><span data-stu-id="4637d-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="4637d-335">Mějme soubor `info.csv` s obsahem z předchozí tabulky (ve formátu odděleném čárkami). Uživatelé poskytovatele by měli být schopni napsat kód, který se podobá následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="4637d-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="4637d-336">V tomto případě by měl kompilátor převést tato volání na něco podobného jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4637d-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="4637d-337">Optimální překlad bude vyžadovat, aby poskytovatel typu definoval typ reálného `CsvFile` v sestavení poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="4637d-338">Poskytovatelé typů často spoléhají na několik pomocných typů a metod pro zabalení důležité logiky.</span><span class="sxs-lookup"><span data-stu-id="4637d-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="4637d-339">Vzhledem k tomu, že se míry vymažou za běhu, můžete jako vymazaný typ řádku použít `float[]`.</span><span class="sxs-lookup"><span data-stu-id="4637d-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="4637d-340">Kompilátor bude zacházet s různými sloupci s různými typy měr.</span><span class="sxs-lookup"><span data-stu-id="4637d-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="4637d-341">Například první sloupec v našem příkladu má typ `float<meter>`a druhý má `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="4637d-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="4637d-342">Smazáná reprezentace ale může zůstat poměrně jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="4637d-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="4637d-343">Následující kód ukazuje základní implementaci.</span><span class="sxs-lookup"><span data-stu-id="4637d-343">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="4637d-344">Všimněte si následujících bodů implementace:</span><span class="sxs-lookup"><span data-stu-id="4637d-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="4637d-345">Přetížené konstruktory umožňují načíst buď původní soubor, nebo jeden, který má stejné schéma.</span><span class="sxs-lookup"><span data-stu-id="4637d-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="4637d-346">Tento model je běžný při psaní poskytovatele typu pro místní nebo vzdálené zdroje dat. Tento model umožňuje použít jako šablonu pro vzdálená data místní soubor.</span><span class="sxs-lookup"><span data-stu-id="4637d-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="4637d-347">Můžete použít hodnotu [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) , která je předána konstruktoru poskytovatele typu k překladu relativních názvů souborů.</span><span class="sxs-lookup"><span data-stu-id="4637d-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="4637d-348">Můžete použít metodu `AddDefinitionLocation` k definování umístění poskytovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="4637d-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="4637d-349">Proto pokud použijete `Go To Definition` pro poskytnutou vlastnost, soubor CSV se otevře v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4637d-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="4637d-350">Typ `ProvidedMeasureBuilder` můžete použít k vyhledání jednotek typu SI a k vygenerování relevantních `float<_>` typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="4637d-351">Nejdůležitější lekce</span><span class="sxs-lookup"><span data-stu-id="4637d-351">Key Lessons</span></span>

<span data-ttu-id="4637d-352">Tato část vysvětluje, jak vytvořit poskytovatele typu pro místní zdroj dat pomocí jednoduchého schématu, které je obsaženo v samotném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="4637d-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="4637d-353">Dál</span><span class="sxs-lookup"><span data-stu-id="4637d-353">Going Further</span></span>

<span data-ttu-id="4637d-354">Následující části obsahují návrhy pro další studii.</span><span class="sxs-lookup"><span data-stu-id="4637d-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="4637d-355">Podívejte se na zkompilovaný kód pro vymazané typy.</span><span class="sxs-lookup"><span data-stu-id="4637d-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="4637d-356">Chcete-li poskytnout určitou představu o tom, jak použití poskytovatele typu odpovídá kódu, který je generován, podívejte se na následující funkci pomocí `HelloWorldTypeProvider`, která je použita dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4637d-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="4637d-357">Tady je obrázek výsledného kódu, který se dekompiluje pomocí programu Ildasm. exe:</span><span class="sxs-lookup"><span data-stu-id="4637d-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="4637d-358">Jak je znázorněno v příkladu, všechny zmínky o typu `Type1` a vlastnost `InstanceProperty` byly smazány, přičemž jsou zapojeny pouze operace s typy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4637d-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="4637d-359">Návrhy a zásady vytváření názvů pro poskytovatele typů</span><span class="sxs-lookup"><span data-stu-id="4637d-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="4637d-360">Při vytváření poskytovatelů typů Sledujte následující konvence.</span><span class="sxs-lookup"><span data-stu-id="4637d-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="4637d-361">**Poskytovatelé protokolů připojení** Obecně platí, že názvy většiny knihoven DLL poskytovatele pro data a protokoly připojení služby, jako jsou například připojení OData nebo SQL, by měly končit `TypeProvider` nebo `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="4637d-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="4637d-362">Například použijte název knihovny DLL, který se podobá následujícímu řetězci:</span><span class="sxs-lookup"><span data-stu-id="4637d-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="4637d-363">Zajistěte, aby poskytnuté typy byly členy odpovídajícího oboru názvů, a označte protokol připojení, který jste implementovali:</span><span class="sxs-lookup"><span data-stu-id="4637d-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="4637d-364">**Poskytovatelé nástrojů pro obecné kódování**.</span><span class="sxs-lookup"><span data-stu-id="4637d-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="4637d-365">Pro poskytovatele typu nástrojů, jako je například pro regulární výrazy, může být poskytovatel typu součástí základní knihovny, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="4637d-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="4637d-366">V tomto případě se poskytnutý typ zobrazí v odpovídajícím bodě podle normálních konvencí pro návrh .NET:</span><span class="sxs-lookup"><span data-stu-id="4637d-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="4637d-367">**Nejednoznačné zdroje dat**.</span><span class="sxs-lookup"><span data-stu-id="4637d-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="4637d-368">Někteří poskytovatelé typů se připojují k jednomu vyhrazenému zdroji dat a poskytují pouze data.</span><span class="sxs-lookup"><span data-stu-id="4637d-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="4637d-369">V takovém případě byste měli vyřadit příponu `TypeProvider` a používat normální konvence pro pojmenování .NET:</span><span class="sxs-lookup"><span data-stu-id="4637d-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="4637d-370">Další informace najdete v tématu `GetConnection` konvence návrhu, která je popsána dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="4637d-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="4637d-371">Vzory návrhu pro poskytovatele typů</span><span class="sxs-lookup"><span data-stu-id="4637d-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="4637d-372">Následující části popisují vzory návrhu, které můžete použít při vytváření poskytovatelů typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="4637d-373">Vzor návrhu GetConnection</span><span class="sxs-lookup"><span data-stu-id="4637d-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="4637d-374">Většina poskytovatelů typů by měla být zapsána pro použití `GetConnection`ho vzoru, který používají Zprostředkovatelé typů v souboru FSharp. data. TypeProviders. dll, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="4637d-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="4637d-375">Poskytovatelé typů zálohovaných vzdálenými daty a službami</span><span class="sxs-lookup"><span data-stu-id="4637d-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="4637d-376">Předtím, než vytvoříte poskytovatele typu, který je zajištěný pomocí vzdálených dat a služeb, je třeba vzít v úvahu řadu problémů, které jsou součástí připojeného programování.</span><span class="sxs-lookup"><span data-stu-id="4637d-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="4637d-377">Mezi tyto problémy patří následující aspekty:</span><span class="sxs-lookup"><span data-stu-id="4637d-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="4637d-378">mapování schématu</span><span class="sxs-lookup"><span data-stu-id="4637d-378">schema mapping</span></span>

- <span data-ttu-id="4637d-379">živý a neplatnost v přítomnosti změny schématu</span><span class="sxs-lookup"><span data-stu-id="4637d-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="4637d-380">ukládání schématu do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="4637d-380">schema caching</span></span>

- <span data-ttu-id="4637d-381">asynchronní implementace operací přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="4637d-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="4637d-382">podpůrné dotazy, včetně dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="4637d-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="4637d-383">přihlašovací údaje a ověřování</span><span class="sxs-lookup"><span data-stu-id="4637d-383">credentials and authentication</span></span>

<span data-ttu-id="4637d-384">V tomto tématu se tyto problémy podrobněji nezobrazují.</span><span class="sxs-lookup"><span data-stu-id="4637d-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="4637d-385">Další techniky vytváření obsahu</span><span class="sxs-lookup"><span data-stu-id="4637d-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="4637d-386">Při psaní vlastních zprostředkovatelů typů je vhodné použít následující další techniky.</span><span class="sxs-lookup"><span data-stu-id="4637d-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="4637d-387">Vytváření typů a členů na vyžádání</span><span class="sxs-lookup"><span data-stu-id="4637d-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="4637d-388">Rozhraní ProvidedType API má opožděné verze AddMember.</span><span class="sxs-lookup"><span data-stu-id="4637d-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="4637d-389">Tyto verze slouží k vytvoření prostorů typu na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="4637d-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="4637d-390">Poskytování typů polí a vytváření instancí obecných typů</span><span class="sxs-lookup"><span data-stu-id="4637d-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="4637d-391">Zadali jste členy (jejichž signatury zahrnují typy polí, typy ByRef a instance obecných typů) pomocí normálního `MakeArrayType`, `MakePointerType`a `MakeGenericType` na jakékoli instanci <xref:System.Type>, včetně `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="4637d-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="4637d-392">V některých případech může být nutné použít pomocníka v `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="4637d-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="4637d-393">Další podrobnosti najdete v [dokumentaci k sadě SDK pro poskytovatele typů](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) .</span><span class="sxs-lookup"><span data-stu-id="4637d-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="4637d-394">Poskytování poznámek k měrné jednotce</span><span class="sxs-lookup"><span data-stu-id="4637d-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="4637d-395">Rozhraní ProvidedTypes API poskytuje nápovědu pro poskytování poznámek k měření.</span><span class="sxs-lookup"><span data-stu-id="4637d-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="4637d-396">Chcete-li například poskytnout typ `float<kg>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="4637d-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="4637d-397">Chcete-li zadat typ `Nullable<decimal<kg/m^2>>`, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="4637d-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="4637d-398">Přístup k místním prostředkům na úrovni projektu nebo na skript</span><span class="sxs-lookup"><span data-stu-id="4637d-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="4637d-399">Každé instanci poskytovatele typu lze předávat `TypeProviderConfig` hodnotu během konstrukce.</span><span class="sxs-lookup"><span data-stu-id="4637d-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="4637d-400">Tato hodnota obsahuje "složku řešení" pro poskytovatele (to znamená složku projektu pro kompilaci nebo adresář, který obsahuje skript), seznam odkazovaných sestavení a další informace.</span><span class="sxs-lookup"><span data-stu-id="4637d-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="4637d-401">Zneplatnění</span><span class="sxs-lookup"><span data-stu-id="4637d-401">Invalidation</span></span>

<span data-ttu-id="4637d-402">Poskytovatelé můžou vyvolávat neplatné signály, které upozorňují F# na službu jazyka, že se předpoklady schématu změnily.</span><span class="sxs-lookup"><span data-stu-id="4637d-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="4637d-403">Pokud dojde k neplatnosti, typecheck se provede, pokud je poskytovatel hostován v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4637d-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="4637d-404">Tento signál bude ignorován, pokud je poskytovatel hostován F# interaktivním nebo F# kompilátorem (FSC. exe).</span><span class="sxs-lookup"><span data-stu-id="4637d-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="4637d-405">Ukládání informací o schématu do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="4637d-405">Caching Schema Information</span></span>

<span data-ttu-id="4637d-406">Poskytovatelé musí často přistupovat k informacím o schématu v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4637d-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="4637d-407">Data uložená v mezipaměti by se měla ukládat pomocí názvu souboru, který je zadaný jako statický parametr nebo jako uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="4637d-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="4637d-408">Příkladem ukládání schématu do mezipaměti je parametr `LocalSchemaFile` ve zprostředkovatelích typů v sestavení `FSharp.Data.TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="4637d-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="4637d-409">V rámci implementace těchto zprostředkovatelů tento statický parametr přesměrovává poskytovatele typu na použití informací o schématu v zadaném místním souboru místo přístupu ke zdroji dat přes síť.</span><span class="sxs-lookup"><span data-stu-id="4637d-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="4637d-410">Chcete-li použít informace o schématu uložené v mezipaměti, je nutné také nastavit statický parametr `ForceUpdate` na `false`.</span><span class="sxs-lookup"><span data-stu-id="4637d-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="4637d-411">Podobnou techniku můžete použít k povolení přístupu k online a offline datům.</span><span class="sxs-lookup"><span data-stu-id="4637d-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="4637d-412">Záložní sestavení</span><span class="sxs-lookup"><span data-stu-id="4637d-412">Backing Assembly</span></span>

<span data-ttu-id="4637d-413">Při kompilaci `.dll` nebo `.exe` souboru je soubor back. dll pro vygenerované typy staticky propojen do výsledného sestavení.</span><span class="sxs-lookup"><span data-stu-id="4637d-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="4637d-414">Tento odkaz je vytvořen zkopírováním definic typu Intermediate Language (IL) a všech spravovaných prostředků ze záložního sestavení do konečného sestavení.</span><span class="sxs-lookup"><span data-stu-id="4637d-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="4637d-415">Když použijete F# Interactive, soubor back. dll se nezkopíruje a místo toho se načte přímo do F# interaktivního procesu.</span><span class="sxs-lookup"><span data-stu-id="4637d-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="4637d-416">Výjimky a diagnostika od zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="4637d-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="4637d-417">Všechna použití všech členů ze zadaných typů mohou vyvolat výjimky.</span><span class="sxs-lookup"><span data-stu-id="4637d-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="4637d-418">Ve všech případech, pokud poskytovatel typu vyvolá výjimku, kompilátor hostitele zavolá chybu na konkrétního poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="4637d-419">Výjimky poskytovatele typu by nikdy neměly vést k vnitřním chybám kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4637d-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="4637d-420">Zprostředkovatelé typů nemůžou oznamovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="4637d-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="4637d-421">Když je poskytovatel typu hostovaný v F# kompilátoru, F# vývojovém prostředí nebo F# interaktivním, jsou zachyceny všechny výjimky z tohoto poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="4637d-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="4637d-422">Vlastnost Message je vždycky text chyby a nezobrazí se žádné trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4637d-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="4637d-423">Pokud budete vyvolávat výjimku, můžete vyvolat následující příklady: `System.NotSupportedException`, `System.IO.IOException``System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="4637d-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="4637d-424">Poskytování generovaných typů</span><span class="sxs-lookup"><span data-stu-id="4637d-424">Providing Generated Types</span></span>

<span data-ttu-id="4637d-425">V tomto dokumentu se zatím vyvolalo, jak poskytnout vymazatelné typy.</span><span class="sxs-lookup"><span data-stu-id="4637d-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="4637d-426">Můžete také použít mechanismus poskytovatele typu v F# k poskytnutí generovaných typů, které jsou přidány jako reálné definice typu .NET do programu uživatelé.</span><span class="sxs-lookup"><span data-stu-id="4637d-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="4637d-427">Musíte odkazovat na generované poskytnuté typy pomocí definice typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="4637d-428">Pomocný kód ProvidedTypes-0,2, který je součástí verze F# 3,0, má pouze omezené podpory pro poskytování generovaných typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="4637d-429">Následující příkazy musí být pro definici generovaného typu pravdivé:</span><span class="sxs-lookup"><span data-stu-id="4637d-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="4637d-430">`isErased` musí být nastavené na `false`.</span><span class="sxs-lookup"><span data-stu-id="4637d-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="4637d-431">Vygenerovaný typ musí být přidán do nově konstruovaného `ProvidedAssembly()`, který představuje kontejner pro vygenerované fragmenty kódu.</span><span class="sxs-lookup"><span data-stu-id="4637d-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="4637d-432">Poskytovatel musí mít sestavení, které má aktuální soubor .NET. dll s odpovídajícím souborem. dll na disku.</span><span class="sxs-lookup"><span data-stu-id="4637d-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="4637d-433">Pravidla a omezení</span><span class="sxs-lookup"><span data-stu-id="4637d-433">Rules and Limitations</span></span>

<span data-ttu-id="4637d-434">Při psaní poskytovatelů typů mějte na paměti následující pravidla a omezení.</span><span class="sxs-lookup"><span data-stu-id="4637d-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="4637d-435">Poskytnuté typy musí být dosažitelné.</span><span class="sxs-lookup"><span data-stu-id="4637d-435">Provided types must be reachable</span></span>

<span data-ttu-id="4637d-436">Všechny poskytnuté typy by měly být dosažitelné z nevnořených typů.</span><span class="sxs-lookup"><span data-stu-id="4637d-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="4637d-437">Nevnořené typy jsou uvedeny ve volání konstruktoru `TypeProviderForNamespaces` nebo volání `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="4637d-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="4637d-438">Například pokud poskytovatel poskytuje typ `StaticClass.P : T`, je nutné zajistit, že T je buď nevnořený typ, nebo je vnořen do jednoho.</span><span class="sxs-lookup"><span data-stu-id="4637d-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="4637d-439">Někteří poskytovatelé mají například statickou třídu jako `DataTypes`, která obsahuje tyto typy `T1, T2, T3, ...`.</span><span class="sxs-lookup"><span data-stu-id="4637d-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="4637d-440">V opačném případě chyba říká, že byl nalezen odkaz na typ T v sestavení A, ale tento typ se v tomto sestavení nenašel.</span><span class="sxs-lookup"><span data-stu-id="4637d-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="4637d-441">Pokud se zobrazí tato chyba, ověřte, zda jsou všechny podtypy dostupné z typů poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="4637d-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="4637d-442">Poznámka: tyto typy `T1, T2, T3...` jsou označovány jako *průběžné* typy.</span><span class="sxs-lookup"><span data-stu-id="4637d-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="4637d-443">Nezapomeňte je umístit do přístupného oboru názvů nebo nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="4637d-444">Omezení mechanismu poskytovatele typu</span><span class="sxs-lookup"><span data-stu-id="4637d-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="4637d-445">Mechanismus poskytovatele typu v F# má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="4637d-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="4637d-446">Základní infrastruktura pro zprostředkovatele typů v F# nepodporuje poskytnuté obecné typy ani poskytnuté obecné metody.</span><span class="sxs-lookup"><span data-stu-id="4637d-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="4637d-447">Mechanismus nepodporuje vnořené typy se statickými parametry.</span><span class="sxs-lookup"><span data-stu-id="4637d-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="4637d-448">Tipy pro vývoj</span><span class="sxs-lookup"><span data-stu-id="4637d-448">Development Tips</span></span>

<span data-ttu-id="4637d-449">Následující tipy mohou být užitečné během procesu vývoje:</span><span class="sxs-lookup"><span data-stu-id="4637d-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="4637d-450">Spuštění dvou instancí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4637d-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="4637d-451">Můžete vyvíjet poskytovatele typu v jedné instanci a otestovat poskytovatele v druhé, protože testovací prostředí IDE povede zámek na soubor. dll, který brání opětovnému sestavení poskytovatele typu.</span><span class="sxs-lookup"><span data-stu-id="4637d-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="4637d-452">Proto je nutné zavřít druhou instanci sady Visual Studio, když je poskytovatel sestaven v první instanci a poté po sestavení poskytovatele znovu otevřít druhou instanci.</span><span class="sxs-lookup"><span data-stu-id="4637d-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="4637d-453">Poskytovatelé typu ladění pomocí volání FSC. exe</span><span class="sxs-lookup"><span data-stu-id="4637d-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="4637d-454">Zprostředkovatele typů můžete vyvolat pomocí následujících nástrojů:</span><span class="sxs-lookup"><span data-stu-id="4637d-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="4637d-455">FSC. exe (kompilátor F# příkazového řádku)</span><span class="sxs-lookup"><span data-stu-id="4637d-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="4637d-456">FSI. exe ( F# interaktivní kompilátor)</span><span class="sxs-lookup"><span data-stu-id="4637d-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="4637d-457">devenv. exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="4637d-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="4637d-458">Můžete často ladit poskytovatele typu, a to pomocí FSC. exe v souboru testovacího skriptu (například Script. FSX).</span><span class="sxs-lookup"><span data-stu-id="4637d-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="4637d-459">Ladicí program můžete spustit z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4637d-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="4637d-460">Můžete použít protokolování pro tisk do STDOUT.</span><span class="sxs-lookup"><span data-stu-id="4637d-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="4637d-461">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4637d-461">See also</span></span>

- [<span data-ttu-id="4637d-462">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="4637d-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="4637d-463">Sada SDK typu zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="4637d-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
