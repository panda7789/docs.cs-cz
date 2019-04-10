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
ms.openlocfilehash: bd26d396c238bfc53858320b8f4487df84b3436a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312576"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="125f1-102">Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="125f1-102">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="125f1-103">Ovládací prvky Windows Forms řazení, když jsou vázané na data.</span><span class="sxs-lookup"><span data-stu-id="125f1-103">Windows Forms controls do not sort when they are data-bound.</span></span> <span data-ttu-id="125f1-104">Seřazená data zobrazíte pomocí zdroje dat, který podporuje řazení a pak je mít zdroj dat seřadit.</span><span class="sxs-lookup"><span data-stu-id="125f1-104">To display sorted data, use a data source that supports sorting and then have the data source sort it.</span></span> <span data-ttu-id="125f1-105">Zdroje dat, které podporují řazení jsou data zobrazení, data zobrazení správci a seřadit pole.</span><span class="sxs-lookup"><span data-stu-id="125f1-105">Data sources that support sorting are data views, data view managers, and sorted arrays.</span></span>  
  
 <span data-ttu-id="125f1-106">Pokud ovládací prvek není vázaný na data, můžete je seřadit.</span><span class="sxs-lookup"><span data-stu-id="125f1-106">If the control is not data-bound, you can sort it.</span></span>  
  
### <a name="to-sort-the-list"></a><span data-ttu-id="125f1-107">Řazení seznamu</span><span class="sxs-lookup"><span data-stu-id="125f1-107">To sort the list</span></span>  
  
1. <span data-ttu-id="125f1-108">Nastavte `Sorted` vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="125f1-108">Set the `Sorted` property to `true`.</span></span>  
  
     <span data-ttu-id="125f1-109">Toto nastavení přemístí všechny existující položky seznamu v seřazeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="125f1-109">This setting repositions all existing list items in sorted order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125f1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="125f1-110">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="125f1-111">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="125f1-111">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="125f1-112">Postupy: Přidání a odebrání položek z ovládacích prvků Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="125f1-112">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="125f1-113">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="125f1-113">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="125f1-114">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="125f1-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
