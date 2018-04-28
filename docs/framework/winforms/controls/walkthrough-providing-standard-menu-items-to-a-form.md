---
title: 'Návod: Poskytnutí standardních položek nabídky formuláři'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00988266804207e85bc715342f888fd29348066e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="913da-102">Návod: Poskytnutí standardních položek nabídky formuláři</span><span class="sxs-lookup"><span data-stu-id="913da-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>
<span data-ttu-id="913da-103">Můžete zadat standardní nabídky svých formulářů s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="913da-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="913da-104">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> řízení vytvořit standardní nabídku.</span><span class="sxs-lookup"><span data-stu-id="913da-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="913da-105">Formulář také odpovědí, pokud uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="913da-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="913da-106">Následující úlohy jsou popsané v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="913da-106">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="913da-107">Vytvoření projektu modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="913da-107">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="913da-108">Vytvoření standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="913da-108">Creating a standard menu.</span></span>  
  
-   <span data-ttu-id="913da-109">Vytváření <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="913da-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
-   <span data-ttu-id="913da-110">Výběr položek nabídky zpracování.</span><span class="sxs-lookup"><span data-stu-id="913da-110">Handling menu item selection.</span></span>  
  
 <span data-ttu-id="913da-111">Jakmile budete hotovi, budete mít formulář s standardní nabídky, která zobrazuje výběr položek nabídky v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="913da-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 <span data-ttu-id="913da-112">Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: poskytování standardních položek nabídky do formuláře](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="913da-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="913da-113">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="913da-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="913da-114">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="913da-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="913da-115">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="913da-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="913da-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="913da-116">Prerequisites</span></span>  
 <span data-ttu-id="913da-117">K dokončení tohoto návodu, budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="913da-117">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="913da-118">Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="913da-118">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="913da-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="913da-119">Creating the Project</span></span>  
 <span data-ttu-id="913da-120">Prvním krokem je vytvoření projektu a nastavte formulář.</span><span class="sxs-lookup"><span data-stu-id="913da-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="913da-121">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="913da-121">To create the project</span></span>  
  
1.  <span data-ttu-id="913da-122">Vytvořte projekt aplikace Windows názvem **StandardMenuForm**.</span><span class="sxs-lookup"><span data-stu-id="913da-122">Create a Windows application project called **StandardMenuForm**.</span></span>  
  
     <span data-ttu-id="913da-123">Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="913da-123">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="913da-124">V Návrháři formulářů Windows vyberte formuláře.</span><span class="sxs-lookup"><span data-stu-id="913da-124">In the Windows Forms Designer, select the form.</span></span>  
  
## <a name="creating-a-standard-menu"></a><span data-ttu-id="913da-125">Vytvoření standardní nabídky</span><span class="sxs-lookup"><span data-stu-id="913da-125">Creating a Standard Menu</span></span>  
 <span data-ttu-id="913da-126">Návrhář formulářů Windows může automaticky vyplnit <xref:System.Windows.Forms.MenuStrip> ovládacího prvku pomocí standardních položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="913da-126">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>  
  
#### <a name="to-create-a-standard-menu"></a><span data-ttu-id="913da-127">Chcete-li vytvořit standardní nabídky</span><span class="sxs-lookup"><span data-stu-id="913da-127">To create a standard menu</span></span>  
  
1.  <span data-ttu-id="913da-128">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.MenuStrip> ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="913da-128">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>  
  
