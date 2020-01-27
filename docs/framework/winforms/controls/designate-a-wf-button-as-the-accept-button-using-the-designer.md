---
title: Označení tlačítka jako tlačítka přijmout pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27a5de51f8c5b2c84cc205e09ac1a2179c315752
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746061"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="d82a3-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d82a3-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="d82a3-103">V jakémkoli formuláři Windows můžete určit <xref:System.Windows.Forms.Button> ovládací prvek jako tlačítko přijmout, označované také jako výchozí tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d82a3-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="d82a3-104">Pokaždé, když uživatel stiskne klávesu ENTER, klikne na tlačítko výchozí, a to bez ohledu na to, který jiný ovládací prvek ve formuláři má fokus.</span><span class="sxs-lookup"><span data-stu-id="d82a3-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="d82a3-105">Výjimkou je, když je ovládací prvek s fokusem jiný tlačítko – v takovém případě se na tlačítko s fokusem klikne – nebo na víceřádkové textové pole nebo na vlastní ovládací prvek, který zachytávání klíče ENTER.</span><span class="sxs-lookup"><span data-stu-id="d82a3-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>

## <a name="to-designate-the-accept-button"></a><span data-ttu-id="d82a3-106">Označení tlačítka přijmout</span><span class="sxs-lookup"><span data-stu-id="d82a3-106">To designate the accept button</span></span>

1. <span data-ttu-id="d82a3-107">Vyberte formulář, na kterém se nachází tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d82a3-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="d82a3-108">V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.Form.AcceptButton%2A> formuláře na název ovládacího prvku <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="d82a3-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="d82a3-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d82a3-109">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="d82a3-110">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="d82a3-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="d82a3-111">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="d82a3-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="d82a3-112">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d82a3-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="d82a3-113">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d82a3-113">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [<span data-ttu-id="d82a3-114">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="d82a3-114">Button Control</span></span>](button-control-windows-forms.md)
