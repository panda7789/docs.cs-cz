---
title: "Kdy použít prvek Windows Forms ComboBox místo prvku ListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b4eb1ce70b1ec4b249eb126b608c9f8578d327c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="d6c90-102">Kdy použít prvek Windows Forms ComboBox místo prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="d6c90-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="d6c90-103"><xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ListBox> ovládacích prvků mají podobné chování a v některých případech může být zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="d6c90-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="d6c90-104">Existují dobu, ale pokud jeden z nich je vhodnější pro úlohu.</span><span class="sxs-lookup"><span data-stu-id="d6c90-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="d6c90-105">Obecně platí pole se seznamem je vhodné, pokud je seznam navrhovaných volby a pole se seznamem je vhodné, pokud chcete omezit vstup na to, co je v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d6c90-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="d6c90-106">Pole se seznamem obsahuje textové pole pole, proto lze napsat volby nejsou na seznamu.</span><span class="sxs-lookup"><span data-stu-id="d6c90-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="d6c90-107">Jedinou výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="d6c90-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="d6c90-108">V takovém případě bude ovládací prvek vyberte položku, pokud zadáte svůj první písmeno.</span><span class="sxs-lookup"><span data-stu-id="d6c90-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="d6c90-109">Kromě toho se seznamem ušetřit místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="d6c90-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="d6c90-110">Protože úplný seznam se nezobrazí, dokud uživatel kliknutím na šipku dolů, můžete snadno začlenit pole se seznamem v malé místo, kde by vyhovovaly pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="d6c90-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="d6c90-111">Výjimkou je, když <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> je nastavena na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: se zobrazuje úplný seznam a pole se seznamem zabírá více místa, než by bylo pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="d6c90-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c90-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6c90-112">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="d6c90-113">Postupy: Přidání a odebrání položek z Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d6c90-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="d6c90-114">Postupy: řazení obsahu ovládacího prvku Windows Forms ComboBox, ListBox nebo CheckedListBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d6c90-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="d6c90-115">Windows Forms – ovládací prvky používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="d6c90-115">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
