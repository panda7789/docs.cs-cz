---
title: 'Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: 60ba1e9304320346d505f3f73e1ba93ff6edab63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315852"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po vytvoření prvku Windows Forms <xref:System.Windows.Forms.DataGrid> díky funkcím, návrhu, můžete také chtít dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky v době běhu. To může zahrnovat změny buď jednotlivé hodnoty v tabulce nebo změna zdroj dat, který je vázán <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Změny v jednotlivých hodnot se provádí prostřednictvím <xref:System.Data.DataSet> objektu, nikoli <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
### <a name="to-change-data-programmatically"></a>Změna dat prostřednictvím kódu programu  
  
1. Zadejte požadovanou tabulku z <xref:System.Data.DataSet> objektu a požadovaný řádek pole z tabulky a buňky nastavena na novou hodnotu.  
  
    > [!NOTE]
    >  Chcete-li určit první tabulky <xref:System.Data.DataSet> nebo první řádek tabulky, použijte 0.  
  
     Následující příklad ukazuje, jak změnit druhou položku první řádek první tabulky datovou sadu kliknutím `Button1`. <xref:System.Data.DataSet> (`ds`) A tabulky (`0` a `1`) byly dříve vytvořeny.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Během spuštění můžete použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu pro vytvoření vazby <xref:System.Windows.Forms.DataGrid> ovládacího prvku k jinému zdroji dat. Například může mít několik [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ovládací prvky dat, každý z nich připojený k jiné databázi.  
  
### <a name="to-change-the-datasource-programmatically"></a>Chcete-li změnit zdroj dat prostřednictvím kódu programu  
  
1. Nastavte <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody k názvu zdroje dat a tabulku, kterou chcete svázat.  
  
     Následující příklad ukazuje, jak změnit datum zdroje pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ovládací prvek dat (adoPubsAuthors), který je připojený k tabulce Autoři databáze Pubs.  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Datové sady ADO.NET](../../data/adonet/ado-net-datasets.md)
- [Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
