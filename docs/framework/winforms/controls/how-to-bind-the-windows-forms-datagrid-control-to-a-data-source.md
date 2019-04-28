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
ms.openlocfilehash: 920a93894cc126f85bc6b618efbe6e9cedea4881
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666427"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je navržená speciálně pro zobrazení informací ze zdroje dat. Vazbu ovládacího prvku za běhu pomocí volání <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody. Přestože lze zobrazit data z různých zdrojů dat, obvykle zdroje jsou datové sady a data zobrazení.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Vytvořit vazbu na data ovládacím prvku DataGrid prostřednictvím kódu programu  
  
1. Napište kód pro naplnění dataset.  
  
     Pokud je zdroj dat datové sady nebo zobrazení dat na základě tabulky datovou sadu, přidejte kód pro formulář k vyplnění datové sady.  
  
     Přesný kód, který používáte závisí na datové sady je kde získávají data. Pokud probíhá naplňování datové sady přímo z databáze, obvykle volat `Fill` metoda adaptéru dat, stejně jako v následujícím příkladu, který naplňuje datovou sadu s názvem `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Pokud se naplní datové sady z webové služby XML, obvykle vytvoříte instanci služby ve vašem kódu a pak volat jednu z jeho metod vrátí datovou sadu. Pak sloučit datové sady z XML webové služby do místní datové sady. Následující příklad ukazuje, jak můžete vytvořit instanci XML webové služby názvem `CategoriesService`, zavolejte jeho `GetCategories` metoda a sloučení volá výsledné datové sady do místní datové sady `DsCategories1`:  
  
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
  
2. Volání <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu předáním zdroje dat a datový člen. Pokud není potřeba explicitně předávat datový člen, zadat prázdný řetězec.  
  
    > [!NOTE]
    >  Pokud mřížky připojujete poprvé, můžete nastavit ovládací prvek <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti. Tyto vlastnosti však nelze obnovit, jakmile byla nastavena. Proto doporučujeme vždy používat <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.  
  
     Následující příklad ukazuje, jak můžete prostřednictvím kódu programu vázat na tabulku Customers v datovou sadu s názvem `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Pokud je tabulka zákazníkům pouze tabulky v datové sadě, může také svážete mřížky tímto způsobem:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (Volitelné) Přidejte příslušné tabulky styly a styly sloupců do mřížky. Pokud neexistují žádné tabulky styly, zobrazí se v tabulce, ale s minimální formátování a všechny viditelné sloupce.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
