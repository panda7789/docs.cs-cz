---
title: Změna zobrazených dat za běhu v ovládacím prvku DataGrid
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
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142378"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid
> [!NOTE]
> Ovládací <xref:System.Windows.Forms.DataGridView> prvek nahradí a přidá <xref:System.Windows.Forms.DataGrid> funkce ovládacího prvku; <xref:System.Windows.Forms.DataGrid> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete. Další informace naleznete v [tématu Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po vytvoření formuláře <xref:System.Windows.Forms.DataGrid> systému Windows pomocí funkcí návrhu můžete také chtít dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky za běhu. To může zahrnovat změny jednotlivých hodnot tabulky nebo změnu <xref:System.Windows.Forms.DataGrid> zdroje dat, který je vázán na ovládací prvek. Změny jednotlivých hodnot se <xref:System.Data.DataSet> provádějí prostřednictvím objektu, nikoli ovládacího <xref:System.Windows.Forms.DataGrid> prvku.  
  
### <a name="to-change-data-programmatically"></a>Chcete-li změnit data programově  
  
1. Zadejte požadovanou <xref:System.Data.DataSet> tabulku z objektu a požadovaný řádek a pole z tabulky a nastavte buňku rovnou na novou hodnotu.  
  
    > [!NOTE]
    > Chcete-li určit první <xref:System.Data.DataSet> tabulku nebo první řádek tabulky, použijte 0.  
  
     Následující příklad ukazuje, jak změnit druhý řádek prvního řádku první tabulky `Button1`datové sady klepnutím na tlačítko . ( <xref:System.Data.DataSet> `ds`) a`0` tabulky `1`( a ) byly dříve vytvořeny.  
  
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
  
     (Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Za běhu můžete použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu <xref:System.Windows.Forms.DataGrid> svázat ovládací prvek s jiným zdrojem dat. Můžete mít například několik ovládacích prvků ADO.NET dat, z nichž každý je připojen k jiné databázi.  
  
### <a name="to-change-the-datasource-programmatically"></a>Programová změna zdroje dat  
  
1. Nastavte <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu na název zdroje dat a tabulky, se kterou chcete vytvořit vazbu.  
  
     Následující příklad ukazuje, jak změnit zdroj <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> data pomocí metody na ovládací prvek ADO.NET data (adoPubsAuthors), který je připojen k tabulce Autoři v databázi Pubs.  
  
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
  
## <a name="see-also"></a>Viz také

- [Datové sady ADO.NET](../../data/adonet/ado-net-datasets.md)
- [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
