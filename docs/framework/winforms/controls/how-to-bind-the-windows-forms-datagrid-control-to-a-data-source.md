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
ms.openlocfilehash: 5f8c0c2865d219eecb88ddd176d99f80521c9ab3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664210"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="16c0a-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="16c0a-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
>  <span data-ttu-id="16c0a-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="16c0a-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="16c0a-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="16c0a-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="16c0a-105">Windows Forms <xref:System.Windows.Forms.DataGrid> ovládací prvek je navržená speciálně pro zobrazení informací ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="16c0a-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="16c0a-106">Vazbu ovládacího prvku za běhu pomocí volání <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="16c0a-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="16c0a-107">Přestože lze zobrazit data z různých zdrojů dat, obvykle zdroje jsou datové sady a data zobrazení.</span><span class="sxs-lookup"><span data-stu-id="16c0a-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="16c0a-108">Vytvořit vazbu na data ovládacím prvku DataGrid prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="16c0a-108">To data-bind the DataGrid control programmatically</span></span>  
  
1.  <span data-ttu-id="16c0a-109">Napište kód pro naplnění dataset.</span><span class="sxs-lookup"><span data-stu-id="16c0a-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="16c0a-110">Pokud je zdroj dat datové sady nebo zobrazení dat na základě tabulky datovou sadu, přidejte kód pro formulář k vyplnění datové sady.</span><span class="sxs-lookup"><span data-stu-id="16c0a-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="16c0a-111">Přesný kód, který používáte závisí na datové sady je kde získávají data.</span><span class="sxs-lookup"><span data-stu-id="16c0a-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="16c0a-112">Pokud probíhá naplňování datové sady přímo z databáze, obvykle volat `Fill` metoda adaptéru dat, stejně jako v následujícím příkladu, který naplňuje datovou sadu s názvem `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="16c0a-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="16c0a-113">Pokud se naplní datové sady z webové služby XML, obvykle vytvoříte instanci služby ve vašem kódu a pak volat jednu z jeho metod vrátí datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="16c0a-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="16c0a-114">Pak sloučit datové sady z XML webové služby do místní datové sady.</span><span class="sxs-lookup"><span data-stu-id="16c0a-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="16c0a-115">Následující příklad ukazuje, jak můžete vytvořit instanci XML webové služby názvem `CategoriesService`, zavolejte jeho `GetCategories` metoda a sloučení volá výsledné datové sady do místní datové sady `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="16c0a-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2.  <span data-ttu-id="16c0a-116">Volání <xref:System.Windows.Forms.DataGrid> ovládacího prvku <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu předáním zdroje dat a datový člen.</span><span class="sxs-lookup"><span data-stu-id="16c0a-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="16c0a-117">Pokud není potřeba explicitně předávat datový člen, zadat prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="16c0a-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16c0a-118">Pokud mřížky připojujete poprvé, můžete nastavit ovládací prvek <xref:System.Windows.Forms.DataGrid.DataSource%2A> a <xref:System.Windows.Forms.DataGrid.DataMember%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="16c0a-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="16c0a-119">Tyto vlastnosti však nelze obnovit, jakmile byla nastavena.</span><span class="sxs-lookup"><span data-stu-id="16c0a-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="16c0a-120">Proto doporučujeme vždy používat <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="16c0a-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="16c0a-121">Následující příklad ukazuje, jak můžete prostřednictvím kódu programu vázat na tabulku Customers v datovou sadu s názvem `DsCustomers1`:</span><span class="sxs-lookup"><span data-stu-id="16c0a-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="16c0a-122">Pokud je tabulka zákazníkům pouze tabulky v datové sadě, může také svážete mřížky tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="16c0a-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  <span data-ttu-id="16c0a-123">(Volitelné) Přidejte příslušné tabulky styly a styly sloupců do mřížky.</span><span class="sxs-lookup"><span data-stu-id="16c0a-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="16c0a-124">Pokud neexistují žádné tabulky styly, zobrazí se v tabulce, ale s minimální formátování a všechny viditelné sloupce.</span><span class="sxs-lookup"><span data-stu-id="16c0a-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c0a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16c0a-125">See also</span></span>
- [<span data-ttu-id="16c0a-126">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="16c0a-126">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="16c0a-127">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="16c0a-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="16c0a-128">Ovládací prvek DataGrid</span><span class="sxs-lookup"><span data-stu-id="16c0a-128">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [<span data-ttu-id="16c0a-129">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="16c0a-129">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)
