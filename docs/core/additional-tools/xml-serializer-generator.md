---
title: "Pomocí generátoru serializátor Microsoft XML na .NET Core"
description: "Přehled generátor serializátor XML společnosti Microsoft."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="642b7-103">Pomocí generátoru serializátor Microsoft XML na .NET Core</span><span class="sxs-lookup"><span data-stu-id="642b7-103">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="642b7-104">V tomto kurzu se naučíte, jak používat generátor serializátor XML společnosti Microsoft v aplikaci C# .NET Core.</span><span class="sxs-lookup"><span data-stu-id="642b7-104">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="642b7-105">V průběhu tohoto kurzu se seznámíte:</span><span class="sxs-lookup"><span data-stu-id="642b7-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="642b7-106">Jak vytvořit aplikaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="642b7-106">How to create a .NET Core app</span></span>
> * <span data-ttu-id="642b7-107">Jak přidat odkaz na balíček Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="642b7-107">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="642b7-108">Úprava vaší MyApp.csproj přidat závislosti</span><span class="sxs-lookup"><span data-stu-id="642b7-108">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="642b7-109">Přidání třídy a třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="642b7-109">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="642b7-110">Postup vytvoření a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="642b7-110">How to build and run the application</span></span> 

<span data-ttu-id="642b7-111">Jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) je ekvivalentem pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="642b7-111">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="642b7-112">Vytvoří sestavení serializace XML pro typy, které jsou součástí sestavení, které chcete zvýšit výkon při spuštění serializace XML při serializaci nebo zrušte serializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="642b7-112">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="642b7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="642b7-113">Prerequisites</span></span>

<span data-ttu-id="642b7-114">K dokončení tohoto kurzu:</span><span class="sxs-lookup"><span data-stu-id="642b7-114">To complete this tutorial:</span></span>

