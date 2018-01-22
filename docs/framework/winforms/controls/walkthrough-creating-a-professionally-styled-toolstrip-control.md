---
title: "Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab9adb72a174da25298b6ea104b002914de0cc40
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="d9073-102">Návod: Vytvoření ovládacího prvku ToolStrip s profesionálním vzhledem</span><span class="sxs-lookup"><span data-stu-id="d9073-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="d9073-103">Aplikace můžete udělit <xref:System.Windows.Forms.ToolStrip> řídí profesionální vzhled a chování vytvořením vlastní třídy odvozené od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="d9073-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="d9073-104">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.ToolStrip> ovládací prvky pro vytvoření složeného ovládacího prvku, který vypadá takto: **navigačním podokně** poskytované Microsoft® Outlook®.</span><span class="sxs-lookup"><span data-stu-id="d9073-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="d9073-105">Následující úlohy jsou popsané v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="d9073-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="d9073-106">Vytvoření projektu knihovny ovládacích prvků Windows.</span><span class="sxs-lookup"><span data-stu-id="d9073-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="d9073-107">Návrh StackView ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="d9073-108">Implementace vlastní zobrazovací jednotky.</span><span class="sxs-lookup"><span data-stu-id="d9073-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="d9073-109">Jakmile budete hotovi, budete mít opakovaně použitelné vlastní ovládací prvek s profesionální vzhled ovládacího prvku Microsoft Office® XP.</span><span class="sxs-lookup"><span data-stu-id="d9073-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="d9073-110">Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: vytvoření profesionálním ve ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="d9073-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9073-111">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="d9073-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d9073-112">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d9073-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d9073-113">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d9073-113">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d9073-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9073-114">Prerequisites</span></span>  
 <span data-ttu-id="d9073-115">K dokončení tohoto návodu, budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="d9073-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="d9073-116">Abyste mohli vytvářet a spouštět projekty aplikací Windows Forms v počítači dostatečná oprávnění kde [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] je nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="d9073-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="d9073-117">Vytvoření projektu knihovny ovládacího prvku systému Windows</span><span class="sxs-lookup"><span data-stu-id="d9073-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="d9073-118">Prvním krokem je vytvoření projektu knihovny ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="d9073-119">Vytvoření projektu knihovny ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d9073-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="d9073-120">Vytvoření nového projektu knihovny ovládacích prvků Windows s názvem `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="d9073-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="d9073-121">V **Průzkumníku**, odstraňte výchozí řízení projektu odstraněním zdrojového souboru s názvem "UserControl1.cs" nebo "UserControl1.vb", v závislosti na vámi zvolený jazyk.</span><span class="sxs-lookup"><span data-stu-id="d9073-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="d9073-122">Další informace najdete v tématu [NIB: postupy: odebrání, odstranění a vyloučit položky](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="d9073-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="d9073-123">Přidejte nový <xref:System.Windows.Forms.UserControl> položkou **StackViewLibrary** projektu.</span><span class="sxs-lookup"><span data-stu-id="d9073-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="d9073-124">Zadejte základní název nové zdrojový soubor `StackView`.</span><span class="sxs-lookup"><span data-stu-id="d9073-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="d9073-125">Navrhování StackView ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d9073-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="d9073-126">`StackView` Ovládací prvek je složeného ovládacího prvku pomocí jednu podřízenou <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="d9073-127">Další informace o složené ovládací prvky najdete v tématu [typy vlastní prvky](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d9073-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="d9073-128">Při návrhu StackView ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d9073-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="d9073-129">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.ToolStrip> ovládacího prvku na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="d9073-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="d9073-130">V **vlastnosti** nastavte <xref:System.Windows.Forms.ToolStrip> vlastností ovládacího prvku podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="d9073-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="d9073-131">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d9073-131">Property</span></span>|<span data-ttu-id="d9073-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d9073-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d9073-133">Název</span><span class="sxs-lookup"><span data-stu-id="d9073-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="d9073-134">CanOverflow –</span><span class="sxs-lookup"><span data-stu-id="d9073-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="d9073-135">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="d9073-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="d9073-136">Písma</span><span class="sxs-lookup"><span data-stu-id="d9073-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="d9073-137">GripStyle.</span><span class="sxs-lookup"><span data-stu-id="d9073-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="d9073-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="d9073-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="d9073-139">Odsazení</span><span class="sxs-lookup"><span data-stu-id="d9073-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="d9073-140">RenderMode –</span><span class="sxs-lookup"><span data-stu-id="d9073-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="d9073-141">V Návrháři formulářů Windows, klikněte na <xref:System.Windows.Forms.ToolStrip> ovládacího prvku **přidat** tlačítko a přidejte <xref:System.Windows.Forms.ToolStripButton> k `stackStrip` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="d9073-142">V **vlastnosti** nastavte <xref:System.Windows.Forms.ToolStripButton> vlastností ovládacího prvku podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="d9073-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="d9073-143">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d9073-143">Property</span></span>|<span data-ttu-id="d9073-144">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d9073-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="d9073-145">Název</span><span class="sxs-lookup"><span data-stu-id="d9073-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="d9073-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="d9073-146">CheckOnClick</span></span>|<span data-ttu-id="d9073-147">true</span><span class="sxs-lookup"><span data-stu-id="d9073-147">true</span></span>|  
    |<span data-ttu-id="d9073-148">CheckState</span><span class="sxs-lookup"><span data-stu-id="d9073-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="d9073-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="d9073-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="d9073-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="d9073-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="d9073-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="d9073-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="d9073-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="d9073-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="d9073-153">Okraj</span><span class="sxs-lookup"><span data-stu-id="d9073-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="d9073-154">Odsazení</span><span class="sxs-lookup"><span data-stu-id="d9073-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="d9073-155">Text</span><span class="sxs-lookup"><span data-stu-id="d9073-155">Text</span></span>|<span data-ttu-id="d9073-156">**E-mailu**</span><span class="sxs-lookup"><span data-stu-id="d9073-156">**Mail**</span></span>|  
    |<span data-ttu-id="d9073-157">Zarovnání textu</span><span class="sxs-lookup"><span data-stu-id="d9073-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="d9073-158">Opakujte krok 7 pro tři další <xref:System.Windows.Forms.ToolStripButton> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d9073-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="d9073-159">Ovládací prvky pojmenovat `calendarStackButton`, `contactsStackButton`, a `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="d9073-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="d9073-160">Nastavte hodnotu <xref:System.Windows.Forms.Control.Text%2A> vlastnost **kalendáře**, **kontakty**, a **úlohy**, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d9073-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="d9073-161">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="d9073-161">Handling Events</span></span>  
 <span data-ttu-id="d9073-162">Dvě události jsou důležité, aby `StackView` řízení chovat správně.</span><span class="sxs-lookup"><span data-stu-id="d9073-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="d9073-163">Zpracování <xref:System.Windows.Forms.UserControl.Load> událost, která má správně umístění ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="d9073-164">Zpracování <xref:System.Windows.Forms.ToolStripItem.Click> událost pro každou <xref:System.Windows.Forms.ToolStripButton> umožnit `StackView` řídit chování stavu podobně jako <xref:System.Windows.Forms.RadioButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="d9073-165">Zpracování událostí</span><span class="sxs-lookup"><span data-stu-id="d9073-165">To handle events</span></span>  
  
1.  <span data-ttu-id="d9073-166">V Návrháři formulářů Windows, vyberte `StackView` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="d9073-167">V **vlastnosti** okně klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="d9073-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="d9073-168">Dvakrát klikněte na událost zatížení ke generování `StackView_Load` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d9073-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="d9073-169">V `StackView_Load` obslužné rutiny události, zkopírujte a vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="d9073-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="d9073-170">V Návrháři formulářů Windows, vyberte `mailStackButton` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="d9073-171">V **vlastnosti** okně klikněte na tlačítko **události**.</span><span class="sxs-lookup"><span data-stu-id="d9073-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="d9073-172">Dvakrát klikněte na událost Click.</span><span class="sxs-lookup"><span data-stu-id="d9073-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="d9073-173">Návrhář formulářů Windows generuje `mailStackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d9073-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="d9073-174">Přejmenujte `mailStackButton_Click` obslužné rutiny události pro `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="d9073-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="d9073-175">Další informace najdete v tématu [postupy: přejmenování identifikátor (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span><span class="sxs-lookup"><span data-stu-id="d9073-175">For more information, see [How to: Rename an Identifier (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="d9073-176">Vložte následující kód do `stackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d9073-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="d9073-177">V Návrháři formulářů Windows, vyberte `calendarStackButton` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="d9073-178">V **vlastnosti** okně nastavení klikněte na tlačítko událostí `stackButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d9073-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="d9073-179">Opakujte kroky 10 a 11 pro `contactsStackButton` a `tasksStackButton` ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d9073-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="d9073-180">Definování ikony</span><span class="sxs-lookup"><span data-stu-id="d9073-180">Defining Icons</span></span>  
 <span data-ttu-id="d9073-181">Každý `StackView` tlačítko obsahuje přidružené ikonu.</span><span class="sxs-lookup"><span data-stu-id="d9073-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="d9073-182">Pro usnadnění práce, každá ikona je reprezentována jako řetězec s kódováním base64, pomocí kterého se deserializovat před <xref:System.Drawing.Bitmap> se vytvoří z něj.</span><span class="sxs-lookup"><span data-stu-id="d9073-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="d9073-183">V produkčním prostředí ukládat data bitmapy jako prostředek a ikon v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="d9073-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="d9073-184">Další informace najdete v tématu [postupy: Přidání obrázky na pozadí do Windows Forms](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span><span class="sxs-lookup"><span data-stu-id="d9073-184">For more information, see [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="d9073-185">K definování ikony</span><span class="sxs-lookup"><span data-stu-id="d9073-185">To define icons</span></span>  
  
1.  <span data-ttu-id="d9073-186">V editoru kódu vložte následující kód do `StackView` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d9073-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="d9073-187">Inicializuje bitmap pro tento kód <xref:System.Windows.Forms.ToolStripButton> ikony.</span><span class="sxs-lookup"><span data-stu-id="d9073-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="d9073-188">Přidejte volání `InitializeImages` metoda v `StackView` konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="d9073-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="d9073-189">Implementace vlastní zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="d9073-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="d9073-190">Můžete přizpůsobit většinu prvků `StackView` řízení Moje implementace třídu odvozenou z <xref:System.Windows.Forms.ToolStripRenderer> – třída.</span><span class="sxs-lookup"><span data-stu-id="d9073-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="d9073-191">V tomto postupu budete implementovat <xref:System.Windows.Forms.ToolStripProfessionalRenderer> třídu, která se přizpůsobí úchytu a nevykresluje barevného přechodu pozadí pro <xref:System.Windows.Forms.ToolStripButton> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d9073-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="d9073-192">Chcete-li implementovat vlastní zobrazovací jednotky</span><span class="sxs-lookup"><span data-stu-id="d9073-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="d9073-193">Vložte následující kód do `StackView` definici ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d9073-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="d9073-194">Toto je definice `StackRenderer` třídy, která přepisuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, a <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody pro vytvoření vlastní vzhled.</span><span class="sxs-lookup"><span data-stu-id="d9073-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="d9073-195">V `StackView` konstruktoru ovládacího prvku, vytvořte novou instanci třídy `StackRenderer` třídy a přiřazení této instance `stackStrip` ovládacího prvku <xref:System.Windows.Forms.ToolStrip.Renderer%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d9073-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="d9073-196">Testování StackView ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d9073-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="d9073-197">`StackView` Ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídy.</span><span class="sxs-lookup"><span data-stu-id="d9073-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="d9073-198">Proto můžete otestovat pomocí ovládacího prvku **UserControl Test kontejneru**.</span><span class="sxs-lookup"><span data-stu-id="d9073-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="d9073-199">Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="d9073-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="d9073-200">Testování StackView ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d9073-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="d9073-201">Stiskněte klávesu F5, aby se projekt sestavil a spustit **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="d9073-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="d9073-202">Přesuňte ukazatel myši tlačítek `StackView` řízení a potom klikněte na tlačítko zobrazit vzhled vybraném stavu.</span><span class="sxs-lookup"><span data-stu-id="d9073-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d9073-203">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d9073-203">Next Steps</span></span>  
 <span data-ttu-id="d9073-204">V tomto návodu jste vytvořili vlastní opakovaně použitelné ovládací prvek s profesionální vzhled ovládacího prvku Office XP.</span><span class="sxs-lookup"><span data-stu-id="d9073-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="d9073-205">Můžete použít <xref:System.Windows.Forms.ToolStrip> rodiny ovládacích prvků pro mnoho jiné účely:</span><span class="sxs-lookup"><span data-stu-id="d9073-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="d9073-206">Vytvořit místní nabídky pro vaše ovládací prvky s <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="d9073-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="d9073-207">Další informace najdete v tématu [ContextMenu – přehled komponenty](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d9073-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="d9073-208">Vytvořte formulář s automaticky zadané standardní nabídku.</span><span class="sxs-lookup"><span data-stu-id="d9073-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="d9073-209">Další informace najdete v tématu [návod: poskytnutí standardních položek nabídky do formuláře](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="d9073-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="d9073-210">Vytvoření více formuláře rozhraní (MDI) dokumentu s ukotvení <xref:System.Windows.Forms.ToolStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d9073-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="d9073-211">Další informace najdete v tématu [postupy: vytvoření formuláře MDI s Menu Merging a ToolStrip – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d9073-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9073-212">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9073-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="d9073-213">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d9073-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="d9073-214">Postupy: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="d9073-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
