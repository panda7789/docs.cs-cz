---
title: Testování knihovny tříd .NET Standard pomocí .NET Core pomocí sady Visual Studio
description: Vytvoří projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 049f0636b1c2c2df33461714aea5a11810ef00ad
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359191"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio"></a>Kurz: testování .NET Standard knihovny tříd pomocí .NET Core pomocí sady Visual Studio

V tomto kurzu se dozvíte, jak automatizovat testování částí přidáním testovacího projektu do řešení.

## <a name="prerequisites"></a>Předpoklady

- Tento kurz spolupracuje s řešením, které vytvoříte v části [Vytvoření knihovny .NET Standard pomocí sady Visual Studio](library-with-visual-studio.md).

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí

Testy jednotek poskytují automatizované softwarové testování během vývoje a publikování. [MSTest](https://github.com/Microsoft/testfx-docs) je jedna ze tří testovacích rozhraní, ze kterých si můžete vybrat. Ostatní jsou [xUnit](https://xunit.net/) a [nUnit](https://nunit.org/).

1. Spusťte Visual Studio.

1. Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v části [vytvoření knihovny .NET Standard pomocí sady Visual Studio](library-with-visual-studio.md).

1. Přidejte do řešení nový projekt testování částí s názvem "StringLibraryTest".

   1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **MSTest** . V seznamu jazyk vyberte **C#** nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem.

   1. Zvolte šablonu **projekt testů MSTest (.NET Core)** a klikněte na tlačítko **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibraryTest** . Potom zvolte **Create** (Vytvořit).

1. Visual Studio vytvoří projekt a otevře soubor třídy v okně Code (kód) s následujícím kódem. Pokud jazyk, který chcete použít, není zobrazen, změňte selektor jazyka v horní části stránky.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.
   - Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut na `UnitTest1` třídu.
   - Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` v jazyce C# nebo `TestSub` v Visual Basic.

   Každá metoda označená pomocí [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) v testovací třídě s označením [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) je provedena automaticky při spuštění testu jednotky.

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Aby projekt testu spolupracoval s `StringLibrary` třídou, přidejte odkaz do projektu **StringLibraryTest** do `StringLibrary` projektu.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a v místní nabídce vyberte **Přidat odkaz na projekt** .

1. V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary** při kompilování projektu **StringLibraryTest** .

1. Vyberte **OK**.

## <a name="add-and-run-unit-test-methods"></a>Přidat a spustit metody testování částí

Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě, která je označena  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atributem. Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.

Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy. Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu. `Assert`V následující tabulce jsou uvedeny některé často volané metody třídy:

| Metody Assert     | Funkce |
| ------------------ | -------- |
| `Assert.AreEqual`  | Ověřuje, zda jsou dvě hodnoty nebo objekty stejné. Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují. |
| `Assert.AreSame`   | Ověřuje, že dvě proměnné objektu odkazují na stejný objekt. Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo. |
| `Assert.IsFalse`   | Ověřuje, jestli je podmínka `false` . Pokud je podmínka, vyhodnocení se nezdařilo `true` . |
| `Assert.IsNotNull` | Ověřuje, že objekt není `null` . Pokud je objekt, vyhodnocení se nezdařilo `null` . |

Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metodu v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána. Test se nezdařil, pokud není vyvolána zadaná výjimka.

Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem. Očekáváte, že se metoda vrátí `true` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodu. Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene. Očekáváte, že se metoda vrátí `false` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodu.

Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec ( `String.Empty` )](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky a jehož <xref:System.String.Length> hodnota je 0, a `null` řetězec, který nebyl inicializován. Můžete zavolat `StartsWithUpper` přímo jako statickou metodu a předat jeden <xref:System.String> argument. Nebo můžete zavolat `StartsWithUpper` jako metodu rozšíření pro `string` proměnnou přiřazenou k `null` .

Budete definovat tři metody, z nichž každá volá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu pro každý prvek v poli řetězců. Zavoláte přetížení metody, které vám umožní zadat chybovou zprávu, která se zobrazí v případě selhání testu. Zpráva identifikuje řetězec, který způsobil chybu.

Postup vytvoření testovacích metod:

1. V okně kódu *UnitTest1.cs* nebo *UnitTest1. vb* nahraďte kód následujícím kódem:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   Test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C). Test malých písmen v `TestDoesNotStartWithUpper` metodě obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433).

1. Na panelu nabídek vyberte **soubor**  >  **Uložit UnitTest1.cs jako** nebo **soubor**  >  **Uložit UnitTest1. vb jako**. V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio uložit soubor jako dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. Kliknutím na tlačítko **Ano** v dialogovém okně **Potvrdit uložení jako** soubor uložte.

1. V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **kódování** znakovou **sadu Unicode (UTF-8 s podpisem 65001)** a vyberte **OK**.

   > [!div class="mx-imgBorder"]
   > ![Dialogové okno Upřesnit možnosti uložení v aplikaci Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII. Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou správné.

1. Na panelu nabídek vyberte možnost **test**  >  **Spustit všechny testy**. Pokud okno **Průzkumník testů** není otevřené, otevřete ho výběrem **test**  >  **Test Explorer**. Tři testy jsou uvedeny v části **prošlé testy** a v části **Souhrn** se zobrazí výsledek testovacího běhu.

   > [!div class="mx-imgBorder"]
   > ![Okno Průzkumníka testů s předáváním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Zpracování selhání testu

Pokud pracujete s vývojem řízeným testováním (TDD), napíšete nejprve testy a při jejich prvním spuštění dojde k chybě. Potom do aplikace přidáte kód, který provede test úspěšně. Pro tento kurz jste vytvořili test po zápisu kódu aplikace, který ověřuje, takže jste neviděli test neúspěšný. Chcete-li ověřit, že test selže, pokud očekáváte, že selže, přidejte do vstupu testu neplatnou hodnotu.

1. Upravte `words` pole v `TestDoesNotStartWithUpper` metodě tak, aby obsahovalo řetězec "Error" (chyba). Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Spusťte test výběrem možnosti **test**  >  **Spustit všechny testy** z řádku nabídek. Okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.

   > [!div class="mx-imgBorder"]
   > ![Okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Vyberte neúspěšný test `TestDoesNotStartWith` .

   V okně **Průzkumník testů** se zobrazí zpráva vytvořená kontrolním výrazem: Assert. NEPRAVDA. Očekávané pro ' error ': false; skutečnost: true ". Z důvodu chyby nejsou v poli Po otestování "Error" žádné řetězce.

   > [!div class="mx-imgBorder"]
   > ![Okno Průzkumníka testů znázorňující chybu kontrolního výrazu NEPRAVDA](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Odeberte řetězec "Error", který jste přidali v kroku 1. Spusťte test znovu a testy proběhnou znovu.

## <a name="test-the-release-version-of-the-library"></a>Testování verze pro vydání knihovny

Nyní, když testy úspěšně prošly při spuštění sestavení ladění knihovny, spusťte testy dodatečně k sestavení vydání knihovny. Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.

Testování sestavení pro vydání:

1. Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.

   > [!div class="mx-imgBorder"]
   > ![Panel nástrojů sady Visual Studio s zvýrazněným sestavením pro vydání](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.

   > [!div class="mx-imgBorder"]
   > ![Místní nabídka StringLibrary s příkazem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Spusťte testy jednotek výběrem možnosti **test spustit**  >  **všechny testy** z řádku nabídek. Testy jsou passované.

## <a name="additional-resources"></a>Další zdroje

* [Základy testování částí – Visual Studio](/visualstudio/test/unit-test-basics)
* [Testování částí v .NET Core a .NET Standard](../testing/index.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu testujete jednotku knihovny tříd. Knihovnu můžete zpřístupnit ostatním tím, že ji publikujete do [NuGet](https://nuget.org) jako balíček. Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:

> [!div class="nextstepaction"]
> [Vytvoření a publikování balíčku NuGet pomocí sady Visual Studio](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

Pokud knihovnu publikujete jako balíček NuGet, můžou ji nainstalovat a používat i ostatní. Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:

> [!div class="nextstepaction"]
> [Instalace a použití balíčku v aplikaci Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

Knihovna nemusí být distribuována jako balíček. Dá se seskupit pomocí konzolové aplikace, která ho používá. Informace o tom, jak publikovat konzolovou aplikaci, najdete v předchozím kurzu v této sérii:

> [!div class="nextstepaction"]
> [Publikování konzolové aplikace .NET Core pomocí sady Visual Studio](publishing-with-visual-studio.md)
