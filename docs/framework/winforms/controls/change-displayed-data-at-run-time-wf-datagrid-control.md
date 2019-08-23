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
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917729"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po vytvoření model Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí funkcí v době návrhu lze také dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky v době běhu. To může zahrnovat změny buď na jednotlivé hodnoty tabulky, nebo změnit, který zdroj dat je svázán s <xref:System.Windows.Forms.DataGrid> ovládacím prvkem. Změny jednotlivých hodnot jsou prováděny prostřednictvím <xref:System.Data.DataSet> objektu, <xref:System.Windows.Forms.DataGrid> nikoli ovládacího prvku.  
  
### <a name="to-change-data-programmatically"></a>Programové změny dat  
  
1. Určete požadovanou tabulku z <xref:System.Data.DataSet> objektu a požadovaný řádek a pole z tabulky a nastavte buňku rovnou na novou hodnotu.  
  
    > [!NOTE]
    > Chcete-li zadat první tabulku <xref:System.Data.DataSet> nebo první řádek tabulky, použijte hodnotu 0.  
  
     Následující příklad ukazuje, jak změnit druhý záznam prvního řádku v první tabulce datové sady kliknutím na `Button1`. Dříve <xref:System.Data.DataSet> se`ds`vytvořily ()`0` a `1`tabulky (a).  
  
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
  
     (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     V době spuštění můžete použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu k <xref:System.Windows.Forms.DataGrid> navázání ovládacího prvku na jiný zdroj dat. Můžete mít například několik ovládacích prvků ADO.NET data, které jsou připojené k jiné databázi.  
  
### <a name="to-change-the-datasource-programmatically"></a>Chcete-li změnit zdroj dat programově  
  
1. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Nastavte metodu na název zdroje dat a tabulky, ke které chcete vytvořit propojení.  
  
     Následující příklad ukazuje, jak změnit zdroj dat pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody na ovládací prvek ADO.NET data (adoPubsAuthors), který je připojen k tabulce Autoři v databázi pubs.  
  
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
- [Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Postupy: Navázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
