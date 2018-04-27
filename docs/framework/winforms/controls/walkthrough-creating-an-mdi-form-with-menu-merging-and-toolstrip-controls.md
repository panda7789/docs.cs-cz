---
title: 'Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip'
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
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc8214815beb0eac6fe3811ba198207a06ee1a9a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="77712-102">Návod: Vytvoření formuláře MDI se slučováním nabídek a s ovládacími prvky ToolStrip</span><span class="sxs-lookup"><span data-stu-id="77712-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="77712-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů podporuje více aplikací rozhraní (MDI) dokumentu a <xref:System.Windows.Forms.MenuStrip> řízení podporuje slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="77712-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="77712-104">MDI formuláře může taky <xref:System.Windows.Forms.ToolStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="77712-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="77712-105">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků pomocí formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="77712-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="77712-106">Formulář podporuje také s nabídkami podřízené slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="77712-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="77712-107">Následující úlohy jsou popsané v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="77712-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="77712-108">Vytvoření projektu modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="77712-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="77712-109">Vytváření hlavní nabídky pro formulář.</span><span class="sxs-lookup"><span data-stu-id="77712-109">Creating the main menu for your form.</span></span> <span data-ttu-id="77712-110">Skutečný název nabídky se budou lišit.</span><span class="sxs-lookup"><span data-stu-id="77712-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="77712-111">Přidávání <xref:System.Windows.Forms.ToolStripPanel> řídit k **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="77712-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="77712-112">Vytvoření podřízené formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="77712-113">Uspořádání <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky podle pořadí z-order.</span><span class="sxs-lookup"><span data-stu-id="77712-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="77712-114">Jakmile budete hotovi, budete mít formuláře MDI, který podporuje slučování nabídek a movable <xref:System.Windows.Forms.ToolStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="77712-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="77712-115">Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: vytvoření formuláře MDI s Menu Merging a ToolStrip – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="77712-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77712-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="77712-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="77712-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="77712-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="77712-118">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="77712-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="77712-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77712-119">Prerequisites</span></span>  
 <span data-ttu-id="77712-120">K dokončení tohoto návodu, budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="77712-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="77712-121">Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77712-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="77712-122">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="77712-122">Creating the Project</span></span>  
 <span data-ttu-id="77712-123">Prvním krokem je vytvoření projektu a nastavte formulář.</span><span class="sxs-lookup"><span data-stu-id="77712-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="77712-124">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="77712-124">To create the project</span></span>  
  
