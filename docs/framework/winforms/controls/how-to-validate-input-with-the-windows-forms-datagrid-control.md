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
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="8f4e4-102">Postupy: Ověřování vstupu s ovládacím prvkem Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="8f4e4-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="8f4e4-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="8f4e4-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8f4e4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="8f4e4-105">Pro ovládací prvek model Windows Forms <xref:System.Windows.Forms.DataGrid> jsou k dispozici dva typy ověřování vstupu.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="8f4e4-106">Pokud se uživatel pokusí zadat hodnotu, která má nepřijatelný datový typ pro buňku, například řetězec na celé číslo, nová neplatná hodnota je nahrazena starou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="8f4e4-107">Tento druh ověření vstupu se provádí automaticky a nedá se přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-107">This kind of input validation is done automatically and cannot be customized.</span></span>

<span data-ttu-id="8f4e4-108">Druhý typ ověření vstupu lze použít k zamítnutí všech nepřijatelných dat, například hodnotu 0 v poli, které musí být větší nebo rovno 1 nebo nevhodný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="8f4e4-109">To se provádí v datové sadě napsáním obslužné rutiny události pro událost <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging>.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="8f4e4-110">Následující příklad používá událost <xref:System.Data.DataTable.ColumnChanging>, protože nepřijatelná hodnota je pro sloupec "Product" nepovolená.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="8f4e4-111">Můžete použít událost <xref:System.Data.DataTable.RowChanging> pro kontrolu, zda je hodnota sloupce "koncové datum" pozdější než sloupec "datum zahájení" na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>

## <a name="to-validate-user-input"></a><span data-ttu-id="8f4e4-112">Ověření vstupu uživatele</span><span class="sxs-lookup"><span data-stu-id="8f4e4-112">To validate user input</span></span>

1. <span data-ttu-id="8f4e4-113">Napište kód pro zpracování události <xref:System.Data.DataTable.ColumnChanging> pro příslušnou tabulku.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="8f4e4-114">Při zjištění nevhodného vstupu zavolejte metodu <xref:System.Data.DataRow.SetColumnError%2A> objektu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>

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

2. <span data-ttu-id="8f4e4-115">Připojte k události obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-115">Connect the event handler to the event.</span></span>

    <span data-ttu-id="8f4e4-116">Vložte následující kód do události <xref:System.Windows.Forms.Form.Load> formuláře nebo jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8f4e4-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8f4e4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f4e4-117">See also</span></span>

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [<span data-ttu-id="8f4e4-118">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="8f4e4-118">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
