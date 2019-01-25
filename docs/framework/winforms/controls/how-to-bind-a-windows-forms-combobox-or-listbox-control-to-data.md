---
title: 'Postupy: Windows Forms ComboBox nebo ListBox – ovládací prvek svázat Data'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 4220e3e7d750e0d0caf0adbcbd2e1d96131e7c88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698372"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="173ed-102">Postupy: Windows Forms ComboBox nebo ListBox – ovládací prvek svázat Data</span><span class="sxs-lookup"><span data-stu-id="173ed-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="173ed-103">Můžete vytvořit vazbu <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> k datům s cílem provést úlohy, jako je procházení dat v databázi, zadáním nových dat nebo úpravy existující data.</span><span class="sxs-lookup"><span data-stu-id="173ed-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="173ed-104">K vytvoření vazby ovládacího prvku ComboBox nebo ListBox</span><span class="sxs-lookup"><span data-stu-id="173ed-104">To bind a ComboBox or ListBox control</span></span>  
  
1.  <span data-ttu-id="173ed-105">Nastavte `DataSource` vlastnost na objekt zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="173ed-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="173ed-106">Zdroje dat patří <xref:System.Windows.Forms.BindingSource> vázán na data, data tabulky, zobrazení dat, datové sady, data zobrazení, správce, pole nebo jakékoli třídy, která implementuje <xref:System.Collections.IList> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="173ed-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="173ed-107">Další informace najdete v tématu [zdroje dat podporované rozhraním Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="173ed-107">For more information, see [Data Sources Supported by Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="173ed-108">Pokud vytváříte vazbu na tabulku, nastavte `DisplayMember` nastavte na název sloupce ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="173ed-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="173ed-109">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="173ed-109">\- or -</span></span>  
  
     <span data-ttu-id="173ed-110">Pokud se vazba na <xref:System.Collections.IList>, nastavte veřejnou vlastnost typu v seznamu zobrazit člena.</span><span class="sxs-lookup"><span data-stu-id="173ed-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="173ed-111">Pokud jsou vázány na zdroj dat, který neimplementuje <xref:System.ComponentModel.IBindingList> rozhraní, například <xref:System.Collections.ArrayList>, vázaného ovládacího prvku dat nebude aktualizovat, když dojde k aktualizaci zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="173ed-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="173ed-112">Například pokud máte pole se seznamem povinen <xref:System.Collections.ArrayList> a data je přidána do <xref:System.Collections.ArrayList>, tyto nové položky v poli se seznamem nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="173ed-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="173ed-113">Ale můžete vynutit pole se seznamem aktualizovat voláním <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> a <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> metody instance <xref:System.Windows.Forms.BindingContext> třídy pro ovládací prvek vázán.</span><span class="sxs-lookup"><span data-stu-id="173ed-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173ed-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="173ed-114">See also</span></span>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="173ed-115">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="173ed-115">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)
- [<span data-ttu-id="173ed-116">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="173ed-116">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)
- [<span data-ttu-id="173ed-117">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="173ed-117">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
