---
title: 'Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112359"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)
Jazykově integrovaný dotaz (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy proti databázi serveru SQL Server. Ukázka určuje minimální a maximální hodnoty výsledků `Aggregate` pomocí `Group By` klauzule a. Další informace naleznete [v tématu Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and Group By [Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Příklady v tomto tématu používají ukázkovou databázi Northwind. Pokud tuto databázi ve vývojovém počítači nemáte, můžete ji stáhnout ze služby Stažení softwaru. Pokyny naleznete v [tématu Stahování ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>Vytvoření připojení k databázi  
  
1. V sadě Visual Studio otevřete**Průzkumníka** **databáze**/serveru klepnutím na**Průzkumník a** **Průzkumník**/serveru v nabídce **Zobrazení.**  
  
2. Klepněte pravým tlačítkem myši na **položku Datová připojení** v**Průzkumníkovi databáze** **serveru**/a potom klepněte na příkaz **Přidat připojení**.  
  
3. Zadejte platné připojení k ukázkové databázi Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Přidání projektu, který obsahuje soubor LINQ do souboru SQL  
  
1. V sadě Visual Studio v nabídce **Soubor** přejděte na **Nový** a potom klikněte na **Project**. Jako typ projektu vyberte aplikaci Visual Basic **Windows Forms Application.**  
  
2. V nabídce **Project** klikněte na **Add New Item**. Vyberte šablonu **položky LINQ na třídy SQL.**  
  
3. Pojmenujte soubor `northwind.dbml`. Klikněte na **Přidat**. Objekt relační návrhář (O/R Designer) je otevřen pro soubor northwind.dbml.  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>Přidání tabulek do dotazu do Návrháře O/R  
  
1. V**Průzkumníku databáze** **serveru**/rozbalte připojení k databázi Northwind. Rozbalte složku **Tabulky.**  
  
     Pokud jste zavřeli O/R Designer, můžete jej znovu otevřít poklepáním na soubor northwind.dbml, který jste přidali dříve.  
  
2. Klikněte na tabulku Zákazníci a přetáhněte ji do levého podokna návrháře. Klikněte na tabulku Objednávky a přetáhněte ji do levého podokna návrháře.  
  
     Návrhář vytvoří `Customer` nové `Order` a objekty pro váš projekt. Všimněte si, že návrhář automaticky detekuje relace mezi tabulkami a vytvoří podřízené vlastnosti pro související objekty. Technologie IntelliSense například zobrazí, `Customer` že `Orders` objekt má vlastnost pro všechny objednávky související s tímto zákazníkem.  
  
3. Uložte změny a zavřete návrháře.  
  
4. Uložte projekt.  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>Přidání kódu k dotazování databáze a zobrazení výsledků  
  
1. Z **panelu nástrojů** <xref:System.Windows.Forms.DataGridView> přetáhněte ovládací prvek do výchozího formuláře systému Windows pro projekt Form1.  
  
2. Poklepáním na formulář1 přidejte kód k `Load` události formuláře.  
  
3. Když jste přidali tabulky do Návrháře O/R, návrhář přidal <xref:System.Data.Linq.DataContext> objekt pro váš projekt. Tento objekt obsahuje kód, který je nutné mít pro přístup k těmto tabulkám, kromě jednotlivých objektů a kolekcí pro každou tabulku. Objekt <xref:System.Data.Linq.DataContext> projektu je pojmenován na základě názvu souboru DBML. Pro tento projekt <xref:System.Data.Linq.DataContext> je `northwindDataContext`objekt pojmenován .  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotaz tabulky určené O/R Designer.  
  
     Přidejte následující kód `Load` k události. Tento kód dotazuje tabulky, které jsou vystaveny jako vlastnosti kontextu dat a určuje minimální a maximální hodnoty pro výsledky. Ukázka používá `Aggregate` klauzuli k dotazování na `Group By` jeden výsledek a klauzule zobrazit průměr pro seskupené výsledky.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Stisknutím **klávesy F5** spusťte projekt a zobrazte výsledky.  
  
## <a name="see-also"></a>Viz také

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [Technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
