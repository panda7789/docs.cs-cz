---
title: 'Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 4e4623c1c0fe7d082e4d1a1f404ddaa94e79fc2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533627"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="0347d-102">Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu</span><span class="sxs-lookup"><span data-stu-id="0347d-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="0347d-103">Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="0347d-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="0347d-104">Další informace o <xref:System.Windows.Forms.ToolTip> součást, najdete v části [ToolTip – přehled komponenty](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0347d-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0347d-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="0347d-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0347d-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="0347d-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0347d-107">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="0347d-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="0347d-108">Chcete-li nastavit popisek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="0347d-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="0347d-109">Přidání ovládacího prvku, který se zobrazí popisek.</span><span class="sxs-lookup"><span data-stu-id="0347d-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="0347d-110">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> součásti.</span><span class="sxs-lookup"><span data-stu-id="0347d-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="0347d-111">Chcete-li nastavit popisek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="0347d-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="0347d-112">Přidat <xref:System.Windows.Forms.ToolTip> součásti pro formulář.</span><span class="sxs-lookup"><span data-stu-id="0347d-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="0347d-113">Vyberte ovládací prvek, který se zobrazí popisek nebo ho přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="0347d-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="0347d-114">V **vlastnosti** nastavte **popis tlačítka na ToolTip1** hodnotu na odpovídající řetězec textu.</span><span class="sxs-lookup"><span data-stu-id="0347d-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0347d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0347d-115">See Also</span></span>  
 [<span data-ttu-id="0347d-116">Přehled komponenty ToolTip</span><span class="sxs-lookup"><span data-stu-id="0347d-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="0347d-117">Postupy: Změna zpoždění komponenty Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="0347d-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="0347d-118">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="0347d-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
