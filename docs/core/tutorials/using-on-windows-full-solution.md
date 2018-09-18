---
title: Vytvoření kompletního řešení .NET Core ve Windows pomocí sady Visual Studio 2017
description: Zjistěte, jak k vytvoření kompletního řešení .NET Core v sadě Visual Studio 2017 na Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: 15537ea8c68b5c873bbf26ab0519a19de0b13230
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969558"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="51e54-103">Vytvoření kompletního řešení .NET Core ve Windows pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="51e54-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="51e54-104">Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vývoj aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51e54-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="51e54-105">Postupy v tomto dokumentu popisují kroky potřebné k začlenění typické řešení .NET Core, který obsahuje opakovaně použitelné knihovny, testování a přes knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="51e54-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="51e54-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51e54-106">Prerequisites</span></span>

<span data-ttu-id="51e54-107">Postupujte podle pokynů [naší stránce s požadavky](../windows-prerequisites.md) k aktualizaci vašeho prostředí.</span><span class="sxs-lookup"><span data-stu-id="51e54-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="51e54-108">Řešení, které využívá jenom projekty .NET Core</span><span class="sxs-lookup"><span data-stu-id="51e54-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="51e54-109">Zápis knihovny</span><span class="sxs-lookup"><span data-stu-id="51e54-109">Writing the library</span></span>

1. <span data-ttu-id="51e54-110">V sadě Visual Studio, zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="51e54-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="51e54-111">V **nový projekt** dialogového okna, rozbalte **Visual C#** uzlu a zvolte **.NET Standard** uzel a klikněte na tlačítko **knihovna tříd (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="51e54-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="51e54-112">Název projektu "Library" a "Golden" řešení.</span><span class="sxs-lookup"><span data-stu-id="51e54-112">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="51e54-113">Ponechte **vytvořit adresář pro řešení** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="51e54-113">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="51e54-114">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="51e54-114">Click **OK**.</span></span>

3. <span data-ttu-id="51e54-115">V Průzkumníku řešení otevřete kontextovou nabídku **závislosti** uzlu a zvolte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="51e54-115">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="51e54-116">Zvolte možnost "nuget.org" jako **zdroj balíčku**a zvolte **Procházet** kartu. Vyhledat **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="51e54-116">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="51e54-117">Klikněte na tlačítko **nainstalovat**a přijměte licenční smlouvu.</span><span class="sxs-lookup"><span data-stu-id="51e54-117">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="51e54-118">Balíček by se měl zobrazit v části **závislosti/NuGet** a se automaticky obnoví.</span><span class="sxs-lookup"><span data-stu-id="51e54-118">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="51e54-119">Přejmenovat `Class1.cs` soubor `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="51e54-119">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="51e54-120">Přijměte přejmenování třídy.</span><span class="sxs-lookup"><span data-stu-id="51e54-120">Accept the rename of the class.</span></span> <span data-ttu-id="51e54-121">Přidejte metodu: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="51e54-121">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="51e54-122">Na **sestavení** nabídce zvolte **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="51e54-122">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="51e54-123">Má řešení sestavit bez chyb.</span><span class="sxs-lookup"><span data-stu-id="51e54-123">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="51e54-124">Zápis testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="51e54-124">Writing the test project</span></span>

1. <span data-ttu-id="51e54-125">V Průzkumníku řešení otevřete kontextovou nabídku **řešení** uzlu a zvolte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="51e54-125">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="51e54-126">V **nový projekt** dialogového okna, v části **Visual C# / .NET Core**, zvolte **projekt testu jednotek (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="51e54-126">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="51e54-127">Pojmenujte ji "TestLibrary" a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="51e54-127">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="51e54-128">V **TestLibrary** projektu, otevřete kontextovou nabídku **závislosti** uzlu a zvolte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="51e54-128">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="51e54-129">Klikněte na tlačítko **projekty**, zkontrolujte projekt knihovny a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="51e54-129">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="51e54-130">To přidá odkaz na knihovnu z testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="51e54-130">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="51e54-131">Přejmenovat `UnitTest1.cs` do souboru `LibraryTests.cs` a přijměte přejmenování třídy.</span><span class="sxs-lookup"><span data-stu-id="51e54-131">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="51e54-132">Přidat `using Library;` na začátek souboru a nahraďte `TestMethod1` metodu s následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="51e54-132">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="51e54-133">Teď by měl být možné sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="51e54-133">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="51e54-134">Na **testování** nabídce zvolte **Windows**, **Průzkumníka testů** zajistí okna Průzkumníka testů do pracovního prostoru.</span><span class="sxs-lookup"><span data-stu-id="51e54-134">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="51e54-135">Po několika sekundách `ThingGetsObjectValFromNumber` test by se měla zobrazit v Průzkumníku testů.</span><span class="sxs-lookup"><span data-stu-id="51e54-135">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="51e54-136">Zvolte **spustit všechny**.</span><span class="sxs-lookup"><span data-stu-id="51e54-136">Choose **Run All**.</span></span>
   
   <span data-ttu-id="51e54-137">Test by měl úspěšný.</span><span class="sxs-lookup"><span data-stu-id="51e54-137">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="51e54-138">Zápis aplikace konzoly</span><span class="sxs-lookup"><span data-stu-id="51e54-138">Writing the console app</span></span>

1. <span data-ttu-id="51e54-139">V Průzkumníku řešení otevřete kontextovou nabídku řešení a přidejte nový **Konzolová aplikace (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="51e54-139">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="51e54-140">Název "Aplikace".</span><span class="sxs-lookup"><span data-stu-id="51e54-140">Name it "App".</span></span>

2. <span data-ttu-id="51e54-141">V **aplikace** projektu, otevřete kontextovou nabídku **závislosti** uzlu a zvolte **přidat**, **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="51e54-141">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="51e54-142">V **správce odkazů** dialogové okno Kontrola **knihovny** pod **projekty**, **řešení** uzlu a pak klikněte na tlačítko **OK**</span><span class="sxs-lookup"><span data-stu-id="51e54-142">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="51e54-143">Otevřete místní nabídku pro **aplikace** uzlu a zvolte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="51e54-143">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="51e54-144">Tím se zajistí, že stisknutí F5 nebo CTRL + F5 se spustí aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="51e54-144">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="51e54-145">Otevřít `Program.cs` přidejte `using Library;` na začátek souboru a pak přidejte `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` k `Main` – metoda.</span><span class="sxs-lookup"><span data-stu-id="51e54-145">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="51e54-146">Nastavte zarážku po řádek, který jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="51e54-146">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="51e54-147">Stisknutím klávesy F5 spusťte aplikaci...</span><span class="sxs-lookup"><span data-stu-id="51e54-147">Press F5 to run the application..</span></span>

   <span data-ttu-id="51e54-148">Aplikace má sestavit bez chyb a by měl zarážce.</span><span class="sxs-lookup"><span data-stu-id="51e54-148">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="51e54-149">Musíte mít také možnost zkontrolovat, že aplikace výstupu "odpověď je 42.".</span><span class="sxs-lookup"><span data-stu-id="51e54-149">You should also be able to check that the application output "The answer is 42.".</span></span>
