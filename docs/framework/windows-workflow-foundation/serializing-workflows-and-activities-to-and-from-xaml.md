---
title: Serializace pracovních postupů a aktivit do a z XAML
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: c18afa7232adabc4f1c4e17fde993064b9189e39
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671897"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="f8d7d-102">Serializace pracovních postupů a aktivit do a z jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="f8d7d-102">Serialize Workflows and Activities to and from XAML</span></span>

<span data-ttu-id="f8d7d-103">Kromě kompilace do typů, které jsou obsaženy v sestaveních, mohou být definice pracovních postupů také serializovány do jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="f8d7d-104">Tyto serializované definice mohou být znovu načteny pro úpravy nebo kontrolu, předány do systému sestavení pro kompilaci nebo načteny a vyvolány.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="f8d7d-105">Toto téma obsahuje přehled serializace definicí pracovních postupů a práci s definicemi pracovního postupu XAML.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>

## <a name="work-with-xaml-workflow-definitions"></a><span data-ttu-id="f8d7d-106">Práce s definicemi pracovního postupu XAML</span><span class="sxs-lookup"><span data-stu-id="f8d7d-106">Work with XAML Workflow definitions</span></span>

<span data-ttu-id="f8d7d-107">Chcete-li vytvořit definici pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> je použita třída.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="f8d7d-108">Vytvoření je velmi podobné jako <xref:System.Activities.DynamicActivity>vytvoření. <xref:System.Activities.ActivityBuilder></span><span class="sxs-lookup"><span data-stu-id="f8d7d-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="f8d7d-109">Jsou zadány všechny požadované argumenty a jsou konfigurovány aktivity, které tvoří chování.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="f8d7d-110">V následujícím příkladu `Add` se vytvoří aktivita, která přijímá dva vstupní argumenty, přidá je společně a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="f8d7d-111">Vzhledem k tomu, že tato aktivita vrací výsledek <xref:System.Activities.ActivityBuilder%601> , je použita obecná třída.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

<span data-ttu-id="f8d7d-112">Každá z <xref:System.Activities.DynamicActivityProperty> těchto instancí představuje jeden ze vstupních argumentů pracovního postupu <xref:System.Activities.ActivityBuilder.Implementation%2A> a obsahuje aktivity, které tvoří logiku pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="f8d7d-113">Všimněte si, že výrazy r-value v tomto příkladu jsou Visual Basic výrazy.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="f8d7d-114">Výrazy lambda nelze serializovat na XAML, pokud <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="f8d7d-115">Pokud mají být serializované pracovní postupy v Návrháři pracovních postupů otevřeny nebo upravovány, měly by být použity Visual Basic výrazy.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-115">If the serialized workflows are intended to be opened or edited in the workflow designer, then Visual Basic expressions should be used.</span></span> <span data-ttu-id="f8d7d-116">Další informace naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="f8d7d-116">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

<span data-ttu-id="f8d7d-117">Pro serializaci definice pracovního postupu reprezentované <xref:System.Activities.ActivityBuilder> instancí na kód XAML použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter>a pak použijte <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="f8d7d-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices>obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instancí na a z kódu XAML a načtení pracovních postupů XAML a <xref:System.Activities.DynamicActivity> vrácení, které lze vyvolat.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="f8d7d-119">V následujícím příkladu <xref:System.Activities.ActivityBuilder> je instance z předchozího příkladu serializována do řetězce a uložena do souboru.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string and saved to a file.</span></span>

```csharp
// Serialize the workflow to XAML and store it in a string.
StringBuilder sb = new StringBuilder();
StringWriter tw = new StringWriter(sb);
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
string serializedAB = sb.ToString();

// Display the XAML to the console.
Console.WriteLine(serializedAB);

// Serialize the workflow to XAML and save it to a file.
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw2, ab);
sw.Close();
```

<span data-ttu-id="f8d7d-120">Následující příklad představuje serializovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-120">The following example represents the serialized workflow.</span></span>

```xaml
<Activity
  x:TypeArguments="x:Int32"
  x:Class="Add"
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
  <x:Members>
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />
  </x:Members>
  <Sequence>
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">
      <Assign.To>
        <OutArgument x:TypeArguments="x:Int32">
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />
          </OutArgument>
      </Assign.To>
    </Assign>
  </Sequence>
</Activity>
```

<span data-ttu-id="f8d7d-121">Chcete-li načíst serializovaný pracovní postup <xref:System.Activities.XamlIntegration.ActivityXamlServices> , použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-121">To load a serialized workflow, use the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="f8d7d-122">Tato definice provede serializovanou definici pracovního postupu a <xref:System.Activities.DynamicActivity> vrátí hodnotu, která představuje definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="f8d7d-123">Všimněte si, že kód XAML není rekonstruován, dokud <xref:System.Activities.Activity.CacheMetadata%2A> není volán v těle <xref:System.Activities.DynamicActivity> během procesu ověřování.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="f8d7d-124">Pokud ověření není explicitně voláno, je provedeno při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-124">If validation is not explicitly called, then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="f8d7d-125">Pokud definice pracovního postupu XAML není platná, <xref:System.ArgumentException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-125">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="f8d7d-126">Jakékoli výjimky vyvolané <xref:System.Activities.Activity.CacheMetadata%2A> z Escape z <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> volání a musí být zpracovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="f8d7d-127">V následujícím příkladu je serializovaný pracovní postup z předchozího příkladu načten a vyvolán pomocí <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

<span data-ttu-id="f8d7d-128">Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-128">When this workflow is invoked, the following output is displayed to the console.</span></span>

<span data-ttu-id="f8d7d-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="f8d7d-129">**25 + 15**</span></span>\
<span data-ttu-id="f8d7d-130">**40**</span><span class="sxs-lookup"><span data-stu-id="f8d7d-130">**40**</span></span>

> [!NOTE]
> <span data-ttu-id="f8d7d-131">Další informace o vyvolání pracovních postupů pomocí vstupních a výstupních argumentů naleznete v tématu [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-131">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>

<span data-ttu-id="f8d7d-132">Pokud serializovaný pracovní postup C# obsahuje výrazy, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance s <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastností nastavenou na `true` hodnotu <xref:System.NotSupportedException> musí být předána jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>do, jinak bude vyvolána se zprávou podobnou na následující: **Typ aktivity výrazu ' CSharpValue ' 1 ' vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že byl pracovní postup zkompilován.**</span><span class="sxs-lookup"><span data-stu-id="f8d7d-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: **Expression Activity type 'CSharpValue\`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.**</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="f8d7d-133">Další informace najdete v tématu [ C# výrazy](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f8d7d-133">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

<span data-ttu-id="f8d7d-134">Serializovanou definici pracovního postupu lze také načíst do <xref:System.Activities.ActivityBuilder> instance <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-134">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="f8d7d-135">Po načtení serializovaného pracovního postupu do <xref:System.Activities.ActivityBuilder> instance je možné ho zkontrolovat a upravit.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-135">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance, it can be inspected and modified.</span></span> <span data-ttu-id="f8d7d-136">To je užitečné pro vlastní autory návrháře pracovních postupů a poskytuje mechanismus pro ukládání a opětovné načítání definic pracovních postupů během procesu návrhu.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-136">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="f8d7d-137">V následujícím příkladu je načtena serializovaná definice pracovního postupu z předchozího příkladu a jsou zkontrolovány jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f8d7d-137">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
