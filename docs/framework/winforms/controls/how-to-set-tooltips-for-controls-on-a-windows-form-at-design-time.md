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
ms.openlocfilehash: cc8f8c620516a943d6d70187e19b72f5a2a99888
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013072"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="7af67-102">Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu</span><span class="sxs-lookup"><span data-stu-id="7af67-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="7af67-103">Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="7af67-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="7af67-104">Další informace o <xref:System.Windows.Forms.ToolTip> komponenty, naleznete v tématu [ToolTip – přehled komponenty](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7af67-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7af67-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7af67-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7af67-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7af67-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7af67-107">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7af67-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="7af67-108">Chcete-li nastavit popisek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="7af67-108">To set a ToolTip programmatically</span></span>  
  
1. <span data-ttu-id="7af67-109">Přidejte ovládací prvek, který se zobrazí popisek.</span><span class="sxs-lookup"><span data-stu-id="7af67-109">Add the control that will display the ToolTip.</span></span>  
  
2. <span data-ttu-id="7af67-110">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7af67-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="7af67-111">Chcete-li nastavit popisek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="7af67-111">To set a ToolTip in the designer</span></span>  
  
1. <span data-ttu-id="7af67-112">Přidat <xref:System.Windows.Forms.ToolTip> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="7af67-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2. <span data-ttu-id="7af67-113">Vyberte ovládací prvek, který zobrazí popis tlačítka, nebo ho přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="7af67-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3. <span data-ttu-id="7af67-114">V **vlastnosti** okno, nastaveno **popisu tlačítka ToolTip1** hodnota, která má odpovídající řetězec textu.</span><span class="sxs-lookup"><span data-stu-id="7af67-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="7af67-115">Chcete-li odebrat popisek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="7af67-115">To remove a ToolTip programmatically</span></span>  
  
1. <span data-ttu-id="7af67-116">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7af67-116">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-remove-a-tooltip-in-the-designer"></a><span data-ttu-id="7af67-117">Chcete-li odebrat popisek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="7af67-117">To remove a ToolTip in the designer</span></span>  
  
1. <span data-ttu-id="7af67-118">Vyberte ovládací prvek, který se zobrazuje v popisku.</span><span class="sxs-lookup"><span data-stu-id="7af67-118">Select the control that is displaying the ToolTip.</span></span>  
  
2. <span data-ttu-id="7af67-119">V **vlastnosti** okna, odstraníte tím stávající text v **popisu tlačítka ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="7af67-119">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="7af67-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7af67-120">See also</span></span>

- [<span data-ttu-id="7af67-121">Přehled komponenty ToolTip</span><span class="sxs-lookup"><span data-stu-id="7af67-121">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="7af67-122">Postupy: Změna zpoždění komponenty Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="7af67-122">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="7af67-123">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="7af67-123">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
