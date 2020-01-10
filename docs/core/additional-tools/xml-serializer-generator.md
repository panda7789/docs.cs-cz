---
title: Generátor serializátorů Microsoft XML
description: Přehled generátoru serializátorů Microsoft XML Pomocí generátoru serializátoru XML vygenerujte sestavení serializace XML pro typy obsažené ve vašem projektu.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714525"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="ec50f-104">Používání generátoru Microsoft XML serializátoru v .NET Core</span><span class="sxs-lookup"><span data-stu-id="ec50f-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="ec50f-105">V tomto kurzu se naučíte používat generátor serializátoru Microsoft XML v aplikaci C# .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ec50f-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="ec50f-106">V průběhu tohoto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="ec50f-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ec50f-107">Vytvoření aplikace v .NET Core</span><span class="sxs-lookup"><span data-stu-id="ec50f-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="ec50f-108">Přidání odkazu do balíčku Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="ec50f-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="ec50f-109">Úprava souboru MyApp.csproj a přidání závislostí</span><span class="sxs-lookup"><span data-stu-id="ec50f-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="ec50f-110">Přidání třídy a objektu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="ec50f-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="ec50f-111">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ec50f-111">How to build and run the application</span></span>

<span data-ttu-id="ec50f-112">Podobně jako [generátor serializátorů XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro .NET Framework je [balíček NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) ekvivalentem pro projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ec50f-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="ec50f-113">Vytvoří sestavení serializace XML pro typy obsažené v sestavení pro zlepšení výkonu při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ec50f-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec50f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec50f-114">Prerequisites</span></span>

<span data-ttu-id="ec50f-115">K provedení kroků v tomto kurzu je potřeba:</span><span class="sxs-lookup"><span data-stu-id="ec50f-115">To complete this tutorial:</span></span>

- <span data-ttu-id="ec50f-116">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější.</span><span class="sxs-lookup"><span data-stu-id="ec50f-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="ec50f-117">Váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="ec50f-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="ec50f-118">Potřebujete nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="ec50f-118">Need to install a code editor?</span></span> <span data-ttu-id="ec50f-119">Vyzkoušejte [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="ec50f-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="ec50f-120">Použití generátoru Microsoft XML serializátoru v konzolové aplikaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="ec50f-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="ec50f-121">Následující pokyny ukazují, jak používat generátor serializátoru XML v konzolové aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ec50f-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="ec50f-122">Vytvoření konzolové aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="ec50f-122">Create a .NET Core console application</span></span>

<span data-ttu-id="ec50f-123">Otevřete příkazový řádek a vytvořte složku s názvem *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="ec50f-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="ec50f-124">Přejděte do složky, kterou jste vytvořili, a zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ec50f-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="ec50f-125">Přidání odkazu na balíček Microsoft. XmlSerializer. Generator v projektu MyApp</span><span class="sxs-lookup"><span data-stu-id="ec50f-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="ec50f-126">Pomocí příkazu [`dotnet add package`](../tools//dotnet-add-package.md) přidejte odkaz do projektu.</span><span class="sxs-lookup"><span data-stu-id="ec50f-126">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="ec50f-127">Typ:</span><span class="sxs-lookup"><span data-stu-id="ec50f-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="ec50f-128">Po přidání balíčku ověřit změny v MyApp. csproj</span><span class="sxs-lookup"><span data-stu-id="ec50f-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="ec50f-129">Otevřete Editor kódu a pojďme začít!</span><span class="sxs-lookup"><span data-stu-id="ec50f-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="ec50f-130">Pořád pracujeme z adresáře *MyApp* , ve kterém jsme aplikaci sestavili.</span><span class="sxs-lookup"><span data-stu-id="ec50f-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="ec50f-131">Otevřete *MyApp. csproj* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="ec50f-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="ec50f-132">Po spuštění příkazu [`dotnet add package`](../tools//dotnet-add-package.md) jsou do souboru aplikace *MyApp. csproj* přidány následující řádky:</span><span class="sxs-lookup"><span data-stu-id="ec50f-132">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="ec50f-133">Přidání další části skupin položek pro podporu .NET Core CLI nástrojů</span><span class="sxs-lookup"><span data-stu-id="ec50f-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="ec50f-134">Přidejte následující řádky za část `ItemGroup`, kterou jsme zkontrolovali:</span><span class="sxs-lookup"><span data-stu-id="ec50f-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="ec50f-135">Přidání třídy do aplikace</span><span class="sxs-lookup"><span data-stu-id="ec50f-135">Add a class in the application</span></span>

<span data-ttu-id="ec50f-136">Otevřete *program.cs* v textovém editoru.</span><span class="sxs-lookup"><span data-stu-id="ec50f-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="ec50f-137">Přidejte třídu s názvem *MyClass* v *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="ec50f-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="ec50f-138">Vytvoření `XmlSerializer` pro MyClass</span><span class="sxs-lookup"><span data-stu-id="ec50f-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="ec50f-139">Přidejte následující řádek do části *Main* a vytvořte `XmlSerializer` pro MyClass:</span><span class="sxs-lookup"><span data-stu-id="ec50f-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="ec50f-140">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ec50f-140">Build and run the application</span></span>

<span data-ttu-id="ec50f-141">Pořád ve složce *MyApp* spusťte aplikaci prostřednictvím [`dotnet run`](../tools/dotnet-run.md) a automaticky načte a použije předem vygenerované serializace za běhu.</span><span class="sxs-lookup"><span data-stu-id="ec50f-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="ec50f-142">V okně konzoly zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ec50f-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="ec50f-143">[`dotnet run`](../tools/dotnet-run.md) volá [`dotnet build`](../tools/dotnet-build.md) , aby bylo zajištěno, že byly sestaveny cíle sestavení, a poté volá `dotnet <assembly.dll>` pro spuštění cílové aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec50f-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec50f-144">Příkazy a kroky uvedené v tomto kurzu pro spuštění aplikace jsou používány pouze během doby vývoje.</span><span class="sxs-lookup"><span data-stu-id="ec50f-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="ec50f-145">Až budete připraveni k nasazení aplikace, podívejte se na různé [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a příkaz [`dotnet publish`](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="ec50f-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="ec50f-146">Pokud je vše úspěšné, sestavení s názvem *MyApp. XmlSerializers. dll* je vygenerováno ve výstupní složce.</span><span class="sxs-lookup"><span data-stu-id="ec50f-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="ec50f-147">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="ec50f-147">Congratulations!</span></span> <span data-ttu-id="ec50f-148">Právě jste:</span><span class="sxs-lookup"><span data-stu-id="ec50f-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ec50f-149">Vytvořili jste aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ec50f-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="ec50f-150">Byl přidán odkaz na balíček Microsoft. XmlSerializer. Generator.</span><span class="sxs-lookup"><span data-stu-id="ec50f-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="ec50f-151">Úpravou MyApp. csproj přidejte závislosti.</span><span class="sxs-lookup"><span data-stu-id="ec50f-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="ec50f-152">Přidala se třída a XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="ec50f-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="ec50f-153">Sestavila a spustila aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec50f-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="ec50f-154">Související informační zdroje</span><span class="sxs-lookup"><span data-stu-id="ec50f-154">Related resources</span></span>

- [<span data-ttu-id="ec50f-155">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="ec50f-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="ec50f-156">Postup při serializaci pomocí XmlSerializerC#()</span><span class="sxs-lookup"><span data-stu-id="ec50f-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="ec50f-157">Postupy: serializace pomocí XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec50f-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
