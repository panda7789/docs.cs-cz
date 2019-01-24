---
title: 'Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid'
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
ms.openlocfilehash: be0bb6d3d7b8d8b362653257139e83900dbb2780
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717867"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Data můžete zobrazit v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku tabulky a sloupce tak, že vytvoříte **styl DataGridTableStyle** objekty a jejich přidání na **GridTableStylesCollection** objekt, který je získává přístup prostřednictvím <xref:System.Windows.Forms.DataGrid> ovládacího prvku **TableStyles** vlastnost. Každý styl tabulky zobrazí obsah libovolné tabulka dat je zadán v **styl DataGridTableStyle** objektu **MappingName** vlastnost. Ve výchozím nastavení styl tabulky se styly žádné sloupce se zobrazí všechny sloupce v tabulce data. Můžete omezit, které sloupce z tabulky zobrazí tak, že přidáte **Styl DataGridColumnStyle** objektů **kolekce GridColumnStylesCollection** objekt, který je přístupný prostřednictvím  **GridColumnStyles** vlastnosti každého **styl DataGridTableStyle** objektu.  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Přidání tabulek a sloupců do ovládacího prvku DataGrid prostřednictvím kódu programu  
  
1.  Pokud chcete zobrazit data v tabulce, je třeba nejdřív svázat <xref:System.Windows.Forms.DataGrid> ovládacího prvku do datové sady. Další informace najdete v tématu [jak: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
    > [!CAUTION]
    >  Při zadávání programově styly sloupců, vždy vytvořit **Styl DataGridColumnStyle** objekty a přidat je do **kolekce GridColumnStylesCollection** objektu před přidáním  **Styl DataGridTableStyle** objektů **GridTableStylesCollection** objektu. Když přidáte prázdná **styl DataGridTableStyle** do kolekce, **Styl DataGridColumnStyle** objekty vygenerují automaticky. V důsledku toho vyvolána výjimka při pokusu přidat nový **Styl DataGridColumnStyle** objektů s duplicitními **MappingName** hodnoty **kolekce GridColumnStylesCollection**objektu.  
  
2.  Deklarovat nový styl tabulky a nastavte její název mapování.  
  
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
  
3.  Deklarovat nový styl sloupce a nastavte její název mapování a dalších vlastností.  
  
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
  
4.  Volání **přidat** metodu **kolekce GridColumnStylesCollection** objektu přidat sloupec styl tabulky  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  Volání **přidat** metodu **GridTableStylesCollection** objekt k sečtení styl tabulky datové mřížce.  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
