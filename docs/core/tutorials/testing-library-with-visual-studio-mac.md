---
title: Otestování .NET Standard knihovny tříd pomocí .NET Core s využitím Visual Studio pro Mac
description: Vytvoří projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 06/08/2020
ms.openlocfilehash: d3c8a5e01d16047949e977f3af6a429970d996d0
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359217"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a>Testování knihovny tříd .NET Standard pomocí .NET Core pomocí sady Visual Studio

V tomto kurzu se dozvíte, jak automatizovat testování částí přidáním testovacího projektu do řešení.

## <a name="prerequisites"></a>Předpoklady

- Tento kurz spolupracuje s řešením, které vytvoříte v části [Vytvoření knihovny .NET Standard pomocí Visual Studio pro Mac](library-with-visual-studio-mac.md).

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí

Testy jednotek poskytují automatizované softwarové testování během vývoje a publikování. [MSTest](https://github.com/Microsoft/testfx-docs) je jedna ze tří testovacích rozhraní, ze kterých si můžete vybrat. Ostatní jsou [xUnit](https://xunit.net/) a [nUnit](https://nunit.org/).

1. Spusťte Visual Studio pro Mac.

1. Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v části [vytvoření knihovny .NET Standard pomocí Visual Studio pro Mac](library-with-visual-studio-mac.md).

1. Na panelu **řešení** <kbd>klikněte na</kbd> `ClassLibraryProjects` řešení a vyberte **Přidat**  >  **Nový projekt**.

1. V dialogovém okně **Nový projekt** vyberte možnost **testy** z uzlu **web a konzola** . Vyberte **projekt MSTest** a potom klikněte na tlačítko **Další**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Visual Studio – nový projekt – dialogové okno pro vytvoření testovacího projektu":::

1. Vyberte **.NET Core 3,1**. Pojmenujte nový projekt "StringLibraryTest" a vyberte **vytvořit**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Visual Studio Mac – dialog nového projektu zadání názvu projektu":::

   Visual Studio vytvoří soubor třídy s následujícím kódem:

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

   Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.
   - Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut na `UnitTest1` třídu.
   - Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut na `TestMethod1` .

   Každá metoda označená pomocí [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) v testovací třídě s označením [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) je provedena automaticky při spuštění testu jednotky.

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Aby projekt testu spolupracoval s `StringLibrary` třídou, přidejte odkaz na `StringLibrary` projekt.

1. Na panelu **řešení** klikněte v části **StringLibraryTest**na **závislosti** <kbd>CTRL</kbd>. V místní nabídce vyberte **Přidat odkaz** .

1. V dialogovém okně **odkazy** vyberte projekt **StringLibrary** . Vyberte **OK**.

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Dialogové okno Visual Studio Mac Edit References":::

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

1. Otevřete soubor *UnitTest1.cs* a nahraďte kód následujícím kódem:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C). Test malých písmen v `TestDoesNotStartWithUpper` metodě obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433).

1. V řádku nabídek vyberte **soubor**  >  **Uložit jako**. V dialogovém okně se ujistěte, že je **kódování** nastaveno na **kódování Unicode (UTF-8)**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio uložit soubor jako dialog":::

1. Až se zobrazí dotaz, jestli chcete nahradit existující soubor, vyberte **nahradit**.

   Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII. Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou správné.

1. Otevřete panel **testování částí** na pravé straně obrazovky. V nabídce vyberte **Zobrazit**  >  **testy** .

1. Kliknutím na ikonu **Dock (ukotvit** ) ponechejte panel otevřený.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Ikona ukotvení panelu Visual Studio pro Mac testování částí":::

1. Klikněte na tlačítko **Spustit vše** .

   Všechny testy jsou passované.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio pro Mac očekávanou zkušební průchody":::

## <a name="handle-test-failures"></a>Zpracování selhání testu

Pokud pracujete s vývojem řízeným testováním (TDD), napíšete nejprve testy a při jejich prvním spuštění dojde k chybě. Potom do aplikace přidáte kód, který provede test úspěšně. Pro tento kurz jste vytvořili test po zápisu kódu aplikace, který ověřuje, takže jste neviděli test neúspěšný. Chcete-li ověřit, že test selže, pokud očekáváte, že selže, přidejte do vstupu testu neplatnou hodnotu.

1. Upravte `words` pole v `TestDoesNotStartWithUpper` metodě tak, aby obsahovalo řetězec "Error" (chyba). Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Spusťte testy znovu.

   Tentokrát okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Okno Průzkumníka testů s neúspěšnými testy":::

1. <kbd>stiskněte klávesu CTRL</kbd>a klikněte na neúspěšný test `TestDoesNotStartWithUpper` a v místní nabídce vyberte možnost **Zobrazit panel výsledků** .

   Na panelu **výsledků** se zobrazí zpráva vytvořená kontrolním výrazem: Assert. NEPRAVDA. Očekávané pro ' error ': false; skutečnost: true ". Z důvodu chyby nejsou v poli Po otestování "Error" žádné řetězce.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="Okno Průzkumníka testů znázorňující chybu kontrolního výrazu NEPRAVDA":::

1. Odeberte řetězec "Error", který jste přidali v kroku 1. Spusťte test znovu a testy proběhnou znovu.

## <a name="test-the-release-version-of-the-library"></a>Testování verze pro vydání knihovny

Nyní, když testy úspěšně prošly při spuštění sestavení ladění knihovny, spusťte testy dodatečně k sestavení vydání knihovny. Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.

Testování sestavení pro vydání:

1. Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Panel nástrojů sady Visual Studio s zvýrazněným sestavením pro vydání":::

1. Na panelu **řešení** klikněte v nabídce <kbd>CTRL</kbd>na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Místní nabídka StringLibrary s příkazem Build":::

1. Znovu spusťte testy jednotek.

   Testy jsou passované.

## <a name="debug-tests"></a>Ladit testy

Můžete použít stejný postup jako v [kurzu: ladění konzolové aplikace .NET Core pomocí Visual Studio pro Mac](debugging-with-visual-studio-mac.md) pro ladění kódu pomocí projektu testování částí. Místo spuštění projektu <kbd>aplikace pro</kbd>selektory klikněte v místní nabídce na projekt **StringLibraryTests** a vyberte **Spustit ladění projektu** . Visual Studio spustí testovací projekt pomocí připojeného ladicího programu. Spuštění se zastaví na všech zarážekch, které jste přidali do testovacího projektu, nebo na podkladový kód knihovny.

## <a name="additional-resources"></a>Další zdroje

* [Testování částí v .NET Core a .NET Standard](../testing/index.md)

## <a name="next-steps"></a>Další kroky

V tomto kurzu testujete jednotku knihovny tříd. Knihovnu můžete zpřístupnit ostatním tím, že ji publikujete do [NuGet](https://nuget.org) jako balíček. Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:

> [!div class="nextstepaction"]
> [Vytvoření a publikování balíčku (rozhraní příkazového řádku dotnet)](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

Pokud knihovnu publikujete jako balíček NuGet, můžou ji nainstalovat a používat i ostatní. Pokud se chcete dozvědět, jak postupovat, postupujte podle kurzu NuGet:

> [!div class="nextstepaction"]
> [Instalace a použití balíčku v Visual Studio pro Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

Knihovna nemusí být distribuována jako balíček. Dá se seskupit pomocí konzolové aplikace, která ho používá. Informace o tom, jak publikovat konzolovou aplikaci, najdete v předchozím kurzu v této sérii:

> [!div class="nextstepaction"]
> [Publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac](publishing-with-visual-studio-mac.md)
