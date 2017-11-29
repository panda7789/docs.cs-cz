---
title: "Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81716be53468242734c3d722eb21e020e58f65ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="5a983-102">Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu</span><span class="sxs-lookup"><span data-stu-id="5a983-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="5a983-103">Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="5a983-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="5a983-104">Další informace o <xref:System.Windows.Forms.ToolTip> součást, najdete v části [ToolTip – přehled komponenty](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5a983-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a983-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="5a983-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5a983-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="5a983-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5a983-107">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5a983-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="5a983-108">Chcete-li nastavit popisek prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5a983-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="5a983-109">Přidání ovládacího prvku, který se zobrazí popisek.</span><span class="sxs-lookup"><span data-stu-id="5a983-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="5a983-110">Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> součásti.</span><span class="sxs-lookup"><span data-stu-id="5a983-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="5a983-111">Chcete-li nastavit popisek v Návrháři</span><span class="sxs-lookup"><span data-stu-id="5a983-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="5a983-112">Přidat <xref:System.Windows.Forms.ToolTip> součásti pro formulář.</span><span class="sxs-lookup"><span data-stu-id="5a983-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="5a983-113">Vyberte ovládací prvek, který se zobrazí popisek nebo ho přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="5a983-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="5a983-114">V **vlastnosti** nastavte **popis tlačítka na ToolTip1** hodnotu na odpovídající řetězec textu.</span><span class="sxs-lookup"><span data-stu-id="5a983-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a983-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a983-115">See Also</span></span>  
 [<span data-ttu-id="5a983-116">ToolTip – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="5a983-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="5a983-117">Postupy: Změna zpoždění součásti Windows Forms ToolTip</span><span class="sxs-lookup"><span data-stu-id="5a983-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="5a983-118">ToolTip – komponenta</span><span class="sxs-lookup"><span data-stu-id="5a983-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
