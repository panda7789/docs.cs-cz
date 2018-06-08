---
title: 'Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)'
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
ms.openlocfilehash: f1b997272bc65a3702353f1f7db02fa330a19c21
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826887"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu pomocí LINQ (Visual Basic)
Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze a spouštět dotazy.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi systému SQL Server. Ukázka Určuje minimální a maximální hodnoty výsledků pomocí `Aggregate` a `Group By` klauzule. Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [skupiny pomocí klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
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
  
2.  Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře. Klikněte na tabulku objednávky a přetáhněte ji do levého podokna návrháře.  
  
     Návrhář vytvoří nové `Customer` a `Order` objekty pro váš projekt. Všimněte si, že návrháře automaticky zjišťuje vztahy mezi tabulkami a vytvoří podřízené vlastnosti pro objekty v relaci. Například, IntelliSense se ukazují, že `Customer` objekt má `Orders` vlastnost pro všechny objednávky týkající se tohoto zákazníka.  
  
3.  Uložte změny a zavřít návrháře.  
  
4.  Uložte projekt.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Chcete-li přidat kód pro dotazování databáze a zobrazit výsledky  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.  
  
2.  Dvakrát klikněte na Form1 k přidejte kód, který `Load` události formuláře.  
  
3.  Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objekt pro váš projekt. Tento objekt obsahuje kód, který musí mít přístup k těchto tabulkách, kromě jednotlivých objektů a kolekcí pro každou tabulku. <xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML. Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určeného Návrhář relací objektů.  
  
     Přidejte následující kód, který `Load` událostí. Tento kód se dotazuje tabulky, které jsou zveřejněné jako vlastnosti vaše data kontextu a určuje minimální a maximální hodnoty výsledků. Příklad používá mu `Aggregate` klauzule dotazu pro jeden výsledek a `Group By` klauzule zobrazíte v průměru pro seskupené výsledky.  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
