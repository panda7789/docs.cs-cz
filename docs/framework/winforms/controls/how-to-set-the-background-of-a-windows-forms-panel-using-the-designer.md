---
title: "Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 451fa6433a53255f5fe45557c2d8b03ac319de71
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="cd3b7-102">Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="cd3b7-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="cd3b7-103">Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek může zobrazit barvu pozadí a obrázek na pozadí.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="cd3b7-104"><xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro ovládací prvky, které jsou obsaženy v panelu, jako je například popisky a přepínač tlačítka.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="cd3b7-105">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> není vlastnost nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> výběr naplní všechny panelu.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="cd3b7-106">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost nastavena, zobrazí se obrázek za ovládacích prvků, které jsou obsaženy v panelu.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="cd3b7-107">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře, který obsahuje <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="cd3b7-108">Informace o tom, jak nastavit tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cd3b7-108">For information about how to set up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd3b7-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cd3b7-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cd3b7-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cd3b7-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="cd3b7-112">Chcete-li nastavit na pozadí v Návrháři formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="cd3b7-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="cd3b7-113">Vyberte <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="cd3b7-114">V **vlastnosti** klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost zobrazit okno s tři karty.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="cd3b7-115">Vyberte **vlastní** zobrazíte paletu barev.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="cd3b7-116">Vyberte **webové** nebo **systému** můžete zobrazit seznam předdefinovaných názvů pro barvy a pak vyberte barvu.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="cd3b7-117">V **vlastnosti** klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="cd3b7-118">V **otevřete** dialogové okno, vyberte soubor, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="cd3b7-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3b7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd3b7-119">See Also</span></span>  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [<span data-ttu-id="cd3b7-120">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="cd3b7-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="cd3b7-121">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="cd3b7-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="cd3b7-122">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="cd3b7-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
