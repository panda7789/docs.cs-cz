---
title: 'Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917729"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="68fe4-102">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid</span><span class="sxs-lookup"><span data-stu-id="68fe4-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="68fe4-103">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="68fe4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="68fe4-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="68fe4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="68fe4-105">Po vytvoření model Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí funkcí v době návrhu lze také dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="68fe4-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="68fe4-106">To může zahrnovat změny buď na jednotlivé hodnoty tabulky, nebo změnit, který zdroj dat je svázán s <xref:System.Windows.Forms.DataGrid> ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="68fe4-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="68fe4-107">Změny jednotlivých hodnot jsou prováděny prostřednictvím <xref:System.Data.DataSet> objektu, <xref:System.Windows.Forms.DataGrid> nikoli ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="68fe4-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="68fe4-108">Programové změny dat</span><span class="sxs-lookup"><span data-stu-id="68fe4-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="68fe4-109">Určete požadovanou tabulku z <xref:System.Data.DataSet> objektu a požadovaný řádek a pole z tabulky a nastavte buňku rovnou na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="68fe4-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="68fe4-110">Chcete-li zadat první tabulku <xref:System.Data.DataSet> nebo první řádek tabulky, použijte hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="68fe4-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="68fe4-111">Následující příklad ukazuje, jak změnit druhý záznam prvního řádku v první tabulce datové sady kliknutím na `Button1`.</span><span class="sxs-lookup"><span data-stu-id="68fe4-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="68fe4-112">Dříve <xref:System.Data.DataSet> se`ds`vytvořily ()`0` a `1`tabulky (a).</span><span class="sxs-lookup"><span data-stu-id="68fe4-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     <span data-ttu-id="68fe4-113">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="68fe4-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="68fe4-114">V době spuštění můžete použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu k <xref:System.Windows.Forms.DataGrid> navázání ovládacího prvku na jiný zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="68fe4-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="68fe4-115">Můžete mít například několik ovládacích prvků ADO.NET data, které jsou připojené k jiné databázi.</span><span class="sxs-lookup"><span data-stu-id="68fe4-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="68fe4-116">Chcete-li změnit zdroj dat programově</span><span class="sxs-lookup"><span data-stu-id="68fe4-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="68fe4-117"><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Nastavte metodu na název zdroje dat a tabulky, ke které chcete vytvořit propojení.</span><span class="sxs-lookup"><span data-stu-id="68fe4-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="68fe4-118">Následující příklad ukazuje, jak změnit zdroj dat pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody na ovládací prvek ADO.NET data (adoPubsAuthors), který je připojen k tabulce Autoři v databázi pubs.</span><span class="sxs-lookup"><span data-stu-id="68fe4-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="68fe4-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68fe4-119">See also</span></span>

- [<span data-ttu-id="68fe4-120">Datové sady ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68fe4-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="68fe4-121">Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="68fe4-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="68fe4-122">Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="68fe4-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="68fe4-123">Postupy: Navázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="68fe4-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
