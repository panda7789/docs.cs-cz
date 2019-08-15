---
title: 'Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: db2c5431dfb0156c1508a18ef13d2af80eb4981b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039537"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="ab6db-102">Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab6db-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="ab6db-103">Průzkumník Windows je běžná volba uživatelského rozhraní pro aplikace z důvodu své připravenosti.</span><span class="sxs-lookup"><span data-stu-id="ab6db-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>

 <span data-ttu-id="ab6db-104">Průzkumník Windows je v podstatě <xref:System.Windows.Forms.TreeView> ovládací prvek <xref:System.Windows.Forms.ListView> a ovládací prvek na samostatných panelech.</span><span class="sxs-lookup"><span data-stu-id="ab6db-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="ab6db-105">Panely mají změnu velikosti příčkou.</span><span class="sxs-lookup"><span data-stu-id="ab6db-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="ab6db-106">Toto uspořádání ovládacích prvků je velmi efektivní pro zobrazení a informace o procházení.</span><span class="sxs-lookup"><span data-stu-id="ab6db-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>

 <span data-ttu-id="ab6db-107">Následující kroky ukazují, jak uspořádat ovládací prvky ve formuláři podobném prohlížeči Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="ab6db-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="ab6db-108">Neukazují, jak přidat funkce pro procházení souborů v aplikaci Průzkumník Windows.</span><span class="sxs-lookup"><span data-stu-id="ab6db-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>

## <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="ab6db-109">Vytvoření formuláře Windows ve stylu Průzkumníka Windows</span><span class="sxs-lookup"><span data-stu-id="ab6db-109">To create a Windows Explorer-style Windows Form</span></span>

1. <span data-ttu-id="ab6db-110">Vytvoření nového projektu aplikace pro Windows (**soubor** > **nového** > **projektu** > **Visual C#**  nebo**klasický Desktop** **Visual Basic** >  >  **Model Windows Forms aplikace**).</span><span class="sxs-lookup"><span data-stu-id="ab6db-110">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="ab6db-111">Ze **sady nástrojů**:</span><span class="sxs-lookup"><span data-stu-id="ab6db-111">From the **Toolbox**:</span></span>

    1. <span data-ttu-id="ab6db-112"><xref:System.Windows.Forms.SplitContainer> Přetáhněte ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ab6db-112">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>

    2. <span data-ttu-id="ab6db-113">Přetáhněte ovládací prvek do **SplitterPanel1** (panel <xref:System.Windows.Forms.SplitContainer> ovládacího prvku označený ovládacího Panel1 (). <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="ab6db-113">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>

    3. <span data-ttu-id="ab6db-114">Přetáhněte ovládací prvek do **SplitterPanel2** (panel <xref:System.Windows.Forms.SplitContainer> ovládacího prvku označený Panel2). <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="ab6db-114">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>

3. <span data-ttu-id="ab6db-115">Vyberte všechny tři ovládací prvky tak, že stisknete klávesu CTRL a pak je kliknete zase.</span><span class="sxs-lookup"><span data-stu-id="ab6db-115">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="ab6db-116">Když vyberete <xref:System.Windows.Forms.SplitContainer> ovládací prvek, klikněte na rozdělovač, nikoli na panely.</span><span class="sxs-lookup"><span data-stu-id="ab6db-116">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ab6db-117">V nabídce **Úpravy** nepoužívejte příkaz **Select All** .</span><span class="sxs-lookup"><span data-stu-id="ab6db-117">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="ab6db-118">Pokud tak učiníte, vlastnost potřebná v dalším kroku se nezobrazí v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="ab6db-118">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>

4. <span data-ttu-id="ab6db-119">V okně **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Fill>hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ab6db-119">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="ab6db-120">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ab6db-120">Press F5 to run the application.</span></span>

     <span data-ttu-id="ab6db-121">Ve formuláři se zobrazí uživatelské rozhraní se dvěma částmi, podobně jako v Průzkumníkovi Windows.</span><span class="sxs-lookup"><span data-stu-id="ab6db-121">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ab6db-122">Při přetahování rozdělovače se panely změní samy na sebe.</span><span class="sxs-lookup"><span data-stu-id="ab6db-122">When you drag the splitter, the panels resize themselves.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab6db-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab6db-123">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="ab6db-124">Postupy: Vytvoření uživatelského rozhraní s více podokny pomocí model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab6db-124">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="ab6db-125">Postupy: Definování chování změny velikosti a umístění v rozděleném okně</span><span class="sxs-lookup"><span data-stu-id="ab6db-125">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="ab6db-126">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="ab6db-126">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="ab6db-127">Ovládací prvek SplitContainer</span><span class="sxs-lookup"><span data-stu-id="ab6db-127">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
