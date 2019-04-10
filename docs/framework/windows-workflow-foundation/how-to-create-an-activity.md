---
title: 'Postupy: Vytvoření aktivity'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 48df9b90a92468858bd3ac5498bd83fd0d57fe75
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315137"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="5baae-102">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="5baae-102">How to: Create an Activity</span></span>

<span data-ttu-id="5baae-103">Aktivity jsou základní jednotka chování v [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5baae-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="5baae-104">Je možné implementovat logiku spouštění aktivity ve spravovaném kódu nebo se dá implementovat pomocí další aktivity.</span><span class="sxs-lookup"><span data-stu-id="5baae-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="5baae-105">Toto téma ukazuje, jak vytvořit dvě aktivity.</span><span class="sxs-lookup"><span data-stu-id="5baae-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="5baae-106">První aktivita je jednoduchá aktivita, která používá kód implementovat logiku jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="5baae-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="5baae-107">Implementace druhou aktivitu se definuje pomocí další aktivity.</span><span class="sxs-lookup"><span data-stu-id="5baae-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="5baae-108">Tyto aktivity se používají v následujících krocích v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="5baae-108">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="5baae-109">Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="5baae-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="5baae-110">Vytvořte projekt knihovny aktivit</span><span class="sxs-lookup"><span data-stu-id="5baae-110">Create the activity library project</span></span>

1. <span data-ttu-id="5baae-111">Otevřít Visual Studio a zvolte **nový** > **projektu** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="5baae-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="5baae-112">V **nový projekt** dialogového okna, v části **nainstalováno** vyberte **Visual C#** > **pracovního postupu** (nebo **Jazyka Visual Basic** > **pracovního postupu**).</span><span class="sxs-lookup"><span data-stu-id="5baae-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5baae-113">Pokud se nezobrazí **pracovního postupu** kategorii šablon, budete muset nainstalovat **Windows Workflow Foundation** komponentu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5baae-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="5baae-114">Zvolte **otevřít instalační program Visual Studio** odkazu na levé straně **nový projekt** dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="5baae-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="5baae-115">V instalačním programu Visual Studio, vyberte **jednotlivé komponenty** kartu. Potom v části **vývojových aktivit** kategorii, vyberte **Windows Workflow Foundation** komponenty.</span><span class="sxs-lookup"><span data-stu-id="5baae-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="5baae-116">Zvolte **změnit** pro instalaci součásti.</span><span class="sxs-lookup"><span data-stu-id="5baae-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="5baae-117">Vyberte **knihovny aktivit** šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="5baae-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="5baae-118">Typ `NumberGuessWorkflowActivities` v **název** pole a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="5baae-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="5baae-119">Klikněte pravým tlačítkem na **Activity1.xaml** v **Průzkumníka řešení** a zvolte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="5baae-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="5baae-120">Klikněte na tlačítko **OK** potvrďte.</span><span class="sxs-lookup"><span data-stu-id="5baae-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="5baae-121">Vytvořit aktivitu readint –</span><span class="sxs-lookup"><span data-stu-id="5baae-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="5baae-122">Zvolte **přidat novou položku** z **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="5baae-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="5baae-123">V **nainstalováno** > **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="5baae-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="5baae-124">Vyberte **aktivita s kódem** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="5baae-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="5baae-125">Typ `ReadInt` do **název** pole a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="5baae-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="5baae-126">Nahraďte existující `ReadInt` definice s následující definicí.</span><span class="sxs-lookup"><span data-stu-id="5baae-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="5baae-127">`ReadInt` Aktivity je odvozena z <xref:System.Activities.NativeActivity%601> místo <xref:System.Activities.CodeActivity>, což je výchozí hodnota pro kód šablony aktivit.</span><span class="sxs-lookup"><span data-stu-id="5baae-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <xref:System.Activities.CodeActivity%601> <span data-ttu-id="5baae-128">lze použít, pokud aktivita poskytuje jeden výsledek, který je zveřejněný prostřednictvím <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nepodporuje používání záložek, takže <xref:System.Activities.NativeActivity%601> se používá.</span><span class="sxs-lookup"><span data-stu-id="5baae-128">can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="5baae-129">Vytvořit aktivitu příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="5baae-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="5baae-130">Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="5baae-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="5baae-131">Vytváření projektu umožňuje `ReadInt` aktivity v tomto projektu, který se má použít k vytvoření vlastní aktivity v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="5baae-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="5baae-132">Zvolte **přidat novou položku** z **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="5baae-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="5baae-133">V **nainstalováno** > **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="5baae-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="5baae-134">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="5baae-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="5baae-135">Typ `Prompt` do **název** pole a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="5baae-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="5baae-136">Dvakrát klikněte na panel **Prompt.xaml** v **Průzkumníka řešení** se zobrazí v návrháři, pokud je už se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="5baae-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="5baae-137">Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit zobrazíte **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="5baae-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="5baae-138">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="5baae-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="5baae-139">Typ `BookmarkName` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a poté stiskněte klávesu **Enter** uložit argument.</span><span class="sxs-lookup"><span data-stu-id="5baae-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="5baae-140">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="5baae-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="5baae-141">Typ `Result` do **název** pole, které se nachází pod nově přidaný `BookmarkName` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte možnost **Int32** z **typ argumentu** rozevíracího seznamu a poté stiskněte klávesu **Enter**.</span><span class="sxs-lookup"><span data-stu-id="5baae-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="5baae-142">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="5baae-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="5baae-143">Typ `Text` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a poté stiskněte klávesu **Enter** uložit argument.</span><span class="sxs-lookup"><span data-stu-id="5baae-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="5baae-144">Tyto tři argumenty, které jsou vázány na odpovídající argument <xref:System.Activities.Statements.WriteLine> a `ReadInt` aktivity, které jsou přidány do `Prompt` aktivity v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="5baae-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="5baae-145">Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="5baae-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="5baae-146">Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Výzvy** návrháře aktivit.</span><span class="sxs-lookup"><span data-stu-id="5baae-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="5baae-147">Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="5baae-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="5baae-148">Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Pořadí** aktivity.</span><span class="sxs-lookup"><span data-stu-id="5baae-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="5baae-149">Vytvoření vazby **Text** argument **WriteLine** aktivitu **Text** argument **výzvy** aktivitu tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole **vlastnosti** okno a poté stiskněte klávesu **kartu** klíč dvakrát.</span><span class="sxs-lookup"><span data-stu-id="5baae-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="5baae-150">Tím zavře okno technologie IntelliSense seznam členů a uloží hodnotu vlastnosti přesunutím výběr vypnout vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5baae-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="5baae-151">Tuto vlastnost můžete nastavit také tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole přímo na aktivitu.</span><span class="sxs-lookup"><span data-stu-id="5baae-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="5baae-152">Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="5baae-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="5baae-153">Přetáhněte **readint –** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **pořadí** aktivitu tak, že následuje **WriteLine** aktivity.</span><span class="sxs-lookup"><span data-stu-id="5baae-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="5baae-154">Vytvoření vazby **BookmarkName** argument **readint –** aktivitu **BookmarkName** argument **výzvy** aktivitu tak, že zadáte `BookmarkName` do **zadejte výraz jazyka VB.** políčka napravo od **BookmarkName** argumentu **okno vlastností**a potom stiskněte klávesu **Kartu** klíč dvakrát zavřete okno technologie IntelliSense seznam členů a uložte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5baae-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="5baae-155">Vytvoření vazby **výsledek** argument **readint –** aktivitu **výsledek** argument **výzvy** aktivitu tak, že zadáte `Result` do **zadejte výraz jazyka VB.** políčka napravo od **výsledek** argumentu **okno vlastností**a potom stiskněte klávesu **kartu** klíč dvakrát.</span><span class="sxs-lookup"><span data-stu-id="5baae-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="5baae-156">Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení řešení.</span><span class="sxs-lookup"><span data-stu-id="5baae-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5baae-157">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5baae-157">Next steps</span></span>

<span data-ttu-id="5baae-158">Pokyny k vytvoření pracovního postupu pomocí těchto aktivit naleznete v části Další krok v tomto kurzu [jak: Vytvoření pracovního postupu](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="5baae-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5baae-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5baae-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="5baae-160">Návrh a implementace vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="5baae-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="5baae-161">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="5baae-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="5baae-162">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="5baae-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="5baae-163">Použití ExpressionTextBox v návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="5baae-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)