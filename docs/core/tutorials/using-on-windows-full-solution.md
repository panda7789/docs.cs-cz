---
title: Vytvoření kompletního řešení .NET Core do systému Windows, pomocí Visual Studio 2017
description: Zjistěte, jak sestavit kompletní .NET Core řešení ve Visual Studio 2017 v systému Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 8e37eb578f9c4ac63fbc120e6227098ea69d169d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="9a806-103">Vytvoření kompletního řešení .NET Core do systému Windows, pomocí Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9a806-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="9a806-104">Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a806-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="9a806-105">Postupy v tomto dokumentu popisují kroky potřebné k vytvoření typické .NET Core řešení, které obsahuje opakovaně použitelné knihovny, testování a používání knihoven třetích stran.</span><span class="sxs-lookup"><span data-stu-id="9a806-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="9a806-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a806-106">Prerequisites</span></span>

<span data-ttu-id="9a806-107">Postupujte podle pokynů [naší stránce s požadavky](../windows-prerequisites.md) aktualizovat vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="9a806-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="9a806-108">Řešení pomocí jenom .NET Core projekty</span><span class="sxs-lookup"><span data-stu-id="9a806-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="9a806-109">Zápis knihovny</span><span class="sxs-lookup"><span data-stu-id="9a806-109">Writing the library</span></span>

1. <span data-ttu-id="9a806-110">V sadě Visual Studio, vyberte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="9a806-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="9a806-111">V **nový projekt** dialogové okno, rozbalte **Visual C#** uzlu a zvolte **.NET Standard** uzel a potom vyberte **(.NET Standard)–Knihovnatříd**.</span><span class="sxs-lookup"><span data-stu-id="9a806-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="9a806-112">Název projektu "Library" a "Golden" řešení.</span><span class="sxs-lookup"><span data-stu-id="9a806-112">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="9a806-113">Nechte **vytvořit adresář pro řešení** zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="9a806-113">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="9a806-114">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="9a806-114">Click **OK**.</span></span>

3. <span data-ttu-id="9a806-115">V Průzkumníku řešení otevřete kontextovou nabídku **závislosti** uzel a zvolte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9a806-115">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="9a806-116">Vyberte "nuget.org" jako **zdroj balíčku**a vyberte **Procházet** kartě. Vyhledejte **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="9a806-116">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="9a806-117">Klikněte na tlačítko **nainstalovat**a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="9a806-117">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="9a806-118">Balíček by se měla zobrazit v části **závislosti nebo NuGet** a automaticky obnovit.</span><span class="sxs-lookup"><span data-stu-id="9a806-118">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="9a806-119">Přejmenujte `Class1.cs` do souboru `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="9a806-119">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="9a806-120">Přijměte přejmenování třídy.</span><span class="sxs-lookup"><span data-stu-id="9a806-120">Accept the rename of the class.</span></span> <span data-ttu-id="9a806-121">Přidání metody: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="9a806-121">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="9a806-122">Na **sestavení** nabídce zvolte **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="9a806-122">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="9a806-123">Řešení má sestavit bez chyby.</span><span class="sxs-lookup"><span data-stu-id="9a806-123">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="9a806-124">Zápis k testovacímu projektu</span><span class="sxs-lookup"><span data-stu-id="9a806-124">Writing the test project</span></span>

1. <span data-ttu-id="9a806-125">V Průzkumníku řešení otevřete kontextovou nabídku **řešení** uzel a zvolte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="9a806-125">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="9a806-126">V **nový projekt** dialogové okno, v části **Visual C# nebo .NET Core**, zvolte **projektu testování částí (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="9a806-126">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="9a806-127">Název "TestLibrary" a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="9a806-127">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="9a806-128">V **TestLibrary** projektu, otevřete kontextovou nabídku **závislosti** uzel a zvolte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="9a806-128">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="9a806-129">Klikněte na tlačítko **projekty**, zkontrolujte projektu knihovny a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="9a806-129">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="9a806-130">Tento postup přidá odkaz na knihovnu z testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="9a806-130">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="9a806-131">Přejmenujte `UnitTest1.cs` do souboru `LibraryTests.cs` a přijměte tříd přejmenujte.</span><span class="sxs-lookup"><span data-stu-id="9a806-131">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="9a806-132">Přidat `using Library;` na začátek souboru a nahradit `TestMethod1` metoda následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="9a806-132">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="9a806-133">Teď by měla být možné sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="9a806-133">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="9a806-134">Na **testování** nabídce zvolte **Windows**, **testování Explorer** mohli okno Průzkumníka testů do pracovního prostoru.</span><span class="sxs-lookup"><span data-stu-id="9a806-134">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="9a806-135">Za několik sekund `ThingGetsObjectValFromNumber` test by se měla objevit v Průzkumníka testů.</span><span class="sxs-lookup"><span data-stu-id="9a806-135">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="9a806-136">Zvolte **spustit všechny**.</span><span class="sxs-lookup"><span data-stu-id="9a806-136">Choose **Run All**.</span></span>
   
   <span data-ttu-id="9a806-137">Test by měla předávat.</span><span class="sxs-lookup"><span data-stu-id="9a806-137">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="9a806-138">Zápis konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="9a806-138">Writing the console app</span></span>

1. <span data-ttu-id="9a806-139">V Průzkumníku řešení otevřete kontextu nabídku pro řešení a přidejte nový **konzolové aplikace (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="9a806-139">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="9a806-140">Název "Aplikace".</span><span class="sxs-lookup"><span data-stu-id="9a806-140">Name it "App".</span></span>

2. <span data-ttu-id="9a806-141">V **aplikace** projektu, otevřete kontextovou nabídku **závislosti** uzel a zvolte **přidat**, **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="9a806-141">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="9a806-142">V **správce odkazů** dialogové okno, zkontrolujte **knihovny** pod **projekty**, **řešení** uzel a pak klikněte na tlačítko **OK**</span><span class="sxs-lookup"><span data-stu-id="9a806-142">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="9a806-143">Otevřete kontextovou nabídku **aplikace** uzel a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="9a806-143">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="9a806-144">Tím se zajistí, že stále mačkat F5 nebo CTRL + F5 spustí konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9a806-144">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="9a806-145">Otevřete `Program.cs` soubor, přidejte `using Library;` direktivy do horní části souboru a poté přidejte `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` k `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="9a806-145">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="9a806-146">Nastavení boru přerušení po řádek, který jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="9a806-146">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="9a806-147">Stisknutím klávesy F5 spusťte aplikaci...</span><span class="sxs-lookup"><span data-stu-id="9a806-147">Press F5 to run the application..</span></span>

   <span data-ttu-id="9a806-148">Aplikace má sestavit bez chyby a měli průchodu zarážkou.</span><span class="sxs-lookup"><span data-stu-id="9a806-148">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="9a806-149">Musíte mít také možnost zkontrolovat, že aplikace výstup "odpověď je 42.".</span><span class="sxs-lookup"><span data-stu-id="9a806-149">You should also be able to check that the application output "The answer is 42.".</span></span>
