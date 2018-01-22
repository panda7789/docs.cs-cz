---
title: "Postupy: Otestování běhového chování UserControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48b7c47a14f27439c60280a5c4202e9f4af76397
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="8debb-102">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="8debb-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="8debb-103">Když budete vyvíjet <xref:System.Windows.Forms.UserControl>, je potřeba provést testování její chování.</span><span class="sxs-lookup"><span data-stu-id="8debb-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="8debb-104">Můžete vytvořit projekt samostatné aplikace systému Windows a umístěte ovládací prvek na formuláři testu, ale tento postup je nepohodlná.</span><span class="sxs-lookup"><span data-stu-id="8debb-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="8debb-105">Je rychlejší a jednodušší způsob použití **UserControl – kontejner testů** poskytované sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8debb-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="8debb-106">Tento kontejner testů spustí přímo z projektu knihovny ovládacího prvku systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8debb-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8debb-107">Pro kontejner testů načíst vaše <xref:System.Windows.Forms.UserControl>, ovládacího prvku musí mít alespoň jeden veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="8debb-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8debb-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="8debb-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8debb-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="8debb-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8debb-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8debb-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8debb-111">Visual C++ ovládacího prvku nelze testovat pomocí **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="8debb-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="8debb-112">K otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="8debb-112">To test the run-time behavior of a UserControl</span></span>  
  
1.  <span data-ttu-id="8debb-113">Vytvoření projektu knihovny ovládacího prvku Windows názvem **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="8debb-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="8debb-114">Podrobnosti najdete v tématu [šablona knihovny ovládacího prvku Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="8debb-114">For details, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="8debb-115">V **Návrhář formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Label> řídit z **sada nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8debb-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="8debb-116">Stiskněte klávesu F5, aby se projekt sestavil a spustit **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="8debb-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="8debb-117">Kontejner testů se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="8debb-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="8debb-118">Vyberte <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost zobrazena v <xref:System.Windows.Forms.PropertyGrid> řízení napravo **Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="8debb-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="8debb-119">Změnit jeho hodnotu na `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="8debb-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="8debb-120">Zkontrolujte, že ovládací prvek změny tmavší barva.</span><span class="sxs-lookup"><span data-stu-id="8debb-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="8debb-121">Zkuste změnit dalších hodnot vlastností a sledovat účinek na vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8debb-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5.  <span data-ttu-id="8debb-122">Klikněte **ukotvení vyplnění uživatelský ovládací prvek** zaškrtnutí políčka dole **Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="8debb-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="8debb-123">Sledujte, změně velikosti ovládacího prvku k vyplnění podokně.</span><span class="sxs-lookup"><span data-stu-id="8debb-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="8debb-124">Resize – kontejner testů a sledovat změně velikosti ovládacího prvku s podokně.</span><span class="sxs-lookup"><span data-stu-id="8debb-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6.  <span data-ttu-id="8debb-125">Zavřete testovací kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8debb-125">Close the test container.</span></span>  
  
7.  <span data-ttu-id="8debb-126">Přidat další uživatelský ovládací prvek na **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="8debb-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="8debb-127">Podrobnosti najdete v tématu [NIB: postupy: Přidání existujících položek do projektu](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="8debb-127">For details, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
8.  <span data-ttu-id="8debb-128">V **Návrhář formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8debb-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="8debb-129">Stisknutím klávesy F5 sestavte projekt a spusťte kontejner testů.</span><span class="sxs-lookup"><span data-stu-id="8debb-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="8debb-130">Klikněte **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="8debb-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="8debb-131">Testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="8debb-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="8debb-132">Uživatelské ovládací prvky z jiných projektů můžete otestovat v aktuálním projektu – kontejner testů.</span><span class="sxs-lookup"><span data-stu-id="8debb-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="8debb-133">K testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="8debb-133">To test user controls from another project</span></span>  
  
1.  <span data-ttu-id="8debb-134">Vytvoření projektu knihovny ovládacího prvku Windows názvem **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="8debb-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="8debb-135">Podrobnosti najdete v tématu [šablona knihovny ovládacího prvku Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="8debb-135">For details, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="8debb-136">V **Návrhář formulářů Windows**, přetáhněte <xref:System.Windows.Forms.RadioButton> řídit z **sada nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8debb-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="8debb-137">Stisknutím klávesy F5 sestavte projekt a spusťte kontejner testů.</span><span class="sxs-lookup"><span data-stu-id="8debb-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="8debb-138">Kontejner testů se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="8debb-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="8debb-139">Klikněte **zatížení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8debb-139">Click the **Load** button.</span></span>  
  
5.  <span data-ttu-id="8debb-140">V **otevřete** dialogové okno pole, přejděte na **TestContainerExample**.dll, který jste vytvořili v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="8debb-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="8debb-141">Vyberte **TestContainerExample**.dll a kliknutím **otevřete** tlačítko načíst uživatelské ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="8debb-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6.  <span data-ttu-id="8debb-142">Použití **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky z **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="8debb-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8debb-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="8debb-143">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="8debb-144">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="8debb-144">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="8debb-145">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="8debb-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="8debb-146">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="8debb-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="8debb-147">Uživatel Designer ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="8debb-147">User Control Designer</span></span>](http://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
