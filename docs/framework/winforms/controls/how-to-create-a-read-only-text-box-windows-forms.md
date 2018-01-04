---
title: "Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 264ef1a7c1f121f889d57dcb0e36e216610418fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="844a8-102">Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="844a8-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="844a8-103">Textového pole na upravitelné Windows Forms můžete převést do ovládacího prvku jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="844a8-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="844a8-104">Textové pole může například zobrazí hodnotu, která je obvykle upravovat, ale nemusí být v současné době z důvodu stavu aplikace.</span><span class="sxs-lookup"><span data-stu-id="844a8-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="844a8-105">Chcete-li vytvořit jen pro čtení textového pole</span><span class="sxs-lookup"><span data-stu-id="844a8-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="844a8-106">Nastavte <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="844a8-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="844a8-107">S vlastností nastavenou na `true`, uživatelé stále přejděte a zvýrazňování textu v textovém poli beze změny.</span><span class="sxs-lookup"><span data-stu-id="844a8-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="844a8-108">A **kopie** příkaz je funkční v textovém poli, ale **Vyjmout** a **vložení** nejsou příkazy.</span><span class="sxs-lookup"><span data-stu-id="844a8-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="844a8-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Vlastnost ovlivňuje pouze interakci s uživatelem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="844a8-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="844a8-110">Můžete je stále změnit obsahu textového pole prostřednictvím kódu programu v době běhu změnou <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti textového pole.</span><span class="sxs-lookup"><span data-stu-id="844a8-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844a8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="844a8-111">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="844a8-112">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="844a8-112">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="844a8-113">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="844a8-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="844a8-114">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="844a8-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="844a8-115">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="844a8-115">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="844a8-116">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="844a8-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="844a8-117">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="844a8-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="844a8-118">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="844a8-118">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