2.  <span data-ttu-id="913da-129">Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> glyfy inteligentní značky ovládacího prvku (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a vyberte **vložit standardní položky**.</span><span class="sxs-lookup"><span data-stu-id="913da-129">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>  
  
     <span data-ttu-id="913da-130"><xref:System.Windows.Forms.MenuStrip> Standardních položek nabídky se zobrazí v řízení.</span><span class="sxs-lookup"><span data-stu-id="913da-130">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>  
  
3.  <span data-ttu-id="913da-131">Klikněte **souboru** položku nabídky zobrazíte jeho výchozí položky nabídky a odpovídajících ikon.</span><span class="sxs-lookup"><span data-stu-id="913da-131">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>  
  
## <a name="creating-a-statusstrip-control"></a><span data-ttu-id="913da-132">Vytvoření ovládacího prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="913da-132">Creating a StatusStrip Control</span></span>  
 <span data-ttu-id="913da-133">Použití <xref:System.Windows.Forms.StatusStrip> ovládacího prvku pro zobrazení stavu pro aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="913da-133">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="913da-134">V aktuální příkladu jsou zobrazené položky nabídky vybraný uživatelem v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="913da-134">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
#### <a name="to-create-a-statusstrip-control"></a><span data-ttu-id="913da-135">Vytvoření ovládacího prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="913da-135">To create a StatusStrip control</span></span>  
  
1.  <span data-ttu-id="913da-136">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.StatusStrip> ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="913da-136">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>  
  
     <span data-ttu-id="913da-137"><xref:System.Windows.Forms.StatusStrip> Řízení automaticky ukotvené do dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="913da-137">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>  
  
2.  <span data-ttu-id="913da-138">Klikněte na tlačítko <xref:System.Windows.Forms.StatusStrip> tlačítko rozevíracího seznamu a vyberte ovládacího prvku **StatusLabel** přidat <xref:System.Windows.Forms.ToolStripStatusLabel> řídit k <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="913da-138">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="handling-item-selection"></a><span data-ttu-id="913da-139">Výběr položek zpracování</span><span class="sxs-lookup"><span data-stu-id="913da-139">Handling Item Selection</span></span>  
 <span data-ttu-id="913da-140">Zpracování <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událost, která má reagovat, když uživatel vybere položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="913da-140">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>  
  
#### <a name="to-handle-item-selection"></a><span data-ttu-id="913da-141">Pro zpracování výběr položek</span><span class="sxs-lookup"><span data-stu-id="913da-141">To handle item selection</span></span>  
  
1.  <span data-ttu-id="913da-142">Klikněte na tlačítko **souboru** položky nabídky, kterou jste vytvořili v části Vytvoření oddílu standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="913da-142">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>  
  
2.  <span data-ttu-id="913da-143">V **vlastnosti** okně klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="913da-143">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="913da-144">Dvakrát klikněte <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.</span><span class="sxs-lookup"><span data-stu-id="913da-144">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
     <span data-ttu-id="913da-145">Návrhář formulářů Windows generuje obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> událostí.</span><span class="sxs-lookup"><span data-stu-id="913da-145">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>  
  
4.  <span data-ttu-id="913da-146">Vložte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="913da-146">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  <span data-ttu-id="913da-147">Vložit `UpdateStatus` definici metody nástroj do formuláře.</span><span class="sxs-lookup"><span data-stu-id="913da-147">Insert the `UpdateStatus` utility method definition into the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a><span data-ttu-id="913da-148">Kontrolní bod</span><span class="sxs-lookup"><span data-stu-id="913da-148">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="913da-149">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="913da-149">To test your form</span></span>  
  
1.  <span data-ttu-id="913da-150">Stisknutím klávesy F5 zkompilování a spuštění svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="913da-150">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="913da-151">Klikněte **souboru** položku nabídky otevřete nabídku.</span><span class="sxs-lookup"><span data-stu-id="913da-151">Click the **File** menu item to open the menu.</span></span>  
  
3.  <span data-ttu-id="913da-152">Na **souboru** nabídky, klikněte na některou z položek vyberte.</span><span class="sxs-lookup"><span data-stu-id="913da-152">On the **File** menu, click one of the items to select it.</span></span>  
  
     <span data-ttu-id="913da-153"><xref:System.Windows.Forms.StatusStrip> Zobrazí vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="913da-153">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="913da-154">Další kroky</span><span class="sxs-lookup"><span data-stu-id="913da-154">Next Steps</span></span>  
 <span data-ttu-id="913da-155">V tomto návodu jste vytvořili formuláře s standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="913da-155">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="913da-156">Můžete použít <xref:System.Windows.Forms.ToolStrip> rodiny ovládacích prvků pro mnoho jiné účely:</span><span class="sxs-lookup"><span data-stu-id="913da-156">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="913da-157">Vytvořit místní nabídky pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="913da-157">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="913da-158">Další informace najdete v tématu [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="913da-158">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="913da-159">Vytvoření více formuláře rozhraní (MDI) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="913da-159">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="913da-160">Další informace najdete v tématu [návod: vytvoření formuláře MDI s Menu Merging a ToolStrip – ovládací prvky](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="913da-160">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
-   <span data-ttu-id="913da-161">Poskytnout vaše <xref:System.Windows.Forms.ToolStrip> profesionální vzhled ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="913da-161">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="913da-162">Další informace najdete v tématu [postupy: nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="913da-162">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913da-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="913da-163">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="913da-164">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="913da-164">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
