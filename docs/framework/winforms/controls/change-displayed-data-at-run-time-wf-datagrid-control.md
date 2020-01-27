---
title: Změna zobrazených dat v době běhu v ovládacím prvku DataGrid
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
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740590"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po vytvoření model Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí funkcí v době návrhu můžete také v době běhu chtít dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky. To může zahrnovat změny buď v jednotlivých hodnotách tabulky, nebo měnit, který zdroj dat je svázán s ovládacím prvkem <xref:System.Windows.Forms.DataGrid>. Změny jednotlivých hodnot se provádí prostřednictvím objektu <xref:System.Data.DataSet>, nikoli pomocí ovládacího prvku <xref:System.Windows.Forms.DataGrid>.  
  
### <a name="to-change-data-programmatically"></a>Programové změny dat  
  
1. Určete požadovanou tabulku z objektu <xref:System.Data.DataSet> a požadovaný řádek a pole z tabulky a nastavte buňku rovnou na novou hodnotu.  
  
    > [!NOTE]
    > Chcete-li zadat první tabulku <xref:System.Data.DataSet> nebo první řádek tabulky, použijte hodnotu 0.  
  
     Následující příklad ukazuje, jak změnit druhý záznam prvního řádku v první tabulce datové sady kliknutím na `Button1`. Již byly vytvořeny <xref:System.Data.DataSet> (`ds`) a tabulky (`0` a `1`).  
  
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
  
     V době spuštění můžete použít metodu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> k navázání ovládacího prvku <xref:System.Windows.Forms.DataGrid> na jiný zdroj dat. Můžete mít například několik ovládacích prvků ADO.NET data, které jsou připojené k jiné databázi.  
  
### <a name="to-change-the-datasource-programmatically"></a>Chcete-li změnit zdroj dat programově  
  
1. Nastavte metodu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> na název zdroje dat a tabulky, ke které chcete vytvořit propojení.  
  
     Následující příklad ukazuje, jak změnit zdroj dat pomocí metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> k ovládacímu prvku ADO.NET data (adoPubsAuthors), který je připojen k tabulce Autoři v databázi pubs.  
  
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
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
