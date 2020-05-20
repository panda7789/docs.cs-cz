---
title: Serializace pracovních postupů a aktivit do a z XAML
description: Tento článek je přehled serializace definicí pracovních postupů a práce s definicemi pracovního postupu XAML v modelu Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 168dbc9a36cfa80c15fddc7481e986d1ce383adb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421342"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="2e20b-103">Serializace pracovních postupů a aktivit do a z jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="2e20b-103">Serialize Workflows and Activities to and from XAML</span></span>

<span data-ttu-id="2e20b-104">Kromě kompilace do typů, které jsou obsaženy v sestaveních, mohou být definice pracovních postupů také serializovány do jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="2e20b-104">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="2e20b-105">Tyto serializované definice mohou být znovu načteny pro úpravy nebo kontrolu, předány do systému sestavení pro kompilaci nebo načteny a vyvolány.</span><span class="sxs-lookup"><span data-stu-id="2e20b-105">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="2e20b-106">Toto téma obsahuje přehled serializace definicí pracovních postupů a práci s definicemi pracovního postupu XAML.</span><span class="sxs-lookup"><span data-stu-id="2e20b-106">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>

## <a name="work-with-xaml-workflow-definitions"></a><span data-ttu-id="2e20b-107">Práce s definicemi pracovního postupu XAML</span><span class="sxs-lookup"><span data-stu-id="2e20b-107">Work with XAML Workflow definitions</span></span>

<span data-ttu-id="2e20b-108">Chcete-li vytvořit definici pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> je použita třída.</span><span class="sxs-lookup"><span data-stu-id="2e20b-108">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="2e20b-109">Vytvoření <xref:System.Activities.ActivityBuilder> je velmi podobné jako vytvoření <xref:System.Activities.DynamicActivity> .</span><span class="sxs-lookup"><span data-stu-id="2e20b-109">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="2e20b-110">Jsou zadány všechny požadované argumenty a jsou konfigurovány aktivity, které tvoří chování.</span><span class="sxs-lookup"><span data-stu-id="2e20b-110">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="2e20b-111">V následujícím příkladu `Add` se vytvoří aktivita, která přijímá dva vstupní argumenty, přidá je společně a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="2e20b-111">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="2e20b-112">Vzhledem k tomu, že tato aktivita vrací výsledek, <xref:System.Activities.ActivityBuilder%601> je použita obecná třída.</span><span class="sxs-lookup"><span data-stu-id="2e20b-112">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

<span data-ttu-id="2e20b-113">Každá z těchto <xref:System.Activities.DynamicActivityProperty> instancí představuje jeden ze vstupních argumentů pracovního postupu a <xref:System.Activities.ActivityBuilder.Implementation%2A> obsahuje aktivity, které tvoří logiku pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2e20b-113">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="2e20b-114">Všimněte si, že výrazy r-value v tomto příkladu jsou Visual Basic výrazy.</span><span class="sxs-lookup"><span data-stu-id="2e20b-114">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="2e20b-115">Výrazy lambda nelze serializovat na XAML, pokud <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="2e20b-115">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="2e20b-116">Pokud mají být serializované pracovní postupy v Návrháři pracovních postupů otevřeny nebo upravovány, měly by být použity Visual Basic výrazy.</span><span class="sxs-lookup"><span data-stu-id="2e20b-116">If the serialized workflows are intended to be opened or edited in the workflow designer, then Visual Basic expressions should be used.</span></span> <span data-ttu-id="2e20b-117">Další informace naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="2e20b-117">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

<span data-ttu-id="2e20b-118">Pro serializaci definice pracovního postupu reprezentované <xref:System.Activities.ActivityBuilder> instancí na kód XAML použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter> a pak použijte <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter> .</span><span class="sxs-lookup"><span data-stu-id="2e20b-118">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="2e20b-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices>obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instancí na a z kódu XAML a načtení pracovních postupů XAML a vrácení <xref:System.Activities.DynamicActivity> , které lze vyvolat.</span><span class="sxs-lookup"><span data-stu-id="2e20b-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="2e20b-120">V následujícím příkladu <xref:System.Activities.ActivityBuilder> je instance z předchozího příkladu serializována do řetězce a uložena do souboru.</span><span class="sxs-lookup"><span data-stu-id="2e20b-120">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string and saved to a file.</span></span>

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

