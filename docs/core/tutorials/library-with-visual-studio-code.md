---
title: Vytvoření knihovny tříd .NET Standard v Visual Studio Code
description: Naučte se vytvářet .NET Standard knihovny tříd pomocí Visual Studio Code.
ms.date: 05/29/2020
ms.openlocfilehash: 5720ac374d50ef27a07d463e57af1bd95a352d83
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446949"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a><span data-ttu-id="ccfd6-103">Kurz: Vytvoření knihovny .NET Standard v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ccfd6-103">Tutorial: Create a .NET Standard library in Visual Studio Code</span></span>

<span data-ttu-id="ccfd6-104">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="ccfd6-105">Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="ccfd6-106">Po dokončení knihovny tříd se můžete rozhodnout, zda je chcete distribuovat jako balíček NuGet, nebo zahrnout jako součást sady s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-106">When you finish your class library, you can decide whether you want to distribute it as a NuGet package or include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="ccfd6-107">Seznam verzí .NET Standard a platforem, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="ccfd6-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="ccfd6-108">V tomto kurzu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="ccfd6-109">Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ccfd6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccfd6-110">Prerequisites</span></span>

1. <span data-ttu-id="ccfd6-111">[Visual Studio Code](https://code.visualstudio.com/) s nainstalovaným [rozšířením C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="ccfd6-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="ccfd6-112">Informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="ccfd6-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="ccfd6-113">[.NET Core 3,1 SDK nebo novější](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="ccfd6-113">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="ccfd6-114">Vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="ccfd6-114">Create a solution</span></span>

<span data-ttu-id="ccfd6-115">Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="ccfd6-116">Řešení slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="ccfd6-117">Do stejného řešení přidáte další související projekty.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="ccfd6-118">Otevřete Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-118">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="ccfd6-119">V hlavní nabídce vyberte **soubor**  >  **Otevřít složku**otevřít / **...** , vytvořte složku *ClassLibraryProjects* a klikněte na **Vybrat složku** / **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-119">Select **File** > **Open Folder**/**Open...** from the main menu, create a *ClassLibraryProjects* folder, and click **Select Folder**/**Open**.</span></span>

1. <span data-ttu-id="ccfd6-120">Kliknutím na **Terminal** **Zobrazit**  >  **terminál** v hlavní nabídce otevřete terminál v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="ccfd6-121">**Terminál** se otevře s příkazovým řádkem ve složce *ClassLibraryProjects* .</span><span class="sxs-lookup"><span data-stu-id="ccfd6-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="ccfd6-122">V **terminálu**zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="ccfd6-123">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="ccfd6-124">Vytvořit projekt knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="ccfd6-124">Create a class library project</span></span>

<span data-ttu-id="ccfd6-125">Přidejte do řešení nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="ccfd6-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="ccfd6-126">V terminálu spusťte následující příkaz, který vytvoří projekt knihovny:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="ccfd6-127">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="ccfd6-128">Spusťte následující příkaz pro přidání projektu knihovny do řešení:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="ccfd6-129">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="ccfd6-130">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="ccfd6-131">V **Průzkumníku**otevřete *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="ccfd6-132">`TargetFramework`Element ukazuje, že cíle projektu .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="ccfd6-133">Otevřete *Class1.cs* a nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="ccfd6-134">Knihovna tříd, `UtilityLibraries.StringLibrary` , obsahuje metodu s názvem `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="ccfd6-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="ccfd6-135">Tato metoda vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="ccfd6-136">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="ccfd6-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda vrátí, `true` zda je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="ccfd6-138">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-138">Save the file.</span></span>

1. <span data-ttu-id="ccfd6-139">Spuštěním následujícího příkazu Sestavte řešení a ověřte, zda se projekt zkompiluje bez chyby.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="ccfd6-140">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-140">The terminal output looks like the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="ccfd6-141">Přidání konzolové aplikace do řešení</span><span class="sxs-lookup"><span data-stu-id="ccfd6-141">Add a console app to the solution</span></span>

<span data-ttu-id="ccfd6-142">Přidejte konzolovou aplikaci, která používá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="ccfd6-143">Aplikace vyzve uživatele, aby zadal řetězec a nahlásil, jestli řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="ccfd6-144">V terminálu spusťte následující příkaz, který vytvoří projekt konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="ccfd6-145">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="ccfd6-146">Spuštěním následujícího příkazu přidejte projekt konzolové aplikace do řešení:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="ccfd6-147">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="ccfd6-148">Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-148">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="ccfd6-149">Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-149">To allow it to call methods in the class library, create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="ccfd6-150">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-150">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. <span data-ttu-id="ccfd6-151">Otevřete seznam *prezentujes/program. cs* a nahraďte celý kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-151">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="ccfd6-152">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-152">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="ccfd6-153">Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-153">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="ccfd6-154">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-154">The program prompts the user to enter a string.</span></span> <span data-ttu-id="ccfd6-155">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-155">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="ccfd6-156">Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-156">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="ccfd6-157">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-157">Save your changes.</span></span>

1. <span data-ttu-id="ccfd6-158">Spusťte program.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-158">Run the program.</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="ccfd6-159">Vyzkoušejte program zadáním řetězců a stisknutím klávesy <kbd>ENTER</kbd>a stisknutím klávesy <kbd>ENTER</kbd> ukončete.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-159">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="ccfd6-160">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccfd6-160">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="ccfd6-161">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ccfd6-161">Additional resources</span></span>

* [<span data-ttu-id="ccfd6-162">Vývoj knihoven pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="ccfd6-162">Develop libraries with the .NET Core CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="ccfd6-163">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ccfd6-163">Next steps</span></span>

<span data-ttu-id="ccfd6-164">V tomto kurzu jste vytvořili řešení, přidali projekt knihovny a Přidali jste projekt konzolové aplikace, který používá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-164">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="ccfd6-165">V dalším kurzu přidáte do řešení projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="ccfd6-165">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ccfd6-166">Testování knihovny .NET Standard pomocí .NET Core v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ccfd6-166">Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
