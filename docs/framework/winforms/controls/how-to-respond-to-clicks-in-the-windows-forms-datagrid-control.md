---
title: Reagovat na kliknutí v ovládacím prvku DataGrid
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
ms.openlocfilehash: e72d117b12d43ece8c4d05ed29ab45693418eede
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141936"
---
# <a name="how-to-respond-to-clicks-in-the-windows-forms-datagrid-control"></a>Postupy: Reakce na kliknutí v ovládacím prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací <xref:System.Windows.Forms.DataGridView> prvek nahradí a přidá <xref:System.Windows.Forms.DataGrid> funkce ovládacího prvku; <xref:System.Windows.Forms.DataGrid> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete. Další informace naleznete v [tématu Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po připojení <xref:System.Windows.Forms.DataGrid> formulářů Windows Forms k databázi můžete sledovat, na kterou buňku uživatel klepnul.  
  
### <a name="to-detect-when-the-user-of-the-datagrid-selects-a-different-cell"></a>Chcete-li zjistit, kdy uživatel DataGrid vybere jinou buňku  
  
- V <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> obslužné rutině události napište kód, který správně odpoví.  
  
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
  
     (Vizuální C#) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.myDataGrid.CurrentCellChanged += new  
       System.EventHandler(this.myDataGrid_CurrentCellChanged);  
    ```  
  
### <a name="to-determine-which-part-of-the-datagrid-the-user-clicked"></a>Chcete-li zjistit, na kterou část datagridu uživatel klepnul  
  
- Volání <xref:System.Windows.Forms.DataGrid.HitTest%2A> metody v příslušné obslužné <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.Click> rutiny události, například pro nebo událost.  
  
     Metoda <xref:System.Windows.Forms.DataGrid.HitTest%2A> vrátí <xref:System.Windows.Forms.DataGrid.HitTestInfo> objekt, který obsahuje řádek a sloupec klepnuté oblasti.  
  
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
  
     (Vizuální C#) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.myDataGrid.MouseDown += new  
       System.Windows.Forms.MouseEventHandler  
       (this.myDataGrid_MouseDown);  
    ```  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid](change-displayed-data-at-run-time-wf-datagrid-control.md)
