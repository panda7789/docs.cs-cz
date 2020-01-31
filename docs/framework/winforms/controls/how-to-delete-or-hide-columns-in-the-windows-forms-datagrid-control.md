---
title: Odstranění nebo skrytí sloupců v ovládacím prvku DataGrid
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
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743293"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Můžete programově odstranit nebo skrýt sloupce v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí vlastností a metod objektů <xref:System.Windows.Forms.GridColumnStylesCollection> a <xref:System.Windows.Forms.DataGridColumnStyle> (které jsou členy třídy <xref:System.Windows.Forms.DataGridTableStyle>).  
  
 Odstraněné nebo skryté sloupce stále existují ve zdroji dat, ke kterému je mřížka vázána, a ke kterým lze nadále přistupovat programově. Již nejsou viditelné v prvku DataGrid.  
  
> [!NOTE]
> Pokud vaše aplikace nepřistupuje k určitým sloupcům dat a nechcete, aby se zobrazila v prvku DataGrid, je pravděpodobné, že je nebudete muset zahrnout do zdroje dat na prvním místě.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Postup při odstranění sloupce z tabulky DataGrid programově  
  
1. V oblasti deklarace ve formuláři deklarujte novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> nastavte na tabulku ve zdroji dat, pro kterou chcete styl použít. V následujícím příkladu je použita vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, která předpokládá, že je již nastavena.  
  
3. Přidejte nový objekt <xref:System.Windows.Forms.DataGridTableStyle> do kolekce stylů tabulky DataGrid.  
  
4. Zavolejte metodu <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> kolekce <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> <xref:System.Windows.Forms.DataGrid>a určete index sloupce sloupce, který se má odstranit.  
  
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
  
1. V oblasti deklarace ve formuláři deklarujte novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Windows.Forms.DataGridTableStyle> na tabulku ve zdroji dat, pro kterou chcete styl použít. Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, která předpokládá, že je již nastavena.  
  
3. Přidejte nový objekt <xref:System.Windows.Forms.DataGridTableStyle> do kolekce stylů tabulky DataGrid.  
  
4. Skryjte sloupec nastavením jeho vlastnosti `Width` na hodnotu 0 a určete index sloupce sloupce, který se má skrýt.  
  
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

- [Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
