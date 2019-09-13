---
title: Testování .NET Standard knihovny tříd pomocí .NET Core v aplikaci Visual Studio 2017
description: Vytvořte projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, že vaše knihovna tříd .NET Core pracuje správně s testy jednotek.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: e8a0d28919d4d26e69fb5a5f926b0e96270a2407
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925892"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Testování knihovny .NET Standard pomocí platformy .NET Core v sadě Visual Studio 2017

V [sestavách knihovny .NET standard C# s a .NET Core v aplikaci Visual Studio 2017](library-with-visual-studio.md) nebo [sestavení knihovny .NET Standard pomocí Visual Basic a .NET core v aplikaci Visual Studio 2017](vb-library-with-visual-studio.md)jste vytvořili jednoduchou knihovnu tříd, která přidá metodu rozšíření do <xref:System.String> třída. Nyní vytvoříte test jednotky, abyste se ujistili, že funguje podle očekávání. Projekt testování částí přidáte do řešení, které jste vytvořili v předchozím článku.

## <a name="creating-a-unit-test-project"></a>Vytvoření projektu testu jednotek

Chcete-li vytvořit projekt testování částí, postupujte následovně:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. V **Průzkumník řešení**otevřete kontextovou nabídku uzlu řešení **ClassLibraryProjects** a vyberte **Přidat** > **Nový projekt**.

1. V dialogovém okně **Přidat nový projekt** vyberte uzel **vizuálu C#**  . Pak vyberte uzel **.NET Core** následovaný šablonou projektu **MSTest test (.NET Core)** . Do textového pole **název** zadejte "StringLibraryTest" jako název projektu. Vyberte **OK** a vytvořte tak projekt testování částí.

   ![Dialogové okno Přidat nový projekt s zobrazeným projektem testu jednotek –C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > Kromě testovacího projektu MSTest můžete také pomocí sady Visual Studio vytvořit projekt testů xUnit pro .NET Core.

1. Visual Studio vytvoří projekt a otevře soubor *UnitTest1.cs* v okně Code (kód).

   ![Okno Visual Studio Code pro třídu projektu testování částí a metodu –C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:

   * Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.

   * Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut `UnitTest1` na třídu. Každá testovací metoda v testovací třídě, která je označena\] atributem TestMethod, \[je provedena automaticky při spuštění testu jednotky.

   * Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` jako testovací metodu pro automatické provádění při spuštění testu jednotky.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a vyberte možnost **Přidat odkaz** z místní nabídky.

   ![Kontextová nabídka závislostí StringLibraryTest-C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary** . Vyberte tlačítko **OK**. Tím se přidá odkaz na váš projekt knihovny tříd, `StringLibrary`.

   ![Dialogová okna pro přidání odkazu na projekt v aplikaci Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. V **Průzkumník řešení**otevřete kontextovou nabídku uzlu řešení **ClassLibraryProjects** a vyberte **Přidat** > **Nový projekt**.

1. V dialogovém okně **Přidat nový projekt** vyberte uzel **Visual Basic** . Pak vyberte uzel **.NET Core** následovaný šablonou projektu **MSTest test (.NET Core)** . Do textového pole **název** zadejte "StringLibraryTest" jako název projektu. Vyberte **OK** a vytvořte tak projekt testování částí.

   ![Dialogové okno Přidat nový projekt s zobrazeným projektem testu jednotek – Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > Kromě testovacího projektu MSTest můžete také pomocí sady Visual Studio vytvořit projekt testů xUnit pro .NET Core.

1. Visual Studio vytvoří projekt a otevře soubor *UnitTest1. vb* v okně Code (kód).

   ![Okno Visual Studio Code pro třídu projektu testování částí a metodu-Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   Zdrojový kód vytvořený šablonou testu jednotky provede následující akce:

   * Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.

   * Aplikuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>atribut) `UnitTest1` na třídu. Každá testovací metoda v testovací třídě, která je označena atributem, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> je provedena automaticky při spuštění testu jednotky.

   * Použije <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` jako testovací metodu pro automatické provádění při spuštění testu jednotky.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a vyberte možnost **Přidat odkaz** z místní nabídky.

   ![Kontextová nabídka závislostí StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary** . Vyberte tlačítko **OK**. Tím se přidá odkaz na váš projekt knihovny tříd, `StringLibrary`.

   ![Dialogová okna pro přidání odkazu na projekt v aplikaci Visual Studio – Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)

---

## <a name="adding-and-running-unit-test-methods"></a>Přidávání a spouštění metod testování částí

Když aplikace Visual Studio spustí test jednotky, provede každou metodu označenou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem ve třídě testu jednotek, třída, na <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> kterou je atribut použit. Testovací metoda končí, když dojde k první chybě nebo když všechny testy obsažené v metodě byly úspěšné.

Nejběžnější testy volají členy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy. Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu. Některé z nejčastěji volaných metod jsou uvedeny v následující tabulce.

Metody Assert | Funkce
--- | ---
`Assert.AreEqual` | Ověřuje, zda jsou dvě hodnoty nebo objekty stejné. Pokud hodnoty nebo objekty nejsou stejné, vyhodnocení se nezdařilo.
`Assert.AreSame` | Ověřuje, že dvě proměnné objektu odkazují na stejný objekt. Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo.
`Assert.IsFalse` | Ověřuje, jestli je `false`podmínka. Pokud je `true`podmínka, vyhodnocení se nezdařilo.
`Assert.IsNotNull` | Ověřuje, že objekt `null`není. Pokud je `null`objekt, vyhodnocení se nezdařilo.

Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atribut na testovací metodu. Označuje typ výjimky. očekává se, že testovací metoda bude vyvolána. Test se nezdařil, pokud není vyvolána zadaná výjimka.

Při testování `StringLibrary.StartsWithUpper` metody je třeba zadat počet řetězců, které začínají velkým znakem. Očekáváte, že se metoda `true` vrátí v těchto případech, takže můžete <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> volat metodu. Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene. Očekáváte, že se metoda `false` vrátí v těchto případech, takže můžete <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> volat metodu.

Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný`String.Empty`řetězec ()](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky <xref:System.String.Length> a jehož hodnota je 0 `null` , a řetězec, který nebyl inicializované. Pokud `StartsWithUpper` je volána jako metoda rozšíření <xref:System.String> v instanci, nelze předat `null` řetězec. Můžete ji však také volat přímo jako statickou metodu a předat jeden <xref:System.String> argument.

Budete definovat tři metody, z nichž každá volá svou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodu opakovaně pro každý prvek v poli řetězců. Vzhledem k tomu, že testovací metoda selže, jakmile dojde k první chybě, zavoláte přetížení metody, které vám umožní předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.

Postup vytvoření testovacích metod:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. V okně *UnitTest1.cs* kód nahraďte kód následujícím kódem:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Všimněte si, že váš test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C) a test malých písmen `TestDoesNotStartWithUpper` v metodě zahrnuje řecký malý znak. Alpha (U + 03B1) a malé písmeno g (U + 0433).

1. Na řádku nabídek vyberte **soubor** > **Uložit UnitTest1.cs jako**. V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.

   ![Visual Studio uložit soubor jako dialog – dialogové oknoC#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. V okně kódu *UnitTest1. vb* nahraďte kód následujícím kódem:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Všimněte si, že váš test velkých písmen v `TestStartsWithUpper` metodě obsahuje řecké velké písmeno alfa (u + 0391) a velké písmeno cyrilice em (u + 041C) a test malých písmen `TestDoesNotStartWithUpper` v metodě zahrnuje řecký malý znak. Alpha (U + 03B1) a malé písmeno g (U + 0433).

1. Na panelu nabídek vyberte **soubor** > **Uložit UnitTest1. vb jako**. V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.

   ![Visual Studio uložit soubor jako dialog – Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

---

1. Kliknutím na tlačítko **Ano** v dialogovém okně **Potvrdit uložení jako** soubor uložte.

1. V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **kódování** znakovou **sadu Unicode (UTF-8 s podpisem 65001)** a vyberte **OK**.

   ![Dialogové okno Upřesnit možnosti uložení v aplikaci Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII. Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou přesné.

1. Na panelu nabídek vyberte možnost **test** > **Spustit** > **všechny testy**. Otevře se okno **Průzkumník testů** , ve kterém se zobrazí, že testy proběhly úspěšně. Tři testy jsou uvedeny v části **prošlé testy** a v části **Souhrn** se zobrazí výsledek testovacího běhu.

   ![Okno Průzkumníka testů s předáváním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Zpracování selhání testu

V testovacím běhu došlo k žádným chybám, ale mírně ho změňte, aby jedna z testovacích metod nebyla úspěšná:

1. `words` Upravte pole`TestDoesNotStartWithUpper` v metodě tak, aby obsahovalo řetězec "Error" (chyba). Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Spusťte test výběrem možnosti **test** > **Spustit** > **všechny testy** z řádku nabídek. Okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.

   ![Okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)

1. V části **nezdařené testy** vyberte neúspěšný test, `TestDoesNotStartWith`. V okně **Průzkumník testů** se zobrazí zpráva vytvořená pomocí kontrolního výrazu: Výraz Assert. NEPRAVDA se nezdařil. Očekávané pro ' error ': false; provedené True ". Z důvodu chyby nebyly testovány všechny řetězce v poli za "Error".

   ![Okno Průzkumníka testů, které zobrazuje nepravdivé selhání kontrolního výrazu](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Vraťte změny, které jste provedli v kroku 1, a odeberte řetězec "Error" (chyba). Spusťte test znovu a testy se budou předávat.

## <a name="testing-the-release-version-of-the-library"></a>Testování verze pro vydání knihovny

Spustili jste testy pro ladicí verzi knihovny. Nyní, když testy úspěšně prošly a jste dostatečně otestovali knihovnu, měli byste spustit testy dodatečně na sestavení vydaných verzí knihovny. Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.

Testování sestavení pro vydání:

1. Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.

   ![Panel nástrojů sady Visual Studio s zvýrazněným sestavením pro vydání](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.

   ![Místní nabídka StringLibrary s příkazem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Spusťte testy jednotek výběrem možnosti **test** > **Spustit** > **všechny testy** z řádku nabídek. Testy jsou passované.

Teď, když jste dokončili testování knihovny, je dalším krokem zpřístupnění volajícím. Můžete ho seskupit s jednou nebo více aplikacemi nebo ho můžete distribuovat jako balíček NuGet. Další informace naleznete v tématu [spotřebovávání knihovny tříd .NET Standard](./consuming-library-with-visual-studio.md).
