---
title: 'Postupy: Vytvořit hlavní podrobných seznamů pomocí ovládacího prvku Windows Forms DataGrid'
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
ms.openlocfilehash: 92b4a7d9513ce0ec9b7c02f57c23fa4267fb26ad
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302396"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="76411-102">Postupy: Vytvoření hlavního/podrobného seznamu pomocí ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="76411-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="76411-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="76411-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="76411-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="76411-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="76411-105">Pokud vaše <xref:System.Data.DataSet> obsahuje řadu souvisejících tabulek, můžete použít dvě <xref:System.Windows.Forms.DataGrid> ovládacích prvků pro zobrazení dat ve formátu hlavního záznamu/podrobností.</span><span class="sxs-lookup"><span data-stu-id="76411-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="76411-106">Jeden <xref:System.Windows.Forms.DataGrid> je určen jako hlavní mřížky, a druhý je určený být mřížku podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="76411-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="76411-107">Když vyberete položku v seznamu hlavních, všechny související podřízené položky jsou uvedeny v seznamu podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="76411-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="76411-108">Například pokud vaše <xref:System.Data.DataSet> obsahuje tabulku zákazníků a související tabulku Orders, zadali byste na hlavní mřížka tabulky Zákazníci a být mřížku podrobnosti o objednávkách.</span><span class="sxs-lookup"><span data-stu-id="76411-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="76411-109">Když je zákazník vybrán z hlavní mřížky, všech objednávek tohoto zákazníka v tabulce objednávky přidružené by zobrazí v mřížce podrobností.</span><span class="sxs-lookup"><span data-stu-id="76411-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="76411-110">Chcete-li nastavit vztah záznamů master/detail prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="76411-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="76411-111">Vytvořit dvě nové <xref:System.Windows.Forms.DataGrid> ovládací prvky a nastavte jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="76411-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="76411-112">Přidání tabulek do datové sady.</span><span class="sxs-lookup"><span data-stu-id="76411-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="76411-113">Deklarovat proměnnou typu <xref:System.Data.DataRelation> k vyjádření vztahu, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="76411-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="76411-114">Zadejte název pro relaci a určením tabulky, sloupce a položku, která bude tyto dvě tabulky spojit vytvořit instanci relace.</span><span class="sxs-lookup"><span data-stu-id="76411-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="76411-115">Přidat vztah k <xref:System.Data.DataSet> objektu <xref:System.Data.DataSet.Relations%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="76411-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="76411-116">Použití <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu <xref:System.Windows.Forms.DataGrid> pro každý z mřížky pro vazbu <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="76411-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="76411-117">Následující příklad ukazuje, jak nastavit záznamů master/detail relace mezi tabulkami Zákazníci a objednávky v dříve vytvořenou <xref:System.Data.DataSet> (`ds`).</span><span class="sxs-lookup"><span data-stu-id="76411-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76411-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76411-118">See also</span></span>

- [<span data-ttu-id="76411-119">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="76411-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="76411-120">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="76411-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="76411-121">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="76411-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
