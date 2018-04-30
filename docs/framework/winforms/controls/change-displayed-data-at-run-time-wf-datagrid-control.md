---
title: 'Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ea90c3532203a61beded5eceeee5cf535a74b87b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Po vytvoření Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí funkce návrhu, může také chcete dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky v době běhu. To může zahrnovat změny buď jednotlivé hodnoty v tabulce nebo změna zdroje dat je vázána <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Změny na jednotlivé hodnoty jsou prováděny prostřednictvím <xref:System.Data.DataSet> objektu není <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
### <a name="to-change-data-programmatically"></a>Chcete-li změnit data prostřednictvím kódu programu  
  
1.  Zadejte požadovanou tabulku z <xref:System.Data.DataSet> objekt a požadovaný řádek a pole z tabulky a nastavte hodnotu na novou hodnotu buňky.  
  
    > [!NOTE]
    >  Chcete-li určit první tabulky <xref:System.Data.DataSet> nebo první řádek tabulky, použijte hodnotu 0.  
  
     Následující příklad ukazuje, jak změnit druhá položka první řádek v první tabulce datovou sadu kliknutím `Button1`. <xref:System.Data.DataSet> (`ds`) A tabulky (`0` a `1`) byly dříve vytvořeny.  
  
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
  
     V době, můžete použít spuštění <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda pro vazbu <xref:System.Windows.Forms.DataGrid> řízení k jinému zdroji dat. Například může mít několik [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ovládací prvky datových, každý z nich připojený k jiné databázi.  
  
### <a name="to-change-the-datasource-programmatically"></a>Chcete-li změnit zdroj dat prostřednictvím kódu programu  
  
1.  Nastavte <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda k názvu zdroje dat a chcete vytvořit vazbu na tabulku.  
  
     Následující příklad ukazuje, jak změnit datum zdrojový pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] řízení dat (adoPubsAuthors), která je připojena k autoři tabulky v databázi Pubs.  
  
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
 [Datové sady ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
