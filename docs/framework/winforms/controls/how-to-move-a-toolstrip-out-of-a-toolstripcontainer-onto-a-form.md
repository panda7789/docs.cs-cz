---
title: 'Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 100e744e6e49fbf214488e9bbb796b5b6fb9591a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142360"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="2c3bf-102">Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři</span><span class="sxs-lookup"><span data-stu-id="2c3bf-102">How to: Move a ToolStrip Out of a ToolStripContainer onto a Form</span></span>
<span data-ttu-id="2c3bf-103">Pomocí následujícího postupu pro přesun <xref:System.Windows.Forms.ToolStrip> z celkového počtu <xref:System.Windows.Forms.ToolStripContainer> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-103">Use the following procedure to move a <xref:System.Windows.Forms.ToolStrip> out of a <xref:System.Windows.Forms.ToolStripContainer> onto a form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c3bf-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2c3bf-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2c3bf-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2c3bf-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a><span data-ttu-id="2c3bf-107">Přesunutí ToolStrip mimo prvek ToolStripContainer formuláře</span><span class="sxs-lookup"><span data-stu-id="2c3bf-107">To move a ToolStrip out of a ToolStripContainer onto a form</span></span>  
  
1.  <span data-ttu-id="2c3bf-108">Vyberte <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-108">Select the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
2.  <span data-ttu-id="2c3bf-109">Vyjmout <xref:System.Windows.Forms.ToolStrip> pomocí klávesy CTRL + X nebo kliknutím pravým tlačítkem <xref:System.Windows.Forms.ToolStrip> a zvolte **Vyjmout** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-109">Cut the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+X, or right-click the <xref:System.Windows.Forms.ToolStrip> and choose **Cut** from the context menu.</span></span>  
  
3.  <span data-ttu-id="2c3bf-110">Vyberte formulář.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-110">Select the form.</span></span>  
  
4.  <span data-ttu-id="2c3bf-111">Vložit <xref:System.Windows.Forms.ToolStrip> pomocí kláves CTRL + V, nebo zvolte **vložit** z **upravit** nabídky.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-111">Paste the <xref:System.Windows.Forms.ToolStrip> by pressing CTRL+V, or choose **Paste** from the **Edit** menu.</span></span>  
  
5.  <span data-ttu-id="2c3bf-112">Nastavte <xref:System.Windows.Forms.ToolStrip.Dock%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k **horní**.</span><span class="sxs-lookup"><span data-stu-id="2c3bf-112">Set the <xref:System.Windows.Forms.ToolStrip.Dock%2A> property of the <xref:System.Windows.Forms.ToolStrip> to **Top**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3bf-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c3bf-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="2c3bf-114">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2c3bf-114">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
