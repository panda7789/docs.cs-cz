---
title: 'Návod: Vytvoření formuláře MDI s ovládacími prvky Menu Merging a ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: 5853760231cbece27805923c009d83e16c9b0a5e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211561"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="dc44f-102">Návod: Vytvoření formuláře MDI s ovládacími prvky Menu Merging a ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc44f-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="dc44f-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů podporuje více dokumentů aplikace (MDI interface) a <xref:System.Windows.Forms.MenuStrip> ovládací prvek podporuje slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="dc44f-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="dc44f-104">MDI formuláře můžete také <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="dc44f-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="dc44f-105">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="dc44f-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="dc44f-106">Formulář podporuje také s nabídkami podřízené slučováním nabídek.</span><span class="sxs-lookup"><span data-stu-id="dc44f-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="dc44f-107">Tyto úlohy jsou uvedené v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="dc44f-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="dc44f-108">Vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dc44f-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="dc44f-109">Vytvoření hlavní nabídky pro formulář.</span><span class="sxs-lookup"><span data-stu-id="dc44f-109">Creating the main menu for your form.</span></span> <span data-ttu-id="dc44f-110">Skutečný název nabídky se liší.</span><span class="sxs-lookup"><span data-stu-id="dc44f-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="dc44f-111">Přidávání <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="dc44f-112">Vytváří se podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="dc44f-112">Creating a child form.</span></span>

- <span data-ttu-id="dc44f-113">Uspořádání <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky podle pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="dc44f-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="dc44f-114">Až budete hotovi, budete mít formuláře MDI, která podporuje menu merging a přesouvatelných <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="dc44f-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="dc44f-115">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="dc44f-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc44f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc44f-116">Prerequisites</span></span>

<span data-ttu-id="dc44f-117">Visual Studio k dokončení tohoto návodu budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="dc44f-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="dc44f-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="dc44f-118">Create the project</span></span>

