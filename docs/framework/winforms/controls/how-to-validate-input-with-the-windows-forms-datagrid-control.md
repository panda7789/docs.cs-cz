---
title: Ověření vstupu pomocí ovládacího prvku DataGrid
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
ms.openlocfilehash: 3958089007401d2e977c9c96f07c9196e6216596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728294"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Postupy: Ověřování vstupu s ovládacím prvkem Windows Forms DataGrid

> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Pro ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGrid> jsou k dispozici dva typy ověřování vstupu. Pokud se uživatel pokusí zadat hodnotu, která má nepřijatelný datový typ pro buňku, například řetězec na celé číslo, nová neplatná hodnota je nahrazena starou hodnotou. Tento druh ověření vstupu se provádí automaticky a nedá se přizpůsobit.

Druhý typ ověření vstupu lze použít k zamítnutí všech nepřijatelných dat, například hodnotu 0 v poli, které musí být větší nebo rovno 1 nebo nevhodný řetězec. To se provádí v datové sadě napsáním obslužné rutiny události pro událost <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging>. Následující příklad používá událost <xref:System.Data.DataTable.ColumnChanging>, protože nepřijatelná hodnota je pro sloupec "Product" nepovolená. Můžete použít událost <xref:System.Data.DataTable.RowChanging> pro kontrolu, zda je hodnota sloupce "koncové datum" pozdější než sloupec "datum zahájení" na stejném řádku.

## <a name="to-validate-user-input"></a>Ověření vstupu uživatele

1. Napište kód pro zpracování události <xref:System.Data.DataTable.ColumnChanging> pro příslušnou tabulku. Při zjištění nevhodného vstupu zavolejte metodu <xref:System.Data.DataRow.SetColumnError%2A> objektu <xref:System.Data.DataRow>.

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

2. Připojte k události obslužnou rutinu události.

    Vložte následující kód do události <xref:System.Windows.Forms.Form.Load> formuláře nebo jeho konstruktoru.

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
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
