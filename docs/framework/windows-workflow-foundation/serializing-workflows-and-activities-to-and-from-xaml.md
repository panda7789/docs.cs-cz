---
title: Serializace pracovních postupů a aktivit do a z XAML
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 70ee2e8e0c457e9db2853935ef95b86c7f903fc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004637"
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="daee3-102">Serializace pracovních postupů a aktivit do a z XAML</span><span class="sxs-lookup"><span data-stu-id="daee3-102">Serializing Workflows and Activities to and from XAML</span></span>
<span data-ttu-id="daee3-103">Kromě kompilaci do typů, které jsou obsaženy v sestavení, definice pracovního postupu lze také serializovat v XAML.</span><span class="sxs-lookup"><span data-stu-id="daee3-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="daee3-104">Tato serializovaná definice je možné znovu zavést pro úpravy nebo kontroly, předán systém sestavení pro kompilaci, nebo načíst a vyvolána.</span><span class="sxs-lookup"><span data-stu-id="daee3-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="daee3-105">Toto téma obsahuje přehled o serializaci definice pracovního postupu a práci s definice pracovního postupu XAML.</span><span class="sxs-lookup"><span data-stu-id="daee3-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>  
  
## <a name="working-with-xaml-workflow-definitions"></a><span data-ttu-id="daee3-106">Práce s definice pracovního postupu XAML</span><span class="sxs-lookup"><span data-stu-id="daee3-106">Working with XAML Workflow Definitions</span></span>  
 <span data-ttu-id="daee3-107">Jak vytvořit definici pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> třída se používá.</span><span class="sxs-lookup"><span data-stu-id="daee3-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="daee3-108">Vytvoření <xref:System.Activities.ActivityBuilder> je velmi podobné jako vytvoření <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="daee3-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="daee3-109">Nejsou zadány žádné požadované argumenty a aktivity, které tvoří chování jsou nakonfigurovány.</span><span class="sxs-lookup"><span data-stu-id="daee3-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="daee3-110">V následujícím příkladu `Add` , který má dva vstupní argumenty, se přidají společně a vrátí výsledek vytvoření aktivity.</span><span class="sxs-lookup"><span data-stu-id="daee3-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="daee3-111">Protože tato aktivita vrátí výsledek, Obecné <xref:System.Activities.ActivityBuilder%601> třída se používá.</span><span class="sxs-lookup"><span data-stu-id="daee3-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 <span data-ttu-id="daee3-112">Každá z <xref:System.Activities.DynamicActivityProperty> instance představuje jeden vstupní argumenty do pracovního postupu a <xref:System.Activities.ActivityBuilder.Implementation%2A> obsahuje aktivity, které tvoří logiku pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="daee3-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="daee3-113">Všimněte si, hodnoty r ve výrazech v tomto příkladu jsou výrazy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="daee3-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="daee3-114">Výrazy lambda nejsou serializovatelný XAML není-li <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se používá.</span><span class="sxs-lookup"><span data-stu-id="daee3-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="daee3-115">Pokud se má otevřít nebo upravit v Návrháři postupu provádění serializovaná pracovních postupů by měl používat výrazy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="daee3-115">If the serialized workflows are intended to be opened or edited in the workflow designer then Visual Basic expressions should be used.</span></span> <span data-ttu-id="daee3-116">Další informace najdete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="daee3-116">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
 <span data-ttu-id="daee3-117">K serializaci definice pracovního postupu, který je reprezentován <xref:System.Activities.ActivityBuilder> instance pro XAML, použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter>a pak použijte <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="daee3-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="daee3-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instance do a z XAML a k načítání pracovních postupů XAML a vrátí <xref:System.Activities.DynamicActivity> , který může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="daee3-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML, and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="daee3-119">V následujícím příkladu <xref:System.Activities.ActivityBuilder> instanci z předchozího příkladu serializovat do řetězce a také uloží do souboru.</span><span class="sxs-lookup"><span data-stu-id="daee3-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string, and also saved to a file.</span></span>  
  
