---
title: 'Postupy: Vytvoření pole jen pro čtení textu (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 0a29e1c4dcb0bcc8e7d292725e64ea967e160d06
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707752"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="e283b-102">Postupy: Vytvoření pole jen pro čtení textu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e283b-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="e283b-103">Upravitelné textové pole formulářů Windows můžete transformovat na ovládací prvek jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e283b-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="e283b-104">Do textového pole mohou například zobrazit hodnotu, která je obvykle upraven, ale nemusí být v současné době kvůli stavu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e283b-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="e283b-105">K vytvoření pole jen pro čtení textu</span><span class="sxs-lookup"><span data-stu-id="e283b-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="e283b-106">Nastavte <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="e283b-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="e283b-107">Vlastnost nastavena na `true`, uživatelé stále můžete posunout a zvýrazňování textu v textovém poli bez povolení změn.</span><span class="sxs-lookup"><span data-stu-id="e283b-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="e283b-108">A **kopírování** příkaz je funkční v textovém poli, ale **Vyjmout** a **vložit** nejsou příkazy.</span><span class="sxs-lookup"><span data-stu-id="e283b-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e283b-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Vlastnost ovlivňuje pouze interakci s uživatelem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e283b-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="e283b-110">Můžete stále změnit obsahu textového pole prostřednictvím kódu programu za běhu pomocí změny <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti textového pole.</span><span class="sxs-lookup"><span data-stu-id="e283b-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e283b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e283b-111">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="e283b-112">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="e283b-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e283b-113">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="e283b-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="e283b-114">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="e283b-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e283b-115">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="e283b-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="e283b-116">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="e283b-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e283b-117">Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="e283b-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e283b-118">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="e283b-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
