---
title: "Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d89f14d034c1050d364282c04424b1326bcff9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Prostřednictvím kódu programu můžete odstranit nebo skrytí sloupců v modelu Windows Forms <xref:System.Windows.Forms.DataGrid> ovládacího prvku pomocí vlastnosti a metody <xref:System.Windows.Forms.GridColumnStylesCollection> a <xref:System.Windows.Forms.DataGridColumnStyle> objekty (které jsou členy <xref:System.Windows.Forms.DataGridTableStyle> třídy).  
  
 Odstraněné nebo skrytých sloupců stále existují ve zdroji dat je vázán k mřížce a stále je možné programově přistupovat. Právě již nejsou viditelné v objektu datagrid.  
  
> [!NOTE]
>  Pokud vaše aplikace není přístup k určité sloupce dat, a nechcete zobrazovat v objektu datagrid, pak je pravděpodobně není potřeba zahrnout je do zdroje dat na prvním místě.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Chcete odstranit sloupec z objektu DataGrid prostřednictvím kódu programu  
  
1.  V oblasti deklarace formuláře deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.  
  
2.  Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> do tabulky ve zdroji dat, který chcete použít styl pro vlastnost. Následující příklad používá <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnosti, která předpokládá, že je již nastaven.  
  
3.  Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt, který má kolekce stylů tabulek v kolekci datagrid.  
  
4.  Volání <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> metodu <xref:System.Windows.Forms.DataGrid>na <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekce, zadání index sloupce sloupce, který se odstranit.  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Skrytí sloupců v objektu DataGrid prostřednictvím kódu programu  
  
1.  V oblasti deklarace formuláře deklarovat novou instanci třídy <xref:System.Windows.Forms.DataGridTableStyle> třídy.  
  
2.  Nastavte <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> vlastnost <xref:System.Windows.Forms.DataGridTableStyle> do tabulky ve zdroji dat, který chcete použít styl pro. Následující příklad kódu používá <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> vlastnosti, která předpokládá, že je již nastaven.  
  
3.  Přidejte nové <xref:System.Windows.Forms.DataGridTableStyle> objekt, který má kolekce stylů tabulek v kolekci datagrid.  
  
4.  Skrýt sloupce nastavením jeho `Width` vlastnost na hodnotu 0, zadání index sloupce sloupce, který se skrýt.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [Postupy: přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
