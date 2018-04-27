---
title: Výrazy jazyka C#
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17528db182676ae69694c4e416ee10bff1ae6ef2
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="c-expressions"></a>Výrazy jazyka C#
Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporovány v systému Windows Workflow Foundation (WF). Nové projekty workflow C# vytvořené v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] cílených [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] použití jazyka C# výrazy a pracovní postup projekty Visual Basic použití výrazů jazyka Visual Basic. Existující [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projekty workflow, které používají výrazy jazyka Visual Basic mohou být migrovány do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bez ohledu na projekt jazyka a jsou podporovány. Toto téma obsahuje přehled výrazy jazyka C# v [!INCLUDE[wf1](../../../includes/wf1-md.md)].  
  
## <a name="using-c-expressions-in-workflows"></a>Pomocí jazyka C# výrazů v pracovních postupech  
  
-   [Pomocí jazyka C# výrazů v Návrháři pracovních postupů](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [Zpětné kompatibility](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [Pomocí jazyka C# výrazů v pracovních postupech kódu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [Pomocí jazyka C# výrazů v pracovních postupech XAML](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [Kompilované Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [Přijít Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [Použití jazyka C# výrazů v XAMLX služeb pracovních postupů](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <a name="WFDesigner"></a> Pomocí jazyka C# výrazů v Návrháři pracovních postupů  
 Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporovány v systému Windows Workflow Foundation (WF). Pracovní postup projektů C# vytvořené v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] cílených [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] použití jazyka C# výrazů, zatímco projekty Visual Basic pracovní postup použití výrazů jazyka Visual Basic. Chcete-li zadat požadované výraz jazyka C#, zadejte ji do pole s názvem bez přípony **zadejte výraz jazyka C#**. Tento popisek se zobrazí v okně vlastností, pokud aktivita je vybrána v Návrháři nebo na aktivity v Návrháři pracovních postupů. V následujícím příkladu dvě `WriteLine` aktivity jsou obsaženy v rámci `Sequence` uvnitř `NoPersistScope`.  
  
 ![Automaticky vytvoří aktivity pořadí](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
> [!NOTE]
>  Výrazy jazyka C# jsou podporovány pouze v sadě Visual Studio a nejsou podporovány v Návrháři znovu hostovaných pracovních postupů. [!INCLUDE[crabout](../../../includes/crabout-md.md)] nové funkce WF45 podporované v Návrháři znovu hostované, viz [podporu pro nové funkce Workflow Foundation 4.5 v Návrháři pracovních postupů opětovné hostování nástroje](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).  
  
####  <a name="BackwardCompat"></a> Zpětné kompatibility  
 Výrazy jazyka Visual Basic v existující [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# projekty workflow, které se migrovaly [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou podporovány. Když jsou výrazy jazyka Visual Basic zobrazit v Návrháři pracovních postupů, se nahradí text existující výrazu jazyka Visual Basic **v jazyce XAML byla nastavena hodnota**, pokud výraz jazyka Visual Basic je platné syntaxe jazyka C#. Pokud je jazyka Visual Basic výrazem platnou syntaxi C#, se zobrazí ve výrazu. Pokud chcete aktualizovat jazyka Visual Basic výrazy jazyka C#, můžete upravovat v Návrháři pracovních postupů a zadejte ekvivalentních výrazů jazyka C#. Není potřeba aktualizovat výrazy jazyka Visual Basic, C#, ale po výrazy jsou aktualizovány v Návrháři pracovních postupů se převedou do jazyka C# a nemusí se vrátí zpátky na Visual Basic.  
  
###  <a name="CodeWorkflows"></a> Pomocí jazyka C# výrazů v pracovních postupech kódu  
 Výrazy jazyka C# jsou podporovány v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovní postupy založené na kódu, ale předtím, než pracovní postup nelze vyvolat musí být zkompilovány výrazy jazyka C# pomocí <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. Autoři pracovního postupu můžete použít `CSharpValue` představují r-value výrazu, a `CSharpReference` představují l hodnotu výrazu. V následujícím příkladu se vytvoří pracovní postup s `Assign` aktivity a `WriteLine` aktivity, které jsou součástí `Sequence` aktivity. A `CSharpReference` pro je zadána `To` argument `Assign`a představuje l hodnotu výrazu. A `CSharpValue` je zadán pro `Value` argument `Assign`a `Text` argument `WriteLine`a představuje r-value pro těchto dvou výrazů.  
  
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
  
 Poté, co je pracovní postup vytvořený, výrazy jazyka C# jsou kompilovaná volání `CompileExpressions` je volána metoda helper a pak pracovního postupu. Následující příklad je `CompileExpressions` metoda.  
  
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
>  Pokud nejsou kompilovány výrazy jazyka C#, <xref:System.NotSupportedException> se vyvolá, když pracovní postup vyvolání zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilace aby bylo možné spustit.  Zkontrolujte, že pracovní postup byl zkompilován. "  
  
 Pokud váš vlastní kód na základě pracovní postup používá `DynamicActivity`, pak některé změny `CompileExpressions` metoda jsou povinné, jak je ukázáno v následujícím příkladu kódu.  
  
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
  
 Existuje několik rozdílů v `CompileExpressions` přetížení, které zkompiluje výrazy jazyka C# v dynamické aktivity.  
  
-   Parametr pro `CompileExpressions` je `DynamicActivity`.  
  
-   Název typu a obor názvů se načítají pomocí `DynamicActivity.Name` vlastnost.  
  
-   `TextExpressionCompilerSettings.ForImplementation` je nastavena na `true`.  
  
-   `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` je volána místo `CompiledExpressionInvoker.SetCompiledExpressionRoot`.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Práce s výrazy v kódu, najdete v části [vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kód](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
###  <a name="XamlWorkflows"></a> Pomocí jazyka C# výrazů v pracovních postupech XAML  
 Výrazy jazyka C# jsou podporovány v pracovních postupech XAML. Kompilované pracovních postupů XAML se zkompiluje do typu, a jsou přijít pracovních postupů XAML načten modulem runtime a zkompilovat do strom aktivity při spuštění pracovního postupu.  
  
-   [Kompilované Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [Přijít Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <a name="CompiledXaml"></a> Kompilované Xaml  
 Výrazy jazyka C# jsou podporovány v kompilovaných pracovních postupech XAML, které zjišťují typu jako součást pracovního postupu projektu C#, jehož cílem [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Kompilované XAML je výchozí typ pracovního postupu vytváření obsahu v sadě Visual Studio, a vytvořit pracovní postup projektů C# v sadě Visual Studio cílených [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] použití výrazů jazyka C#.  
  
####  <a name="LooseXaml"></a> Přijít Xaml  
 Výrazy jazyka C# jsou podporovány v přijít pracovních postupech XAML. Musí mít jako cíl pracovního postupu hostitelského programu, který načte a vyvolá přijít XAML pracovního postupu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], a <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musí být nastavena na `true` (výchozí hodnota je `false`). Chcete-li nastavit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> k `true`, vytvořit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na hodnotu `true`a předáváme jako parametr, který se <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Pokud `CompileExpressions` není nastavený na `true`, <xref:System.NotSupportedException> bude vyvolána s zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilace aby bylo možné spustit.  Zkontrolujte, že pracovní postup byl zkompilován. "  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Práce s pracovních postupů XAML, najdete v části [serializaci pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
###  <a name="WFServices"></a> Použití jazyka C# výrazů v XAMLX služeb pracovních postupů  
 Výrazy jazyka C# jsou podporovány v XAMLX služeb pracovních postupů. Pokud služby pracovního postupu je hostován v IIS nebo WAS pak nejsou potřeba žádné další kroky, ale pokud je samoobslužně hostovaná služba XAML pracovního postupu, musí být zkompilovány výrazy jazyka C#. Kompilace výrazy jazyka C# ve vlastním hostováním služby pracovního postupu XAMLX, nejdřív načtěte soubor XAMLX do `WorkflowService`a pak `Body` z `WorkflowService` k `CompileExpressions` metody popsané v předchozí [pomocí jazyka C# výrazy v pracovních postupech kód](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) části. V následujícím příkladu je načtena XAMLX služby pracovních postupů, se kompilují výrazy jazyka C# a pak služby pracovního postupu je otevřen a čeká na požadavky.  
  
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
  
 Pokud nejsou kompilovány výrazy jazyka C#, `Open` operace úspěšná, ale pracovní postup se nezdaří, při vyvolání. Následující `CompileExpressions` metoda je stejná jako metoda z předchozí [pomocí jazyka C# výrazy v pracovních postupech kód](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) části.  
  
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
