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
ms.openlocfilehash: b4957a3f2efcb31594806a188e3d3bb10c2dac09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792207"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="0656a-102">Návod: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="0656a-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="0656a-103">Můžete zadat standardní nabídky formuláře s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0656a-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="0656a-104">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> řízení vytvořit standardní nabídku.</span><span class="sxs-lookup"><span data-stu-id="0656a-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="0656a-105">Formuláře také reaguje, když uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="0656a-106">Tyto úlohy jsou uvedené v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="0656a-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
- <span data-ttu-id="0656a-107">Vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0656a-107">Creating a Windows Forms project.</span></span>  
  
- <span data-ttu-id="0656a-108">Vytvoření standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-108">Creating a standard menu.</span></span>  
  
- <span data-ttu-id="0656a-109">Vytváření <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0656a-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
- <span data-ttu-id="0656a-110">Zpracování výběru položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="0656a-111">Až budete hotovi, budete mít formulář s standardní nabídky, která zobrazuje výběru položky nabídky v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0656a-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="0656a-112">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Zajištění standardních položek nabídky pro formulář](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="0656a-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0656a-113">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="0656a-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0656a-114">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0656a-115">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0656a-115">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0656a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0656a-116">Prerequisites</span></span>  
 <span data-ttu-id="0656a-117">K dokončení tohoto návodu budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="0656a-117">In order to complete this walkthrough, you will need:</span></span>  
  
- <span data-ttu-id="0656a-118">Dostatečná oprávnění k vytvoření a spuštění projektů aplikace Windows Forms v počítači nainstalovanou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0656a-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="0656a-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="0656a-119">Creating the Project</span></span>  
 <span data-ttu-id="0656a-120">Prvním krokem je vytvoření projektu a nastavení formuláře.</span><span class="sxs-lookup"><span data-stu-id="0656a-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="0656a-121">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="0656a-121">To create the project</span></span>  
  
1. <span data-ttu-id="0656a-122">Vytvoření projektu aplikace Windows volá **StandardMenuForm** (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms Aplikace**).</span><span class="sxs-lookup"><span data-stu-id="0656a-122">Create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2. <span data-ttu-id="0656a-123">V Návrháři formulářů Windows vyberte formulář.</span><span class="sxs-lookup"><span data-stu-id="0656a-123">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="0656a-124">Vytvoření standardní nabídky</span><span class="sxs-lookup"><span data-stu-id="0656a-124">Creating a Standard Menu</span></span>  
 <span data-ttu-id="0656a-125">Návrhář formulářů Windows můžete automaticky naplnit <xref:System.Windows.Forms.MenuStrip> ovládací prvek s standardních položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-125">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="0656a-126">Chcete-li vytvořit standardní nabídky</span><span class="sxs-lookup"><span data-stu-id="0656a-126">To create a standard menu</span></span>  
  
1. <span data-ttu-id="0656a-127">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku na formulář.</span><span class="sxs-lookup"><span data-stu-id="0656a-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2. <span data-ttu-id="0656a-128">Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> piktogram inteligentní značky ovládacího prvku (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **vložit standardní položky**.</span><span class="sxs-lookup"><span data-stu-id="0656a-128">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="0656a-129"><xref:System.Windows.Forms.MenuStrip> Ovládací prvek se vyplní standardních položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-129">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3. <span data-ttu-id="0656a-130">Klikněte na tlačítko **souboru** položka nabídky zobrazit jeho výchozí položky nabídky a odpovídajících ikon.</span><span class="sxs-lookup"><span data-stu-id="0656a-130">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="0656a-131">Vytvoření ovládacího prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="0656a-131">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="0656a-132">Použití <xref:System.Windows.Forms.StatusStrip> ovládací prvek pro zobrazení stavu pro aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0656a-132">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="0656a-133">V uvedeném příkladě se zobrazí položky nabídky vybraných uživatelem v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0656a-133">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="0656a-134">Vytvoření ovládacího prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="0656a-134">To create a StatusStrip control</span></span>  
  
1. <span data-ttu-id="0656a-135">Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.StatusStrip> ovládacího prvku na formulář.</span><span class="sxs-lookup"><span data-stu-id="0656a-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="0656a-136"><xref:System.Windows.Forms.StatusStrip> Ovládací prvek automaticky ukotvené do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="0656a-136">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2. <span data-ttu-id="0656a-137">Klikněte na tlačítko <xref:System.Windows.Forms.StatusStrip> ovládacího prvku tlačítko rozevíracího seznamu a vyberte **StatusLabel** přidáte <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvek <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0656a-137">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="0656a-138">Výběr položek zpracování</span><span class="sxs-lookup"><span data-stu-id="0656a-138">Handling Item Selection</span></span>  
 <span data-ttu-id="0656a-139">Zpracování <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> události a reagovat, když uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-139">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="0656a-140">Pro zpracování výběr položky</span><span class="sxs-lookup"><span data-stu-id="0656a-140">To handle item selection</span></span>  
  
1. <span data-ttu-id="0656a-141">Klikněte na tlačítko **soubor** položku nabídky, kterou jste vytvořili v části Vytvoření oddílu standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="0656a-141">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2. <span data-ttu-id="0656a-142">V **vlastnosti** okna, klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="0656a-142">In the **Properties** window, click **Events**.</span></span>  
  
3. <span data-ttu-id="0656a-143">Dvakrát klikněte <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.</span><span class="sxs-lookup"><span data-stu-id="0656a-143">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="0656a-144">Návrhář formulářů Windows generuje obslužná rutina události <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.</span><span class="sxs-lookup"><span data-stu-id="0656a-144">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4. <span data-ttu-id="0656a-145">Vložte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0656a-145">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5. <span data-ttu-id="0656a-146">Vložit `UpdateStatus` nástroj definici metody do formuláře.</span><span class="sxs-lookup"><span data-stu-id="0656a-146">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="0656a-147">CheckPoint</span><span class="sxs-lookup"><span data-stu-id="0656a-147">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="0656a-148">K otestování formuláře</span><span class="sxs-lookup"><span data-stu-id="0656a-148">To test your form</span></span>  
  
1. <span data-ttu-id="0656a-149">Stisknutím klávesy F5 kompilace a spuštění formuláře.</span><span class="sxs-lookup"><span data-stu-id="0656a-149">Press F5 to compile and run your form.</span></span>  
  
2. <span data-ttu-id="0656a-150">Klikněte na tlačítko **souboru** položky nabídky a otevřete nabídku.</span><span class="sxs-lookup"><span data-stu-id="0656a-150">Click the **File** menu item to open the menu.</span></span>  
  
3. <span data-ttu-id="0656a-151">Na **souboru** nabídky, klikněte na jednu z položek, vyberte ho.</span><span class="sxs-lookup"><span data-stu-id="0656a-151">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="0656a-152"><xref:System.Windows.Forms.StatusStrip> Ovládací prvek zobrazuje vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="0656a-152">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0656a-153">Další kroky</span><span class="sxs-lookup"><span data-stu-id="0656a-153">Next Steps</span></span>  
 <span data-ttu-id="0656a-154">V tomto návodu jste vytvořili, pomocí standardní nabídky formuláře.</span><span class="sxs-lookup"><span data-stu-id="0656a-154">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="0656a-155">Můžete použít <xref:System.Windows.Forms.ToolStrip> řady ovládacích prvků pro mnoho dalších důvodů:</span><span class="sxs-lookup"><span data-stu-id="0656a-155">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
- <span data-ttu-id="0656a-156">Vytváření místních nabídek pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="0656a-156">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="0656a-157">Další informace najdete v tématu [ContextMenu – přehled komponenty](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0656a-157">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>  
  
- <span data-ttu-id="0656a-158">Vytvoření více formuláře (MDI interface) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="0656a-158">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="0656a-159">Další informace najdete v tématu [názorný postup: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0656a-159">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
- <span data-ttu-id="0656a-160">Zadejte vaše <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled.</span><span class="sxs-lookup"><span data-stu-id="0656a-160">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="0656a-161">Další informace najdete v tématu [jak: Nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="0656a-161">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0656a-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0656a-162">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="0656a-163">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="0656a-163">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
