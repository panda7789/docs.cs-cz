---
title: 'Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 942cb889c595f8caaf86dee1c025a935bd7db1b1
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934776"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)
Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server. Ukázka počítá, sečte a předběhli aktuální fázi výsledky pomocí `Aggregate` a `Group By` klauzule. Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [klauzule Group](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 V příkladech v tomto tématu se používá ukázkové databáze Northwind. Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Chcete-li vytvořit připojení k databázi  
  
1.  V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.  
  
2.  Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze** a potom klikněte na tlačítko **přidat připojení**.  
  
3.  Zadejte platné připojení k ukázkové databázi Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Chcete-li přidat projekt, který obsahuje souboru LINQ to SQL  
  
1.  V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**. Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**. Vyberte **třídy LINQ to SQL** šablony položky.  
  
3.  Název souboru `northwind.dbml`. Klikněte na tlačítko **přidat**. Návrhář relací objektů (O/R Designer), je otevřené northwind.dbml souboru.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Přidání tabulek do dotazu do Návrháře relací objektů  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind. Rozbalte **tabulky** složky.  
  
     Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.  
  
2.  Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři. Klikněte na tabulky objednávky a přetáhněte ji do levého podokna v návrháři.  
  
     Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt. Všimněte si, že návrhář automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci. Například technologie IntelliSense se zobrazí, který `Customer` objekt má `Orders` týkající se vlastností pro všechny objednávky daného zákazníka.  
  
3.  Uložte změny a zavřete návrháře.  
  
4.  Uložte projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků  
  
1.  Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.  
  
2.  Dvakrát klikněte na Přidat kód pro Form1 `Load` události formuláře.  
  
3.  Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu pro váš projekt. Tento objekt obsahuje kód, který musí mít pro přístup k těchto tabulek a pro přístup k jednotlivým objekty a kolekce pro každou tabulku. <xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml. Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.  
  
     Přidejte následující kód, který `Load` událostí k dotazování tabulky, které jsou vystaveny jako vlastnosti vaší <xref:System.Data.Linq.DataContext> a počet součet a průměr výsledky. Ukázka používá `Aggregate` klauzule dotazu pro jeden výsledek a `Group By` seskupené klauzule zobrazíte průměr pro výsledky.  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Klauzule Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md)