1.  <span data-ttu-id="77712-125">Vytvořte projekt aplikace Windows názvem **MdiForm**.</span><span class="sxs-lookup"><span data-stu-id="77712-125">Create a Windows Application project called **MdiForm**.</span></span>  
  
     <span data-ttu-id="77712-126">Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="77712-126">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="77712-127">V Návrháři formulářů Windows vyberte formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-127">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="77712-128">V okně vlastností nastavte hodnotu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="77712-128">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="77712-129">Vytváření z hlavní nabídky</span><span class="sxs-lookup"><span data-stu-id="77712-129">Creating the Main Menu</span></span>  
 <span data-ttu-id="77712-130">Nadřazené formuláře MDI obsahuje hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="77712-130">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="77712-131">V hlavní nabídce má jedna položka nabídky s názvem **okno**.</span><span class="sxs-lookup"><span data-stu-id="77712-131">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="77712-132">Pomocí **okno** položky nabídky, můžete vytvořit podřízených formulářů.</span><span class="sxs-lookup"><span data-stu-id="77712-132">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="77712-133">Položky nabídky z podřízených formulářů jsou sloučeny do hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="77712-133">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="77712-134">Chcete-li vytvořit v hlavní nabídce</span><span class="sxs-lookup"><span data-stu-id="77712-134">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="77712-135">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.MenuStrip> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="77712-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="77712-136">Přidat <xref:System.Windows.Forms.ToolStripMenuItem> k <xref:System.Windows.Forms.MenuStrip> řízení a pojmenujte ji **okno**.</span><span class="sxs-lookup"><span data-stu-id="77712-136">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="77712-137">Vyberte <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77712-137">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="77712-138">V okně vlastností nastavte hodnotu <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="77712-138">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="77712-139">Přidat podřízenou položku k **okno** položky nabídky a potom název podpoložek **nový**.</span><span class="sxs-lookup"><span data-stu-id="77712-139">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="77712-140">V okně vlastností klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="77712-140">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="77712-141">Dvakrát klikněte <xref:System.Windows.Forms.ToolStripItem.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="77712-141">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="77712-142">Návrhář formulářů Windows generuje obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="77712-142">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="77712-143">Vložte následující kód do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="77712-143">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="77712-144">Přidání ovládacího prvku ToolStripPanel do sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="77712-144">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="77712-145">Při použití <xref:System.Windows.Forms.MenuStrip> ovládacích prvků pomocí formuláře MDI musí mít <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77712-145">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="77712-146">Je nutné přidat <xref:System.Windows.Forms.ToolStripPanel> řídit k **sada nástrojů** k vytvoření formuláře MDI v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="77712-146">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="77712-147">Přidání ovládacího prvku ToolStripPanel do sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="77712-147">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="77712-148">Otevřete **sada nástrojů**a pak klikněte na tlačítko **všechny formuláře Windows** zobrazte dostupné ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="77712-148">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="77712-149">Klikněte pravým tlačítkem myši a místní nabídce a vyberte **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="77712-149">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="77712-150">V **výběr položek sady nástrojů** dialogové okno, přejděte dolů **název** sloupce vyhledejte **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="77712-150">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="77712-151">Zaškrtněte políčko podle **ToolStripPanel**a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="77712-151">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="77712-152"><xref:System.Windows.Forms.ToolStripPanel> Zobrazí ovládací prvek v **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="77712-152">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="77712-153">Vytvoření podřízené formuláře</span><span class="sxs-lookup"><span data-stu-id="77712-153">Creating a Child Form</span></span>  
 <span data-ttu-id="77712-154">V tomto postupu bude definovat samostatnou podřízenou formuláře třídy, která má svou vlastní <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77712-154">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="77712-155">Položky nabídky pro tento formulář jsou sloučeny s těmi, která nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-155">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="77712-156">Chcete-li definovat podřízené formuláře</span><span class="sxs-lookup"><span data-stu-id="77712-156">To define a child form</span></span>  
  
