---
title: 'Návod: Manipulace s daty (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 8941ac30a67406346e5448ca5af4af8512d168a8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781001"
---
# <a name="walkthrough-manipulating-data-c"></a>Návod: Manipulace s daty (C#)
Tento návod poskytuje základní kompletní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scénář pro přidání, úpravu a odstranění dat v databázi. Budete používat kopii ukázkové databáze Northwind pro přidání zákazníka, změnu názvu zákazníka a odstranění objednávky.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Tento návod byl napsán s použitím nastavení C# vizuálního vývoje.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento návod vyžaduje následující:  
  
- Tento návod používá pro uchovávání souborů vyhrazenou složku (c:\linqtest6). Před zahájením tohoto návodu vytvořte tuto složku.  
  
- Ukázkovou databázi Northwind  
  
     Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu služby Stažení softwaru společnosti Microsoft. Pokyny najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md). Po stažení databáze zkopírujte soubor northwnd. mdf do složky c:\linqtest6.  
  
- Soubor C# kódu vygenerovaný z databáze Northwind.  
  
     Tento soubor můžete vygenerovat buď pomocí Návrhář relací objektů, nebo pomocí nástroje SQLMetal. Tento návod byl napsán pomocí nástroje SQLMetal s následujícím příkazovým řádkem:  
  
     **SQLMetal/Code: "c:\linqtest6\northwind.cs"/Language: CSharp "C:\linqtest6\northwnd.mdf"/pluralize**  
  
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
  
1. V nabídce **soubor** v aplikaci Visual Studio přejděte na **Nový**a klikněte na **projekt**.  
  
2. V podokně **typy projektů** v dialogovém okně **Nový projekt** klikněte na položku **vizuál C#** .  
  
3. V podokně **šablony** klikněte na **Konzolová aplikace**.  
  
4. Do pole **název** zadejte **LinqDataManipulationApp**.  
  
5. V poli **umístění** ověřte, kam chcete uložit soubory projektu.  
  
6. Klikněte na **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Přidání odkazů a direktiv LINQ  
 Tento návod používá sestavení, která nemusí být nainstalována ve výchozím nastavení v projektu. Pokud System. data. Linq není v projektu uveden jako odkaz, přidejte jej, jak je vysvětleno v následujícím postupu:  
  
#### <a name="to-add-systemdatalinq"></a>Přidání System. data. Linq  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a pak klikněte na **Přidat odkaz**.  
  
2. V dialogovém okně **Přidat odkaz** klikněte na položku **.NET**, klikněte na položku sestavení System. data. Linq a pak klikněte na tlačítko **OK**.  
  
     Sestavení je přidáno do projektu.  
  
3. Do horní části Program.cs přidejte následující direktivy:  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Přidání souboru s kódem Northwind do projektu  
 Tyto kroky předpokládají, že jste použili nástroj SQLMetal k vygenerování souboru kódu z ukázkové databáze Northwind. Další informace najdete v části požadavky výše v tomto návodu.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Přidání souboru s kódem Northwind do projektu  
  
1. V nabídce **projekt** klikněte na položku **Přidat existující položku**.  
  
2. V dialogovém okně **Přidat existující položku** přejděte na c:\linqtest6\northwind.cs a pak klikněte na **Přidat**.  
  
     Soubor northwind.cs se přidá do projektu.  
  
## <a name="setting-up-the-database-connection"></a>Nastavení připojení k databázi  
 Nejprve otestujte připojení k databázi. Pamatujte na to, že databáze northwnd nemá žádný znak. Pokud generujete chyby v dalších krocích, zkontrolujte soubor northwind.cs a určete, jak je částečná třída Northwind napsaná.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Nastavení a otestování připojení k databázi  
  
1. Zadejte nebo vložte následující kód do `Main` metody ve třídě program:  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. V tomto okamžiku otestujte aplikaci stisknutím klávesy F5.  
  
     Otevře se okno **konzoly** .  
  
     Aplikaci můžete zavřít stisknutím klávesy ENTER v okně **konzoly** nebo kliknutím na **Zastavit ladění** v nabídce **ladění** aplikace Visual Studio.  
  
## <a name="creating-a-new-entity"></a>Vytvoření nové entity  
 Vytvoření nové entity je jednoduché. Můžete vytvořit objekty (například `Customer`) `new` pomocí klíčového slova.  
  
 V tomto a v následujících částech provedete změny pouze v místní mezipaměti. Do databáze se neodesílají žádné změny, dokud nebudete volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> směrem ke konci tohoto návodu.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Přidání nového objektu entity zákazníka  
  
1. Vytvořte nový `Customer` přidáním následujícího `Console.ReadLine();` kódu do `Main` metody:  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. Pro ladění řešení stiskněte klávesu F5.  
  
3. V okně **konzoly** stiskněte klávesu ENTER a zastavte ladění a pokračujte v tomto postupu.  
  
## <a name="updating-an-entity"></a>Aktualizace entity  
 V následujících krocích `Customer` navedete objekt a upravíte jednu z jeho vlastností.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Změna názvu zákazníka  
  
- Níže přidejte následující kód `Console.ReadLine();`:  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Odstranění entity  
 Pomocí stejného objektu zákazníka můžete odstranit první objednávku.  
  
 Následující kód ukazuje, jak se mají mezi řádky vymezit servery a jak odstranit řádek z databáze. `Console.ReadLine` Chcete-li zjistit, jak lze objekty odstranit, přidejte následující kód:  
  
#### <a name="to-delete-a-row"></a>Odstranění řádku  
  
- Přidejte následující kód, který je `Console.ReadLine();`právě uveden výše:  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Odesílání změn do databáze  
 Poslední krok potřebný k vytváření, aktualizaci a odstraňování objektů slouží ke skutečnému odeslání změn do databáze. Bez tohoto kroku budou vaše změny jenom místní a ve výsledcích dotazu se nezobrazí.  
  
#### <a name="to-submit-changes-to-the-database"></a>Odeslání změn do databáze  
  
1. Vložte následující kód hned `Console.ReadLine`takto:  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. Vložte následující kód (po `SubmitChanges`), chcete-li zobrazit před a za následky odeslání změn:  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. Pro ladění řešení stiskněte klávesu F5.  
  
4. V okně **konzoly** stiskněte klávesu ENTER, aby se aplikace zavřela.  
  
> [!NOTE]
> Po přidání nového zákazníka odesláním změn už toto řešení nebudete moct znovu spustit, jak je. Pokud chcete řešení znovu spustit, změňte jméno zákazníka a ID zákazníka, které chcete přidat.  
  
## <a name="see-also"></a>Viz také:

- [Učení podle návodů](learning-by-walkthroughs.md)
