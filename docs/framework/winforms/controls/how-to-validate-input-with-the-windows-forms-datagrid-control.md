---
title: "Postupy: Ověřování vstupu s ovládacím prvkem Windows Forms DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5e0c366f71f602be2bb1508a6abb00d3d0c83ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Postupy: Ověřování vstupu s ovládacím prvkem Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Nejsou k dispozici pro Windows Forms dva typy ověřování vstupu <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Pokud se uživatel pokusí zadejte hodnotu, která je typu nemůže být přijata dat pro buňky, například řetězec na celé číslo se nová neplatná hodnota nahradí původní hodnoty. Tento druh ověřování vstupu se provádí automaticky a nelze jej upravit.  
  
 Jiný typ ověření vstupu umožňuje odmítnout nemůže být přijata žádná data, například 0 hodnotu do pole, které musí být větší než nebo rovna 1 nebo nevhodných řetězec. K tomu je potřeba v datové sadě obslužné rutiny události pro zápis <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> událostí. V příkladu níže používá <xref:System.Data.DataTable.ColumnChanging> událostí protože nepřijatelné hodnota je zakázaná zejména pro sloupec "Produkt". Můžete použít <xref:System.Data.DataTable.RowChanging> událostí pro kontrolu, hodnotě sloupec "Koncové datum" je novější než sloupci "Počáteční datum" ve stejném řádku.  
  
### <a name="to-validate-user-input"></a>K ověření vstupu uživatele  
  
1.  Napsat kód pro zpracování <xref:System.Data.DataTable.ColumnChanging> událost pro příslušnou tabulku. Když se detekuje nevhodných vstup, volání <xref:System.Data.DataRow.SetColumnError%2A> metodu <xref:System.Data.DataRow> objektu.  
  
    ```vb  
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _  
    ByVal e As System.Data.DataColumnChangeEventArgs)  
       ' Only check for errors in the Product column  
       If (e.Column.ColumnName.Equals("Product")) Then  
          ' Do not allow "Automobile" as a product.  
          If CType(e.ProposedValue, String) = "Automobile" Then  
             Dim badValue As Object = e.ProposedValue  
             e.ProposedValue = "Bad Data"  
             e.Row.RowError = "The Product column contians an error"  
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
  
2.  Obslužné rutiny události se připojte k události.  
  
     Místní následující kód v rámci buď formuláře <xref:System.Windows.Forms.Form.Load> události nebo jeho konstruktoru.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [DataGrid – ovládací prvek](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
