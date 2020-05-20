---
title: 'Postupy: Vytvoření aktivity'
description: 'V tomto článku se dozvíte, jak vytvořit dvě aktivity v modelu Workflow Foundation: jeden, který používá kód k implementaci své logiky a jedno, které je definováno pomocí jiných aktivit.'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: dae099d102b0c85d09a1ef8bcce56e8a9096bd20
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419587"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="b6454-103">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="b6454-103">How to: Create an Activity</span></span>

<span data-ttu-id="b6454-104">Aktivity jsou základní jednotkou chování v [!INCLUDE[wf1](../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b6454-104">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="b6454-105">Logika provádění aktivity může být implementována ve spravovaném kódu nebo může být implementována pomocí jiných aktivit.</span><span class="sxs-lookup"><span data-stu-id="b6454-105">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="b6454-106">Toto téma ukazuje, jak vytvořit dvě aktivity.</span><span class="sxs-lookup"><span data-stu-id="b6454-106">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="b6454-107">První aktivita je jednoduchá aktivita, která používá kód k implementaci logiky provádění.</span><span class="sxs-lookup"><span data-stu-id="b6454-107">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="b6454-108">Implementace druhé aktivity je definována pomocí jiných aktivit.</span><span class="sxs-lookup"><span data-stu-id="b6454-108">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="b6454-109">Tyto aktivity se používají v následujících krocích v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="b6454-109">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="b6454-110">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="b6454-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="b6454-111">Vytvoření projektu knihovny aktivit</span><span class="sxs-lookup"><span data-stu-id="b6454-111">Create the activity library project</span></span>

1. <span data-ttu-id="b6454-112">Otevřete Visual Studio a v **New**  >  nabídce **soubor** vyberte nový**projekt** .</span><span class="sxs-lookup"><span data-stu-id="b6454-112">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="b6454-113">V dialogovém okně **Nový projekt** v části **nainstalovaná** kategorie vyberte pracovní **postup Visual C#**  >  **Workflow** (nebo **Visual Basic**  >  **pracovní postup**).</span><span class="sxs-lookup"><span data-stu-id="b6454-113">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6454-114">Pokud nevidíte kategorii šablony **pracovního postupu** , bude pravděpodobně nutné nainstalovat **programovací model Windows Workflow Foundation** součást sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b6454-114">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="b6454-115">Na levé straně dialogového okna **Nový projekt** klikněte na odkaz **otevřít instalační program pro Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="b6454-115">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="b6454-116">V Instalační program pro Visual Studio vyberte kartu **jednotlivé součásti** . Pak v kategorii **vývojové aktivity** vyberte součást **programovací model Windows Workflow Foundation** .</span><span class="sxs-lookup"><span data-stu-id="b6454-116">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="b6454-117">Pro instalaci součásti klikněte na tlačítko **Upravit** .</span><span class="sxs-lookup"><span data-stu-id="b6454-117">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="b6454-118">Vyberte šablonu projektu **knihovny aktivit** .</span><span class="sxs-lookup"><span data-stu-id="b6454-118">Select the **Activity Library** project template.</span></span> <span data-ttu-id="b6454-119">`NumberGuessWorkflowActivities`Do pole **název** zadejte a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6454-119">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="b6454-120">V **Průzkumník řešení** klikněte pravým tlačítkem na **Activity1. XAML** a vyberte **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="b6454-120">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="b6454-121">Potvrďte kliknutím na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="b6454-121">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="b6454-122">Vytvoření aktivity ReadInt</span><span class="sxs-lookup"><span data-stu-id="b6454-122">Create the ReadInt activity</span></span>

1. <span data-ttu-id="b6454-123">V nabídce **projekt** klikněte na příkaz **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="b6454-123">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="b6454-124">V uzlu **nainstalované**  >  **společné položky** vyberte možnost **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="b6454-124">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b6454-125">V seznamu **pracovních postupů** vyberte **aktivita kódu** .</span><span class="sxs-lookup"><span data-stu-id="b6454-125">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="b6454-126">`ReadInt`Do pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="b6454-126">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="b6454-127">Nahraďte stávající `ReadInt` definici následující definicí.</span><span class="sxs-lookup"><span data-stu-id="b6454-127">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="b6454-128">`ReadInt`Aktivita je odvozena z <xref:System.Activities.NativeActivity%601> místo <xref:System.Activities.CodeActivity> , což je výchozí hodnota pro šablonu aktivity kódu.</span><span class="sxs-lookup"><span data-stu-id="b6454-128">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="b6454-129"><xref:System.Activities.CodeActivity%601>dá se použít, pokud aktivita poskytuje jeden výsledek, který je vystavený přes <xref:System.Activities.Activity%601.Result%2A> argument, ale nepodporuje <xref:System.Activities.CodeActivity%601> použití záložek, takže <xref:System.Activities.NativeActivity%601> se používá.</span><span class="sxs-lookup"><span data-stu-id="b6454-129"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="b6454-130">Vytvoření aktivity výzvy</span><span class="sxs-lookup"><span data-stu-id="b6454-130">Create the Prompt activity</span></span>

1. <span data-ttu-id="b6454-131">Stisknutím **kombinace kláves CTRL** + **+ SHIFT** + **B** Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="b6454-131">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="b6454-132">Sestavování projektu umožňuje, aby se `ReadInt` aktivita v tomto projektu použila k vytvoření vlastní aktivity z tohoto kroku.</span><span class="sxs-lookup"><span data-stu-id="b6454-132">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="b6454-133">V nabídce **projekt** klikněte na příkaz **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="b6454-133">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="b6454-134">V uzlu **nainstalované**  >  **společné položky** vyberte možnost **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="b6454-134">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b6454-135">V seznamu **pracovních postupů** vyberte **aktivita** .</span><span class="sxs-lookup"><span data-stu-id="b6454-135">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="b6454-136">`Prompt`Do pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="b6454-136">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="b6454-137">Dvojitým kliknutím na položku **prompt. XAML** v **Průzkumník řešení** ji zobrazte v návrháři, pokud ještě není zobrazená.</span><span class="sxs-lookup"><span data-stu-id="b6454-137">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="b6454-138">Kliknutím na **argumenty** v levé dolní části návrháře aktivit zobrazíte podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="b6454-138">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="b6454-139">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="b6454-139">Click **Create Argument**.</span></span>

8. <span data-ttu-id="b6454-140">`BookmarkName`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v, v** rozevíracím seznamu **typ argumentu** vyberte **řetězec** a potom stiskněte klávesu **ENTER** a argument uložte.</span><span class="sxs-lookup"><span data-stu-id="b6454-140">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="b6454-141">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="b6454-141">Click **Create Argument**.</span></span>

10. <span data-ttu-id="b6454-142">`Result`Do pole **název** , které se nachází pod nově přidaným `BookmarkName` argumentem, vyberte **out** v rozevíracím seznamu **směr** , v rozevíracím seznamu **typ argumentu** vyberte **Int32** a potom stiskněte klávesu **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="b6454-142">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="b6454-143">Klikněte na **vytvořit argument**.</span><span class="sxs-lookup"><span data-stu-id="b6454-143">Click **Create Argument**.</span></span>

12. <span data-ttu-id="b6454-144">`Text`Do pole **název** zadejte, v rozevíracím seznamu **směr** vyberte možnost **v, v** rozevíracím seznamu **typ argumentu** vyberte **řetězec** a potom stiskněte klávesu **ENTER** a argument uložte.</span><span class="sxs-lookup"><span data-stu-id="b6454-144">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="b6454-145">Tyto tři argumenty jsou vázány na odpovídající argumenty <xref:System.Activities.Statements.WriteLine> `ReadInt` aktivity a, které jsou přidány k `Prompt` aktivitě v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="b6454-145">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="b6454-146">Kliknutím na **argumenty** v levé dolní části návrháře aktivit zavřete podokno **argumenty** .</span><span class="sxs-lookup"><span data-stu-id="b6454-146">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="b6454-147">Přetáhněte aktivitu **sekvence** z části **Flow řízení** v **sadě nástrojů** a přetáhněte ji do pole Sem přetáhněte **aktivitu** Návrhář aktivity **výzvy** .</span><span class="sxs-lookup"><span data-stu-id="b6454-147">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="b6454-148">Pokud okno **panelu nástrojů** není zobrazeno, vyberte z nabídky **zobrazení** možnost **Sada nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="b6454-148">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="b6454-149">Přetáhněte aktivitu **WriteLine** z oddílu **Primitivs** v **sadě nástrojů** a přetáhněte ji do pole **drop Activity (odkládací aktivita** ) na popisek aktivity **sekvence** .</span><span class="sxs-lookup"><span data-stu-id="b6454-149">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="b6454-150">Navažte argument **textu** aktivity **WriteLine** na **textový** argument aktivity **výzvy** zadáním `Text` do **výrazu zadejte výraz jazyka C#** nebo **Zadejte pole výrazu VB** v okně **vlastnosti** a potom stiskněte klávesu **TAB** dvakrát.</span><span class="sxs-lookup"><span data-stu-id="b6454-150">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="b6454-151">Tím se nevynechává okno členové seznamu IntelliSense a uloží hodnotu vlastnosti přesunutím výběru mimo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b6454-151">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="b6454-152">Tuto vlastnost lze také nastavit tak, že zadáte `Text` do **výrazu zadejte výraz jazyka C#** nebo do samotné aktivity **Zadejte pole výrazu VB** .</span><span class="sxs-lookup"><span data-stu-id="b6454-152">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="b6454-153">Pokud se **okno Vlastnosti** nezobrazí, v nabídce **zobrazení** vyberte **okno Vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="b6454-153">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="b6454-154">Přetáhněte aktivitu **ReadInt** z oddílu **NumberGuessWorkflowActivities** **panelu nástrojů** a přetáhněte ji do aktivity **sekvence** tak, aby se doprovází aktivity **WriteLine** .</span><span class="sxs-lookup"><span data-stu-id="b6454-154">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="b6454-155">Zapojte argument **Bookmark** aktivity **ReadInt** k argumentu **Bookmark** aktivity **výzvy** zadáním `BookmarkName` do pole **Zadejte výraz jazyka VB** vpravo od argumentu **Bookmark** v **okně Vlastnosti**a potom stiskněte klávesu **TAB** dvakrát pro zavření okna členů seznamu a vlastnost uložte.</span><span class="sxs-lookup"><span data-stu-id="b6454-155">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="b6454-156">Navažte argument **výsledku** aktivity **ReadInt** na **výsledek** aktivity **výzvy** zadáním `Result` do pole **Zadejte výraz VB** napravo od argumentu **výsledek** v **okně Vlastnosti**a potom stiskněte klávesu **TAB** dvakrát.</span><span class="sxs-lookup"><span data-stu-id="b6454-156">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="b6454-157">Stisknutím **kombinace kláves CTRL** + **+ SHIFT** + **B** sestavíte řešení.</span><span class="sxs-lookup"><span data-stu-id="b6454-157">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6454-158">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b6454-158">Next steps</span></span>

<span data-ttu-id="b6454-159">Pokyny k vytvoření pracovního postupu pomocí těchto aktivit najdete v dalším kroku v tomto kurzu [: vytvoření pracovního postupu](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b6454-159">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6454-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6454-160">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="b6454-161">Návrh a implementace vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="b6454-161">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="b6454-162">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="b6454-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="b6454-163">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b6454-163">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="b6454-164">Použití ExpressionTextBox v návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="b6454-164">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
