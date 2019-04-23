---
title: 'Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: 8770a8761af4b55394d9280b21d2a6a5b71b6ed5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304893"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)
Language-Integrated Query (LINQ) dotazy umožňují snadno přistupovat k informací o databázi a hodnot v databázi.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která načte a informací o aktualizacích v databázi serveru SQL Server.  
  
 V příkladech v tomto tématu se používá ukázkové databáze Northwind. Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete si ho stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
### <a name="to-create-a-connection-to-a-database"></a>Chcete-li vytvořit připojení k databázi  
  
1. V sadě Visual Studio, otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **zobrazení** nabídky a pak vyberte **Průzkumníka serveru** / **Databázového Průzkumníka**.  
  
2. Klikněte pravým tlačítkem na **datová připojení** v **Průzkumníka serveru**/**Průzkumník databáze**a klikněte na tlačítko **přidat připojení**.  
  
3. Zadejte platné připojení k ukázkové databázi Northwind.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Přidání projektu s LINQ na soubor SQL  
  
1. V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**. Výběr jazyka Visual Basic **formulářová aplikace Windows** jako typ projektu.  
  
2. Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**. Vyberte **třídy LINQ to SQL** šablony položky.  
  
3. Pojmenujte soubor `northwind.dbml`. Klikněte na **Přidat**. Návrhář relací objektů (O/R Designer), je otevřené `northwind.dbml` souboru.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Chcete-li přidat tabulky k dotazování a modifikaci do návrháře  
  
1. V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind. Rozbalte **tabulky** složky.  
  
     Pokud jste zavřeli O/R Designer, můžete znovu otevřít jej dvojitým kliknutím `northwind.dbml` soubor, který jste přidali dříve.  
  
2. Klikněte na tabulce Zákazníci a přetáhněte ji do levého podokna v návrháři.  
  
     Návrhář vytvoří nový objekt zákazníka pro váš projekt.  
  
3. Uložte změny a zavřete návrháře.  
  
4. Uložte projekt.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Přidání kódu k úpravám databáze a zobrazení výsledků  
  
1. Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> ovládacího prvku na výchozí formulář Windows pro váš projekt Form1.  
  
2. Při přidání tabulky do Návrháře relací objektů, přidá návrháře <xref:System.Data.Linq.DataContext> objektu do projektu. Tento objekt obsahuje kód, který můžete použít pro přístup k tabulce Zákazníci. Také obsahuje kód, který definuje místní objekt zákazníka a kolekci zákazníků pro tabulku. <xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu souboru .dbml. Pro tento projekt <xref:System.Data.Linq.DataContext> se nazývá `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> objekt v kódu a dotazování a úprava zákazníkům kolekci specifikované souborem Návrháře relací objektů. Změny provedené ke kolekci zákazníků se neprojeví v databázi, dokud odeslání je voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodu <xref:System.Data.Linq.DataContext> objektu.  
  
     Klikněte dvakrát na Windows formuláři Form1, přidat kód pro <xref:System.Windows.Forms.Form.Load> událost dotaz Zákazníci tabulku, která je vystavena jako vlastnost vaše <xref:System.Data.Linq.DataContext>. Přidejte následující kód:  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3. Z **nástrojů**, přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky na formuláři. Vyberte první `Button` ovládacího prvku. V **vlastnosti** okno, nastaveno `Name` z `Button` ovládací prvek `AddButton` a `Text` k `Add`. Vyberte druhé tlačítko a nastavte `Name` vlastnost `UpdateButton` a `Text` vlastnost `Update`. Vyberte třetí tlačítko a nastavte `Name` vlastnost `DeleteButton` a `Text` vlastnost `Delete`.  
  
4. Dvakrát klikněte **přidat** tlačítko Přidat kód pro jeho `Click` událostí. Přidejte následující kód:  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5. Dvakrát klikněte **aktualizace** tlačítko Přidat kód pro jeho `Click` událostí. Přidejte následující kód:  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6. Dvakrát klikněte **odstranit** tlačítko Přidat kód pro jeho `Click` událostí. Přidejte následující kód:  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7. Stisknutím klávesy F5 spusťte váš projekt. Klikněte na tlačítko **přidat** přidáte nový záznam. Klikněte na tlačítko **aktualizace** Upravit nový záznam. Klikněte na tlačítko **odstranit** nový záznam odstranit.  
  
## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