1.  <span data-ttu-id="77712-157">Přidejte nový formulář s názvem `ChildForm` do projektu.</span><span class="sxs-lookup"><span data-stu-id="77712-157">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="77712-158">Další informace najdete v tématu [postupy: Přidání Windows Forms do projektu](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="77712-158">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="77712-159">Z **sada nástrojů**, přetáhněte <xref:System.Windows.Forms.MenuStrip> na formuláři podřízený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="77712-159">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="77712-160">Klikněte na tlačítko <xref:System.Windows.Forms.MenuStrip> glyfy inteligentní značky ovládacího prvku (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) a potom vyberte **upravit položky**.</span><span class="sxs-lookup"><span data-stu-id="77712-160">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="77712-161">V **Editor kolekce položek** dialogové okno pole, přidejte nový <xref:System.Windows.Forms.ToolStripMenuItem> s názvem **ChildMenuItem** do nabídky podřízené.</span><span class="sxs-lookup"><span data-stu-id="77712-161">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="77712-162">Další informace najdete v tématu [Editor kolekce položek ToolStrip](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span><span class="sxs-lookup"><span data-stu-id="77712-162">For more information, see [ToolStrip Items Collection Editor](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="77712-163">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="77712-163">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="77712-164">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="77712-164">To test your form</span></span>  
  
1.  <span data-ttu-id="77712-165">Stisknutím klávesy F5 zkompilování a spuštění svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-165">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="77712-166">Klikněte **okno** otevřete nabídku a pak klikněte na položku nabídky **nový**.</span><span class="sxs-lookup"><span data-stu-id="77712-166">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="77712-167">V klientské oblasti formuláře MDI se vytvoří nový formulář podřízené.</span><span class="sxs-lookup"><span data-stu-id="77712-167">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="77712-168">Podřízené formuláře nabídky je sloučen s v hlavní nabídce.</span><span class="sxs-lookup"><span data-stu-id="77712-168">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="77712-169">Podřízené formulář zavřete.</span><span class="sxs-lookup"><span data-stu-id="77712-169">Close the child form.</span></span>  
  
     <span data-ttu-id="77712-170">Podřízené formuláře nabídky se odebere z hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="77712-170">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="77712-171">Klikněte na tlačítko **nový** několikrát.</span><span class="sxs-lookup"><span data-stu-id="77712-171">Click **New** several times.</span></span>  
  
     <span data-ttu-id="77712-172">Podřízené formuláře jsou automaticky uvedené v části olit**ipomenutí** položky nabídky, protože <xref:System.Windows.Forms.MenuStrip> ovládacího prvku <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> vlastnost je přiřazen.</span><span class="sxs-lookup"><span data-stu-id="77712-172">The child forms are automatically listed under the W**indow** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="77712-173">Přidání podpory ToolStrip</span><span class="sxs-lookup"><span data-stu-id="77712-173">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="77712-174">V tomto postupu budete přidávat čtyři <xref:System.Windows.Forms.ToolStrip> ovládacích prvků formuláře MDI nadřazené.</span><span class="sxs-lookup"><span data-stu-id="77712-174">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="77712-175">Každý <xref:System.Windows.Forms.ToolStrip> ovládací prvek přidán uvnitř <xref:System.Windows.Forms.ToolStripPanel> řízení, které je ukotvena hrany formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-175">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="77712-176">Přidání ovládacích prvků ToolStrip do nadřazeného formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="77712-176">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="77712-177">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.ToolStripPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="77712-177">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="77712-178">S <xref:System.Windows.Forms.ToolStripPanel> vybraný ovládací prvek, dvakrát klikněte <xref:System.Windows.Forms.ToolStrip> řídit ve **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="77712-178">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="77712-179">A <xref:System.Windows.Forms.ToolStrip> ovládací prvek je vytvořen v <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77712-179">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="77712-180">Vyberte <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77712-180">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="77712-181">V okně vlastností změňte hodnotu ovládacího prvku <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="77712-181">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="77712-182"><xref:System.Windows.Forms.ToolStripPanel> Řízení přepraviště na levé straně formuláře, pod v hlavní nabídce.</span><span class="sxs-lookup"><span data-stu-id="77712-182">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="77712-183">Klientské oblasti MDI přizpůsobí <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77712-183">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="77712-184">Opakujte kroky 1 až 4.</span><span class="sxs-lookup"><span data-stu-id="77712-184">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="77712-185">Ukotvení – nové <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do horní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-185">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="77712-186"><xref:System.Windows.Forms.ToolStripPanel> Řízení ukotven pod hlavní nabídky, ale napravo od první <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77712-186">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="77712-187">Tento krok ukazuje význam pořadí z-order v správně umístění <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="77712-187">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="77712-188">Opakujte kroky 1 až 4 pro dva další <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="77712-188">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="77712-189">Ukotvení – nové <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky vpravo a dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-189">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="77712-190">Uspořádání ovládacích prvků ToolStripPanel podle pořadí Z-order</span><span class="sxs-lookup"><span data-stu-id="77712-190">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="77712-191">Pozice ukotveného <xref:System.Windows.Forms.ToolStripPanel> ovládacím prvku formuláře MDI je určen podle umístění ovládacího prvku v pořadí.</span><span class="sxs-lookup"><span data-stu-id="77712-191">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="77712-192">Můžete snadno uspořádat pořadí vykreslování ovládacích prvků v okně Osnova dokumentu.</span><span class="sxs-lookup"><span data-stu-id="77712-192">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="77712-193">Chcete-li uspořádat ovládací prvky ToolStripPanel podle pořadí Z-order</span><span class="sxs-lookup"><span data-stu-id="77712-193">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="77712-194">V **zobrazení** nabídky, klikněte na tlačítko **ostatní okna**a potom klikněte na **Osnova dokumentu**.</span><span class="sxs-lookup"><span data-stu-id="77712-194">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="77712-195">Uspořádání vaší <xref:System.Windows.Forms.ToolStripPanel> je nestandardní ovládací prvky v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="77712-195">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="77712-196">Je to proto, že pořadí z-order není správná.</span><span class="sxs-lookup"><span data-stu-id="77712-196">This is because the z-order is not correct.</span></span> <span data-ttu-id="77712-197">Chcete-li změnit pořadí vykreslování ovládacích prvků použijte okno Osnova dokumentu.</span><span class="sxs-lookup"><span data-stu-id="77712-197">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="77712-198">V okně Osnova dokumentu vyberte **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="77712-198">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="77712-199">Klikněte na tlačítko šipky dolů opakovaně, dokud **ToolStripPanel4** je v dolní části seznamu.</span><span class="sxs-lookup"><span data-stu-id="77712-199">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="77712-200">**ToolStripPanel4** řízení ukotven v dolní části formuláře pod ostatní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="77712-200">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="77712-201">Vyberte **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="77712-201">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="77712-202">Klikněte na tlačítko šipky dolů jednou na třetí umístění ovládacího prvku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="77712-202">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="77712-203">**ToolStripPanel2** řízení ukotven k horní části formuláře, pod v hlavní nabídce a vyšší jiných ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="77712-203">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="77712-204">Vyberte různé ovládacích prvků v **Osnova dokumentu** okno a přesuňte je na jiná místa v pořadí.</span><span class="sxs-lookup"><span data-stu-id="77712-204">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="77712-205">Všimněte si vliv pořadí z-order na umístění ukotvených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="77712-205">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="77712-206">Pomocí kombinace kláves CTRL-Z nebo **vrátit zpět** na **upravit** nabídky vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="77712-206">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="77712-207">Kontrolní bod</span><span class="sxs-lookup"><span data-stu-id="77712-207">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="77712-208">Testování formuláře</span><span class="sxs-lookup"><span data-stu-id="77712-208">To test your form</span></span>  
  
1.  <span data-ttu-id="77712-209">Stisknutím klávesy F5 zkompilování a spuštění svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="77712-209">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="77712-210">Klikněte na tlačítko úchytu z <xref:System.Windows.Forms.ToolStrip> řízení a přetáhněte ovládací prvek na formuláři na jiné místo.</span><span class="sxs-lookup"><span data-stu-id="77712-210">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="77712-211">Můžete přetáhnout <xref:System.Windows.Forms.ToolStrip> ovládacího prvku z jedné <xref:System.Windows.Forms.ToolStripPanel> ovládacího prvku do jiného.</span><span class="sxs-lookup"><span data-stu-id="77712-211">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="77712-212">Další kroky</span><span class="sxs-lookup"><span data-stu-id="77712-212">Next Steps</span></span>  
 <span data-ttu-id="77712-213">V tomto návodu jste vytvořili nadřazené formuláře MDI s <xref:System.Windows.Forms.ToolStrip> ovládací prvky a slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="77712-213">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="77712-214">Můžete použít <xref:System.Windows.Forms.ToolStrip> rodiny ovládacích prvků pro mnoho jiné účely:</span><span class="sxs-lookup"><span data-stu-id="77712-214">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="77712-215">Vytvořit místní nabídky pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="77712-215">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="77712-216">Další informace najdete v tématu [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="77712-216">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="77712-217">Vytvořit formulář se automaticky zadané standardní nabídku.</span><span class="sxs-lookup"><span data-stu-id="77712-217">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="77712-218">Další informace najdete v tématu [návod: poskytnutí standardních položek nabídky do formuláře](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="77712-218">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="77712-219">Poskytnout vaše <xref:System.Windows.Forms.ToolStrip> profesionální vzhled ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="77712-219">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="77712-220">Další informace najdete v tématu [postupy: nastavení vykreslovacího modulu prvku ToolStrip pro aplikaci](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="77712-220">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77712-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="77712-221">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="77712-222">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="77712-222">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="77712-223">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="77712-223">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="77712-224">Postupy: Vložení prvku MenuStrip do rozevíracího seznamu MDI</span><span class="sxs-lookup"><span data-stu-id="77712-224">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="77712-225">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="77712-225">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
