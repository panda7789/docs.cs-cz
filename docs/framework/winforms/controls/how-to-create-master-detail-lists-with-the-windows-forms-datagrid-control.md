---
title: Vytvoření seznamu hlavní-podrobnosti pomocí ovládacího prvku DataGrid
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
ms.openlocfilehash: e8ab63d52d97a8a6e6f60da741186e3937350e1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730983"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Postupy: Vytvoření hlavního/podrobného seznamu pomocí ovládacího prvku Windows Forms DataGrid
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pokud vaše <xref:System.Data.DataSet> obsahuje řadu souvisejících tabulek, můžete použít dva ovládací prvky <xref:System.Windows.Forms.DataGrid> a zobrazit data v hlavním nebo podrobném formátu. Jeden <xref:System.Windows.Forms.DataGrid> je označený jako hlavní mřížka a druhý je označený jako mřížka podrobností. Když vyberete položku v seznamu hlavní seznam, zobrazí se v seznamu podrobnosti všechny související podřízené položky. Pokud například vaše <xref:System.Data.DataSet> obsahuje tabulku Customers (zákazníci) a související tabulky Orders, zadali byste tabulku Customers (zákazníci), která bude hlavní mřížkou, a tabulkou objednávky, která bude mřížka podrobností. Když je zákazník vybraný z hlavní mřížky, v mřížce podrobností se zobrazí všechny objednávky přidružené k tomuto zákazníkovi v tabulce Orders.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Programové nastavení vztahu hlavní/podrobnosti  
  
1. Vytvořte dva nové ovládací prvky <xref:System.Windows.Forms.DataGrid> a nastavte jejich vlastnosti.  
  
2. Přidejte tabulky do datové sady.  
  
3. Deklarujte proměnnou typu <xref:System.Data.DataRelation>, aby představovala vztah, který chcete vytvořit.  
  
4. Vytvořte instanci vztahu zadáním názvu pro relaci a zadáním tabulky, sloupce a položky, které budou spojovat tyto dvě tabulky.  
  
5. Přidejte relaci do kolekce <xref:System.Data.DataSet.Relations%2A> objektů <xref:System.Data.DataSet>.  
  
6. K navázání každé mřížky na <xref:System.Data.DataSet>použijte metodu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> <xref:System.Windows.Forms.DataGrid>.  
  
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
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGrid](datagrid-control-windows-forms.md)
- [Přehled ovládacího prvku DataGrid](datagrid-control-overview-windows-forms.md)
- [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
