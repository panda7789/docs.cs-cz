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
ms.openlocfilehash: 3217680a2bab43124b75529bead97ffcfbb06aea
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882140"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="716b3-102">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid DataGrid</span><span class="sxs-lookup"><span data-stu-id="716b3-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="716b3-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.DataGrid> řízení; však <xref:System.Windows.Forms.DataGrid> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="716b3-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="716b3-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="716b3-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="716b3-105">Po vytvoření prvku Windows Forms <xref:System.Windows.Forms.DataGrid> díky funkcím, návrhu, můžete také chtít dynamicky měnit prvky <xref:System.Data.DataSet> objektu mřížky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="716b3-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="716b3-106">To může zahrnovat změny buď jednotlivé hodnoty v tabulce nebo změna zdroj dat, který je vázán <xref:System.Windows.Forms.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="716b3-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="716b3-107">Změny v jednotlivých hodnot se provádí prostřednictvím <xref:System.Data.DataSet> objektu, nikoli <xref:System.Windows.Forms.DataGrid> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="716b3-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="716b3-108">Změna dat prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="716b3-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="716b3-109">Zadejte požadovanou tabulku z <xref:System.Data.DataSet> objektu a požadovaný řádek pole z tabulky a buňky nastavena na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="716b3-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="716b3-110">Chcete-li určit první tabulky <xref:System.Data.DataSet> nebo první řádek tabulky, použijte 0.</span><span class="sxs-lookup"><span data-stu-id="716b3-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="716b3-111">Následující příklad ukazuje, jak změnit druhou položku první řádek první tabulky datovou sadu kliknutím `Button1`.</span><span class="sxs-lookup"><span data-stu-id="716b3-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="716b3-112"><xref:System.Data.DataSet> (`ds`) A tabulky (`0` a `1`) byly dříve vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="716b3-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="716b3-113">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="716b3-113">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="716b3-114">Během spuštění můžete použít <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodu pro vytvoření vazby <xref:System.Windows.Forms.DataGrid> ovládacího prvku k jinému zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="716b3-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="716b3-115">Například můžete mít několik ovládacích prvků dat ADO.NET, každý z nich připojený k jiné databázi.</span><span class="sxs-lookup"><span data-stu-id="716b3-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="716b3-116">Chcete-li změnit zdroj dat prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="716b3-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="716b3-117">Nastavte <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody k názvu zdroje dat a tabulku, kterou chcete svázat.</span><span class="sxs-lookup"><span data-stu-id="716b3-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="716b3-118">Následující příklad ukazuje, jak změnit datum zdroje pomocí <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda na ovládací prvek dat ADO.NET (adoPubsAuthors), který je připojený k tabulce Autoři databáze Pubs.</span><span class="sxs-lookup"><span data-stu-id="716b3-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="716b3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="716b3-119">See also</span></span>

- [<span data-ttu-id="716b3-120">Datové sady ADO.NET</span><span class="sxs-lookup"><span data-stu-id="716b3-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="716b3-121">Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="716b3-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="716b3-122">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="716b3-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="716b3-123">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="716b3-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
