---
title: 'Návod: Manipulace s daty (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 0dd70eb5d3b3ad56a8597ce0658a296a03d5f4a7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618052"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>Návod: Manipulace s daty (Visual Basic)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravy a odstraňování dat v databázi. Přidejte zákazníka, změňte název zákazníka a odstranit objednávky použijete kopii ukázkové databáze Northwind.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím vývojového nastavení jazyka Visual Basic.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
- Tento návod používá vyhrazené složky ("c:\linqtest2") pro uložení souborů. Vytvoření této složky, před zahájením návodu.  
  
- Ukázkovou databázi Northwind  
  
     Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download. Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databáze, zkopírujte do složky c:\linqtest2 northwnd.mdf souboru.  
  
- Soubor kódu jazyka Visual Basic generují z databáze Northwind.  
  
     Tento soubor můžete vygenerovat buď pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo nástroji SQLMetal. Tento návod byl napsán s použitím nástroje SQLMetal s následujícím příkazovým řádkem:  
  
     **SqlMetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" / pluralize**  
  
     Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavních úloh:  
  
- Vytváří [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.  
  
- Přidání kódu databázový soubor do projektu.  
  
- Vytváří se nový objekt zákazníka.  
  
- Úprava kontaktní jméno zákazníka.  
  
- Odstraňuje se objednávky.  
  
- Odesílá se tyto změny k databázi Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytvoření LINQ to SQL řešení  
 V této první úloze vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>K vytvoření LINQ to SQL řešení  
  
1. V sadě Visual Studio **souboru** nabídky, klikněte na tlačítko **nový projekt**.  
  
2. V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **jazyka Visual Basic**.  
  
3. V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.  
  
4. V **název** zadejte **LinqDataManipulationApp**.  
  
5. Klikněte na **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů LINQ a direktivy  
 Tento návod používá sestavení, která nemusí být nainstalován ve výchozím nastavení ve vašem projektu. Pokud `System.Data.Linq` není uveden jako odkaz v projektu (klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníku řešení** a rozbalte **odkazy** uzlu), přidat, jak je vysvětleno v Následující kroky.  
  
#### <a name="to-add-systemdatalinq"></a>Chcete-li přidat System.Data.Linq  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.  
  
2. V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.  
  
     Sestavení se přidá do projektu.  
  
3. V editoru kódu přidejte následující direktivy výše **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento postup předpokládá, že jste použili nástroj SQLMetal ke generování souboru kódu z ukázkové databáze Northwind. Další informace najdete v oddílu požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Chcete-li přidat soubor kódu northwind do projektu  
  
1. Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2. V **přidat existující položku** dialogové okno, přejděte do c:\linqtest2\northwind.vb a potom klikněte na tlačítko **přidat**.  
  
     Soubor northwind.vb je přidán do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Nastavení připojení k databázi  
 Nejprve zkontrolujte připojení k databázi. Zejména Všimněte si, že název databáze, Northwnd, nemá žádné i znak. Pokud se generují chyby v dalších krocích, zkontrolujte soubor northwind.vb k určení, jak je napsaný částečné třídy Northwind.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>K nastavení a otestovat připojení k databázi  
  
1. Zadejte nebo vložte následující kód do `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. Testování aplikace v tomto okamžiku stisknutím klávesy F5.  
  
     A **konzoly** otevře se okno.  
  
     Ukončete aplikaci stisknutím klávesy Enter v **konzoly** okna, nebo kliknutím **Zastavit ladění** v sadě Visual Studio **ladění** nabídky.  
  
## <a name="creating-a-new-entity"></a>Vytvoření nové Entity  
 Vytvoření nové entity je jednoduché. Můžete vytvořit objekty (například `Customer`) s použitím `New` – klíčové slovo.  
  
 V této a v dalších částech provádíte změny pouze do místní mezipaměti. Žádné změny se odesílají do databáze až do okamžiku volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na konci tohoto návodu.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Chcete-li přidat nový objekt entity zákazníka  
  
1. Vytvořte nový `Customer` přidáním následujícího kódu před `Console.ReadLine` v `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. Stiskněte klávesu F5, chcete-li ladit řešení.  
  
     Výsledky, které jsou zobrazeny v okně konzoly jsou následující:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Všimněte si, že na novém řádku se nezobrazí ve výsledcích. Nová data dosud nebyla odeslána do databáze.  
  
3. Stisknutím klávesy Enter v **konzoly** okno chcete zastavit ladění.  
  
## <a name="updating-an-entity"></a>Aktualizují se Entity  
 V následujících krocích se budou načítat `Customer` objektu a změňte některou z jeho vlastností.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Chcete-li změnit název zákazníka  
  
- Přidejte následující kód nad `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Odstraňuje se entita  
 Pomocí stejného objektu zákazníka, můžete odstranit první pořadí.  
  
 Následující kód ukazuje, jak server vztahy mezi řádky a tom, jak můžete z databáze odstranit řádek.  
  
#### <a name="to-delete-a-row"></a>Odstranit řádek  
  
- Následující kód přidejte přímo nad `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Odeslání změn do databáze  
 Poslední krok vyžadovaný pro vytvoření, aktualizaci a odstraňování objektů je ve skutečnosti odeslat provedené změny do databáze. Bez tohoto kroku změny jsou pouze místní a nezobrazí se ve výsledcích dotazu.  
  
#### <a name="to-submit-changes-to-the-database"></a>K odeslání změn do databáze  
  
1. Vložte následující kód nad `Console.ReadLine`:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. Vložte následující kód (po `SubmitChanges`) zobrazíte před a po účinky odeslání změn:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. Stiskněte klávesu F5, chcete-li ladit řešení.  
  
     V okně konzoly se zobrazí takto:  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. Stisknutím klávesy Enter v **konzoly** okno chcete zastavit ladění.  
  
> [!NOTE]
>  Po přidání nového zákazníka, odešlete změny nelze provést toto řešení znovu, je-li tento parametr, vzhledem k tomu, že nemůžete přidat stejnou zákazníka znovu jako je. Pokud chcete znovu spustit řešení, změňte hodnotu ID zákazníka, které mají být přidány.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
