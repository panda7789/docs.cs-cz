---
title: Vazby ovládacího prvku DataGrid se zdrojem dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182247"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat
> [!NOTE]
> Ovládací <xref:System.Windows.Forms.DataGridView> prvek nahradí a přidá <xref:System.Windows.Forms.DataGrid> funkce ovládacího prvku; <xref:System.Windows.Forms.DataGrid> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete. Další informace naleznete v [tématu Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGrid> Windows Forms je speciálně navržen tak, aby zobrazoval informace ze zdroje dat. Svázat ovládací prvek za běhu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> voláním metody. I když můžete zobrazit data z různých zdrojů dat, nejtypičtějšízdroje jsou datové sady a zobrazení dat.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Chcete-li data-bind ovládací prvek DataGrid programově  
  
1. Napište kód pro vyplnění datové sady.  
  
     Pokud je zdrojem dat dat sada dat nebo zobrazení dat založené na tabulce datových sad, přidejte do formuláře kód pro vyplnění datové sady.  
  
     Přesný kód, který používáte, závisí na tom, kde datová sada získává data. Pokud je datová sada naplněna přímo z databáze, `Fill` obvykle voláte metodu datového adaptéru, jako v `DsCategories1`následujícím příkladu, který naplňuje datovou sadu s názvem :  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Pokud je datová sada vyplňována z webové služby XML, obvykle vytvoříte instanci služby v kódu a pak zavoláte jednu z jejích metod a vrátíte datovou sadu. Potom sloučit datovou sadu z webové služby XML do místní datové sady. Následující příklad ukazuje, jak můžete vytvořit instanci `CategoriesService`webové `GetCategories` služby XML s názvem , volat její `DsCategories1`metodu a sloučit výslednou datovou sadu do místní datové sady s názvem :  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. Volání <xref:System.Windows.Forms.DataGrid> metody ovládacího <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> prvku, předání zdroje dat a datového člena. Pokud nepotřebujete explicitně předat datový člen, předejte prázdný řetězec.  
  
    > [!NOTE]
    > Pokud jste vazba mřížky poprvé, můžete nastavit <xref:System.Windows.Forms.DataGrid.DataSource%2A> ovládací <xref:System.Windows.Forms.DataGrid.DataMember%2A> prvek a vlastnosti. Tyto vlastnosti však nelze obnovit, jakmile byly nastaveny. Proto se doporučuje vždy použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu.  
  
     Následující příklad ukazuje, jak můžete programově vytvořit vazbu na `DsCustomers1`tabulku Zákazníci v datové sadě s názvem :  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Pokud je tabulka Zákazníci jedinou tabulkou v datové sadě, můžete alternativně svázat mřížku tímto způsobem:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (Nepovinné) Přidejte do mřížky příslušné styly a styly sloupců. Pokud nejsou k dispozici žádné styly tabulky, zobrazí se tabulka, ale s minimálním formátováním a se všemi viditelnými sloupci.  
  
## <a name="see-also"></a>Viz také

- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
