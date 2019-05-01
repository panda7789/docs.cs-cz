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
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a>Serializace pracovních postupů a aktivit do a z XAML
Kromě kompilaci do typů, které jsou obsaženy v sestavení, definice pracovního postupu lze také serializovat v XAML. Tato serializovaná definice je možné znovu zavést pro úpravy nebo kontroly, předán systém sestavení pro kompilaci, nebo načíst a vyvolána. Toto téma obsahuje přehled o serializaci definice pracovního postupu a práci s definice pracovního postupu XAML.  
  
## <a name="working-with-xaml-workflow-definitions"></a>Práce s definice pracovního postupu XAML  
 Jak vytvořit definici pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> třída se používá. Vytvoření <xref:System.Activities.ActivityBuilder> je velmi podobné jako vytvoření <xref:System.Activities.DynamicActivity>. Nejsou zadány žádné požadované argumenty a aktivity, které tvoří chování jsou nakonfigurovány. V následujícím příkladu `Add` , který má dva vstupní argumenty, se přidají společně a vrátí výsledek vytvoření aktivity. Protože tato aktivita vrátí výsledek, Obecné <xref:System.Activities.ActivityBuilder%601> třída se používá.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 Každá z <xref:System.Activities.DynamicActivityProperty> instance představuje jeden vstupní argumenty do pracovního postupu a <xref:System.Activities.ActivityBuilder.Implementation%2A> obsahuje aktivity, které tvoří logiku pracovního postupu. Všimněte si, hodnoty r ve výrazech v tomto příkladu jsou výrazy jazyka Visual Basic. Výrazy lambda nejsou serializovatelný XAML není-li <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se používá. Pokud se má otevřít nebo upravit v Návrháři postupu provádění serializovaná pracovních postupů by měl používat výrazy jazyka Visual Basic. Další informace najdete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
 K serializaci definice pracovního postupu, který je reprezentován <xref:System.Activities.ActivityBuilder> instance pro XAML, použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter>a pak použijte <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter>. <xref:System.Activities.XamlIntegration.ActivityXamlServices> obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instance do a z XAML a k načítání pracovních postupů XAML a vrátí <xref:System.Activities.DynamicActivity> , který může být vyvolána. V následujícím příkladu <xref:System.Activities.ActivityBuilder> instanci z předchozího příkladu serializovat do řetězce a také uloží do souboru.  
  
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
  
 Následující příklad představuje serializovaná pracovního postupu.  
  
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
  
 Načíst serializovaná pracovního postupu, <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda se používá. Tato definice pracovního postupu serializovaná převezme a vrátí <xref:System.Activities.DynamicActivity> , která představuje definici pracovního postupu. Všimněte si, že XAML není deserializovat do <xref:System.Activities.Activity.CacheMetadata%2A> je volána v těle <xref:System.Activities.DynamicActivity> během procesu ověřování. Pokud ověření není explicitně volána. pak se provede při vyvolání pracovního postupu. Pokud definice pracovního postupu XAML je neplatný, pak <xref:System.ArgumentException> je vyvolána výjimka. Výjimky vyvolané z <xref:System.Activities.Activity.CacheMetadata%2A> úniku z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a volající musí být zpracován. V následujícím příkladu je serializovaná pracovní postup z předchozího příkladu načten a vyvolány pomocí <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 Když uživatel vyvolá tento pracovní postup, se zobrazí následující výstup do konzoly.  
  
 **25 + 15**  
**40**    
> [!NOTE]
>  Další informace o volání pracovní postupy s vstupní a výstupní argumenty najdete v tématu [použití WorkflowInvoker a WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A>.  
  
 Pokud obsahuje serializovaná pracovního postupu C# výrazy, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instanci s jeho <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastnost nastavena na `true` musí být předán jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, jinak <xref:System.NotSupportedException> a zobrazí se zpráva podobná, bude vyvolána pro následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že pracovní postup byl zkompilován. "  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 Další informace najdete v tématu [ C# výrazy](csharp-expressions.md).  
  
 Je také možné načíst definice serializovaná pracovního postupu do <xref:System.Activities.ActivityBuilder> instance pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody. Po načtení serializovaná pracovní postup do <xref:System.Activities.ActivityBuilder> instance, můžete ho zkontrolovat a upravit. To je užitečné pro autory návrháře vlastní pracovní postupy a poskytuje mechanismus pro uložení a načtení definice pracovního postupu během procesu návrhu. V následujícím příkladu je načtena definice pracovního postupu serializovaná z předchozího příkladu a její vlastnosti jsou kontrolovány.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