* <span data-ttu-id="642b7-115">Nainstalujte [.NET Core SDK 2.1.3 nebo novější](https://www.microsoft.com/net/download)</span><span class="sxs-lookup"><span data-stu-id="642b7-115">Install [.NET Core SDK 2.1.3 or later](https://www.microsoft.com/net/download)</span></span>
* <span data-ttu-id="642b7-116">Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="642b7-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="642b7-117">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="642b7-117">Need to install a code editor?</span></span> <span data-ttu-id="642b7-118">Zkuste [sady Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="642b7-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="642b7-119">Použít Microsoft XML serializátor generátor v konzolové aplikaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="642b7-119">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="642b7-120">Následující pokyny ukazují, jak používat generátor serializátor XML v konzolové aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="642b7-120">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="642b7-121">Vytvoření aplikace konzoly .NET Core</span><span class="sxs-lookup"><span data-stu-id="642b7-121">Create a .NET Core console application</span></span>

<span data-ttu-id="642b7-122">Otevřete příkazový řádek a vytvořte složku s názvem *Moje aplikace*.</span><span class="sxs-lookup"><span data-stu-id="642b7-122">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="642b7-123">Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="642b7-123">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="642b7-124">Přidat odkaz na balíček Microsoft.XmlSerializer.Generator v projektu Moje aplikace</span><span class="sxs-lookup"><span data-stu-id="642b7-124">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="642b7-125">Použití [ `dotnet add package` ](../tools//dotnet-add-package.md) příkaz Přidat odkaz ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="642b7-125">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="642b7-126">Typ:</span><span class="sxs-lookup"><span data-stu-id="642b7-126">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="642b7-127">Ověřit si změny MyApp.csproj po přidání balíčku</span><span class="sxs-lookup"><span data-stu-id="642b7-127">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="642b7-128">Otevřete editor kódu a můžeme začít!</span><span class="sxs-lookup"><span data-stu-id="642b7-128">Open your code editor and let's get started!</span></span> <span data-ttu-id="642b7-129">Stále pracujeme z *Moje aplikace* jsme vytvořili aplikaci v adresáři.</span><span class="sxs-lookup"><span data-stu-id="642b7-129">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="642b7-130">Otevřete *MyApp.csproj* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="642b7-130">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="642b7-131">Po spuštění [ `dotnet add package` ](../tools//dotnet-add-package.md) příkazu, jsou přidány následující řádky do vaší *MyApp.csproj* soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="642b7-131">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="642b7-132">Přidat jinou část ItemGroup pro podporu rozhraní .NET Core rozhraní příkazového řádku nástroje</span><span class="sxs-lookup"><span data-stu-id="642b7-132">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="642b7-133">Přidejte následující řádky po `ItemGroup` oddíl, který jsme prověřovány:</span><span class="sxs-lookup"><span data-stu-id="642b7-133">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="642b7-134">Přidání třídy v aplikaci</span><span class="sxs-lookup"><span data-stu-id="642b7-134">Add a class in the application</span></span>

<span data-ttu-id="642b7-135">Otevřete *Program.cs* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="642b7-135">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="642b7-136">Přidejte třídu s názvem *MyClass* v *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="642b7-136">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="642b7-137">Vytvoření `XmlSerializer` pro MyClass</span><span class="sxs-lookup"><span data-stu-id="642b7-137">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="642b7-138">Přidejte následující řádek uvnitř *hlavní* vytvořit `XmlSerializer` pro MyClass:</span><span class="sxs-lookup"><span data-stu-id="642b7-138">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="642b7-139">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="642b7-139">Build and run the application</span></span>

<span data-ttu-id="642b7-140">Stále ještě v *Moje aplikace* složky, spusťte aplikaci prostřednictvím [ `dotnet run` ](../tools/dotnet-run.md) a automaticky načte a používá předem vygenerovaná serializátorů za běhu.</span><span class="sxs-lookup"><span data-stu-id="642b7-140">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="642b7-141">Zadejte následující příkaz v okně konzoly:</span><span class="sxs-lookup"><span data-stu-id="642b7-141">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="642b7-142">[`dotnet run`](../tools/dotnet-run.md)volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby sestavení, které se sestavily cíle a poté zavolá `dotnet <assembly.dll>` ke spuštění cílová aplikace.</span><span class="sxs-lookup"><span data-stu-id="642b7-142">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="642b7-143">Příkazy a postupy v tomto kurzu ke spuštění vaší aplikace se používají pouze dobu vývoj.</span><span class="sxs-lookup"><span data-stu-id="642b7-143">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="642b7-144">Jakmile budete připraveni k nasazení své aplikace, prohlédněte si různými [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="642b7-144">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="642b7-145">Pokud všechno proběhne úspěšně, sestavení s názvem *MyApp.XmlSerializers.dll* se generuje ve výstupní složce.</span><span class="sxs-lookup"><span data-stu-id="642b7-145">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="642b7-146">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="642b7-146">Congratulations!</span></span> <span data-ttu-id="642b7-147">máte právě:</span><span class="sxs-lookup"><span data-stu-id="642b7-147">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="642b7-148">Vytvořit .NET Core aplikace.</span><span class="sxs-lookup"><span data-stu-id="642b7-148">Created a .NET Core app.</span></span>
> * <span data-ttu-id="642b7-149">Přidat odkaz na balíček Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="642b7-149">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="642b7-150">Upravit vaše MyApp.csproj přidat závislosti.</span><span class="sxs-lookup"><span data-stu-id="642b7-150">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="642b7-151">Přidání třídy a XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="642b7-151">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="642b7-152">Vytvořené a spustil aplikaci.</span><span class="sxs-lookup"><span data-stu-id="642b7-152">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="642b7-153">Související informační zdroje</span><span class="sxs-lookup"><span data-stu-id="642b7-153">Related Resources</span></span>

* [<span data-ttu-id="642b7-154">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="642b7-154">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="642b7-155">Postupy: serializace pomocí třídy XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="642b7-155">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [<span data-ttu-id="642b7-156">Postupy: serializace pomocí třídy XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="642b7-156">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
