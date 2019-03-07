---
title: 'Postupy: Ověřování vstupu s ovládacím prvku Windows Forms DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: 84057a2d9709963c7a7302110ab11931b86fcad9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497623"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Postupy: Ověřování vstupu s ovládacím prvku Windows Forms DataGrid

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Existují dva typy ověřování vstupu dostupná pro formuláře Windows <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Pokud se uživatel pokusí o hodnotu, která je nepřijatelné datového typu pro buňky, například řetězec na celé číslo, zadejte nové neplatná hodnota nahradí se původní hodnota. Tento druh ověření vstupu je prováděno automaticky a nelze je upravovat.

Jiný typ ověřování vstupu umožňuje odmítnout nemůže být přijata žádná data, například 0 hodnotu v poli, které musí být větší než nebo rovna 1 nebo nevhodných řetězec. To se provádí v datové sadě napsáním obslužná rutina události <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> událostí. V příkladu níže použití <xref:System.Data.DataTable.ColumnChanging> události protože nepřijatelné hodnota není povolena pro sloupec "Produkt" zejména. Můžete použít <xref:System.Data.DataTable.RowChanging> události zjistíte, že hodnota sloupce "Koncové datum" je novější než sloupec "Datum zahájení" ve stejném řádku.

## <a name="to-validate-user-input"></a>Pro ověření uživatelského vstupu

1. Napište kód pro zpracování <xref:System.Data.DataTable.ColumnChanging> událost pro odpovídající tabulky. Při zjištění nevhodný vstup volání <xref:System.Data.DataRow.SetColumnError%2A> metodu <xref:System.Data.DataRow> objektu.

    ```vb
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _
    ByVal e As System.Data.DataColumnChangeEventArgs)
       ' Only check for errors in the Product column
       If (e.Column.ColumnName.Equals("Product")) Then
          ' Do not allow "Automobile" as a product.
          If CType(e.ProposedValue, String) = "Automobile" Then
             Dim badValue As Object = e.ProposedValue
             e.ProposedValue = "Bad Data"
             e.Row.RowError = "The Product column contains an error"
             e.Row.SetColumnError(e.Column, "Product cannot be " & _
             CType(badValue, String))
          End If
       End If
    End Sub
    ```

    ```csharp
    //Handle column changing events on the Customers table
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {

       //Only check for errors in the Product column
       if (e.Column.ColumnName.Equals("Product")) {

          //Do not allow "Automobile" as a product
          if (e.ProposedValue.Equals("Automobile")) {
             object badValue = e.ProposedValue;
             e.ProposedValue = "Bad Data";
             e.Row.RowError = "The Product column contains an error";
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);
          }
       }
    }
    ```

2. Obslužná rutina události připojení k této události.

    Místo tohoto kódu v rámci buď formuláře <xref:System.Windows.Forms.Form.Load> události nebo konstruktoru.

    ```vb
    ' Assumes the grid is bound to a dataset called customersDataSet1
    ' with a table called Customers.
    ' Put this code in the form's Load event or its constructor.
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging
    ```

    ```csharp
    // Assumes the grid is bound to a dataset called customersDataSet1
    // with a table called Customers.
    // Put this code in the form's Load event or its constructor.
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);
    ```

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
