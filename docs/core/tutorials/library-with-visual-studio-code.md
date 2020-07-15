---
title: Vytvoření .NET Standard knihovny tříd pomocí Visual Studio Code
description: Naučte se vytvářet .NET Standard knihovny tříd pomocí Visual Studio Code.
ms.date: 06/08/2020
ms.openlocfilehash: 714b5cf2125f1d296adc4a4dc7d1b6c9420417ed
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308881"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="5088f-103">Kurz: Vytvoření knihovny .NET Standard pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5088f-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="5088f-104">V tomto kurzu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="5088f-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="5088f-105">Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="5088f-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="5088f-106">*Knihovna tříd* definuje typy a metody, které jsou volány aplikací.</span><span class="sxs-lookup"><span data-stu-id="5088f-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="5088f-107">Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5088f-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="5088f-108">Po dokončení knihovny tříd ji můžete distribuovat jako součást třetí strany nebo jako součást balíčku s jednou nebo více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="5088f-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5088f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5088f-109">Prerequisites</span></span>

1. <span data-ttu-id="5088f-110">[Visual Studio Code](https://code.visualstudio.com/) s nainstalovaným [rozšířením C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="5088f-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="5088f-111">Informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="5088f-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="5088f-112">[.NET Core 3,1 SDK nebo novější](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="5088f-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="5088f-113">Vytvoření řešení</span><span class="sxs-lookup"><span data-stu-id="5088f-113">Create a solution</span></span>

<span data-ttu-id="5088f-114">Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do.</span><span class="sxs-lookup"><span data-stu-id="5088f-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="5088f-115">Řešení slouží jako kontejner pro jeden nebo více projektů.</span><span class="sxs-lookup"><span data-stu-id="5088f-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="5088f-116">Do stejného řešení přidáte další související projekty.</span><span class="sxs-lookup"><span data-stu-id="5088f-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="5088f-117">Spusťte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="5088f-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="5088f-118">V hlavní nabídce vyberte **soubor**  >  **Otevřít složku** (**otevřít...** v MacOS).</span><span class="sxs-lookup"><span data-stu-id="5088f-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="5088f-119">V dialogovém okně **Otevřít složku** vytvořte složku *ClassLibraryProjects* a klikněte na **Vybrat složku** (**otevřít** v MacOS).</span><span class="sxs-lookup"><span data-stu-id="5088f-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="5088f-120">Kliknutím na **Terminal** **Zobrazit**  >  **terminál** v hlavní nabídce otevřete terminál v Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="5088f-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="5088f-121">**Terminál** se otevře s příkazovým řádkem ve složce *ClassLibraryProjects* .</span><span class="sxs-lookup"><span data-stu-id="5088f-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="5088f-122">V **terminálu**zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5088f-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="5088f-123">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="5088f-124">Vytvořit projekt knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="5088f-124">Create a class library project</span></span>

<span data-ttu-id="5088f-125">Přidejte do řešení nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".</span><span class="sxs-lookup"><span data-stu-id="5088f-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="5088f-126">V terminálu spusťte následující příkaz, který vytvoří projekt knihovny:</span><span class="sxs-lookup"><span data-stu-id="5088f-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="5088f-127">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="5088f-128">Spusťte následující příkaz pro přidání projektu knihovny do řešení:</span><span class="sxs-lookup"><span data-stu-id="5088f-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="5088f-129">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="5088f-130">Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5088f-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="5088f-131">V **Průzkumníku**otevřete *StringLibrary/StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="5088f-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="5088f-132">`TargetFramework`Element ukazuje, že cíle projektu .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="5088f-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="5088f-133">Otevřete *Class1.cs* a nahraďte kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5088f-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="5088f-134">Knihovna tříd, `UtilityLibraries.StringLibrary` , obsahuje metodu s názvem `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="5088f-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="5088f-135">Tato metoda vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="5088f-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="5088f-136">Standard Unicode rozlišuje velká písmena od malých písmen.</span><span class="sxs-lookup"><span data-stu-id="5088f-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="5088f-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda vrátí, `true` zda je znak velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="5088f-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="5088f-138">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="5088f-138">Save the file.</span></span>

1. <span data-ttu-id="5088f-139">Spuštěním následujícího příkazu Sestavte řešení a ověřte, zda se projekt zkompiluje bez chyby.</span><span class="sxs-lookup"><span data-stu-id="5088f-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="5088f-140">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-140">The terminal output looks like the following example:</span></span>

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

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="5088f-141">Přidání konzolové aplikace do řešení</span><span class="sxs-lookup"><span data-stu-id="5088f-141">Add a console app to the solution</span></span>

<span data-ttu-id="5088f-142">Přidejte konzolovou aplikaci, která používá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="5088f-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="5088f-143">Aplikace vyzve uživatele, aby zadal řetězec a nahlásil, jestli řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="5088f-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="5088f-144">V terminálu spusťte následující příkaz, který vytvoří projekt konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="5088f-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="5088f-145">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="5088f-146">Spuštěním následujícího příkazu přidejte projekt konzolové aplikace do řešení:</span><span class="sxs-lookup"><span data-stu-id="5088f-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="5088f-147">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="5088f-148">Otevřete seznam *prezentujes/program. cs* a nahraďte celý kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5088f-148">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="5088f-149">Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="5088f-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="5088f-150">Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.</span><span class="sxs-lookup"><span data-stu-id="5088f-150">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5088f-151">Program vyzve uživatele k zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="5088f-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5088f-152">Označuje, zda řetězec začíná velkým znakem.</span><span class="sxs-lookup"><span data-stu-id="5088f-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5088f-153">Pokud uživatel stiskne klávesu <kbd>ENTER</kbd> bez zadání řetězce, aplikace skončí a okno konzoly se zavře.</span><span class="sxs-lookup"><span data-stu-id="5088f-153">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="5088f-154">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="5088f-154">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="5088f-155">Přidat odkaz na projekt</span><span class="sxs-lookup"><span data-stu-id="5088f-155">Add a project reference</span></span>

<span data-ttu-id="5088f-156">Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="5088f-156">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="5088f-157">Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="5088f-157">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="5088f-158">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5088f-158">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="5088f-159">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-159">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="5088f-160">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="5088f-160">Run the app</span></span>

1. <span data-ttu-id="5088f-161">V terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5088f-161">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="5088f-162">Vyzkoušejte program zadáním řetězců a stisknutím klávesy <kbd>ENTER</kbd>a stisknutím klávesy <kbd>ENTER</kbd> ukončete.</span><span class="sxs-lookup"><span data-stu-id="5088f-162">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="5088f-163">Výstup terminálu vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5088f-163">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="5088f-164">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5088f-164">Additional resources</span></span>

* [<span data-ttu-id="5088f-165">Vývoj knihoven pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="5088f-165">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="5088f-166">[.NET Standard verze a podporované platformy](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="5088f-166">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5088f-167">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5088f-167">Next steps</span></span>

<span data-ttu-id="5088f-168">V tomto kurzu jste vytvořili řešení, přidali projekt knihovny a Přidali jste projekt konzolové aplikace, který používá knihovnu.</span><span class="sxs-lookup"><span data-stu-id="5088f-168">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="5088f-169">V dalším kurzu přidáte do řešení projekt testování částí.</span><span class="sxs-lookup"><span data-stu-id="5088f-169">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5088f-170">Testování knihovny .NET Standard pomocí .NET Core s využitím Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5088f-170">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
