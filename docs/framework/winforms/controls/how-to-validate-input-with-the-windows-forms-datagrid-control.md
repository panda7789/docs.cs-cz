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
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="383d2-102">Postupy: Ověřování vstupu s ovládacím prvkem Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="383d2-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="383d2-103"><xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="383d2-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="383d2-104">Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="383d2-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="383d2-105">Nejsou k dispozici pro Windows Forms dva typy ověřování vstupu <xref:System.Windows.Forms.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="383d2-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="383d2-106">Pokud se uživatel pokusí zadejte hodnotu, která je typu nemůže být přijata dat pro buňky, například řetězec na celé číslo se nová neplatná hodnota nahradí původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="383d2-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="383d2-107">Tento druh ověřování vstupu se provádí automaticky a nelze jej upravit.</span><span class="sxs-lookup"><span data-stu-id="383d2-107">This kind of input validation is done automatically and cannot be customized.</span></span>  
  
 <span data-ttu-id="383d2-108">Jiný typ ověření vstupu umožňuje odmítnout nemůže být přijata žádná data, například 0 hodnotu do pole, které musí být větší než nebo rovna 1 nebo nevhodných řetězec.</span><span class="sxs-lookup"><span data-stu-id="383d2-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="383d2-109">K tomu je potřeba v datové sadě obslužné rutiny události pro zápis <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> událostí.</span><span class="sxs-lookup"><span data-stu-id="383d2-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="383d2-110">V příkladu níže používá <xref:System.Data.DataTable.ColumnChanging> událostí protože nepřijatelné hodnota je zakázaná zejména pro sloupec "Produkt".</span><span class="sxs-lookup"><span data-stu-id="383d2-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="383d2-111">Můžete použít <xref:System.Data.DataTable.RowChanging> událostí pro kontrolu, hodnotě sloupec "Koncové datum" je novější než sloupci "Počáteční datum" ve stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="383d2-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>  
  
### <a name="to-validate-user-input"></a><span data-ttu-id="383d2-112">K ověření vstupu uživatele</span><span class="sxs-lookup"><span data-stu-id="383d2-112">To validate user input</span></span>  
  
1.  <span data-ttu-id="383d2-113">Napsat kód pro zpracování <xref:System.Data.DataTable.ColumnChanging> událost pro příslušnou tabulku.</span><span class="sxs-lookup"><span data-stu-id="383d2-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="383d2-114">Když se detekuje nevhodných vstup, volání <xref:System.Data.DataRow.SetColumnError%2A> metodu <xref:System.Data.DataRow> objektu.</span><span class="sxs-lookup"><span data-stu-id="383d2-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>  
  
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
  
2.  <span data-ttu-id="383d2-115">Obslužné rutiny události se připojte k události.</span><span class="sxs-lookup"><span data-stu-id="383d2-115">Connect the event handler to the event.</span></span>  
  
     <span data-ttu-id="383d2-116">Místní následující kód v rámci buď formuláře <xref:System.Windows.Forms.Form.Load> události nebo jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="383d2-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="383d2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="383d2-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [<span data-ttu-id="383d2-118">DataGrid – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="383d2-118">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
