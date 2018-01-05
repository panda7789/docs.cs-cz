---
title: "Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e72b2516efab3bc5b5d8cc7cacb66f149f3a66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="4b55e-102">Postupy: Definování ikony pro tlačítko ToolBar pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="4b55e-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="4b55e-103"><xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="4b55e-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="4b55e-104"><xref:System.Windows.Forms.ToolBar>tlačítka jsou moci zobrazit ikony v nich pro snazší identifikaci uživatelů.</span><span class="sxs-lookup"><span data-stu-id="4b55e-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="4b55e-105">Toho je dosaženo pomocí přidávání obrázků na <xref:System.Windows.Forms.ImageList> součástí a její přidružení <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4b55e-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="4b55e-106">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ToolBar> řízení a <xref:System.Windows.Forms.ImageList> součásti.</span><span class="sxs-lookup"><span data-stu-id="4b55e-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="4b55e-107">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4b55e-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b55e-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="4b55e-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4b55e-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="4b55e-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4b55e-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4b55e-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="4b55e-111">Chcete-li nastavit ikonu pro tlačítka panelu nástrojů v době návrhu</span><span class="sxs-lookup"><span data-stu-id="4b55e-111">To set an icon for a toolbar button at design time</span></span>  
  
1.  <span data-ttu-id="4b55e-112">Přidat Image do <xref:System.Windows.Forms.ImageList> součásti.</span><span class="sxs-lookup"><span data-stu-id="4b55e-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="4b55e-113">Další informace najdete v tématu [postupy: Přidání nebo odebrání obrázků ImageList pomocí návrháře](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4b55e-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="4b55e-114">Vyberte <xref:System.Windows.Forms.ToolBar> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="4b55e-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3.  <span data-ttu-id="4b55e-115">V **vlastnosti** nastavte <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.ImageList%2A> vlastnost, která má <xref:System.Windows.Forms.ImageList> součásti.</span><span class="sxs-lookup"><span data-stu-id="4b55e-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="4b55e-116">Klikněte <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost vyberte ho a klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="4b55e-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="4b55e-117">Použití **přidat** tlačítko pro přidání tlačítek <xref:System.Windows.Forms.ToolBar> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4b55e-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6.  <span data-ttu-id="4b55e-118">V **vlastnosti** okno, které se zobrazí v podokně na pravé straně **Editor kolekce ToolBarButton**, nastavte <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> vlastnost tlačítko panelu nástrojů na jednu z hodnot v seznamu, který výběr pochází z Image přidat do <xref:System.Windows.Forms.ImageList> součásti.</span><span class="sxs-lookup"><span data-stu-id="4b55e-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b55e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b55e-119">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="4b55e-120">Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="4b55e-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="4b55e-121">Ovládací prvek ToolBar</span><span class="sxs-lookup"><span data-stu-id="4b55e-121">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="4b55e-122">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="4b55e-122">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
