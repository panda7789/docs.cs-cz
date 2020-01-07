---
title: Využití knihovny .NET Standard v sadě Visual Studio
description: Sestavte aplikaci .NET Core, která volá členy jiné knihovny tříd pomocí sady Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 9fcfb2e0c664186feda24c2a12daacb38769a68e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340015"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Využití knihovny .NET Standard v sadě Visual Studio

Jakmile vytvoříte knihovnu tříd .NET Standard, otestujete ji a sestavíte si prodejní verzi knihovny, je dalším krokem zpřístupnění volajícím. To můžete provést dvěma způsoby:

- Pokud bude knihovna použita v jednom řešení (například v případě, že se jedná o komponentu v jedné velké aplikaci), můžete ji zahrnout jako projekt ve vašem řešení.
- Pokud bude knihovna veřejně dostupná, můžete ji distribuovat jako balíček NuGet.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte konzolovou aplikaci do řešení, které odkazuje na projekt knihovny .NET Standard.
> - Vytvořte balíček NuGet, který obsahuje projekt knihovny .NET Standard.

## <a name="add-a-console-app-to-your-solution"></a>Přidání konzolové aplikace do řešení

Stejně jako v případě, že jste zahrnuli jednotkové testy do stejného řešení jako knihovnu tříd v rámci [testu knihovny .NET Standard v aplikaci Visual Studio](testing-library-with-visual-studio.md), můžete zahrnout aplikaci jako součást tohoto řešení. Knihovnu tříd můžete například použít v konzolové aplikaci, která vyzve uživatele k zadání řetězce a oznamuje, zda je jeho první znak velkými písmeny:

1. Otevřete řešení `ClassLibraryProjects`, které jste vytvořili v článku [Vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md) .

1. Do řešení přidejte novou konzolovou aplikaci .NET Core s názvem prezentující.

   1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Console** . V **C#** seznamu jazyků vyberte nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem. Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **prezentující** . Pak zvolte **vytvořit**.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **prezentace** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .

   ![Místní nabídka projektu sady Visual Studio pro nastavení spouštěného projektu](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Zpočátku váš projekt nemá přístup k vaší knihovně tříd. Chcete-li, aby mohla volat metody ve vaší knihovně tříd, vytvořte odkaz na knihovnu tříd. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu `ShowCase` a vyberte možnost **Přidat odkaz**.

   ![Přidat kontextovou nabídku odkazu v aplikaci Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** vyberte **StringLibrary**, projekt knihovny tříd a klikněte na tlačítko **OK** .

   ![Dialog Správce odkazů s vybraným StringLibrary](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. V okně kódu pro soubor *program.cs* nebo *program. vb* nahraďte celý kód následujícím kódem:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kód používá proměnnou `row` k udržení počtu řádků dat zapsaných do okna konzoly. Pokaždé, když je větší nebo rovno 25, kód vymaže okno konzoly a zobrazí uživateli zprávu.

   Program vyzve uživatele k zadání řetězce. Označuje, zda řetězec začíná velkým znakem. Pokud uživatel stiskne klávesu ENTER bez zadání řetězce, aplikace skončí a okno konzoly se zavře.

1. V případě potřeby změňte panel nástrojů pro zkompilování **ladicí** verze `ShowCase` projektu. Zkompilujte a spusťte program tak, že vyberete zelenou šipku na **tlačítku pro** sestavování.

   ![Panel nástrojů projekt sady Visual Studio zobrazující tlačítko ladění](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Můžete ladit a publikovat aplikaci, která používá tuto knihovnu, pomocí postupu v části [ladění aplikace C# nebo Visual Basic .NET Core Hello World pomocí sady Visual Studio](debugging-with-visual-studio.md) a [publikování aplikace .NET Core Hello World v aplikaci Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Vytvoření balíčku NuGet

Vaše knihovna tříd může být široce dostupná, když ji publikujete jako balíček NuGet. Visual Studio nepodporuje vytváření balíčků NuGet. Abyste ho mohli vytvořit, musíte použít .NET Core CLI příkazy:

1. Otevřete okno konzoly.

   Zadejte například **příkazový řádek** do pole Hledat na panelu úloh systému Windows. Vyberte aplikaci desktopového **řádku** nebo stiskněte klávesu **ENTER** , pokud už je ve výsledcích hledání vybraná.

1. Přejděte do adresáře projektu knihovny. Adresář obsahuje zdrojový kód a soubor projektu, *StringLibrary. csproj* nebo *StringLibrary. vbproj*.

1. Spusťte příkaz [dotnet Pack](../tools/dotnet-pack.md) pro vygenerování balíčku s příponou *. nupkg* :

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Pokud adresář, který obsahuje *dotnet. exe* , není ve vaší cestě, můžete najít jeho umístění zadáním `where dotnet.exe` v okně konzoly.

Další informace o vytváření balíčků NuGet najdete v tématu [Postup vytvoření balíčku NuGet s nástroji pro různé platformy](../deploying/creating-nuget-packages.md).
