---
title: "Výrazy jazyka C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7d62d147bdc0177a28dbcc7d235f1c48dc51460
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="c-expressions"></a><span data-ttu-id="66ae9-102">Výrazy jazyka C#</span><span class="sxs-lookup"><span data-stu-id="66ae9-102">C# Expressions</span></span>
<span data-ttu-id="66ae9-103">Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporovány v [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66ae9-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="66ae9-104">Nové projekty workflow C# vytvořené v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] cílených [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] použití jazyka C# výrazy a pracovní postup projekty Visual Basic použití výrazů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66ae9-104">New C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="66ae9-105">Existující [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projekty workflow, které používají výrazy jazyka Visual Basic mohou být migrovány do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bez ohledu na projekt jazyka a jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="66ae9-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="66ae9-106">Toto téma obsahuje přehled výrazy jazyka C# v [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66ae9-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>  
  
## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="66ae9-107">Pomocí jazyka C# výrazů v pracovních postupech</span><span class="sxs-lookup"><span data-stu-id="66ae9-107">Using C# expressions in workflows</span></span>  
  
-   [<span data-ttu-id="66ae9-108">Pomocí jazyka C# výrazů v Návrháři pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="66ae9-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [<span data-ttu-id="66ae9-109">Zpětné kompatibility</span><span class="sxs-lookup"><span data-stu-id="66ae9-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [<span data-ttu-id="66ae9-110">Pomocí jazyka C# výrazů v pracovních postupech kódu</span><span class="sxs-lookup"><span data-stu-id="66ae9-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [<span data-ttu-id="66ae9-111">Pomocí jazyka C# výrazů v pracovních postupech XAML</span><span class="sxs-lookup"><span data-stu-id="66ae9-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [<span data-ttu-id="66ae9-112">Kompilované Xaml</span><span class="sxs-lookup"><span data-stu-id="66ae9-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [<span data-ttu-id="66ae9-113">Přijít Xaml</span><span class="sxs-lookup"><span data-stu-id="66ae9-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [<span data-ttu-id="66ae9-114">Použití jazyka C# výrazů v XAMLX služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="66ae9-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <span data-ttu-id="66ae9-115"><a name="WFDesigner"></a>Pomocí jazyka C# výrazů v Návrháři pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="66ae9-115"><a name="WFDesigner"></a> Using C# expressions in the Workflow Designer</span></span>  
 <span data-ttu-id="66ae9-116">Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporovány v [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66ae9-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="66ae9-117">Pracovní postup projektů C# vytvořené v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] cílených [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] použití jazyka C# výrazů, zatímco projekty Visual Basic pracovní postup použití výrazů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66ae9-117">C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="66ae9-118">Chcete-li zadat požadované výraz jazyka C#, zadejte ji do pole s názvem bez přípony **zadejte výraz jazyka C#**.</span><span class="sxs-lookup"><span data-stu-id="66ae9-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="66ae9-119">Tento popisek se zobrazí v okně vlastností, pokud aktivita je vybrána v Návrháři nebo na aktivity v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="66ae9-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="66ae9-120">V následujícím příkladu dvě `WriteLine` aktivity jsou obsaženy v rámci `Sequence` uvnitř `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="66ae9-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>  
  
 <span data-ttu-id="66ae9-121">![Automaticky vytvoří aktivity pořadí](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="66ae9-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66ae9-122">Výrazy jazyka C# jsou podporovány pouze v [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]a nejsou podporovány v Návrháři znovu hostovaných pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="66ae9-122">C# expressions are supported only in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and are not supported in the re-hosted workflow designer.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="66ae9-123">nové funkce WF45 podporované v Návrháři znovu hostované, viz [podporu pro nové funkce Workflow Foundation 4.5 v Návrháři pracovních postupů opětovné hostování nástroje](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="66ae9-123"> new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>  
  
####  <span data-ttu-id="66ae9-124"><a name="BackwardCompat"></a>Zpětné kompatibility</span><span class="sxs-lookup"><span data-stu-id="66ae9-124"><a name="BackwardCompat"></a> Backwards compatibility</span></span>  
 <span data-ttu-id="66ae9-125">Výrazy jazyka Visual Basic v existující [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# projekty workflow, které se migrovaly [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="66ae9-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="66ae9-126">Když jsou výrazy jazyka Visual Basic zobrazit v Návrháři pracovních postupů, se nahradí text existující výrazu jazyka Visual Basic **v jazyce XAML byla nastavena hodnota**, pokud výraz jazyka Visual Basic je platné syntaxe jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="66ae9-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="66ae9-127">Pokud je jazyka Visual Basic výrazem platnou syntaxi C#, se zobrazí ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="66ae9-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="66ae9-128">Pokud chcete aktualizovat jazyka Visual Basic výrazy jazyka C#, můžete upravovat v Návrháři pracovních postupů a zadejte ekvivalentních výrazů jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="66ae9-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="66ae9-129">Není potřeba aktualizovat výrazy jazyka Visual Basic, C#, ale po výrazy jsou aktualizovány v Návrháři pracovních postupů se převedou do jazyka C# a nemusí se vrátí zpátky na Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66ae9-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>  
  
###  <span data-ttu-id="66ae9-130"><a name="CodeWorkflows"></a>Pomocí jazyka C# výrazů v pracovních postupech kódu</span><span class="sxs-lookup"><span data-stu-id="66ae9-130"><a name="CodeWorkflows"></a> Using C# expressions in code workflows</span></span>  
 <span data-ttu-id="66ae9-131">Výrazy jazyka C# jsou podporovány v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovní postupy založené na kódu, ale předtím, než pracovní postup nelze vyvolat musí být zkompilovány výrazy jazyka C# pomocí <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66ae9-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66ae9-132">Autoři pracovního postupu můžete použít `CSharpValue` představují r-value výrazu, a `CSharpReference` představují l hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="66ae9-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="66ae9-133">V následujícím příkladu se vytvoří pracovní postup s `Assign` aktivity a `WriteLine` aktivity, které jsou součástí `Sequence` aktivity.</span><span class="sxs-lookup"><span data-stu-id="66ae9-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="66ae9-134">A `CSharpReference` pro je zadána `To` argument `Assign`a představuje l hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="66ae9-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="66ae9-135">A `CSharpValue` je zadán pro `Value` argument `Assign`a `Text` argument `WriteLine`a představuje r-value pro těchto dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="66ae9-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>  
  
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
  
 <span data-ttu-id="66ae9-136">Poté, co je pracovní postup vytvořený, výrazy jazyka C# jsou kompilovaná volání `CompileExpressions` je volána metoda helper a pak pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="66ae9-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="66ae9-137">Následující příklad je `CompileExpressions` metoda.</span><span class="sxs-lookup"><span data-stu-id="66ae9-137">The following example is the `CompileExpressions` method.</span></span>  
  
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
>  <span data-ttu-id="66ae9-138">Pokud nejsou kompilovány výrazy jazyka C#, <xref:System.NotSupportedException> se vyvolá, když pracovní postup vyvolání zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilace aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="66ae9-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="66ae9-139">Zkontrolujte, že pracovní postup byl zkompilován. "</span><span class="sxs-lookup"><span data-stu-id="66ae9-139">Please ensure that the workflow has been compiled.\`</span></span>  
  
 <span data-ttu-id="66ae9-140">Pokud váš vlastní kód na základě pracovní postup používá `DynamicActivity`, pak některé změny `CompileExpressions` metoda jsou povinné, jak je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="66ae9-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="66ae9-141">Existuje několik rozdílů v `CompileExpressions` přetížení, které zkompiluje výrazy jazyka C# v dynamické aktivity.</span><span class="sxs-lookup"><span data-stu-id="66ae9-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>  
  
-   <span data-ttu-id="66ae9-142">Parametr pro `CompileExpressions` je `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="66ae9-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>  
  
-   <span data-ttu-id="66ae9-143">Název typu a obor názvů se načítají pomocí `DynamicActivity.Name` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="66ae9-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>  
  
-   <span data-ttu-id="66ae9-144">`TextExpressionCompilerSettings.ForImplementation`je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="66ae9-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>  
  
-   <span data-ttu-id="66ae9-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation`je volána místo `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="66ae9-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="66ae9-146">Práce s výrazy v kódu, najdete v části [vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kód](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="66ae9-146"> working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
###  <span data-ttu-id="66ae9-147"><a name="XamlWorkflows"></a>Pomocí jazyka C# výrazů v pracovních postupech XAML</span><span class="sxs-lookup"><span data-stu-id="66ae9-147"><a name="XamlWorkflows"></a> Using C# expressions in XAML workflows</span></span>  
 <span data-ttu-id="66ae9-148">Výrazy jazyka C# jsou podporovány v pracovních postupech XAML.</span><span class="sxs-lookup"><span data-stu-id="66ae9-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="66ae9-149">Kompilované pracovních postupů XAML se zkompiluje do typu, a jsou přijít pracovních postupů XAML načten modulem runtime a zkompilovat do strom aktivity při spuštění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="66ae9-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>  
  
-   [<span data-ttu-id="66ae9-150">Kompilované Xaml</span><span class="sxs-lookup"><span data-stu-id="66ae9-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [<span data-ttu-id="66ae9-151">Přijít Xaml</span><span class="sxs-lookup"><span data-stu-id="66ae9-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <span data-ttu-id="66ae9-152"><a name="CompiledXaml"></a>Kompilované Xaml</span><span class="sxs-lookup"><span data-stu-id="66ae9-152"><a name="CompiledXaml"></a> Compiled Xaml</span></span>  
 <span data-ttu-id="66ae9-153">Výrazy jazyka C# jsou podporovány v kompilovaných pracovních postupech XAML, které zjišťují typu jako součást pracovního postupu projektu C#, jehož cílem [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66ae9-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="66ae9-154">Kompilované XAML je výchozí typ pracovního postupu vytváření obsahu v [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], a pracovní postup projektů C# vytvoří v [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] cílených [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] použití jazyka C# výrazů.</span><span class="sxs-lookup"><span data-stu-id="66ae9-154">Compiled XAML is the default type of workflow authoring in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and C# workflow projects created in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>  
  
####  <span data-ttu-id="66ae9-155"><a name="LooseXaml"></a>Přijít Xaml</span><span class="sxs-lookup"><span data-stu-id="66ae9-155"><a name="LooseXaml"></a> Loose Xaml</span></span>  
 <span data-ttu-id="66ae9-156">Výrazy jazyka C# jsou podporovány v přijít pracovních postupech XAML.</span><span class="sxs-lookup"><span data-stu-id="66ae9-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="66ae9-157">Musí mít jako cíl pracovního postupu hostitelského programu, který načte a vyvolá přijít XAML pracovního postupu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], a <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musí být nastavena na `true` (výchozí hodnota je `false`).</span><span class="sxs-lookup"><span data-stu-id="66ae9-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="66ae9-158">Chcete-li nastavit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> k `true`, vytvořit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na hodnotu `true`a předáváme jako parametr, který se <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66ae9-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66ae9-159">Pokud `CompileExpressions` není nastavený na `true`, <xref:System.NotSupportedException> bude vyvolána s zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilace aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="66ae9-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="66ae9-160">Zkontrolujte, že pracovní postup byl zkompilován. "</span><span class="sxs-lookup"><span data-stu-id="66ae9-160">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="66ae9-161">Práce s pracovních postupů XAML, najdete v části [serializaci pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="66ae9-161"> working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
###  <span data-ttu-id="66ae9-162"><a name="WFServices"></a>Použití jazyka C# výrazů v XAMLX služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="66ae9-162"><a name="WFServices"></a> Using C# expressions in XAMLX workflow services</span></span>  
 <span data-ttu-id="66ae9-163">Výrazy jazyka C# jsou podporovány v XAMLX služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="66ae9-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="66ae9-164">Pokud služby pracovního postupu je hostován v IIS nebo WAS pak nejsou potřeba žádné další kroky, ale pokud je samoobslužně hostovaná služba XAML pracovního postupu, musí být zkompilovány výrazy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="66ae9-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="66ae9-165">Kompilace výrazy jazyka C# ve vlastním hostováním služby pracovního postupu XAMLX, nejdřív načtěte soubor XAMLX do `WorkflowService`a pak `Body` z `WorkflowService` k `CompileExpressions` metody popsané v předchozí [pomocí jazyka C# výrazy v pracovních postupech kód](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) části.</span><span class="sxs-lookup"><span data-stu-id="66ae9-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="66ae9-166">V následujícím příkladu je načtena XAMLX služby pracovních postupů, se kompilují výrazy jazyka C# a pak služby pracovního postupu je otevřen a čeká na požadavky.</span><span class="sxs-lookup"><span data-stu-id="66ae9-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>  
  
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
  
 <span data-ttu-id="66ae9-167">Pokud nejsou kompilovány výrazy jazyka C#, `Open` operace úspěšná, ale pracovní postup se nezdaří, při vyvolání.</span><span class="sxs-lookup"><span data-stu-id="66ae9-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="66ae9-168">Následující `CompileExpressions` metoda je stejná jako metoda z předchozí [pomocí jazyka C# výrazy v pracovních postupech kód](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) části.</span><span class="sxs-lookup"><span data-stu-id="66ae9-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>  
  
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
