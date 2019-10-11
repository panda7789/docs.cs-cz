---
title: 'Postupy: testování chování prvku UserControl v době běhu'
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
ms.openlocfilehash: 110036e5031a2956375b1edf0689237661522d39
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180209"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="c7044-102">Postupy: testování chování prvku UserControl v době běhu</span><span class="sxs-lookup"><span data-stu-id="c7044-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="c7044-103">Když vyvíjíte <xref:System.Windows.Forms.UserControl>, je nutné otestovat jeho chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="c7044-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="c7044-104">Můžete vytvořit samostatný projekt aplikace pro systém Windows a umístit ovládací prvek do formuláře testu, ale tato procedura je nepraktická.</span><span class="sxs-lookup"><span data-stu-id="c7044-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="c7044-105">Rychlejší a snazší způsob použití **kontejneru testu UserControl** , který poskytuje Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7044-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="c7044-106">Tento kontejner testů začíná přímo z projektu knihovny ovládacích prvků systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c7044-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7044-107">Aby mohl kontejner testu načíst <xref:System.Windows.Forms.UserControl>, ovládací prvek musí mít alespoň jeden veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c7044-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="c7044-108">Vizuální C++ ovládací prvek nelze testovat pomocí **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="c7044-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="c7044-109">Testování chování prvku UserControl v době běhu</span><span class="sxs-lookup"><span data-stu-id="c7044-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="c7044-110">V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="c7044-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="c7044-111">V **Návrhář formulářů**přetáhněte ovládací prvek <xref:System.Windows.Forms.Label> ze **sady nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7044-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="c7044-112">Stisknutím klávesy <kbd>F5</kbd> Sestavte projekt a spusťte **kontejner testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="c7044-112">Press <kbd>F5</kbd> to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="c7044-113">Kontejner testu se zobrazí s vaším <xref:System.Windows.Forms.UserControl> v podokně **náhledu** .</span><span class="sxs-lookup"><span data-stu-id="c7044-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="c7044-114">Vyberte vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> zobrazenou v ovládacím prvku <xref:System.Windows.Forms.PropertyGrid> napravo od podokna **náhledu** .</span><span class="sxs-lookup"><span data-stu-id="c7044-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="c7044-115">Změňte její hodnotu na **ControlDark**.</span><span class="sxs-lookup"><span data-stu-id="c7044-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="c7044-116">Pozor, aby se ovládací prvek změnil na tmavší barvu.</span><span class="sxs-lookup"><span data-stu-id="c7044-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="c7044-117">Zkuste změnit další hodnoty vlastností a sledujte efekt ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7044-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="c7044-118">V podokně **náhledu** klikněte na zaškrtávací políčko **ukotvit výplň uživatelského ovládacího prvku** .</span><span class="sxs-lookup"><span data-stu-id="c7044-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="c7044-119">Všimněte si, že se změní velikost ovládacího prvku, aby bylo možné vyplnit podokno.</span><span class="sxs-lookup"><span data-stu-id="c7044-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="c7044-120">Změňte velikost kontejneru testu a sledujte, že se změní velikost ovládacího prvku v podokně.</span><span class="sxs-lookup"><span data-stu-id="c7044-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="c7044-121">Zavřete kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="c7044-121">Close the test container.</span></span>

7. <span data-ttu-id="c7044-122">Přidejte do projektu **TestContainerExample** další uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c7044-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="c7044-123">V **Návrhář formulářů**přetáhněte ovládací prvek <xref:System.Windows.Forms.Button> ze **sady nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7044-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="c7044-124">Stisknutím klávesy <kbd>F5</kbd> Sestavte projekt a spusťte kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="c7044-124">Press <kbd>F5</kbd> to build the project and run the test container.</span></span>

10. <span data-ttu-id="c7044-125">Klikněte na **ovládací prvek vybrat uživatele** <xref:System.Windows.Forms.ComboBox> pro přepínání mezi dvěma uživatelskými ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="c7044-125">Click the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="c7044-126">Testování uživatelských ovládacích prvků z jiného projektu</span><span class="sxs-lookup"><span data-stu-id="c7044-126">Test user controls from another project</span></span>

<span data-ttu-id="c7044-127">Uživatelské ovládací prvky můžete testovat z jiných projektů v aktuálním kontejneru testů projektu.</span><span class="sxs-lookup"><span data-stu-id="c7044-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="c7044-128">V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="c7044-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="c7044-129">V **Návrhář formulářů**přetáhněte ovládací prvek <xref:System.Windows.Forms.RadioButton> ze **sady nástrojů** na návrhovou plochu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7044-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="c7044-130">Stisknutím klávesy <kbd>F5</kbd> Sestavte projekt a spusťte kontejner testu.</span><span class="sxs-lookup"><span data-stu-id="c7044-130">Press <kbd>F5</kbd> to build the project and run the test container.</span></span> <span data-ttu-id="c7044-131">Kontejner testu se zobrazí s vaším <xref:System.Windows.Forms.UserControl> v podokně **náhledu** .</span><span class="sxs-lookup"><span data-stu-id="c7044-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="c7044-132">Klikněte na tlačítko **načíst** .</span><span class="sxs-lookup"><span data-stu-id="c7044-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="c7044-133">V dialogovém okně **otevřít** přejděte na *TestContainerExample. dll*, které jste vytvořili v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="c7044-133">In the **Open** dialog box, navigate to *TestContainerExample.dll*, which you built in the previous procedure.</span></span> <span data-ttu-id="c7044-134">Vyberte *TestContainerExample. dll* a kliknutím na tlačítko **otevřít** načtěte uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c7044-134">Select *TestContainerExample.dll* and click the **Open** button to load the user controls.</span></span>

6. <span data-ttu-id="c7044-135">Pomocí **ovládacího prvku vybrat uživatelský** <xref:System.Windows.Forms.ComboBox> můžete přepínat mezi dvěma uživatelskými ovládacími prvky z projektu **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="c7044-135">Use the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7044-136">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="c7044-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="c7044-137">Postupy: vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="c7044-137">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="c7044-138">Návod: vytváření složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c7044-138">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="c7044-139">[Návrhář uživatelského ovládacího prvku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c7044-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
