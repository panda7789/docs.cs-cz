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
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="6e1c1-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="6e1c1-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="6e1c1-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="6e1c1-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="6e1c1-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6e1c1-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="6e1c1-105">Model Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je speciálně navržen pro zobrazení informací ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="6e1c1-106">Ovládací prvek navážete za běhu voláním <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="6e1c1-107">I když můžete zobrazit data z nejrůznějších zdrojů dat, nejdůležitější zdroje jsou datové sady a zobrazení dat.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="6e1c1-108">Pro datovou svázání ovládacího prvku DataGrid prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="6e1c1-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="6e1c1-109">Zadejte kód, který bude datovou sadu vyplnit.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="6e1c1-110">Pokud je zdrojem dat datová sada nebo zobrazení dat založené na tabulce DataSet, přidejte do formuláře kód, který datovou sadu vyplní.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="6e1c1-111">Přesný kód, který použijete, závisí na tom, kde datová sada získává data.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="6e1c1-112">Pokud je datová sada naplněna přímo z databáze, obvykle zavoláte `Fill` metodu datového adaptéru, jak je uvedeno v následujícím příkladu, který naplňuje datovou sadu s `DsCategories1`názvem:</span><span class="sxs-lookup"><span data-stu-id="6e1c1-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="6e1c1-113">Pokud je datová sada vyplněna z webové služby XML, obvykle je ve svém kódu vytvořena instance služby a poté je volána jedna z metod, která vrátí datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="6e1c1-114">Datovou sadu pak sloučíte z webové služby XML do vaší místní datové sady.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="6e1c1-115">Následující příklad ukazuje, jak lze vytvořit instanci webové služby XML s názvem `CategoriesService`, zavolat její `GetCategories` metodu a sloučit výslednou datovou sadu do místní datové sady s názvem `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="6e1c1-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="6e1c1-116"><xref:System.Windows.Forms.DataGrid> Zavolejte metodu<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> ovládacího prvku a předejte jí zdroj dat a datový člen.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="6e1c1-117">Pokud nepotřebujete explicitně předat datový člen, předejte prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6e1c1-118">Pokud vytváříte vazbu k mřížce poprvé, můžete nastavit vlastnosti ovládacího prvku <xref:System.Windows.Forms.DataGrid.DataSource%2A> a. <xref:System.Windows.Forms.DataGrid.DataMember%2A></span><span class="sxs-lookup"><span data-stu-id="6e1c1-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="6e1c1-119">Po nastavení ale tyto vlastnosti nemůžete resetovat.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="6e1c1-120">Proto se doporučuje vždy používat <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="6e1c1-121">Následující příklad ukazuje, jak lze programově navazovat vazby na tabulku Customers v datové sadě `DsCustomers1`s názvem:</span><span class="sxs-lookup"><span data-stu-id="6e1c1-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="6e1c1-122">Pokud tabulka Customers (zákazníci) je jediná tabulka v datové sadě, můžete datovou mřížku vytvořit jinak, a to takto:</span><span class="sxs-lookup"><span data-stu-id="6e1c1-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="6e1c1-123">Volitelné Přidejte do mřížky vhodné styly tabulek a sloupců.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="6e1c1-124">Pokud neexistují žádné styly tabulek, zobrazí se tabulka, ale s minimálním formátováním a všemi zobrazenými sloupci.</span><span class="sxs-lookup"><span data-stu-id="6e1c1-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1c1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e1c1-125">See also</span></span>

- [<span data-ttu-id="6e1c1-126">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="6e1c1-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="6e1c1-127">Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="6e1c1-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="6e1c1-128">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="6e1c1-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="6e1c1-129">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="6e1c1-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
