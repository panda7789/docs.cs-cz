---
title: Testování .NET Standard knihovny tříd pomocí .NET Core v aplikaci Visual Studio
description: Vytvořte projekt testu jednotek pro knihovnu tříd .NET Core. Ověřte, že vaše knihovna tříd .NET Core pracuje správně s testy jednotek.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156618"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Testování knihovny .NET Standard pomocí .NET Core v aplikaci Visual Studio

V [sestavení knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md)jste vytvořili jednoduchou knihovnu tříd, která přidá metodu rozšíření do <xref:System.String> třídy. Nyní vytvoříte test jednotky, abyste se ujistili, že funguje podle očekávání. Projekt testování částí přidáte do řešení, které jste vytvořili v předchozím článku.

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testů jednotek

Chcete-li vytvořit projekt testování částí, postupujte následovně:

1. Otevřete řešení `ClassLibraryProjects`, které jste vytvořili v článku [Vytvoření knihovny .NET Standard v aplikaci Visual Studio](library-with-visual-studio.md) .

1. Přidejte do řešení nový projekt testování částí s názvem "StringLibraryTest".

   1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **MSTest** . V **C#** seznamu jazyků vyberte nebo **Visual Basic** a pak vyberte **všechny platformy** ze seznamu platforem. Zvolte šablonu **projekt testů MSTest (.NET Core)** a klikněte na tlačítko **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibraryTest** . Potom zvolte **Create** (Vytvořit).

   > [!NOTE]
   > Kromě MSTest můžete také vytvořit xUnit a nUnit testovací projekty pro .NET Core v aplikaci Visual Studio.

