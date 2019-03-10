---
title: Výrazy jazyka C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: 2ffc380d9c65ec398084bfcbeadfe0fd2c3d6720
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720576"
---
# <a name="c-expressions"></a><span data-ttu-id="4114d-102">Výrazy jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4114d-102">C# Expressions</span></span>
<span data-ttu-id="4114d-103">Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporované ve Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="4114d-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="4114d-104">Vytvořit nové projekty pracovního postupu C# v sadě Visual Studio 2012, které se zaměřují [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] použití výrazy jazyka C# a projekty pracovního postupu Visual Basic používat výrazy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4114d-104">New C# workflow projects created in Visual Studio 2012 that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="4114d-105">Existující [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projekty pracovního postupu, které používají výrazy jazyka Visual Basic se dají migrovat do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bez ohledu na to, projekt jazyka a jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="4114d-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="4114d-106">Toto téma obsahuje přehled výrazy jazyka C# v [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4114d-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>

## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="4114d-107">Používání výrazy jazyka C# v pracovních postupech</span><span class="sxs-lookup"><span data-stu-id="4114d-107">Using C# expressions in workflows</span></span>

-   [<span data-ttu-id="4114d-108">Použití výrazy jazyka C# v Návrháři postupu provádění</span><span class="sxs-lookup"><span data-stu-id="4114d-108">Using C# expressions in the Workflow Designer</span></span>](csharp-expressions.md#WFDesigner)

    -   [<span data-ttu-id="4114d-109">Zpětné kompatibility</span><span class="sxs-lookup"><span data-stu-id="4114d-109">Backwards compatibility</span></span>](csharp-expressions.md#BackwardCompat)

-   [<span data-ttu-id="4114d-110">Používání výrazy jazyka C# v pracovních postupech kódu</span><span class="sxs-lookup"><span data-stu-id="4114d-110">Using C# expressions in code workflows</span></span>](csharp-expressions.md#CodeWorkflows)

-   [<span data-ttu-id="4114d-111">Používání výrazy jazyka C# v pracovních postupech XAML</span><span class="sxs-lookup"><span data-stu-id="4114d-111">Using C# expressions in XAML workflows</span></span>](csharp-expressions.md#XamlWorkflows)

    -   [<span data-ttu-id="4114d-112">Kompilované Xaml</span><span class="sxs-lookup"><span data-stu-id="4114d-112">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

    -   [<span data-ttu-id="4114d-113">Volný Xaml</span><span class="sxs-lookup"><span data-stu-id="4114d-113">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

-   [<span data-ttu-id="4114d-114">Používat výrazy jazyka C# ve službách pracovních postupů XAMLX</span><span class="sxs-lookup"><span data-stu-id="4114d-114">Using C# expressions in XAMLX workflow services</span></span>](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a> <span data-ttu-id="4114d-115">Použití výrazy jazyka C# v Návrháři postupu provádění</span><span class="sxs-lookup"><span data-stu-id="4114d-115">Using C# expressions in the Workflow Designer</span></span>
 <span data-ttu-id="4114d-116">Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporované ve Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="4114d-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="4114d-117">Projekty pracovního postupu C# vytvořené v sadě Visual Studio 2012, které se zaměřují [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] používat výrazy jazyka C#, zatímco projekty pracovního postupu Visual Basic používat výrazy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4114d-117">C# workflow projects created in Visual Studio 2012 that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="4114d-118">K určení požadovaných výraz C#, zadejte do pole s popiskem **zadejte výraz C#**.</span><span class="sxs-lookup"><span data-stu-id="4114d-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="4114d-119">Při výběru aktivity v návrháři, nebo na aktivitu v Návrháři postupu provádění, zobrazí se tento popisek v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4114d-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="4114d-120">V následujícím příkladu dvě `WriteLine` aktivity jsou obsaženy v rámci `Sequence` uvnitř `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="4114d-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>

 <span data-ttu-id="4114d-121">![Automaticky vytvořit sekvenční aktivitu](./media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="4114d-121">![Automatically created sequence activity](./media/autosurround2.png "AutoSurround2")</span></span>

> [!NOTE]
>  <span data-ttu-id="4114d-122">Výrazy jazyka C# jsou podporovány pouze v sadě Visual Studio a nejsou podporovány v Návrháři znovu hostovaných pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="4114d-122">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="4114d-123">Další informace o nových funkcích WF45 podporované v Návrháři znovu hostované najdete v tématu [podpora nových funkcí Workflow Foundation 4.5 v Návrháři postupu provádění se změněným hostováním](wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4114d-123">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](wf-features-in-the-rehosted-workflow-designer.md).</span></span>

#### <a name="BackwardCompat"></a> <span data-ttu-id="4114d-124">Zpětné kompatibility</span><span class="sxs-lookup"><span data-stu-id="4114d-124">Backwards compatibility</span></span>
 <span data-ttu-id="4114d-125">Výrazy jazyka Visual Basic v existujícím [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projekty jazyka C# pracovního postupu, které se migrovaly na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="4114d-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="4114d-126">Při výrazy jazyka Visual Basic jsou zobrazení v Návrháři postupu provádění, existující výrazu jazyka Visual Basic se nahrazuje s **hodnota byla nastavená v XAML**, pokud výraz jazyka Visual Basic je platná syntaxe jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4114d-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="4114d-127">Výraz jazyka Visual Basic je platná syntaxe jazyka C#, se zobrazí výraz.</span><span class="sxs-lookup"><span data-stu-id="4114d-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="4114d-128">K aktualizaci výrazy jazyka Visual Basic do jazyka C#, můžete upravit v Návrháři pracovních postupů a určení ekvivalentních výrazů C#.</span><span class="sxs-lookup"><span data-stu-id="4114d-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="4114d-129">Není potřeba aktualizovat výrazy jazyka Visual Basic do jazyka C#, ale po výrazy jsou aktualizovány v Návrháři pracovních postupů jsou převedeny do jazyka C# a nemusí vrátit do jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4114d-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>

### <a name="CodeWorkflows"></a> <span data-ttu-id="4114d-130">Používání výrazy jazyka C# v pracovních postupech kódu</span><span class="sxs-lookup"><span data-stu-id="4114d-130">Using C# expressions in code workflows</span></span>
 <span data-ttu-id="4114d-131">Výrazy jazyka C# jsou podporovány v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovní postupy založené na kódu, ale předtím, než pracovní postup může být vyvolána výrazy jazyka C# musí být kompilováno s použitím <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4114d-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4114d-132">Autoři pracovního postupu můžete použít `CSharpValue` představující r výrazu a `CSharpReference` k reprezentaci l hodnoty výrazu.</span><span class="sxs-lookup"><span data-stu-id="4114d-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="4114d-133">V následujícím příkladu se vytvoří pracovní postup s `Assign` aktivity a `WriteLine` aktivity obsažené v `Sequence` aktivity.</span><span class="sxs-lookup"><span data-stu-id="4114d-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="4114d-134">A `CSharpReference` je určená pro `To` argument `Assign`a představuje l hodnotou výrazu.</span><span class="sxs-lookup"><span data-stu-id="4114d-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="4114d-135">A `CSharpValue` je určená pro `Value` argument `Assign`a `Text` argument `WriteLine`a představuje r-value u těchto dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="4114d-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>

```csharp
Variable<int> n = new Variable<int>
{
    Name = "n"
};

Activity wf = new Sequence
{
    Variables = { n },
    Activities =
    {
        new Assign<int>
        {
            To = new CSharpReference<int>("n"),
            Value = new CSharpValue<int>("new Random().Next(1, 101)")
        },
        new WriteLine
        {
            Text = new CSharpValue<string>("\"The number is \" + n")
        }
    }
};

CompileExpressions(wf);

WorkflowInvoker.Invoke(wf);
```

 <span data-ttu-id="4114d-136">Po pracovního postupu je vytvořena, výrazy jazyka C# jsou kompilovány pomocí volání `CompileExpressions` vyvolání Pomocná metoda a potom pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4114d-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="4114d-137">V následujícím příkladu je `CompileExpressions` metody.</span><span class="sxs-lookup"><span data-stu-id="4114d-137">The following example is the `CompileExpressions` method.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

> [!NOTE]
>  <span data-ttu-id="4114d-138">Pokud C# výrazy nejsou zkompilovány, <xref:System.NotSupportedException> je vyvolána, když uživatel vyvolá pracovní postup a zobrazí se zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="4114d-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="4114d-139">Ujistěte se prosím, že pracovní postup byl zkompilován. "</span><span class="sxs-lookup"><span data-stu-id="4114d-139">Please ensure that the workflow has been compiled.\`</span></span>

 <span data-ttu-id="4114d-140">Pokud váš vlastní kód na základě pracovní postup používá `DynamicActivity`, pak některé změny `CompileExpressions` metody jsou povinné, jak je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4114d-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>

```csharp
static void CompileExpressions(DynamicActivity dynamicActivity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions. For Dynamic Activities this can be retrieved using the
    // name property , which must be in the form Namespace.Type.
    string activityName = dynamicActivity.Name;

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = dynamicActivity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = true
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(
        dynamicActivity, compiledExpressionRoot);
}
```

 <span data-ttu-id="4114d-141">Existuje několik rozdílů v `CompileExpressions` přetížení, které zkompiluje výrazy jazyka C# v dynamické aktivity.</span><span class="sxs-lookup"><span data-stu-id="4114d-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>

-   <span data-ttu-id="4114d-142">Parametr `CompileExpressions` je `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="4114d-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>

-   <span data-ttu-id="4114d-143">Název typu a obor názvů se načítají pomocí `DynamicActivity.Name` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4114d-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>

-   <span data-ttu-id="4114d-144">`TextExpressionCompilerSettings.ForImplementation` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="4114d-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>

-   <span data-ttu-id="4114d-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` je volána místo `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="4114d-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>

 <span data-ttu-id="4114d-146">Další informace o práci s výrazy v kódu, naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="4114d-146">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

### <a name="XamlWorkflows"></a> <span data-ttu-id="4114d-147">Používání výrazy jazyka C# v pracovních postupech XAML</span><span class="sxs-lookup"><span data-stu-id="4114d-147">Using C# expressions in XAML workflows</span></span>
 <span data-ttu-id="4114d-148">Výrazy jazyka C# jsou podporovány v pracovních postupech XAML.</span><span class="sxs-lookup"><span data-stu-id="4114d-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="4114d-149">Kompilované pracovních postupů XAML jsou kompilovány do typu, a dojde ke ztrátě pracovních postupů XAML načten modulem runtime a zkompilovány do strom aktivity při spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4114d-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>

-   [<span data-ttu-id="4114d-150">Kompilované Xaml</span><span class="sxs-lookup"><span data-stu-id="4114d-150">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

-   [<span data-ttu-id="4114d-151">Volný Xaml</span><span class="sxs-lookup"><span data-stu-id="4114d-151">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a> <span data-ttu-id="4114d-152">Kompilované Xaml</span><span class="sxs-lookup"><span data-stu-id="4114d-152">Compiled Xaml</span></span>
 <span data-ttu-id="4114d-153">Výrazy jazyka C# jsou podporovány v kompilovaných pracovních postupech XAML, které jsou kompilovány do typu jako součást projektu jazyka C# pracovního postupu, který se zaměřuje [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4114d-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="4114d-154">Kompilované XAML je výchozí typ pracovního postupu pro vytváření ve Visual Studiu a projekty pracovního postupu C# vytvořené v sadě Visual Studio, které se zaměřují [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] používat výrazy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4114d-154">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>

#### <a name="LooseXaml"></a> <span data-ttu-id="4114d-155">Volný Xaml</span><span class="sxs-lookup"><span data-stu-id="4114d-155">Loose Xaml</span></span>
 <span data-ttu-id="4114d-156">Výrazy jazyka C# jsou podporovány v pracovních postupech volný XAML.</span><span class="sxs-lookup"><span data-stu-id="4114d-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="4114d-157">Program hostitele pracovního postupu, který načte a vyvolá volný XAML workflowu, musí jako cíl [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], a <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musí být nastaveno na `true` (výchozí hodnota je `false`).</span><span class="sxs-lookup"><span data-stu-id="4114d-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="4114d-158">Nastavit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> k `true`, vytvořit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na hodnotu `true`a předáváme jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4114d-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4114d-159">Pokud `CompileExpressions` není nastavená na `true`, <xref:System.NotSupportedException> bude vyvolána a zobrazí se zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="4114d-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="4114d-160">Ujistěte se prosím, že pracovní postup byl zkompilován. "</span><span class="sxs-lookup"><span data-stu-id="4114d-160">Please ensure that the workflow has been compiled.\`</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

 <span data-ttu-id="4114d-161">Další informace o práci s pracovními postupy XAML najdete v tématu [serializace pracovních postupů a aktivit do a z XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4114d-161">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

### <a name="WFServices"></a> <span data-ttu-id="4114d-162">Používat výrazy jazyka C# ve službách pracovních postupů XAMLX</span><span class="sxs-lookup"><span data-stu-id="4114d-162">Using C# expressions in XAMLX workflow services</span></span>
 <span data-ttu-id="4114d-163">Výrazy jazyka C# jsou podporovány v XAMLX služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="4114d-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="4114d-164">Když jsou služby pracovního postupu je hostované v IIS nebo WAS pak nejsou vyžadovány žádné další kroky, ale služba pracovního postupu XAML je samoobslužně hostovaná, musí být kompilována výrazy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4114d-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="4114d-165">Chcete-li zkompilovat výrazy jazyka C# v místním prostředí služby pracovního postupu XAMLX, nejdřív načtěte soubor XAMLX do `WorkflowService`a pak předejte `Body` z `WorkflowService` k `CompileExpressions` metody popsané v předchozí [pomocí jazyka C# výrazy v pracovních postupech kód](csharp-expressions.md#CodeWorkflows) oddílu.</span><span class="sxs-lookup"><span data-stu-id="4114d-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="4114d-166">V následujícím příkladu XAMLX služby pracovního postupu je načtena, jsou zkompilovány výrazy jazyka C# a potom služba pracovního postupu je otevřený a čeká na požadavky.</span><span class="sxs-lookup"><span data-stu-id="4114d-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>

```csharp
// Load the XAMLX workflow service.
WorkflowService workflow1 =
    (WorkflowService)XamlServices.Load(xamlxPath);

// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.
CompileExpressions(workflow1.Body);

// Initialize the WorkflowServiceHost.
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));

// Enable Metadata publishing/
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
smb.HttpGetEnabled = true;
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;
host.Description.Behaviors.Add(smb);

// Open the WorkflowServiceHost and wait for requests.
host.Open();
Console.WriteLine("Press enter to quit");
Console.ReadLine();
```

 <span data-ttu-id="4114d-167">Pokud nejsou výrazy jazyka C# zkompilovány, `Open` operace úspěšná, ale pracovní postup se nezdaří, pokud je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="4114d-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="4114d-168">Následující `CompileExpressions` metodu je stejná jako metoda z předchozího [výrazy pomocí jazyka C# v pracovních postupech kód](csharp-expressions.md#CodeWorkflows) oddílu.</span><span class="sxs-lookup"><span data-stu-id="4114d-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```
