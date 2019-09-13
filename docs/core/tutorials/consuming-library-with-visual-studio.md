---
title: Využití knihovny .NET Standard v sadě Visual Studio 2017
description: Sestavte aplikaci .NET Core, která volá členy jiné knihovny tříd pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: ff60bb5de403970f432e938cba81ca4e99476e8a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925976"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a>Využití knihovny .NET Standard v sadě Visual Studio 2017

Po vytvoření knihovny tříd .NET Standard pomocí postupu v části [Vytvoření knihovny C# tříd pomocí .NET Core v aplikaci Visual Studio 2017](./library-with-visual-studio.md) nebo [Vytvoření knihovny tříd Visual Basic pomocí .NET core v aplikaci Visual Studio 2017](vb-library-with-visual-studio.md)je testováno v [ Testování knihovny tříd pomocí .NET Core v aplikaci Visual Studio 2017](testing-library-with-visual-studio.md)a sestavení vydané verze knihovny, je dalším krokem zpřístupnění volajícím. Můžete to provést dvěma způsoby:

* Pokud bude knihovna použita v jednom řešení (například v případě, že se jedná o komponentu v jedné velké aplikaci), můžete ji zahrnout jako projekt ve vašem řešení.

* Pokud bude knihovna všeobecně dostupná, můžete ji distribuovat jako balíček NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Zahrnutí knihovny jako projektu do řešení

Stejně jako v případě, že jste zahrnuli jednotkové testy do stejného řešení jako vaše knihovna tříd, můžete zahrnout aplikaci jako součást tohoto řešení. Knihovnu tříd můžete například použít v konzolové aplikaci, která vyzve uživatele k zadání řetězce a oznamuje, zda je jeho první znak velkými písmeny:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Otevřete řešení, které jste vytvořili v tématu [sestavení C# knihovny tříd pomocí .NET Core v aplikaci Visual Studio 2017.](./library-with-visual-studio.md) `ClassLibraryProjects` V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **ClassLibraryProjects** a v místní nabídce vyberte **Přidat** > **Nový projekt** .

1. V dialogovém okně **Přidat nový projekt** rozbalte uzel  **C# vizuál** a vyberte uzel **.NET Core** následovaný šablonou projektu **Konzolová aplikace (.NET Core)** . Do textového pole **název** zadejte "prezentuje" a klikněte na tlačítko **OK** .

   ![Dialogová okna pro přidání nového projektu sady Visual Studio –C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu –C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Zpočátku váš projekt nemá přístup k vaší knihovně tříd. Chcete-li, aby mohla volat metody ve vaší knihovně tříd, vytvořte odkaz na knihovnu tříd. V **Průzkumník řešení**klikněte pravým tlačítkem myši `ShowCase` na uzel **závislosti** projektu a vyberte možnost **Přidat odkaz**.

   ![Místní nabídka pro přidání odkazu na projekt sady Visual Studio –C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a klikněte na tlačítko **OK** .

   ![Dialogové okno Správa odkazů v aplikaci Visual Studio –C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. V okně kódu pro soubor *program.cs* nahraďte celý kód následujícím kódem:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly. Vždy, když je číslo větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.

   Program vyzve uživatele k zadání řetězce. Označuje, zda řetězec začíná velkým znakem. Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.

1. V případě potřeby změňte panel nástrojů pro zkompilování **ladicí** verze `ShowCase` projektu. Zkompilujte a spusťte program tak, že vyberete zelenou šipku na **tlačítku pro** sestavování.

   ![Panel nástrojů projekt sady Visual Studio zobrazující tlačítko ladění –C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Otevřete řešení, které jste vytvořili v tématu [sestavení knihovny tříd pomocí Visual Basic a .NET Core v aplikaci Visual Studio 2017.](vb-library-with-visual-studio.md) `ClassLibraryProjects` V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **ClassLibraryProjects** a v místní nabídce vyberte **Přidat** > **Nový projekt** .

1. V dialogovém okně **Přidat nový projekt** rozbalte uzel **Visual Basic** a vyberte uzel **.NET Core** následovaný šablonou projektu **Konzolová aplikace (.NET Core)** . Do textového pole **název** zadejte "prezentuje" a klikněte na tlačítko **OK** .

   ![Dialogová okna pro přidání nového projektu sady Visual Studio – Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** . 

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu-Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Zpočátku váš projekt nemá přístup k vaší knihovně tříd. Chcete-li, aby mohla volat metody ve vaší knihovně tříd, vytvořte odkaz na knihovnu tříd. V **Průzkumník řešení**klikněte pravým tlačítkem myši `ShowCase` na uzel **závislosti** projektu a vyberte možnost **Přidat odkaz**.

   ![Místní nabídka pro přidání odkazu na projekt sady Visual Studio – Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a klikněte na tlačítko **OK** .

   ![Dialogové okno Správa odkazů v aplikaci Visual Studio – Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. V okně kód pro soubor *program. vb* nahraďte celý kód následujícím kódem:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kód používá `row` proměnnou k udržování počtu řádků dat zapsaných do okna konzoly. Vždy, když je číslo větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.

   Program vyzve uživatele k zadání řetězce. Označuje, zda řetězec začíná velkým znakem. Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.

1. V případě potřeby změňte panel nástrojů pro zkompilování **ladicí** verze `ShowCase` projektu. Zkompilujte a spusťte program tak, že vyberete zelenou šipku na **tlačítku pro** sestavování.

   ![Ladění na panelu nástrojů – Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

Můžete ladit a publikovat aplikaci, která používá tuto knihovnu, podle kroků v části [ladění aplikace Hello World pomocí sady Visual studio 2017](debugging-with-visual-studio.md) a [publikování Hello World aplikace pomocí sady Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribuce knihovny do balíčku NuGet

Vaše knihovna tříd může být široce dostupná, když ji publikujete jako balíček NuGet. Visual Studio nepodporuje vytváření balíčků NuGet. Pokud ho chcete vytvořit, použijte [ `dotnet` nástroj příkazového řádku](../tools/dotnet.md):

1. Otevřete okno konzoly. Například v textovém poli **Zobrazit vše** v hlavním panelu systému Windows zadejte `Command Prompt` (nebo `cmd` pro krátkou hodnotu) a otevřete okno konzoly, a to tak, že vyberete aplikaci pro stolní počítače nebo stisknete klávesu ENTER, pokud je vybraná ve vyhledávání. důsledk.

1. Přejděte do adresáře projektu knihovny. Pokud jste nenakonfigurovali typické umístění souboru, je to v adresáři *Documents\Visual Studio 2017 \ Projects\ClassLibraryProjects\StringLibrary* . Adresář obsahuje zdrojový kód a soubor projektu *StringLibrary. csproj*.

1. Vydejte příkaz `dotnet pack --no-build`. Nástroj vygeneruje balíček s příponou *. nupkg.* `dotnet`

   > [!TIP]
   > Pokud adresář, který obsahuje *dotnet. exe* , není ve vaší cestě, můžete najít jeho umístění zadáním `where dotnet.exe` v okně konzoly.

Další informace o vytváření balíčků NuGet najdete v tématu [Postup vytvoření balíčku NuGet s nástroji pro různé platformy](../deploying/creating-nuget-packages.md).
