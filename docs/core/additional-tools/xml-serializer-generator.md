---
title: Generátor serializátor XML společnosti Microsoft
description: Přehled generátor serializátor XML společnosti Microsoft. Generátor serializátor XML můžete generovat sestavení serializace XML pro typy obsažené v projektu.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 74d10b0fb27a4acf477fc66451a5cf6fc1f4317c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631696"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="4cab4-104">Pomocí generátor serializátor XML společnosti Microsoft v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cab4-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="4cab4-105">V tomto kurzu se naučíte, jak používat generátor serializátor XML společnosti Microsoft v C# aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4cab4-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="4cab4-106">V průběhu tohoto kurzu se dozvíte:</span><span class="sxs-lookup"><span data-stu-id="4cab4-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="4cab4-107">Jak vytvořit aplikaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cab4-107">How to create a .NET Core app</span></span>
> * <span data-ttu-id="4cab4-108">Jak přidat odkaz na balíček Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="4cab4-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="4cab4-109">Úprava vaše MyApp.csproj přidat závislosti</span><span class="sxs-lookup"><span data-stu-id="4cab4-109">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="4cab4-110">Přidání třídy a objektu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="4cab4-110">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="4cab4-111">Jak sestavit a spustit aplikaci</span><span class="sxs-lookup"><span data-stu-id="4cab4-111">How to build and run the application</span></span>

<span data-ttu-id="4cab4-112">Podobně jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) ekvivalent pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4cab4-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="4cab4-113">Vytvoří sestavení serializace XML pro typy, které jsou obsaženy v sestavení, které chcete zlepšit výkon při spuštění serializace XML při serializaci nebo deserializaci objektů z těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4cab4-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4cab4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cab4-114">Prerequisites</span></span>

<span data-ttu-id="4cab4-115">K provedení kroků v tomto kurzu je potřeba:</span><span class="sxs-lookup"><span data-stu-id="4cab4-115">To complete this tutorial:</span></span>

* <span data-ttu-id="4cab4-116">[Sady SDK .NET core 2.1](https://www.microsoft.com/net/download) nebo novější</span><span class="sxs-lookup"><span data-stu-id="4cab4-116">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="4cab4-117">Váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="4cab4-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="4cab4-118">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="4cab4-118">Need to install a code editor?</span></span> <span data-ttu-id="4cab4-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="4cab4-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="4cab4-120">Použít Microsoft generátor serializátor XML v konzolovou aplikaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cab4-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="4cab4-121">Následující pokyny ukazují, jak používat generátor serializátor XML v konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4cab4-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="4cab4-122">Vytvořte konzolovou aplikaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cab4-122">Create a .NET Core console application</span></span>

<span data-ttu-id="4cab4-123">Otevřete příkazový řádek a vytvořte složku s názvem *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="4cab4-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="4cab4-124">Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4cab4-124">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="4cab4-125">Přidejte odkaz na balíček Microsoft.XmlSerializer.Generator MyApp projektu</span><span class="sxs-lookup"><span data-stu-id="4cab4-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="4cab4-126">Použití [ `dotnet add package` ](../tools//dotnet-add-package.md) příkaz pro přidání odkazu ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="4cab4-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="4cab4-127">Zadejte:</span><span class="sxs-lookup"><span data-stu-id="4cab4-127">Type:</span></span>

```console
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="4cab4-128">Ověřit si změny MyApp.csproj po přidání balíčku</span><span class="sxs-lookup"><span data-stu-id="4cab4-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="4cab4-129">Otevřete editor kódu a můžeme začít!</span><span class="sxs-lookup"><span data-stu-id="4cab4-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="4cab4-130">Pořád pracujeme z *MyApp* jsme vytvořili aplikaci v adresáři.</span><span class="sxs-lookup"><span data-stu-id="4cab4-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="4cab4-131">Otevřít *MyApp.csproj* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="4cab4-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="4cab4-132">Po spuštění [ `dotnet add package` ](../tools//dotnet-add-package.md) příkazu následující řádky se přidají do vašeho *MyApp.csproj* souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="4cab4-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="4cab4-133">Přidejte další část ItemGroup pro podporu nástroje rozhraní příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cab4-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="4cab4-134">Přidejte následující řádky za `ItemGroup` oddíl, který jsme ho zkontrolovat:</span><span class="sxs-lookup"><span data-stu-id="4cab4-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="4cab4-135">Přidejte třídu v aplikaci</span><span class="sxs-lookup"><span data-stu-id="4cab4-135">Add a class in the application</span></span>

<span data-ttu-id="4cab4-136">Otevřít *Program.cs* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="4cab4-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="4cab4-137">Přidejte třídu s názvem *MyClass* v *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="4cab4-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="4cab4-138">Vytvoření `XmlSerializer` pro MyClass</span><span class="sxs-lookup"><span data-stu-id="4cab4-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="4cab4-139">Přidejte následující řádek uvnitř *hlavní* k vytvoření `XmlSerializer` pro MyClass:</span><span class="sxs-lookup"><span data-stu-id="4cab4-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="4cab4-140">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="4cab4-140">Build and run the application</span></span>

<span data-ttu-id="4cab4-141">Pořád ještě uvnitř *MyApp* složky, spusťte aplikaci prostřednictvím [ `dotnet run` ](../tools/dotnet-run.md) a automaticky načte a používá předem generovaného serializátory za běhu.</span><span class="sxs-lookup"><span data-stu-id="4cab4-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="4cab4-142">Zadejte následující příkaz v okně konzoly:</span><span class="sxs-lookup"><span data-stu-id="4cab4-142">Type the following command in your console window:</span></span>

```console
dotnet run
```

> [!NOTE]
> <span data-ttu-id="4cab4-143">[`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby se sestavily cíle sestavení a poté zavolá `dotnet <assembly.dll>` spustit cílovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4cab4-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4cab4-144">Příkazy a postupy v tomto kurzu ke spuštění aplikace se používají pouze během vývoje.</span><span class="sxs-lookup"><span data-stu-id="4cab4-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="4cab4-145">Jakmile budete připraveni k nasazení své aplikace, podívejte se na různé [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="4cab4-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="4cab4-146">Pokud všechno proběhne úspěšně, sestavení s názvem *MyApp.XmlSerializers.dll* se generuje ve výstupní složce.</span><span class="sxs-lookup"><span data-stu-id="4cab4-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="4cab4-147">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="4cab4-147">Congratulations!</span></span> <span data-ttu-id="4cab4-148">máte jen:</span><span class="sxs-lookup"><span data-stu-id="4cab4-148">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="4cab4-149">Vytvoření .NET Core aplikace.</span><span class="sxs-lookup"><span data-stu-id="4cab4-149">Created a .NET Core app.</span></span>
> * <span data-ttu-id="4cab4-150">Přidat odkaz na balíček Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="4cab4-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="4cab4-151">Upravit vaše MyApp.csproj přidat závislosti.</span><span class="sxs-lookup"><span data-stu-id="4cab4-151">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="4cab4-152">Přidat třídu a objektu XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="4cab4-152">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="4cab4-153">Vytvořené a byla aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="4cab4-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="4cab4-154">Související prostředky</span><span class="sxs-lookup"><span data-stu-id="4cab4-154">Related resources</span></span>

* [<span data-ttu-id="4cab4-155">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="4cab4-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="4cab4-156">Postupy: Serializace pomocí třídy XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="4cab4-156">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [<span data-ttu-id="4cab4-157">Postupy: Serializace pomocí třídy XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cab4-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
