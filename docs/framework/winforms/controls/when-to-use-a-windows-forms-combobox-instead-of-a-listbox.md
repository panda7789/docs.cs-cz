---
title: Kdy použít prvek Windows Forms ComboBox místo prvku ListBox
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
ms.openlocfilehash: 5dc7778f43c01fd28a14489a7b4179dd851568b2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702994"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="efde2-102">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="efde2-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="efde2-103"><xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> ovládací prvky mají podobné chování a v některých případech může být zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="efde2-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="efde2-104">Existují však situace, kdy je vhodnější k úkolu jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="efde2-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="efde2-105">Obecně platí je příslušné pole se seznamem, pokud je seznam navrhovaných volby a seznamu je vhodné, pokud chcete omezit vstup na to, co je v seznamu.</span><span class="sxs-lookup"><span data-stu-id="efde2-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="efde2-106">Pole se seznamem obsahuje textové pole, takže lze napsat volby není v seznamu.</span><span class="sxs-lookup"><span data-stu-id="efde2-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="efde2-107">Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="efde2-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="efde2-108">V takovém případě bude ovládací prvek vyberte položku, pokud zadáte své první písmeno.</span><span class="sxs-lookup"><span data-stu-id="efde2-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="efde2-109">Kromě toho pole se seznamem ušetřit místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="efde2-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="efde2-110">Protože úplný seznam se nezobrazí, dokud uživatel klepne na šipku dolů, pole se seznamem snadno vejde do omezeného místa, kde nevejde pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="efde2-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="efde2-111">Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: Zobrazí úplný seznam a pole se seznamem zabírá více místa, než by bylo pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="efde2-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efde2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efde2-112">See also</span></span>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="efde2-113">Postupy: Přidání a odebrání položek z Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="efde2-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="efde2-114">Postupy: Řazení obsahu Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="efde2-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="efde2-115">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="efde2-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
