---
title: 'Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: fc8161ea29da92f5dcc2e76f956f3fecd6140acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Data můžete zobrazit v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku tabulky a sloupce vytvořením **styl DataGridTableStyle** objekty a jejich přidání **GridTableStylesCollection** objekt, který je přistupovat prostřednictvím <xref:System.Windows.Forms.DataGrid> ovládacího prvku **TableStyles** vlastnost. Každý styl tabulky zobrazí obsah ať tabulky dat je zadán v **styl DataGridTableStyle** objektu **MappingName** vlastnost. Ve výchozím nastavení zobrazí styl tabulky se žádné sloupce styly definované všechny sloupce v této tabulce data. Můžete omezit, které sloupce z tabulky se objeví přidáním **Styl DataGridColumnStyle** objekty ke **kolekce GridColumnStylesCollection** objekt, který je přístupný prostřednictvím  **GridColumnStyles** vlastnost jednotlivých **styl DataGridTableStyle** objektu.  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Přidání tabulek a sloupců do ovládacího prvku DataGrid prostřednictvím kódu programu  
  
1.  Chcete-li zobrazit data v tabulce, je třeba nejprve svázat <xref:System.Windows.Forms.DataGrid> ovládacího prvku do datové sady. Další informace najdete v tématu [postupy: vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
    > [!CAUTION]
    >  Při zadávání prostřednictvím kódu programu styly sloupců, vždycky vytvořte **Styl DataGridColumnStyle** objekty a přidat je do **kolekce GridColumnStylesCollection** objekt před přidáním  **Styl DataGridTableStyle** objekty ke **GridTableStylesCollection** objektu. Když přidáte prázdnou **styl DataGridTableStyle** objektu do kolekce, **Styl DataGridColumnStyle** objekty vygenerují automaticky. V důsledku toho se výjimka vyvolána, pokud se pokusíte přidat nové **Styl DataGridColumnStyle** objekty s duplicitní **MappingName** hodnoty k **kolekce GridColumnStylesCollection**objektu.  
  
2.  Deklarování nový styl tabulky a nastavit jeho název mapování.  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  Deklarace styl nové sloupce a nastavit jeho název mapování a další vlastnosti.  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  Volání **přidat** metodu **kolekce GridColumnStylesCollection** objekt, který chcete přidat sloupce do tabulky styl  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  Volání **přidat** metodu **GridTableStylesCollection** objekt, který chcete přidat styl tabulky k mřížce data.  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
