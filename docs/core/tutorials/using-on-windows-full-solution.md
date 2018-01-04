---
title: "Vytvoření kompletního řešení .NET Core do systému Windows, pomocí Visual Studio 2017"
description: "Zjistěte, jak sestavit kompletní .NET Core řešení ve Visual Studio 2017 v systému Windows."
keywords: "Rozhraní .NET, .NET core"
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ba7e082c-a7c8-431e-a342-f67734b660f6
ms.workload: dotnetcore
ms.openlocfilehash: e922a2c91fab5c513f5c560920d37d77da2d6f84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="faa7b-104">Vytvoření kompletního řešení .NET Core do systému Windows, pomocí Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="faa7b-104">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="faa7b-105">Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="faa7b-105">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="faa7b-106">Postupy v tomto dokumentu popisují kroky potřebné k vytvoření typické .NET Core řešení, které obsahuje opakovaně použitelné knihovny, testování a používání knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="faa7b-106">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="faa7b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="faa7b-107">Prerequisites</span></span>

<span data-ttu-id="faa7b-108">Postupujte podle pokynů [naší stránce s požadavky](../windows-prerequisites.md) aktualizovat vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="faa7b-108">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="faa7b-109">Řešení pomocí jenom .NET Core projekty</span><span class="sxs-lookup"><span data-stu-id="faa7b-109">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="faa7b-110">Zápis knihovny</span><span class="sxs-lookup"><span data-stu-id="faa7b-110">Writing the library</span></span>

1. <span data-ttu-id="faa7b-111">V sadě Visual Studio, vyberte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-111">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="faa7b-112">V **nový projekt** dialogové okno, rozbalte **Visual C#** uzlu a zvolte **.NET Standard** uzel a potom vyberte **(.NET Standard)–Knihovnatříd**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-112">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="faa7b-113">Název projektu "Library" a "Golden" řešení.</span><span class="sxs-lookup"><span data-stu-id="faa7b-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="faa7b-114">Nechte **vytvořit adresář pro řešení** zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="faa7b-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="faa7b-115">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-115">Click **OK**.</span></span>

3. <span data-ttu-id="faa7b-116">V Průzkumníku řešení otevřete kontextovou nabídku **závislosti** uzel a zvolte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="faa7b-117">Vyberte "nuget.org" jako **zdroj balíčku**a vyberte **Procházet** kartě. Vyhledejte **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="faa7b-118">Klikněte na tlačítko **nainstalovat**a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="faa7b-118">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="faa7b-119">Balíček by se měla zobrazit v části **závislosti nebo NuGet** a automaticky obnovit.</span><span class="sxs-lookup"><span data-stu-id="faa7b-119">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="faa7b-120">Přejmenujte `Class1.cs` do souboru `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="faa7b-120">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="faa7b-121">Přijměte přejmenování třídy.</span><span class="sxs-lookup"><span data-stu-id="faa7b-121">Accept the rename of the class.</span></span> <span data-ttu-id="faa7b-122">Přidání metody:`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="faa7b-122">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="faa7b-123">Na **sestavení** nabídce zvolte **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-123">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="faa7b-124">Řešení má sestavit bez chyby.</span><span class="sxs-lookup"><span data-stu-id="faa7b-124">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="faa7b-125">Zápis k testovacímu projektu</span><span class="sxs-lookup"><span data-stu-id="faa7b-125">Writing the test project</span></span>

1. <span data-ttu-id="faa7b-126">V Průzkumníku řešení otevřete kontextovou nabídku **řešení** uzel a zvolte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-126">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="faa7b-127">V **nový projekt** dialogové okno, v části **Visual C# nebo .NET Core**, zvolte **projektu testování částí (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-127">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="faa7b-128">Název "TestLibrary" a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="faa7b-128">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="faa7b-129">V **TestLibrary** projektu, otevřete kontextovou nabídku **závislosti** uzel a zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-129">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="faa7b-130">Klikněte na tlačítko **projekty**, zkontrolujte projektu knihovny a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="faa7b-130">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="faa7b-131">Tento postup přidá odkaz na knihovnu z testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="faa7b-131">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="faa7b-132">Přejmenujte `UnitTest1.cs` do souboru `LibraryTests.cs` a přijměte tříd přejmenujte.</span><span class="sxs-lookup"><span data-stu-id="faa7b-132">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="faa7b-133">Přidat `using Library;` na začátek souboru a nahradit `TestMethod1` metoda následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="faa7b-133">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="faa7b-134">Teď by měla být možné sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="faa7b-134">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="faa7b-135">Na **testování** nabídce zvolte **Windows**, **testování Explorer** mohli okno Průzkumníka testů do pracovního prostoru.</span><span class="sxs-lookup"><span data-stu-id="faa7b-135">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="faa7b-136">Za několik sekund `ThingGetsObjectValFromNumber` test by se měla objevit v Průzkumníka testů.</span><span class="sxs-lookup"><span data-stu-id="faa7b-136">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="faa7b-137">Zvolte **spustit všechny**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-137">Choose **Run All**.</span></span>
   
   <span data-ttu-id="faa7b-138">Test by měla předávat.</span><span class="sxs-lookup"><span data-stu-id="faa7b-138">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="faa7b-139">Zápis konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="faa7b-139">Writing the console app</span></span>

1. <span data-ttu-id="faa7b-140">V Průzkumníku řešení otevřete kontextu nabídku pro řešení a přidejte nový **konzolové aplikace (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="faa7b-140">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="faa7b-141">Název "Aplikace".</span><span class="sxs-lookup"><span data-stu-id="faa7b-141">Name it "App".</span></span>

2. <span data-ttu-id="faa7b-142">V **aplikace** projektu, otevřete kontextovou nabídku **závislosti** uzel a zvolte **přidat**, **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-142">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="faa7b-143">V **správce odkazů** dialogové okno, zkontrolujte **knihovny** pod **projekty**, **řešení** uzel a pak klikněte na tlačítko **OK**</span><span class="sxs-lookup"><span data-stu-id="faa7b-143">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="faa7b-144">Otevřete kontextovou nabídku **aplikace** uzel a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="faa7b-144">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="faa7b-145">Tím se zajistí, že stále mačkat F5 nebo CTRL + F5 spustí konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="faa7b-145">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="faa7b-146">Otevřete `Program.cs` soubor, přidejte `using Library;` direktivy do horní části souboru a poté přidejte `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` k `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="faa7b-146">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="faa7b-147">Nastavení boru přerušení po řádek, který jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="faa7b-147">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="faa7b-148">Stisknutím klávesy F5 spusťte aplikaci...</span><span class="sxs-lookup"><span data-stu-id="faa7b-148">Press F5 to run the application..</span></span>

   <span data-ttu-id="faa7b-149">Aplikace má sestavit bez chyby a měli průchodu zarážkou.</span><span class="sxs-lookup"><span data-stu-id="faa7b-149">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="faa7b-150">Musíte mít také možnost zkontrolovat, že aplikace výstup "odpověď je 42.".</span><span class="sxs-lookup"><span data-stu-id="faa7b-150">You should also be able to check that the application output "The answer is 42.".</span></span>
