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
ms.openlocfilehash: 55e30744f57364fb37c9fde5b6bade6bab60fa26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925092"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Můžete zobrazit data v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> v tabulkách a sloupcích vytvořením objektů **Styl DataGridTableStyle** a jejich přidáním do objektu **GridTableStylesCollection** <xref:System.Windows.Forms.DataGrid> , který je k dispozici prostřednictvím ovládacího prvku Vlastnost **TableStyles** Každý styl tabulky zobrazuje obsah libovolné tabulky dat, která je zadána ve vlastnosti **Mapping** **Styl DataGridTableStyle** objektu. Ve výchozím nastavení zobrazí styl tabulky bez zadaných stylů sloupců všechny sloupce v této tabulce dat. Můžete omezit, které sloupce z tabulky se zobrazí přidáním objektů **styl DataGridColumnStyle** do objektu **kolekce GridColumnStylesCollection** , který je k dispozici prostřednictvím vlastnosti **GridColumnStyles** každého **Styl DataGridTableStyle** předmětů.  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Přidání tabulky a sloupce do DataGrid programově  
  
1. Aby bylo možné zobrazit data v tabulce, je nutné nejprve navazovat <xref:System.Windows.Forms.DataGrid> ovládací prvek na datovou sadu. Další informace najdete v tématu [jak: Navažte model Windows Forms ovládací prvek DataGrid na zdroj](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)dat.  
  
    > [!CAUTION]
    >  Při programovém zadání stylů sloupců vždy vytvořit objekty **styl DataGridColumnStyle** a přidat je do objektu **kolekce GridColumnStylesCollection** před přidáním objektů **Styl DataGridTableStyle** do  **Objekt GridTableStylesCollection** Když do kolekce přidáte prázdný objekt **Styl DataGridTableStyle** , automaticky se vygenerují objekty **styl DataGridColumnStyle** . V důsledku toho bude vyvolána výjimka, pokud se pokusíte přidat nové objekty **styl DataGridColumnStyle** s duplicitními hodnotami **mapování** na objekt **kolekce GridColumnStylesCollection** .  
  
2. Deklarujete nový styl tabulky a nastavte jeho název mapování.  
  
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
  
3. Deklarujete nový styl sloupce a nastavte jeho název mapování a další vlastnosti.  
  
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
  
4. Voláním metody **Add** objektu **kolekce GridColumnStylesCollection** přidejte sloupec do stylu tabulky.  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5. Voláním metody **Add** objektu **GridTableStylesCollection** přidejte do datové mřížky styl tabulky.  
  
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

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
