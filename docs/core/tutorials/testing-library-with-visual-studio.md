---
title: Testování knihovny tříd .NET Standard s jádrem .NET v sadě Visual Studio
description: Vytvořte projekt testování částí pro knihovnu tříd .NET Core. Ověřte, zda knihovna tříd .NET Core funguje správně s testy částí.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156618"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Testování knihovny .NET Standard s jádrem .NET v sadě Visual Studio

V [části Sestavení knihovny .NET Standard v sadě Visual Studio](library-with-visual-studio.md)jste <xref:System.String> vytvořili jednoduchou knihovnu tříd, která do třídy přidá metodu rozšíření. Nyní vytvoříte test částí a ujistěte se, že funguje podle očekávání. Přidáte projekt testování částí do řešení, které jste vytvořili v předchozím článku.

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí

Chcete-li vytvořit projekt testování částí, postupujte takto:

1. Otevřete `ClassLibraryProjects` řešení, které jste vytvořili v článku [Sestavení a standardní knihovny .NET v sadě Visual Studio.](library-with-visual-studio.md)

1. Přidejte do řešení nový projekt testování částí s názvem "StringLibraryTest".

   1. Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **mstest.** V seznamu Jazyk zvolte **C#** nebo **Visual Basic** a pak ze seznamu Platforma zvolte **Všechny platformy.** Zvolte šablonu **Testovací projekt MsTest (.NET Core)** a pak zvolte **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte **StringLibraryTest** do pole **Název projektu.** Potom zvolte **Create** (Vytvořit).

   > [!NOTE]
   > Kromě MSTest, můžete také vytvořit xUnit a nUnit testovací projekty pro .NET Core v sadě Visual Studio.

