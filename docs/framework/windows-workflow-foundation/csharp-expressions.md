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
# <a name="c-expressions"></a>Výrazy C#
Počínaje .NET Framework 4,5 jsou C# výrazy podporované v programovací model Windows Workflow Foundation (WF). Nové C# projekty pracovního postupu vytvořené v aplikaci Visual Studio 2012, které cílí C# na 4,5 .NET Framework výrazy use a Visual Basic pracovního postupu, používají Visual Basic výrazy. Stávající projekty pracovního postupu .NET Framework 4, které používají Visual Basic výrazy, lze migrovat do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] bez ohledu na jazyk projektu a jsou podporovány. Toto téma poskytuje přehled C# výrazů v [!INCLUDE[wf1](../../../includes/wf1-md.md)].

## <a name="using-c-expressions-in-workflows"></a>Použití C# výrazů v pracovních postupech

- [Použití C# výrazů v Návrhář postupu provádění](csharp-expressions.md#WFDesigner)

  - [Zpětná kompatibilita](csharp-expressions.md#BackwardCompat)

- [Použití C# výrazů v pracovních postupech kódu](csharp-expressions.md#CodeWorkflows)

- [Použití C# výrazů v pracovních postupech XAML](csharp-expressions.md#XamlWorkflows)

  - [Zkompilovaný kód XAML](csharp-expressions.md#CompiledXaml)

  - [Volný kód XAML](csharp-expressions.md#LooseXaml)

- [Použití C# výrazů ve službě xamlx Workflow Services](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a>Použití C# výrazů v Návrhář postupu provádění

Počínaje .NET Framework 4,5 jsou C# výrazy podporované v programovací model Windows Workflow Foundation (WF). C#projekty pracovního postupu vytvořené v aplikaci Visual Studio 2012, které cílí C# na .NET Framework 4,5 výrazy use, zatímco Visual Basic projekty pracovního postupu používají Visual Basic výrazy. Chcete-li zadat C# požadovaný výraz, zadejte ho do pole s popiskem **zadat C# výraz**. Tento popisek se zobrazí v okně vlastnosti, když je aktivita vybrána v Návrháři nebo v aktivitě v Návrháři pracovních postupů. V následujícím příkladu jsou dvě aktivity `WriteLine` obsaženy v rámci `Sequence` uvnitř `NoPersistScope`.

![Snímek obrazovky zobrazující automaticky vytvořenou aktivitu sekvence](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> C#výrazy jsou podporovány pouze v aplikaci Visual Studio a nejsou podporovány v Návrháři opětovného hostovaného pracovního postupu. Další informace o nových funkcích WF45 podporovaných v opětovném hostovaném návrháři najdete v článku [Podpora nových funkcí pracovního postupu 4,5 v článku Návrhář postupu provádění hostitele](wf-features-in-the-rehosted-workflow-designer.md).

#### <a name="BackwardCompat"></a>Zpětná kompatibilita

Podporovány jsou Visual Basic výrazy v existujících C# projektech pracovních postupů .NET Framework 4, které byly migrovány do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Pokud jsou výrazy Visual Basic zobrazeny v Návrháři sledu prací, text stávajícího výrazu Visual Basic je nahrazen **hodnotou nastavenou v jazyce XAML**, pokud výraz Visual Basic není platná C# syntaxe. Pokud je výraz Visual Basic platnou C# syntaxí, zobrazí se výraz. Chcete-li aktualizovat Visual Basic výrazy C#na, můžete je upravit v Návrháři pracovních postupů a zadat ekvivalentní C# výraz. Není nutné aktualizovat Visual Basic výrazy na C#, ale po aktualizaci výrazů v Návrháři pracovního postupu jsou převedeny na C# a nemusí být vráceny zpět na Visual Basic.

### <a name="CodeWorkflows"></a>Použití C# výrazů v pracovních postupech kódu

C#výrazy jsou podporované v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovních postupech na základě kódu, ale před vyvoláním pracovního C# postupu musí být výrazy kompilovány pomocí <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. Autoři pracovního postupu můžou použít `CSharpValue` k vyjádření hodnoty r výrazu a `CSharpReference` k reprezentaci l-Value výrazu. V následujícím příkladu je vytvořen pracovní postup s aktivitou `Assign` a aktivitou `WriteLine` obsaženou v `Sequence` aktivitě. Pro argument `To` `Assign`je určena `CSharpReference` a představuje l-hodnotu výrazu. `CSharpValue` je určena pro `Value` argument `Assign`a pro `Text` argument `WriteLine`a představuje hodnotu r pro tyto dva výrazy.

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

Po vytvoření pracovního postupu jsou C# výrazy kompilovány voláním pomocné metody `CompileExpressions` a následně vyvoláním pracovního postupu. Následující příklad je metoda `CompileExpressions`.

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
> Pokud nejsou C# výrazy kompilovány, je vyvolána <xref:System.NotSupportedException>, když je pracovní postup vyvolán pomocí zprávy podobné následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že byl pracovní postup zkompilován. '

Pokud vlastní pracovní postup založený na kódu používá `DynamicActivity`, pak některé změny metody `CompileExpressions` jsou požadovány, jak je znázorněno v následujícím příkladu kódu.

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

Existuje několik rozdílů v `CompileExpressions` přetížení, které kompiluje C# výrazy v dynamické aktivitě.

- Parametr pro `CompileExpressions` je `DynamicActivity`.

- Název typu a obor názvů se načítají pomocí vlastnosti `DynamicActivity.Name`.

- `TextExpressionCompilerSettings.ForImplementation` je nastavená na `true`.

- místo `CompiledExpressionInvoker.SetCompiledExpressionRoot`je volána `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation`.

Další informace o práci s výrazy v kódu naleznete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="XamlWorkflows"></a>Použití C# výrazů v pracovních postupech XAML

C#výrazy jsou podporovány v pracovních postupech XAML. Zkompilované pracovní postupy XAML jsou kompilovány do typu a volné pracovní postupy XAML jsou načteny modulem runtime a kompilovány do stromu aktivity při spuštění pracovního postupu.

- [Zkompilovaný kód XAML](csharp-expressions.md#CompiledXaml)

- [Volný kód XAML](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a>Zkompilovaný kód XAML

C#výrazy jsou podporovány v kompilovaných pracovních postupech XAML, které jsou kompilovány do typu jako C# součást projektu pracovního postupu, který cílí na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Zkompilovaný kód XAML je výchozí typ vytváření pracovních postupů v aplikaci Visual Studio a C# projekty pracovního postupu vytvořené v aplikaci Visual Studio, které C# cílí na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] výrazy použití.

#### <a name="LooseXaml"></a>Volný kód XAML

C#výrazy jsou podporovány v volných pracovních postupech XAML. Hostitelský program pracovního postupu, který načte a vyvolá volný pracovní postup XAML, musí cílit na [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]a <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> musí být nastaven na `true` (výchozí hodnota je `false`). Chcete-li nastavit <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true`, vytvořte instanci <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> s vlastností <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> nastavenou na hodnotu `true`a předejte ji jako parametr pro <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Pokud `CompileExpressions` není nastavená na `true`, bude vyvolána <xref:System.NotSupportedException> zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že byl pracovní postup zkompilován. '

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Další informace o práci s pracovními postupy XAML naleznete v tématu [serializace pracovních postupů a aktivit do a z jazyka XAML](serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="WFServices"></a>Použití C# výrazů ve službě xamlx Workflow Services

C#ve službách pracovního postupu XAMLX jsou podporované výrazy. Když je služba pracovního postupu hostovaná ve službě IIS nebo se nevyžadují žádné další kroky, ale pokud je služba pracovního postupu XAML v místním prostředí, pak C# se výrazy musí zkompilovat. Chcete-li C# kompilovat výrazy ve službě xamlx pracovního postupu v místním prostředí, načtěte soubor XAMLX do `WorkflowService`a pak předejte `Body` `WorkflowService` do metody `CompileExpressions` popsané v části předchozí [výrazy using C# v tématu pracovní postupy kódu](csharp-expressions.md#CodeWorkflows) . V následujícím příkladu je načtena služba XAMLX Workflow, C# výrazy jsou kompilovány a poté je spuštěna služba pracovního postupu, která čeká na požadavky.

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

Pokud nejsou C# výrazy kompilovány, `Open` operace proběhne úspěšně, ale pracovní postup selže při jeho vyvolání. Následující metoda `CompileExpressions` je shodná s metodou z předchozích [výrazů using C# v části pracovní postupy kódu](csharp-expressions.md#CodeWorkflows) .

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
