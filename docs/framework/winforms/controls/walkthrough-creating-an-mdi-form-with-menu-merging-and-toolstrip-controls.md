---
title: 'Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip'
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
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628784"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="a7ad5-102">Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a7ad5-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="a7ad5-103">Obor názvů <xref:System.Windows.Forms?displayProperty=nameWithType> podporuje aplikace MDI (Multiple Document Interface) a ovládací prvek <xref:System.Windows.Forms.MenuStrip> podporuje slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="a7ad5-104">Formuláře MDI mohou také <xref:System.Windows.Forms.ToolStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="a7ad5-105">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky s formulářem MDI.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="a7ad5-106">Formulář také podporuje slučování nabídek s podřízenými nabídkami.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="a7ad5-107">V tomto návodu jsou znázorněné následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="a7ad5-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="a7ad5-108">Vytvoření projektu model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="a7ad5-109">Vytvoření hlavní nabídky pro formulář.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-109">Creating the main menu for your form.</span></span> <span data-ttu-id="a7ad5-110">Skutečný název nabídky se bude lišit.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="a7ad5-111">Přidání ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> do **panelu nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="a7ad5-112">Vytvoření podřízeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-112">Creating a child form.</span></span>

- <span data-ttu-id="a7ad5-113">Uspořádání ovládacích prvků <xref:System.Windows.Forms.ToolStripPanel> podle pořadí z.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="a7ad5-114">Až budete hotovi, budete mít formulář MDI, který podporuje slučování nabídek a <xref:System.Windows.Forms.ToolStrip> ovládací prvky s pohyblivým ovládáním.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="a7ad5-115">Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [Postup: Vytvoření formuláře MDI s nabídkou slučování a ovládacími prvky ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a7ad5-116">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="a7ad5-116">Prerequisites</span></span>

<span data-ttu-id="a7ad5-117">K dokončení tohoto Názorného postupu budete potřebovat Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a7ad5-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="a7ad5-118">Create the project</span></span>

1. <span data-ttu-id="a7ad5-119">V aplikaci Visual Studio vytvořte projekt aplikace pro Windows s názvem **MDIForm** (**File** > **New** > **Project** >  **C# Visual** nebo **Visual Basic** > **Classic Desktop** > **model Windows Forms aplikace**).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="a7ad5-120">V Návrhář formulářů vyberte formulář.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="a7ad5-121">V okno Vlastnosti nastavte hodnotu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="a7ad5-122">Vytvoření hlavní nabídky</span><span class="sxs-lookup"><span data-stu-id="a7ad5-122">Create the main menu</span></span>

<span data-ttu-id="a7ad5-123">Nadřazený formulář MDI obsahuje hlavní nabídku.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="a7ad5-124">Hlavní nabídka obsahuje jednu položku nabídky s názvem **okno**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="a7ad5-125">Pomocí položky nabídky **okno** můžete vytvořit podřízené formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="a7ad5-126">Položky nabídky z podřízených formulářů jsou sloučeny do hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="a7ad5-127">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.MenuStrip> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="a7ad5-128">Přidejte <xref:System.Windows.Forms.ToolStripMenuItem> do ovládacího prvku <xref:System.Windows.Forms.MenuStrip> a pojmenujte ho v **okně**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="a7ad5-129">Vyberte ovládací prvek <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="a7ad5-130">V okno Vlastnosti nastavte hodnotu vlastnosti <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> na `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="a7ad5-131">Přidejte podpoložku do položky nabídky **okna** a pak pojmenujte podpoložku **novou**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="a7ad5-132">V okno Vlastnosti klikněte na položku **události**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="a7ad5-133">Dvakrát klikněte na událost <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="a7ad5-134">Návrhář formulářů generuje obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="a7ad5-135">Do obslužné rutiny události vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="a7ad5-136">Přidání ovládacího prvku ToolStripPanel do panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="a7ad5-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="a7ad5-137">Pokud používáte <xref:System.Windows.Forms.MenuStrip> ovládací prvky s formulářem MDI, je nutné mít ovládací prvek <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="a7ad5-138">Chcete-li vytvořit formulář MDI v Návrhář formulářů, je nutné přidat ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> do **panelu nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="a7ad5-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="a7ad5-139">Otevřete **sadu nástrojů**a potom kliknutím na kartu **Všechny model Windows Forms** zobrazte dostupné model Windows Forms ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="a7ad5-140">Kliknutím pravým tlačítkem otevřete místní nabídku a vyberte **možnost vybrat položky**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="a7ad5-141">V dialogovém okně **zvolit položky sady nástrojů** přejděte dolů na sloupec **název** , dokud nenajdete **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="a7ad5-142">Zaškrtněte políčko na **ToolStripPanel**a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="a7ad5-143">Ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> se zobrazí v **sadě nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="a7ad5-144">Vytvoření podřízeného formuláře</span><span class="sxs-lookup"><span data-stu-id="a7ad5-144">Create a child form</span></span>

<span data-ttu-id="a7ad5-145">V tomto postupu definujete samostatnou podřízenou třídu formuláře, která má svůj vlastní ovládací prvek <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="a7ad5-146">Položky nabídky tohoto formuláře jsou sloučeny s prvky nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="a7ad5-147">Přidejte do projektu nový formulář s názvem `ChildForm`.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="a7ad5-148">Další informace naleznete v tématu [How to: Add model Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="a7ad5-149">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.MenuStrip> do podřízeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="a7ad5-150">Klikněte na glyf akcí návrháře <xref:System.Windows.Forms.MenuStrip> (![malé černé šipky](./media/designer-actions-glyph.gif)) a pak vyberte **Upravit položky**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-150">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="a7ad5-151">V dialogovém okně **Editor kolekce položek** přidejte do podřízené nabídky nový <xref:System.Windows.Forms.ToolStripMenuItem> s názvem **ChildMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="a7ad5-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="a7ad5-152">Další informace naleznete v tématu [Editor kolekce položek ovládacího prvku ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="a7ad5-153">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="a7ad5-153">Test the form</span></span>

1. <span data-ttu-id="a7ad5-154">Pro zkompilování a spuštění formuláře stiskněte klávesu **F5** .</span><span class="sxs-lookup"><span data-stu-id="a7ad5-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="a7ad5-155">Kliknutím na položku nabídky **okno** otevřete nabídku a potom klikněte na tlačítko **Nový**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="a7ad5-156">V klientské oblasti MDI formuláře se vytvoří nový podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="a7ad5-157">Nabídka podřízeného formuláře je sloučena s hlavní nabídkou.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="a7ad5-158">Zavřete podřízený formulář.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-158">Close the child form.</span></span>

     <span data-ttu-id="a7ad5-159">Nabídka podřízeného formuláře je odebrána z hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="a7ad5-160">Klikněte několikrát na **Nový** .</span><span class="sxs-lookup"><span data-stu-id="a7ad5-160">Click **New** several times.</span></span>

     <span data-ttu-id="a7ad5-161">Podřízené formuláře jsou automaticky uvedeny v položce nabídky **okna** , protože je přiřazena vlastnost <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> ovládacího prvku <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="a7ad5-162">Přidat podporu prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a7ad5-162">Add ToolStrip support</span></span>

<span data-ttu-id="a7ad5-163">V tomto postupu přidáte čtyři ovládací prvky <xref:System.Windows.Forms.ToolStrip> do nadřazeného formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="a7ad5-164">Každý <xref:System.Windows.Forms.ToolStrip> ovládací prvek je přidán do ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel>, který je ukotven k okraji formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="a7ad5-165">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="a7ad5-166">Po výběru ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> dvakrát klikněte na ovládací prvek <xref:System.Windows.Forms.ToolStrip> v sadě **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="a7ad5-167">V ovládacím prvku <xref:System.Windows.Forms.ToolStripPanel> je vytvořen ovládací prvek <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="a7ad5-168">Vyberte ovládací prvek <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="a7ad5-169">V okno Vlastnosti změňte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> ovládacího prvku na <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="a7ad5-170">Ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> Docker na levou stranu formuláře pod hlavní nabídkou.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="a7ad5-171">Oblast klienta MDI se mění tak, aby odpovídala ovládacímu prvku <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="a7ad5-172">Opakujte kroky 1 až 4.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="a7ad5-173">Ukotvěte nový ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> do horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="a7ad5-174">Ovládací prvek <xref:System.Windows.Forms.ToolStripPanel> je ukotven pod hlavní nabídkou, ale napravo od prvního ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="a7ad5-175">Tento krok ukazuje důležitost pořadí vykreslování při správném umísťování <xref:System.Windows.Forms.ToolStripPanel>ch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="a7ad5-176">Opakujte kroky 1 až 4 pro dva další <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="a7ad5-177">Ukotvěte nové ovládací prvky <xref:System.Windows.Forms.ToolStripPanel> doprava a dolů formuláře.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="a7ad5-178">Uspořádat ovládací prvky ToolStripPanel podle pořadí Z</span><span class="sxs-lookup"><span data-stu-id="a7ad5-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="a7ad5-179">Pozice ukotveného ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> ve formuláři MDI je určena pozicí ovládacího prvku v pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="a7ad5-180">Pořadí vykreslování ovládacích prvků lze snadno uspořádat v okně Osnova dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="a7ad5-181">V nabídce **zobrazení** klikněte na položku **ostatní okna**a potom klikněte na položku **Osnova dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="a7ad5-182">Uspořádání ovládacích prvků <xref:System.Windows.Forms.ToolStripPanel> z předchozího postupu je nestandardní.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="a7ad5-183">Je to proto, že pořadí vykreslování není správné.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="a7ad5-184">Pomocí okna Osnova dokumentu můžete změnit pořadí vykreslování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="a7ad5-185">V okně Osnova dokumentu vyberte **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="a7ad5-186">Opakovaně klikněte na tlačítko se šipkou dolů, dokud **ToolStripPanel4** není v dolní části seznamu.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="a7ad5-187">Ovládací prvek **ToolStripPanel4** je ukotven na spodní straně formuláře pod ostatními ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="a7ad5-188">Vyberte **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="a7ad5-189">Pokud chcete ovládací prvek umístit třetí v seznamu, klikněte na tlačítko se šipkou dolů jen jednou.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="a7ad5-190">Ovládací prvek **ToolStripPanel2** je ukotvený v horní části formuláře pod hlavní nabídkou a nad ostatními ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="a7ad5-191">V okně **Osnova dokumentu** vyberte různé ovládací prvky a přesuňte je na jiné pozice v pořadí z.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="a7ad5-192">Poznamenejte si účinek pořadí vykreslování na umístění ukotvených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="a7ad5-193">Pomocí kombinace kláves CTRL + Z nebo **příkazu zpět** v nabídce **Upravit** můžete změny vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="a7ad5-194">Kontrolní bod – testování formuláře</span><span class="sxs-lookup"><span data-stu-id="a7ad5-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="a7ad5-195">Pro zkompilování a spuštění formuláře stiskněte klávesu **F5** .</span><span class="sxs-lookup"><span data-stu-id="a7ad5-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="a7ad5-196">Klikněte na úchyt ovládacího prvku <xref:System.Windows.Forms.ToolStrip> a přetáhněte ovládací prvek na jiné pozice ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="a7ad5-197">Ovládací prvek <xref:System.Windows.Forms.ToolStrip> lze přetáhnout z jednoho ovládacího prvku <xref:System.Windows.Forms.ToolStripPanel> na jiný.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a7ad5-198">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a7ad5-198">Next steps</span></span>

<span data-ttu-id="a7ad5-199">V tomto návodu jste vytvořili nadřazený formulář MDI s ovládacími prvky <xref:System.Windows.Forms.ToolStrip> a slučováním nabídek.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="a7ad5-200"><xref:System.Windows.Forms.ToolStrip> rodinu ovládacích prvků lze použít pro mnoho dalších účelů:</span><span class="sxs-lookup"><span data-stu-id="a7ad5-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="a7ad5-201">Vytvořte místní nabídky pro ovládací prvky pomocí <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="a7ad5-202">Další informace najdete v tématu věnovaném [přehledu komponent](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="a7ad5-203">Vytvořili jste formulář s automaticky vyplněnou standardní nabídkou.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="a7ad5-204">Další informace najdete v tématu [Návod: poskytnutí standardních položek nabídky formuláři](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="a7ad5-205">Poskytněte vašemu <xref:System.Windows.Forms.ToolStrip> profesionální vzhled.</span><span class="sxs-lookup"><span data-stu-id="a7ad5-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="a7ad5-206">Další informace naleznete v tématu [How to: set a Renderer ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="a7ad5-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7ad5-207">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7ad5-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="a7ad5-208">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="a7ad5-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="a7ad5-209">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="a7ad5-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="a7ad5-210">Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI</span><span class="sxs-lookup"><span data-stu-id="a7ad5-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="a7ad5-211">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a7ad5-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
