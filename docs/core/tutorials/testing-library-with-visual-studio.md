---
title: "Testování knihovny tříd s .NET Core v Visual Studio 2017"
description: "Zjistěte, jak otestovat napsané v C# s použitím Visual Studio 2017 knihovny tříd"
keywords: ".NET core, .NET Standard testování částí třídy knihovny, Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7c884985873679b25831c15ef5c8b6370ecd6460
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Testování knihovny tříd s .NET Core v Visual Studio 2017

V [vytvoření knihovny tříd s C# a .NET Core ve Visual Studio 2017](library-with-visual-studio.md) nebo [vytvoření knihovny tříd jazyka Visual Basic a .NET Core ve Visual Studio 2017](vb-library-with-visual-studio.md), vytvoříte jednoduchou třídu knihovnu, která přidá metody rozšíření pro <xref:System.String> třídy. Teď vytvoříte testování částí a ujistěte se, že funguje podle očekávání. K řešení, které jste vytvořili v předchozím tématu přidáte vašeho projektu testování částí.

## <a name="creating-a-unit-test-project"></a>Vytvoření projektu testování částí

Vytvoření projektu testů jednotek, postupujte takto:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. V **Průzkumníku řešení**, otevřete kontextovou nabídku **ClassLibraryProjects** řešení uzel a vyberte možnost **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogovém okně, vyberte **Visual C#** uzlu. Vyberte **.NET Core** následuje uzlu **projektu testování částí (.NET Core)** šablona projektu. V **název** textové pole, jako název projektu zadejte "StringLibraryTest". Vyberte **OK** k vytvoření projektu testování částí.

   ![Přidat dialogové okno Nový projekt](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > Kromě jednotkové testování projektu můžete také použít Visual Studio k vytvoření projektu testů xUnit pro .NET Core.

1. Visual Studio vytvoří projekt a otevře *UnitTest1.cs* souborů v okně kód.

   ![Visual Studio kódu – okno zobrazující výchozí jednotku testování projektu UnitTest1 třídy a TestMethod1 – metoda](./media/testing-library-with-visual-studio/unittestwindow.png)

   Zdrojový kód vytvořených šablonou testů jednotek provede následující akce:

   * Importuje [oboru názvů Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) obor názvů, který obsahuje typy používané k testování jednotek.

   * Se vztahuje [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) atribut `UnitTest1` třídy. Každý test metodu v třídě testovací označené \[TestMethod\] atribut se spustí automaticky při spuštění testování částí.

   * Se vztahuje [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) definici atributu `TestMethod1` jako testovací metody pro automatické spuštění při spuštění testování částí.

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **závislosti** uzlu **StringLibraryTest** projektu a vyberte **přidat odkaz na** z v místní nabídce.

   ![Kontextové nabídky StringLibraryTest závislosti](./media/testing-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogové okno, rozbalte **projekty** uzlu a zaškrtněte políčko vedle **StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít **StringLibrary** metody. Vyberte **OK** tlačítko. Tento příkaz přidá odkaz do projektu knihovny tříd `StringLibrary`.

   ![Správce odkazů](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. V **Průzkumníku řešení**, otevřete kontextovou nabídku **ClassLibraryProjects** řešení uzel a vyberte možnost **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogovém okně, vyberte **jazyka Visual Basic** uzlu. Vyberte **.NET Core** následuje uzlu **projektu testování částí (.NET Core)** šablona projektu. V **název** textové pole, jako název projektu zadejte "StringLibraryTest". Vyberte **OK** k vytvoření projektu testování částí.

   ![Přidat dialogové okno Nový projekt](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > Kromě jednotkové testování projektu můžete také použít Visual Studio k vytvoření projektu testů xUnit pro .NET Core.

1. Visual Studio vytvoří projekt a otevře *UnitTest1.vb* souborů v okně kód.

   ![Visual Studio kódu – okno zobrazující výchozí jednotku testování projektu UnitTest1 třídy a TestMethod1 – metoda](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   Zdrojový kód vytvořených šablonou testů jednotek provede následující akce:

   * Importuje [oboru názvů Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) obor názvů, který obsahuje typy používané k testování jednotek.

   * Se vztahuje [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) atribut `UnitTest1` třídy. Každý test metodu v třídě testovací označené \[TestMethod\] atribut se spustí automaticky při spuštění testování částí.

   * Se vztahuje [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) definici atributu `TestMethod1` jako testovací metody pro automatické spuštění při spuštění testování částí.

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **závislosti** uzlu **StringLibraryTest** projektu a vyberte **přidat odkaz na** z v místní nabídce.

   ![Kontextové nabídky StringLibraryTest závislosti](./media/testing-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogové okno, rozbalte **projekty** uzlu a zaškrtněte políčko vedle **StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít **StringLibrary** metody. Vyberte **OK** tlačítko. Tento příkaz přidá odkaz do projektu knihovny tříd `StringLibrary`.

   ![Správce odkazů](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>Přidání a spuštění jednotky testovací metody

Při spuštění testů jednotek sady Visual Studio se provede každé metody označené jako [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) atribut v třídě test jednotky, třídu, ke kterému [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) atribut se používá. Test metody ukončí po prvním selhání nebo když všechny testy, které jsou obsažené v metodě proběhlo úspěšně.

Nejběžnější testy členy volání [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) třídy. Mnoho assert metody obsahovat aspoň dva parametry, z nichž jeden je výsledkem očekávaný testovací a druhá z nich je výsledek skutečné testu. Některé z jeho nejčastěji vyvolání metody se zobrazují v následující tabulce.

Assert – metody | Funkce
--- | ---
`Assert.AreEqual` | Ověřuje, zda dva objekty nebo hodnoty jsou si rovny. Assert selže, pokud hodnoty nebo objekty nejsou stejné.
`Assert.AreSame` | Ověřuje, že dvě proměnné objektu odkazovat na stejný objekt. Assert selže, pokud proměnné odkazovat na jiné objekty.
`Assert.IsFalse` | Ověřuje, že je podmínka `false`. Assert nezdaří, pokud je podmínka vyhodnocena jako `true`.
`Assert.IsNotNull` | Ověřuje, že objekt není `null`. Assert nezdaří, pokud je objekt `null`.

Můžete taky použít [ \[ExpectedException\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) atribut metoda testu. Označuje typ výjimky, očekávána throw metoda testu. Test se nezdaří, pokud není zadaný výjimka vydána.

Při testování `StringLibrary.StartsWithUpper` metody, které chcete zadat počet řetězce, které začínají znakem velká písmena. Očekáváte, že metoda vrátí `true` v těchto případech, takže můžete volat [Assert.IsTrue (logická hodnota, řetězec)](https://msdn.microsoft.com/library/ms243754.aspx) metoda. Obdobně chcete zadat počet řetězce, které začínají s něco jiného než velké písmeno. Očekáváte, že metoda vrátí `false` v těchto případech, takže můžete volat [Assert.IsFalse (logická hodnota, řetězec)](https://msdn.microsoft.com/library/ms243805.aspx) metoda.

Vzhledem k tomu, že vaše knihovna metoda zpracovává řetězce, také chtít zajistit, že úspěšně zpracovává [prázdný řetězec (`String.Empty`)](xref:System.String.Empty), platný řetězec, který má žádné znaky a jehož <xref:System.String.Length> 0 a `null` řetězec která nebyla inicializována. Pokud `StartsWithUpper` nazývá jako metody rozšíření na <xref:System.String> instance, ho nelze předat `null` řetězec. Ale můžete také volat přímo jako statickou metodu a předat jedné <xref:System.String> argument.

Definujete tři metody, každý z který volá jeho [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) metoda opakovaně pro každý prvek v poli řetězců. Protože metodu testu se nezdařila při výskytu prvním selhání, budete volat přetížení metody, která umožňuje předat řetězec, který určuje hodnotu řetězce použitá ve volání metody.

Pokud chcete vytvořit zkušební metody:

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. V *UnitTest1.cs* kódu okno, nahraďte kód následujícím kódem:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Všimněte si, že váš test velká znaků `TestStartsWithUpper` metoda obsahuje Velké řecké písmeno alfa (U + 0391) a velké písmeno cyrilice EM (U + 041 C) a test malá písmena v `TestDoesNotStartWithUpper` metoda obsahuje malé řecké písmeno Alpha (U + 03B1) a azbuce malé písmeno g (U + 0433).

1. Na panelu nabídek vyberte **soubor** > **uložit UnitTest1.cs jako**. V **uložit soubor jako** dialogovém okně, vyberte na šipku vedle položky **Uložit** tlačítko a vyberte **uložit s kódování**.

   ![Uložte soubor jako dialogové okno](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. V *UnitTest1.vb* kódu okno, nahraďte kód následujícím kódem:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Všimněte si, že váš test velká znaků `TestStartsWithUpper` metoda obsahuje Velké řecké písmeno alfa (U + 0391) a velké písmeno cyrilice EM (U + 041 C) a test malá písmena v `TestDoesNotStartWithUpper` metoda obsahuje malé řecké písmeno Alpha (U + 03B1) a azbuce malé písmeno g (U + 0433).

1. Na panelu nabídek vyberte **soubor** > **uložit UnitTest1.vb jako**. V **uložit soubor jako** dialogovém okně, vyberte na šipku vedle položky **Uložit** tlačítko a vyberte **uložit s kódování**.

   ![Uložte soubor jako dialogové okno](./media/testing-library-with-visual-studio/savefileas.png)
---

1. V **potvrďte uložit jako** dialogovém okně, vyberte **Ano** tlačítko pro uložení souboru.

1. V **rozšířené možnosti ukládání** dialogovém okně, vyberte **Unicode (UTF-8 podpisem) - Codepage 65001** z **kódování** rozevíracího seznamu a vyberte **OK** .

   ![Dialogové okno Upřesnit nastavení uložit](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   Pokud uložíte jako soubor s kódováním UTF8 vašeho zdrojového kódu, Visual Studio může uložit jako soubor s kódováním ASCII. Pokud k tomu dojde, modul runtime není dekódování přesně znaků UTF8 mimo rozsah ASCII a nebude přesné výsledky testů.

1. Na panelu nabídek vyberte **Test** > **spustit** > **všechny testy**. **Průzkumníka testů** se otevře okno a ukazuje, že testy proběhla úspěšně. Tři testy jsou uvedeny v **předán testy** části a **Souhrn** části sestavy výsledek testovacím běhu.

   ![Okno Průzkumníka testů](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a>Zpracování selhání při testu

Test spusťte měl žádné chyby, ale trochu změnit tak, aby jednu z metod test nezdaří:

1. Změnit `words` pole v `TestDoesNotStartWithUpper` tak, aby zahrnoval řetězec "Chyba". Nemusíte soubor uložit, protože při řešení je sestavena pro běh testů Visual Studio automaticky uloží otevřených souborů.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```
   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```
1. Spuštění testu výběrem **testování** > **spustit** > **všechny testy** z řádku nabídek. **Průzkumníka testů** okno označuje, že dva testy úspěšné a jedním se nezdařilo.

   ![Okno Průzkumníka testů](./media/testing-library-with-visual-studio/failedtest.png)

1. V **se nezdařilo testy** vyberte neúspěšných testů `TestDoesNotStartWith`. **Průzkumníka testů** okno zobrazí zprávu, kterou assert zobrazí: "Assert.IsFalse se nezdařilo. Očekávání pro "Chyba": false; Skutečná: True ". Z důvodu selhání nebyly testovány všechny řetězce v poli po "Chyba".

   ![Okno Průzkumníka testovacího zobrazení je False assertion selhání](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. Odebrat kód, který jste přidali (`"Error", `) a znovu spusťte test. Testy předá.

## <a name="testing-the-release-version-of-the-library"></a>Testování verzi knihovny

Jste byla spuštěna testy proti ladění verzi knihovny. Teď, když testy všechny předané a adekvátní otestujete knihovnu, byste měli spustit testy další čas proti sestavení pro vydání knihovny. Několika faktory, včetně optimalizace kompilátoru může někdy vytvářet různé chování mezi sestaveními Debug a Release.

Pro testování sestavení pro vydání:

1. Na panelu nástrojů Visual Studio změnit konfiguraci sestavení z **ladění** k **verze**.

   ![Panel nástrojů Visual Studio](./media/testing-library-with-visual-studio/toolbar.png)

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **StringLibrary** projektu a vyberte **sestavení** v místní nabídce překompilovat knihovny.

   ![StringLibrary kontextové nabídky](./media/testing-library-with-visual-studio/buildlibrary.png)

1. Spouštění testů jednotek výběrem **Test** > **spustit** > **všechny testy** z řádku nabídek. Jsou testy úspěšné.

Teď, když jste dokončili testování knihovnu, dalším krokem je a zpřístupněte ji volající. Můžete ji svázat s jednu nebo více aplikací nebo distribuovat ji jako balíček NuGet. Další informace najdete v tématu [využívání standardní knihovny tříd rozhraní .NET](./consuming-library-with-visual-studio.md).
