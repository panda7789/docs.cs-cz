---
title: 'Postupy: Řazení výsledků dotazu pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: d2114e908077ec947164a28f48841282abefda2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053740"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a>Postupy: Řazení výsledků dotazu pomocí LINQ (Visual Basic)
Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server a řadí výsledky podle několika polí pomocí `Order By` klauzuli. Pořadí řazení pro každé pole můžete vzestupně nebo sestupně. Další informace najdete v tématu [klauzuli ORDER by](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 V příkladech v tomto tématu se používá ukázkové databáze Northwind. Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Chcete-li vytvořit připojení k databázi  
  
1. V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.  
  
2. Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.  
  
3. Zadejte platné připojení k ukázkové databázi Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL  
  
1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**. Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.  
  
2. Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**. Vyberte **třídy LINQ to SQL** šablony položky.  
  
3. Pojmenujte soubor `northwind.dbml`. Klikněte na **Přidat**. Návrhář relací objektů (O/R Designer), je otevřené northwind.dbml souboru.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Přidání tabulek do dotazu do Návrháře relací objektů  
  
1. V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind. Rozbalte **tabulky** složky.  
  
     Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.  
  
2. Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři. Klikněte na tabulky objednávky a přetáhněte ji do levého podokna v návrháři.  
  
     Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt. Všimněte si, že návrhář automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci. Například technologie IntelliSense se zobrazí, který `Customer` objekt má `Orders` týkající se vlastností pro všechny objednávky daného zákazníka.  
  
3. Uložte změny a zavřete návrháře.  
  
4. Uložte projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků  
  
1. Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.  
  
2. Dvakrát klikněte na Přidat kód pro Form1 `Load` události formuláře.  
  
3. Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu do projektu. Tento objekt obsahuje kód, který musí mít pro přístup k těchto tabulek a pro přístup k jednotlivým objekty a kolekce pro každou tabulku. <xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml. Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.  
  
     Přidejte následující kód, který `Load` událostí do tabulky, které jsou vystaveny jako vlastnosti kontextu dat a řazení výsledků dotazu. Dotaz výsledky seřadí podle čísel objednávek zákazníků v sestupném pořadí. Zákazníci, kteří mají stejný počet objednávek jsou řazeny podle názvu společnosti ve vzestupném pořadí (výchozí).  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.  
  
## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
