---
title: Použití rozhraní .NET standardní knihovny v Visual Studio 2017
description: Zjistěte, jak volat členy v knihovny tříd s Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1e71001ee8595741119293304190fd9ef4251148
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827310"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a>Použití rozhraní .NET standardní knihovny v Visual Studio 2017

Po vytvoření knihovny tříd rozhraní .NET standardní podle kroků v [vytvoření knihovny tříd jazyka C# s .NET Core ve Visual Studio 2017](./library-with-visual-studio.md) nebo [vytvoření knihovny tříd jazyka Visual Basic s .NET Core v Visual Studio 2017 ](vb-library-with-visual-studio.md), otestovat ji v [testování knihovny tříd s .NET Core ve Visual Studio 2017](testing-library-with-visual-studio.md), a vytvořili verzi knihovny, je dalším krokem a zpřístupněte ji volající. Můžete provést dvěma způsoby:

* Pokud knihovny použije jedno řešení (například pokud je součástí jedné velké aplikace), můžete ho jako projekt zahrnout ve vašem řešení.

* Pokud knihovny bude obvykle přístupné, můžete ho distribuovat jako balíčku NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Včetně knihovny jako na projekt v řešení

Stejně jako jste zahrnuli testy jednotek ve stejném řešení jako knihovny tříd, můžete zahrnout aplikace v rámci tohoto řešení. Například můžete použít knihovny tříd v konzolovou aplikaci, která zobrazí výzvu k zadání řetězec a sestavy, zda jeho první znak je velká písmena:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v [vytvoření knihovny tříd jazyka C# s .NET Core ve Visual Studio 2017](./library-with-visual-studio.md) tématu. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z v místní nabídce.

1. V **přidat nový projekt** dialogové okno, rozbalte **Visual C#** uzel a vyberte možnost **.NET Core** následuje uzlu **konzolové aplikace (.NET Core)** Šablona projektu. V **název** textového pole zadejte "Představením" a vyberte **OK** tlačítko.

   ![Přidat dialogové okno Nový projekt](./media/consuming-library-with-visual-studio/addnewproject.png)

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **představením** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce. 

   ![Představením kontextové nabídky](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Na začátku projektu nemá přístup do knihovny tříd. Tak, aby ji volat metody ve knihovny tříd, vytvořit odkaz na knihovnu tříd. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz na**.

   ![Představením závislosti kontextové nabídky](./media/consuming-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogovém okně, vyberte **StringLibrary**, vašeho projektu knihovny tříd a vyberte **OK** tlačítko.

   ![Správce odkazů](./media/consuming-library-with-visual-studio/referencemanager.png)

1. V okně kód pro *Program.cs* souboru, všechny kódu nahraďte následujícím kódem:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kód používá `row` proměnná udržovat počet řádků dat zapsaných do okna konzoly. Vždy, když je větší než nebo roven 25, kód vymaže v okně konzoly a zobrazí zprávu pro uživatele.

   Program zobrazí výzvu k zadání řetězec. Označuje, zda text začíná velké písmeno. Pokud uživatel stiskne klávesu Enter bez zadávání řetězec, ukončí aplikaci a zavření okna konzoly.

1. V případě potřeby změňte panelu nástrojů zkompilovat **ladění** vydání `ShowCase` projektu. Zkompilování a spuštění programu výběrem zelenou šipku na **představením** tlačítko.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v [vytváření třídy knihovny jazyka Visual Basic a .NET Core ve Visual Studio 2017](vb-library-with-visual-studio.md) tématu. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **ClassLibraryProjects** řešení a vyberte **přidat** > **nový projekt** z v místní nabídce.

1. V **přidat nový projekt** dialogové okno, rozbalte **jazyka Visual Basic** uzel a vyberte možnost **.NET Core** následuje uzlu **konzolové aplikace (.NET Core)** šablona projektu. V **název** textového pole zadejte "Představením" a vyberte **OK** tlačítko.

   ![Přidat dialogové okno Nový projekt](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **představením** projektu a vyberte **nastavit jako spouštěný projekt** v místní nabídce. 

   ![Představením kontextové nabídky](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Na začátku projektu nemá přístup do knihovny tříd. Tak, aby ji volat metody ve knihovny tříd, vytvořit odkaz na knihovnu tříd. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `ShowCase` projektu **závislosti** uzel a vyberte možnost **přidat odkaz na**.

   ![Představením závislosti kontextové nabídky](./media/consuming-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogovém okně, vyberte **StringLibrary**, vašeho projektu knihovny tříd a vyberte **OK** tlačítko.

   ![Správce odkazů](./media/consuming-library-with-visual-studio/referencemanager.png)

1. V okně kód pro *soubor Program.vb* souboru, všechny kódu nahraďte následujícím kódem:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kód používá `row` proměnná udržovat počet řádků dat zapsaných do okna konzoly. Vždy, když je větší než nebo roven 25, kód vymaže v okně konzoly a zobrazí zprávu pro uživatele.

   Program zobrazí výzvu k zadání řetězec. Označuje, zda text začíná velké písmeno. Pokud uživatel stiskne klávesu Enter bez zadávání řetězec, ukončí aplikaci a zavření okna konzoly.

1. V případě potřeby změňte panelu nástrojů zkompilovat **ladění** vydání `ShowCase` projektu. Zkompilování a spuštění programu výběrem zelenou šipku na **představením** tlačítko.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
---

Můžete ladit a publikovat aplikace, která tuto knihovnu používá podle kroků v [ladění aplikace Hello World s Visual Studio 2017](debugging-with-visual-studio.md) a [publikování aplikace Hello World pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribuce knihoven v balíčku NuGet

Dobrá dostupnost knihovny tříd můžete nastavit tak, že publikujete ji jako balíček NuGet. Visual Studio nepodporuje vytváření balíčků NuGet. Chcete-li vytvořit, je použít [ `dotnet` nástroj příkazového řádku](../../core/tools/dotnet.md):

1. Otevřete okno konzoly. Například v **dotaz na nic** textové pole na hlavním panelu systému Windows, zadejte `Command Prompt` (nebo `cmd` pro zkrácení) a otevřete okno konzoly můžete buď **příkazového řádku** aplikace na ploše nebo pokud je vybrána ve výsledcích hledání z nich stiskněte Enter.

1. Přejděte do adresáře projektu své knihovny. Pokud jste změnili konfiguraci umístění typické souboru, je v *2017\Projects\ClassLibraryProjects\StringLibrary Documents\Visual Studio* adresáře. Adresář obsahuje zdrojový kód a soubor projektu *StringLibrary.csproj*.

1. Vydejte příkaz `dotnet pack --no-build`. `dotnet` Nástroj generuje balíček s *.nupkg* rozšíření.

   > [!TIP]
   > Pokud adresář, který obsahuje *dotnet.exe* není v CESTĚ, můžete najít její umístění zadáním `where dotnet.exe` v okně konzoly.

Další informace o vytváření balíčků NuGet najdete v tématu [vytvoření balíčku NuGet se mezi nástroje platformy](../../core/deploying/creating-nuget-packages.md).
