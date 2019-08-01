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
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a>Serializace pracovních postupů a aktivit do a z jazyka XAML

Kromě kompilace do typů, které jsou obsaženy v sestaveních, mohou být definice pracovních postupů také serializovány do jazyka XAML. Tyto serializované definice mohou být znovu načteny pro úpravy nebo kontrolu, předány do systému sestavení pro kompilaci nebo načteny a vyvolány. Toto téma obsahuje přehled serializace definicí pracovních postupů a práci s definicemi pracovního postupu XAML.

## <a name="work-with-xaml-workflow-definitions"></a>Práce s definicemi pracovního postupu XAML

Chcete-li vytvořit definici pracovního postupu pro serializaci, <xref:System.Activities.ActivityBuilder> je použita třída. Vytvoření je velmi podobné jako <xref:System.Activities.DynamicActivity>vytvoření. <xref:System.Activities.ActivityBuilder> Jsou zadány všechny požadované argumenty a jsou konfigurovány aktivity, které tvoří chování. V následujícím příkladu `Add` se vytvoří aktivita, která přijímá dva vstupní argumenty, přidá je společně a vrátí výsledek. Vzhledem k tomu, že tato aktivita vrací výsledek <xref:System.Activities.ActivityBuilder%601> , je použita obecná třída.

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

Každá z <xref:System.Activities.DynamicActivityProperty> těchto instancí představuje jeden ze vstupních argumentů pracovního postupu <xref:System.Activities.ActivityBuilder.Implementation%2A> a obsahuje aktivity, které tvoří logiku pracovního postupu. Všimněte si, že výrazy r-value v tomto příkladu jsou Visual Basic výrazy. Výrazy lambda nelze serializovat na XAML, pokud <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> se nepoužívá. Pokud mají být serializované pracovní postupy v Návrháři pracovních postupů otevřeny nebo upravovány, měly by být použity Visual Basic výrazy. Další informace naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md).

Pro serializaci definice pracovního postupu reprezentované <xref:System.Activities.ActivityBuilder> instancí na kód XAML použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices> k vytvoření <xref:System.Xaml.XamlWriter>a pak použijte <xref:System.Xaml.XamlServices> k serializaci definice pracovního postupu pomocí <xref:System.Xaml.XamlWriter>. <xref:System.Activities.XamlIntegration.ActivityXamlServices>obsahuje metody pro mapování <xref:System.Activities.ActivityBuilder> instancí na a z kódu XAML a načtení pracovních postupů XAML a <xref:System.Activities.DynamicActivity> vrácení, které lze vyvolat. V následujícím příkladu <xref:System.Activities.ActivityBuilder> je instance z předchozího příkladu serializována do řetězce a uložena do souboru.

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

Chcete-li načíst serializovaný pracovní postup <xref:System.Activities.XamlIntegration.ActivityXamlServices> , použijte <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metodu. Tato definice provede serializovanou definici pracovního postupu a <xref:System.Activities.DynamicActivity> vrátí hodnotu, která představuje definici pracovního postupu. Všimněte si, že kód XAML není rekonstruován, dokud <xref:System.Activities.Activity.CacheMetadata%2A> není volán v těle <xref:System.Activities.DynamicActivity> během procesu ověřování. Pokud ověření není explicitně voláno, je provedeno při vyvolání pracovního postupu. Pokud definice pracovního postupu XAML není platná, <xref:System.ArgumentException> je vyvolána výjimka. Jakékoli výjimky vyvolané <xref:System.Activities.Activity.CacheMetadata%2A> z Escape z <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> volání a musí být zpracovány volajícím. V následujícím příkladu je serializovaný pracovní postup z předchozího příkladu načten a vyvolán pomocí <xref:System.Activities.WorkflowInvoker>.

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup.

**25 + 15**\
**40**

> [!NOTE]
> Další informace o vyvolání pracovních postupů pomocí vstupních a výstupních argumentů naleznete v tématu [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) a <xref:System.Activities.WorkflowInvoker.Invoke%2A>.

Pokud serializovaný pracovní postup C# obsahuje výrazy, pak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance s <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> vlastností nastavenou na `true` hodnotu <xref:System.NotSupportedException> musí být předána jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>do, jinak bude vyvolána se zprávou podobnou na následující: **Typ aktivity výrazu ' CSharpValue ' 1 ' vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že byl pracovní postup zkompilován.**

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Další informace najdete v tématu [ C# výrazy](csharp-expressions.md).

Serializovanou definici pracovního postupu lze také načíst do <xref:System.Activities.ActivityBuilder> instance <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> pomocí metody. Po načtení serializovaného pracovního postupu do <xref:System.Activities.ActivityBuilder> instance je možné ho zkontrolovat a upravit. To je užitečné pro vlastní autory návrháře pracovních postupů a poskytuje mechanismus pro ukládání a opětovné načítání definic pracovních postupů během procesu návrhu. V následujícím příkladu je načtena serializovaná definice pracovního postupu z předchozího příkladu a jsou zkontrolovány jeho vlastnosti.

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
