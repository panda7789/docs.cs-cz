---
title: Testování knihovny tříd pomocí platformy .NET Core v sadě Visual Studio 2017
description: Zjistěte, jak otestovat knihovny tříd napsané v jazyce C# pomocí sady Visual Studio 2017
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 04fef4f84658b3a8b82e4e71b62c3bab8537424d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990970"
---
# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Testování knihovny tříd pomocí platformy .NET Core v sadě Visual Studio 2017

V [vytvoření knihovny tříd pomocí jazyka C# a .NET Core v sadě Visual Studio 2017](library-with-visual-studio.md) nebo [vytváření knihovny tříd pomocí jazyka Visual Basic a .NET Core v sadě Visual Studio 2017](vb-library-with-visual-studio.md), vytvoříte jednoduchou třídu knihovnu, která se přidá metodu rozšíření k <xref:System.String> třídy. Teď vytvoříte test jednotky a ujistit se, že pracuje podle očekávání. Přidáte projektu jednotkového testu k řešení, které jste vytvořili v předchozím tématu.

## <a name="creating-a-unit-test-project"></a>Vytvoření projektu testů jednotek

Chcete-li vytvořit projekt testování částí, postupujte takto:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. V **Průzkumníka řešení**, otevřete kontextovou nabídku **ClassLibraryProjects** uzel řešení a vyberte **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogového okna, vyberte **Visual C#** uzlu. Vyberte **.NET Core** uzel, za nímž následuje **projekt testů MSTest (.NET Core)** šablony projektu. V **název** textové pole, zadejte "StringLibraryTest" jako název projektu. Vyberte **OK** k vytvoření projektu testování částí.

   ![Přidání dialogového okna Nový projekt](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > Kromě projekt testů MSTest můžete také použít sady Visual Studio vytvořit projekt testů xUnit pro .NET Core.

1. Visual Studio vytvoří projekt a otevře *UnitTest1.cs* souborů v okně kódu.

   ![Visual Studio code okno Výchozí jednotka testovací třída UnitTest1 projektu a TestMethod1 – metoda](./media/testing-library-with-visual-studio/unittestwindow.png)

   Zdrojový kód vytvořený pomocí šablony testu jednotek provede následující akce:

   * Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> obor názvů, který obsahuje typy používané pro testování částí.

   * Se vztahuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut `UnitTest1` třídy. Každý testovací metody ve třídě testu označené \[TestMethod\] atribut provádí automaticky při spuštění testu jednotek.

   * Se vztahuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` jako testovací metody pro automatické spuštění při spuštění testu jednotek.

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **závislosti** uzlu **StringLibraryTest** projektu a vyberte **přidat odkaz** z kontextové nabídky.

   ![Místní nabídka StringLibraryTest závislostí](./media/testing-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogového okna, rozbalte **projekty** uzlu a zaškrtněte políčko vedle položky **StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít **StringLibrary** metody. Vyberte **OK** tlačítko. To přidá odkaz na váš projekt knihovny tříd `StringLibrary`.

   ![Správce odkazů](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. V **Průzkumníka řešení**, otevřete kontextovou nabídku **ClassLibraryProjects** uzel řešení a vyberte **přidat** > **nový projekt**.

1. V **přidat nový projekt** dialogového okna, vyberte **jazyka Visual Basic** uzlu. Vyberte **.NET Core** uzel, za nímž následuje **projekt testů MSTest (.NET Core)** šablony projektu. V **název** textové pole, zadejte "StringLibraryTest" jako název projektu. Vyberte **OK** k vytvoření projektu testování částí.

   ![Přidání dialogového okna Nový projekt](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > Kromě projekt testů MSTest můžete také použít sady Visual Studio vytvořit projekt testů xUnit pro .NET Core.

1. Visual Studio vytvoří projekt a otevře *UnitTest1.vb* souborů v okně kódu.

   ![Visual Studio code okno Výchozí jednotka testovací třída UnitTest1 projektu a TestMethod1 – metoda](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   Zdrojový kód vytvořený pomocí šablony testu jednotek provede následující akce:

   * Importy oboru názvů [Microsoft.VisualStudio.TestTools.UnitTesting]<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=namewithType> obor názvů, který obsahuje typy používané pro testování částí.

   * Se vztahuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) atribut `UnitTest1` třídy. Každý testovací metody ve třídě testu označené <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut provádí automaticky při spuštění testu jednotek.

   * Se vztahuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut pro definování `TestMethod1` jako testovací metody pro automatické spuštění při spuštění testu jednotek.

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **závislosti** uzlu **StringLibraryTest** projektu a vyberte **přidat odkaz** z kontextové nabídky.

   ![Místní nabídka StringLibraryTest závislostí](./media/testing-library-with-visual-studio/addreference.png)

1. V **správce odkazů** dialogového okna, rozbalte **projekty** uzlu a zaškrtněte políčko vedle položky **StringLibrary**. Přidání odkazu na `StringLibrary` sestavení umožňuje kompilátoru najít **StringLibrary** metody. Vyberte **OK** tlačítko. To přidá odkaz na váš projekt knihovny tříd `StringLibrary`.

   ![Správce odkazů](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>Přidání a spuštění jednotky testovací metody

Při spuštění testů jednotek sady Visual Studio spustí každá metoda označená pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut ve třídě testu jednotek, třídy, ke kterému <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut se používá. Testovací metoda skončí při prvním selhání nebo při všech testů, obsažen v metodě proběhlo úspěšně.

Nejběžnější testuje volání členů <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třídy. Mnoho vyhodnocení obsahovat aspoň dva parametry, z nichž jeden je výsledek testu očekávané a druhý operand, který je výsledkem skutečné testovací metody. V následující tabulce jsou uvedené některé z nejčastěji volané metody.

Assert – metody | Funkce
--- | ---
`Assert.AreEqual` | Ověřuje, že dvě hodnoty nebo objekty rovnají. Vyhodnocení se nezdaří, pokud hodnoty nebo objekty nejsou stejné.
`Assert.AreSame` | Ověřuje, že dvě objektových proměnných odkazují na stejný objekt. Vyhodnocení se nezdaří, pokud proměnné odkazují na různé objekty.
`Assert.IsFalse` | Ověřuje, že je podmínka `false`. Kontrolní výraz selže, pokud je podmínka `true`.
`Assert.IsNotNull` | Ověřuje, že není objekt `null`. Kontrolní výraz selže, pokud je objekt `null`.

Můžete také použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atribut testovací metody. Označuje typ výjimky, které je předpokládáno vyvolání testovací metody. Test se nezdaří, pokud není vyvolána Zadaná výjimka.

Při testování `StringLibrary.StartsWithUpper` metody, které chcete poskytnout počet řetězců, které začínají s velkým písmenem. Očekáváte, že metoda vrátí `true` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> metody. Podobně budete chtít zadat číslo řetězců, které začínají s jinou hodnotu než velké písmeno. Očekáváte, že metoda vrátí `false` v těchto případech, takže můžete volat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> metody.

Protože vaše knihovna obsluhovala řetězce, chcete také ujistěte se, že úspěšně zpracovává [prázdný řetězec (`String.Empty`)](xref:System.String.Empty), platný řetězec, který nemá žádné znaky a jehož <xref:System.String.Length> je 0 a `null` řetězec která nebyla inicializována. Pokud `StartsWithUpper` je volána jako metody rozšíření v <xref:System.String> instance, ho nelze předat `null` řetězec. Ale můžete také volat přímo jako statickou metodu a předejte jeden <xref:System.String> argument.

Definujete tři metody, každý z který volá jeho <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> opakovaně pro každý prvek v poli řetězců. Vzhledem k tomu, že testovací metoda selže při výskytu první selhání, budete volat přetížení metody, která umožňuje předat řetězec, který určuje hodnotu řetězce, který jste použili ve volání metody.

Vytvoření testovací metody:

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. V *UnitTest1.cs* okno kódu, nahraďte kód následujícím kódem:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Všimněte si, že váš test velká znaků `TestStartsWithUpper` metoda obsahuje písmena řecké alfa (U + 0391) a velké písmeno cyrilice EM (U + 041 C) a test malá písmena v `TestDoesNotStartWithUpper` metoda obsahuje Řecké malé písmeno systém Alpha (U + 03B1) a cyrilice malé písmeno g (U + 0433).

1. Na panelu nabídek vyberte **souboru** > **uložit UnitTest1.cs jako**. V **uložit soubor jako** dialogového okna, vyberte šipku vedle **Uložit** tlačítko a vyberte **uložit s kódováním**.

   ![Uložte soubor jako dialogové okno](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. V *UnitTest1.vb* okno kódu, nahraďte kód následujícím kódem:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Všimněte si, že váš test velká znaků `TestStartsWithUpper` metoda obsahuje písmena řecké alfa (U + 0391) a velké písmeno cyrilice EM (U + 041 C) a test malá písmena v `TestDoesNotStartWithUpper` metoda obsahuje Řecké malé písmeno systém Alpha (U + 03B1) a cyrilice malé písmeno g (U + 0433).

1. Na panelu nabídek vyberte **souboru** > **uložit UnitTest1.vb jako**. V **uložit soubor jako** dialogového okna, vyberte šipku vedle **Uložit** tlačítko a vyberte **uložit s kódováním**.

   ![Uložte soubor jako dialogové okno](./media/testing-library-with-visual-studio/savefileas.png)
---

1. V **potvrzení uložit jako** dialogového okna, vyberte **Ano** tlačítko pro uložení souboru.

1. V **pokročilé nastavení uložení** dialogového okna, vyberte **kódování Unicode (UTF-8 s podpisem) - znaková stránka 65001** z **kódování** rozevíracího seznamu a vyberte **OK** .

   ![Dialogové okno pokročilé nastavení uložení](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   Pokud chcete uložit svůj zdrojový kód jako soubor kódovaný v UTF8, Visual Studio může uložit jako soubor ve formátu ASCII. Pokud k tomu dojde, modul runtime nepodporuje dekódovat přesně UTF8 znaky mimo rozsah ASCII a výsledky testů, nebude odpovídat skutečnosti.

1. Na panelu nabídek vyberte **testovací** > **spustit** > **všechny testy**. **Průzkumník testů** okno otevře a zobrazí úspěšně proběhly testy. Tři testy jsou uvedeny v **úspěšné testy** části a **Souhrn** části sestavy výsledků testovacího běhu.

   ![Okno Průzkumníka testu](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a>Zpracování selhání testu

Vašeho testovacího běhu došlo k chybám, žádné, ale mírně změnit tak, aby selhání jednoho z testovací metody:

1. Upravit `words` obsahuje pole `TestDoesNotStartWithUpper` tak, aby zahrnoval řetězec "Chyba". Není nutné soubor uložit, protože při vytváření řešení pro spouštění testů sady Visual Studio automaticky ukládá otevřených souborů.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```
   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```
1. Spuštění testu tak, že vyberete **testování** > **spustit** > **všechny testy** z řádku nabídek. **Průzkumník testů** okno označuje, že dva testy úspěšné a jeden se nezdařilo.

   ![Okno Průzkumníka testu](./media/testing-library-with-visual-studio/failedtest.png)

1. V **neúspěšné testy** neúspěšných testů, vyberte `TestDoesNotStartWith`. **Průzkumník testů** okno zobrazí zprávu vytvářených assert: "Assert.IsFalse se nezdařilo. Byl očekáván pro "Chyba": false; skutečné: True ". Kvůli chybě nebyly testovány všechny řetězce v poli po "Chyba".

   ![Okno Průzkumníka testu je False neplatnost kontrolního výrazu](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. Odebrat kód, který jste přidali (`"Error", `) a opětovné spuštění testu. Testy budou úspěšné.

## <a name="testing-the-release-version-of-the-library"></a>Testování verze knihovny

Běží testy proti ladicí verze knihovny. Teď, když vaše všechny prošly testy a dostatečně otestujete knihovny, byste měli spustit testy další čas proti sestavení pro vydání knihovny. Několika faktory, včetně optimalizace kompilátoru, může někdy vytvořit různé chování mezi sestaveními Debug a Release.

K testování verze sestavení:

1. Na panelu nástrojů sady Visual Studio, změňte konfiguraci buildu z **ladění** k **vydání**.

   ![Panel nástrojů Visual Studio](./media/testing-library-with-visual-studio/toolbar.png)

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **StringLibrary** projektu a vyberte **sestavení** z místní nabídky znovu zkompilovat knihovny.

   ![Místní nabídka StringLibrary](./media/testing-library-with-visual-studio/buildlibrary.png)

1. Spustit testy jednotek výběrem **testovací** > **spustit** > **všechny testy** z řádku nabídek. Testy jsou úspěšné.

Teď, když dokončíte testování své knihovny, dalším krokem je zpřístupnit volající. Můžete svázat ho s minimálně jedna aplikace nebo je můžete distribuovat jako balíček NuGet. Další informace najdete v tématu [použití standardní knihovny tříd .NET](./consuming-library-with-visual-studio.md).
