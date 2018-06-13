---
title: 'Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox'
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: 8b8f9c7ad0ad7d3bbb7f3eeffd44e555207b82c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535643"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="6e515-102">Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="6e515-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="6e515-103">Ovládací prvky Windows Forms řazení, když jsou vázané na data.</span><span class="sxs-lookup"><span data-stu-id="6e515-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="6e515-104">Pokud chcete zobrazit seřazená data, používat zdroj dat, který podporuje řazení a tak zdroji dat se seřadí.</span><span class="sxs-lookup"><span data-stu-id="6e515-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="6e515-105">Zdroje dat, které podporují řazení jsou zobrazení dat, data správci zobrazit a seřadit pole.</span><span class="sxs-lookup"><span data-stu-id="6e515-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="6e515-106">Pokud ovládací prvek není vázané na data, je možné seřadit.</span><span class="sxs-lookup"><span data-stu-id="6e515-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="6e515-107">Pokud chcete seřadit</span><span class="sxs-lookup"><span data-stu-id="6e515-107">To sort the list</span></span>  
  
1.  <span data-ttu-id="6e515-108">Nastavte `Sorted` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="6e515-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="6e515-109">Toto nastavení přemístí všechny existující položky seznamu seřazená.</span><span class="sxs-lookup"><span data-stu-id="6e515-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e515-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e515-110">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="6e515-111">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="6e515-111">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="6e515-112">Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e515-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="6e515-113">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="6e515-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="6e515-114">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="6e515-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
