---
title: 'Návod: Manipulace s daty (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 2d45861569bc4a8b57427b01e107f87809203e11
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742732"
---
# <a name="walkthrough-manipulating-data-c"></a>Návod: Manipulace s daty (C#)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravy a odstraňování dat v databázi. Přidejte zákazníka, změňte název zákazníka a odstranit objednávky použijete kopii ukázkové databáze Northwind.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím Visual C# vývojovým nastavením.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
- Tento návod používá vyhrazené složky ("c:\linqtest6") pro uložení souborů. Vytvoření této složky, před zahájením návodu.  
  
- Ukázkovou databázi Northwind  
  
     Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft download. Pokyny najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databáze, zkopírujte do složky c:\linqtest6 northwnd.mdf souboru.  
  
- A C# soubor kód generovaný z databáze Northwind.  
  
     Tento soubor můžete vygenerovat pomocí Návrháře relací objektů nebo nástroji SQLMetal. Tento návod byl napsán s použitím nástroje SQLMetal s následujícím příkazovým řádkem:  
  
     **SqlMetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" / pluralize**  
  
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
  
1. V sadě Visual Studio **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
2. V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#** .  
  
3. V **šablony** podokně klikněte na tlačítko **konzolovou aplikaci**.  
  
4. V **název** zadejte **LinqDataManipulationApp**.  
  
5. V **umístění** pole, ověřte, kam chcete uložit soubory projektu.  
  
6. Klikněte na **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů LINQ a direktivy  
 Tento návod používá sestavení, která nemusí být nainstalován ve výchozím nastavení ve vašem projektu. Pokud System.Data.Linq není uveden jako odkaz v projektu, přidejte ji tak, jak je popsáno v následujících krocích:  
  
#### <a name="to-add-systemdatalinq"></a>Chcete-li přidat System.Data.Linq  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na tlačítko **přidat odkaz**.  
  
2. V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a klikněte na **OK**.  
  
     Sestavení se přidá do projektu.  
  
3. V horní části souboru program.cs přidejte následující direktivy:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento postup předpokládá, že jste použili nástroj SQLMetal ke generování souboru kódu z ukázkové databáze Northwind. Další informace najdete v oddílu požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Chcete-li přidat soubor kódu northwind do projektu  
  
1. Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2. V **přidat existující položku** dialogové okno, přejděte do c:\linqtest6\northwind.cs a potom klikněte na tlačítko **přidat**.  
  
     Soubor northwind.cs je přidán do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Nastavení připojení k databázi  
 Nejprve zkontrolujte připojení k databázi. Zejména Všimněte si, že databáze, Northwnd, nemá žádné i znak. Pokud se generují chyby v dalších krocích, zkontrolujte soubor northwind.cs k určení, jak je napsaný částečné třídy Northwind.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>K nastavení a otestovat připojení k databázi  
  
1. Zadejte nebo vložte následující kód do `Main` metodu do třídy Program:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. Testování aplikace v tomto okamžiku stisknutím klávesy F5.  
  
     A **konzoly** otevře se okno.  
  
     Aplikace můžete zavřít stisknutím klávesy Enter v **konzoly** okna, nebo kliknutím **Zastavit ladění** v sadě Visual Studio **ladění** nabídky.  
  
## <a name="creating-a-new-entity"></a>Vytvoření nové Entity  
 Vytvoření nové entity je jednoduché. Můžete vytvořit objekty (například `Customer`) s použitím `new` – klíčové slovo.  
  
 V této a v dalších částech provádíte změny pouze do místní mezipaměti. Žádné změny se odesílají do databáze až do okamžiku volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na konci tohoto návodu.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Chcete-li přidat nový objekt entity zákazníka  
  
1. Vytvořte nový `Customer` přidáním následujícího kódu před `Console.ReadLine();` v `Main` metody:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. Stiskněte klávesu F5, chcete-li ladit řešení.  
  
3. Stisknutím klávesy Enter v **konzoly** okna Zastavit ladění a pokračovat v tomto návodu.  
  
## <a name="updating-an-entity"></a>Aktualizují se Entity  
 V následujících krocích se budou načítat `Customer` objektu a změňte některou z jeho vlastností.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Chcete-li změnit název zákazníka  
  
- Přidejte následující kód nad `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Odstraňuje se entita  
 Pomocí stejného objektu zákazníka, můžete odstranit první pořadí.  
  
 Následující kód ukazuje, jak server vztahy mezi řádky a tom, jak můžete z databáze odstranit řádek. Přidejte následující kód před `Console.ReadLine` zobrazíte, jak je možné odstranit objekty:  
  
#### <a name="to-delete-a-row"></a>Odstranit řádek  
  
- Následující kód přidejte přímo nad `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Odeslání změn do databáze  
 Posledním krokem vyžadovaný pro vytvoření, aktualizaci a odstraňování objektů, je ve skutečnosti odeslání změn do databáze. Bez tohoto kroku změny jsou pouze místní a nezobrazí se ve výsledcích dotazu.  
  
#### <a name="to-submit-changes-to-the-database"></a>K odeslání změn do databáze  
  
1. Vložte následující kód nad `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. Vložte následující kód (po `SubmitChanges`) zobrazíte před a po účinky odeslání změn:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. Stiskněte klávesu F5, chcete-li ladit řešení.  
  
4. Stisknutím klávesy Enter v **konzoly** okno zavřít aplikaci.  
  
> [!NOTE]
>  Po přidání nového zákazníka, odešlete změny nelze provést toto řešení znovu, jak je. Pokud chcete znovu spustit řešení, změňte název zákazníka a ID zákazníka, které mají být přidány.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
