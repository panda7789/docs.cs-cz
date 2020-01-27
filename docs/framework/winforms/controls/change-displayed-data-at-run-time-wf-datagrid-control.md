---
title: Změna zobrazených dat v době běhu v ovládacím prvku DataGrid
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
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740590"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="ac8d6-102">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid</span><span class="sxs-lookup"><span data-stu-id="ac8d6-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="ac8d6-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="ac8d6-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ac8d6-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="ac8d6-105">Po vytvoření model Windows Forms <xref:System.Windows.Forms.DataGrid> pomocí funkcí v době návrhu můžete také v době běhu chtít dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="ac8d6-106">To může zahrnovat změny buď v jednotlivých hodnotách tabulky, nebo měnit, který zdroj dat je svázán s ovládacím prvkem <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="ac8d6-107">Změny jednotlivých hodnot se provádí prostřednictvím objektu <xref:System.Data.DataSet>, nikoli pomocí ovládacího prvku <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="ac8d6-108">Programové změny dat</span><span class="sxs-lookup"><span data-stu-id="ac8d6-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="ac8d6-109">Určete požadovanou tabulku z objektu <xref:System.Data.DataSet> a požadovaný řádek a pole z tabulky a nastavte buňku rovnou na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ac8d6-110">Chcete-li zadat první tabulku <xref:System.Data.DataSet> nebo první řádek tabulky, použijte hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="ac8d6-111">Následující příklad ukazuje, jak změnit druhý záznam prvního řádku v první tabulce datové sady kliknutím na `Button1`.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="ac8d6-112">Již byly vytvořeny <xref:System.Data.DataSet> (`ds`) a tabulky (`0` a `1`).</span><span class="sxs-lookup"><span data-stu-id="ac8d6-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="ac8d6-113">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="ac8d6-114">V době spuštění můžete použít metodu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> k navázání ovládacího prvku <xref:System.Windows.Forms.DataGrid> na jiný zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="ac8d6-115">Můžete mít například několik ovládacích prvků ADO.NET data, které jsou připojené k jiné databázi.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="ac8d6-116">Chcete-li změnit zdroj dat programově</span><span class="sxs-lookup"><span data-stu-id="ac8d6-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="ac8d6-117">Nastavte metodu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> na název zdroje dat a tabulky, ke které chcete vytvořit propojení.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="ac8d6-118">Následující příklad ukazuje, jak změnit zdroj dat pomocí metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> k ovládacímu prvku ADO.NET data (adoPubsAuthors), který je připojen k tabulce Autoři v databázi pubs.</span><span class="sxs-lookup"><span data-stu-id="ac8d6-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac8d6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac8d6-119">See also</span></span>

- [<span data-ttu-id="ac8d6-120">Datové sady ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ac8d6-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="ac8d6-121">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="ac8d6-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="ac8d6-122">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="ac8d6-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="ac8d6-123">Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="ac8d6-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
