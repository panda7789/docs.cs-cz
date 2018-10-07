---
title: Vytvoření kompletního řešení .NET Core ve Windows pomocí sady Visual Studio 2017
description: Zjistěte, jak k vytvoření kompletního řešení .NET Core v sadě Visual Studio 2017 na Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: c21c257b55c4389ea4a60fca55eb83cff60ff3b5
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840937"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="627d7-103">Vytvoření kompletního řešení .NET Core ve Windows pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="627d7-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="627d7-104">Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="627d7-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="627d7-105">Postupy v tomto dokumentu popisují kroky potřebné k začlenění typické řešení .NET Core, který obsahuje opakovaně použitelné knihovny, testování a přes knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="627d7-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="627d7-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="627d7-106">Prerequisites</span></span>

<span data-ttu-id="627d7-107">Postupujte podle pokynů [naší stránce s požadavky](../windows-prerequisites.md) k aktualizaci vašeho prostředí.</span><span class="sxs-lookup"><span data-stu-id="627d7-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="627d7-108">Řešení, které využívá jenom projekty .NET Core</span><span class="sxs-lookup"><span data-stu-id="627d7-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="627d7-109">Zápis knihovny</span><span class="sxs-lookup"><span data-stu-id="627d7-109">Writing the library</span></span>

1. <span data-ttu-id="627d7-110">V sadě Visual Studio, zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="627d7-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="627d7-111">V **nový projekt** dialogového okna, rozbalte **Visual C#** uzlu a zvolte **.NET Standard** uzel a klikněte na tlačítko **knihovna tříd (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="627d7-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> <span data-ttu-id="627d7-112">Tím se vytvoří knihovny .NET Standard, který cílí na .NET Core stejně jako jiné implementace .NET, která podporuje verzi 2.0 [.Net Standard](https://docs.microsoft.com/en-us/dotnet/standard/net-standard)</span><span class="sxs-lookup"><span data-stu-id="627d7-112">This creates a .NET Standard library that targets .NET Core as well as any other .NET implementation that supports version 2.0 of the [.Net Standard](https://docs.microsoft.com/en-us/dotnet/standard/net-standard)</span></span>

2. <span data-ttu-id="627d7-113">Název projektu "Library" a "Golden" řešení.</span><span class="sxs-lookup"><span data-stu-id="627d7-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="627d7-114">Ponechte **vytvořit adresář pro řešení** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="627d7-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="627d7-115">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="627d7-115">Click **OK**.</span></span>

3. <span data-ttu-id="627d7-116">V Průzkumníku řešení otevřete kontextovou nabídku **závislosti** uzlu a zvolte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="627d7-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="627d7-117">Zvolte možnost "nuget.org" jako **zdroj balíčku**a zvolte **Procházet** kartu. Vyhledat **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="627d7-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="627d7-118">Klikněte na tlačítko **nainstalovat**a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="627d7-118">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="627d7-119">Balíček by se měl zobrazit v části **závislosti/NuGet** a se automaticky obnoví.</span><span class="sxs-lookup"><span data-stu-id="627d7-119">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="627d7-120">Přejmenovat `Class1.cs` soubor `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="627d7-120">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="627d7-121">Přijměte přejmenování třídy.</span><span class="sxs-lookup"><span data-stu-id="627d7-121">Accept the rename of the class.</span></span> <span data-ttu-id="627d7-122">Přidejte metodu: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="627d7-122">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="627d7-123">Na **sestavení** nabídce zvolte **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="627d7-123">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="627d7-124">Má řešení sestavit bez chyb.</span><span class="sxs-lookup"><span data-stu-id="627d7-124">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="627d7-125">Zápis testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="627d7-125">Writing the test project</span></span>

1. <span data-ttu-id="627d7-126">V Průzkumníku řešení otevřete kontextovou nabídku **řešení** uzlu a zvolte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="627d7-126">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="627d7-127">V **nový projekt** dialogového okna, v části **Visual C# / .NET Core**, zvolte **projekt testu jednotek (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="627d7-127">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="627d7-128">Pojmenujte ji "TestLibrary" a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="627d7-128">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="627d7-129">V **TestLibrary** projektu, otevřete kontextovou nabídku **závislosti** uzlu a zvolte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="627d7-129">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="627d7-130">Klikněte na tlačítko **projekty**, zkontrolujte projekt knihovny a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="627d7-130">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="627d7-131">To přidá odkaz na knihovnu z testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="627d7-131">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="627d7-132">Přejmenovat `UnitTest1.cs` do souboru `LibraryTests.cs` a přijměte přejmenování třídy.</span><span class="sxs-lookup"><span data-stu-id="627d7-132">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="627d7-133">Přidat `using Library;` na začátek souboru a nahraďte `TestMethod1` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="627d7-133">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="627d7-134">Teď by měl být možné sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="627d7-134">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="627d7-135">Na **testování** nabídce zvolte **Windows**, **Průzkumníka testů** zajistí okna Průzkumníka testů do pracovního prostoru.</span><span class="sxs-lookup"><span data-stu-id="627d7-135">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="627d7-136">Po několika sekundách `ThingGetsObjectValFromNumber` test by se měla zobrazit v Průzkumníku testů.</span><span class="sxs-lookup"><span data-stu-id="627d7-136">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="627d7-137">Zvolte **spustit všechny**.</span><span class="sxs-lookup"><span data-stu-id="627d7-137">Choose **Run All**.</span></span>
   
   <span data-ttu-id="627d7-138">Test by měl úspěšný.</span><span class="sxs-lookup"><span data-stu-id="627d7-138">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="627d7-139">Zápis aplikace konzoly</span><span class="sxs-lookup"><span data-stu-id="627d7-139">Writing the console app</span></span>

1. <span data-ttu-id="627d7-140">V Průzkumníku řešení otevřete kontextovou nabídku řešení a přidejte nový **Konzolová aplikace (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="627d7-140">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="627d7-141">Název "Aplikace".</span><span class="sxs-lookup"><span data-stu-id="627d7-141">Name it "App".</span></span>

2. <span data-ttu-id="627d7-142">V **aplikace** projektu, otevřete kontextovou nabídku **závislosti** uzlu a zvolte **přidat**, **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="627d7-142">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="627d7-143">V **správce odkazů** dialogové okno Kontrola **knihovny** pod **projekty**, **řešení** uzlu a pak klikněte na tlačítko **OK**</span><span class="sxs-lookup"><span data-stu-id="627d7-143">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="627d7-144">Otevřete místní nabídku pro **aplikace** uzlu a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="627d7-144">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="627d7-145">Tím se zajistí, že stisknutí F5 nebo CTRL + F5 se spustí aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="627d7-145">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="627d7-146">Otevřít `Program.cs` přidejte `using Library;` na začátek souboru a pak přidejte `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` k `Main` – metoda.</span><span class="sxs-lookup"><span data-stu-id="627d7-146">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="627d7-147">Nastavte zarážku po řádek, který jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="627d7-147">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="627d7-148">Stisknutím klávesy F5 spusťte aplikaci...</span><span class="sxs-lookup"><span data-stu-id="627d7-148">Press F5 to run the application..</span></span>

   <span data-ttu-id="627d7-149">Aplikace má sestavit bez chyb a by měl zarážce.</span><span class="sxs-lookup"><span data-stu-id="627d7-149">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="627d7-150">Musíte mít také možnost zkontrolovat, že aplikace výstupu "odpověď je 42.".</span><span class="sxs-lookup"><span data-stu-id="627d7-150">You should also be able to check that the application output "The answer is 42.".</span></span>
