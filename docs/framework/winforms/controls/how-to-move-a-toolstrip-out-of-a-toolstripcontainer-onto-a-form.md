---
title: "Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daa372397a3c85ef8359261c4816fbba664928bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="c7f3a-102">Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři</span><span class="sxs-lookup"><span data-stu-id="c7f3a-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="c7f3a-103">Pomocí následujícího postupu přesunutí <xref:System.Windows.Forms.ToolStrip> mimo <xref:System.Windows.Forms.ToolStripContainer> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7f3a-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c7f3a-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c7f3a-106">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c7f3a-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="c7f3a-107">Přesunutí ToolStrip mimo prvek ToolStripContainer formuláře</span><span class="sxs-lookup"><span data-stu-id="c7f3a-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="c7f3a-108">Vyberte <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="c7f3a-109">Vyjmout <xref:System.Windows.Forms.ToolStrip> pomocí klávesy CTRL + X, nebo klikněte pravým tlačítkem <xref:System.Windows.Forms.ToolStrip> a zvolte **Vyjmout** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="c7f3a-110">Vyberte formuláře.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="c7f3a-111">Vložení <xref:System.Windows.Forms.ToolStrip> pomocí kláves CTRL + V, nebo zvolte **vložení** z **upravit** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="c7f3a-112">Nastavte <xref:System.Windows.Forms.ToolStrip.Dock%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k **horní**.</span><span class="sxs-lookup"><span data-stu-id="c7f3a-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f3a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7f3a-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="c7f3a-114">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c7f3a-114">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
