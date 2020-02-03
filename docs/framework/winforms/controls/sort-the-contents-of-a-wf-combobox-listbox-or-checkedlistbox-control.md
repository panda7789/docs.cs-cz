---
title: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: dee969d777edf76434622fe632f7e934987a1dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742963"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="d5229-102">Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="d5229-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="d5229-103">Model Windows Forms ovládací prvky nelze seřadit, jsou-li vázány na data.</span><span class="sxs-lookup"><span data-stu-id="d5229-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="d5229-104">Chcete-li zobrazit seřazená data, použijte zdroj dat, který podporuje řazení a potom zdroj dat seřaďte.</span><span class="sxs-lookup"><span data-stu-id="d5229-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="d5229-105">Zdroje dat, které podporují řazení, jsou zobrazení dat, manažeři zobrazení dat a seřazená pole.</span><span class="sxs-lookup"><span data-stu-id="d5229-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="d5229-106">Pokud ovládací prvek není vázán na data, můžete jej seřadit.</span><span class="sxs-lookup"><span data-stu-id="d5229-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="d5229-107">Řazení seznamu</span><span class="sxs-lookup"><span data-stu-id="d5229-107">To sort the list</span></span>  
  
1. <span data-ttu-id="d5229-108">Vlastnost `Sorted` nastavte na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="d5229-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="d5229-109">Toto nastavení přemístí všechny existující položky seznamu v seřazeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d5229-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5229-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5229-110">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="d5229-111">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="d5229-111">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="d5229-112">Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5229-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="d5229-113">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="d5229-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="d5229-114">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="d5229-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
