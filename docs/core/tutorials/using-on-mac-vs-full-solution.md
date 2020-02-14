---
title: Sestavení kompletního řešení .NET Core pomocí Visual Studio pro Mac
description: Tento článek vás provede vytvořením řešení .NET Core, které obsahuje opakovaně použitelnou knihovnu a testování částí.
ms.date: 12/19/2019
ms.openlocfilehash: dea23da33912de849f0dcbe1e2f6fa3edb3a5e24
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215204"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Sestavení kompletního řešení .NET Core na macOS pomocí Visual Studio pro Mac

Visual Studio pro Mac poskytuje integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Tento článek vás provede vytvořením řešení .NET Core, které obsahuje opakovaně použitelnou knihovnu a testování částí.

V tomto kurzu se dozvíte, jak vytvořit aplikaci, která přijímá hledané slovo a řetězec textu od uživatele, spočítá počet, kolikrát se hledané slovo v řetězci zobrazí pomocí metody v knihovně tříd a vrátí výsledek uživateli. Řešení zahrnuje také testování částí knihovny tříd jako úvod do konceptů testování částí. Pokud budete chtít pokračovat v kurzu s kompletní ukázkou, Stáhněte si [ukázkové řešení](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Vaše zpětná vazba je vysoce ohodnocená. Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:
>
> - V Visual Studio pro Mac vyberte **Help** > **nahlásit problém** z nabídky nebo **nahlásit problém** z úvodní obrazovky, která otevře okno pro podání zprávy o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Chcete-li vytvořit návrh, vyberte možnost **Help** > **poskytnout návrh** z nabídky nebo **Poskytněte návrh** z úvodní obrazovky, který vás přesměruje na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Předpoklady

- [.NET Core SDK 3,1 nebo novější](https://dotnet.microsoft.com/download)
- [Visual Studio 2019 pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Další informace o požadavcích najdete v tématu [závislosti a požadavky .NET Core](../install/dependencies.md?pivots=os-macos). Úplné požadavky na systém pro sadu Visual Studio 2019 pro Mac najdete v tématu [požadavky na systém pro produktovou řadu Visual studio 2019 for Mac](/visualstudio/productinfo/vs2019-system-requirements-mac).

## <a name="building-a-library"></a>Sestavení knihovny

1. V okně Start vyberte **Nový projekt**. V dialogovém okně **Nový projekt** pod uzlem **.NET Core** vyberte šablonu **knihovny .NET Standard** . Tento příkaz vytvoří knihovnu .NET Standard, která cílí na rozhraní .NET Core, i na jakoukoli jinou implementaci rozhraní .NET, která podporuje verzi 2,1 [.NET Standard](../../standard/net-standard.md). Pokud máte nainstalováno více verzí .NET Core SDK, můžete pro knihovnu zvolit různé verze .NET Standard. Zvolte .NET Standard 2,1 a vyberte **Další**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac dialogové okno Nový projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Pojmenujte projekt "TextUtils" (krátký název "text Utilities") a řešením "WordCounter". Ponechejte možnost **vytvořit adresář projektu v adresáři řešení** zaškrtnuté. Vyberte **Create** (Vytvořit).

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac dialogových oknech Nový projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Na panelu **řešení** rozbalte uzel `TextUtils`, aby se zobrazil soubor třídy poskytnutý šablonou, *Class1.cs*. Podržte klávesu CTRL a klikněte na soubor, v místní nabídce vyberte **Přejmenovat** a přejmenujte soubor na *WORDCOUNT.cs*. Otevřete soubor a nahraďte jeho obsah následujícím kódem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Uložte soubor pomocí kterékoli ze tří různých metod: <kbd>&#8984;</kbd> použijte klávesovou zkratku+<kbd>s</kbd>, vyberte **soubor** > **Uložit** z nabídky nebo stiskněte klávesu CTRL na kartě soubor a v místní nabídce vyberte **Uložit** . Následující obrázek znázorňuje okno IDE:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac okno IDE se souborem knihovny tříd a metodou](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. V dolní části okna IDE vyberte **chyby** a otevřete panel **chyby** . Vyberte tlačítko **výstup sestavení** .

   > [!div class="mx-imgBorder"]
   > ![dolního okraje integrovaného vývojového prostředí (IDE) sady Visual Studio, které zobrazuje tlačítko chyby](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. V nabídce vyberte **sestavit** > **sestavit vše** .

   Řešení vytvoří. Na panelu výstup sestavení se zobrazí, že sestavení proběhlo úspěšně.

   > [!div class="mx-imgBorder"]
   > ![podokna výstup sestavení Mac sady Visual Studio na panelu chyby se zprávou úspěšné sestavení](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Vytvoření testovacího projektu

Testy jednotek poskytují automatizované softwarové testování během vývoje a publikování. Testovací rozhraní, které používáte v tomto kurzu, je [xUnit (verze 2.4.0 nebo novější)](https://xunit.github.io/), které se instaluje automaticky při přidání projektu testů xUnit do řešení v následujících krocích:

1. Na bočním panelu **řešení** klikněte na `WordCounter` řešení a vyberte **Přidat** > **Přidat nový projekt**.

1. V dialogovém okně **Nový projekt** vyberte možnost **testy** z uzlu **.NET Core** . Vyberte **projekt testů xUnit** a potom klikněte na tlačítko **Další**.

   > [!div class="mx-imgBorder"]
   > dialog ![Visual Studio Mac nový projekt vytváření projektu testů xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Pokud máte více verzí .NET Core SDK, budete muset vybrat verzi tohoto projektu. Vyberte **.NET Core 3,1**. Pojmenujte nový projekt "TestLibrary" a vyberte **vytvořit**.

   > [!div class="mx-imgBorder"]
   > ![dialogovém okně Visual Studio Mac nový projekt zadáním názvu projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Aby mohla knihovna testů pracovat s třídou `WordCount`, přidejte odkaz na projekt `TextUtils`. Na bočním panelu **řešení** klikněte v části **TestLibrary**na **závislosti** CTRL. V místní nabídce vyberte **Upravit odkazy** .

1. V dialogovém okně **Upravit odkazy** vyberte projekt **TextUtils** na kartě **projekty** . Vyberte **OK**.

   > [!div class="mx-imgBorder"]
   > ![dialogovém okně Visual Studio Mac Edit References](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. V projektu **TestLibrary** přejmenujte soubor *UnitTest1.cs* na *TextUtilsTests.cs*.

1. Otevřete soubor a nahraďte kód následujícím kódem:

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");

               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   Na následujícím obrázku je znázorněno integrované vývojové prostředí (IDE) s kódem testování částí. Věnujte pozornost příkazu `Assert.NotEqual`.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac počáteční test jednotky v hlavním okně IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Je důležité, aby se nový test nezdařil jednou, aby bylo možné potvrdit, že je logika testování správná. Metoda předává název "zdířka" (velká písmena) a řetězec se znakem "zdířka" a "zdířka" (velká a malá písmena). Pokud metoda `GetWordCount` pracuje správně, vrátí počet dvou instancí hledaného slova. Aby nedošlo k selhání tohoto testu, nejprve implementujte test vyhodnocení, že dvě instance hledaného slova "kolík" nejsou vráceny metodou `GetWordCount`. Pokračujte dalším krokem, abyste nevyhověli testu za účelem.

1. Otevřete panel **testování částí** na pravé straně obrazovky. V nabídce vyberte **zobrazit** > **testy** .

   > [!div class="mx-imgBorder"]
   > panel testování částí ![Visual Studio pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Kliknutím na ikonu **Dock (ukotvit** ) ponechejte panel otevřený. (Zvýrazněný na následujícím obrázku.)

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac ikona ukotvení panelu testování částí](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Klikněte na tlačítko **Spustit vše** .

   Test se nezdařil, což je správný výsledek. Testovací metoda vyhodnotí, že dvě instance `inputString`, "konektor", nejsou vraceny z řetězce "konektorové zdířky" poskytnuté metodě `GetWordCount`. Vzhledem k tomu, že se v metodě `GetWordCount` nepoužilo slovo velká písmena, vrátí se dvě instance. Kontrolní výraz, který 2 *není roven* 2, se nezdařil. Výsledkem je správný výsledek a logika našeho testu je dobrá.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac chyba testu](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Upravte `IgnoreCasing` testovací metodu změnou `Assert.NotEqual` na `Assert.Equal`. Uložte soubor pomocí klávesové zkratky <kbd>Ctrl</kbd>+<kbd>s</kbd>, **soubor** > **Uložit** z nabídky nebo se stisknutím klávesy CTRL a kliknutím na tlačítko **Uložit** v místní nabídce na kartu souboru.

   Očekává se, že `searchWord` "konektor" vrátí dvě instance `inputString` "konektorovou zásuvkou" předané do `GetWordCount`. Spusťte test znovu kliknutím na tlačítko **Spustit testy** na panelu **testy jednotek** nebo na tlačítko **znovu spustit testy** na panelu **výsledky testů** v dolní části obrazovky. Test byl úspěšný. Existují dvě instance "zdířka" v řetězci "zdířková zdířka" (ignoruje velikost písmen) a kontrolní výraz testu je `true`.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac testy se přejdou zobrazit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Testování jednotlivých návratových hodnot pomocí `Fact` je pouze začátek toho, co můžete provádět s testováním částí. Další výkonná technika vám umožní otestovat několik hodnot najednou pomocí `Theory`. Přidejte následující metodu do třídy `TextUtils_GetWordCountShould`. Po přidání této metody máte ve třídě dvě metody:

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count,
                                       string searchWord,
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` kontroluje, zda se metoda `GetWordCount` správně počítá. `InlineData` poskytuje počet, hledané slovo a vstupní řetězec pro kontrolu. Testovací metoda se spustí jednou pro každý řádek dat. Všimněte si, že znovu vyřešíte selhání pomocí `Assert.NotEqual`, a to i v případě, že víte, že počty v datech jsou správné a že hodnoty odpovídají počtu vraceným metodou `GetWordCount`. Provádění kroku selhání testu se může zdát jako plýtvání času v prvním, ale Kontrola logiky testu tím, že je napřed nezdařila, je důležité zkontrolovat logiku testů. Pokud jste pocházeli v rámci testovací metody, která projde, když očekáváte, že selže, našla jste chybu v logice testu. Je vhodné provést tento krok pokaždé, když vytvoříte testovací metodu.

1. Uložte soubor a spusťte testy znovu. Test velkých a malých písmen projde, ale tři testy počtu selžou. Tento výsledek přesně odpovídá tomu, co byste očekávali.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac očekávaná chyba testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Upravte `CountInstancesCorrectly` testovací metodu změnou `Assert.NotEqual` na `Assert.Equal`. Uložte soubor. Spusťte testy znovu. Všechny testy jsou passované.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac byl očekáván test průchodů](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Přidání konzolové aplikace

1. Na bočním panelu **řešení** stiskněte CTRL a klikněte na řešení `WordCounter`. Přidejte nový projekt **konzolové aplikace** tak, že vyberete šablonu ze šablon **aplikací** >  **.NET Core** . Vyberte **Další**. Pojmenujte projekt **WordCounterApp**. Vyberte **vytvořit** a vytvořte projekt v řešení.

1. Na bočním panelu **řešení** klikněte na uzel **závislosti** nového projektu **WordCounterApp** . V dialogovém okně **Upravit odkazy** zaškrtněte **TextUtils** a vyberte **OK**.

1. Otevřete soubor *program.cs* . Nahraďte kód následujícím kódem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Stiskněte klávesu CTRL a klikněte na projekt `WordCounterApp` a v místní nabídce vyberte **spustit projekt** . Po spuštění aplikace zadejte do příkazového řádku v okně konzoly hodnoty pro hledané slovo a vstupní řetězec. Aplikace označuje počet, kolikrát se hledané slovo v řetězci zobrazuje.

   > [!div class="mx-imgBorder"]
   > Visual Studio pro Mac okno konzoly ![, ve kterém se zobrazuje vaše aplikace](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Poslední funkcí k prozkoumávání je ladění pomocí Visual Studio pro Mac. Nastavte zarážku na příkaz `Console.WriteLine`: vyberte na levém okraji řádku 23 a zobrazí se červené kolečko vedle řádku kódu. Případně vyberte libovolné místo na řádku kódu a vyberte možnost **spustit** > **Přepnout zarážku** z nabídky.

   > [!div class="mx-imgBorder"]
   > sada zarážek ![Visual Studio pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. stiskněte klávesu CTRL a klikněte na projekt `WordCounterApp`. V místní nabídce vyberte **Spustit ladění projektu** . Po spuštění aplikace zadejte hledané slovo "Cat" a "pes sledování odkazůa Cat, ale řídicí sekvence Cat." řetězec, který chcete vyhledat. Když je dosaženo příkazu `Console.WriteLine`, spuštění programu se před provedením příkazu zastaví. Na kartě **místní** hodnoty vidíte `searchWord`, `inputString`, `wordCount`a hodnoty `pluralChar`.

   > [!div class="mx-imgBorder"]
   > běh programu ![Visual Studio pro Mac ladicí program byl zastaven](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. V podokně **Immediate** zadejte "wordCount = 999;" a stiskněte klávesu ENTER. Tento příkaz přiřadí hodnotu nonsense, která je 999, do proměnné `wordCount` ukazuje, že při ladění můžete nahradit hodnoty proměnných.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac změně hodnot v příkazovém okně](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na panelu nástrojů klikněte na šipku *pokračovat* . Podívejte se na výstup v okně konzoly. Oznamuje nesprávnou hodnotu 999, kterou jste nastavili při ladění aplikace.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac tlačítko pokračovat na panelu nástrojů](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > výstup okna konzoly ![Visual Studio pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Stejný postup můžete použít k ladění kódu pomocí projektu testování částí. Namísto spuštění projektu aplikace WordCount, stiskněte klávesu CTRL a klikněte na projekt **knihovny testů** a v místní nabídce vyberte **Spustit ladění projektu** . Visual Studio pro Mac spustí testovací projekt pomocí připojeného ladicího programu. Spuštění se zastaví na všech zarážekch, které jste přidali do testovacího projektu, nebo na podkladový kód knihovny.

## <a name="see-also"></a>Viz také

- [Zpráva k vydání verze pro Visual Studio 2019 pro Mac](/visualstudio/releasenotes/vs2019-mac-relnotes)
