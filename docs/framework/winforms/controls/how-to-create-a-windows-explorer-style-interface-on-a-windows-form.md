---
title: 'Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 578fdf8e24803db0e0d80ff22aa5cebebbc2663e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615999"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="0bee0-102">Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0bee0-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="0bee0-103">Windows Explorer je běžné volbou uživatelského rozhraní pro aplikace z důvodu jeho známý připravený.</span><span class="sxs-lookup"><span data-stu-id="0bee0-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="0bee0-104">Průzkumník Windows je v podstatě <xref:System.Windows.Forms.TreeView> ovládacího prvku a <xref:System.Windows.Forms.ListView> ovládací prvek na samostatné panelů.</span><span class="sxs-lookup"><span data-stu-id="0bee0-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="0bee0-105">Panely vyrábí celá rozdělovač umožňující změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="0bee0-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="0bee0-106">Uspořádání ovládacích prvků je velice efektivní pro zobrazení informací o procházení.</span><span class="sxs-lookup"><span data-stu-id="0bee0-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="0bee0-107">Následující kroky ukazují, jak k uspořádání ovládacích prvků ve Windows Explorer podobě.</span><span class="sxs-lookup"><span data-stu-id="0bee0-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="0bee0-108">Nezobrazovat přidání funkce procházení souborů v aplikaci Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="0bee0-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bee0-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="0bee0-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0bee0-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="0bee0-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0bee0-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0bee0-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="0bee0-112">Vytvoření formuláře Windows stylem podobným Průzkumníku Windows</span><span class="sxs-lookup"><span data-stu-id="0bee0-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1. <span data-ttu-id="0bee0-113">Vytvoření nového projektu aplikace Windows (**souboru** > **nový** > **projektu** > **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="0bee0-113">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="0bee0-114">Z **nástrojů**:</span><span class="sxs-lookup"><span data-stu-id="0bee0-114">From the **Toolbox**:</span></span>  
  
    1. <span data-ttu-id="0bee0-115">Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku na formulář.</span><span class="sxs-lookup"><span data-stu-id="0bee0-115">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2. <span data-ttu-id="0bee0-116">Přetáhněte <xref:System.Windows.Forms.TreeView> ovládací prvek do **SplitterPanel1** (panelu <xref:System.Windows.Forms.SplitContainer> označený ovládací prvek **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="0bee0-116">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3. <span data-ttu-id="0bee0-117">Přetáhněte <xref:System.Windows.Forms.ListView> ovládací prvek do **SplitterPanel2** (panelu <xref:System.Windows.Forms.SplitContainer> označený ovládací prvek **ovládací prvek Panel2**).</span><span class="sxs-lookup"><span data-stu-id="0bee0-117">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3. <span data-ttu-id="0bee0-118">Vyberte klávesy CTRL a kliknutím zase na všechny tři ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="0bee0-118">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="0bee0-119">Když vyberete <xref:System.Windows.Forms.SplitContainer> řídit, klikněte na tlačítko rozdělovač, nikoli panelů.</span><span class="sxs-lookup"><span data-stu-id="0bee0-119">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bee0-120">Nepoužívejte **Vybrat vše** příkaz **upravit** nabídky.</span><span class="sxs-lookup"><span data-stu-id="0bee0-120">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="0bee0-121">Pokud tak učiníte, vlastnost, je potřeba v dalším kroku nebude zobrazovat **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="0bee0-121">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="0bee0-122">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="0bee0-122">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5. <span data-ttu-id="0bee0-123">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0bee0-123">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="0bee0-124">Formulář zobrazí dvě části uživatelského rozhraní, podobně jako u v Průzkumníku Windows.</span><span class="sxs-lookup"><span data-stu-id="0bee0-124">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0bee0-125">Při přetažení příčky změnit velikost panelů sami.</span><span class="sxs-lookup"><span data-stu-id="0bee0-125">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bee0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bee0-126">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="0bee0-127">Postupy: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0bee0-127">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="0bee0-128">Postupy: Definování změny velikosti a polohování v rozděleném okně chování</span><span class="sxs-lookup"><span data-stu-id="0bee0-128">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="0bee0-129">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="0bee0-129">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="0bee0-130">Ovládací prvek SplitContainer</span><span class="sxs-lookup"><span data-stu-id="0bee0-130">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
