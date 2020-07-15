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
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a>Kurz: Vytvoření knihovny .NET Standard pomocí Visual Studio Code

V tomto kurzu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců. Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem <xref:System.String> třídy.

*Knihovna tříd* definuje typy a metody, které jsou volány aplikací. Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard. Po dokončení knihovny tříd ji můžete distribuovat jako součást třetí strany nebo jako součást balíčku s jednou nebo více aplikacemi.

## <a name="prerequisites"></a>Požadavky

1. [Visual Studio Code](https://code.visualstudio.com/) s nainstalovaným [rozšířením C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) . Informace o tom, jak nainstalovat rozšíření na Visual Studio Code, najdete v tématu [rozšíření vs Code Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [.NET Core 3,1 SDK nebo novější](https://dotnet.microsoft.com/download)

## <a name="create-a-solution"></a>Vytvoření řešení

Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do. Řešení slouží jako kontejner pro jeden nebo více projektů. Do stejného řešení přidáte další související projekty.

1. Spusťte Visual Studio Code.

1. V hlavní nabídce vyberte **soubor**  >  **Otevřít složku** (**otevřít...** v MacOS).

1. V dialogovém okně **Otevřít složku** vytvořte složku *ClassLibraryProjects* a klikněte na **Vybrat složku** (**otevřít** v MacOS).

1. Kliknutím na **Terminal** **Zobrazit**  >  **terminál** v hlavní nabídce otevřete terminál v Visual Studio Code.

   **Terminál** se otevře s příkazovým řádkem ve složce *ClassLibraryProjects* .

1. V **terminálu**zadejte následující příkaz:

   ```dotnetcli
   dotnet new sln
   ```

   Výstup terminálu vypadá jako v následujícím příkladu:

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a>Vytvořit projekt knihovny tříd

Přidejte do řešení nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".

1. V terminálu spusťte následující příkaz, který vytvoří projekt knihovny:

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   Výstup terminálu vypadá jako v následujícím příkladu:

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. Spusťte následující příkaz pro přidání projektu knihovny do řešení:

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   Výstup terminálu vypadá jako v následujícím příkladu:

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard. V **Průzkumníku**otevřete *StringLibrary/StringLibrary. csproj*.

   `TargetFramework`Element ukazuje, že cíle projektu .NET Standard 2,0.

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. Otevřete *Class1.cs* a nahraďte kód následujícím kódem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   Knihovna tříd, `UtilityLibraries.StringLibrary` , obsahuje metodu s názvem `StartsWithUpper` . Tato metoda vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem. Standard Unicode rozlišuje velká písmena od malých písmen. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda vrátí, `true` zda je znak velkými písmeny.

1. Uložte soubor.

1. Spuštěním následujícího příkazu Sestavte řešení a ověřte, zda se projekt zkompiluje bez chyby.

   ```dotnetcli
   dotnet build
   ```

   Výstup terminálu vypadá jako v následujícím příkladu:

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

## <a name="add-a-console-app-to-the-solution"></a>Přidání konzolové aplikace do řešení

Přidejte konzolovou aplikaci, která používá knihovnu tříd. Aplikace vyzve uživatele, aby zadal řetězec a nahlásil, jestli řetězec začíná velkým znakem.

1. V terminálu spusťte následující příkaz, který vytvoří projekt konzolové aplikace:

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   Výstup terminálu vypadá jako v následujícím příkladu:

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. Spuštěním následujícího příkazu přidejte projekt konzolové aplikace do řešení:

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   Výstup terminálu vypadá jako v následujícím příkladu:

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. Otevřete seznam *prezentujes/program. cs* a nahraďte celý kód následujícím kódem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly. Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.

   Program vyzve uživatele k zadání řetězce. Označuje, zda řetězec začíná velkým znakem. Pokud uživatel stiskne klávesu <kbd>ENTER</kbd> bez zadání řetězce, aplikace skončí a okno konzoly se zavře.

1. Uložte provedené změny.

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Zpočátku má nový projekt konzolové aplikace přístup ke knihovně tříd. Chcete-li, aby mohla volat metody v knihovně tříd, vytvořte odkaz na projekt knihovny tříd.

1. Spusťte následující příkaz:

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   Výstup terminálu vypadá jako v následujícím příkladu:

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a>Spuštění aplikace

1. V terminálu spusťte následující příkaz:

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. Vyzkoušejte program zadáním řetězců a stisknutím klávesy <kbd>ENTER</kbd>a stisknutím klávesy <kbd>ENTER</kbd> ukončete.

   Výstup terminálu vypadá jako v následujícím příkladu:

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a>Další zdroje

* [Vývoj knihoven pomocí .NET Core CLI](libraries.md)
* [.NET Standard verze a podporované platformy](../../standard/net-standard.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili řešení, přidali projekt knihovny a Přidali jste projekt konzolové aplikace, který používá knihovnu. V dalším kurzu přidáte do řešení projekt testování částí.

> [!div class="nextstepaction"]
> [Testování knihovny .NET Standard pomocí .NET Core s využitím Visual Studio Code](testing-library-with-visual-studio-code.md)
