---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: e94553a31ecdbf325c12815aa7a782cb68b95f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526136"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="ca875-102">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="ca875-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="ca875-103">Na všechny formuláře Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Zrušit.</span><span class="sxs-lookup"><span data-stu-id="ca875-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="ca875-104">Vždy, když uživatel stisknutím klávesy ESC, bez ohledu na to, které další ovládací prvek na formuláři fokus, po kliknutí na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="ca875-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="ca875-105">Toto tlačítko je obvykle naprogramovaný tak, aby uživatelům umožnit rychle operaci ukončit bez potvrzení na každou akci.</span><span class="sxs-lookup"><span data-stu-id="ca875-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca875-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ca875-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ca875-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ca875-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ca875-108">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ca875-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="ca875-109">Chcete-li určit tlačítko Zrušit</span><span class="sxs-lookup"><span data-stu-id="ca875-109">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="ca875-110">Vyberte formuláře, na kterém se nachází na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ca875-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="ca875-111">V **vlastnosti** nastavte formuláře <xref:System.Windows.Forms.Form.CancelButton%2A> vlastnost, která má <xref:System.Windows.Forms.Button> název ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ca875-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca875-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca875-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="ca875-113">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="ca875-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="ca875-114">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="ca875-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="ca875-115">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca875-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="ca875-116">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="ca875-116">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="ca875-117">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="ca875-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
