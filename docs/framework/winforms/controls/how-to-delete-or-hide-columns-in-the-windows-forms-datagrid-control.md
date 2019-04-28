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
ms.openlocfilehash: d3f1f013cbb5e41c997014f556602b01bab62914
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757388"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Programově můžete odstranit nebo skrytí sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku pomocí vlastnosti a metody <xref:System.Windows.Forms.GridColumnStylesCollection> a <xref:System.Windows.Forms.DataGridColumnStyle> objekty (které jsou členy objektu <xref:System.Windows.Forms.DataGridTableStyle> třídy).  
  
 Odstraněné nebo skryté sloupce stále existují ve zdroji dat je vázán na mřížky a i nadále přístupný prostřednictvím kódu programu. Stačí už nejsou viditelné v mřížce datagrid.  
  
> [!NOTE]
>  Pokud vaše aplikace není přístup k určité sloupce dat, a nechcete zobrazovat v mřížce datagrid, pak je pravděpodobně není nutné zahrnout je do zdroje dat na prvním místě.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Chcete-li odstranit sloupce z mřížky DataGrid prostřednictvím kódu programu  
  
1. V oblasti formuláře deklarace deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.  
  
2. Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> vlastnost do tabulky ve zdroji dat, který chcete použít styl. V následujícím příkladu <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnost, která předpokládá, že je již nastaven.  
  
3. Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt kolekce stylů tabulek mřížce datagrid.  
  
4. Volání <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.DataGrid>společnosti <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekci index sloupce sloupce, který se odstranit zadání.  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Chcete-li skrýt sloupec v mřížce DataGrid prostřednictvím kódu programu  
  
1. V oblasti formuláře deklarace deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.  
  
2. Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle> do tabulky ve zdroji dat, který chcete použít styl. Následující příklad kódu používá <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnost, která předpokládá, že je již nastaven.  
  
3. Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt kolekce stylů tabulek mřížce datagrid.  
  
4. Skrýt sloupec tak, že nastavíte její `Width` vlastnost na hodnotu 0, určení sloupcový index sloupce, který se skrýt.  
  
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
- [Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
