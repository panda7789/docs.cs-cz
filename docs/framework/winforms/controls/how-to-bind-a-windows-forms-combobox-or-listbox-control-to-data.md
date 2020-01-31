---
title: Vazba ovládacího prvku ComboBox nebo ListBox na data
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
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742031"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="52e52-102">Postupy: Vázání ovládacího prvku Windows Forms ComboBox nebo ListBox k datům</span><span class="sxs-lookup"><span data-stu-id="52e52-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="52e52-103">Můžete navazovat <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> na data, abyste mohli provádět úlohy, jako je například procházení dat v databázi, zadávání nových dat nebo úprava stávajících dat.</span><span class="sxs-lookup"><span data-stu-id="52e52-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="52e52-104">Svázání ovládacího prvku ComboBox nebo ListBox</span><span class="sxs-lookup"><span data-stu-id="52e52-104">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="52e52-105">Vlastnost `DataSource` nastavte na objekt zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="52e52-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="52e52-106">Možné zdroje dat zahrnují <xref:System.Windows.Forms.BindingSource> vázaný na data, datovou tabulku, zobrazení dat, datovou sadu, Správce zobrazení dat, pole nebo libovolnou třídu, která implementuje rozhraní <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="52e52-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="52e52-107">Další informace najdete v tématu [zdroje dat podporované nástrojem model Windows Forms](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="52e52-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="52e52-108">Pokud vytváříte vazbu na tabulku, nastavte vlastnost `DisplayMember` na název sloupce ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="52e52-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="52e52-109">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="52e52-109">\- or -</span></span>  
  
     <span data-ttu-id="52e52-110">Pokud vytváříte vazbu na <xref:System.Collections.IList>, nastavte člena zobrazení na veřejnou vlastnost typu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="52e52-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="52e52-111">Pokud jste vázáni na zdroj dat, který neimplementuje rozhraní <xref:System.ComponentModel.IBindingList>, například <xref:System.Collections.ArrayList>, data vázaného ovládacího prvku nebudou aktualizována při aktualizaci zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="52e52-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="52e52-112">Například pokud máte pole se seznamem vázané na <xref:System.Collections.ArrayList> a data jsou přidána do <xref:System.Collections.ArrayList>, tyto nové položky se nezobrazí v poli se seznamem.</span><span class="sxs-lookup"><span data-stu-id="52e52-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="52e52-113">Můžete však vynutit aktualizaci pole se seznamem voláním <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> a <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>ch metod na instanci třídy <xref:System.Windows.Forms.BindingContext>, ke které je ovládací prvek vázán.</span><span class="sxs-lookup"><span data-stu-id="52e52-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e52-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52e52-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="52e52-115">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="52e52-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="52e52-116">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52e52-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="52e52-117">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="52e52-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
