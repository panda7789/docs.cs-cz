---
title: "Návod: Manipulace s daty (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b4bc7baee8e95243cf05a52f49c37aa2d8916666
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>Návod: Manipulace s daty (Visual Basic)
Tento názorný postup obsahuje základní začátku do konce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravy a odstraňování dat v databázi. Kopie v ukázkové databázi Northwind použije k přidání zákazníka, změňte název zákazníka a odstranění objednávky.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento názorný postup napsané pomocí jazyka Visual Basic – vývojové nastavení.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento postup vyžaduje následující:  
  
-   Tento návod používá k uložení souborů vyhrazené složky ("c:\linqtest2"). Než začnete návodu, vytvořte této složky.  
  
-   Ukázkovou databázi Northwind  
  
     Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft download. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Po stažení databázi, zkopírujte soubor northwnd.mdf ke složce c:\linqtest2.  
  
-   Kód jazyka Visual Basic soubor generovaný z databáze Northwind.  
  
     Tento soubor můžete vygenerovat pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nebo na SQLMetal nástroj. Tento názorný postup byla zapsána pomocí nástroje SQLMetal s následující příkazový řádek:  
  
     **SqlMetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" / pluralizovat**  
  
     Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá z šesti hlavní úlohy:  
  
-   Vytváření [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] řešení v [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Přidání souboru kódu databáze do projektu.  
  
-   Vytvoření nového objektu zákazníka.  
  
-   Úpravy jméno kontaktní osoby zákazníka.  
  
-   Odstranění pořadí.  
  
-   Odesílá se tyto změny v databázi Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytváření dotazu LINQ to SQL řešení  
 V této úloze první vytvoříte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] řešení, který obsahuje potřebné odkazy na sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Chcete-li vytvořit LINQ to SQL řešení  
  
1.  Na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **soubor** nabídky, klikněte na tlačítko **nový projekt**.  
  
2.  V **typy projektů** v podokně **nový projekt** dialogové okno, klikněte na tlačítko **jazyka Visual Basic**.  
  
3.  V **šablony** podokně klikněte na tlačítko **konzolové aplikace**.  
  
4.  V **název** zadejte **LinqDataManipulationApp**.  
  
5.  Click **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů LINQ a direktivy  
 Tento návod používá sestavení, které nemusí být nainstalovány ve výchozím nastavení ve vašem projektu. Pokud `System.Data.Linq` není uvedena jako odkaz ve vašem projektu (klikněte na tlačítko **zobrazit všechny soubory** v **Průzkumníku řešení** a rozbalte **odkazy** uzlu), přidat, jak je popsáno v Následující kroky.  
  
#### <a name="to-add-systemdatalinq"></a>To add System.Data.Linq  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **odkazy**a potom klikněte na **přidat odkaz na**.  
  
2.  V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET**, klikněte na tlačítko System.Data.Linq sestavení a pak klikněte na tlačítko **OK**.  
  
     Je sestavení přidáno do projektu.  
  
3.  V editoru kódu, přidejte následující direktivy výše **modul 1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru Northwind kódu do projektu  
 Tento postup předpokládá, že jste použili nástroj SQLMetal generování souboru kódu na základě ukázková databáze Northwind. Další informace najdete v části požadavky dříve v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Přidání souboru northwind kódu do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**.  
  
2.  V **přidat existující položku** dialogové okno, přejděte na c:\linqtest2\northwind.vb a pak klikněte na tlačítko **přidat**.  
  
     Soubor northwind.vb je přidán do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Nastavení připojení k databázi  
 Nejprve zkontrolujte připojení k databázi. Zejména Všimněte si, že název databáze, Northwnd, nemá žádné i znak. Pokud se v dalších krocích můžete způsobit chyby, zkontrolujte soubor northwind.vb k určení, jak je napsaný Northwind třídu.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Jak nastavit a otestovat připojení k databázi  
  
1.  Zadejte nebo vložte následující kód do `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  Stisknutím klávesy F5 testování aplikace v tomto okamžiku.  
  
     A **konzoly** otevře se okno.  
  
     Zavřete aplikaci stisknutím klávesy Enter v **konzoly** okno, nebo kliknutím **Zastavte ladění** na [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **ladění** nabídky.  
  
## <a name="creating-a-new-entity"></a>Vytvoření nové Entity  
 Vytvoření nové entity je jednoduchá. Můžete vytvořit objekty (například `Customer`) pomocí `New` – klíčové slovo.  
  
 V této a v následujících částech provádíte změny pouze do místní mezipaměti. Žádné změny se odesílají do databáze, dokud zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na konci tohoto průvodce.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Chcete-li přidat nový objekt entity zákazníka  
  
1.  Vytvořte novou `Customer` přidáním následujícího kódu před `Console.ReadLine` v `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  Stisknutím klávesy F5 ladění řešení.  
  
     Výsledky, které jsou zobrazeny v okně konzoly jsou následující:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Všimněte si, že nový řádek nezobrazí ve výsledcích. Nová data do databáze dosud nebyla odeslána.  
  
3.  Stiskněte klávesu Enter v **konzoly** okno přestane ladění.  
  
## <a name="updating-an-entity"></a>Aktualizace Entity  
 V následujících krocích se budou načítat `Customer` objekt a upravte jednu ze svých vlastností.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Chcete-li změnit název zákazníka  
  
-   Přidejte následující kód výše `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Odstranění Entity  
 Pomocí stejného objektu zákazníka, můžete odstranit první pořadí.  
  
 Následující kód ukazuje, jak severu vztahy mezi řádky a jak odstranit řádek z databáze.  
  
#### <a name="to-delete-a-row"></a>Chcete-li odstranit řádek  
  
-   Přidejte následující kód právě vyšší `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Odeslání změn do databáze  
 V posledním kroku potřebné k vytváření, aktualizaci a odstraňování objektů je ve skutečnosti odeslat provedené změny do databáze. Bez tohoto kroku změny jsou pouze místní a nezobrazí ve výsledcích dotazů.  
  
#### <a name="to-submit-changes-to-the-database"></a>Odeslat změny do databáze  
  
1.  Následující kód nad vložení `Console.ReadLine`:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  Vložte následující kód (po `SubmitChanges`) zobrazíte před a po důsledky odesílání změny:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  Stisknutím klávesy F5 ladění řešení.  
  
     V okně konzoly zobrazí se následující:  
  
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
  
4.  Stiskněte klávesu Enter v **konzoly** okno přestane ladění.  
  
> [!NOTE]
>  Po přidání nového zákazníka odesláním změny, nelze provést toto řešení znovu, protože nelze přidat tentýž zákazník znovu jako je. Znovu provést řešení, změňte hodnotu ID zákazníka, které chcete přidat.  
  
## <a name="see-also"></a>Viz také  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
