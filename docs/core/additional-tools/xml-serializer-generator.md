---
title: Generátor serializátorů XML společnosti Microsoft
description: Přehled generátoru serializátorů XML společnosti Microsoft. Generátor serializátorů XML slouží ke generování sestavení serializace XML pro typy obsažené v projektu.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714525"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="24ff7-104">Použití generátoru serializátorů jazyka Microsoft XML v jádru .NET Core</span><span class="sxs-lookup"><span data-stu-id="24ff7-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="24ff7-105">Tento kurz vás naučí používat generátor serializátorů XML společnosti Microsoft v aplikaci C# .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24ff7-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="24ff7-106">V průběhu tohoto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="24ff7-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="24ff7-107">Vytvoření aplikace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="24ff7-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="24ff7-108">Přidání odkazu do balíčku Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="24ff7-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="24ff7-109">Úprava souboru MyApp.csproj a přidání závislostí</span><span class="sxs-lookup"><span data-stu-id="24ff7-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="24ff7-110">Přidání třídy a objektu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="24ff7-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="24ff7-111">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="24ff7-111">How to build and run the application</span></span>

<span data-ttu-id="24ff7-112">Podobně jako [generátor serializátorů XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework je [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) ekvivalentní pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="24ff7-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="24ff7-113">Vytvoří sestavení serializace XML pro typy obsažené v sestavení ke zlepšení výkonu při spuštění serializace XML při <xref:System.Xml.Serialization.XmlSerializer>serializaci nebo deserializaci objektů těchto typů pomocí .</span><span class="sxs-lookup"><span data-stu-id="24ff7-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24ff7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24ff7-114">Prerequisites</span></span>

<span data-ttu-id="24ff7-115">Pro absolvování tohoto kurzu potřebujete:</span><span class="sxs-lookup"><span data-stu-id="24ff7-115">To complete this tutorial:</span></span>

- <span data-ttu-id="24ff7-116">[Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější.</span><span class="sxs-lookup"><span data-stu-id="24ff7-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="24ff7-117">Váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="24ff7-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="24ff7-118">Potřebujete nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="24ff7-118">Need to install a code editor?</span></span> <span data-ttu-id="24ff7-119">Vyzkoušejte [visual studio!](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="24ff7-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="24ff7-120">Použití generátoru serializátorů jazyka Microsoft XML v aplikaci konzoly .NET Core</span><span class="sxs-lookup"><span data-stu-id="24ff7-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="24ff7-121">Následující pokyny ukazují, jak používat generátor serializátorů XML v aplikaci konzoly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24ff7-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="24ff7-122">Vytvoření konzolové aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="24ff7-122">Create a .NET Core console application</span></span>

<span data-ttu-id="24ff7-123">Otevřete příkazový řádek a vytvořte složku s názvem *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="24ff7-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="24ff7-124">Přejděte do složky, kterou jste vytvořili, a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="24ff7-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="24ff7-125">Přidání odkazu na balíček Microsoft.XmlSerializer.Generator v projektu MyApp</span><span class="sxs-lookup"><span data-stu-id="24ff7-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="24ff7-126">Pomocí [`dotnet add package`](../tools//dotnet-add-package.md) příkazu přidejte odkaz v projektu.</span><span class="sxs-lookup"><span data-stu-id="24ff7-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="24ff7-127">Zadejte:</span><span class="sxs-lookup"><span data-stu-id="24ff7-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="24ff7-128">Ověření změn myapp.csproj po přidání balíčku</span><span class="sxs-lookup"><span data-stu-id="24ff7-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="24ff7-129">Otevřete editor kódu a začneme!</span><span class="sxs-lookup"><span data-stu-id="24ff7-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="24ff7-130">Stále pracujeme z adresáře *MyApp,* do kterýjsme aplikaci vytvořili.</span><span class="sxs-lookup"><span data-stu-id="24ff7-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="24ff7-131">Otevřete *myApp.csproj* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="24ff7-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="24ff7-132">Po spuštění [`dotnet add package`](../tools//dotnet-add-package.md) příkazu se do souboru projektu *MyApp.csproj* přidají následující řádky:</span><span class="sxs-lookup"><span data-stu-id="24ff7-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="24ff7-133">Přidání další části Skupiny položek pro podporu nástroje .NET Core CLI Tool</span><span class="sxs-lookup"><span data-stu-id="24ff7-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="24ff7-134">Za `ItemGroup` oddíl, který jsme zkontrolovali, přidejte následující řádky:</span><span class="sxs-lookup"><span data-stu-id="24ff7-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="24ff7-135">Přidání třídy do aplikace</span><span class="sxs-lookup"><span data-stu-id="24ff7-135">Add a class in the application</span></span>

<span data-ttu-id="24ff7-136">Otevřete *Program.cs* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="24ff7-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="24ff7-137">Přidejte třídu s názvem *MyClass* do *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="24ff7-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="24ff7-138">Vytvořit `XmlSerializer` pro MyClass</span><span class="sxs-lookup"><span data-stu-id="24ff7-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="24ff7-139">Přidejte následující *Main* řádek uvnitř `XmlSerializer` Main pro vytvoření pro MyClass:</span><span class="sxs-lookup"><span data-stu-id="24ff7-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="24ff7-140">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="24ff7-140">Build and run the application</span></span>

<span data-ttu-id="24ff7-141">Stále ve složce *MyApp,* [`dotnet run`](../tools/dotnet-run.md) spusťte aplikaci přes a automaticky načte a používá pre-generované serializers za běhu.</span><span class="sxs-lookup"><span data-stu-id="24ff7-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="24ff7-142">Do okna konzole zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="24ff7-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="24ff7-143">[`dotnet run`](../tools/dotnet-run.md)volání [`dotnet build`](../tools/dotnet-build.md) zajistit, že cíle sestavení byly vytvořeny `dotnet <assembly.dll>` a potom volá ke spuštění cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="24ff7-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24ff7-144">Příkazy a kroky uvedené v tomto kurzu ke spuštění aplikace se používají pouze v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="24ff7-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="24ff7-145">Až budete připraveni k nasazení aplikace, podívejte se na různé [strategie nasazení](../deploying/index.md) [`dotnet publish`](../tools/dotnet-publish.md) pro aplikace .NET Core a příkaz.</span><span class="sxs-lookup"><span data-stu-id="24ff7-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="24ff7-146">Pokud vše úspěšné, sestavení s názvem *MyApp.XmlSerializers.dll* je generovánve výstupní složce.</span><span class="sxs-lookup"><span data-stu-id="24ff7-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="24ff7-147">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="24ff7-147">Congratulations!</span></span> <span data-ttu-id="24ff7-148">Máte jen:</span><span class="sxs-lookup"><span data-stu-id="24ff7-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="24ff7-149">Byla vytvořena aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24ff7-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="24ff7-150">Byl přidán odkaz na balíček Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="24ff7-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="24ff7-151">Upravil myApp.csproj přidat závislosti.</span><span class="sxs-lookup"><span data-stu-id="24ff7-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="24ff7-152">Přidána třída a XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="24ff7-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="24ff7-153">Byla vytvořena a spuštěna aplikace.</span><span class="sxs-lookup"><span data-stu-id="24ff7-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="24ff7-154">Související prostředky</span><span class="sxs-lookup"><span data-stu-id="24ff7-154">Related resources</span></span>

- [<span data-ttu-id="24ff7-155">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="24ff7-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="24ff7-156">Jak serializovat pomocí XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="24ff7-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="24ff7-157">Postup: Serializace pomocí xmlserializeru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24ff7-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
