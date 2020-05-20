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
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a>Serializace pracovních postupů a aktivit do a z jazyka XAML

Kromě kompilace do typů, které jsou obsaženy v sestaveních, mohou být definice pracovních postupů také serializovány do jazyka XAML. Tyto serializované definice mohou být znovu načteny pro úpravy nebo kontrolu, předány do systému sestavení pro kompilaci nebo načteny a vyvolány. Toto téma obsahuje přehled serializace definicí pracovních postupů a práci s definicemi pracovního postupu XAML.

## <a name="work-with-xaml-workflow-definitions"></a>Práce s definicemi pracovního postupu XAML

Chcete-li vytvořit definici pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> je použita třída. Vytvoření <xref:System.Activities.ActivityBuilder> je velmi podobné jako vytvoření <xref:System.Activities.DynamicActivity> . Jsou zadány všechny požadované argumenty a jsou konfigurovány aktivity, které tvoří chování. V následujícím příkladu `Add` se vytvoří aktivita, která přijímá dva vstupní argumenty, přidá je společně a vrátí výsledek. Vzhledem k tomu, že tato aktivita vrací výsledek, <xref:System.Activities.ActivityBuilder%601> je použita obecná třída.

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

Každá z těchto <xref:System.Activities.DynamicActivityProperty> instancí představuje jeden ze vstupních argumentů pracovního postupu a <xref:System.Activities.ActivityBuilder.Implementation%2A> obsahuje aktivity, které tvoří logiku pracovního postupu. Všimněte si, že výrazy r-value v tomto příkladu jsou Visual Basic výrazy. Výrazy lambda nelze serializovat na XAML, pokud <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se nepoužívá. Pokud mají být serializované pracovní postupy v Návrháři pracovních postupů otevřeny nebo upravovány, měly by být použity Visual Basic výrazy. Další informace naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).

Pro serializaci definice pracovního postupu reprezentované <xref:System.Activities.ActivityBuilder> instancí na kód XAML použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter> a pak použijte <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter> . <xref:System.Activities.XamlIntegration.ActivityXamlServices>obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instancí na a z kódu XAML a načtení pracovních postupů XAML a vrácení <xref:System.Activities.DynamicActivity> , které lze vyvolat. V následujícím příkladu <xref:System.Activities.ActivityBuilder> je instance z předchozího příkladu serializována do řetězce a uložena do souboru.

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

Následující příklad představuje serializovaný pracovní postup.

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

Chcete-li načíst serializovaný pracovní postup, použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodu. Tato definice provede serializovanou definici pracovního postupu a vrátí hodnotu <xref:System.Activities.DynamicActivity> , která představuje definici pracovního postupu. Všimněte si, že kód XAML není rekonstruován, dokud <xref:System.Activities.Activity.CacheMetadata%2A> není volán v těle <xref:System.Activities.DynamicActivity> během procesu ověřování. Pokud ověření není explicitně voláno, je provedeno při vyvolání pracovního postupu. Pokud definice pracovního postupu XAML není platná, <xref:System.ArgumentException> je vyvolána výjimka. Jakékoli výjimky vyvolané z <xref:System.Activities.Activity.CacheMetadata%2A> Escape z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracovány volajícím. V následujícím příkladu je serializovaný pracovní postup z předchozího příkladu načten a vyvolán pomocí <xref:System.Activities.WorkflowInvoker> .

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.

**25 + 15**\
**40**

> [!NOTE]
> Další informace o vyvolání pracovních postupů pomocí vstupních a výstupních argumentů naleznete v tématu [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A> .

Pokud serializovaný pracovní postup obsahuje výrazy jazyka C#, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance s <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastností nastavenou na hodnotu `true` musí být předána jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> , jinak <xref:System.NotSupportedException> bude vyvolána zpráva podobná následující: **typ aktivity výrazu ' CSharpValue ' 1 ' vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že byl pracovní postup zkompilován.**

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Další informace naleznete v tématu [výrazy jazyka C#](csharp-expressions.md).

Serializovanou definici pracovního postupu lze také načíst do <xref:System.Activities.ActivityBuilder> instance pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody. Po načtení serializovaného pracovního postupu do <xref:System.Activities.ActivityBuilder> instance je možné ho zkontrolovat a upravit. To je užitečné pro vlastní autory návrháře pracovních postupů a poskytuje mechanismus pro ukládání a opětovné načítání definic pracovních postupů během procesu návrhu. V následujícím příkladu je načtena serializovaná definice pracovního postupu z předchozího příkladu a jsou zkontrolovány jeho vlastnosti.

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
