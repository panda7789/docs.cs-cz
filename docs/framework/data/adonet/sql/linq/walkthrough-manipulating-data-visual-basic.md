---
title: 'Návod: Manipulace s daty (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: a74216c53c45790b974938c7155e0b5e1043ac13
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792284"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>Návod: Manipulace s daty (Visual Basic)
Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravu a odstranění dat v databázi. Budete používat kopii ukázkové databáze Northwind pro přidání zákazníka, změnu názvu zákazníka a odstranění objednávky.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán pomocí Visual Basic nastavení vývoje.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento návod vyžaduje následující:  
  
- Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest2). Před zahájením tohoto návodu vytvořte tuto složku.  
  
- Ukázkovou databázi Northwind  
  
     Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft. Pokyny najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md). Po stažení databáze zkopírujte soubor northwnd. mdf do složky c:\linqtest2.  
  
- Visual Basic soubor kódu vygenerovaný z databáze Northwind.  
  
     Tento soubor můžete vygenerovat buď pomocí Návrhář relací objektů, nebo pomocí nástroje SQLMetal. Tento návod byl napsán pomocí nástroje SQLMetal s následujícím příkazovým řádkem:  
  
     **SQLMetal/Code: "c:\linqtest2\northwind.vb"/Language: VB "C:\linqtest2\northwnd.mdf"/pluralize**  
  
     Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Tento názorný postup se skládá ze šesti hlavních úloh:  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Vytvoření řešení v aplikaci Visual Studio.  
  
- Do projektu se přidává soubor s kódem databáze.  
  
- Vytváření nového objektu zákazníka  
  
- Změna jména kontaktu zákazníka.  
  
- Odstranění objednávky.  
  
- Odesílají se tyto změny do databáze Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Vytvoření řešení LINQ to SQL  
 V tomto prvním úkolu vytvoříte řešení sady Visual Studio, které obsahuje nezbytné odkazy pro sestavení a spuštění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Vytvoření řešení LINQ to SQL  
  
1. V nabídce **soubor** v aplikaci Visual Studio klikněte na **Nový projekt**.  
  
2. V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **Visual Basic**.  
  
3. V podokně **šablony** klikněte na **Konzolová aplikace**.  
  
4. Do pole **název** zadejte **LinqDataManipulationApp**.  
  
5. Klikněte na **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů a direktiv LINQ  
 Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu. Pokud `System.Data.Linq` není v projektu uvedena jako odkaz (klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení** a rozbalte uzel **odkazy** ), přidejte jej, jak je vysvětleno v následujícím postupu.  
  
#### <a name="to-add-systemdatalinq"></a>Přidání System. data. Linq  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.  
  
2. V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.  
  
     Sestavení je přidáno do projektu.  
  
3. V editoru kódu přidejte následující direktivy nad **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru s kódem Northwind do projektu  
 Tyto kroky předpokládají, že jste použili nástroj SQLMetal k vygenerování souboru kódu z ukázkové databáze Northwind. Další informace najdete v části požadavky výše v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Přidání souboru s kódem Northwind do projektu  
  
1. V nabídce **projekt** klikněte na položku **Přidat existující položku**.  
  
2. V dialogovém okně **Přidat existující položku** přejděte na c:\linqtest2\northwind.vb a pak klikněte na **Přidat**.  
  
     Do projektu se přidá soubor Northwind. vb.  
  
## <a name="setting-up-the-database-connection"></a>Nastavení připojení k databázi  
 Nejprve otestujte připojení k databázi. Pamatujte na to, že název databáze northwnd nemá žádný znak. Pokud generujete chyby v dalších krocích, zkontrolujte soubor Northwind. vb a určete, jak je částečná třída Northwind napsaná.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Nastavení a otestování připojení k databázi  
  
1. Do `Sub Main`následujícího pole zadejte nebo vložte následující kód:  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. V tomto okamžiku otestujte aplikaci stisknutím klávesy F5.  
  
     Otevře se okno **konzoly** .  
  
     Ukončete aplikaci stisknutím klávesy ENTER v okně **konzoly** nebo kliknutím na **Zastavit ladění** v nabídce **ladění** sady Visual Studio.  
  
## <a name="creating-a-new-entity"></a>Vytvoření nové entity  
 Vytvoření nové entity je jednoduché. Můžete vytvořit objekty (například `Customer`) `New` pomocí klíčového slova.  
  
 V tomto a v následujících částech provedete změny pouze v místní mezipaměti. Do databáze se neodesílají žádné změny, dokud nebudete volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> směrem ke konci tohoto návodu.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Přidání nového objektu entity zákazníka  
  
1. Vytvořte nový `Customer` přidáním následujícího `Console.ReadLine` kódu do `Sub Main`:  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. Pro ladění řešení stiskněte klávesu F5.  
  
     Výsledky, které se zobrazují v okně konzoly, jsou následující:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Všimněte si, že se nový řádek ve výsledcích nezobrazuje. Nová data nebyla dosud odeslána do databáze.  
  
3. V okně **konzoly** stiskněte klávesu ENTER a zastavte ladění.  
  
## <a name="updating-an-entity"></a>Aktualizace entity  
 V následujících krocích `Customer` navedete objekt a upravíte jednu z jeho vlastností.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Změna názvu zákazníka  
  
- Níže přidejte následující kód `Console.ReadLine()`:  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Odstranění entity  
 Pomocí stejného objektu zákazníka můžete odstranit první objednávku.  
  
 Následující kód ukazuje, jak se mají mezi řádky vymezit servery a jak odstranit řádek z databáze.  
  
#### <a name="to-delete-a-row"></a>Odstranění řádku  
  
- Přidejte následující kód, který je `Console.ReadLine()`právě uveden výše:  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Odesílání změn do databáze  
 Poslední krok potřebný k vytváření, aktualizaci a odstraňování objektů slouží ke skutečnému odeslání změn do databáze. Bez tohoto kroku budou vaše změny jenom místní a ve výsledcích dotazu se nezobrazí.  
  
#### <a name="to-submit-changes-to-the-database"></a>Odeslání změn do databáze  
  
1. Vložte následující kód hned `Console.ReadLine`takto:  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. Vložte následující kód (po `SubmitChanges`), chcete-li zobrazit před a za následky odeslání změn:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. Pro ladění řešení stiskněte klávesu F5.  
  
     Okno konzoly se zobrazí takto:  
  
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
  
4. V okně **konzoly** stiskněte klávesu ENTER a zastavte ladění.  
  
> [!NOTE]
> Po přidání nového zákazníka odesláním změn už toto řešení nemůžete znovu spustit tak, jak je, protože nemůžete přidat stejného zákazníka tak, jak je. Pokud chcete řešení znovu spustit, změňte hodnotu ID zákazníka, která se má přidat.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](learning-by-walkthroughs.md)