<span data-ttu-id="2e20b-121">Následující příklad představuje serializovaný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="2e20b-121">The following example represents the serialized workflow.</span></span>

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

<span data-ttu-id="2e20b-122">Chcete-li načíst serializovaný pracovní postup, použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="2e20b-122">To load a serialized workflow, use the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="2e20b-123">Tato definice provede serializovanou definici pracovního postupu a vrátí hodnotu <xref:System.Activities.DynamicActivity> , která představuje definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2e20b-123">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="2e20b-124">Všimněte si, že kód XAML není rekonstruován, dokud <xref:System.Activities.Activity.CacheMetadata%2A> není volán v těle <xref:System.Activities.DynamicActivity> během procesu ověřování.</span><span class="sxs-lookup"><span data-stu-id="2e20b-124">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="2e20b-125">Pokud ověření není explicitně voláno, je provedeno při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2e20b-125">If validation is not explicitly called, then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="2e20b-126">Pokud definice pracovního postupu XAML není platná, <xref:System.ArgumentException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2e20b-126">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="2e20b-127">Jakékoli výjimky vyvolané z <xref:System.Activities.Activity.CacheMetadata%2A> Escape z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="2e20b-127">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="2e20b-128">V následujícím příkladu je serializovaný pracovní postup z předchozího příkladu načten a vyvolán pomocí <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="2e20b-128">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

<span data-ttu-id="2e20b-129">Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.</span><span class="sxs-lookup"><span data-stu-id="2e20b-129">When this workflow is invoked, the following output is displayed to the console.</span></span>

<span data-ttu-id="2e20b-130">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="2e20b-130">**25 + 15**</span></span>\
<span data-ttu-id="2e20b-131">**40**</span><span class="sxs-lookup"><span data-stu-id="2e20b-131">**40**</span></span>

> [!NOTE]
> <span data-ttu-id="2e20b-132">Další informace o vyvolání pracovních postupů pomocí vstupních a výstupních argumentů naleznete v tématu [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="2e20b-132">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>

<span data-ttu-id="2e20b-133">Pokud serializovaný pracovní postup obsahuje výrazy jazyka C#, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance s <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastností nastavenou na hodnotu `true` musí být předána jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> , jinak <xref:System.NotSupportedException> bude vyvolána zpráva podobná následující: **typ aktivity výrazu ' CSharpValue ' 1 ' vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že byl pracovní postup zkompilován.**</span><span class="sxs-lookup"><span data-stu-id="2e20b-133">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: **Expression Activity type 'CSharpValue\`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.**</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="2e20b-134">Další informace naleznete v tématu [výrazy jazyka C#](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2e20b-134">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

<span data-ttu-id="2e20b-135">Serializovanou definici pracovního postupu lze také načíst do <xref:System.Activities.ActivityBuilder> instance pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2e20b-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="2e20b-136">Po načtení serializovaného pracovního postupu do <xref:System.Activities.ActivityBuilder> instance je možné ho zkontrolovat a upravit.</span><span class="sxs-lookup"><span data-stu-id="2e20b-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance, it can be inspected and modified.</span></span> <span data-ttu-id="2e20b-137">To je užitečné pro vlastní autory návrháře pracovních postupů a poskytuje mechanismus pro ukládání a opětovné načítání definic pracovních postupů během procesu návrhu.</span><span class="sxs-lookup"><span data-stu-id="2e20b-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="2e20b-138">V následujícím příkladu je načtena serializovaná definice pracovního postupu z předchozího příkladu a jsou zkontrolovány jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2e20b-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
