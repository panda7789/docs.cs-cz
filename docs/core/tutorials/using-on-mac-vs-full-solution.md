---
title: Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede vytvořením řešení .NET Core, které obsahuje opakovaně použitelnou knihovnu a testování částí.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 46d118cc4dc54e34db0f964aa3f8d76f0ad67249
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926000"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio pro Mac poskytuje integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Toto téma vás provede vytvořením řešení .NET Core, které obsahuje opakovaně použitelnou knihovnu a testování částí.

V tomto kurzu se dozvíte, jak vytvořit aplikaci, která přijímá hledané slovo a řetězec textu od uživatele, spočítá počet, kolikrát se hledané slovo v řetězci zobrazí pomocí metody v knihovně tříd a vrátí výsledek uživateli. Řešení zahrnuje také testování částí knihovny tříd jako úvod do konceptů testování částí. Pokud budete chtít pokračovat v kurzu s kompletní ukázkou, Stáhněte si [ukázkové řešení](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Vaše zpětná vazba je vysoce ohodnocená. Existují dva způsoby, jak můžete poskytnout týmu vývoje zpětnou vazbu v Visual Studio pro Mac:
>
> - V Visual Studio pro Mac vyberte v nabídce **nápovědu** > **nahlásit problém** nebo **nahlásit problém** z úvodní obrazovky, která otevře okno pro podání zprávy o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Chcete-li vytvořit návrh, vyberte v **nabídce možnost** > **poskytnout návrh** nebo **Poskytněte návrh** z úvodní obrazovky, který vás přesměruje na [webovou stránku komunity vývojářů Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Požadavky

- OpenSSL (Pokud používáte .NET Core 1,1): Podívejte se na téma [požadavky pro .NET Core na Macu](../macos-prerequisites.md) .
- [.NET Core SDK 1,1 nebo novější](https://dotnet.microsoft.com/download)
- [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Další informace o požadavcích najdete v tématu [požadavky pro .NET Core na Macu](../macos-prerequisites.md). Úplné požadavky na systém pro sadu Visual Studio 2017 pro Mac najdete v tématu [požadavky na systém pro produktovou řadu Visual studio 2017 for Mac](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Sestavení knihovny

1. Na úvodní obrazovce vyberte **Nový projekt**. V dialogovém okně **Nový projekt** pod uzlem **.NET Core** vyberte šablonu **knihovny .NET Standard** . Tím se vytvoří knihovna .NET Standard, která cílí na rozhraní .NET Core, i na jakoukoli jinou implementaci .NET, která podporuje [.NET Standard](../../standard/net-standard.md)verze 2,0. Vyberte **Další**.

   ![Dialog Visual Studio pro Mac nový projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Pojmenujte projekt "TextUtils" (krátký název "text Utilities") a řešením "WordCounter". Ponechejte možnost **vytvořit adresář projektu v adresáři řešení** zaškrtnuté. Vyberte **Vytvořit**.

   ![Visual Studio pro Mac možnosti dialogového okna Nový projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Na bočním panelu **řešení** rozbalte `TextUtils` uzel, aby se zobrazil soubor třídy poskytnutý šablonou, *Class1.cs*. Klikněte na soubor pravým tlačítkem, v místní nabídce vyberte **Přejmenovat** a pak tento soubor přejmenujte na *WORDCOUNT.cs*. Otevřete soubor a nahraďte jeho obsah následujícím kódem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Uložte soubor pomocí kterékoli ze tří různých metod: <kbd>&#8984;</kbd> + <kbd>použijte klávesovou zkratku</kbd>, v nabídce vyberte**Uložit** **soubor** > nebo klikněte pravým tlačítkem na kartu soubor a vyberte **Uložit** z kontextové nabídce. Následující obrázek znázorňuje okno IDE:

   ![Visual Studio pro Mac okno IDE se souborem knihovny tříd a metodou](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. V dolní části okna IDE vyberte **chyby** a otevřete panel **chyby** . Vyberte tlačítko **výstup sestavení** .

   ![Spodní okraj integrovaného vývojového prostředí (IDE) sady Visual Studio zobrazující tlačítko chyby](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. V nabídce vyberte **sestavit** > **vše** .

   Řešení vytvoří. Na panelu výstup sestavení se zobrazí, že sestavení proběhlo úspěšně.

   ![Podokno výstupu sestavení Mac sady Visual Studio na panelu chyby se zprávou úspěšné sestavení](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Vytvoření testovacího projektu

Testy jednotek poskytují automatizované softwarové testování během vývoje a publikování. Testovací rozhraní, které používáte v tomto kurzu, je [xUnit (verze 2.2.0 nebo novější)](https://xunit.github.io/), které se instaluje automaticky při přidání projektu testů xUnit do řešení v následujících krocích:

1. Na bočním panelu **řešení** klikněte pravým tlačítkem `WordCounter` na řešení a vyberte **Přidat** > **Přidat nový projekt**.

1. V dialogovém okně **Nový projekt** vyberte možnost **testy** z uzlu **.NET Core** . Vyberte **projekt testů xUnit** a potom klikněte na tlačítko **Další**.

   ![Visual Studio – nový projekt – dialogové okno vytvoření projektu testů xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Pojmenujte nový projekt "TestLibrary" a vyberte **vytvořit**.

   ![Visual Studio Mac – dialog nového projektu zadání názvu projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Chcete-li, aby knihovna testů spolupracovala `WordCount` s třídou, přidejte odkaz `TextUtils` na projekt. Na bočním panelu **řešení** klikněte pravým tlačítkem na **závislosti** pod **TestLibrary**. V místní nabídce vyberte **Upravit odkazy** .

1. V dialogovém okně **Upravit odkazy** vyberte projekt **TextUtils** na kartě **projekty** . Vyberte **OK**.

   ![Dialogové okno Visual Studio Mac Edit References](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

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

   Na následujícím obrázku je znázorněno integrované vývojové prostředí (IDE) s kódem testování částí. Věnujte pozornost `Assert.NotEqual` příkazu.

   ![Visual Studio pro Mac počáteční test jednotky v hlavním okně IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Je důležité, aby se nový test nezdařil jednou, aby bylo možné potvrdit, že je logika testování správná. Metoda předává název "zdířka" (velká písmena) a řetězec se znakem "zdířka" a "zdířka" (velká a malá písmena). `GetWordCount` Pokud metoda pracuje správně, vrátí počet dvou instancí hledaného slova. Aby nedošlo k selhání tohoto testu, nejprve implementujte test, který vyhodnotí, že se `GetWordCount` v metodě nevrátí dvě instance hledaného slova "kolík". Pokračujte dalším krokem, abyste nevyhověli testu za účelem.

1. Otevřete panel **testování částí** na pravé straně obrazovky.

   ![Panel testování částí Visual Studio pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Kliknutím na ikonu **Dock (ukotvit** ) ponechejte panel otevřený.

   ![Ikona ukotvení panelu Visual Studio pro Mac testování částí](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Klikněte na tlačítko **Spustit vše** .

   Test se nezdařil, což je správný výsledek. Testovací metoda vyhodnotí, že z řetězce " `inputString`zdířková zdířka" poskytnutého `GetWordCount` metodě nejsou vraceny dvě instance "konektor". Vzhledem k `GetWordCount` tomu, že velká a malá písmena byla v metodě rozložena, jsou vraceny dvě instance. Kontrolní výraz, který 2 *není roven* 2, se nezdařil. Toto je správný výsledek a logika našeho testu je dobrá.

   ![Visual Studio pro Mac zobrazení selhání testu](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Upravte testovací metodu změnou `Assert.NotEqual` na `Assert.Equal`. `IgnoreCasing` <kbd>&#8984;</kbd> +Uložte soubor <kbd>pomocí klávesových zkratek</kbd>,**Uložit** **soubor** > z nabídky nebo klikněte pravým tlačítkem na kartu soubor a v místní nabídce vyberte možnost **Uložit** .

   Očekává se, že `searchWord` "konektor" vrátí dvě instance se `inputString` předanými `GetWordCount`"konektorovou zásuvkou". Spusťte test znovu kliknutím na tlačítko **Spustit testy** na panelu **testy jednotek** nebo na tlačítko **znovu spustit testy** na panelu **výsledky testů** v dolní části obrazovky. Test byl úspěšný. Existují dvě instance "zdířka" v řetězci "zdířková zdířka" (ignoruje velikost písmen) a kontrolní výraz testu je `true`.

   ![Zobrazení Visual Studio pro Macového průchodu testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Testování jednotlivých návratových hodnot pomocí `Fact` je pouze začátek toho, co můžete provádět s testováním částí. Další výkonná technika vám umožní otestovat několik hodnot najednou pomocí `Theory`. Do `TextUtils_GetWordCountShould` třídy přidejte následující metodu. Po přidání této metody máte ve třídě dvě metody:

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

   `CountInstancesCorrectly` Kontroluje ,`GetWordCount` zda metoda počítá správně. `InlineData` Poskytuje počet, hledané slovo a vstupní řetězec pro kontrolu. Testovací metoda se spustí jednou pro každý řádek dat. Všimněte si, že jakmile znovu vyřešíte selhání, použijte `Assert.NotEqual`, i když víte, že počty v datech jsou správné a že hodnoty odpovídají počtu vráceným `GetWordCount` metodou. Provádění kroku selhání testu se může zdát jako plýtvání času v prvním, ale Kontrola logiky testu tím, že je napřed nezdařila, je důležité zkontrolovat logiku testů. Pokud jste pocházeli v rámci testovací metody, která projde, když očekáváte, že selže, našla jste chybu v logice testu. Je vhodné provést tento krok pokaždé, když vytvoříte testovací metodu.

1. Uložte soubor a spusťte testy znovu. Test velkých a malých písmen projde, ale tři testy počtu selžou. To je přesně to, co očekáváte.

   ![Visual Studio pro Mac očekávaného selhání testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Upravte testovací metodu změnou `Assert.NotEqual` na `Assert.Equal`. `CountInstancesCorrectly` Uložte soubor. Spusťte testy znovu. Všechny testy jsou passované.

   ![Visual Studio pro Mac očekávanou zkušební úspěšnost](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Přidání konzolové aplikace

1. Na bočním panelu **řešení** klikněte pravým tlačítkem `WordCounter` na řešení. Přidejte nový projekt **konzolové aplikace** tak, že vyberete šablonu ze šablon**aplikací** **.NET Core** > . Vyberte **Další**. Pojmenujte projekt **WordCounterApp**. Vyberte **vytvořit** a vytvořte projekt v řešení.

1. Na bočním panelu **řešení** klikněte pravým tlačítkem myši na uzel **závislosti** nového projektu **WordCounterApp** . V dialogovém okně **Upravit odkazy** zaškrtněte **TextUtils** a vyberte **OK**.

1. Otevřete soubor *program.cs* . Nahraďte kód následujícím kódem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Chcete-li aplikaci spustit v okně konzoly místo rozhraní IDE, klikněte pravým tlačítkem myši `WordCounterApp` na projekt, vyberte **možnost možnosti**a otevřete **výchozí** uzel v části **Konfigurace**. Zaškrtněte políčko **Spustit na externí konzole**. Ponechte zaškrtnuté políčko **pozastavit výstup konzoly** . Toto nastavení způsobí, že se aplikace spustí v okně konzoly, takže můžete zadat vstup pro `Console.ReadLine` příkazy. Pokud necháte aplikaci spuštěnou v integrovaném vývojovém prostředí (IDE), můžete zobrazit pouze `Console.WriteLine` výstup příkazů. `Console.ReadLine`příkazy nefungují v panelu **výstupu aplikace** IDE.

   ![Visual Studio pro Mac okno možností projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-project-options.png)

1. Vzhledem k tomu, že aktuální verze Visual Studio pro Mac nemůže spustit testy při spuštění řešení, spusťte konzolovou aplikaci přímo. Klikněte pravým tlačítkem myši na projektavybertemožnostspustitpoložkuzkontextové`WordCounterApp` nabídky. Pokud se pokusíte spustit aplikaci pomocí tlačítka Přehrát, spouštěč testů a aplikaci nelze spustit. Další informace o stavu práce na tomto problému najdete v tématu [xUnit/xamarinstudio. xUnit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Po spuštění aplikace zadejte do příkazového řádku v okně konzoly hodnoty pro hledané slovo a vstupní řetězec. Aplikace označuje počet, kolikrát se hledané slovo v řetězci zobrazuje.

   ![Okno konzoly Visual Studio pro Mac znázorňující spuštěnou aplikaci](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Poslední funkcí k prozkoumávání je ladění pomocí Visual Studio pro Mac. Nastavte zarážku na `Console.WriteLine` příkaz: Vyberte v levém okraji řádku 23 a zobrazí se vedle řádku kódu červené kolečko. Případně vyberte libovolné místo na řádku kódu a v nabídce vyberte **Spustit** > **Přepnout zarážku** .

   ![Sada zarážek Visual Studio pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. Klikněte pravým tlačítkem `WordCounterApp` na projekt. V místní nabídce vyberte **položku Spustit ladění** . Po spuštění aplikace zadejte hledané slovo "Cat" a "pes sledování odkazůa Cat, ale řídicí sekvence Cat." řetězec, který chcete vyhledat. Po dosažení `Console.WriteLine` příkazu se spuštění programu zastaví před provedením příkazu. Na kartě `searchWord` `inputString`místní hodnotyvidítehodnoty`pluralChar` ,, `wordCount`a.

   ![Spuštění programu ladicího programu Visual Studio pro Mac bylo zastaveno.](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. V podokně **Immediate** zadejte "wordCount = 999;" a stiskněte klávesu ENTER. Tím se přiřadí hodnota nonsense 999 k `wordCount` proměnné, která ukazuje, že při ladění můžete nahradit hodnoty proměnných.

   ![Visual Studio pro Mac Změna hodnot v příkazovém okně](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na panelu nástrojů klikněte na šipku *pokračovat* . Podívejte se na výstup v okně konzoly. Oznamuje nesprávnou hodnotu 999, kterou jste nastavili při ladění aplikace.

   ![Tlačítko pro Visual Studio pro Mac pokračování na panelu nástrojů](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   ![Výstup okna konzoly Visual Studio pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

## <a name="see-also"></a>Viz také:

- [Zpráva k vydání verze pro Visual Studio 2017 for Mac](/visualstudio/releasenotes/vs2017-mac-relnotes)
