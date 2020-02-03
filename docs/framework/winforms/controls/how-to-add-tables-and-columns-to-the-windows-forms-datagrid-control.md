---
title: Přidání tabulek a sloupců do ovládacího prvku DataGrid
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
ms.openlocfilehash: 2db2e38c326cbcd78c58ee4fe00cd9ed20ae0e8a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747207"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid

> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Data můžete zobrazit v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> v tabulkách a sloupcích vytvořením objektů **Styl DataGridTableStyle** a jejich přidáním do objektu **GridTableStylesCollection** , který je k dispozici prostřednictvím vlastnosti **TableStyles** ovládacího prvku <xref:System.Windows.Forms.DataGrid>. Každý styl tabulky zobrazuje obsah libovolné tabulky dat, která je zadána ve vlastnosti **Mapping** **Styl DataGridTableStyle** objektu. Ve výchozím nastavení zobrazí styl tabulky bez zadaných stylů sloupců všechny sloupce v této tabulce dat. Můžete omezit, které sloupce z tabulky se zobrazí přidáním objektů **styl DataGridColumnStyle** do objektu **kolekce GridColumnStylesCollection** , který je k dispozici prostřednictvím vlastnosti **GridColumnStyles** každého objektu **Styl DataGridTableStyle** .

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Přidání tabulky a sloupce do DataGrid programově

1. Aby bylo možné zobrazit data v tabulce, musíte nejprve vytvořit vazby ovládacího prvku <xref:System.Windows.Forms.DataGrid> k datové sadě. Další informace naleznete v tématu [How to: bind the model Windows Forms DataGrid Control to a Source (zdroj dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)).

    > [!CAUTION]
    > Při programovém zadání stylů sloupců vždy vytvořte objekty **styl DataGridColumnStyle** a přidejte je do objektu **kolekce GridColumnStylesCollection** před přidáním objektů **Styl DataGridTableStyle** do objektu **GridTableStylesCollection** . Když do kolekce přidáte prázdný objekt **Styl DataGridTableStyle** , automaticky se vygenerují objekty **styl DataGridColumnStyle** . V důsledku toho bude vyvolána výjimka, pokud se pokusíte přidat nové objekty **styl DataGridColumnStyle** s duplicitními hodnotami **mapování** na objekt **kolekce GridColumnStylesCollection** .

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

## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
