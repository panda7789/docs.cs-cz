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
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="aad74-102">Postupy: Vytvoření hlavního/podrobného seznamu pomocí ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="aad74-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="aad74-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="aad74-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="aad74-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="aad74-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="aad74-105">Pokud vaše <xref:System.Data.DataSet> obsahuje řadu souvisejících tabulek, můžete použít dva ovládací prvky <xref:System.Windows.Forms.DataGrid> a zobrazit data v hlavním nebo podrobném formátu.</span><span class="sxs-lookup"><span data-stu-id="aad74-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="aad74-106">Jeden <xref:System.Windows.Forms.DataGrid> je označený jako hlavní mřížka a druhý je označený jako mřížka podrobností.</span><span class="sxs-lookup"><span data-stu-id="aad74-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="aad74-107">Když vyberete položku v seznamu hlavní seznam, zobrazí se v seznamu podrobnosti všechny související podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="aad74-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="aad74-108">Pokud například vaše <xref:System.Data.DataSet> obsahuje tabulku Customers (zákazníci) a související tabulky Orders, zadali byste tabulku Customers (zákazníci), která bude hlavní mřížkou, a tabulkou objednávky, která bude mřížka podrobností.</span><span class="sxs-lookup"><span data-stu-id="aad74-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="aad74-109">Když je zákazník vybraný z hlavní mřížky, v mřížce podrobností se zobrazí všechny objednávky přidružené k tomuto zákazníkovi v tabulce Orders.</span><span class="sxs-lookup"><span data-stu-id="aad74-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="aad74-110">Programové nastavení vztahu hlavní/podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aad74-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="aad74-111">Vytvořte dva nové ovládací prvky <xref:System.Windows.Forms.DataGrid> a nastavte jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aad74-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="aad74-112">Přidejte tabulky do datové sady.</span><span class="sxs-lookup"><span data-stu-id="aad74-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="aad74-113">Deklarujte proměnnou typu <xref:System.Data.DataRelation>, aby představovala vztah, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="aad74-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="aad74-114">Vytvořte instanci vztahu zadáním názvu pro relaci a zadáním tabulky, sloupce a položky, které budou spojovat tyto dvě tabulky.</span><span class="sxs-lookup"><span data-stu-id="aad74-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="aad74-115">Přidejte relaci do kolekce <xref:System.Data.DataSet.Relations%2A> objektů <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="aad74-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="aad74-116">K navázání každé mřížky na <xref:System.Data.DataSet>použijte metodu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="aad74-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="aad74-117">Následující příklad ukazuje, jak nastavit relaci hlavního/podrobného vztahu mezi tabulkami Zákazníci a objednávky v dříve generované <xref:System.Data.DataSet> (`ds`).</span><span class="sxs-lookup"><span data-stu-id="aad74-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aad74-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aad74-118">See also</span></span>

- [<span data-ttu-id="aad74-119">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="aad74-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="aad74-120">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="aad74-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="aad74-121">Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="aad74-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
