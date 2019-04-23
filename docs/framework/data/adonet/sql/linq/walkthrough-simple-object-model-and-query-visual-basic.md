---
title: 'Návod: Jednoduchý objektový model a dotaz (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: 326caf550e8b138b4b968f0021a7fc475dc58c8d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338069"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>Návod: Jednoduchý objektový model a dotaz (Visual Basic)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálními složitosti. Vytvořte třídu entity, která modeluje tabulku Customers v ukázkové databázi Northwind. Pak vytvoříte jednoduchý dotaz do seznamu zákazníků, kteří jsou umístěny v Londýně.  
  
 Tento názorný postup je kód objektově orientovaný záměrné pomohou zobrazit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koncepty. Obvykle vzato můžete využít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vytvoření objektového modelu.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Tento návod používá vyhrazené složky ("c:\linqtest") pro uložení souborů. Vytvoření této složky, před zahájením návodu.  
  
-   Tento návod vyžaduje ukázkové databáze Northwind. Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download. Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databáze, zkopírujte soubor do složky c:\linqtest.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavních úloh:  
  
-   Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.  
  
-   Mapování třídy do databázové tabulky.  
  
-   Určení vlastnosti na třídu, představují sloupce databáze.  
  
-   Zadání připojení k databázi Northwind.  
  
-   Vytvoření jednoduchého dotazu ke spuštění na databázi.  
  
-   Provádění dotazu a sledování výsledky.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytvoření LINQ to SQL řešení  
 V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>K vytvoření LINQ to SQL řešení  
  
1. Na **souboru** nabídky, klikněte na tlačítko **nový projekt**.  
  
2. V **typy projektů** podokně **nový projekt** dialogové okno, klikněte na tlačítko **jazyka Visual Basic**.  
  
3. V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.  
  
4. V **název** zadejte **LinqConsoleApp**.  
  
5. Klikněte na **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů LINQ a direktivy  
 Tento návod používá sestavení, která nemusí být nainstalován ve výchozím nastavení ve vašem projektu. Pokud `System.Data.Linq` není uveden jako odkaz v projektu (klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníku řešení** a rozbalte **odkazy** uzlu), přidat, jak je vysvětleno v Následující kroky.  
  
#### <a name="to-add-systemdatalinq"></a>Chcete-li přidat System.Data.Linq  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.  
  
2. V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.  
  
     Sestavení se přidá do projektu.  
  
3. Také v **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, přejděte k položce a klikněte na System.Windows.Forms a potom klikněte na **OK**.  
  
     Toto sestavení, která podporuje okně se zprávou v návodu, se přidá do projektu.  
  
4. Přidejte následující direktivy výše `Module1`:  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mapování třídy do tabulky databáze  
 V tomto kroku vytvoříte třídu a mapovat do tabulky databáze. Tato třída se nazývá *třída entity*. Všimněte si, že mapování lze provést pouze přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atribut. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Chcete-li vytvořit třídu entity a jejich mapování na tabulku databáze  
  
-   Zadejte nebo vložte následující kód do Module1.vb okamžitě výše `Sub Main`:  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Určení vlastnosti na třídu, představují sloupce databáze  
 V tomto kroku můžete provést několik úloh.  
  
-   Můžete použít <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení `CustomerID` a `City` vlastnosti v entitě tříd jako sloupce v tabulce databáze.  
  
-   Můžete určit `CustomerID` vlastnost jako sloupec primárního klíče v databázi.  
  
-   Určíte `_CustomerID` a `_City` polí privátního úložiště. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Můžete pak ukládat a načítat hodnoty přímo, namísto použití veřejnou přistupující objekty, které mohou obsahovat obchodní logiku.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>K reprezentaci charakteristiky dva sloupce databáze  
  
-   Zadejte nebo vložte následující kód do Module1.vb těsně před `End Class`:  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Zadání připojení k databázi Northwind  
 V tomto kroku použijete <xref:System.Data.Linq.DataContext> objektu k navázání připojení mezi založený na kódu datových struktur a samotná databáze. <xref:System.Data.Linq.DataContext> Je hlavní kanál, přes který načtení objektů z databáze a odeslat změny.  
  
 Můžete také deklarovat `Table(Of Customer)` tak, aby fungoval jako tabulku logické, zadaný pro vaše dotazy na tabulku Customers v databázi. Vytvoříte a spusťte tyto dotazy v dalších krocích.  
  
#### <a name="to-specify-the-database-connection"></a>K určení připojení k databázi  
  
-   Zadejte nebo vložte následující kód do `Sub Main` metody.  
  
     Všimněte si, že `northwnd.mdf` soubor je považován za ve složce linqtest. Další informace najdete v oddílu požadavky dříve v tomto návodu.  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a>Vytvoření jednoduchého dotazu  
 V tomto kroku vytvoříte dotaz, který najde, které zákazníkům v tabulce Zákazníci databáze jsou umístěny v Londýně. Dotaz kód v tomto kroku právě popisuje dotazu. Nespustí se. Tento postup se označuje jako *odložené provedení*. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Bude také vytvoří protokol výstup na zobrazení SQL příkazy, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje. Tato funkce protokolování (který používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečné při ladění a určit, že příkazy odesílané do databáze přesně představovat svůj dotaz.  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
-   Zadejte nebo vložte následující kód do `Sub Main` za `Table(Of Customer)` deklarace:  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a>Provádění dotazu  
 V tomto kroku skutečně spusťte dotaz. Výrazy dotazu, který jste vytvořili v předchozích krocích není vyhodnocen, dokud jsou potřebné výsledky. Když začnete `For Each` iterace, spuštění příkazu SQL na databázi a objekty jsou vyhodnocena.  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1. Zadejte nebo vložte následující kód na konci `Sub Main` – metoda (po description dotazu):  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2. Stisknutím klávesy F5 pro ladění aplikace.  
  
    > [!NOTE]
    >  Pokud vaše aplikace generuje chyba za běhu, najdete v části řešení potíží [učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     Okno se zprávou zobrazí seznam šest zákazníků. V okně konzoly se zobrazí vygenerovaný kód SQL.  
  
3. Klikněte na tlačítko **OK** zavřete okno se zprávou.  
  
     Aplikace se zavře.  
  
4. Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.  
  
     Pokud budete pokračovat s dalšího názorného postupu musíte tuto aplikaci.  
  
## <a name="next-steps"></a>Další kroky  
 [Názorný postup: Dotazování napříč relacemi (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) tématu pokračuje, kde končí tohoto návodu. Dotazování napříč vztahy názorný postup ukazuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dotazování přes tabulky, podobně jako *spojení* v relační databázi.  
  
 Pokud chcete provést dotazování napříč vztahy návodu, ujistěte se, že se uložit řešení pro návod, který právě jste dokončili, což je předpoklad.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
