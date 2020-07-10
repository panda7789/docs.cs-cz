---
title: Pole se seznamem vs. ListBox
description: Seznamte se s používáním model Windows Forms pole se seznamem a model Windows Forms seznamem a Naučte se, jak dejte vědět, kdy je jedna nebo druhá pro úkol vhodnější.
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
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174416"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="d3b2f-103">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="d3b2f-103">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="d3b2f-104"><xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> Ovládací prvky a mají podobné chování a v některých případech mohou být zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-104">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="d3b2f-105">Existují však situace, kdy je jedna nebo druhá pro úkol vhodnější.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-105">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="d3b2f-106">Obecně je pole se seznamem vhodné, pokud existuje seznam navrhovaných možností a seznam je vhodný, když chcete omezit vstup na to, co je v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-106">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="d3b2f-107">Pole se seznamem obsahuje pole textového pole, takže výběry, které nejsou na seznamu, lze zadat v.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-107">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="d3b2f-108">Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je vlastnost nastavena na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> .</span><span class="sxs-lookup"><span data-stu-id="d3b2f-108">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="d3b2f-109">V takovém případě ovládací prvek vybere položku, pokud zadáte její první písmeno.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-109">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="d3b2f-110">Kromě toho pole se seznamem šetří místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-110">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="d3b2f-111">Vzhledem k tomu, že se úplný seznam nezobrazí, dokud uživatel neklikne na šipku dolů, pole se seznamem se dá snadno přizpůsobit na malé místo, kde se seznam nevejde.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-111">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="d3b2f-112">Výjimkou je, že pokud <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je vlastnost nastavena na hodnotu <xref:System.Windows.Forms.ComboBoxStyle.Simple> : zobrazí se úplný seznam a pole se seznamem bude trvat více místa, než je pole seznamu.</span><span class="sxs-lookup"><span data-stu-id="d3b2f-112">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b2f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3b2f-113">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="d3b2f-114">Postupy: Přidání a odebrání položek z ovládacích prvků ComboBox, ListBox nebo CheckedListBox z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3b2f-114">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="d3b2f-115">Postupy: Řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="d3b2f-115">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="d3b2f-116">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="d3b2f-116">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