1. <span data-ttu-id="dc44f-119">V sadě Visual Studio vytvořte projekt aplikace Windows s názvem **MdiForm** (**souboru** > **nový** > **projektu**  >  **Visual C#**  nebo **jazyka Visual Basic** > **klasický desktopový**  >   **Aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="dc44f-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="dc44f-120">V Návrháři formulářů Windows vyberte formulář.</span><span class="sxs-lookup"><span data-stu-id="dc44f-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="dc44f-121">V okně Vlastnosti nastavte hodnotu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="dc44f-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="dc44f-122">Vytvořte v hlavní nabídce</span><span class="sxs-lookup"><span data-stu-id="dc44f-122">Create the main menu</span></span>

<span data-ttu-id="dc44f-123">Nadřazený formulář MDI obsahuje hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dc44f-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="dc44f-124">V hlavní nabídce má jedna položka nabídky s názvem **okno**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="dc44f-125">S **okno** položku nabídky, můžete vytvořit podřízené formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc44f-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="dc44f-126">Položky nabídky z podřízené formuláře jsou sloučeny do hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dc44f-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="dc44f-127">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="dc44f-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="dc44f-128">Přidat <xref:System.Windows.Forms.ToolStripMenuItem> k <xref:System.Windows.Forms.MenuStrip> řídit a pojmenujte ho **okno**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="dc44f-129">Vyberte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dc44f-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="dc44f-130">V okně Vlastnosti nastavte hodnotu <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="dc44f-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="dc44f-131">Přidat podřízenou položku k **okno** položky nabídky a pojmenujte podřízenou položku **nový**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="dc44f-132">V okně Vlastnosti klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="dc44f-133">Dvakrát klikněte <xref:System.Windows.Forms.ToolStripItem.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="dc44f-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="dc44f-134">Návrhář formulářů Windows generuje obslužná rutina události <xref:System.Windows.Forms.ToolStripItem.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="dc44f-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="dc44f-135">Vložte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="dc44f-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="dc44f-136">ToolStripPanel – ovládací prvek přidat do panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="dc44f-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="dc44f-137">Při použití <xref:System.Windows.Forms.MenuStrip> ovládacích prvků formuláře MDI musí mít <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dc44f-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="dc44f-138">Je nutné přidat <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek **nástrojů** k vytvoření formuláře MDI v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="dc44f-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="dc44f-139">Otevřít **nástrojů**a potom klikněte na tlačítko **všechny formuláře Windows** zobrazte dostupné ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dc44f-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="dc44f-140">Klikněte pravým tlačítkem na otevřete místní nabídku a vyberte **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="dc44f-141">V **zvolit položky nástrojů** dialogové okno, přejděte dolů **název** sloupce, dokud nenajdete **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="dc44f-142">Zaškrtněte políčko podle **ToolStripPanel**a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="dc44f-143"><xref:System.Windows.Forms.ToolStripPanel> Ovládací prvek zobrazí **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="dc44f-144">Vytváření podřízených formulářů</span><span class="sxs-lookup"><span data-stu-id="dc44f-144">Create a child form</span></span>

<span data-ttu-id="dc44f-145">V tomto postupu bude definujete třídu samostatnou podřízenou formulář, který má vlastní <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dc44f-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="dc44f-146">Položky nabídky pro tento formulář jsou sloučeny s těmi nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc44f-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="dc44f-147">Přidat nový formulář s názvem `ChildForm` do projektu.</span><span class="sxs-lookup"><span data-stu-id="dc44f-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="dc44f-148">Další informace najdete v tématu [jak: Přidat do projektu Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dc44f-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="dc44f-149">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládací prvek na podřízeném formuláři.</span><span class="sxs-lookup"><span data-stu-id="dc44f-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="dc44f-150">Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> piktogram inteligentní značky ovládacího prvku (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a pak vyberte **upravit položky**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-150">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="dc44f-151">V **Editor kolekce položek** dialogovém okně přidejte nový <xref:System.Windows.Forms.ToolStripMenuItem> s názvem **ChildMenuItem** do nabídky podřízené.</span><span class="sxs-lookup"><span data-stu-id="dc44f-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="dc44f-152">Další informace najdete v tématu [Editor kolekce položek ovládacího prvku ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dc44f-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="dc44f-153">Testovací formulář</span><span class="sxs-lookup"><span data-stu-id="dc44f-153">Test the form</span></span>

1. <span data-ttu-id="dc44f-154">Stisknutím klávesy **F5** kompilace a spuštění formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc44f-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="dc44f-155">Klikněte na tlačítko **okno** otevřete nabídku a pak klikněte na položku nabídky **nový**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="dc44f-156">V klientské oblasti formuláře MDI se vytvoří nový podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="dc44f-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="dc44f-157">Nabídky podřízené formuláře je sloučen s hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dc44f-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="dc44f-158">Podřízený formulář zavřete.</span><span class="sxs-lookup"><span data-stu-id="dc44f-158">Close the child form.</span></span>

     <span data-ttu-id="dc44f-159">Nabídky podřízené formuláře se odebere z hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dc44f-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="dc44f-160">Klikněte na tlačítko **nový** několikrát.</span><span class="sxs-lookup"><span data-stu-id="dc44f-160">Click **New** several times.</span></span>

     <span data-ttu-id="dc44f-161">Podřízené formuláře se automaticky zobrazí **okno** položky nabídky, protože <xref:System.Windows.Forms.MenuStrip> ovládacího prvku <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> přiřadit vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dc44f-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="dc44f-162">Přidání podpory pro ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc44f-162">Add ToolStrip support</span></span>

<span data-ttu-id="dc44f-163">V tomto postupu přidáte čtyři <xref:System.Windows.Forms.ToolStrip> ovládacích prvků na nadřazený formulář MDI.</span><span class="sxs-lookup"><span data-stu-id="dc44f-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="dc44f-164">Každý <xref:System.Windows.Forms.ToolStrip> ovládací prvek je přidán uvnitř <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek, který je ukotven k okraji formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc44f-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="dc44f-165">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="dc44f-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="dc44f-166">S <xref:System.Windows.Forms.ToolStripPanel> vybraný ovládací prvek, dvakrát klikněte <xref:System.Windows.Forms.ToolStrip> v ovládacím prvku **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="dc44f-167">A <xref:System.Windows.Forms.ToolStrip> ovládací prvek je vytvořen v <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dc44f-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="dc44f-168">Vyberte <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dc44f-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="dc44f-169">V okně Vlastnosti změňte hodnotu ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="dc44f-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="dc44f-170"><xref:System.Windows.Forms.ToolStripPanel> Řídit ukotví na levou stranu formuláře pod hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dc44f-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="dc44f-171">V oblasti klienta MDI přizpůsobí svou velikost <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dc44f-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="dc44f-172">Opakujte kroky 1 až 4.</span><span class="sxs-lookup"><span data-stu-id="dc44f-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="dc44f-173">Ukotvit nové <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc44f-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="dc44f-174"><xref:System.Windows.Forms.ToolStripPanel> Ovládací prvek ukotven pod hlavní nabídky, ale napravo od prvního <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dc44f-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="dc44f-175">Tento krok ukazuje důležitost pořadí vykreslování v správně umístění <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="dc44f-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="dc44f-176">Opakujte kroky 1 až 4 pro dva další <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="dc44f-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="dc44f-177">Ukotvit nové <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků doprava a dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc44f-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="dc44f-178">Uspořádat podle pořadí vykreslování ovládacími prvky ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="dc44f-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="dc44f-179">Pozice ukotvených <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek formuláře MDI se určuje podle pozice ovládacího prvku v pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="dc44f-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="dc44f-180">Snadno můžete uspořádat pořadí vykreslování ovládacích prvků v okně osnovy dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dc44f-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="dc44f-181">V **zobrazení** nabídky, klikněte na tlačítko **ostatní Windows**a potom klikněte na tlačítko **Osnova dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="dc44f-182">Uspořádání vašich <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky z předchozího postupu je nestandardní.</span><span class="sxs-lookup"><span data-stu-id="dc44f-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="dc44f-183">Je to proto, že pořadí vykreslování není správný.</span><span class="sxs-lookup"><span data-stu-id="dc44f-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="dc44f-184">Chcete-li změnit pořadí vykreslování ovládacích prvků použijte okno osnovy dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dc44f-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="dc44f-185">V okně Osnova dokumentu vyberte **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="dc44f-186">Klikněte na tlačítko se šipkou dolů opakovaně, dokud **ToolStripPanel4** je v dolní části seznamu.</span><span class="sxs-lookup"><span data-stu-id="dc44f-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="dc44f-187">**ToolStripPanel4** ovládací prvek ukotven k dolní části formuláře, pod ostatní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="dc44f-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="dc44f-188">Vyberte **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="dc44f-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="dc44f-189">Kliknutím na tlačítko se šipkou dolů jednou třetí umístění ovládacího prvku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="dc44f-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="dc44f-190">**ToolStripPanel2** ovládací prvek ukotven k hornímu okraji pod hlavní nabídky a vyšší než ostatní ovládací prvky formulář.</span><span class="sxs-lookup"><span data-stu-id="dc44f-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="dc44f-191">Vyberte různé ovládací prvky v **Osnova dokumentu** okno a přesouvat je na jinou pozici v pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="dc44f-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="dc44f-192">Všimněte si vliv pořadí vykreslování na umístění ukotvených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="dc44f-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="dc44f-193">Pomocí CTRL-Z nebo **zpět** na **upravit** nabídky vrátit zpět provedené změny.</span><span class="sxs-lookup"><span data-stu-id="dc44f-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="dc44f-194">Kontrolní bod – testování formuláře</span><span class="sxs-lookup"><span data-stu-id="dc44f-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="dc44f-195">Stisknutím klávesy **F5** kompilace a spuštění formuláře.</span><span class="sxs-lookup"><span data-stu-id="dc44f-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="dc44f-196">Klikněte na úchytu o <xref:System.Windows.Forms.ToolStrip> řídit a přetáhněte jej na různých místech ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="dc44f-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="dc44f-197">Můžete přetáhnout <xref:System.Windows.Forms.ToolStrip> ovládacího prvku z jednoho <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do jiného.</span><span class="sxs-lookup"><span data-stu-id="dc44f-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc44f-198">Další kroky</span><span class="sxs-lookup"><span data-stu-id="dc44f-198">Next steps</span></span>

<span data-ttu-id="dc44f-199">V tomto návodu vytvoříte nadřazené formuláře MDI s <xref:System.Windows.Forms.ToolStrip> ovládací prvky a slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="dc44f-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="dc44f-200">Můžete použít <xref:System.Windows.Forms.ToolStrip> řady ovládacích prvků pro mnoho dalších důvodů:</span><span class="sxs-lookup"><span data-stu-id="dc44f-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="dc44f-201">Vytváření místních nabídek pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="dc44f-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="dc44f-202">Další informace najdete v tématu [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="dc44f-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="dc44f-203">Vytvoření formuláře se automaticky vyplněná standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="dc44f-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="dc44f-204">Další informace najdete v tématu [názorný postup: Poskytnutí standardních položek nabídky formuláři](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="dc44f-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="dc44f-205">Zadejte vaše <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled.</span><span class="sxs-lookup"><span data-stu-id="dc44f-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="dc44f-206">Další informace najdete v tématu [jak: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="dc44f-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc44f-207">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc44f-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="dc44f-208">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="dc44f-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="dc44f-209">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="dc44f-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="dc44f-210">Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI</span><span class="sxs-lookup"><span data-stu-id="dc44f-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="dc44f-211">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc44f-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
