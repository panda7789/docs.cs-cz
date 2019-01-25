---
title: 'Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: ebefe596728b5cabd9d24720d8c39f13c8836bd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609405"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="f6ff0-102">Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="f6ff0-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="f6ff0-103">Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="f6ff0-104">Další informace o <xref:System.Windows.Forms.ToolTip> komponenty, naleznete v tématu [ToolTip – přehled komponenty](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f6ff0-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6ff0-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f6ff0-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f6ff0-107">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f6ff0-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="f6ff0-108">Chcete-li nastavit popisek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="f6ff0-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="f6ff0-109">Přidejte ovládací prvek, který se zobrazí popisek.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="f6ff0-110">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="f6ff0-111">Chcete-li nastavit popisek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="f6ff0-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="f6ff0-112">Přidat <xref:System.Windows.Forms.ToolTip> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="f6ff0-113">Vyberte ovládací prvek, který zobrazí popis tlačítka, nebo ho přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="f6ff0-114">V **vlastnosti** okno, nastaveno **popisu tlačítka ToolTip1** hodnota, která má odpovídající řetězec textu.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="f6ff0-115">Chcete-li odebrat popisek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="f6ff0-115">To remove a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="f6ff0-116">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-116">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a><span data-ttu-id="f6ff0-117">Chcete-li odebrat popisek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="f6ff0-117">To remove a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="f6ff0-118">Vyberte ovládací prvek, který se zobrazuje v popisku.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-118">Select the control that is displaying the ToolTip.</span></span>  
  
2.  <span data-ttu-id="f6ff0-119">V **vlastnosti** okna, odstraníte tím stávající text v **popisu tlačítka ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-119">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f6ff0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6ff0-120">See also</span></span>
- [<span data-ttu-id="f6ff0-121">Přehled komponenty ToolTip</span><span class="sxs-lookup"><span data-stu-id="f6ff0-121">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="f6ff0-122">Postupy: Změna zpoždění komponenty Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="f6ff0-122">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="f6ff0-123">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="f6ff0-123">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
