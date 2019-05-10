---
title: 'Návod: Zajištění standardních položek nabídky pro formulář'
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
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211508"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="40308-102">Návod: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="40308-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="40308-103">Můžete zadat standardní nabídky formuláře s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="40308-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="40308-104">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> řízení vytvořit standardní nabídku.</span><span class="sxs-lookup"><span data-stu-id="40308-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="40308-105">Formuláře také reaguje, když uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="40308-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="40308-106">Tyto úlohy jsou uvedené v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="40308-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="40308-107">Vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40308-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="40308-108">Vytvoření standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="40308-108">Creating a standard menu.</span></span>

- <span data-ttu-id="40308-109">Vytváření <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="40308-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="40308-110">Zpracování výběru položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="40308-110">Handling menu item selection.</span></span>

<span data-ttu-id="40308-111">Až budete hotovi, budete mít formulář s standardní nabídky, která zobrazuje výběru položky nabídky v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="40308-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="40308-112">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Zajištění standardních položek nabídky pro formulář](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="40308-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40308-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40308-113">Prerequisites</span></span>

<span data-ttu-id="40308-114">Visual Studio k dokončení tohoto návodu budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="40308-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="40308-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="40308-115">Create the project</span></span>

1. <span data-ttu-id="40308-116">V sadě Visual Studio vytvořte projekt aplikace Windows volá **StandardMenuForm** (**souboru** > **nový** > **projektu**   >  **Visual C#**  nebo **jazyka Visual Basic** > **klasický desktopový**  >  **Aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="40308-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="40308-117">V Návrháři formulářů Windows vyberte formulář.</span><span class="sxs-lookup"><span data-stu-id="40308-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="40308-118">Vytvořit standardní nabídku</span><span class="sxs-lookup"><span data-stu-id="40308-118">Create a standard menu</span></span>

<span data-ttu-id="40308-119">Návrhář formulářů Windows můžete automaticky naplnit <xref:System.Windows.Forms.MenuStrip> ovládací prvek s standardních položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="40308-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="40308-120">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku na formulář.</span><span class="sxs-lookup"><span data-stu-id="40308-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="40308-121">Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> piktogram inteligentní značky ovládacího prvku (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **vložit standardní položky**.</span><span class="sxs-lookup"><span data-stu-id="40308-121">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="40308-122"><xref:System.Windows.Forms.MenuStrip> Ovládací prvek se vyplní standardních položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="40308-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="40308-123">Klikněte na tlačítko **souboru** položka nabídky zobrazit jeho výchozí položky nabídky a odpovídajících ikon.</span><span class="sxs-lookup"><span data-stu-id="40308-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="40308-124">Vytvoření ovládacího prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="40308-124">Create a StatusStrip control</span></span>

<span data-ttu-id="40308-125">Použití <xref:System.Windows.Forms.StatusStrip> ovládací prvek pro zobrazení stavu pro aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40308-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="40308-126">V uvedeném příkladě se zobrazí položky nabídky vybraných uživatelem v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="40308-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="40308-127">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.StatusStrip> ovládacího prvku na formulář.</span><span class="sxs-lookup"><span data-stu-id="40308-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="40308-128"><xref:System.Windows.Forms.StatusStrip> Ovládací prvek automaticky ukotvené do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="40308-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="40308-129">Klikněte na tlačítko <xref:System.Windows.Forms.StatusStrip> ovládacího prvku tlačítko rozevíracího seznamu a vyberte **StatusLabel** přidáte <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvek <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="40308-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="40308-130">Výběr položek popisovač</span><span class="sxs-lookup"><span data-stu-id="40308-130">Handle item selection</span></span>

<span data-ttu-id="40308-131">Zpracování <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> události a reagovat, když uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="40308-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="40308-132">Klikněte na tlačítko **soubor** položku nabídky, kterou jste vytvořili v části Vytvoření oddílu standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="40308-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="40308-133">V **vlastnosti** okna, klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="40308-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="40308-134">Dvakrát klikněte <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.</span><span class="sxs-lookup"><span data-stu-id="40308-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="40308-135">Návrhář formulářů Windows generuje obslužná rutina události <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.</span><span class="sxs-lookup"><span data-stu-id="40308-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="40308-136">Vložte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="40308-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="40308-137">Vložit `UpdateStatus` nástroj definici metody do formuláře.</span><span class="sxs-lookup"><span data-stu-id="40308-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="40308-138">Kontrolní bod – testování formuláře</span><span class="sxs-lookup"><span data-stu-id="40308-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="40308-139">Stisknutím klávesy **F5** kompilace a spuštění formuláře.</span><span class="sxs-lookup"><span data-stu-id="40308-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="40308-140">Klikněte na tlačítko **souboru** položky nabídky a otevřete nabídku.</span><span class="sxs-lookup"><span data-stu-id="40308-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="40308-141">Na **souboru** nabídky, klikněte na jednu z položek, vyberte ho.</span><span class="sxs-lookup"><span data-stu-id="40308-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="40308-142"><xref:System.Windows.Forms.StatusStrip> Ovládací prvek zobrazuje vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="40308-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="40308-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="40308-143">Next steps</span></span>

<span data-ttu-id="40308-144">V tomto návodu jste vytvořili, pomocí standardní nabídky formuláře.</span><span class="sxs-lookup"><span data-stu-id="40308-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="40308-145">Můžete použít <xref:System.Windows.Forms.ToolStrip> řady ovládacích prvků pro mnoho dalších důvodů:</span><span class="sxs-lookup"><span data-stu-id="40308-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="40308-146">Vytváření místních nabídek pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="40308-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="40308-147">Další informace najdete v tématu [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="40308-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="40308-148">Vytvoření více formuláře (MDI interface) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="40308-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="40308-149">Další informace najdete v tématu [názorný postup: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="40308-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="40308-150">Zadejte vaše <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled.</span><span class="sxs-lookup"><span data-stu-id="40308-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="40308-151">Další informace najdete v tématu [jak: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="40308-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40308-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40308-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="40308-153">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="40308-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
