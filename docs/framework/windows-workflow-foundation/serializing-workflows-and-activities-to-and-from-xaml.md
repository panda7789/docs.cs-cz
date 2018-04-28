---
title: Serializace pracovních postupů a aktivit do a z XAML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a215be76002b9e8fca8ac4a9073885b3b30a97b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a>Serializace pracovních postupů a aktivit do a z XAML
Kromě se zkompiluje do typy, které jsou součástí sestavení, definice pracovního postupu také serializovat lze do jazyka XAML. Tyto serializovaných definice můžete znovu pro úpravy nebo kontroly, předaný systém sestavení pro kompilaci, nebo načíst a volána. Toto téma poskytuje přehled o serializaci definice pracovního postupu a práce s XAML pracovního postupu definice.  
  
## <a name="working-with-xaml-workflow-definitions"></a>Práce s definicí pracovního postupu XAML  
 K vytvoření definice pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> třída se používá. Vytvoření <xref:System.Activities.ActivityBuilder> je velmi podobný vytváření <xref:System.Activities.DynamicActivity>. Nejsou zadány žádné požadované argumenty a aktivity, které tvoří chování jsou nakonfigurovány. V následujícím příkladu se `Add` je vytvořena aktivita, která má dva vstupní argumenty, společně se přidají a vrátí výsledek. Protože tato aktivita vrací výsledek, Obecné <xref:System.Activities.ActivityBuilder%601> třída se používá.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 Každý z <xref:System.Activities.DynamicActivityProperty> instance představuje jeden z vstupní argumenty do pracovního postupu a <xref:System.Activities.ActivityBuilder.Implementation%2A> obsahuje aktivity, které tvoří logika pracovního postupu. Všimněte si, že hodnoty r ve výrazech v tomto příkladu jsou výrazy jazyka Visual Basic. Lambda – výrazy nejsou serializovatelný do jazyka XAML Pokud <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se používá. Pokud chcete otevřít nebo upravit v Návrháři pracovních postupů jsou určené serializovaných pracovních pak lze použít výrazy jazyka Visual Basic. Další informace najdete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kód](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
 K serializaci reprezentována definice pracovního postupu <xref:System.Activities.ActivityBuilder> instance do jazyka XAML, použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter>a potom pomocí <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter>. <xref:System.Activities.XamlIntegration.ActivityXamlServices> obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instance do a z XAML a pro spouštění pracovních postupů XAML a vrátit <xref:System.Activities.DynamicActivity> může být volána. V následujícím příkladu <xref:System.Activities.ActivityBuilder> instance z předchozího příkladu je serializovat na řetězec a taky uloží do souboru.  
  
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
  
 V následujícím příkladu představuje serializovaných pracovního postupu.  
  
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
  
 Pro načtení serializovaných pracovního postupu, <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda se používá. To trvá definice serializovaných pracovního postupu a vrátí <xref:System.Activities.DynamicActivity> představující definice pracovního postupu. Všimněte si, že dokud není deserializovat XAML <xref:System.Activities.Activity.CacheMetadata%2A> se volá na text <xref:System.Activities.DynamicActivity> během procesu ověření. Pokud ověření není explicitně volána poté se provádí při vyvolání pracovního postupu. Pokud definice XAML pracovního postupu je neplatná, pak <xref:System.ArgumentException> je vyvolána výjimka. Jakékoli výjimky vyvolány z <xref:System.Activities.Activity.CacheMetadata%2A> řídicí z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracována volající. V následujícím příkladu je serializovaná pracovní postup z předchozího příkladu načíst a vyvolána pomocí <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 Po vyvolání tento pracovní postup se zobrazí následující výstup do konzoly.  
  
 **25 + 15**  
**40**    
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)] vyvolání pracovních s vstupní a výstupní argumenty, najdete v části [pomocí WorkflowInvoker a WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A>.  
  
 Pokud serializovaných pracovní postup obsahuje C# výrazy, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na hodnotu `true` musí být předán jako parametr pro <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, jinak hodnota <xref:System.NotSupportedException> bude vyvolána s zprávu podobnou té následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilace aby bylo možné spustit.  Zkontrolujte, že pracovní postup byl zkompilován. "  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 Další informace najdete v tématu [výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
 Definice serializovaných pracovního postupu můžete také načíst do <xref:System.Activities.ActivityBuilder> instance pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metoda. Po načtení serializovaných pracovního postupu do <xref:System.Activities.ActivityBuilder> instance může být prověřovány a změnit. To je užitečné pro autory návrháře vlastní pracovní postup a poskytuje mechanismus pro ukládání a načíst definice pracovního postupu během procesu návrhu. V následujícím příkladu je načtena definice pracovního postupu serializovaných z předchozího příkladu a jsou prověřovány jeho vlastnosti.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
