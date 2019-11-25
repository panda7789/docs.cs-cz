---
title: Výrazy C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: d1728758a4f1af76c2d08695a83c0f9acc3dde3e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140097"
---
# <a name="c-expressions"></a><span data-ttu-id="e1d23-102">Výrazy C#</span><span class="sxs-lookup"><span data-stu-id="e1d23-102">C# Expressions</span></span>
<span data-ttu-id="e1d23-103">Počínaje .NET Framework 4,5 jsou C# výrazy podporované v programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="e1d23-103">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="e1d23-104">Nové C# projekty pracovního postupu vytvořené v aplikaci Visual Studio 2012, které cílí C# na 4,5 .NET Framework výrazy use a Visual Basic pracovního postupu, používají Visual Basic výrazy.</span><span class="sxs-lookup"><span data-stu-id="e1d23-104">New C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="e1d23-105">Stávající projekty pracovního postupu .NET Framework 4, které používají Visual Basic výrazy, lze migrovat do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bez ohledu na jazyk projektu a jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="e1d23-105">Existing .NET Framework 4 workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="e1d23-106">Toto téma poskytuje přehled C# výrazů v [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1d23-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>

## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="e1d23-107">Použití C# výrazů v pracovních postupech</span><span class="sxs-lookup"><span data-stu-id="e1d23-107">Using C# expressions in workflows</span></span>

