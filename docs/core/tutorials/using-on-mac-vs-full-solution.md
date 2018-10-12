---
title: Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede sestavení řešení .NET Core, která obsahuje opakovaně použitelné knihovny a testování částí.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: 589b3e72f7e8425051a96f66f07f24327d273c45
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122817"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio for Mac obsahuje plně vybavené integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Toto téma vás provede sestavení řešení .NET Core, která obsahuje opakovaně použitelné knihovny a testování částí.

V tomto kurzu se dozvíte, jak vytvořit aplikaci, která přijímá hledaným slovem a řetězce textu od uživatele, se počítá počet, kolikrát hledaným slovem se zobrazí v řetězci pomocí jiné metody v knihovně tříd a vrátí výsledek pro uživatele. Toto řešení zahrnuje také testování jednotek pro knihovny tříd jako úvod do testování konceptů. Pokud budete chtít pokračovat v průběhu kurzu s úplnou ukázku, stáhněte si [ukázkové řešení](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Vaše zpětná vazba je vysoce Vážíme si toho. Existují dva způsoby, jak můžete poskytnout zpětnou vazbu vývojovému týmu sady Visual Studio pro Mac:
> * V sadě Visual Studio pro Mac, vyberte **pomáhají** > **nahlásit problém** z nabídky nebo **nahlásit problém** na úvodní obrazovce, která se otevře okno podání hlášení o chybě. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html).
> * Máte nějaký návrh, vyberte **pomáhají** > **poslat návrh** z nabídky nebo **poslat návrh** na úvodní obrazovce, která přejde na [ Visual Studio pro webovou stránku Mac UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Požadavky

- OpenSSL (je-li spuštěna .NET Core 1.1): najdete v článku [předpoklady pro .NET Core v počítačích Mac](../macos-prerequisites.md) tématu.
- [.NET core SDK 1.1 nebo vyšší](https://www.microsoft.com/net/core#macos)
- [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)

Další informace o požadavky najdete v článku [předpoklady pro .NET Core v počítačích Mac](../../core/macos-prerequisites.md). Úplné systémové požadavky sady Visual Studio 2017 pro Mac, najdete v části [Visual Studio 2017 for Mac produktová řada požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Vytváření knihovny

1. Na úvodní obrazovce vyberte **nový projekt**. V **nový projekt** dialogového okna v části **Multiplatformní** uzlu, vyberte **knihovna .NET Standard** šablony. Tím se vytvoří knihovny .NET Standard, který cílí na .NET Core stejně jako jiné implementace .NET, která podporuje verzi 2.0 [.Net Standard](https://docs.microsoft.com/en-us/dotnet/standard/net-standard). Vyberte **Další**.

   ![Dialogové okno nového projektu](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. Pojmenujte projekt "TextUtils" (krátký název pro "Nástroje Text") a řešení "WordCounter". Ponechte **vytvořit adresář projektu v adresáři řešení** zaškrtnuto. Vyberte **vytvořit**.

   ![Dialogové okno nového projektu](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. V **řešení** postranního panelu, rozbalte `TextUtils` uzel zobrazí soubor třídy poskytovanou šablonou, *Class1.cs*. Klikněte pravým tlačítkem na soubor, vyberte **přejmenovat** v místní nabídce a přejmenujte soubor na *WordCount.cs*. Otevřete soubor a nahraďte obsah následujícím kódem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Uložte soubor pomocí některé z třemi způsoby: použijte klávesovou zkratku <kbd> &#8984; </kbd> + <kbd>s</kbd>vyberte **souboru**  >  **Uložit** z nabídky, nebo klikněte pravým tlačítkem na kartu souboru a vyberte **Uložit** z kontextové nabídky. Následující obrázek ukazuje okno integrovaného vývojového prostředí:

   ![Okno integrovaného vývojového prostředí TextUtils třídy knihovny, soubor třídy WordCount, statické třídy WordCount a GetWordCount – metoda](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Vyberte **chyby** na okraji v dolní části okna integrovaného vývojového prostředí, které otevřete **chyby** panelu. Vyberte **výstupu sestavení** tlačítko.

   ![Dolní okraj IDE zobrazuje tlačítko chyby](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Vyberte **sestavení** > **sestavení všechny** z nabídky.

   Řešení je sestaveno. Panel výstupu sestavení ukazuje úspěšném dokončení sestavení.

   ![Vytvořit výstupní podokna panelu chyby zobrazení zprávy úspěšné sestavení](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>Vytvoření testovacího projektu

Testování částí poskytuje software automatizované testování během vývoje a publikování. Testovací rozhraní, který používáte v tomto kurzu je [xUnit (verze 2.2.0 nebo novější)](https://xunit.github.io/), který se nainstaluje automaticky při projekt testů xUnit je přidán do řešení v následujících krocích:

1. V **řešení** postranního panelu, klikněte pravým tlačítkem myši `WordCounter` řešení a vyberte **přidat** > **přidat nový projekt**.

1. V **nový projekt** dialogového okna, vyberte **testy** z **.NET Core** uzlu. Vyberte **projekt testů xUnit** následovaný **Další**.

   ![Dialogové okno nového projektu vytvořit projekt testů xUnit](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. Zadejte název nového projektu "TestLibrary" a vyberte **vytvořit**.

   ![Dialogové okno Nový projekt poskytuje název projektu](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. V pořadí pro knihovnu testu pro práci s `WordCount` třídy, přidejte odkaz na `TextUtils` projektu. V **řešení** postranního panelu, klikněte pravým tlačítkem na **závislosti** pod **TestLibrary**. Vyberte **upravit odkazy** v místní nabídce.

1. V **upravit odkazy** dialogového okna, vyberte **TextUtils** projekt **projekty** kartu. Vyberte **OK**.

   ![Odkazy na dialogové okno Upravit](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. V **TestLibrary** projektu, přejmenovat *UnitTest1.cs* do souboru *TextUtilsTests.cs*.

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

   Následující obrázek ukazuje integrované vývojové prostředí s kódu testování částí na místě. Věnujte pozornost `Assert.NotEqual` příkazu.

   ![Počáteční Jednotkový test ke kontrole GetWordCount v hlavním okně integrovaného vývojového prostředí](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   Je důležité, aby nového testu po selhání potvrďte, že se že jeho testování logika je správný. Metoda předává název "Jan" (velká písmena) a řetězec "Jan" a "Jan" (velká a malá písmena). Pokud `GetWordCount` metoda pracuje správně, vrátí počet dvě instance s hledaným slovem. Pokud chcete tento test záměrně selžou, nejprve implementujete test potvrzující, že se dvě instance s hledaným slovem "Jan" vrácené `GetWordCount` metody. Pokračujte k dalšímu kroku záměrně selhání testu.

1. Otevřít **testování částí** panel na pravé straně obrazovky.

   ![Panel testy jednotek](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. Klikněte na tlačítko **Dock** ikonu panelu nechat otevřené.

   ![Ikona ukotvení panelu testy jednotek](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. Klikněte na tlačítko **spustit všechny** tlačítko.

   Test se nezdaří, což je správný výsledek. Testovací metoda uplatňuje této dvě instance `inputString`, "Jan", nebudou zobrazeny z řetězce "Konektor jack" k dispozici na `GetWordCount` metoda. Protože slov velká a malá písmena se dostaneme out `GetWordCount` metody, jsou vráceny dvě instance. Výraz, který 2 *není roven* 2 selže. Toto je správný výsledek a logiku testovacím je dobrá.

   ![Selhání testu](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Upravit `IgnoreCasing` testovací metoda tak, že změníte `Assert.NotEqual` k `Assert.Equal`. Uložte soubor pomocí klávesové zkratky <kbd> &#8984; </kbd> + <kbd>s</kbd>, **souboru** > **Uložit** v nabídce nebo na kartě soubor pravým tlačítkem myši a vyberete **Uložit** v místní nabídce.

   Můžete očekávat, že `searchWord` "Jan" vrátí dvě instance s `inputString` "Jan jack" předán `GetWordCount`. Znovu spusťte test kliknutím **spustit testy** tlačítko **testování částí** panelu nebo **znovu spustit testy** tlačítko v **výsledky testu** panel v dolní části obrazovky. Test byl úspěšný. Existují dvě instance "Jan" v řetězci "Jan jack" (bez rozlišování malých a velkých písmen) a je kontrolní výraz test `true`.

   ![Průchod testu](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. Testování jednotlivých návratové hodnoty `Fact` je jenom začátek můžete dělat s testováním částí. Další efektivní technikou využijete k otestování několik hodnot současně pomocí `Theory`. Přidejte následující metodu do vaší `TextUtils_GetWordCountShould` třídy. Máte dvě metody ve třídě po přidání této metody:

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

   `CountInstancesCorrectly` Kontroluje, zda `GetWordCount` metoda správně vrátí. `InlineData` Poskytuje počet hledaným slovem a vstupní řetězec ke kontrole. Testovací metody spustí jednou pro každý řádek dat. Znovu Upozorňujeme, že jste už uplatnění selhání nejprve s použitím `Assert.NotEqual`, i když víte, že jsou správné počty v datech a, hodnoty odpovídají počtu vrácených `GetWordCount` metody. Provádí se krok záměrně selháním testu může jevit plýtvání čas první, ale Kontrola logiky testu pomocí služeb při selhání se nejdřív je důležité kontrolu na logiku testy. Pokud narazíte na testovací metodu, která úspěšný, pokud očekáváte, že selhala, našli jste chybu v logice testu. Je vhodné úsilí, abyste mohli tento krok pokaždé, když vytváříte testovací metody.

1. Uložte soubor a znovu spusťte testy. Velká a malá písmena test úspěšný, ale selže tři počet testů. To je přesně to co očekáváte, které se provedou.

   ![Selhání testu](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Upravit `CountInstancesCorrectly` testovací metoda tak, že změníte `Assert.NotEqual` k `Assert.Equal`. Uložte soubor. Spusťte testy znovu. Všechny testy byly úspěšné.

   ![Průchod testu](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>Přidává se aplikace konzoly

1. V **řešení** postranního panelu, klikněte pravým tlačítkem myši `WordCounter` řešení. Přidat nový **konzolovou aplikaci** výběrem šablony z projektu **.NET Core** > **aplikace** šablony. Vyberte **Další**. Pojmenujte projekt **WordCounterApp**. Vyberte **vytvořit** pro vytvoření projektu v řešení.

1. V **řešení** postranního panelu, klikněte pravým tlačítkem na **závislosti** uzlu nového **WordCounterApp** projektu. V **upravit odkazy** dialogové okno Kontrola **TextUtils** a vyberte **OK**.

1. Otevřít *Program.cs* souboru. Nahraďte kód následujícím kódem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Spuštění aplikace v okně konzoly namísto rozhraní IDE, klikněte pravým tlačítkem myši `WordCounterApp` projekt, vyberte **možnosti**a otevřete **výchozí** pod uzlem **konfigurace**. Zaškrtněte políčko u **spouštět na externí konzole**. Nechte **pozastavit výstup konzoly** zaškrtnutým políčkem. Toto nastavení způsobí, že aplikace nejde vytvořit podřízený v okně konzoly tak, že zadáte pro vstup `Console.ReadLine` příkazy. Ponecháte-li aplikaci pro spuštění v integrovaném vývojovém prostředí, můžete jenom zobrazit výstup `Console.WriteLine` příkazy. `Console.ReadLine` příkazy v rozhraní IDE nefungují **výstup aplikace** panelu.

   ![Okno Možnosti projektu](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Protože testy nemůžete spustit aktuální verzi sady Visual Studio pro Mac, při spuštění řešení, spustíte aplikaci konzoly přímo. Klikněte pravým tlačítkem na `WordCounterApp` projektu a vyberte **spustit položky** v místní nabídce. Při pokusu o spuštění aplikace s tlačítko Přehrát, nástroj test runner a aplikace nezdaří spustit. Další informace o stavu práce na tento problém, naleznete v tématu [xunit/xamarinstudio.xunit (60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Při spuštění aplikace, zadejte hodnoty pro vstupní řetězec na vyzvání v okně konzoly a hledaným slovem. Aplikace udává, že počet pokusů, které se zobrazí hledaným slovem v řetězci.

   ![Okna konzoly zobrazuje slovo oliv vyhledávat v řetězci: "Iro snědli oliv podle jezera a oliv byly vynikající." Aplikace reaguje, "oliv word search se zobrazí časy 2."](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. Poslední funkci k prozkoumání je ladění pomocí sady Visual Studio pro Mac. Nastavit zarážku na `Console.WriteLine` – příkaz: vyberte levý okraj řádku 23, a zobrazí červené kolečko vedle řádku kódu. Alternativně klikněte kamkoli na řádek kódu a vyberte **spustit** > **Přepnout zarážku** z nabídky.

   ![Nastavit zarážku na řádku 23, příkaz Console.WriteLine](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Klikněte pravým tlačítkem myši `WordCounterApp` projektu. Vyberte **spustit ladění položky** v místní nabídce. Při spuštění aplikace hledání zadejte slovo "cat" a "pes sledováno kočky, ale kočky uvozeny řídicími znaky." pro hledaný řetězec. Když `Console.WriteLine` je dosažen příkaz, zastaví spuštění programu před provedením příkazu. V **lokální** kartě, zobrazí se `searchWord`, `inputString`, `wordCount`, a `pluralChar` hodnoty.

   ![Spuštění programu byla zastavena v příkazu Console.WriteLine s místní okno zobrazuje hodnoty bezprostředně před provedením příkazu Console.WriteLine.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. V **okamžité** podokně, zadejte "wordCount = 999;" a stiskněte klávesu Enter. Toto přiřadí hodnotu nesmysl 999 k `wordCount` proměnné znázorňující, že při ladění můžete nahradit hodnoty proměnných.

   ![Naše zarážkou. WordCount se změní na hodnotu 999 do okna Příkazy](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Na panelu nástrojů klikněte na tlačítko *pokračovat* šipku. Podívejte se na výstup v okně konzoly. Oznámí nesprávnou hodnotu 999, které jste nastavili při byly ladění aplikace.

   ![Pokračovat tlačítko na panelu nástrojů](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Počet slov vyhledávání se změní na hodnotu 999 ve výstupu aplikace](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a>Viz také:

* [Visual Studio 2017 for Mac zpráva k vydání verze](/visualstudio/releasenotes/vs2017-mac-relnotes)
