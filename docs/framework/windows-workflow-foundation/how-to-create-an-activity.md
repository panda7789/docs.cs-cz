---
title: 'Postupy: vytvoření aktivity'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: deb1b6ca5c6fc996a015e32dd5e0c7b9bd6530fa
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45510174"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="fc359-102">Postupy: vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="fc359-102">How to: Create an Activity</span></span>
<span data-ttu-id="fc359-103">Aktivity jsou základní jednotka chování v [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc359-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="fc359-104">Je možné implementovat logiku spouštění aktivity ve spravovaném kódu nebo se dá implementovat pomocí další aktivity.</span><span class="sxs-lookup"><span data-stu-id="fc359-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="fc359-105">Toto téma ukazuje, jak vytvořit dvě aktivity.</span><span class="sxs-lookup"><span data-stu-id="fc359-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="fc359-106">První aktivita je jednoduchá aktivita, která používá kód implementovat logiku jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="fc359-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="fc359-107">Implementace druhou aktivitu se definuje pomocí další aktivity.</span><span class="sxs-lookup"><span data-stu-id="fc359-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="fc359-108">Tyto aktivity se používají v následujících krocích v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="fc359-108">These activities are used in following steps in the tutorial.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc359-109">Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="fc359-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-activity-library-project"></a><span data-ttu-id="fc359-110">Vytvoření projektu knihovny aktivit</span><span class="sxs-lookup"><span data-stu-id="fc359-110">To create the activity library project</span></span>  
  
1.  <span data-ttu-id="fc359-111">Otevřít [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a zvolte **nový**, **projektu** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc359-111">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and choose **New**,  **Project** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="fc359-112">Rozbalte **ostatní typy projektů** uzlu **nainstalováno**, **šablony** seznam a vyberte **řešení sady Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="fc359-112">Expand the **Other Project Types** node in the **Installed**, **Templates** list and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="fc359-113">Vyberte **prázdné řešení** z **řešení sady Visual Studio** seznamu.</span><span class="sxs-lookup"><span data-stu-id="fc359-113">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="fc359-114">Ujistěte se, že **rozhraní .NET Framework 4.5** je vybrali v rozevíracím seznamu verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc359-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="fc359-115">Typ `WF45GettingStartedTutorial` v **název** pole a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc359-115">Type `WF45GettingStartedTutorial` in the **Name** box and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="fc359-116">Klikněte pravým tlačítkem na **WF45GettingStartedTutorial** v **Průzkumníka řešení** a zvolte **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="fc359-116">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="fc359-117">Pokud **Průzkumníka řešení** okno nezobrazí, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc359-117">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="fc359-118">V **nainstalováno** uzlu, vyberte **Visual C#**, **pracovního postupu** (nebo **jazyka Visual Basic**, **pracovního postupu**).</span><span class="sxs-lookup"><span data-stu-id="fc359-118">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span> <span data-ttu-id="fc359-119">Ujistěte se, že **rozhraní .NET Framework 4.5** výběru v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] verze rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fc359-119">Ensure that **.NET Framework 4.5** is selected in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version drop-down list.</span></span> <span data-ttu-id="fc359-120">Vyberte **knihovny aktivit** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="fc359-120">Select **Activity Library** from the **Workflow** list.</span></span> <span data-ttu-id="fc359-121">Typ `NumberGuessWorkflowActivities` v **název** pole a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc359-121">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc359-122">V závislosti na programovací jazyk, který je nakonfigurovaný jako primární jazyk v sadě Visual Studio **Visual C#** nebo **jazyka Visual Basic** uzel může být v rámci **jiné jazyky** v uzlu **nainstalováno** uzlu.</span><span class="sxs-lookup"><span data-stu-id="fc359-122">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
6.  <span data-ttu-id="fc359-123">Klikněte pravým tlačítkem na **Activity1.xaml** v **Průzkumníka řešení** a zvolte **odstranit**.</span><span class="sxs-lookup"><span data-stu-id="fc359-123">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="fc359-124">Klikněte na tlačítko **OK** potvrďte.</span><span class="sxs-lookup"><span data-stu-id="fc359-124">Click **OK** to confirm.</span></span>  
  
### <a name="to-create-the-readint-activity"></a><span data-ttu-id="fc359-125">Vytvořit aktivitu readint –</span><span class="sxs-lookup"><span data-stu-id="fc359-125">To create the ReadInt activity</span></span>  
  
1.  <span data-ttu-id="fc359-126">Zvolte **přidat novou položku** z **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc359-126">Choose **Add New Item** from the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="fc359-127">V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="fc359-127">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="fc359-128">Vyberte **aktivita s kódem** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="fc359-128">Select **Code Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="fc359-129">Typ `ReadInt` do **název** pole a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="fc359-129">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="fc359-130">Nahraďte existující `ReadInt` definice s následující definicí.</span><span class="sxs-lookup"><span data-stu-id="fc359-130">Replace the existing `ReadInt` definition with the following definition.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="fc359-131">`ReadInt` Aktivity je odvozena z <xref:System.Activities.NativeActivity%601> místo <xref:System.Activities.CodeActivity>, což je výchozí hodnota pro kód šablony aktivit.</span><span class="sxs-lookup"><span data-stu-id="fc359-131">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="fc359-132"><xref:System.Activities.CodeActivity%601> lze použít, pokud aktivita poskytuje jeden výsledek, který je zveřejněný prostřednictvím <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nepodporuje používání záložek, takže <xref:System.Activities.NativeActivity%601> se používá.</span><span class="sxs-lookup"><span data-stu-id="fc359-132"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>  
  
### <a name="to-create-the-prompt-activity"></a><span data-ttu-id="fc359-133">Vytvořit aktivitu příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="fc359-133">To create the Prompt activity</span></span>  
  
1.  <span data-ttu-id="fc359-134">Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="fc359-134">Press CTRL+SHIFT+B to build the project.</span></span> <span data-ttu-id="fc359-135">Vytváření projektu umožňuje `ReadInt` aktivity v tomto projektu, který se má použít k vytvoření vlastní aktivity v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="fc359-135">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>  
  
2.  <span data-ttu-id="fc359-136">Zvolte **přidat novou položku** z **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc359-136">Choose **Add New Item** from the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="fc359-137">V **nainstalováno**, **společné položky** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="fc359-137">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="fc359-138">Vyberte **aktivity** z **pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="fc359-138">Select **Activity** from the **Workflow** list.</span></span>  
  
4.  <span data-ttu-id="fc359-139">Typ `Prompt` do **název** pole a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="fc359-139">Type `Prompt` into the **Name** box and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="fc359-140">Dvakrát klikněte na panel **Prompt.xaml** v **Průzkumníka řešení** se zobrazí v návrháři, pokud je už se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="fc359-140">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>  
  
6.  <span data-ttu-id="fc359-141">Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit zobrazíte **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="fc359-141">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>  
  
7.  <span data-ttu-id="fc359-142">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="fc359-142">Click **Create Argument**.</span></span>  
  
8.  <span data-ttu-id="fc359-143">Typ `BookmarkName` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.</span><span class="sxs-lookup"><span data-stu-id="fc359-143">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
9. <span data-ttu-id="fc359-144">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="fc359-144">Click **Create Argument**.</span></span>  
  
10. <span data-ttu-id="fc359-145">Typ `Result` do **název** pole, které se nachází pod nově přidaný `BookmarkName` argument, vyberte **si** z **směr** rozevíracího seznamu vyberte možnost **Int32** z **typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="fc359-145">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
11. <span data-ttu-id="fc359-146">Klikněte na tlačítko **vytvořit Argument**.</span><span class="sxs-lookup"><span data-stu-id="fc359-146">Click **Create Argument**.</span></span>  
  
12. <span data-ttu-id="fc359-147">Typ `Text` do **název** vyberte **v** z **směr** rozevíracího seznamu vyberte **řetězec** z **Typ argumentu** rozevíracího seznamu a potom stiskněte klávesu ENTER k uložení argument.</span><span class="sxs-lookup"><span data-stu-id="fc359-147">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
     <span data-ttu-id="fc359-148">Tyto tři argumenty, které jsou vázány na odpovídající argument <xref:System.Activities.Statements.WriteLine> a `ReadInt` aktivity, které jsou přidány do `Prompt` aktivity v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="fc359-148">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>  
  
13. <span data-ttu-id="fc359-149">Klikněte na tlačítko **argumenty** v levého dolního rohu návrháře aktivit, zavřete **argumenty** podokně.</span><span class="sxs-lookup"><span data-stu-id="fc359-149">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
14. <span data-ttu-id="fc359-150">Přetáhněte **pořadí** aktivita z **tok řízení** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Výzvy** návrháře aktivit.</span><span class="sxs-lookup"><span data-stu-id="fc359-150">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="fc359-151">Pokud **nástrojů** okno nezobrazí, vyberte **nástrojů** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc359-151">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
15. <span data-ttu-id="fc359-152">Přetáhněte **WriteLine** aktivita z **primitiv** část **nástrojů** a umístěte ho do **Sem přetáhněte aktivitu** popisek **Pořadí** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fc359-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>  
  
16. <span data-ttu-id="fc359-153">Vytvoření vazby **Text** argument **WriteLine** aktivitu **Text** argument **výzvy** aktivitu tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole **vlastnosti** okno a poté stiskněte klávesu KARTĚ klíč dvakrát.</span><span class="sxs-lookup"><span data-stu-id="fc359-153">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the TAB key two times.</span></span> <span data-ttu-id="fc359-154">Tím zavře okno technologie IntelliSense seznam členů a uloží hodnotu vlastnosti přesunutím výběr vypnout vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fc359-154">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="fc359-155">Tuto vlastnost můžete nastavit také tak, že zadáte `Text` do **zadejte výraz C#** nebo **zadejte výraz jazyka VB.** pole přímo na aktivitu.</span><span class="sxs-lookup"><span data-stu-id="fc359-155">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="fc359-156">Pokud **okno vlastností** není zobrazený, vyberte **okno vlastností** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc359-156">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
17. <span data-ttu-id="fc359-157">Přetáhněte **readint –** aktivita z **NumberGuessWorkflowActivities** část **nástrojů** a umístěte jej do **pořadí** aktivitu tak, že následuje **WriteLine** aktivity.</span><span class="sxs-lookup"><span data-stu-id="fc359-157">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>  
  
18. <span data-ttu-id="fc359-158">Vytvoření vazby **BookmarkName** argument **readint –** aktivitu **BookmarkName** argument **výzvy** aktivitu tak, že zadáte `BookmarkName` do **zadejte výraz jazyka VB.** políčka napravo od **BookmarkName** argumentu **okno Vlastnosti**a stiskněte klávesu TAB dvě časový limit zavřete okno technologie IntelliSense seznam členů a uložte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fc359-158">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the TAB key two times to close the IntelliSense list members window and save the property.</span></span>  
  
19. <span data-ttu-id="fc359-159">Vytvoření vazby **výsledek** argument **readint –** aktivitu **výsledek** argument **výzvy** aktivitu tak, že zadáte `Result` do **zadejte výraz jazyka VB.** políčka napravo od **výsledek** argumentu **okno vlastností**a potom stiskněte klávesu Tabulátor dvakrát.</span><span class="sxs-lookup"><span data-stu-id="fc359-159">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the TAB key two times.</span></span>  
  
20. <span data-ttu-id="fc359-160">Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.</span><span class="sxs-lookup"><span data-stu-id="fc359-160">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="fc359-161">Pokyny k vytvoření pracovního postupu pomocí těchto aktivit naleznete v části Další krok v tomto kurzu [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="fc359-161">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc359-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc359-162">See Also</span></span>  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [<span data-ttu-id="fc359-163">Návrh a implementace vlastních aktivit</span><span class="sxs-lookup"><span data-stu-id="fc359-163">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [<span data-ttu-id="fc359-164">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="fc359-164">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="fc359-165">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="fc359-165">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="fc359-166">Použití ExpressionTextBox v návrháři vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="fc359-166">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
