---
title: Vytvoření kompletního řešení .NET Core pomocí Visual Studia pro Mac
description: Tento článek vás provede vytvářením řešení .NET Core, které zahrnuje opakovaně použitelné knihovny a testování částí.
ms.date: 12/19/2019
ms.openlocfilehash: 8c9fcca404a3875b6bb7f9cf20551a017ff553c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239960"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Vytvoření kompletního řešení .NET Core na macOS pomocí Visual Studia pro Mac

Visual Studio for Mac poskytuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj základních aplikací .NET. Tento článek vás provede vytvářením řešení .NET Core, které zahrnuje opakovaně použitelné knihovny a testování částí.

Tento kurz ukazuje, jak vytvořit aplikaci, která přijímá hledané slovo a řetězec textu od uživatele, spočítá počet zobrazení hledaného slova v řetězci pomocí metody v knihovně tříd a vrátí výsledek uživateli. Řešení také zahrnuje testování částí pro knihovnu tříd jako úvod do konceptů testování částí. Pokud dáváte přednost pokračovat v kurzu s úplnou ukázku, stáhněte si [ukázkové řešení](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Vaše zpětná vazba je vysoce ceněna. Vývojový tým Visual Studia for Mac může poskytnout zpětnou vazbu dvěma způsoby:
>
> - V Visual Studiu pro Mac vyberte **nápovědu** > **nahlásit problém** z nabídky nebo **Nahlásit problém** na úvodní obrazovce, která otevře okno pro podání hlášení o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Chcete-li vytvořit návrh, vyberte **v** > nabídce**možnost Poskytnout návrh** nebo **Poskytněte návrh** na úvodní obrazovce, která vás přenese na [webovou stránku komunity vývojářů sady Visual Studio pro Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Požadavky

- [Sada .NET Core SDK 3.1 nebo novější](https://dotnet.microsoft.com/download)
- [Visual Studio 2019 pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Další informace o požadavcích naleznete v tématu [.NET Core závislosti a požadavky](../install/dependencies.md?pivots=os-macos). Úplné systémové požadavky Visual Studia 2019 pro Mac najdete v [tématu Visual Studio 2019 for Mac Product Family System Requirements](/visualstudio/productinfo/vs2019-system-requirements-mac).

## <a name="building-a-library"></a>Budování knihovny

1. V úvodním okně vyberte **Nový projekt**. V dialogovém okně **Nový projekt** pod uzu **.NET Core** vyberte šablonu **.NET Standard Library.** Tento příkaz vytvoří knihovnu .NET Standard, která cílí na jádro .NET, stejně jako na jakoukoli jinou implementaci rozhraní .NET, která podporuje verzi 2.1 [standardu .NET .](../../standard/net-standard.md) Pokud máte nainstalováno více verzí sady .NET Core SDK, můžete pro knihovnu zvolit různé verze standardu .NET. Zvolte ".NET Standard 2.1" a vyberte **Další**.

   > [!div class="mx-imgBorder"]
   > ![Dialogové okno Visual Studio for Mac Nový projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Pojmenujte projekt "TextUtils" (krátký název pro "Textové nástroje") a řešení "WordCounter". Ponechat **Ponechat Políčko Vytvořit adresář projektu v adresáři řešení** zaškrtnuto. Vyberte **Vytvořit**.

   > [!div class="mx-imgBorder"]
   > ![Možnosti dialogového okna Visual Studio for Mac Nové okno projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Na panelu **Řešení** `TextUtils` rozbalte uzel a zjevte soubor třídy poskytnutý šablonou *Class1.cs*. Klepněte se stisknutou klávesou Ctrl, z kontextové nabídky vyberte **Přejmenovat** a přejmenujte soubor na *WordCount.cs*. Otevřete soubor a nahraďte obsah následujícím kódem:

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/TextUtils/WordCount.cs)]

1. Uložte soubor pomocí některé ze tří různých metod: použijte klávesovou zkratku <kbd>&#8984;</kbd> + <kbd>s</kbd>, z nabídky vyberte**Uložit** **soubor** > nebo klepněte se stisknutou klávesou Ctrl na kartu souboru a z kontextové nabídky vyberte **Uložit.** Následující obrázek znázorňuje okno IDE:

   > [!div class="mx-imgBorder"]
   > ![Okno Visual Studio pro Mac IDE se souborem a metodou knihovny tříd](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Vyberte **Chyby** v okraji v dolní části okna IDE, chcete-li otevřít panel **Chyby.** Vyberte tlačítko **Výstup sestavení.**

   > [!div class="mx-imgBorder"]
   > ![Dolní okraj ide Mac sady Visual Studio s tlačítkem Chyby](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. V nabídce vyberte **Build** > **Build All** .

   Řešení se staví. Výstupní panel sestavení ukazuje, že sestavení je úspěšné.

   > [!div class="mx-imgBorder"]
   > ![Vizuální Studio Mac Vytvoří výstupní podokno panelu Chyby s odesláním úspěšné zprávy](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Vytvoření testovacího projektu

Testy částí poskytují automatizované testování softwaru během vývoje a publikování. Testování rozhraní, které používáte v tomto kurzu je [xUnit (verze 2.4.0 nebo novější)](https://xunit.github.io/), který je nainstalován automaticky při přidání projektu xUnit test do řešení v následujících krocích:

1. Na postranním panelu **Řešení** `WordCounter` klepněte se stisknutou klávesou Ctrl na řešení a vyberte **Přidat** > **nový projekt**.

1. V dialogovém okně **Nový projekt** vyberte **testy** z uzlu **.NET Core.** Vyberte **testovací projekt xUnit** následovaný položkou **Next**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac Nový projekt dialogové okno vytváření xUnit testovací projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Pokud máte více verzí sady .NET Core SDK, budete muset vybrat verzi pro tento projekt. Vyberte **.NET Core 3.1**. Pojmenujte nový projekt "TestLibrary" a vyberte **Vytvořit**.

   > [!div class="mx-imgBorder"]
   > ![Dialogové okno Visual Studio Mac Nový projekt s názvem projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Aby testovací knihovna fungovala `WordCount` s třídou, přidejte odkaz na `TextUtils` projekt. Na postranním panelu **Řešení** klepněte se stisknutou klávesou **Ctrl na položku Závislosti** v části **TestLibrary**. Z kontextové nabídky vyberte **Upravit odkazy.**

1. V dialogovém okně **Upravit odkazy** vyberte projekt TextUtils **OK**na kartě **Projekty.** **Projects**

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac – dialogové okno Upravit reference](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

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

   Následující obrázek znázorňuje ide s kódem testování částí na místě. Dávejte pozor `Assert.NotEqual` na prohlášení.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac Počáteční testování částí v hlavním okně IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Je důležité, aby nový test selhání jednou potvrdit jeho testování logika je správná. Metoda prochází v názvu "Jack" (velká písmena) a řetězec s "Jack" a "jack" (velká a malá písmena). Pokud `GetWordCount` metoda funguje správně, vrátí počet dvou instancí hledaného slova. Chcete-li selhání tohoto testu záměrně, nejprve implementovat test potvrzuje, že dvě instance hledané `GetWordCount` slovo "Jack" nejsou vráceny metodou. Pokračujte k dalšímu kroku, abyste test záměrně neprošel.

1. Otevřete panel **Testy částí** na pravé straně obrazovky. V nabídce vyberte **Zobrazit** > **testy.**

   > [!div class="mx-imgBorder"]
   > ![Panel Visual Studio for Mac Unit Tests](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Klepnutím na ikonu **Dock** ponechte panel otevřený. (Zvýrazněno na následujícím obrázku.)

   > [!div class="mx-imgBorder"]
   > ![Ikona doku panelu Visual Studio for Mac Unit Tests](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Klepněte na tlačítko **Spustit vše.**

   Test se nezdaří, což je správný výsledek. Testovací metoda tvrdí, že dvě `inputString`instance , "Jack", nejsou vráceny z řetězce "Jack jack" poskytované metodě. `GetWordCount` Vzhledem k tomu, že `GetWordCount` v metodě byla zohledněna malá písmena slov, jsou vráceny dvě instance. Tvrzení, že 2 *se nerovná* 2 selže. Tento výsledek je správný výsledek a logika našeho testu je dobrá.

   > [!div class="mx-imgBorder"]
   > ![Zobrazení selhání testu sady Visual Studio for Mac](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Upravte `IgnoreCasing` zkušební metodu změnou `Assert.NotEqual` na `Assert.Equal`. Uložte soubor pomocí klávesové<kbd>zkratky</kbd> <kbd>Ctrl</kbd>+s , **File** > **Save** z nabídky nebo klepnutím se stisknutou klávesou Ctrl na kartu souboru a výběrem **možnosti Uložit** z kontextové nabídky.

   Očekáváte, `searchWord` že "Jack" vrátí `inputString` dvě instance s `GetWordCount`"Jack jack" předándo . Spusťte test znovu klepnutím na tlačítko **Spustit testy** v panelu **Testy částí** nebo na tlačítko Znovu spustit **testy** v panelu **Výsledky testu** v dolní části obrazovky. Test projde. Existují dvě instance "Jack" v řetězci "Jack jack" (ignorování krytu) a kontrolní výraz testu je `true`.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac testy projít displej](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Testování jednotlivých vrácených hodnot s a `Fact` je pouze začátek toho, co můžete dělat s testováním částí. Další výkonná technika umožňuje otestovat několik `Theory`hodnot najednou pomocí . Přidejte do třídy `TextUtils_GetWordCountShould` následující metodu. Máte dvě metody ve třídě po přidání této metody:

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

   Zkontroluje, `CountInstancesCorrectly` `GetWordCount` že metoda počítá správně. Poskytuje `InlineData` počet, hledané slovo a vstupní řetězec ke kontrole. Testovací metoda běží jednou pro každý řádek dat. Všimněte si znovu, že jste uplatnění `Assert.NotEqual`selhání nejprve pomocí , i když víte, že počty v datech jsou správné a že hodnoty odpovídají počty vrácené `GetWordCount` metodou. Provedení kroku selhání testu záměrně se může zdát jako ztráta času na první, ale kontrola logiky testu tím, že nejprve nepodaří, je důležitá kontrola logiky vašich testů. Když narazíte na testovací metodu, která projde, když očekáváte, že se nezdaří, našli jste chybu v logice testu. Stojí za to, aby tento krok při každém vytvoření zkušební metody.

1. Uložte soubor a spusťte testy znovu. Test skříně projde, ale tři počet testy nezdaří. Tento výsledek je přesně to, co očekáváte, že se stane.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac očekávané selhání testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Upravte `CountInstancesCorrectly` zkušební metodu změnou `Assert.NotEqual` na `Assert.Equal`. Uložte soubor. Spusťte testy znovu. Všechny testy jsou v pořádku.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac očekávané testovací průchody](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Přidání konzolové aplikace

1. V postranním panelu **Řešení** `WordCounter` klepněte se stisknutou klávesou Ctrl na řešení. Přidejte nový projekt **konzolové aplikace** výběrem šablony ze šablon **.NET Core** > **App.** Vyberte **další**. Pojmenujte projekt **WordCounterApp**. Vyberte **Vytvořit,** chcete-li vytvořit projekt v řešení.

1. Na postranním panelu **Řešení** klepněte se stisknutou klávesou **Ctrl** na uzel Závislosti nového projektu **WordCounterApp.** V dialogovém okně **Upravit odkazy** zaškrtněte **textutils** a vyberte **OK**.

1. Otevřete *soubor Program.cs.* Nahraďte kód následujícím kódem:

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/WordCounterApp/Program.cs)]

1. Se stisknutou `WordCounterApp` klávesou Ctrl na projekt a z kontextové nabídky vyberte **Spustit projekt.** Při spuštění aplikace zadejte hodnoty pro hledané slovo a vstupní řetězec na výzvy v okně konzoly. Aplikace označuje, kolikrát se hledané slovo zobrazí v řetězci.

   > [!div class="mx-imgBorder"]
   > ![Okno konzole Visual Studia pro Mac zobrazující spuštěnou aplikaci](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Poslední funkcí, kterou je třeba prozkoumat, je ladění pomocí Visual Studia for Mac. Nastavte zarážku `Console.WriteLine` na výpisu: Vyberte v levém okraji řádku 23 a zobrazí se červený kruh vedle řádku kódu. Případně vyberte libovolné místo na řádku kódu a z nabídky vyberte **Spustit** > **zaoknout zarážky.**

   > [!div class="mx-imgBorder"]
   > ![Sada zarážk a zarážky Visual Studia pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. se stisknutou `WordCounterApp` klávesou ctrl- na projekt. V místní nabídce vyberte **Spustit ladění projektu.** Když aplikace běží, zadejte hledané slovo "kočka" a "Pes honil kočku, ale kočka utekla." pro prohledání řetězce. Po `Console.WriteLine` dosažení příkazu se provádění programu zastaví před provedením příkazu. Na kartě **Locals** se `searchWord`zobrazí `inputString` `wordCount`hodnoty `pluralChar` , , a.

   > [!div class="mx-imgBorder"]
   > ![Spuštění programu ladicího programu sady Visual Studio for Mac bylo zastaveno](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. V podokně **Okamžité** zadejte "wordCount = 999;" a stiskněte Enter. Tento příkaz přiřadí hodnotu nesmysl 999 `wordCount` proměnné, která ukazuje, že při ladění můžete nahradit hodnoty proměnných.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pro Mac mění hodnoty v bezprostředním okně](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na panelu nástrojů klepněte na šipku *continue.* Podívejte se na výstup v okně konzoly. Hlásí nesprávnou hodnotu 999, kterou jste nastavili při ladění aplikace.

   > [!div class="mx-imgBorder"]
   > ![Tlačítko Pokračovat v Visual Studiu pro Mac na panelu nástrojů](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![Výstup okna konzoly Visual Studio pro Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Stejný proces můžete použít k ladění kódu pomocí projektu testování částí. Místo spuštění projektu aplikace WordCount klikněte se stisknutou klávesou Ctrl na projekt **Testovací knihovny** a z kontextové nabídky vyberte **Spustit ladění projektu.** Visual Studio pro Mac spustí testovací projekt s připojeným ladicím programem. Spuštění se zastaví na všechny zarážky, které jste přidali do testovacího projektu nebo základní kód knihovny.

## <a name="see-also"></a>Viz také

- [Zpráva k vydání verze pro Visual Studio 2019 pro Mac](/visualstudio/releasenotes/vs2019-mac-relnotes)
