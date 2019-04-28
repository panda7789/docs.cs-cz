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
ms.openlocfilehash: 15b37c71e6643b588c0378510965a9a3e7cb56e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672572"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="64a22-102">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="64a22-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="64a22-103">Při vývoji <xref:System.Windows.Forms.UserControl>, je potřeba testovat jeho chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="64a22-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="64a22-104">Můžete vytvořit projekt samostatné aplikace pro systém Windows a umístit ovládací prvek na formuláři testu, ale tento postup je praktické.</span><span class="sxs-lookup"><span data-stu-id="64a22-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="64a22-105">Jednodušší a rychlejší způsob je použít **UserControl – kontejner testů** poskytovaný sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64a22-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="64a22-106">Tento kontejner testu spustí přímo z vašeho projektu knihovny ovládacích prvků Windows.</span><span class="sxs-lookup"><span data-stu-id="64a22-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64a22-107">Pro kontejner testu se načíst vaše <xref:System.Windows.Forms.UserControl>, ovládací prvek musí mít aspoň jeden veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="64a22-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64a22-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="64a22-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="64a22-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="64a22-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="64a22-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="64a22-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64a22-111">Ovládací prvek Visual C++ nelze provést test pomocí **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="64a22-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="64a22-112">K otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="64a22-112">To test the run-time behavior of a UserControl</span></span>  
  
1. <span data-ttu-id="64a22-113">Vytvoření projektu knihovny ovládacích prvků Windows volá **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="64a22-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="64a22-114">Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="64a22-114">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="64a22-115">V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Label> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="64a22-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="64a22-116">Stisknutím klávesy F5 projekt sestavit a spustit **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="64a22-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="64a22-117">Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="64a22-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="64a22-118">Vyberte <xref:System.Windows.Forms.Control.BackColor%2A> zobrazená v vlastnost <xref:System.Windows.Forms.PropertyGrid> ovládací prvek vpravo od **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="64a22-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="64a22-119">Změňte tuto hodnotu na `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="64a22-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="64a22-120">Podívejte se, že ovládací prvek změní tmavší barvu.</span><span class="sxs-lookup"><span data-stu-id="64a22-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="64a22-121">Zkuste změnit jiné hodnoty vlastností a sledujte vliv na váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="64a22-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5. <span data-ttu-id="64a22-122">Klikněte na tlačítko **Ukotvit výplň uživatelský ovládací prvek** zaškrtnutím políčka níže **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="64a22-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="64a22-123">Podívejte se, že ovládací prvek svou velikost tak, aby vyplnil podokna.</span><span class="sxs-lookup"><span data-stu-id="64a22-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="64a22-124">Změna velikosti kontejneru testů a podívejte se, že ovládací prvek svou velikost podokna.</span><span class="sxs-lookup"><span data-stu-id="64a22-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6. <span data-ttu-id="64a22-125">Zavřete kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="64a22-125">Close the test container.</span></span>  
  
7. <span data-ttu-id="64a22-126">Přidat jiný uživatelský ovládací prvek **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="64a22-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="64a22-127">Podrobnosti najdete v tématu [jak: Přidání existující položky do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="64a22-127">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>  
  
8. <span data-ttu-id="64a22-128">V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="64a22-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="64a22-129">Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="64a22-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="64a22-130">Klikněte na tlačítko **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="64a22-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="64a22-131">Testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="64a22-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="64a22-132">Uživatelské ovládací prvky z jiných projektů můžete otestovat v kontejneru testů aktuálního projektu.</span><span class="sxs-lookup"><span data-stu-id="64a22-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="64a22-133">K testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="64a22-133">To test user controls from another project</span></span>  
  
1. <span data-ttu-id="64a22-134">Vytvoření projektu knihovny ovládacích prvků Windows volá **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="64a22-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="64a22-135">Podrobnosti najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="64a22-135">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="64a22-136">V **Návrháře formulářů Windows**, přetáhněte <xref:System.Windows.Forms.RadioButton> ovládacího prvku **nástrojů** na návrhové ploše ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="64a22-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3. <span data-ttu-id="64a22-137">Stisknutím klávesy F5 projekt sestavit a spustit kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="64a22-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="64a22-138">Kontejner testu se zobrazí s vaší <xref:System.Windows.Forms.UserControl> v **ve verzi Preview** podokně.</span><span class="sxs-lookup"><span data-stu-id="64a22-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4. <span data-ttu-id="64a22-139">Klikněte na tlačítko **zatížení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="64a22-139">Click the **Load** button.</span></span>  
  
5. <span data-ttu-id="64a22-140">V **otevřít** dialogové okno, přejděte na **TestContainerExample**.dll, který jste vytvořili v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="64a22-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="64a22-141">Vyberte **TestContainerExample**.dll a kliknutím **otevřít** tlačítko načíst uživatelské ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="64a22-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6. <span data-ttu-id="64a22-142">Použití **vyberte uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> přepínat mezi dvěma uživatelské ovládací prvky z **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="64a22-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a22-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64a22-143">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="64a22-144">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="64a22-144">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="64a22-145">Návod: Vytvoření složeného ovládacího prvku s jazykem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64a22-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="64a22-146">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="64a22-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="64a22-147">[Návrhář uživatelského ovládacího prvku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64a22-147">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
