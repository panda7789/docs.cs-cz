---
title: Použití knihovny .NET Standard v sadě Visual Studio 2017
description: Zjistěte, jak volat členy v knihovně tříd pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52ec46c23bb928b49f034270ed1d510d1acf992e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518162"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a>Použití knihovny .NET Standard v sadě Visual Studio 2017

Po vytvoření knihovny tříd .NET Standard podle postupu v [vytváření knihovny tříd jazyka C# pomocí .NET Core v sadě Visual Studio 2017](./library-with-visual-studio.md) nebo [vytváření knihovny tříd jazyka Visual Basic pomocí .NET Core v sadě Visual Studio 2017 ](vb-library-with-visual-studio.md), otestovat ji v [testování knihovny tříd pomocí platformy .NET Core v sadě Visual Studio 2017](testing-library-with-visual-studio.md), a integrované verzi knihovny, dalším krokem je zpřístupnit volající. Můžete to provést dvěma způsoby:

* Pokud knihovny použije jediného řešení (například, pokud je součástí jedné velké aplikace), můžete ho zahrnout jako projekt ve vašem řešení.

* Pokud knihovny bude obecně dostupná, můžete ho distribuovat jako balíček NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Včetně knihovnu jako projekt v řešení

Stejně jako jste zahrnuli testy jednotek ve stejném řešení jako knihovnu tříd, může obsahovat aplikaci jako součást tohoto řešení. Například můžete použít knihovnu tříd v konzolové aplikaci, která se zobrazí výzva k zadání řetězec a sestavy, zda je jeho prvního znaku velké písmeno:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Otevřít `ClassLibraryProjects` řešení, které jste vytvořili v [vytváření knihovny tříd jazyka C# pomocí .NET Core v sadě Visual Studio 2017](./library-with-visual-studio.md) tématu. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z kontextové nabídky.

1. V **přidat nový projekt** dialogového okna, rozbalte **Visual C#** uzel a vyberte **.NET Core** uzel, za nímž následuje **Konzolová aplikace (.NET Core)** Šablona projektu. V **název** textového pole zadejte "Prezentaci" a vyberte **OK** tlačítko.

   ![Přidání dialogového okna Nový projekt](./media/consuming-library-with-visual-studio/addnewproject.png)

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prezentaci** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce. 

   ![Místní nabídka prezentace](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Na začátku projektu nemá přístup do knihovny tříd. Aby mohla volat metody v knihovně tříd, vytvořit odkaz na knihovnu tříd. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz**.

   ![Prezentace závislosti kontextové nabídky](./media/consuming-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogového okna, vyberte **StringLibrary**, váš projekt knihovny tříd a vyberte **OK** tlačítko.

   ![Správce odkazů](./media/consuming-library-with-visual-studio/referencemanager.png)

1. V okně kódu *Program.cs* souboru, nahraďte kód následujícím kódem:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Tento kód použije `row` proměnné udržovat přehled o počtu řádků dat zapsaných do okna konzoly. Pokaždé, když je větší než nebo roven 25, kód vymaže okno konzoly a zobrazí zprávu pro uživatele.

   Program se zobrazí výzva k zadání řetězec. Znamená to, jestli řetězec začíná velkým písmenem. Pokud uživatel stiskne klávesu Enter bez zadání řetězce, se aplikace ukončí a zavře okno konzoly.

1. V případě potřeby změňte nástrojů ke kompilaci **ladění** vydání `ShowCase` projektu. Zkompilujte a spusťte program výběrem na zelenou šipku na **prezentaci** tlačítko.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Otevřít `ClassLibraryProjects` řešení, které jste vytvořili v [vytváření třídy knihovny jazyka Visual Basic a .NET Core v sadě Visual Studio 2017](vb-library-with-visual-studio.md) tématu. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z kontextové nabídky.

1. V **přidat nový projekt** dialogového okna, rozbalte **jazyka Visual Basic** uzel a vyberte **.NET Core** uzel, za nímž následuje **Konzolová aplikace (.NET Core)** šablony projektu. V **název** textového pole zadejte "Prezentaci" a vyberte **OK** tlačítko.

   ![Přidání dialogového okna Nový projekt](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prezentaci** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce. 

   ![Místní nabídka prezentace](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Na začátku projektu nemá přístup do knihovny tříd. Aby mohla volat metody v knihovně tříd, vytvořit odkaz na knihovnu tříd. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz**.

   ![Prezentace závislosti kontextové nabídky](./media/consuming-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogového okna, vyberte **StringLibrary**, váš projekt knihovny tříd a vyberte **OK** tlačítko.

   ![Správce odkazů](./media/consuming-library-with-visual-studio/referencemanager.png)

1. V okně kódu *soubor Program.vb* souboru, nahraďte kód následujícím kódem:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Tento kód použije `row` proměnné udržovat přehled o počtu řádků dat zapsaných do okna konzoly. Pokaždé, když je větší než nebo roven 25, kód vymaže okno konzoly a zobrazí zprávu pro uživatele.

   Program se zobrazí výzva k zadání řetězec. Znamená to, jestli řetězec začíná velkým písmenem. Pokud uživatel stiskne klávesu Enter bez zadání řetězce, se aplikace ukončí a zavře okno konzoly.

1. V případě potřeby změňte nástrojů ke kompilaci **ladění** vydání `ShowCase` projektu. Zkompilujte a spusťte program výběrem na zelenou šipku na **prezentaci** tlačítko.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
---

Můžete ladit a publikovat aplikaci, která používá tuto knihovnu podle postupu v [ladění aplikace Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md) a [publikování aplikace Hello World pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribuce knihoven v balíčku NuGet

Můžete provést knihovnu tříd široce dostupné a publikujte ho jako balíček NuGet. Visual Studio nepodporuje vytváření balíčků NuGet. Chcete-li jeden vytvořit, je použít [ `dotnet` nástroj příkazového řádku](../../core/tools/dotnet.md):

1. Otevřete okno konzoly. Například v **zeptejte se mě, nic** textové pole na hlavním panelu Windows, zadejte `Command Prompt` (nebo `cmd` zkráceně) a otevřete okno konzoly tak, že vyberete **příkazového řádku** desktopové aplikace nebo stisknutím klávesy Enter, pokud je vybrána ve výsledcích hledání.

1. Přejděte do adresáře projektu své knihovny. Pokud jste změnili konfiguraci umístění typické souboru, se *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* adresáře. Adresář obsahuje váš zdrojový kód a soubor projektu *StringLibrary.csproj*.

1. Příkaz `dotnet pack --no-build`. `dotnet` Nástroj vygeneruje balíček se *.nupkg* rozšíření.

   > [!TIP]
   > Pokud adresář, který obsahuje *dotnet.exe* není v CESTĚ, můžete najít tak, že zadáte jeho umístění `where dotnet.exe` v okně konzoly.

Další informace o vytváření balíčků NuGet, naleznete v tématu [vytvoření balíčku NuGet pomocí nástrojů pro různé platformy](../../core/deploying/creating-nuget-packages.md).
