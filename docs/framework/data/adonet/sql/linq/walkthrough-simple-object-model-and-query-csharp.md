---
title: 'Návod: Jednoduché objektový Model a dotazů (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 2c2529c828c0b02ec2f53c7ea899bbe728ba88d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362361"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>Návod: Jednoduché objektový Model a dotazů (C#)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář s minimálním složité kroky. Vytvoří třídu entity modelů tabulku zákazníků v ukázkové databázi Northwind. Pak vytvoříte jednoduchý dotaz seznamu zákazníkům, kteří jsou umístěny v Londýně.  
  
 Tento názorný postup je kód orientované návrhu můžete zobrazit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koncepty. Obvykle platí, že byste použili [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření objektu modelu.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento názorný postup napsané pomocí Visual C# – vývojové nastavení.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest5"). Než začnete návodu, vytvořte této složky.  
  
-   Tento postup vyžaduje ukázková databáze Northwind. Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databázi, zkopírujte soubor do složky c:\linqtest5.  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavní úlohy:  
  
-   Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.  
  
-   Mapování třídu do databázové tabulky.  
  
-   Určení vlastností na třídu, představují sloupců databáze.  
  
-   Určení připojení k databázi Northwind.  
  
-   Vytvoření jednoduchého dotazu ke spouštění na databázi.  
  
-   Provádění dotazu a sledování výsledků.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytváření dotazu LINQ to SQL řešení  
 V této úloze první vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Chcete-li vytvořit LINQ to SQL řešení  
  
1.  V sadě Visual Studio **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
2.  V **typy projektů** podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#**.  
  
3.  V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.  
  
4.  V **název** zadejte **LinqConsoleApp**.  
  
5.  V **umístění** ověřte, kam chcete uložit soubory projektu.  
  
6.  Click **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů LINQ a direktivy  
 Tento návod používá sestavení, které nemusí být nainstalovány ve výchozím nastavení ve vašem projektu. Pokud System.Data.Linq není uvedena jako odkaz ve vašem projektu (rozbalte **odkazy** uzlu v **Průzkumníku řešení**), přidejte ho, jak je popsáno v následujících krocích.  
  
#### <a name="to-add-systemdatalinq"></a>Chcete-li přidat System.Data.Linq  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.  
  
2.  V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.  
  
     Je sestavení přidáno do projektu.  
  
3.  Přidejte následující direktivy v horní části **Program.cs**:  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mapování třídu do databázové tabulky  
 V tomto kroku vytvoříte třídu a mapovat do databázové tabulky. Tato třída se říká *třídy entita*. Všimněte si, že mapování lze provést pouze přidáním <xref:System.Data.Linq.Mapping.TableAttribute> atribut. <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost určuje název tabulky v databázi.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Vytvořte třídu entity a namapovat je do databázové tabulky  
  
-   Zadejte nebo vložte následující kód do souboru Program.cs okamžitě výše `Program` deklarace třídy:  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Určení vlastností na třídu, představují sloupců databáze  
 V tomto kroku můžete provést několik úloh.  
  
-   Můžete použít <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení `CustomerID` a `City` vlastnosti u entity třídy představující sloupců v tabulce databáze.  
  
-   Určíte `CustomerID` vlastnost jako představující sloupec primárního klíče v databázi.  
  
-   Určíte `_CustomerID` a `_City` pole pro privátní úložiště. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Můžete pak ukládání a načítání hodnot přímo, namísto použití veřejného přístupových objektů, které mohou zahrnovat obchodní logiku.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>Představují charakteristiky dvou sloupců databáze  
  
-   Zadejte nebo vložte následující kód do souboru Program.cs uvnitř složených závorek pro `Customer` třídy.  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Určení připojení k databázi Northwind  
 V tomto kroku použijete <xref:System.Data.Linq.DataContext> objektu k navázání připojení mezi vaší založené na kódu datové struktury a samotná databáze. <xref:System.Data.Linq.DataContext> Je hlavní kanál, pomocí kterého se načtení objektů z databáze a odeslání změn.  
  
 Je také deklarovat `Table<Customer>` tak, aby fungoval jako logické, typu tabulky pro vaše dotazy pro tabulku zákazníků v databázi. Vytvoříte a spusťte tyto dotazy v dalších krocích.  
  
#### <a name="to-specify-the-database-connection"></a>K určení připojení k databázi  
  
-   Zadejte nebo vložte následující kód do `Main` metoda.  
  
     Všimněte si, že `northwnd.mdf` souboru se předpokládá, že se ve složce linqtest5. Další informace najdete v části požadavky dříve v tomto návodu.  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a>Vytvoření jednoduchého dotazu  
 V tomto kroku vytvoříte dotaz, který najde v tabulce databáze zákazníci uvedeni zákazníci, kteří jsou umístěny v Londýně. Kód dotazu v tomto kroku právě popisuje dotaz. Ho ji není provedena. Tento postup se označuje jako *odložené spouštění*. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Budete také produktu protokolu výstup zobrazíte SQL příkazy, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje. Tato funkce protokolování (které používá <xref:System.Data.Linq.DataContext.Log%2A>) je užitečné v ladění a určení, že příkazy odesílány do databáze přesně představují dotazu.  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
-   Zadejte nebo vložte následující kód do `Main` metoda po `Table<Customer>` deklarace.  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a>Provádění dotazu  
 V tomto kroku skutečně provést dotaz. Výrazy dotazů, které jste vytvořili v předchozích krocích nebudou vyhodnoceny, dokud jsou potřeba výsledky. Když začnete `foreach` iterace, je spustit příkaz SQL pro databázi a objekty jsou materializována.  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1.  Zadejte nebo vložte následující kód na konci `Main` – metoda (po popis dotazu).  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  Stisknutím klávesy F5 ladění aplikace.  
  
    > [!NOTE]
    >  Pokud vaše aplikace generuje chyba spuštění, naleznete v části řešení potíží [učení podle návody](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     Výsledky dotazu v okně konzoly se zobrazí následující:  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  Stisknutím klávesy Enter v okně konzoly aplikace se zavře.  
  
## <a name="next-steps"></a>Další kroky  
 [Návod: dotazování napříč vztahy (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) tématu pokračuje, které končí tento návod. Dotaz napříč vztahy návod ukazuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete dotazování mezi tabulkami, podobně jako *spojení* v relační databázi.  
  
 Pokud chcete do dotazu napříč vztahy návod, uložte řešení pro, který právě jste dokončili Průvodce, který je podmínkou.  
  
## <a name="see-also"></a>Viz také  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
