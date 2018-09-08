---
title: 'Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 50a4dff90dc1ce02869978f1da147e530cefc3e1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44176693"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Postupy: Volání uložené procedury pomocí LINQ (Visual Basic)
Language Integrated Query (LINQ) usnadňuje přístup k informacím o databáze, včetně databázové objekty, jako uložené procedury.  
  
 Následující příklad ukazuje, jak vytvořit aplikaci, která volá uloženou proceduru v databázi serveru SQL Server. Vzorek ukazuje, jak volat dvě různé uložené procedury v databázi. Každý postup vrátí výsledky dotazu. Jeden procedura používá vstupní parametry a další postup nepřijímá parametry.  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Chcete-li přidat úložné procedury do Návrháře relací objektů  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind. Rozbalte **uložené procedury** složky.  
  
     Pokud jste zavřeli O/R Designer, můžete ho znovu otevřít poklikáním northwind.dbml soubor, který jste přidali dříve.  
  
2.  Klikněte na tlačítko **prodeje podle roku** uložené procedury a přetáhněte ho do pravého podokna návrháře. Klikněte na tlačítko **deset nejvíce nákladné produktů** uložené procedury, přetáhněte ho do pravého podokna návrháře.  
  
3.  Uložte změny a zavřete návrháře.  
  
4.  Uložte projekt.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Chcete-li přidat kód pro zobrazení výsledků uložených procedur  
  
1.  Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.  
  
2.  Klikněte dvakrát na Form1 přidat kód pro jeho `Load` událostí.  
  
3.  Když jste přidali do Návrháře relací objektů uložených procedur, přidá návrháře <xref:System.Data.Linq.DataContext> objektu pro váš projekt. Tento objekt obsahuje kód, který musí mít pro přístup k těmto postupy. <xref:System.Data.Linq.DataContext> Objektu pro projekt je s názvem podle názvu souboru .dbml. Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> v kódu a volání určené metody uloženou proceduru Návrháře relací objektů. K vytvoření vazby <xref:System.Windows.Forms.DataGridView> objektu, možná budete muset vynutit dotaz tak, aby okamžitě je spouštějte voláním <xref:System.Linq.Enumerable.ToList%2A> metodu na výsledky uložené procedury.  
  
     Přidejte následující kód, který `Load` události a volání buď uložené procedury jako metody pro datový kontext.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  Stisknutím klávesy F5 spusťte váš projekt a prohlédněte si výsledky.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/index.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
