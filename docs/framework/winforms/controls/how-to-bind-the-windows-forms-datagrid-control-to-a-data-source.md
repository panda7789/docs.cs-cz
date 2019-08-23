---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat'
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
ms.openlocfilehash: bac24c2dd622ea780408e902d08708ac09561044
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922729"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Model Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je speciálně navržen pro zobrazení informací ze zdroje dat. Ovládací prvek navážete za běhu voláním <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody. I když můžete zobrazit data z nejrůznějších zdrojů dat, nejdůležitější zdroje jsou datové sady a zobrazení dat.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Pro datovou svázání ovládacího prvku DataGrid prostřednictvím kódu programu  
  
1. Zadejte kód, který bude datovou sadu vyplnit.  
  
     Pokud je zdrojem dat datová sada nebo zobrazení dat založené na tabulce DataSet, přidejte do formuláře kód, který datovou sadu vyplní.  
  
     Přesný kód, který použijete, závisí na tom, kde datová sada získává data. Pokud je datová sada naplněna přímo z databáze, obvykle zavoláte `Fill` metodu datového adaptéru, jak je uvedeno v následujícím příkladu, který naplňuje datovou sadu s `DsCategories1`názvem:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Pokud je datová sada vyplněna z webové služby XML, obvykle je ve svém kódu vytvořena instance služby a poté je volána jedna z metod, která vrátí datovou sadu. Datovou sadu pak sloučíte z webové služby XML do vaší místní datové sady. Následující příklad ukazuje, jak lze vytvořit instanci webové služby XML s názvem `CategoriesService`, zavolat její `GetCategories` metodu a sloučit výslednou datovou sadu do místní datové sady s názvem `DsCategories1`:  
  
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
  
2. <xref:System.Windows.Forms.DataGrid> Zavolejte metodu<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> ovládacího prvku a předejte jí zdroj dat a datový člen. Pokud nepotřebujete explicitně předat datový člen, předejte prázdný řetězec.  
  
    > [!NOTE]
    > Pokud vytváříte vazbu k mřížce poprvé, můžete nastavit vlastnosti ovládacího prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> a. <xref:System.Windows.Forms.DataGrid.DataMember%2A> Po nastavení ale tyto vlastnosti nemůžete resetovat. Proto se doporučuje vždy používat <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu.  
  
     Následující příklad ukazuje, jak lze programově navazovat vazby na tabulku Customers v datové sadě `DsCustomers1`s názvem:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Pokud tabulka Customers (zákazníci) je jediná tabulka v datové sadě, můžete datovou mřížku vytvořit jinak, a to takto:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. Volitelné Přidejte do mřížky vhodné styly tabulek a sloupců. Pokud neexistují žádné styly tabulek, zobrazí se tabulka, ale s minimálním formátováním a všemi zobrazenými sloupci.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
