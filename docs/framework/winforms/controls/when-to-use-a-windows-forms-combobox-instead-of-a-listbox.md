---
title: Pole se seznamem vs. ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 7087760a393bb58d83d899c1741c745fb28585bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739926"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="c305d-102">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="c305d-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="c305d-103"><xref:System.Windows.Forms.ComboBox> a ovládací prvky <xref:System.Windows.Forms.ListBox> mají podobné chování a v některých případech mohou být zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="c305d-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="c305d-104">Existují však situace, kdy je jedna nebo druhá pro úkol vhodnější.</span><span class="sxs-lookup"><span data-stu-id="c305d-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="c305d-105">Obecně je pole se seznamem vhodné, pokud existuje seznam navrhovaných možností a seznam je vhodný, když chcete omezit vstup na to, co je v seznamu.</span><span class="sxs-lookup"><span data-stu-id="c305d-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="c305d-106">Pole se seznamem obsahuje pole textového pole, takže výběry, které nejsou na seznamu, lze zadat v.</span><span class="sxs-lookup"><span data-stu-id="c305d-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="c305d-107">Výjimkou je, když je vlastnost <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> nastavena na hodnotu <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="c305d-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="c305d-108">V takovém případě ovládací prvek vybere položku, pokud zadáte její první písmeno.</span><span class="sxs-lookup"><span data-stu-id="c305d-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="c305d-109">Kromě toho pole se seznamem šetří místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c305d-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="c305d-110">Vzhledem k tomu, že se úplný seznam nezobrazí, dokud uživatel neklikne na šipku dolů, pole se seznamem se dá snadno přizpůsobit na malé místo, kde se seznam nevejde.</span><span class="sxs-lookup"><span data-stu-id="c305d-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="c305d-111">Výjimkou je, že vlastnost <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na hodnotu <xref:System.Windows.Forms.ComboBoxStyle.Simple>: zobrazí se úplný seznam a pole se seznamem bude trvat více místa, než je pole seznamu.</span><span class="sxs-lookup"><span data-stu-id="c305d-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c305d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c305d-112">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="c305d-113">Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c305d-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="c305d-114">Postupy: Řazení obsahu ovládacího prvku ComboBox, ListBox nebo CheckedListBox z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c305d-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="c305d-115">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="c305d-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
