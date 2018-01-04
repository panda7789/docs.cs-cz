---
title: "Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bb7b970d42a44ad925883b7a935aae386b1f1d5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)
Language-Integrated Query (LINQ) usnadňuje přístup k informacím databáze, včetně databázové objekty, jako uložené procedury.  
  
 Následující příklad ukazuje, jak vytvořit aplikaci, která volá uloženou proceduru v databázi systému SQL Server. Ukázka ukazuje způsob volání dva různé postupy uložené v databázi. Každý postup vrátí výsledky dotazu. Jeden procedura používá vstupní parametry a další postup nemusí provádět žádné parametry.  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Chcete-li přidat uložené procedury pro Návrhář relací objektů  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind. Rozbalte **uložené procedury** složky.  
  
     Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím na soubor northwind.dbml, které jste přidali dříve.  
  
2.  Klikněte **prodeje podle roku** uložené procedury a přetáhněte ji do pravého podokna návrháře. Klikněte **deset nejvíce nákladné produkty** uložené procedury, přetáhněte ji do pravého podokna návrháře.  
  
3.  Uložte změny a zavřít návrháře.  
  
4.  Uložte projekt.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Chcete-li přidat kód, který zobrazí výsledky uložené procedury  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.  
  
2.  Dvakrát klikněte na Form1 přidání kódu k jeho `Load` událostí.  
  
3.  Pokud jste přidali uložené procedury Návrhář relací objektů, návrháře přidat <xref:System.Data.Linq.DataContext> objekt pro váš projekt. Tento objekt obsahuje kód, který musí mít přístup k tyto postupy. <xref:System.Data.Linq.DataContext> Objektu pro název projektu na základě názvu souboru DBML. Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a volání metody uložené procedury určeného Návrhář relací objektů. K vytvoření vazby <xref:System.Windows.Forms.DataGridView> objektu, možná budete muset vynutit dotaz provést okamžitě voláním <xref:System.Linq.Enumerable.ToList%2A> metodu výsledky uložené procedury.  
  
     Přidejte následující kód, který `Load` události zavolat buď uložené procedury, které jsou zveřejněné jako metody pro vaše data kontextu.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Stisknutím klávesy F5 spusťte projekt a zobrazit výsledky.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
