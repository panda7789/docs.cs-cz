---
title: Označení tlačítka pro tlačítko Storno pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746049"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="0ba5b-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="0ba5b-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="0ba5b-103">V jakémkoli formuláři Windows můžete určit <xref:System.Windows.Forms.Button> ovládací prvek pro tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="0ba5b-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="0ba5b-104">Kliknutím na tlačítko Storno dojde vždy, když uživatel stiskne klávesu ESC bez ohledu na to, který jiný ovládací prvek ve formuláři má fokus.</span><span class="sxs-lookup"><span data-stu-id="0ba5b-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="0ba5b-105">Toto tlačítko je obvykle naprogramováno, aby uživatel mohl rychle ukončit operaci bez nutnosti potvrzení akce.</span><span class="sxs-lookup"><span data-stu-id="0ba5b-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="0ba5b-106">Chcete-li určit tlačítko Storno</span><span class="sxs-lookup"><span data-stu-id="0ba5b-106">To designate the cancel button</span></span>

1. <span data-ttu-id="0ba5b-107">Vyberte formulář, na kterém se nachází tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0ba5b-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="0ba5b-108">V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.Form.CancelButton%2A> formuláře na název ovládacího prvku <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="0ba5b-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ba5b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ba5b-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="0ba5b-110">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="0ba5b-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="0ba5b-111">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="0ba5b-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="0ba5b-112">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0ba5b-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="0ba5b-113">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="0ba5b-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="0ba5b-114">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="0ba5b-114">Button Control</span></span>](button-control-windows-forms.md)
