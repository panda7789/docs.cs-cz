---
title: "Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbdc074bef64413b8b25709e48bba49f296ecb95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a>Postupy: Počet, suma nebo průměr dat pomocí LINQ (Visual Basic)
Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze a spouštět dotazy.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která provádí dotazy na databázi systému SQL Server. Ukázka počty sčítá a zobrazí průměr výsledky pomocí `Aggregate` a `Group By` klauzule. Další informace najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) a [skupiny pomocí klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 V příkladech v tomto tématu použijte ukázková databáze Northwind. Pokud ve svém vývojovém počítači nemáte ukázková databáze Northwind, si můžete stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) webu. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
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
  
3.  Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objekt pro váš projekt. Tento objekt obsahuje kód, který musíte mít přístup k těchto tabulek a pro přístup k jednotlivých objektů a kolekcí pro každou tabulku. <xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML. Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a dotazování tabulky určeného Návrhář relací objektů.  
  
     Přidejte následující kód, který `Load` události při dotazování tabulky, které jsou zveřejněné jako vlastnosti vaší <xref:System.Data.Linq.DataContext> a počet, sum a průměrná výsledky. Ukázce se používá `Aggregate` klauzule dotazu pro jeden výsledek a `Group By` klauzule zobrazíte v průměru pro seskupené výsledky.  
  
     [!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]  
  
4.  Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Klauzule Group By](../../../../visual-basic/language-reference/queries/group-by-clause.md)
