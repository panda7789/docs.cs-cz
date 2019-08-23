---
title: 'Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967379"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Můžete programově odstranit nebo skrýt sloupce v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí vlastností a metod <xref:System.Windows.Forms.GridColumnStylesCollection> objektů a <xref:System.Windows.Forms.DataGridColumnStyle> (které jsou členy <xref:System.Windows.Forms.DataGridTableStyle> třídy).  
  
 Odstraněné nebo skryté sloupce stále existují ve zdroji dat, ke kterému je mřížka vázána, a ke kterým lze nadále přistupovat programově. Již nejsou viditelné v prvku DataGrid.  
  
> [!NOTE]
> Pokud vaše aplikace nepřistupuje k určitým sloupcům dat a nechcete, aby se zobrazila v prvku DataGrid, je pravděpodobné, že je nebudete muset zahrnout do zdroje dat na prvním místě.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Postup při odstranění sloupce z tabulky DataGrid programově  
  
1. V oblasti deklarace ve formuláři deklarujte novou instanci <xref:System.Windows.Forms.DataGridTableStyle> třídy.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> Nastavte vlastnost na tabulku ve zdroji dat, pro kterou chcete styl použít. V následujícím příkladu je použita <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnost, kterou předpokládá, že je již nastavena.  
  
3. Přidejte nový <xref:System.Windows.Forms.DataGridTableStyle> objekt do kolekce stylů tabulky objektu DataGrid.  
  
4. <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> Zavolejte metodu <xref:System.Windows.Forms.DataGrid>kolekce aurčeteindexsloupcesloupce,kterýsemáodstranit.<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Programové skrytí sloupce v ovládacím prvku DataGrid  
  
1. V oblasti deklarace ve formuláři deklarujte novou instanci <xref:System.Windows.Forms.DataGridTableStyle> třídy.  
  
2. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> Nastavte vlastnost <xref:System.Windows.Forms.DataGridTableStyle> na tabulku ve zdroji dat, pro kterou chcete styl použít. Následující příklad kódu používá <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnost, která předpokládá, že je již nastavena.  
  
3. Přidejte nový <xref:System.Windows.Forms.DataGridTableStyle> objekt do kolekce stylů tabulky objektu DataGrid.  
  
4. Skryjte sloupec nastavením jeho `Width` vlastnosti na hodnotu 0 a určete index sloupce sloupce, který se má skrýt.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Změna zobrazených dat v době běhu v ovládacím prvku model Windows Forms DataGrid](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
