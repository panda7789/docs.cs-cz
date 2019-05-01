---
title: Výrazy C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: 2ffc380d9c65ec398084bfcbeadfe0fd2c3d6720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009809"
---
# <a name="c-expressions"></a>Výrazy C#
Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporované ve Windows Workflow Foundation (WF). Vytvořit nové projekty pracovního postupu C# v sadě Visual Studio 2012, které se zaměřují [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] použití výrazy jazyka C# a projekty pracovního postupu Visual Basic používat výrazy jazyka Visual Basic. Existující [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projekty pracovního postupu, které používají výrazy jazyka Visual Basic se dají migrovat do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bez ohledu na to, projekt jazyka a jsou podporovány. Toto téma obsahuje přehled výrazy jazyka C# v [!INCLUDE[wf1](../../../includes/wf1-md.md)].

## <a name="using-c-expressions-in-workflows"></a>Používání výrazy jazyka C# v pracovních postupech

- [Použití výrazy jazyka C# v Návrháři postupu provádění](csharp-expressions.md#WFDesigner)

    - [Zpětné kompatibility](csharp-expressions.md#BackwardCompat)

- [Používání výrazy jazyka C# v pracovních postupech kódu](csharp-expressions.md#CodeWorkflows)

- [Používání výrazy jazyka C# v pracovních postupech XAML](csharp-expressions.md#XamlWorkflows)

    - [Kompilované Xaml](csharp-expressions.md#CompiledXaml)

    - [Volný Xaml](csharp-expressions.md#LooseXaml)

- [Používat výrazy jazyka C# ve službách pracovních postupů XAMLX](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a> Použití výrazy jazyka C# v Návrháři postupu provádění
 Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka C# jsou podporované ve Windows Workflow Foundation (WF). Projekty pracovního postupu C# vytvořené v sadě Visual Studio 2012, které se zaměřují [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] používat výrazy jazyka C#, zatímco projekty pracovního postupu Visual Basic používat výrazy jazyka Visual Basic. K určení požadovaných výraz C#, zadejte do pole s popiskem **zadejte výraz C#**. Při výběru aktivity v návrháři, nebo na aktivitu v Návrháři postupu provádění, zobrazí se tento popisek v okně Vlastnosti. V následujícím příkladu dvě `WriteLine` aktivity jsou obsaženy v rámci `Sequence` uvnitř `NoPersistScope`.

 ![Automaticky vytvořit sekvenční aktivitu](./media/autosurround2.png "AutoSurround2")

> [!NOTE]
>  Výrazy jazyka C# jsou podporovány pouze v sadě Visual Studio a nejsou podporovány v Návrháři znovu hostovaných pracovních postupů. Další informace o nových funkcích WF45 podporované v Návrháři znovu hostované najdete v tématu [podpora nových funkcí Workflow Foundation 4.5 v Návrháři postupu provádění se změněným hostováním](wf-features-in-the-rehosted-workflow-designer.md).

#### <a name="BackwardCompat"></a> Zpětné kompatibility
 Výrazy jazyka Visual Basic v existujícím [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] projekty jazyka C# pracovního postupu, které se migrovaly na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jsou podporovány. Při výrazy jazyka Visual Basic jsou zobrazení v Návrháři postupu provádění, existující výrazu jazyka Visual Basic se nahrazuje s **hodnota byla nastavená v XAML**, pokud výraz jazyka Visual Basic je platná syntaxe jazyka C#. Výraz jazyka Visual Basic je platná syntaxe jazyka C#, se zobrazí výraz. K aktualizaci výrazy jazyka Visual Basic do jazyka C#, můžete upravit v Návrháři pracovních postupů a určení ekvivalentních výrazů C#. Není potřeba aktualizovat výrazy jazyka Visual Basic do jazyka C#, ale po výrazy jsou aktualizovány v Návrháři pracovních postupů jsou převedeny do jazyka C# a nemusí vrátit do jazyka Visual Basic.

### <a name="CodeWorkflows"></a> Používání výrazy jazyka C# v pracovních postupech kódu
 Výrazy jazyka C# jsou podporovány v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovní postupy založené na kódu, ale předtím, než pracovní postup může být vyvolána výrazy jazyka C# musí být kompilováno s použitím <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. Autoři pracovního postupu můžete použít `CSharpValue` představující r výrazu a `CSharpReference` k reprezentaci l hodnoty výrazu. V následujícím příkladu se vytvoří pracovní postup s `Assign` aktivity a `WriteLine` aktivity obsažené v `Sequence` aktivity. A `CSharpReference` je určená pro `To` argument `Assign`a představuje l hodnotou výrazu. A `CSharpValue` je určená pro `Value` argument `Assign`a `Text` argument `WriteLine`a představuje r-value u těchto dvou výrazů.

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

 Po pracovního postupu je vytvořena, výrazy jazyka C# jsou kompilovány pomocí volání `CompileExpressions` vyvolání Pomocná metoda a potom pracovního postupu. V následujícím příkladu je `CompileExpressions` metody.

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
>  Pokud C# výrazy nejsou zkompilovány, <xref:System.NotSupportedException> je vyvolána, když uživatel vyvolá pracovní postup a zobrazí se zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že pracovní postup byl zkompilován. "

 Pokud váš vlastní kód na základě pracovní postup používá `DynamicActivity`, pak některé změny `CompileExpressions` metody jsou povinné, jak je ukázáno v následujícím příkladu kódu.

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

- Parametr `CompileExpressions` je `DynamicActivity`.

- Název typu a obor názvů se načítají pomocí `DynamicActivity.Name` vlastnost.

- `TextExpressionCompilerSettings.ForImplementation` je nastavena na `true`.

- `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` je volána místo `CompiledExpressionInvoker.SetCompiledExpressionRoot`.

 Další informace o práci s výrazy v kódu, naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="XamlWorkflows"></a> Používání výrazy jazyka C# v pracovních postupech XAML
 Výrazy jazyka C# jsou podporovány v pracovních postupech XAML. Kompilované pracovních postupů XAML jsou kompilovány do typu, a dojde ke ztrátě pracovních postupů XAML načten modulem runtime a zkompilovány do strom aktivity při spuštění pracovního postupu.

- [Kompilované Xaml](csharp-expressions.md#CompiledXaml)

- [Volný Xaml](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a> Kompilované Xaml
 Výrazy jazyka C# jsou podporovány v kompilovaných pracovních postupech XAML, které jsou kompilovány do typu jako součást projektu jazyka C# pracovního postupu, který se zaměřuje [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Kompilované XAML je výchozí typ pracovního postupu pro vytváření ve Visual Studiu a projekty pracovního postupu C# vytvořené v sadě Visual Studio, které se zaměřují [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] používat výrazy jazyka C#.

#### <a name="LooseXaml"></a> Volný Xaml
 Výrazy jazyka C# jsou podporovány v pracovních postupech volný XAML. Program hostitele pracovního postupu, který načte a vyvolá volný XAML workflowu, musí jako cíl [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], a <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musí být nastaveno na `true` (výchozí hodnota je `false`). Nastavit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> k `true`, vytvořit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na hodnotu `true`a předáváme jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Pokud `CompileExpressions` není nastavená na `true`, <xref:System.NotSupportedException> bude vyvolána a zobrazí se zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že pracovní postup byl zkompilován. "

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

 Další informace o práci s pracovními postupy XAML najdete v tématu [serializace pracovních postupů a aktivit do a z XAML](serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="WFServices"></a> Používat výrazy jazyka C# ve službách pracovních postupů XAMLX
 Výrazy jazyka C# jsou podporovány v XAMLX služeb pracovních postupů. Když jsou služby pracovního postupu je hostované v IIS nebo WAS pak nejsou vyžadovány žádné další kroky, ale služba pracovního postupu XAML je samoobslužně hostovaná, musí být kompilována výrazy jazyka C#. Chcete-li zkompilovat výrazy jazyka C# v místním prostředí služby pracovního postupu XAMLX, nejdřív načtěte soubor XAMLX do `WorkflowService`a pak předejte `Body` z `WorkflowService` k `CompileExpressions` metody popsané v předchozí [pomocí jazyka C# výrazy v pracovních postupech kód](csharp-expressions.md#CodeWorkflows) oddílu. V následujícím příkladu XAMLX služby pracovního postupu je načtena, jsou zkompilovány výrazy jazyka C# a potom služba pracovního postupu je otevřený a čeká na požadavky.

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

 Pokud nejsou výrazy jazyka C# zkompilovány, `Open` operace úspěšná, ale pracovní postup se nezdaří, pokud je vyvolána. Následující `CompileExpressions` metodu je stejná jako metoda z předchozího [výrazy pomocí jazyka C# v pracovních postupech kód](csharp-expressions.md#CodeWorkflows) oddílu.

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