- [<span data-ttu-id="e1d23-108">Použití C# výrazů v Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="e1d23-108">Using C# expressions in the Workflow Designer</span></span>](csharp-expressions.md#WFDesigner)

  - [<span data-ttu-id="e1d23-109">Zpětná kompatibilita</span><span class="sxs-lookup"><span data-stu-id="e1d23-109">Backwards compatibility</span></span>](csharp-expressions.md#BackwardCompat)

- [<span data-ttu-id="e1d23-110">Použití C# výrazů v pracovních postupech kódu</span><span class="sxs-lookup"><span data-stu-id="e1d23-110">Using C# expressions in code workflows</span></span>](csharp-expressions.md#CodeWorkflows)

- [<span data-ttu-id="e1d23-111">Použití C# výrazů v pracovních postupech XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-111">Using C# expressions in XAML workflows</span></span>](csharp-expressions.md#XamlWorkflows)

  - [<span data-ttu-id="e1d23-112">Zkompilovaný kód XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-112">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

  - [<span data-ttu-id="e1d23-113">Volný kód XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-113">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

- [<span data-ttu-id="e1d23-114">Použití C# výrazů ve službě xamlx Workflow Services</span><span class="sxs-lookup"><span data-stu-id="e1d23-114">Using C# expressions in XAMLX workflow services</span></span>](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a><span data-ttu-id="e1d23-115">Použití C# výrazů v Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="e1d23-115">Using C# expressions in the Workflow Designer</span></span>

<span data-ttu-id="e1d23-116">Počínaje .NET Framework 4,5 jsou C# výrazy podporované v programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="e1d23-116">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="e1d23-117">C#projekty pracovního postupu vytvořené v aplikaci Visual Studio 2012, které cílí C# na .NET Framework 4,5 výrazy use, zatímco Visual Basic projekty pracovního postupu používají Visual Basic výrazy.</span><span class="sxs-lookup"><span data-stu-id="e1d23-117">C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="e1d23-118">Chcete-li zadat C# požadovaný výraz, zadejte ho do pole s popiskem **zadat C# výraz**.</span><span class="sxs-lookup"><span data-stu-id="e1d23-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="e1d23-119">Tento popisek se zobrazí v okně vlastnosti, když je aktivita vybrána v Návrháři nebo v aktivitě v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e1d23-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="e1d23-120">V následujícím příkladu jsou dvě aktivity `WriteLine` obsaženy v rámci `Sequence` uvnitř `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="e1d23-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>

![Snímek obrazovky zobrazující automaticky vytvořenou aktivitu sekvence](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> <span data-ttu-id="e1d23-122">C#výrazy jsou podporovány pouze v aplikaci Visual Studio a nejsou podporovány v Návrháři opětovného hostovaného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e1d23-122">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="e1d23-123">Další informace o nových funkcích WF45 podporovaných v opětovném hostovaném návrháři najdete v článku [Podpora nových funkcí pracovního postupu 4,5 v článku Návrhář postupu provádění hostitele](wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e1d23-123">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](wf-features-in-the-rehosted-workflow-designer.md).</span></span>

#### <a name="BackwardCompat"></a><span data-ttu-id="e1d23-124">Zpětná kompatibilita</span><span class="sxs-lookup"><span data-stu-id="e1d23-124">Backwards compatibility</span></span>

<span data-ttu-id="e1d23-125">Podporovány jsou Visual Basic výrazy v existujících C# projektech pracovních postupů .NET Framework 4, které byly migrovány do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1d23-125">Visual Basic expressions in existing .NET Framework 4 C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="e1d23-126">Pokud jsou výrazy Visual Basic zobrazeny v Návrháři sledu prací, text stávajícího výrazu Visual Basic je nahrazen **hodnotou nastavenou v jazyce XAML**, pokud výraz Visual Basic není platná C# syntaxe.</span><span class="sxs-lookup"><span data-stu-id="e1d23-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="e1d23-127">Pokud je výraz Visual Basic platnou C# syntaxí, zobrazí se výraz.</span><span class="sxs-lookup"><span data-stu-id="e1d23-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="e1d23-128">Chcete-li aktualizovat Visual Basic výrazy C#na, můžete je upravit v Návrháři pracovních postupů a zadat ekvivalentní C# výraz.</span><span class="sxs-lookup"><span data-stu-id="e1d23-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="e1d23-129">Není nutné aktualizovat Visual Basic výrazy na C#, ale po aktualizaci výrazů v Návrháři pracovního postupu jsou převedeny na C# a nemusí být vráceny zpět na Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e1d23-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>

### <a name="CodeWorkflows"></a><span data-ttu-id="e1d23-130">Použití C# výrazů v pracovních postupech kódu</span><span class="sxs-lookup"><span data-stu-id="e1d23-130">Using C# expressions in code workflows</span></span>

<span data-ttu-id="e1d23-131">C#výrazy jsou podporované v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovních postupech na základě kódu, ale před vyvoláním pracovního C# postupu musí být výrazy kompilovány pomocí <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1d23-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1d23-132">Autoři pracovního postupu můžou použít `CSharpValue` k vyjádření hodnoty r výrazu a `CSharpReference` k reprezentaci l-Value výrazu.</span><span class="sxs-lookup"><span data-stu-id="e1d23-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="e1d23-133">V následujícím příkladu je vytvořen pracovní postup s aktivitou `Assign` a aktivitou `WriteLine` obsaženou v `Sequence` aktivitě.</span><span class="sxs-lookup"><span data-stu-id="e1d23-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="e1d23-134">Pro argument `To` `Assign`je určena `CSharpReference` a představuje l-hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="e1d23-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="e1d23-135">`CSharpValue` je určena pro `Value` argument `Assign`a pro `Text` argument `WriteLine`a představuje hodnotu r pro tyto dva výrazy.</span><span class="sxs-lookup"><span data-stu-id="e1d23-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>

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

<span data-ttu-id="e1d23-136">Po vytvoření pracovního postupu jsou C# výrazy kompilovány voláním pomocné metody `CompileExpressions` a následně vyvoláním pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e1d23-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="e1d23-137">Následující příklad je metoda `CompileExpressions`.</span><span class="sxs-lookup"><span data-stu-id="e1d23-137">The following example is the `CompileExpressions` method.</span></span>

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
> <span data-ttu-id="e1d23-138">Pokud nejsou C# výrazy kompilovány, je vyvolána <xref:System.NotSupportedException>, když je pracovní postup vyvolán pomocí zprávy podobné následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="e1d23-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="e1d23-139">Ujistěte se prosím, že byl pracovní postup zkompilován. '</span><span class="sxs-lookup"><span data-stu-id="e1d23-139">Please ensure that the workflow has been compiled.\`</span></span>

<span data-ttu-id="e1d23-140">Pokud vlastní pracovní postup založený na kódu používá `DynamicActivity`, pak některé změny metody `CompileExpressions` jsou požadovány, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e1d23-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>

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

<span data-ttu-id="e1d23-141">Existuje několik rozdílů v `CompileExpressions` přetížení, které kompiluje C# výrazy v dynamické aktivitě.</span><span class="sxs-lookup"><span data-stu-id="e1d23-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>

- <span data-ttu-id="e1d23-142">Parametr pro `CompileExpressions` je `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="e1d23-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>

- <span data-ttu-id="e1d23-143">Název typu a obor názvů se načítají pomocí vlastnosti `DynamicActivity.Name`.</span><span class="sxs-lookup"><span data-stu-id="e1d23-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>

- <span data-ttu-id="e1d23-144">`TextExpressionCompilerSettings.ForImplementation` je nastavená na `true`.</span><span class="sxs-lookup"><span data-stu-id="e1d23-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>

- <span data-ttu-id="e1d23-145">místo `CompiledExpressionInvoker.SetCompiledExpressionRoot`je volána `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation`.</span><span class="sxs-lookup"><span data-stu-id="e1d23-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>

<span data-ttu-id="e1d23-146">Další informace o práci s výrazy v kódu naleznete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="e1d23-146">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

### <a name="XamlWorkflows"></a><span data-ttu-id="e1d23-147">Použití C# výrazů v pracovních postupech XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-147">Using C# expressions in XAML workflows</span></span>

<span data-ttu-id="e1d23-148">C#výrazy jsou podporovány v pracovních postupech XAML.</span><span class="sxs-lookup"><span data-stu-id="e1d23-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="e1d23-149">Zkompilované pracovní postupy XAML jsou kompilovány do typu a volné pracovní postupy XAML jsou načteny modulem runtime a kompilovány do stromu aktivity při spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e1d23-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>

- [<span data-ttu-id="e1d23-150">Zkompilovaný kód XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-150">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

- [<span data-ttu-id="e1d23-151">Volný kód XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-151">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a><span data-ttu-id="e1d23-152">Zkompilovaný kód XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-152">Compiled Xaml</span></span>

<span data-ttu-id="e1d23-153">C#výrazy jsou podporovány v kompilovaných pracovních postupech XAML, které jsou kompilovány do typu jako C# součást projektu pracovního postupu, který cílí na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1d23-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="e1d23-154">Zkompilovaný kód XAML je výchozí typ vytváření pracovních postupů v aplikaci Visual Studio a C# projekty pracovního postupu vytvořené v aplikaci Visual Studio, které C# cílí na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] výrazy použití.</span><span class="sxs-lookup"><span data-stu-id="e1d23-154">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>

#### <a name="LooseXaml"></a><span data-ttu-id="e1d23-155">Volný kód XAML</span><span class="sxs-lookup"><span data-stu-id="e1d23-155">Loose Xaml</span></span>

<span data-ttu-id="e1d23-156">C#výrazy jsou podporovány v volných pracovních postupech XAML.</span><span class="sxs-lookup"><span data-stu-id="e1d23-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="e1d23-157">Hostitelský program pracovního postupu, který načte a vyvolá volný pracovní postup XAML, musí cílit na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]a <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musí být nastaven na `true` (výchozí hodnota je `false`).</span><span class="sxs-lookup"><span data-stu-id="e1d23-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="e1d23-158">Chcete-li nastavit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true`, vytvořte instanci <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> s vlastností <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> nastavenou na hodnotu `true`a předejte ji jako parametr pro <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1d23-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1d23-159">Pokud `CompileExpressions` není nastavená na `true`, bude vyvolána <xref:System.NotSupportedException> zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="e1d23-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="e1d23-160">Ujistěte se prosím, že byl pracovní postup zkompilován. '</span><span class="sxs-lookup"><span data-stu-id="e1d23-160">Please ensure that the workflow has been compiled.\`</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="e1d23-161">Další informace o práci s pracovními postupy XAML naleznete v tématu [serializace pracovních postupů a aktivit do a z jazyka XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="e1d23-161">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

### <a name="WFServices"></a><span data-ttu-id="e1d23-162">Použití C# výrazů ve službě xamlx Workflow Services</span><span class="sxs-lookup"><span data-stu-id="e1d23-162">Using C# expressions in XAMLX workflow services</span></span>

<span data-ttu-id="e1d23-163">C#ve službách pracovního postupu XAMLX jsou podporované výrazy.</span><span class="sxs-lookup"><span data-stu-id="e1d23-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="e1d23-164">Když je služba pracovního postupu hostovaná ve službě IIS nebo se nevyžadují žádné další kroky, ale pokud je služba pracovního postupu XAML v místním prostředí, pak C# se výrazy musí zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="e1d23-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="e1d23-165">Chcete-li C# kompilovat výrazy ve službě xamlx pracovního postupu v místním prostředí, načtěte soubor XAMLX do `WorkflowService`a pak předejte `Body` `WorkflowService` do metody `CompileExpressions` popsané v části předchozí [výrazy using C# v tématu pracovní postupy kódu](csharp-expressions.md#CodeWorkflows) .</span><span class="sxs-lookup"><span data-stu-id="e1d23-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="e1d23-166">V následujícím příkladu je načtena služba XAMLX Workflow, C# výrazy jsou kompilovány a poté je spuštěna služba pracovního postupu, která čeká na požadavky.</span><span class="sxs-lookup"><span data-stu-id="e1d23-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>

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

<span data-ttu-id="e1d23-167">Pokud nejsou C# výrazy kompilovány, `Open` operace proběhne úspěšně, ale pracovní postup selže při jeho vyvolání.</span><span class="sxs-lookup"><span data-stu-id="e1d23-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="e1d23-168">Následující metoda `CompileExpressions` je shodná s metodou z předchozích [výrazů using C# v části pracovní postupy kódu](csharp-expressions.md#CodeWorkflows) .</span><span class="sxs-lookup"><span data-stu-id="e1d23-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span>

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
