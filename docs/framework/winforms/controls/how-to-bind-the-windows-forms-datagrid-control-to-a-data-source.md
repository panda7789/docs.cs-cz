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
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="19ef8-102">Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="19ef8-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="19ef8-103">Ovládací <xref:System.Windows.Forms.DataGridView> prvek nahradí a přidá <xref:System.Windows.Forms.DataGrid> funkce ovládacího prvku; <xref:System.Windows.Forms.DataGrid> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="19ef8-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="19ef8-104">Další informace naleznete v [tématu Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="19ef8-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="19ef8-105">Ovládací prvek <xref:System.Windows.Forms.DataGrid> Windows Forms je speciálně navržen tak, aby zobrazoval informace ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="19ef8-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="19ef8-106">Svázat ovládací prvek za běhu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="19ef8-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="19ef8-107">I když můžete zobrazit data z různých zdrojů dat, nejtypičtějšízdroje jsou datové sady a zobrazení dat.</span><span class="sxs-lookup"><span data-stu-id="19ef8-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="19ef8-108">Chcete-li data-bind ovládací prvek DataGrid programově</span><span class="sxs-lookup"><span data-stu-id="19ef8-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="19ef8-109">Napište kód pro vyplnění datové sady.</span><span class="sxs-lookup"><span data-stu-id="19ef8-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="19ef8-110">Pokud je zdrojem dat dat sada dat nebo zobrazení dat založené na tabulce datových sad, přidejte do formuláře kód pro vyplnění datové sady.</span><span class="sxs-lookup"><span data-stu-id="19ef8-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="19ef8-111">Přesný kód, který používáte, závisí na tom, kde datová sada získává data.</span><span class="sxs-lookup"><span data-stu-id="19ef8-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="19ef8-112">Pokud je datová sada naplněna přímo z databáze, `Fill` obvykle voláte metodu datového adaptéru, jako v `DsCategories1`následujícím příkladu, který naplňuje datovou sadu s názvem :</span><span class="sxs-lookup"><span data-stu-id="19ef8-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="19ef8-113">Pokud je datová sada vyplňována z webové služby XML, obvykle vytvoříte instanci služby v kódu a pak zavoláte jednu z jejích metod a vrátíte datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="19ef8-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="19ef8-114">Potom sloučit datovou sadu z webové služby XML do místní datové sady.</span><span class="sxs-lookup"><span data-stu-id="19ef8-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="19ef8-115">Následující příklad ukazuje, jak můžete vytvořit instanci `CategoriesService`webové `GetCategories` služby XML s názvem , volat její `DsCategories1`metodu a sloučit výslednou datovou sadu do místní datové sady s názvem :</span><span class="sxs-lookup"><span data-stu-id="19ef8-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="19ef8-116">Volání <xref:System.Windows.Forms.DataGrid> metody ovládacího <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> prvku, předání zdroje dat a datového člena.</span><span class="sxs-lookup"><span data-stu-id="19ef8-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="19ef8-117">Pokud nepotřebujete explicitně předat datový člen, předejte prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="19ef8-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="19ef8-118">Pokud jste vazba mřížky poprvé, můžete nastavit <xref:System.Windows.Forms.DataGrid.DataSource%2A> ovládací <xref:System.Windows.Forms.DataGrid.DataMember%2A> prvek a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="19ef8-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="19ef8-119">Tyto vlastnosti však nelze obnovit, jakmile byly nastaveny.</span><span class="sxs-lookup"><span data-stu-id="19ef8-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="19ef8-120">Proto se doporučuje vždy použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="19ef8-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="19ef8-121">Následující příklad ukazuje, jak můžete programově vytvořit vazbu na `DsCustomers1`tabulku Zákazníci v datové sadě s názvem :</span><span class="sxs-lookup"><span data-stu-id="19ef8-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="19ef8-122">Pokud je tabulka Zákazníci jedinou tabulkou v datové sadě, můžete alternativně svázat mřížku tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="19ef8-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="19ef8-123">(Nepovinné) Přidejte do mřížky příslušné styly a styly sloupců.</span><span class="sxs-lookup"><span data-stu-id="19ef8-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="19ef8-124">Pokud nejsou k dispozici žádné styly tabulky, zobrazí se tabulka, ale s minimálním formátováním a se všemi viditelnými sloupci.</span><span class="sxs-lookup"><span data-stu-id="19ef8-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ef8-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="19ef8-125">See also</span></span>

- [<span data-ttu-id="19ef8-126">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="19ef8-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="19ef8-127">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="19ef8-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="19ef8-128">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="19ef8-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="19ef8-129">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="19ef8-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
