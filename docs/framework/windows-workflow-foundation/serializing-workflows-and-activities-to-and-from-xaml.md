---
title: "Serializace pracovních postupů a aktivit do a z XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 72956d1044ae6b99134665ef296b5d347673deab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="91fcf-102">Serializace pracovních postupů a aktivit do a z XAML</span><span class="sxs-lookup"><span data-stu-id="91fcf-102">Serializing Workflows and Activities to and from XAML</span></span>
<span data-ttu-id="91fcf-103">Kromě se zkompiluje do typy, které jsou součástí sestavení, definice pracovního postupu také serializovat lze do jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="91fcf-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="91fcf-104">Tyto serializovaných definice můžete znovu pro úpravy nebo kontroly, předaný systém sestavení pro kompilaci, nebo načíst a volána.</span><span class="sxs-lookup"><span data-stu-id="91fcf-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="91fcf-105">Toto téma poskytuje přehled o serializaci definice pracovního postupu a práce s XAML pracovního postupu definice.</span><span class="sxs-lookup"><span data-stu-id="91fcf-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>  
  
## <a name="working-with-xaml-workflow-definitions"></a><span data-ttu-id="91fcf-106">Práce s definicí pracovního postupu XAML</span><span class="sxs-lookup"><span data-stu-id="91fcf-106">Working with XAML Workflow Definitions</span></span>  
 <span data-ttu-id="91fcf-107">K vytvoření definice pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> třída se používá.</span><span class="sxs-lookup"><span data-stu-id="91fcf-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="91fcf-108">Vytvoření <xref:System.Activities.ActivityBuilder> je velmi podobný vytváření <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="91fcf-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="91fcf-109">Nejsou zadány žádné požadované argumenty a aktivity, které tvoří chování jsou nakonfigurovány.</span><span class="sxs-lookup"><span data-stu-id="91fcf-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="91fcf-110">V následujícím příkladu se `Add` je vytvořena aktivita, která má dva vstupní argumenty, společně se přidají a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="91fcf-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="91fcf-111">Protože tato aktivita vrací výsledek, Obecné <xref:System.Activities.ActivityBuilder%601> třída se používá.</span><span class="sxs-lookup"><span data-stu-id="91fcf-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 <span data-ttu-id="91fcf-112">Každý z <xref:System.Activities.DynamicActivityProperty> instance představuje jeden z vstupní argumenty do pracovního postupu a <xref:System.Activities.ActivityBuilder.Implementation%2A> obsahuje aktivity, které tvoří logika pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="91fcf-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="91fcf-113">Všimněte si, že hodnoty r ve výrazech v tomto příkladu jsou výrazy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="91fcf-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="91fcf-114">Lambda – výrazy nejsou serializovatelný do jazyka XAML Pokud <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se používá.</span><span class="sxs-lookup"><span data-stu-id="91fcf-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="91fcf-115">Pokud chcete otevřít nebo upravit v Návrháři pracovních postupů jsou určené serializovaných pracovních pak lze použít výrazy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="91fcf-115">If the serialized workflows are intended to be opened or edited in the workflow designer then Visual Basic expressions should be used.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="91fcf-116">[Vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kódu](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="91fcf-116"> [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
 <span data-ttu-id="91fcf-117">K serializaci reprezentována definice pracovního postupu <xref:System.Activities.ActivityBuilder> instance do jazyka XAML, použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter>a potom pomocí <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="91fcf-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="91fcf-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices>obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instance do a z XAML a pro spouštění pracovních postupů XAML a vrátit <xref:System.Activities.DynamicActivity> může být volána.</span><span class="sxs-lookup"><span data-stu-id="91fcf-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML, and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="91fcf-119">V následujícím příkladu <xref:System.Activities.ActivityBuilder> instance z předchozího příkladu je serializovat na řetězec a taky uloží do souboru.</span><span class="sxs-lookup"><span data-stu-id="91fcf-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string, and also saved to a file.</span></span>  
  
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
  
 <span data-ttu-id="91fcf-120">V následujícím příkladu představuje serializovaných pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="91fcf-120">The following example represents the serialized workflow.</span></span>  
  
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
  
 <span data-ttu-id="91fcf-121">Pro načtení serializovaných pracovního postupu, <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda se používá.</span><span class="sxs-lookup"><span data-stu-id="91fcf-121">To load a serialized workflow, the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method is used.</span></span> <span data-ttu-id="91fcf-122">To trvá definice serializovaných pracovního postupu a vrátí <xref:System.Activities.DynamicActivity> představující definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="91fcf-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="91fcf-123">Všimněte si, že dokud není deserializovat XAML <xref:System.Activities.Activity.CacheMetadata%2A> se volá na text <xref:System.Activities.DynamicActivity> během procesu ověření.</span><span class="sxs-lookup"><span data-stu-id="91fcf-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="91fcf-124">Pokud ověření není explicitně volána poté se provádí při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="91fcf-124">If validation is not explicitly called then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="91fcf-125">Pokud definice XAML pracovního postupu je neplatná, pak <xref:System.Argument> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="91fcf-125">If the XAML workflow definition is invalid, then an <xref:System.Argument> exception is thrown.</span></span> <span data-ttu-id="91fcf-126">Jakékoli výjimky vyvolány z <xref:System.Activities.Activity.CacheMetadata%2A> řídicí z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracována volající.</span><span class="sxs-lookup"><span data-stu-id="91fcf-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="91fcf-127">V následujícím příkladu je serializovaná pracovní postup z předchozího příkladu načíst a vyvolána pomocí <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="91fcf-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 <span data-ttu-id="91fcf-128">Po vyvolání tento pracovní postup se zobrazí následující výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="91fcf-128">When this workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="91fcf-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="91fcf-129">**25 + 15**</span></span>  
<span data-ttu-id="91fcf-130">**40**</span><span class="sxs-lookup"><span data-stu-id="91fcf-130">**40**</span></span>    
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="91fcf-131">vyvolání pracovních s vstupní a výstupní argumenty, najdete v části [pomocí WorkflowInvoker a WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="91fcf-131"> invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>  
  
 <span data-ttu-id="91fcf-132">Pokud serializovaných pracovní postup obsahuje C# výrazy, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na hodnotu `true` musí být předán jako parametr pro <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, jinak hodnota <xref:System.NotSupportedException> bude vyvolána s zprávu podobnou té následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilace aby bylo možné spustit.</span><span class="sxs-lookup"><span data-stu-id="91fcf-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="91fcf-133">Zkontrolujte, že pracovní postup byl zkompilován. "</span><span class="sxs-lookup"><span data-stu-id="91fcf-133">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="91fcf-134">[Výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="91fcf-134"> [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="91fcf-135">Definice serializovaných pracovního postupu můžete také načíst do <xref:System.Activities.ActivityBuilder> instance pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="91fcf-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="91fcf-136">Po načtení serializovaných pracovního postupu do <xref:System.Activities.ActivityBuilder> instance může být prověřovány a změnit.</span><span class="sxs-lookup"><span data-stu-id="91fcf-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance it can be inspected and modified.</span></span> <span data-ttu-id="91fcf-137">To je užitečné pro autory návrháře vlastní pracovní postup a poskytuje mechanismus pro ukládání a načíst definice pracovního postupu během procesu návrhu.</span><span class="sxs-lookup"><span data-stu-id="91fcf-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="91fcf-138">V následujícím příkladu je načtena definice pracovního postupu serializovaných z předchozího příkladu a jsou prověřovány jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="91fcf-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