1. Visual Studio vytvoří projekt a otevře soubor třídy v okně kódu s následujícím kódem:

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

   Zdrojový kód vytvořený šablonou testování částí provádí následující akce:

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.

   - Použije [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) atribut třídy. `UnitTest1` Každá testovací metoda v testovací třídě označená atributem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) je automaticky provedena při spuštění testu jednotky.

   - Použije [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) atribut definovat `TestMethod1` v jazyce `TestSub` C# nebo v jazyce Visual Basic jako testovací metoda pro automatické spuštění při spuštění testu jednotky.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Závislosti** projektu **StringLibraryTest** a z kontextové nabídky vyberte **přidat odkaz.**

   > [!div class="mx-imgBorder"]
   > ![Místní nabídka závislostí StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** rozbalte uzel **Projekty** a zaškrtněte políčko vedle **položky StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít metody **StringLibrary.** Vyberte tlačítko **OK**. Do projektu knihovny tříd je `StringLibrary`přidán odkaz .

   ![Dialogové okno Správce odkazů v sadě Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Přidání a spuštění testovacích metod jednotek

Při spuštění testu částí Visual Studio provede každou metodu, která je označena <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atributem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> ve třídě testování částí, třídy, na které je atribut použit. Testovací metoda končí, když je nalezena první selhání nebo všechny testy obsažené v metodě byly úspěšné.

Nejběžnější testy volání členů <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy. Mnoho metod assert zahrnuje alespoň dva parametry, z nichž jeden je očekávaný výsledek testu a druhý je skutečný výsledek testu. Některé z `Assert` nejčastěji nazývaných metod třídy jsou uvedeny v následující tabulce:

| Metody uplatnění     | Funkce |
| ------------------ | -------- |
| `Assert.AreEqual`  | Ověří, že dvě hodnoty nebo objekty jsou stejné. Vyhodnocení se nezdaří, pokud hodnoty nebo objekty nejsou stejné. |
| `Assert.AreSame`   | Ověří, že dvě proměnné objektu odkazují na stejný objekt. Assert se nezdaří, pokud proměnné odkazují na různé objekty. |
| `Assert.IsFalse`   | Ověří, zda je `false`podmínka . Nepodmíněný výraz se `true`nezdaří, pokud je podmínka . |
| `Assert.IsNotNull` | Ověří, zda objekt není `null`. Assert se nezdaří, `null`pokud je objekt . |

Metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> můžete také použít v testovací metodě k označení typu výjimky, kterou se očekává vyvolání. Test se nezdaří, pokud není vyvolána zadaná výjimka.

Při testování `StringLibrary.StartsWithUpper` metody chcete poskytnout počet řetězců, které začínají velkým znakem. Očekáváte, že `true` metoda vrátit v těchto případech, takže můžete volat metodu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> Podobně chcete poskytnout počet řetězců, které začínají něčím jiným než velkým znakem. Očekáváte, že `false` metoda vrátit v těchto případech, takže můžete volat metodu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>

Vzhledem k tomu, že metoda knihovny zpracovává řetězce, chcete se také ujistit, že úspěšně zpracovává [prázdný řetězec (`String.Empty`)](xref:System.String.Empty), platný řetězec, který nemá žádné znaky a jehož <xref:System.String.Length> je 0 a `null` řetězec, který nebyl inicializován. Pokud `StartsWithUpper` je volána jako <xref:System.String> metoda rozšíření na instanci, nelze předat `null` řetězec. Můžete jej však také volat přímo jako statickou metodu a předat jeden <xref:System.String> argument.

Definujete tři metody, z nichž <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> každá volá metodu opakovaně pro každý prvek v řetězcovém poli. Vzhledem k tomu, že testovací metoda selže, jakmile najde první selhání, zavoláte přetížení metody, která umožňuje předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.

Chcete-li vytvořit zkušební metody:

1. V okně kódu *UnitTest1.cs* nebo *UnitTest1.vb* nahraďte kód následujícím kódem:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Test velkých písmen v `TestStartsWithUpper` metodě zahrnuje řecké velké písmeno alfa (U + 0391) a velké písmeno cyrilice EM (U + 041C). Test malých písmen v `TestDoesNotStartWithUpper` metodě zahrnuje řecké malé písmeno alfa (U + 03B1) a cyrilice malé písmeno ghe (U + 0433).

1. Na řádku nabídek vyberte **Soubor** > **Uložit UnitTest1.cs jako** nebo **Soubor** > **Uložit UnitTest1.vb jako**. V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte Uložit **pomocí kódování**.

   > [!div class="mx-imgBorder"]
   > ![Dialogové okno Uložit soubor jako v sadě Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. V dialogovém okně **Potvrdit uložení jako** vyberte tlačítko **Ano** pro uložení souboru.

1. V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **Kódování** **položku Unicode (UTF-8 s podpisem) – znaková stránka 65001** a vyberte **ok**.

   > [!div class="mx-imgBorder"]
   > ![Dialogové okno Upřesnit možnosti ukládání sady Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Pokud se vám nepodaří uložit zdrojový kód jako soubor kódovaný UTF8, Visual Studio jej může uložit jako soubor ASCII. Když se to stane, runtime není přesně dekódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebude správné.

1. Na řádku nabídek vyberte **Testovat** > **spustit** > **všechny testy**. Otevře se okno **Průzkumníka testů** a zobrazí se, že testy byly úspěšně spuštěny. Tři testy jsou uvedeny v části **Předané testy** a **část Souhrn** hlásí výsledek testu.

   > [!div class="mx-imgBorder"]
   > ![Okno Průzkumníka testů s absolvováním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Zpracování selhání testu

Spuštění testu nemělo žádné chyby, ale mírně jej změňte tak, aby jedna z testovacích metod selhala:

1. Upravte `words` pole `TestDoesNotStartWithUpper` v metodě tak, aby obsahovalo řetězec "Chyba". Soubor není nutné ukládat, protože visual studio automaticky ukládá otevřené soubory, když je řešení vytvořeno pro spuštění testů.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Spusťte test výběrem **možnosti** > **Spustit** > všechny**testy** z řádku nabídek. Okno **Průzkumník testů** označuje, že dva testy byly úspěšné a jeden neúspěšný.

   > [!div class="mx-imgBorder"]
   > ![Okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Vyberte neúspěšný `TestDoesNotStartWith`test . Okno **Průzkumník testů** zobrazí zprávu vytvořenou assert: "Assert.IsFalse se nezdařilo. Očekáváno pro 'Chyba': false; aktuální: True". Z důvodu selhání nebyly testovány všechny řetězce v poli po "Chyba".

   > [!div class="mx-imgBorder"]
   > ![Okno Průzkumníka testů zobrazující selhání kontrolního výrazu IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Vrátit zpět změny provedené v kroku 1 a odebrat řetězec "Chyba". Znovu spusťte test a testy budou projít.

## <a name="test-the-release-version-of-the-library"></a>Otestujte verzi knihovny

Byly jste spuštění testů proti ladění verze knihovny. Nyní, když všechny testy byly všechny předány a jste dostatečně otestovali knihovnu, měli byste spustit testy další čas proti vydání sestavení knihovny. Řada faktorů, včetně optimalizace kompilátoru, může někdy způsobit různé chování mezi ladění a vydání sestavení.

Chcete-li otestovat sestavení verze:

1. Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **Ladění** na **Release**.

   > [!div class="mx-imgBorder"]
   > ![Panel nástrojů Sady Visual Studio se zvýrazněným sestavením verze](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **StringLibrary** a z kontextové nabídky vyberte **Build** a knihovnu znovu zkompilujte.

   > [!div class="mx-imgBorder"]
   > ![Kontextová nabídka StringLibrary s příkazem sestavení](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Spusťte testy částí výběrem **možnosti** > **Spustit** > všechny**testy** z panelu nabídek. Testy projdou.

Nyní, když jste dokončili testování knihovny, dalším krokem je zpřístupnit ji volajícím. Můžete jej svázat s jednou nebo více aplikacemi, nebo ji můžete distribuovat jako balíček NuGet. Další informace naleznete [v tématu Náročné knihovna standardních tříd .NET](consuming-library-with-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Základy testování částí - Visual Studio](/visualstudio/test/unit-test-basics)
