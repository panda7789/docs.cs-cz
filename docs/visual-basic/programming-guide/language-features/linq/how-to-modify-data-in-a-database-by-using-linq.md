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
ms.openlocfilehash: ebf0ed1be8d74b60b7e626db996e7cefb1c01131
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524521"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Postupy: Změna dat v databázi pomocí LINQ (Visual Basic)

Dotazy LINQ (Language-Integrated Query) usnadňují přístup k informacím o databázi a upravují hodnoty v databázi.

Následující příklad ukazuje, jak vytvořit novou aplikaci, která načte a aktualizuje informace v databázi SQL Server.

V příkladech v tomto tématu se používá ukázková databáze Northwind. Pokud tuto databázi ve vývojovém počítači nemáte, můžete si ji stáhnout z webu Microsoft Download Center. Pokyny najdete v tématu [stažení ukázkových databází](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

### <a name="to-create-a-connection-to-a-database"></a>Vytvoření připojení k databázi

1. V aplikaci Visual Studio otevřete **Průzkumník serveru** /**Průzkumníku databáze** tak, že kliknete na nabídku **zobrazení** a pak vyberete **Průzkumník serveru** /**Průzkumník databáze**.

2. Klikněte pravým tlačítkem na **datová připojení** v **Průzkumník serveru** /**Průzkumníku databáze**a klikněte na **Přidat připojení**.

3. Zadejte platné připojení k ukázkové databázi Northwind.

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Přidání projektu se souborem LINQ to SQL

1. V aplikaci Visual Studio v nabídce **soubor** přejděte na možnost **Nový** a poté klikněte na položku **projekt**. Jako typ projektu vyberte Visual Basic **model Windows Forms aplikace** .

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**. Vyberte šablonu položky **LINQ to SQL třídy** .

3. Pojmenujte soubor `northwind.dbml`. Klikněte na tlačítko **Přidat**. Pro `northwind.dbml` soubor se otevře Návrhář relací objektů (Návrhář O/R).

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Přidání tabulek pro dotazování a úpravy v Návrháři

1. V **Průzkumník serveru** /**Průzkumníku databáze**rozbalte připojení k databázi Northwind. Rozbalte složku **tabulky** .

     Pokud jste návrháře O/R zavřeli, můžete ho znovu otevřít dvojitým kliknutím na soubor `northwind.dbml`, který jste přidali dříve.

2. Klikněte na tabulku Customers (zákazníci) a přetáhněte ji do levého podokna návrháře.

     Návrhář vytvoří nový objekt zákazníka pro váš projekt.

3. Uložte změny a zavřete návrháře.

4. Uložte projekt.

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Přidání kódu pro úpravu databáze a zobrazení výsledků

1. Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.DataGridView> do výchozího formuláře Windows pro váš projekt, Form1.

2. Když jste přidali tabulky do návrháře pro/R, Návrhář přidal do projektu objekt <xref:System.Data.Linq.DataContext>. Tento objekt obsahuje kód, který můžete použít pro přístup k tabulce Customers. Obsahuje také kód, který definuje místní objekt zákazníka a kolekci Customers pro tabulku. Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu souboru. dbml. Pro tento projekt má objekt <xref:System.Data.Linq.DataContext> název `northwindDataContext`.

     Můžete vytvořit instanci objektu <xref:System.Data.Linq.DataContext> v kódu a dotazovat a upravit kolekci Customers, kterou určuje Návrhář relací O/R. Změny, které provedete v kolekci Customers, se v databázi neprojeví, dokud je neodešlete voláním metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A> objektu <xref:System.Data.Linq.DataContext>.

     Dvojitým kliknutím na formulář Windows, Form1 přidáte kód do události <xref:System.Windows.Forms.Form.Load> pro dotaz na tabulku Customers, která je vystavena jako vlastnost <xref:System.Data.Linq.DataContext>. Přidejte následující kód:

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

3. Z **panelu nástrojů**přetáhněte do formuláře tři ovládací prvky <xref:System.Windows.Forms.Button>. Vyberte první ovládací prvek `Button`. V okně **vlastnosti** nastavte `Name` ovládacího prvku `Button` na `AddButton` a `Text` na `Add`. Vyberte druhé tlačítko a vlastnost `Name` nastavte na `UpdateButton` a vlastnost `Text` na `Update`. Vyberte třetí tlačítko a vlastnost `Name` nastavte na `DeleteButton` a vlastnost `Text` na `Delete`.

4. Dvojím kliknutím na tlačítko **Přidat** přidejte kód do události `Click`. Přidejte následující kód:

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

5. Dvojím kliknutím na tlačítko **aktualizovat** přidejte do události `Click` kód. Přidejte následující kód:

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

6. Dvojím kliknutím na tlačítko **Odstranit** přidejte kód do události `Click`. Přidejte následující kód:

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

7. Stisknutím klávesy F5 spusťte projekt. Kliknutím na tlačítko **Přidat** přidejte nový záznam. Kliknutím na **aktualizovat** upravíte nový záznam. Kliknutím na **Odstranit** odstraňte nový záznam.

## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
