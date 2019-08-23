---
title: 'Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 34a5cd735c350688d9e83003806668e213932c85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960627"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="a8b5c-102">Postupy: Vytváření rozhraní ve stylu Průzkumníka Windows ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8b5c-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="a8b5c-103">Průzkumník Windows je běžná volba uživatelského rozhraní pro aplikace z důvodu své připravenosti.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>

 <span data-ttu-id="a8b5c-104">Průzkumník Windows je v podstatě <xref:System.Windows.Forms.TreeView> ovládací prvek <xref:System.Windows.Forms.ListView> a ovládací prvek na samostatných panelech.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="a8b5c-105">Panely mají změnu velikosti příčkou.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="a8b5c-106">Toto uspořádání ovládacích prvků je velmi efektivní pro zobrazení a informace o procházení.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>

 <span data-ttu-id="a8b5c-107">Následující kroky ukazují, jak uspořádat ovládací prvky ve formuláři podobném prohlížeči Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="a8b5c-108">Neukazují, jak přidat funkce pro procházení souborů v aplikaci Průzkumník Windows.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>

## <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="a8b5c-109">Vytvoření formuláře Windows ve stylu Průzkumníka Windows</span><span class="sxs-lookup"><span data-stu-id="a8b5c-109">To create a Windows Explorer-style Windows Form</span></span>

1. <span data-ttu-id="a8b5c-110">Vytvoření nového projektu aplikace pro Windows (**soubor** > **nového** > **projektu** > **Visual C#**  nebo**klasický Desktop** **Visual Basic** >  >  **Model Windows Forms aplikace**).</span><span class="sxs-lookup"><span data-stu-id="a8b5c-110">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="a8b5c-111">Ze **sady nástrojů**:</span><span class="sxs-lookup"><span data-stu-id="a8b5c-111">From the **Toolbox**:</span></span>

    1. <span data-ttu-id="a8b5c-112"><xref:System.Windows.Forms.SplitContainer> Přetáhněte ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-112">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>

    2. <span data-ttu-id="a8b5c-113">Přetáhněte ovládací prvek do **SplitterPanel1** (panel <xref:System.Windows.Forms.SplitContainer> ovládacího prvku označený ovládacího Panel1 (). <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="a8b5c-113">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>

    3. <span data-ttu-id="a8b5c-114">Přetáhněte ovládací prvek do **SplitterPanel2** (panel <xref:System.Windows.Forms.SplitContainer> ovládacího prvku označený Panel2). <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="a8b5c-114">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>

3. <span data-ttu-id="a8b5c-115">Vyberte všechny tři ovládací prvky tak, že stisknete klávesu CTRL a pak je kliknete zase.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-115">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="a8b5c-116">Když vyberete <xref:System.Windows.Forms.SplitContainer> ovládací prvek, klikněte na rozdělovač, nikoli na panely.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-116">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a8b5c-117">V nabídce **Úpravy** nepoužívejte příkaz **Select All** .</span><span class="sxs-lookup"><span data-stu-id="a8b5c-117">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="a8b5c-118">Pokud tak učiníte, vlastnost potřebná v dalším kroku se nezobrazí v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="a8b5c-118">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>

4. <span data-ttu-id="a8b5c-119">V okně **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost na <xref:System.Windows.Forms.DockStyle.Fill>hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-119">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="a8b5c-120">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-120">Press F5 to run the application.</span></span>

     <span data-ttu-id="a8b5c-121">Ve formuláři se zobrazí uživatelské rozhraní se dvěma částmi, podobně jako v Průzkumníkovi Windows.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-121">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a8b5c-122">Při přetahování rozdělovače se panely změní samy na sebe.</span><span class="sxs-lookup"><span data-stu-id="a8b5c-122">When you drag the splitter, the panels resize themselves.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8b5c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8b5c-123">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="a8b5c-124">Postupy: Vytvoření uživatelského rozhraní s více podokny pomocí model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8b5c-124">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="a8b5c-125">Postupy: Definování chování změny velikosti a umístění v rozděleném okně</span><span class="sxs-lookup"><span data-stu-id="a8b5c-125">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="a8b5c-126">Postupy: Vodorovné rozdělení okna</span><span class="sxs-lookup"><span data-stu-id="a8b5c-126">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="a8b5c-127">Ovládací prvek SplitContainer</span><span class="sxs-lookup"><span data-stu-id="a8b5c-127">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
