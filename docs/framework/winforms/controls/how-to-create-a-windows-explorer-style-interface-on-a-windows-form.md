---
title: 'Postupy: Vytváření rozhraní ve stylu Průzkumníku Windows ve formuláři Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 2d5b79244d867ea4b6134413d42710b2eadc871e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532383"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="c5f5a-102">Postupy: Vytváření rozhraní ve stylu Průzkumníku Windows ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="c5f5a-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="c5f5a-103">Průzkumník Windows je běžné volbou uživatelského rozhraní pro aplikace z důvodu jeho připravené znalosti.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="c5f5a-104">Průzkumník Windows je v podstatě <xref:System.Windows.Forms.TreeView> řízení a <xref:System.Windows.Forms.ListView> ovládací prvek v samostatných panelů.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="c5f5a-105">Panely jsou vytvářeny podle rozdělovač umožňující změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="c5f5a-106">Uspořádání ovládacích prvků je velmi efektivní pro zobrazení a procházení informace.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="c5f5a-107">Následující kroky ukazují, jak k uspořádání ovládacích prvků ve formuláři stylu Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="c5f5a-108">Nezobrazovat jak přidat funkce procházení souborů aplikace Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5f5a-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c5f5a-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c5f5a-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c5f5a-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="c5f5a-112">K vytvoření formuláře Windows stylu Průzkumníku Windows</span><span class="sxs-lookup"><span data-stu-id="c5f5a-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1.  <span data-ttu-id="c5f5a-113">Vytvořte nový projekt aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-113">Create a new Windows Application project.</span></span> <span data-ttu-id="c5f5a-114">Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="c5f5a-114">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="c5f5a-115">Z **sada nástrojů**:</span><span class="sxs-lookup"><span data-stu-id="c5f5a-115">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="c5f5a-116">Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-116">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="c5f5a-117">Přetáhněte <xref:System.Windows.Forms.TreeView> řízení do **SplitterPanel1** (na panelu <xref:System.Windows.Forms.SplitContainer> řízení označena **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="c5f5a-117">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="c5f5a-118">Přetáhněte <xref:System.Windows.Forms.ListView> řízení do **SplitterPanel2** (na panelu <xref:System.Windows.Forms.SplitContainer> řízení označena **Panel2**).</span><span class="sxs-lookup"><span data-stu-id="c5f5a-118">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3.  <span data-ttu-id="c5f5a-119">Všechny tři ovládací prvky pro výběr stisknete klávesu CTRL a kliknutím na je naopak.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-119">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="c5f5a-120">Když vyberete <xref:System.Windows.Forms.SplitContainer> řídit, klikněte na tento panel, nikoli panely.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-120">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c5f5a-121">Nepoužívejte **Vybrat vše** příkaz na **upravit** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-121">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="c5f5a-122">Pokud tak učiníte, vlastnost potřeba v dalším kroku se nebude zobrazovat na **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-122">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="c5f5a-123">V **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-123">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="c5f5a-124">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-124">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="c5f5a-125">Formulář zobrazí dvě části uživatelské rozhraní, podobně jako u Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-125">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c5f5a-126">Při přetažení rozdělovače změnit velikost panely sami.</span><span class="sxs-lookup"><span data-stu-id="c5f5a-126">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f5a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5f5a-127">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="c5f5a-128">Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5f5a-128">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [<span data-ttu-id="c5f5a-129">Postupy: Definování chování změny velikosti a polohování v rozděleném okně</span><span class="sxs-lookup"><span data-stu-id="c5f5a-129">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [<span data-ttu-id="c5f5a-130">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="c5f5a-130">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [<span data-ttu-id="c5f5a-131">Ovládací prvek SplitContainer</span><span class="sxs-lookup"><span data-stu-id="c5f5a-131">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
