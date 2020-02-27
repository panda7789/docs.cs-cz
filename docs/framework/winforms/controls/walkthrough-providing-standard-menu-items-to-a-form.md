---
title: 'Návod: Poskytnutí standardních položek nabídky formuláři'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628771"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="2213c-102">Návod: Poskytnutí standardních položek nabídky formuláři</span><span class="sxs-lookup"><span data-stu-id="2213c-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="2213c-103">Pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip> můžete poskytnout standardní nabídku pro vaše formuláře.</span><span class="sxs-lookup"><span data-stu-id="2213c-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="2213c-104">Tento návod ukazuje, jak pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip> vytvořit standardní nabídku.</span><span class="sxs-lookup"><span data-stu-id="2213c-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="2213c-105">Formulář také reaguje, když uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="2213c-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="2213c-106">V tomto návodu jsou znázorněné následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="2213c-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="2213c-107">Vytvoření projektu model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2213c-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="2213c-108">Vytvoření standardní nabídky</span><span class="sxs-lookup"><span data-stu-id="2213c-108">Creating a standard menu.</span></span>

- <span data-ttu-id="2213c-109">Vytvoření ovládacího prvku <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2213c-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="2213c-110">Zpracování výběru položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="2213c-110">Handling menu item selection.</span></span>

<span data-ttu-id="2213c-111">Po dokončení budete mít formulář se standardní nabídkou, která zobrazí výběr položek nabídky v ovládacím prvku <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2213c-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="2213c-112">Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [Postup: poskytnutí standardních položek nabídky do formuláře](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="2213c-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2213c-113">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="2213c-113">Prerequisites</span></span>

<span data-ttu-id="2213c-114">K dokončení tohoto Názorného postupu budete potřebovat Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2213c-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="2213c-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="2213c-115">Create the project</span></span>

1. <span data-ttu-id="2213c-116">V aplikaci Visual Studio vytvořte projekt aplikace pro Windows s názvem **StandardMenuForm** (**File** > **New** > **Project** >  **C# Visual** nebo **Visual Basic** > **Classic Desktop** > **model Windows Forms aplikace**).</span><span class="sxs-lookup"><span data-stu-id="2213c-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="2213c-117">V Návrhář formulářů vyberte formulář.</span><span class="sxs-lookup"><span data-stu-id="2213c-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="2213c-118">Vytvořit standardní nabídku</span><span class="sxs-lookup"><span data-stu-id="2213c-118">Create a standard menu</span></span>

<span data-ttu-id="2213c-119">Návrhář formulářů může automaticky naplnit ovládací prvek <xref:System.Windows.Forms.MenuStrip> pomocí standardních položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="2213c-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="2213c-120">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.MenuStrip> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="2213c-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="2213c-121">Klikněte na piktogram akcí návrháře <xref:System.Windows.Forms.MenuStrip> (![malé černé šipky](./media/designer-actions-glyph.gif)) a vyberte **Vložit standardní položky**.</span><span class="sxs-lookup"><span data-stu-id="2213c-121">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="2213c-122">Ovládací prvek <xref:System.Windows.Forms.MenuStrip> se naplní standardními položkami nabídky.</span><span class="sxs-lookup"><span data-stu-id="2213c-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="2213c-123">Kliknutím na položku nabídky **soubor** zobrazíte její výchozí položky nabídky a příslušné ikony.</span><span class="sxs-lookup"><span data-stu-id="2213c-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="2213c-124">Vytvoření ovládacího prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="2213c-124">Create a StatusStrip control</span></span>

<span data-ttu-id="2213c-125">Pro zobrazení stavu aplikací model Windows Forms použijte ovládací prvek <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2213c-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="2213c-126">V aktuálním příkladu se položky nabídky vybrané uživatelem zobrazí v ovládacím prvku <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2213c-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="2213c-127">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.StatusStrip> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="2213c-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="2213c-128">Ovládací prvek <xref:System.Windows.Forms.StatusStrip> se automaticky ukotví do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="2213c-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="2213c-129">Klikněte na tlačítko rozevíracího seznamu <xref:System.Windows.Forms.StatusStrip>ho ovládacího prvku a výběrem **StatusLabel** přidejte ovládací prvek <xref:System.Windows.Forms.ToolStripStatusLabel> do ovládacího prvku <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="2213c-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="2213c-130">Zpracovat výběr položky</span><span class="sxs-lookup"><span data-stu-id="2213c-130">Handle item selection</span></span>

<span data-ttu-id="2213c-131">Zpracuje událost <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>, aby reagovala, když uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="2213c-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="2213c-132">Klikněte na položku nabídky **soubor** , kterou jste vytvořili v části vytvoření standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="2213c-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="2213c-133">V okně **vlastnosti** klikněte na položku **události**.</span><span class="sxs-lookup"><span data-stu-id="2213c-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="2213c-134">Dvakrát klikněte na událost <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="2213c-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="2213c-135">Návrhář formulářů generuje obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="2213c-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="2213c-136">Do obslužné rutiny události vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="2213c-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="2213c-137">Do formuláře vložte definici metody nástroje `UpdateStatus`.</span><span class="sxs-lookup"><span data-stu-id="2213c-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="2213c-138">Kontrolní bod – testování formuláře</span><span class="sxs-lookup"><span data-stu-id="2213c-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="2213c-139">Pro zkompilování a spuštění formuláře stiskněte klávesu **F5** .</span><span class="sxs-lookup"><span data-stu-id="2213c-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="2213c-140">Kliknutím na položku nabídky **soubor** otevřete nabídku.</span><span class="sxs-lookup"><span data-stu-id="2213c-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="2213c-141">V nabídce **soubor** klikněte na jednu z položek a vyberte ji.</span><span class="sxs-lookup"><span data-stu-id="2213c-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="2213c-142">Ovládací prvek <xref:System.Windows.Forms.StatusStrip> zobrazí vybranou položku.</span><span class="sxs-lookup"><span data-stu-id="2213c-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2213c-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2213c-143">Next steps</span></span>

<span data-ttu-id="2213c-144">V tomto návodu jste vytvořili formulář se standardní nabídkou.</span><span class="sxs-lookup"><span data-stu-id="2213c-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="2213c-145"><xref:System.Windows.Forms.ToolStrip> rodinu ovládacích prvků lze použít pro mnoho dalších účelů:</span><span class="sxs-lookup"><span data-stu-id="2213c-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="2213c-146">Vytvořte místní nabídky pro ovládací prvky pomocí <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="2213c-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="2213c-147">Další informace najdete v tématu věnovaném [přehledu komponent](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2213c-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="2213c-148">Vytvořte formulář MDI (Multiple Document Interface) s ovládacími prvky docking <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="2213c-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="2213c-149">Další informace najdete v tématu [Návod: Vytvoření formuláře MDI pomocí slučování nabídek a ovládacích prvků ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2213c-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="2213c-150">Poskytněte vašemu <xref:System.Windows.Forms.ToolStrip> profesionální vzhled.</span><span class="sxs-lookup"><span data-stu-id="2213c-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="2213c-151">Další informace naleznete v tématu [How to: set a Renderer ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="2213c-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2213c-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="2213c-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="2213c-153">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="2213c-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
