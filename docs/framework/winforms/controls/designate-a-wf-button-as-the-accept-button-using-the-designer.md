---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: ca049e86ab53fbd84cb24e81b0a850050ec2823f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507781"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="01150-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="01150-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="01150-103">Na formuláři Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Přijmout, označované také jako výchozího tlačítka.</span><span class="sxs-lookup"><span data-stu-id="01150-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="01150-104">Pokaždé, když uživatel stiskne klávesu ENTER, výchozí je stisknuto tlačítko bez ohledu na to, který má jiný ovládací prvek ve formuláři fokus.</span><span class="sxs-lookup"><span data-stu-id="01150-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="01150-105">Výjimky jsou při ovládací prvek fokus je jiný tlačítko – v takovém případě bude kliknutí na tlačítko s fokusem – nebo víceřádkovém textovém poli, nebo vlastní ovládací prvek, který zachycuje klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="01150-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01150-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="01150-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="01150-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="01150-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="01150-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="01150-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="01150-109">Chcete-li určit tlačítka přijmout</span><span class="sxs-lookup"><span data-stu-id="01150-109">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="01150-110">Vyberte formulář, na kterém je umístěn tlačítku.</span><span class="sxs-lookup"><span data-stu-id="01150-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="01150-111">V **vlastnosti** okno, nastavte formuláře <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnost <xref:System.Windows.Forms.Button> název ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="01150-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01150-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="01150-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="01150-113">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="01150-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="01150-114">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="01150-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="01150-115">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01150-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="01150-116">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="01150-116">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="01150-117">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="01150-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
