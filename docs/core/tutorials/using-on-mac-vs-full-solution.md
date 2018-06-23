---
title: Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac
description: Toto téma vás provede procesem vytvoření .NET Core řešení, která obsahuje opakovaně použitelné knihovny a testování částí.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: f8dfbb712957d22e5b4aa16920e7b003a79c4444
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314695"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac

Visual Studio pro Mac poskytuje plné integrované vývojové prostředí (IDE) pro vývoj aplikací .NET Core. Toto téma vás provede procesem vytvoření .NET Core řešení, která obsahuje opakovaně použitelné knihovny a testování částí.

V tomto kurzu se dozvíte, jak vytvořit aplikaci, která přijímá slovo vyhledávání a řetězce textu od uživatele, spočítá počet hledaného slova se zobrazí v řetězci pomocí jiné metody v knihovny tříd a vrátí výsledek pro uživatele. Řešení obsahuje také jednotky testování pro knihovny tříd jako úvod do koncepty testy řízený vývoj (TDD). Pokud dáváte přednost pokračujte kurzu s ucelenou ukázku, stáhněte si [ukázkové řešení](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Vaše zpětná vazba je vysoce hodnot. Existují dva způsoby, kterými zajistíte názor na vývojový tým v sadě Visual Studio pro Mac:
> * V sadě Visual Studio pro Mac, vyberte **pomoci** > **nahlásit problém** z nabídky nebo **nahlásit problém** z úvodní obrazovky, který otevírá okno pro podání Sestava chyb. Svou zpětnou vazbu sledujte na portálu [komunity vývojářů](https://developercommunity.visualstudio.com/spaces/41/index.html).
> * Námět, vyberte **pomoci** > **poskytují zlepšení** z nabídky nebo **poskytují zlepšení** z úvodní obrazovky, který přejdete na [ Visual Studio pro webovou stránku Mac UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Požadavky

- OpenSSL (je-li spuštěna .NET Core 1.1): najdete v článku [požadavky pro .NET Core v systému Mac](../macos-prerequisites.md) tématu.
- [.NET core SDK 1.1 nebo novější](https://www.microsoft.com/net/core#macos)
- [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)

Další informace o požadovaných součástí najdete v tématu [požadavky pro .NET Core v systému Mac](../../core/macos-prerequisites.md). Požadavky úplnou Visual Studio 2017 pro Mac najdete v tématu [Visual Studio 2017 požadavky na systém Mac produktu rodiny](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Sestavení knihovny

1. Na úvodní obrazovce vyberte **nový projekt**. V **nový projekt** dialogové okno pod **Multiplatform** uzlu, vyberte **standardní knihovny .NET** šablony. Vyberte **Další**.

   ![Dialogové okno Nový projekt](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. Název projektu "TextUtils" (krátký název "Nástroje Text") a řešení "WordCounter". Nechte **vytvořte adresář projektu v adresáři řešení** zaškrtnutí. Vyberte **vytvořit**.

   ![Dialogové okno Nový projekt](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. V **řešení** bočním panelu, rozbalte `TextUtils` uzlu na nich soubor třídy definované šablonou, *Class1.cs*. Klikněte pravým tlačítkem na soubor, vyberte **přejmenovat** v místní nabídce a přejmenujte soubor *WordCount.cs*. Otevřete soubor a nahraďte obsah následujícím kódem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Uložte soubor pomocí některé z tři různé metody: použijte klávesovou zkratku <kbd> &#8984; </kbd> + <kbd>s</kbd>, vyberte **soubor**  >  **Uložit** z nabídky, nebo klikněte pravým tlačítkem na kartu a vyberte v souboru **Uložit** v kontextové nabídce. Následující obrázek znázorňuje okna IDE:

   ![Okno IDE zobrazuje TextUtils třídy knihovny, soubor třídy WordCount, statická třída WordCount a metoda GetWordCount](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Vyberte **chyby** u okraje v dolní části okna IDE otevřete **chyby** panelu. Vyberte **sestavení výstupu** tlačítko.

   ![Dolní okraj rozhraní IDE zobrazuje tlačítko chyby](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Vyberte **sestavení** > **sestavení všechny** z nabídky.

   Sestavení řešení. Panelu Výstup sestavení ukazuje, že sestavení byla úspěšně dokončena.

   ![Sestavení v podokně výstupu chyby panelu zobrazení zpráv úspěšné sestavení](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>Vytvoření projektu testů

Testování částí zadejte automatizované softwaru testování během vaší vývoje a publikování. Testování framework, který používáte v tomto kurzu je [xUnit (verze 2.2.0 nebo novější)](https://xunit.github.io/), který se nainstaluje automaticky při xUnit testovacího projektu je přidán do řešení v následujících krocích:

1. V **řešení** bočním panelu, klikněte pravým tlačítkem myši `WordCounter` řešení a vyberte **přidat** > **přidat nový projekt**.

1. V **nový projekt** dialogovém okně, vyberte **testy** z **.NET Core** uzlu. Vyberte **xUnit testovacího projektu** následuje **Další**.

   ![Dialogové okno Nový projekt vytváření xUnit testovacího projektu](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. Název nového projektu "TestLibrary" a vyberte **vytvořit**.

   ![Dialogové okno Nový projekt poskytuje název projektu](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. V pořadí pro knihovnu testu pro práci s `WordCount` třídy, přidejte odkaz na `TextUtils` projektu. V **řešení** bočním panelu, klikněte pravým tlačítkem na **závislosti** pod **TestLibrary**. Vyberte **upravit odkazy** v místní nabídce.

1. V **upravit odkazy** dialogovém okně, vyberte **TextUtils** projektu na **projekty** kartě. Vyberte **OK**.

   ![Odkazy na dialogové okno Upravit](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. V **TestLibrary** projektu, přejmenujte *UnitTest1.cs* do souboru *TextUtilsTests.cs*.

1. Otevřete soubor a nahraďte kód tímto:

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

   Následující obrázek ukazuje zavedené IDE kódem test jednotky. Věnovat pozornost `Assert.NotEqual` příkaz.

   ![Testování částí počáteční ke kontrole GetWordCount v hlavním okně IDE](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   Použití vývoje řízeného Testováním, je důležité zajistit nový test jednou nepodaří potvrďte správnost testování logiky pravidla. Metoda předá v názvu "Konektor" (velká písmena) a řetězec s "Konektor" a "konektor" (velká a malá písmena). Pokud `GetWordCount` metoda funguje správně, vrátí počet dvě instance hledaného slova. Chcete-li tento test se nezdaří s cílem, první implementaci testovací potvrzující, že nejsou vrácený dvě instance hledaného slova "Konektor" `GetWordCount` metoda. Pokračujte k dalšímu kroku s cílem selhání testu.

1. Otevřete **testování částí** panely na pravé straně obrazovky.

![Panel testy jednotek](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. Klikněte **ukotvení** ikonu na panelu nechat otevřené.

![Ikona ukotvení panelu testy jednotek](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. Klikněte **spustit všechny** tlačítko.
   
   Test se nezdaří, který je správný výsledek. Metodu test vyhodnotí této dvě instance `inputString`, "Jakub" nebudou zobrazeny z řetězce "Konektor konektoru" poskytované `GetWordCount` metoda. Vzhledem k tomu, že aplikace word velká a malá písmena byla odhlašování započítá `GetWordCount` metoda, jsou vráceny dvě instance. Kontrolní výraz který 2 *se nerovná* 2 selže. Toto je správný výsledek a je vhodný pro logiku našem testu.

   ![Test selhání](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Změnit `IgnoreCasing` test – metoda změnou `Assert.NotEqual` k `Assert.Equal`. Uložte soubor pomocí klávesové zkratky <kbd> &#8984; </kbd> + <kbd>s</kbd>, **soubor** > **Uložit** v nabídce nebo kliknete na kartu soubor pravým tlačítkem a vyberete **Uložit** v místní nabídce.

   Očekáváte, který `searchWord` "Konektor" vrátí dvě instance s `inputString` "Konektor konektoru" předaný do `GetWordCount`. Znovu spusťte test kliknutím **spuštění testů** tlačítko v **testování částí** panelu nebo **znovu spusťte testy** tlačítka na **výsledky testu** panelu v dolní části obrazovky. Test byl úspěšný. Existují dvě instance "Konektor" v řetězci "Konektor konektoru" (bez rozlišování velká a malá písmena) a je kontrolní test `true`.

   ![Průchodu testu](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. Testování jednotlivých návratové hodnoty s `Fact` je jenom začátek co můžete dělat s testování částí. Jiné výkonné technika umožňuje otestovat několik hodnoty najednou pomocí `Theory`. Přidejte následující metodu do vaší `TextUtils_GetWordCountShould` třídy. Máte dvě metody ve třídě, po přidání této metody:

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

   `CountInstancesCorrectly` Kontroluje, zda `GetWordCount` metoda počty správně. `InlineData` Poskytuje počet, word vyhledávání a vstupní řetězec ke kontrole. Metoda test se spustí jednou pro každý řádek dat. Ještě jednou Všimněte si, že jste se potvrzující selhání nejdřív pomocí `Assert.NotEqual`, i když víte, zda počty v datech jsou správná a že hodnoty odpovídat počtu vrácených `GetWordCount` metoda. Provádění krok selhání testu s cílem jevily jako plýtvání čas na první, ale kontrola logiku testu pomocí selhání ji nejdřív se důležité kontrola na logice testy. Pokud narazíte na testovací metodu, která bude provedeno úspěšně, pokud očekáváte nezdaří, nenajdete chyby v logice testu. Je vhodné úsilí provést tento krok pokaždé, když vytvoříte testovací metodu.
   
1. Uložte soubor a znovu spusťte testy. Předá velká a malá písmena test ale selže tři počet testů. Toto je přesně očekávat dojít.

   ![Test selhání](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Změnit `CountInstancesCorrectly` test – metoda změnou `Assert.NotEqual` k `Assert.Equal`. Uložte soubor. Znovu spusťte testy. Všechny testy byly úspěšné.

   ![Průchodu testu](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>Přidání konzolové aplikace

1. V **řešení** bočním panelu, klikněte pravým tlačítkem myši `WordCounter` řešení. Přidejte nový **konzolové aplikace** projektu výběrem šablony z **.NET Core** > **aplikace** šablony. Vyberte **Další**. Název projektu **WordCounterApp**. Vyberte **vytvořit** pro vytvoření projektu v řešení.

1. V **řešení** bočním panelu, klikněte pravým tlačítkem myši **závislosti** uzlu nové **WordCounterApp** projektu. V **upravit odkazy** dialogové okno, zkontrolujte **TextUtils** a vyberte **OK**.

1. Otevřete *Program.cs* souboru. Nahraďte kód tímto:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Spusťte aplikaci v okně konzoly namísto integrovaného vývojového prostředí, klikněte pravým tlačítkem `WordCounterApp` projekt, vyberte **možnosti**a otevřete **výchozí** pod uzlem **konfigurace**. Zaškrtněte políčko pro **spustit na externí konzoly**. Ponechte **pozastavit výstup konzoly** možnost zaškrtnutí. Toto nastavení způsobí, že spawn v okně konzoly, takže můžete zadat vstup pro aplikaci `Console.ReadLine` příkazy. Pokud necháte aplikaci spustit v prostředí IDE, lze zobrazit pouze výstup `Console.WriteLine` příkazy. `Console.ReadLine` příkazy v prostředí IDE nefungují **výstupu aplikace** panelu.

   ![Okno Možnosti projektu](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Aktuální verze sady Visual Studio pro Mac nemůže spustit testy, při spuštění řešení, proto konzolovou aplikaci můžete spustit přímo. Klikněte pravým tlačítkem na `WordCounterApp` projektu a vyberte **spustit položky** v místní nabídce. Pokud se uživatel pokusí spustit aplikaci s tlačítko Přehrát akci, test runner a aplikace se nepodaří spustit. Další informace o stavu pracovních na tento problém, naleznete v části [xunit/xamarinstudio.xunit (č. 60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Při spuštění aplikace, zadejte hodnoty pro vyhledávání word a vstupní řetězec na výzvy v okně konzoly. Aplikace určuje, kolikrát se objeví hledaného slova v řetězci.

   ![Okno konzoly zobrazující slovo olivy vyhledávat v řetězci: "Iro uje oliv podle jezera a olivy byly vynikající." Aplikace odpoví, "olivy word hledání se zobrazí 2 časy."](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. Poslední funkce chcete prozkoumat je ladění pomocí sady Visual Studio for Mac. Nastavit zarážky `Console.WriteLine` příkaz: vyberte v levém okraji řádku 23 a zobrazí červené kolečko zobrazí vedle řádek kódu. Na řádku kódu a vyberte, případně vyberte možnost kdekoli **spustit** > **Přepnout zarážku** z nabídky.

   ![Na řádku 23, příkaz Console.WriteLine je nastavena zarážka](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Klikněte pravým tlačítkem myši `WordCounterApp` projektu. Vyberte **spustit ladění položky** v místní nabídce. Při spuštění aplikace, zadejte hledání slovo "kočka" a "pes sledováno kočky, ale kočky uvozené." pro hledaný řetězec. Když `Console.WriteLine` příkaz je dosaženo, spuštění programu zastaví před provedením příkazu. V **místní hodnoty –** kartě, zobrazí se `searchWord`, `inputString`, `wordCount`, a `pluralChar` hodnoty.

   ![Spuštění programu byla zastavena v příkazu Console.WriteLine s místní okno s hodnotami okamžitě, před provedením příkazu Console.WriteLine.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. V **Immediate** podokně, zadejte "wordCount = 999;" a stiskněte klávesu Enter. Tím se přiřadí hodnota nesmysl 999 k `wordCount` proměnnou ukazující, že můžete nahradit hodnoty proměnné při ladění.

   ![Naše zarážek je přístupů. WordCount se změní na hodnotu 999 v příkazové podokno](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Na panelu nástrojů klikněte *pokračovat* šipku. Podívejte se na výstup v okně konzoly. Oznámí nesprávnou hodnotu 999, který jste nastavili při byly ladění aplikace.

   ![Pokračovat tlačítka na panelu nástrojů](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Počet slov vyhledávání se změní na hodnotu 999 ve výstupu aplikace](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a>Viz také:

[Visual Studio 2017 poznámky k verzi pro Mac](/visualstudio/releasenotes/vs2017-mac-relnotes)
