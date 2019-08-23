---
title: 'Postupy: Vytvoření seznamu hlavní-podrobnosti pomocí model Windows Forms ovládacího prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914754"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Postupy: Vytvoření hlavního/podrobného seznamu pomocí ovládacího prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pokud obsahuje řadu souvisejících tabulek, můžete použít dva <xref:System.Windows.Forms.DataGrid> ovládací prvky k zobrazení dat v hlavním nebo podrobném formátu. <xref:System.Data.DataSet> Jedna <xref:System.Windows.Forms.DataGrid> je určena jako hlavní mřížka a druhá je označena jako mřížka podrobností. Když vyberete položku v seznamu hlavní seznam, zobrazí se v seznamu podrobnosti všechny související podřízené položky. Pokud <xref:System.Data.DataSet> například obsahuje tabulku Customers (zákazníci) a související tabulky objednávek, zadali byste tabulku Customers (zákazníci), která bude hlavní mřížkou, a tabulkou Orders, která bude mřížka podrobností. Když je zákazník vybraný z hlavní mřížky, v mřížce podrobností se zobrazí všechny objednávky přidružené k tomuto zákazníkovi v tabulce Orders.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Programové nastavení vztahu hlavní/podrobnosti  
  
1. Vytvořte dva nové <xref:System.Windows.Forms.DataGrid> ovládací prvky a nastavte jejich vlastnosti.  
  
2. Přidejte tabulky do datové sady.  
  
3. Deklarujte proměnnou typu <xref:System.Data.DataRelation> představující relaci, kterou chcete vytvořit.  
  
4. Vytvořte instanci vztahu zadáním názvu pro relaci a zadáním tabulky, sloupce a položky, které budou spojovat tyto dvě tabulky.  
  
5. Přidejte relaci do <xref:System.Data.DataSet> <xref:System.Data.DataSet.Relations%2A> kolekce objektu.  
  
6. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Použijte metodu <xref:System.Windows.Forms.DataGrid> pro svázání všech mřížek s <xref:System.Data.DataSet>.  
  
     Následující příklad ukazuje, jak nastavit relaci hlavního/podrobného vztahu mezi tabulkami Zákazníci a objednávky v dříve generované <xref:System.Data.DataSet> (`ds`).  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Navázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
