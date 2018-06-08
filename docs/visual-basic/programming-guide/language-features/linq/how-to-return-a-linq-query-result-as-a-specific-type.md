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
ms.openlocfilehash: 2c3a10ed901832846da058018a91349be0c2495b
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827082"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Postupy: Vrácení výsledku dotazu LINQ jako specifického typu (Visual Basic)
Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze a spouštět dotazy. Ve výchozím nastavení dotazů LINQ vrátí seznam objektů jako anonymní typ. Můžete také určit, že dotaz vrátí seznam konkrétního typu pomocí `Select` klauzule.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi systému SQL Server a projekty výsledky jako specifického typu s názvem. Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [klauzule Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
 V příkladech v tomto tématu použijte ukázková databáze Northwind. Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Chcete-li vytvořit připojení k databázi  
  
1.  V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **Průzkumníka serveru**/**databáze Průzkumník** na **zobrazení** nabídky.  
  
2.  Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze** a pak klikněte na **přidat připojení**.  
  
3.  Zadejte platné připojení k ukázková databáze Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Chcete-li přidat projekt, který obsahuje LINQ to SQL souboru  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**. Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**. Vyberte **třídy LINQ to SQL** šablony položky.  
  
3.  Název souboru `northwind.dbml`. Klikněte na tlačítko **přidat**. Návrhář relací objektů (Návrhář relací objektů), je otevřené northwind.dbml souboru.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Chcete-li přidat tabulky k dotazování na Návrhář relací objektů  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind. Rozbalte **tabulky** složky.  
  
     Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím na soubor northwind.dbml, které jste přidali dříve.  
  
2.  Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře.  
  
     Vytvoří novou návrháře `Customer` objekt pro váš projekt. Výsledek dotazu jako můžete promítnout `Customer` typu nebo jako typ, který vytvoříte. Tato ukázka vytvoříte nový typ v pozdějším postupu a výsledek dotazu jako tento typ projektu.  
  
3.  Uložte změny a zavřít návrháře.  
  
4.  Uložte projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Chcete-li přidat kód pro dotazování databáze a zobrazit výsledky  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.  
  
2.  Dvakrát klikněte na Form1 k úpravě Form1 třídy.  
  
3.  Po `End Class` příkaz Form1 třídy, přidejte následující kód k vytvoření `CustomerInfo` typ k ukládání výsledků dotazu pro tuto ukázku.  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objektu do projektu. Tento objekt obsahuje kód, který musíte mít přístup k těchto tabulek a pro přístup k jednotlivých objektů a kolekcí pro každou tabulku. <xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML. Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určeného Návrhář relací objektů.  
  
     V `Load` událostí Form1 třídy, přidejte následující kód k dotazování tabulky, které jsou zveřejněné jako vlastnosti vaše data kontextu. `Select` Klauzuli dotazu se vytvoří nové `CustomerInfo` typ místo anonymní typ pro každou položku výsledku dotazu.  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
