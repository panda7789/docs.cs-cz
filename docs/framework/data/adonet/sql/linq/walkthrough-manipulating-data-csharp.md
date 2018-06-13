---
title: 'Návod: Manipulace s daty (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: b9b19d4f9a1fb56ddabbf3584c1fb7bb29cd6d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357657"
---
# <a name="walkthrough-manipulating-data-c"></a>Návod: Manipulace s daty (C#)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravy a odstraňování dat v databázi. Kopie v ukázkové databázi Northwind použije k přidání zákazníka, změňte název zákazníka a odstranění objednávky.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento názorný postup napsané pomocí Visual C# – vývojové nastavení.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest6"). Než začnete návodu, vytvořte této složky.  
  
-   Ukázkovou databázi Northwind  
  
     Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databázi, zkopírujte soubor northwnd.mdf ke složce c:\linqtest6.  
  
-   C# soubor kódu vygenerovaném z databáze Northwind.  
  
     Tento soubor můžete vygenerovat pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo na SQLMetal nástroj. Tento názorný postup byla zapsána pomocí nástroje SQLMetal s následující příkazový řádek:  
  
     **SqlMetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" / pluralizovat**  
  
     Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavní úlohy:  
  
-   Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v sadě Visual Studio.  
  
-   Přidání souboru kódu databáze do projektu.  
  
-   Vytvoření nového objektu zákazníka.  
  
-   Úpravy jméno kontaktní osoby zákazníka.  
  
-   Odstranění pořadí.  
  
-   Odesílá se tyto změny v databázi Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytváření dotazu LINQ to SQL řešení  
 V této úloze první vytvoříte řešení sady Visual Studio, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Chcete-li vytvořit LINQ to SQL řešení  
  
1.  V sadě Visual Studio **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
2.  V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **Visual C#**.  
  
3.  V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.  
  
4.  V **název** zadejte **LinqDataManipulationApp**.  
  
5.  V **umístění** ověřte, kam chcete uložit soubory projektu.  
  
6.  Click **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů LINQ a direktivy  
 Tento návod používá sestavení, které nemusí být nainstalovány ve výchozím nastavení ve vašem projektu. Pokud System.Data.Linq není uvedena jako odkaz v projektu, přidejte ho, jak je popsáno v následujících krocích:  
  
#### <a name="to-add-systemdatalinq"></a>Chcete-li přidat System.Data.Linq  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.  
  
2.  V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.  
  
     Je sestavení přidáno do projektu.  
  
3.  V horní části souboru Program.cs přidejte následující direktivy:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento postup předpokládá, že jste použili nástroj SQLMetal generování souboru kódu na základě ukázková databáze Northwind. Další informace najdete v části požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Přidání souboru northwind kódu do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2.  V **přidat existující položku** dialogové okno, přejděte na c:\linqtest6\northwind.cs a pak klikněte na tlačítko **přidat**.  
  
     Soubor northwind.cs je přidán do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Nastavení připojení k databázi  
 Nejprve zkontrolujte připojení k databázi. Zejména Všimněte si, že databáze, Northwnd, nemá žádné i znak. Pokud se v dalších krocích můžete způsobit chyby, zkontrolujte soubor northwind.cs k určení, jak je napsaný Northwind třídu.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Jak nastavit a otestovat připojení k databázi  
  
1.  Zadejte nebo vložte následující kód do `Main` metodu v třídě Program:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  Stisknutím klávesy F5 testování aplikace v tomto okamžiku.  
  
     A **konzoly** otevře se okno.  
  
     Aplikace můžete zavřít stisknutím klávesy Enter v **konzoly** okno, nebo kliknutím **Zastavte ladění** v sadě Visual Studio **ladění** nabídky.  
  
## <a name="creating-a-new-entity"></a>Vytvoření nové Entity  
 Vytvoření nové entity je jednoduchá. Můžete vytvořit objekty (například `Customer`) pomocí `new` – klíčové slovo.  
  
 V této a v následujících částech provádíte změny pouze do místní mezipaměti. Žádné změny se odesílají do databáze, dokud zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na konci tohoto průvodce.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Chcete-li přidat nový objekt entity zákazníka  
  
1.  Vytvořte novou `Customer` přidáním následujícího kódu před `Console.ReadLine();` v `Main` metoda:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  Stisknutím klávesy F5 ladění řešení.  
  
3.  Stiskněte klávesu Enter v **konzoly** okno Zastavte ladění a pokračujte návodu.  
  
## <a name="updating-an-entity"></a>Aktualizace Entity  
 V následujících krocích se budou načítat `Customer` objekt a upravte jednu ze svých vlastností.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Chcete-li změnit název zákazníka  
  
-   Přidejte následující kód výše `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Odstranění Entity  
 Pomocí stejného objektu zákazníka, můžete odstranit první pořadí.  
  
 Následující kód ukazuje, jak severu vztahy mezi řádky a jak odstranit řádek z databáze. Přidejte následující kód před `Console.ReadLine` zobrazíte, jak můžete objekty odstraněny:  
  
#### <a name="to-delete-a-row"></a>Chcete-li odstranit řádek  
  
-   Přidejte následující kód právě vyšší `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Odeslání změn do databáze  
 V posledním kroku potřebné k vytváření, aktualizaci a odstraňování objektů, je ve skutečnosti odeslat provedené změny do databáze. Bez tohoto kroku změny jsou pouze místní a nezobrazí ve výsledcích dotazů.  
  
#### <a name="to-submit-changes-to-the-database"></a>Odeslat změny do databáze  
  
1.  Následující kód nad vložení `Console.ReadLine`:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  Vložte následující kód (po `SubmitChanges`) zobrazíte před a po důsledky odesílání změny:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  Stisknutím klávesy F5 ladění řešení.  
  
4.  Stiskněte klávesu Enter v **konzoly** okno aplikace se zavře.  
  
> [!NOTE]
>  Po přidání nového zákazníka odesláním změny, nelze provést toto řešení znovu, protože je. Znovu provést řešení, změňte název odběratele a ID zákazníka, které chcete přidat.  
  
## <a name="see-also"></a>Viz také  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