```csharp  
// Serialize the workflow to XAML and store it in a string.  
StringBuilder sb = new StringBuilder();  
StringWriter tw = new StringWriter(sb);  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));  
XamlServices.Save(xw , ab);  
string serializedAB = sb.ToString();  
  
// Display the XAML to the console.  
Console.WriteLine(serializedAB);  
  
// Serialize the workflow to XAML and save it to a file.  
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");  
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw2, ab);  
sw.Close();  
```  
  
 <span data-ttu-id="daee3-120">Následující příklad představuje serializovaná pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="daee3-120">The following example represents the serialized workflow.</span></span>  
  
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
  
 <span data-ttu-id="daee3-121">Načíst serializovaná pracovního postupu, <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda se používá.</span><span class="sxs-lookup"><span data-stu-id="daee3-121">To load a serialized workflow, the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method is used.</span></span> <span data-ttu-id="daee3-122">Tato definice pracovního postupu serializovaná převezme a vrátí <xref:System.Activities.DynamicActivity> , která představuje definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="daee3-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="daee3-123">Všimněte si, že XAML není deserializovat do <xref:System.Activities.Activity.CacheMetadata%2A> je volána v těle <xref:System.Activities.DynamicActivity> během procesu ověřování.</span><span class="sxs-lookup"><span data-stu-id="daee3-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="daee3-124">Pokud ověření není explicitně volána. pak se provede při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="daee3-124">If validation is not explicitly called then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="daee3-125">Pokud definice pracovního postupu XAML je neplatný, pak <xref:System.ArgumentException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="daee3-125">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="daee3-126">Výjimky vyvolané z <xref:System.Activities.Activity.CacheMetadata%2A> úniku z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a volající musí být zpracován.</span><span class="sxs-lookup"><span data-stu-id="daee3-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="daee3-127">V následujícím příkladu je serializovaná pracovní postup z předchozího příkladu načten a vyvolány pomocí <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="daee3-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 <span data-ttu-id="daee3-128">Když uživatel vyvolá tento pracovní postup, se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="daee3-128">When this workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="daee3-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="daee3-129">**25 + 15**</span></span>  
<span data-ttu-id="daee3-130">**40**</span><span class="sxs-lookup"><span data-stu-id="daee3-130">**40**</span></span>    
> [!NOTE]
>  <span data-ttu-id="daee3-131">Další informace o volání pracovní postupy s vstupní a výstupní argumenty najdete v tématu [použití WorkflowInvoker a WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="daee3-131">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>  
  
 <span data-ttu-id="daee3-132">Pokud obsahuje serializovaná pracovního postupu C# výrazy, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na `true` musí být předán jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, jinak <xref:System.NotSupportedException> a zobrazí se zpráva podobná, bude vyvolána pro následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="daee3-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="daee3-133">Ujistěte se prosím, že pracovní postup byl zkompilován. "</span><span class="sxs-lookup"><span data-stu-id="daee3-133">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 <span data-ttu-id="daee3-134">Další informace najdete v tématu [ C# výrazy](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="daee3-134">For more information, see [C# Expressions](csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="daee3-135">Je také možné načíst definice serializovaná pracovního postupu do <xref:System.Activities.ActivityBuilder> instance pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="daee3-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="daee3-136">Po načtení serializovaná pracovní postup do <xref:System.Activities.ActivityBuilder> instance, můžete ho zkontrolovat a upravit.</span><span class="sxs-lookup"><span data-stu-id="daee3-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance it can be inspected and modified.</span></span> <span data-ttu-id="daee3-137">To je užitečné pro autory návrháře vlastní pracovní postupy a poskytuje mechanismus pro uložení a načtení definice pracovního postupu během procesu návrhu.</span><span class="sxs-lookup"><span data-stu-id="daee3-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="daee3-138">V následujícím příkladu je načtena definice pracovního postupu serializovaná z předchozího příkladu a její vlastnosti jsou kontrolovány.</span><span class="sxs-lookup"><span data-stu-id="daee3-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