1. Visual Studio vytvoří projekt a otevře soubor třídy v okně Code (kód) s následujícím kódem:

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

   - Importuje obor názvů <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, který obsahuje typy používané pro testování částí.

   - Aplikuje atribut [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) na třídu `UnitTest1`. Každá testovací metoda v testovací třídě, která je označena atributem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) , je provedena automaticky při spuštění testu jednotky.

   - Použije atribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) k definování `TestMethod1` v C# nebo `TestSub` v Visual Basic jako testovací metodu pro automatické provedení při spuštění testu jednotek.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **závislosti** projektu **StringLibraryTest** a vyberte možnost **Přidat odkaz** z místní nabídky.

   > [!div class="mx-imgBorder"]
   > ![kontextová nabídka závislostí StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. V dialogovém okně **Správce odkazů** rozbalte uzel **projekty** a zaškrtněte políčko vedle položky **StringLibrary**. Přidání odkazu na sestavení `StringLibrary` umožňuje kompilátoru najít metody **StringLibrary** . Vyberte tlačítko **OK**. Do projektu knihovny tříd se přidá odkaz, `StringLibrary`.

   ![Dialogové okno Správce odkazů v aplikaci Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Přidat a spustit metody testování částí

Když aplikace Visual Studio spustí test jednotky, provede každou metodu, která je označena atributem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> ve třídě testu jednotek, třída, na kterou je atribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> použit. Testovací metoda končí při nalezení prvního selhání nebo po úspěšném dokončení všech testů obsažených v metodě.

Nejběžnější testy volají členy třídy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Mnoho metod Assert zahrnuje nejméně dva parametry, jeden z nich je očekávaný výsledek testu a druhý z nich je skutečný výsledek testu. Některé často volané metody třídy `Assert` jsou uvedeny v následující tabulce:

| Metody Assert     | Funkce |
| ------------------ | -------- |
| `Assert.AreEqual`  | Ověřuje, zda jsou dvě hodnoty nebo objekty stejné. Vyhodnocení se nezdařila, pokud se hodnoty nebo objekty neshodují. |
| `Assert.AreSame`   | Ověřuje, že dvě proměnné objektu odkazují na stejný objekt. Pokud proměnné odkazují na různé objekty, vyhodnocení se nezdařilo. |
| `Assert.IsFalse`   | Ověřuje, že je `false`podmínka. Pokud je podmínka `true`, vyhodnocení se nezdařilo. |
| `Assert.IsNotNull` | Ověřuje, že objekt není `null`. Pokud je objekt `null`, vyhodnocení se nezdařilo. |

Můžete také použít metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> v testovací metodě k označení typu výjimky, kterou očekává, že má být vyvolána. Test se nezdařil, pokud není vyvolána zadaná výjimka.

Při testování metody `StringLibrary.StartsWithUpper` chcete zadat počet řetězců, které začínají velkým znakem. Očekáváte, že metoda vrátí `true` v těchto případech, takže můžete volat metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. Podobně je vhodné zadat počet řetězců, které začínají jinou výjimkou znaku velkého písmene. Očekáváte, že metoda vrátí `false` v těchto případech, takže můžete volat metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Vzhledem k tomu, že vaše metoda knihovny zpracovává řetězce, je také vhodné se ujistit, že úspěšně zpracovává [prázdný řetězec (`String.Empty`)](xref:System.String.Empty), platný řetězec, který neobsahuje žádné znaky a jehož <xref:System.String.Length> je 0, a `null` řetězec, který nebyl inicializován. Pokud je `StartsWithUpper` volána jako metoda rozšíření v instanci <xref:System.String>, nelze předat `null` řetězec. Můžete ji však také volat přímo jako statickou metodu a předat jeden <xref:System.String> argument.

Budete definovat tři metody, každý z nich volá metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> opakovaně pro každý prvek v poli řetězců. Vzhledem k tomu, že testovací metoda selže, jakmile najde první selhání, zavoláte přetížení metody, které vám umožní předat řetězec, který označuje hodnotu řetězce použitou ve volání metody.

Postup vytvoření testovacích metod:

1. V okně kódu *UnitTest1.cs* nebo *UnitTest1. vb* nahraďte kód následujícím kódem:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Test velkých písmen v metodě `TestStartsWithUpper` obsahuje řecké velké písmeno alfa (U + 0391) a velké písmeno cyrilice EM (U + 041C). Test malých písmen v metodě `TestDoesNotStartWithUpper` obsahuje řecké malé písmeno alfa (U + 03B1) a malé písmeno g (u + 0433) v cyrilici.

1. V řádku nabídek vyberte **soubor** > **Uložit UnitTest1.cs jako** nebo **soubor** > **Uložit UnitTest1. vb jako**. V dialogovém okně **Uložit soubor jako** vyberte šipku vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio uložit soubor jako dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. Kliknutím na tlačítko **Ano** v dialogovém okně **Potvrdit uložení jako** soubor uložte.

1. V dialogovém okně **Upřesnit možnosti uložení** vyberte v rozevíracím seznamu **kódování** znakovou **sadu Unicode (UTF-8 s podpisem 65001)** a vyberte **OK**.

   > [!div class="mx-imgBorder"]
   > Dialogové okno ![Upřesnit možnosti uložení v aplikaci Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Pokud neuložíte zdrojový kód jako soubor s kódováním UTF8, Visual Studio ho může uložit jako soubor ASCII. Pokud k tomu dojde, modul runtime nebude přesně kódovat znaky UTF8 mimo rozsah ASCII a výsledky testu nebudou správné.

1. Na panelu nabídek vyberte možnost **Test** > **Spustit** > **všechny testy**. Otevře se okno **Průzkumník testů** , ve kterém se zobrazí, že testy proběhly úspěšně. Tři testy jsou uvedeny v části **prošlé testy** a v části **Souhrn** se zobrazí výsledek testovacího běhu.

   > [!div class="mx-imgBorder"]
   > ![okno Průzkumníka testů s předáváním testů](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Zpracování selhání testu

V testovacím běhu došlo k žádným chybám, ale mírně ho změňte, aby jedna z testovacích metod nebyla úspěšná:

1. Upravte pole `words` v metodě `TestDoesNotStartWithUpper` tak, aby obsahovala řetězec "Error" (chyba). Nemusíte soubor ukládat, protože Visual Studio automaticky ukládá otevřené soubory, když je řešení sestaveno pro spouštění testů.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Spusťte test výběrem možnosti **test** > **Spustit** > **všechny testy** z řádku nabídek. Okno **Průzkumník testů** indikuje, že dva testy byly úspěšné a jedna se nezdařila.

   > [!div class="mx-imgBorder"]
   > ![okno Průzkumníka testů s neúspěšnými testy](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Vyberte neúspěšný test `TestDoesNotStartWith`. V okně **Průzkumník testů** se zobrazí zpráva vytvořená kontrolním výrazem: Assert. NEPRAVDA. Očekávané pro ' error ': false; skutečnost: true ". Z důvodu chyby nebyly testovány všechny řetězce v poli po "Error".

   > [!div class="mx-imgBorder"]
   > ![okno Průzkumníka testů znázorňující selhání kontrolního výrazu s hodnotou false](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Vraťte změny, které jste provedli v kroku 1, a odeberte řetězec "Error" (chyba). Spusťte test znovu a testy se budou předávat.

## <a name="test-the-release-version-of-the-library"></a>Testování verze pro vydání knihovny

Spustili jste testy pro ladicí verzi knihovny. Nyní, když testy úspěšně prošly a jste dostatečně otestovali knihovnu, měli byste spustit testy dodatečně na sestavení vydaných verzí knihovny. Několik faktorů, včetně optimalizací kompilátoru, může někdy způsobit různé chování mezi sestaveními ladění a vydání.

Testování sestavení pro vydání:

1. Na panelu nástrojů sady Visual Studio změňte konfiguraci sestavení z **ladit** na **release**.

   > [!div class="mx-imgBorder"]
   > panel nástrojů ![sady Visual Studio s zvýrazněnou verzí buildu](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **StringLibrary** a vyberte **sestavení** z místní nabídky pro rekompilaci knihovny.

   > [!div class="mx-imgBorder"]
   > místní nabídka ![StringLibrary pomocí příkazu Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Spusťte testy jednotek výběrem možnosti **Test** > **Spustit** > **všechny testy** z řádku nabídek. Testy jsou passované.

Teď, když jste dokončili testování knihovny, je dalším krokem zpřístupnění volajícím. Můžete ho seskupit s jednou nebo více aplikacemi nebo ho můžete distribuovat jako balíček NuGet. Další informace naleznete v tématu [spotřebovávání knihovny tříd .NET Standard](consuming-library-with-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Základy testování částí – Visual Studio](/visualstudio/test/unit-test-basics)
