---
title: 'Postupy: Reakce na kliknutí v ovládacím prvku Windows Forms DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Click event [Windows Forms], monitoring in DataGrid controls
- DataGrid control [Windows Forms], examples
- DataGrid control [Windows Forms], returning clicked cell value
- cells [Windows Forms], location in DataGrid
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], click events
ms.assetid: a0aa204b-8351-4d82-9933-ee21a5c9e409
ms.openlocfilehash: 55ca52390cd6c5d5af4a764ea4438d8ce935dfbb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191897"
---
# <a name="how-to-respond-to-clicks-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="95c11-102">Postupy: Reakce na kliknutí v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="95c11-102">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="95c11-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="95c11-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="95c11-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="95c11-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="95c11-105">Po Windows Forms <xref:System.Windows.Forms.DataGrid> je připojený k databázi, můžete sledovat, které uživatel klikl na buňky.</span><span class="sxs-lookup"><span data-stu-id="95c11-105">After the Windows Forms <xref:System.Windows.Forms.DataGrid> is connected to a database, you can monitor which cell the user clicked.</span></span>  
  
### <a name="to-detect-when-the-user-of-the-datagrid-selects-a-different-cell"></a><span data-ttu-id="95c11-106">Chcete-li zjistit, kdy uživatel v prvku DataGrid vybere jinou buňku</span><span class="sxs-lookup"><span data-stu-id="95c11-106">To detect when the user of the DataGrid selects a different cell</span></span>  
  
-   <span data-ttu-id="95c11-107">V <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> obslužná rutina události, napište kód, který odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="95c11-107">In the <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> event handler, write code to respond appropriately.</span></span>  
  
    ```vb  
    Private Sub myDataGrid_CurrentCellChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles myDataGrid.CurrentCellChanged  
       MessageBox.Show("Col is " & myDataGrid.CurrentCell.ColumnNumber _  
          & ", Row is " & myDataGrid.CurrentCell.RowNumber _  
          & ", Value is " & myDataGrid.Item(myDataGrid.CurrentCell))  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_CurrentCellChanged(object sender,   
    System.EventArgs e)  
    {  
       MessageBox.Show ("Col is " + myDataGrid.CurrentCell.ColumnNumber  
          + ", Row is " + myDataGrid.CurrentCell.RowNumber   
          + ", Value is " + myDataGrid[myDataGrid.CurrentCell] );  
    }  
    ```  
  
     <span data-ttu-id="95c11-108">(Visual C#) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="95c11-108">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.CurrentCellChanged += new  
       System.EventHandler(this.myDataGrid_CurrentCellChanged);  
    ```  
  
### <a name="to-determine-which-part-of-the-datagrid-the-user-clicked"></a><span data-ttu-id="95c11-109">Chcete-li zjistit, které části objektu DataGrid uživatel klikl na</span><span class="sxs-lookup"><span data-stu-id="95c11-109">To determine which part of the DataGrid the user clicked</span></span>  
  
-   <span data-ttu-id="95c11-110">Volání <xref:System.Windows.Forms.DataGrid.HitTest%2A> metoda v obslužné rutině události, například jako pro <xref:System.Windows.Forms.Control.MouseDown> nebo <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="95c11-110">Call the <xref:System.Windows.Forms.DataGrid.HitTest%2A> method in an appropriate event handler, such as for the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     <span data-ttu-id="95c11-111"><xref:System.Windows.Forms.DataGrid.HitTest%2A> Metoda vrátí hodnotu <xref:System.Windows.Forms.DataGrid.HitTestInfo> objekt, který obsahuje řádek a sloupec na kliknutí na oblast.</span><span class="sxs-lookup"><span data-stu-id="95c11-111">The <xref:System.Windows.Forms.DataGrid.HitTest%2A> method returns a <xref:System.Windows.Forms.DataGrid.HitTestInfo> object that contains the row and column of a clicked area.</span></span>  
  
    ```vb  
    Private Sub myDataGrid_MouseDown(ByVal sender As Object, _  
    ByVal e As MouseEventArgs) Handles myDataGrid.MouseDown  
       Dim myGrid As DataGrid = CType(sender, DataGrid)  
       Dim hti As System.Windows.Forms.DataGrid.HitTestInfo  
       hti = myGrid.HitTest(e.X, e.Y)  
       Dim message As String = "You clicked "  
  
       Select Case hti.Type  
          Case System.Windows.Forms.DataGrid.HitTestType.None  
             message &= "the background."  
          Case System.Windows.Forms.DataGrid.HitTestType.Cell  
             message &= "cell at row " & hti.Row & ", col " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader  
             message &= "the column header for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowHeader  
             message &= "the row header for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnResize  
             message &= "the column resizer for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowResize  
             message &= "the row resizer for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.Caption  
             message &= "the caption"  
          Case System.Windows.Forms.DataGrid.HitTestType.ParentRows  
             message &= "the parent row"  
       End Select  
  
       Console.WriteLine(message)  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       DataGrid myGrid = (DataGrid) sender;  
       System.Windows.Forms.DataGrid.HitTestInfo hti;  
       hti = myGrid.HitTest(e.X, e.Y);  
       string message = "You clicked ";  
  
       switch (hti.Type)   
       {  
          case System.Windows.Forms.DataGrid.HitTestType.None :  
             message += "the background.";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Cell :  
             message += "cell at row " + hti.Row + ", col " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader :  
             message += "the column header for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowHeader :  
             message += "the row header for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnResize :  
             message += "the column resizer for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowResize :  
             message += "the row resizer for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Caption :  
             message += "the caption";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ParentRows :  
             message += "the parent row";  
             break;  
          }  
  
          Console.WriteLine(message);  
    }  
    ```  
  
     <span data-ttu-id="95c11-112">(Visual C#) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="95c11-112">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.MouseDown += new  
       System.Windows.Forms.MouseEventHandler  
       (this.myDataGrid_MouseDown);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="95c11-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95c11-113">See also</span></span>

- [<span data-ttu-id="95c11-114">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="95c11-114">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="95c11-115">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="95c11-115">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
