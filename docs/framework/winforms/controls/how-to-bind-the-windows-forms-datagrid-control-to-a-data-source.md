---
title: "Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat"
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c136aca0eda9ea906ad8bf6853a263adf6130609
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je určená speciálně pro zobrazení informací ze zdroje dat. Vytvoření vazby ovládacího prvku v době běhu voláním <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda. I když můžete zobrazit data z různých zdrojů dat, některé běžné zdroje jsou datové sady a data zobrazení.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Chcete vytvořit datovou vazbu ovládacího prvku DataGrid prostřednictvím kódu programu  
  
1.  Napište kód pro vyplnění datové sady.  
  
     Pokud je zdroj dat datové sady nebo zobrazení dat na základě datové sady tabulky, přidejte kód pro formulář k vyplnění datové sady.  
  
     Přesný kód, který používáte, závisí na kterém je datová sada získávání dat. Pokud se datová sada je právě nezadají přímo z databáze, obvykle volání `Fill` metoda adaptér pro data, jako v následujícím příkladu, který naplní datovou sadu s názvem `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Pokud se datová sada se naplní z webové služby XML, obvykle vytvoření instance služby v kódu a pak volání jednoho z jeho metody vrátit datovou sadu. Pak sloučit datové sady z webové služby XML do místní datovou sadu. Následující příklad ukazuje, jak můžete vytvořit instanci webové služby XML názvem `CategoriesService`, volání jeho `GetCategories` metoda a merge názvem výsledné datové sady do místní datové sady `DsCategories1`:  
  
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
  
2.  Volání <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda, předání zdroje dat a dat člena. Pokud není nutné explicitně předat data člena, zadat prázdný řetězec.  
  
    > [!NOTE]
    >  Pokud vytváříte vazbu mřížky poprvé, můžete nastavit ovládacího prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti. Tyto vlastnosti však nelze obnovit po byla nastavena. Proto se doporučuje, aby vždy použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda.  
  
     Následující příklad ukazuje, jak můžete programově vázat na tabulku zákazníků v datovou sadu s názvem `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Pokud je tabulka Zákazníci pouze tabulky v datové sadě, které může navázat mřížky tímto způsobem:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  (Volitelné) Přidejte příslušné tabulce styly a styly sloupců do mřížky. Pokud neexistují žádné tabulky styly, zobrazí se v tabulce, ale s minimálním formátování a všechny sloupce, které jsou viditelné.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)
