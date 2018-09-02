---
title: 'Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 720660153cb357c11168ab45ebf8343559faf82a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393243"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)
Language Integrated Query (LINQ) usnadňuje přístup k informacím o databázi a spouštění dotazů. Ve výchozím nastavení dotazy LINQ vrací seznam objektů jako anonymního typu. Můžete také určit, že dotaz vrátí seznam určitého typu pomocí `Select` klauzuli.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi serveru SQL Server a projekty výsledky jako konkrétní pojmenovaného typu. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
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
  
2.  Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.  
  
     Vytvoří nový Návrhář `Customer` objektu pro váš projekt. Jako výsledek dotazu můžete promítnout `Customer` typ nebo typ, který vytvoříte. Tato ukázka vytvoří nový typ v pozdějším postupu a výsledek dotazu jako tento typ projektu.  
  
3.  Uložte změny a zavřete návrháře.  
  
4.  Uložte projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Chcete-li přidat kód pro dotaz na databázi a zobrazení výsledků  
  
1.  Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.  
  
2.  Klikněte dvakrát na Form1 upravte třídu Form1.  
  
3.  Po `End Class` příkazu Form1 třídy, přidejte následující kód k vytvoření `CustomerInfo` typu k ukládání výsledků dotazu pro tuto ukázku.  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu do projektu. Tento objekt obsahuje kód, který musí mít pro přístup k těchto tabulek a pro přístup k jednotlivým objekty a kolekce pro každou tabulku. <xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml. Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určené Návrháře relací objektů.  
  
     V `Load` událost třídy Form1, přidejte následující kód k dotazování tabulky, které jsou vystaveny jako vlastnosti datového kontextu. `Select` Klauzule dotazu se vytvoří nový `CustomerInfo` typ místo anonymního typu pro každou položku výsledku dotazu.  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
