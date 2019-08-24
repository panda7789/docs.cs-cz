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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015768"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="c62bf-102">Postupy: Testování chování prvku UserControl v době běhu</span><span class="sxs-lookup"><span data-stu-id="c62bf-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="c62bf-103">Při vývoji <xref:System.Windows.Forms.UserControl>nástroje je nutné otestovat jeho chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="c62bf-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="c62bf-104">Můžete vytvořit samostatný projekt aplikace pro systém Windows a umístit ovládací prvek do formuláře testu, ale tato procedura je nepraktická.</span><span class="sxs-lookup"><span data-stu-id="c62bf-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="c62bf-105">Rychlejší a snazší způsob použití **kontejneru testu UserControl** , který poskytuje Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c62bf-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="c62bf-106">Tento kontejner testů začíná přímo z projektu knihovny ovládacích prvků systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c62bf-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c62bf-107">Aby mohl kontejner testu načíst svůj <xref:System.Windows.Forms.UserControl>ovládací prvek, musí mít alespoň jeden veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c62bf-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="c62bf-108">Vizuální C++ ovládací prvek nelze testovat pomocí **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="c62bf-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="c62bf-109">Testování chování prvku UserControl v době běhu</span><span class="sxs-lookup"><span data-stu-id="c62bf-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="c62bf-110">V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="c62bf-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="c62bf-111">V **Návrhář formulářů**přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek z **panelu nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c62bf-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="c62bf-112">Stisknutím klávesy **F5** Sestavte projekt a spusťte **kontejner testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="c62bf-112">Press **F5** to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="c62bf-113">Kontejner testu se zobrazí <xref:System.Windows.Forms.UserControl> v podokně **náhledu** .</span><span class="sxs-lookup"><span data-stu-id="c62bf-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="c62bf-114">Vyberte vlastnost zobrazenou <xref:System.Windows.Forms.PropertyGrid> v ovládacím prvku napravo od podokna **náhledu.** <xref:System.Windows.Forms.Control.BackColor%2A></span><span class="sxs-lookup"><span data-stu-id="c62bf-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="c62bf-115">Změňte její hodnotu na **ControlDark**.</span><span class="sxs-lookup"><span data-stu-id="c62bf-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="c62bf-116">Pozor, aby se ovládací prvek změnil na tmavší barvu.</span><span class="sxs-lookup"><span data-stu-id="c62bf-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="c62bf-117">Zkuste změnit další hodnoty vlastností a sledujte efekt ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c62bf-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="c62bf-118">V podokně **náhledu** klikněte na zaškrtávací políčko **ukotvit výplň uživatelského ovládacího prvku** .</span><span class="sxs-lookup"><span data-stu-id="c62bf-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="c62bf-119">Všimněte si, že se změní velikost ovládacího prvku, aby bylo možné vyplnit podokno.</span><span class="sxs-lookup"><span data-stu-id="c62bf-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="c62bf-120">Změňte velikost kontejneru testu a sledujte, že se změní velikost ovládacího prvku v podokně.</span><span class="sxs-lookup"><span data-stu-id="c62bf-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="c62bf-121">Zavřete kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="c62bf-121">Close the test container.</span></span>

7. <span data-ttu-id="c62bf-122">Přidejte do projektu **TestContainerExample** další uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c62bf-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="c62bf-123">V **Návrhář formulářů**přetáhněte <xref:System.Windows.Forms.Button> ovládací prvek z **panelu nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c62bf-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="c62bf-124">Stisknutím klávesy **F5** Sestavte projekt a spusťte kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="c62bf-124">Press **F5** to build the project and run the test container.</span></span>

10. <span data-ttu-id="c62bf-125">Klikněte na **ovládací prvek** <xref:System.Windows.Forms.ComboBox> pro výběr uživatele, který chcete přepínat mezi dvěma uživatelskými ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="c62bf-125">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="c62bf-126">Testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="c62bf-126">Test user controls from another project</span></span>

<span data-ttu-id="c62bf-127">Uživatelské ovládací prvky můžete testovat z jiných projektů v aktuálním kontejneru testů projektu.</span><span class="sxs-lookup"><span data-stu-id="c62bf-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="c62bf-128">V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="c62bf-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="c62bf-129">V **Návrhář formulářů**přetáhněte <xref:System.Windows.Forms.RadioButton> ovládací prvek z **panelu nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c62bf-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="c62bf-130">Stisknutím klávesy **F5** Sestavte projekt a spusťte kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="c62bf-130">Press **F5** to build the project and run the test container.</span></span> <span data-ttu-id="c62bf-131">Kontejner testu se zobrazí <xref:System.Windows.Forms.UserControl> v podokně **náhledu** .</span><span class="sxs-lookup"><span data-stu-id="c62bf-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="c62bf-132">Klikněte na tlačítko **načíst** .</span><span class="sxs-lookup"><span data-stu-id="c62bf-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="c62bf-133">V dialogovém okně **otevřít** přejděte na **TestContainerExample**. dll, které jste vytvořili v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="c62bf-133">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="c62bf-134">Vyberte **TestContainerExample**. dll a kliknutím na tlačítko **otevřít** načtěte uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c62bf-134">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>

6. <span data-ttu-id="c62bf-135">Pomocí **ovládacího prvku vybrat uživatelský ovládací prvek** <xref:System.Windows.Forms.ComboBox> můžete přepínat mezi dvěma uživatelskými ovládacími prvky z projektu **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="c62bf-135">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="c62bf-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c62bf-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="c62bf-137">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="c62bf-137">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="c62bf-138">Návod: Vytváření složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c62bf-138">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="c62bf-139">[Návrhář uživatelského ovládacího prvku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c62bf-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
