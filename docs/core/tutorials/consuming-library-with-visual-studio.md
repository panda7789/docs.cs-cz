---
title: Využití knihovny .NET Standard v sadě Visual Studio
description: Vytvořte aplikaci .NET Core, která volá členy jiné knihovny tříd pomocí Visual Studia 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920460"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Využití knihovny .NET Standard v sadě Visual Studio

Jakmile vytvoříte knihovnu tříd .NET Standard, otestujete ji a vytvoříte vyvolanou verzi knihovny, dalším krokem je zpřístupnit ji volajícím. To můžete provést dvěma způsoby:

- Pokud bude knihovna používána jediným řešením (například pokud se jedná o součást v jedné velké aplikaci), můžete ji zahrnout jako projekt do řešení.
- Pokud bude knihovna veřejně dostupná, můžete ji distribuovat jako balíček NuGet.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte do svého řešení konzolovou aplikaci, která odkazuje na projekt knihovny .NET Standard.
> - Vytvořte balíček NuGet, který obsahuje projekt knihovny .NET Standard.

## <a name="add-a-console-app-to-your-solution"></a>Přidání konzolové aplikace do vašeho řešení

Stejně jako jste zahrnuli testy částí do stejného řešení jako vaše knihovna tříd v [test .NET Standard knihovny v sadě Visual Studio](testing-library-with-visual-studio.md), můžete zahrnout aplikace jako součást tohoto řešení. Knihovnu tříd můžete například použít v konzolové aplikaci, která vyzve uživatele k zadání řetězce a oznámí, zda je jeho první znak velkými písmeny:

1. Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v článku [Sestavení a standardní knihovny .NET v sadě Visual Studio.](library-with-visual-studio.md)

1. Přidejte do řešení novou aplikaci konzoly .NET Core s názvem "ShowCase".

   1. Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte **konzolu** do vyhledávacího pole. V seznamu Jazyk zvolte **C#** nebo **Visual Basic** a pak ze seznamu Platforma zvolte **Všechny platformy.** Zvolte šablonu **Konzola aplikace (.NET Core)** a pak zvolte **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole Název **projektu** **ZobrazitPřípad.** Potom zvolte **Vytvořit**.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **ShowCase** a v místní nabídce vyberte nastavit **jako projekt spuštění.**

   ![Kontextová nabídka projektu sady Visual Studio pro nastavení spouštěcího projektu](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Zpočátku projekt nemá přístup ke knihovně tříd. Chcete-li povolit volání metod v knihovně tříd, vytvořte odkaz na knihovnu tříd. V **Průzkumníku řešení**klepněte pravým tlačítkem `ShowCase` myši na uzel **Závislosti** projektu a vyberte příkaz Přidat **odkaz**.

   ![Přidání kontextové nabídky odkazu v sadě Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a vyberte tlačítko **OK.**

   ![Dialogové okno Správce odkazů s vybranou knihovnou stringlibrary](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. V okně kódu pro soubor *Program.cs* nebo *Program.vb* nahraďte celý kód následujícím kódem:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kód používá `row` proměnnou k udržení počtu řádků dat zapsaných do okna konzoly. Vždy, když je větší než nebo rovno 25, kód vymaže okno konzoly a zobrazí zprávu uživateli.

   Program vyzve uživatele k zadání řetězce. Označuje, zda řetězec začíná znakem velkými písmeny. Pokud uživatel stiskne klávesu Enter bez zadání řetězce, aplikace se ukončí a okno konzoly se zavře.

1. V případě potřeby změňte panel nástrojů a `ShowCase` zkompilujte verzi **projektu ladění.** Zkompilujte a spusťte program výběrem zelené šipky na tlačítku **ShowCase.**

   ![Panel nástrojů projektu sady Visual Studio s tlačítkem Ladění](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Aplikaci, která používá tuto knihovnu, můžete ladit a publikovat podle kroků v části [Ladění aplikace C# nebo Visual Basic .NET Core Hello World pomocí sady Visual Studio](debugging-with-visual-studio.md) a publikování aplikace [.NET Core Hello World pomocí sady Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Vytvoření balíčku NuGet

Knihovnu tříd můžete zpřístupnit publikováním jako balíček NuGet. Visual Studio nepodporuje vytváření balíčků NuGet. Chcete-li jej vytvořit, musíte použít příkazy příkazu PŘÍKAZU .NET Core:

1. Otevřete okno konzoly.

   Zadejte například **příkazový řádek** do vyhledávacího pole na hlavním panelu systému Windows. Vyberte aplikaci **Command Prompt** desktop nebo stiskněte **Enter,** pokud je již ve výsledcích hledání vybraná.

1. Přejděte do adresáře projektu knihovny. Adresář obsahuje zdrojový kód a soubor projektu *StringLibrary.csproj* nebo *StringLibrary.vbproj*.

1. Spusťte příkaz [dotnet pack](../tools/dotnet-pack.md) a vygenerujte balíček s příponou *.nupkg:*

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Pokud adresář, který obsahuje *program dotnet.exe,* není ve vaší `where dotnet.exe` cestě, můžete jeho umístění najít zadáním do okna konzoly.

Další informace o vytváření balíčků NuGet naleznete v [tématu Jak vytvořit balíček NuGet s rozhraním .NET Core CLI](../deploying/creating-nuget-packages.md).
