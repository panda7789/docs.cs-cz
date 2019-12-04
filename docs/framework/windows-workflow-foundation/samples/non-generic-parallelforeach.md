---
title: Neobecná ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 33e0c8ef8c04b7d58815760ae1152f63891fdfd5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715646"
---
# <a name="non-generic-parallelforeach"></a>Neobecná ParallelForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] lodí ve své sadě nástrojů sadu aktivit toku řízení, včetně <xref:System.Activities.Statements.ParallelForEach%601>, což umožňuje iteraci v kolekcích <xref:System.Collections.Generic.IEnumerable%601>.

<xref:System.Activities.Statements.ParallelForEach%601> vyžaduje, aby vlastnost <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> byla typu <xref:System.Collections.Generic.IEnumerable%601>. To uživatelům brání v iteracích v datových strukturách, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní (například <xref:System.Collections.ArrayList>). Neobecná verze <xref:System.Activities.Statements.ParallelForEach%601> přebírá tento požadavek, na úkor více složitosti za běhu za účelem zajištění kompatibility typů hodnot v kolekci.

Tento příklad ukazuje, jak implementovat neobecnou <xref:System.Activities.Statements.ParallelForEach%601> aktivitu a její Návrhář. Tuto aktivitu lze použít k iterování prostřednictvím <xref:System.Collections.ArrayList>.

## <a name="parallelforeach-activity"></a>Aktivita ParallelForEach

Příkaz C#/VB `foreach` vytvoří výčet prvků kolekce a spustí vložený příkaz pro každý prvek kolekce. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ekvivalentní aktivity jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>. Aktivita <xref:System.Activities.Statements.ForEach%601> obsahuje seznam hodnot a textů. V době běhu se seznam opakuje a text se spustí pro každou hodnotu v seznamu.

<xref:System.Activities.Statements.ParallelForEach%601> má <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, aby byla <xref:System.Activities.Statements.ParallelForEach%601> aktivita dokončena včas, pokud vyhodnocení <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vrátí `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> se vyhodnocuje po dokončení každé iterace.

Ve většině případů by měla být obecná verze aktivity upřednostňovaným řešením, protože pokrývá většinu scénářů, ve kterých se používá, a poskytuje kontrolu typu v době kompilace. Neobecnou verzi lze použít pro iteraci v rámci typů, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.

## <a name="class-definition"></a>Definice třídy

Následující příklad kódu ukazuje definici neobecného `ParallelForEach` aktivity je.

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

Tělo (volitelné) \
<xref:System.Activities.ActivityAction> typu <xref:System.Object>, který se spustí pro každý prvek v kolekci. Každý jednotlivý prvek je předán do těla prostřednictvím jeho vlastnosti argumentu.

Hodnoty (volitelné) \
Kolekce prvků, které jsou iterované přes. Zajistěte, aby všechny prvky kolekce byly kompatibilní typy v době běhu.

CompletionCondition (volitelné) \
Vlastnost <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> je vyhodnocena po dokončení jakékoli iterace. Pokud se vyhodnotí jako `true`, naplánovaných nevyřízených iterací se zruší. Pokud tato vlastnost není nastavená, všechny aktivity v kolekci větví se spustí až do dokončení.

## <a name="example-of-using-parallelforeach"></a>Příklad použití ParallelForEach

Následující kód ukazuje, jak používat aktivitu ParallelForEach v aplikaci.

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a>Návrhář ParallelForEach

Návrhář aktivity pro ukázku je podobný vzhledu pro návrháře poskytnutého pro integrovanou <xref:System.Activities.Statements.ParallelForEach%601> aktivitu. Návrhář se zobrazí v sadě nástrojů v kategorii **ukázky**, **neobecné aktivity** . Návrhář má název **ParallelForEachWithBodyFactory** v sadě nástrojů, protože aktivita zpřístupňuje <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivitu s správně nakonfigurovanou <xref:System.Activities.ActivityAction>.

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a>Chcete-li spustit ukázku

1. Nastavte zvolený projekt jako projekt po spuštění řešení.

    1. **CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.

    2. **DesignerTestClient** ukazuje, jak používat aktivitu v návrháři.

2. Sestavte a spusťte projekt.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
