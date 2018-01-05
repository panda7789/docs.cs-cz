---
title: "Postupy: vytváření seznamů seznam podrobnosti s ovládacím prvkem Windows Forms DataGrid"
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
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 516cdd8905b1566b9e3bc56f2652264c7f4c3b7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Postupy: Vytvoření hlavního/podrobného seznamu pomocí ovládacího prvku Windows Forms DataGrid
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pokud vaše <xref:System.Data.DataSet> obsahuje řadu související tabulky, můžete použít dva <xref:System.Windows.Forms.DataGrid> ovládacích prvků pro zobrazení dat ve formátu, a podrobností. Jeden <xref:System.Windows.Forms.DataGrid> je určen jako hlavní mřížky, a druhý je určený jako podrobnosti mřížky. Když vyberete položku v seznamu hlavní, všech souvisejících podřízených položek se zobrazí v seznamu podrobnosti. Například pokud vaše <xref:System.Data.DataSet> obsahuje tabulku zákazníků a související tabulky objednávky, zadali byste tabulku zákazníků jako hlavní mřížky a tabulky objednávky být podrobnosti mřížky. Pokud zákazník je vybraná z hlavní mřížky, všechny objednávky přidružené tohoto zákazníka v tabulce objednávky bude zobrazen v mřížce podrobností.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Chcete-li nastavit vztahu seznam podrobnosti prostřednictvím kódu programu  
  
1.  Vytvořte dvě nové <xref:System.Windows.Forms.DataGrid> ovládací prvky a nastavte jejich vlastnosti.  
  
2.  Přidání tabulky do datové sady.  
  
3.  Deklarace proměnné typu <xref:System.Data.DataRelation> představují vztah, který chcete vytvořit.  
  
4.  Instance relace se provádí zadáním názvu pro relaci a určením tabulky, sloupce a položku, která bude tie dvě tabulky.  
  
5.  Přidat vztah k <xref:System.Data.DataSet> objektu <xref:System.Data.DataSet.Relations%2A> kolekce.  
  
6.  Použití <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu <xref:System.Windows.Forms.DataGrid> pro každý z mřížky pro vazbu <xref:System.Data.DataSet>.  
  
     Následující příklad ukazuje, jak nastavit a podrobností relace mezi tabulkami Zákazníci a objednávky v dříve vytvořený <xref:System.Data.DataSet> (`ds`).  
  
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
 [Ovládací prvek DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Přehled ovládacího prvku DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
