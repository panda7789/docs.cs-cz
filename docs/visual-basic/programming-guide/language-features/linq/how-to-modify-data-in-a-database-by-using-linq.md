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
ms.openlocfilehash: 617bb62f9009c507658b5d1262657cb4dfa860e9
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827108"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)
Language-Integrated Query (LINQ) dotazy usnadňují přístup k informacím databáze a upravte hodnoty v databázi.  
  
 Následující příklad ukazuje, jak vytvořit novou aplikaci, která načte a informace o aktualizacích v databázi systému SQL Server.  
  
 V příkladech v tomto tématu použijte ukázková databáze Northwind. Pokud jste tuto databázi ve svém vývojovém počítači, můžete ji stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [stažení ukázkové databáze](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
### <a name="to-create-a-connection-to-a-database"></a>Chcete-li vytvořit připojení k databázi  
  
1.  V sadě Visual Studio otevřete **Průzkumníka serveru**/**Průzkumník databáze** kliknutím **zobrazení** nabídce a potom vyberte **Průzkumníka serveru** / **Databáze Explorer**.  
  
2.  Klikněte pravým tlačítkem na **připojení dat** v **Průzkumníka serveru**/**Průzkumník databáze**a klikněte na tlačítko **přidat připojení**.  
  
3.  Zadejte platné připojení k ukázková databáze Northwind.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Přidat k projektu s LINQ souboru SQL  
  
1.  V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**. Vyberte jazyka Visual Basic **formulářové aplikace Windows** jako typ projektu.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**. Vyberte **třídy LINQ to SQL** šablony položky.  
  
3.  Název souboru `northwind.dbml`. Klikněte na tlačítko **přidat**. Návrhář relací objektů (Návrhář relací objektů), je otevřené `northwind.dbml` souboru.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Chcete-li přidat tabulky pro dotazování a upravit návrháře  
  
1.  V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte možnost připojení k databázi Northwind. Rozbalte **tabulky** složky.  
  
     Pokud jste zavřeli Návrhář relací objektů, můžete ho znovu otevřít dvojitým kliknutím `northwind.dbml` soubor, který jste přidali dříve.  
  
2.  Klikněte na tabulku zákazníků a přetáhněte ji do levého podokna návrháře.  
  
     Návrhář vytvoří nový objekt zákazníka pro váš projekt.  
  
3.  Uložte změny a zavřít návrháře.  
  
4.  Uložte projekt.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Přidání kódu k úpravě databáze a zobrazit výsledky  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.DataGridView> na výchozí formuláře Windows pro svůj projekt Form1 ovládací prvek.  
  
2.  Při přidání tabulky do Návrhář relací objektů návrháře přidat <xref:System.Data.Linq.DataContext> objektu do projektu. Tento objekt obsahuje kód, který můžete použít pro přístup k tabulce zákazníků. Také obsahuje kód, který definuje objekt místní zákazníka a kolekci zákazníci pro tabulku. <xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu souboru DBML. Pro tento projekt <xref:System.Data.Linq.DataContext> názvem objektu `northwindDataContext`.  
  
     Můžete vytvořit instanci <xref:System.Data.Linq.DataContext> objekt v kódu a dotazů a upravit kolekci zákazníkům určit Návrhář relací objektů. Změny provedené ke kolekci zákazníků se neprojeví v databázi, dokud odeslání voláním <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodu <xref:System.Data.Linq.DataContext> objektu.  
  
     Dvakrát klikněte na Windows formuláře, formulář1, přidejte kód, který <xref:System.Windows.Forms.Form.Load> událost, která má dotaz zákazníků tabulku, která je k dispozici jako vlastnost vaší <xref:System.Data.Linq.DataContext>. Přidejte následující kód:  
  
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
  
3.  Z **sada nástrojů**, přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky na formuláři. Vyberte první `Button` ovládacího prvku. V **vlastnosti** nastavte `Name` z `Button` řídit k `AddButton` a `Text` k `Add`. Vyberte tlačítko druhý a nastavte `Name` vlastnost `UpdateButton` a `Text` vlastnost `Update`. Vyberte tlačítko třetí a nastavte `Name` vlastnost `DeleteButton` a `Text` vlastnost `Delete`.  
  
4.  Dvakrát klikněte **přidat** tlačítko Přidat kód pro jeho `Click` událostí. Přidejte následující kód:  
  
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
  
5.  Dvakrát klikněte **aktualizace** tlačítko Přidat kód pro jeho `Click` událostí. Přidejte následující kód:  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  Dvakrát klikněte **odstranit** tlačítko Přidat kód pro jeho `Click` událostí. Přidejte následující kód:  
  
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
  
7.  Stisknutím klávesy F5 spusťte projekt. Klikněte na tlačítko **přidat** přidat nový záznam. Klikněte na tlačítko **aktualizace** nový záznam upravit. Klikněte na tlačítko **odstranit** odstranit novém záznamu.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
