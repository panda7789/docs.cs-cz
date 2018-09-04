---
title: 'Postupy: Otestování běhového chování UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: 40ec136a86b52dcb007d15d5a2917212745961f2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512206"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="901d4-102">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="901d4-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="901d4-103">Při vývoji <xref:System.Windows.Forms.UserControl>, je potřeba testovat jeho chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="901d4-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="901d4-104">Můžete vytvořit projekt samostatné aplikace pro systém Windows a umístit ovládací prvek na formuláři testu, ale tento postup je praktické.</span><span class="sxs-lookup"><span data-stu-id="901d4-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="901d4-105">Jednodušší a rychlejší způsob je použít **UserControl – kontejner testů** poskytovaný sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="901d4-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="901d4-106">Tento kontejner testu spustí přímo z vašeho projektu knihovny ovládacích prvků Windows.</span><span class="sxs-lookup"><span data-stu-id="901d4-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="901d4-107">Pro kontejner testu se načíst vaše <xref:System.Windows.Forms.UserControl>, ovládací prvek musí mít aspoň jeden veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="901d4-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="901d4-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="901d4-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="901d4-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="901d4-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="901d4-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="901d4-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="901d4-111">Ovládací prvek Visual C++ nelze provést test pomocí **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="901d4-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="901d4-112">K otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="901d4-112">To test the run-time behavior of a UserControl</span></span>  
  
1.  <span data-ttu-id="901d4-113">Vytvoření projektu knihovny ovládacích prvků Windows volá **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="901d4-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="901d4-114">Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="901d4-114">For details, see [Windows Control Library Template](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="901d4-115">V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Label> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="901d4-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="901d4-116">Stisknutím klávesy F5 projekt sestavit a spustit **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="901d4-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="901d4-117">Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="901d4-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="901d4-118">Vyberte <xref:System.Windows.Forms.Control.BackColor%2A> zobrazená v vlastnost <xref:System.Windows.Forms.PropertyGrid> ovládací prvek vpravo od **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="901d4-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="901d4-119">Změňte tuto hodnotu na `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="901d4-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="901d4-120">Podívejte se, že ovládací prvek změní tmavší barvu.</span><span class="sxs-lookup"><span data-stu-id="901d4-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="901d4-121">Zkuste změnit jiné hodnoty vlastností a sledujte vliv na váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="901d4-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5.  <span data-ttu-id="901d4-122">Klikněte na tlačítko **Ukotvit výplň uživatelský ovládací prvek** zaškrtnutím políčka níže **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="901d4-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="901d4-123">Podívejte se, že ovládací prvek svou velikost tak, aby vyplnil podokna.</span><span class="sxs-lookup"><span data-stu-id="901d4-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="901d4-124">Změna velikosti kontejneru testů a podívejte se, že ovládací prvek svou velikost podokna.</span><span class="sxs-lookup"><span data-stu-id="901d4-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6.  <span data-ttu-id="901d4-125">Zavřete kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="901d4-125">Close the test container.</span></span>  
  
7.  <span data-ttu-id="901d4-126">Přidat jiný uživatelský ovládací prvek **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="901d4-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="901d4-127">Podrobnosti najdete v tématu [NIB: postupy: Přidání existující položky do projektu](https://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="901d4-127">For details, see [NIB:How to: Add Existing Items to a Project](https://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
8.  <span data-ttu-id="901d4-128">V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="901d4-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="901d4-129">Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="901d4-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="901d4-130">Klikněte na tlačítko **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="901d4-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="901d4-131">Testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="901d4-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="901d4-132">Uživatelské ovládací prvky z jiných projektů můžete otestovat v kontejneru testů aktuálního projektu.</span><span class="sxs-lookup"><span data-stu-id="901d4-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="901d4-133">K testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="901d4-133">To test user controls from another project</span></span>  
  
1.  <span data-ttu-id="901d4-134">Vytvoření projektu knihovny ovládacích prvků Windows volá **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="901d4-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="901d4-135">Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="901d4-135">For details, see [Windows Control Library Template](https://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="901d4-136">V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.RadioButton> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="901d4-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="901d4-137">Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="901d4-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="901d4-138">Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="901d4-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="901d4-139">Klikněte na tlačítko **zatížení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="901d4-139">Click the **Load** button.</span></span>  
  
5.  <span data-ttu-id="901d4-140">V **otevřít** dialogové okno, přejděte na **TestContainerExample**.dll, který jste vytvořili v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="901d4-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="901d4-141">Vyberte **TestContainerExample**.dll a kliknutím **otevřít** tlačítko načíst uživatelské ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="901d4-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6.  <span data-ttu-id="901d4-142">Použití **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky z **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="901d4-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901d4-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="901d4-143">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="901d4-144">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="901d4-144">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="901d4-145">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="901d4-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="901d4-146">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="901d4-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="901d4-147">Návrhář uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="901d4-147">User Control Designer</span></span>](https://msdn.microsoft.com/library/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
