---
title: Neobecná aktivita ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 52b851686ea2fdc8c573a0622fe91ca5e205edeb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637742"
---
# <a name="non-generic-parallelforeach"></a>Neobecná aktivita ParallelForEach

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] ve svých nástrojů se dodává sadu tok řízení aktivit, včetně <xref:System.Activities.Statements.ParallelForEach%601>, který umožňuje procházení <xref:System.Collections.Generic.IEnumerable%601> kolekce.

<xref:System.Activities.Statements.ParallelForEach%601> vyžaduje jeho <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> vlastnost typu <xref:System.Collections.Generic.IEnumerable%601>. To vylučuje uživatele od iterování celého datové struktury, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní (třeba <xref:System.Collections.ArrayList>). Obecné verzi <xref:System.Activities.Statements.ParallelForEach%601> překonává tento požadavek za cenu za běhu složitější pro zajištění kompatibility typy hodnot v kolekci.

Tento příklad ukazuje, jak implementovat neobecných <xref:System.Activities.Statements.ParallelForEach%601> aktivita a její návrháře. Tuto aktivitu lze použít k iteraci v rámci <xref:System.Collections.ArrayList>.

## <a name="parallelforeach-activity"></a>Použití aktivity ParallelForEach

C# /VB `foreach` příkaz vytvoří výčet prvků kolekce, provádění vloženým příkazem pro každý prvek kolekce. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Jsou ekvivalentní aktivity <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Aktivita obsahuje seznam hodnot a tělo. Za běhu je provést iteraci seznamu a text je provedena pro každou hodnotu v seznamu.

<xref:System.Activities.Statements.ParallelForEach%601> má <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>tak, aby <xref:System.Activities.Statements.ParallelForEach%601> aktivity může-li dokončeny včas vyhodnocení <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vrátí `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Je vyhodnocen po každé iteraci.

Pro většinu případů obecné verze aktivity musí být preferovaným řešením, protože zabírá většinu scénářů, ve kterých se používá a nabízí kontrolu v době kompilace. Neobecnou verze může být použita pro iterace typy, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.

## <a name="class-definition"></a>Definice třídy

Následující příklad kódu ukazuje definice není obecný `ParallelForEach` aktivita.

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

Text (volitelné) \
<xref:System.Activities.ActivityAction> Typu <xref:System.Object>, který je proveden pro každý prvek v kolekci. Každý jednotlivý prvek, jeho vlastnost Argument předána do datové části.

Hodnoty (volitelné) \
Kolekce prvků, které jsou provést iteraci. Zajištění, že jsou všechny prvky kolekce typů kompatibilní se provádí v době běhu.

(Volitelné) CompletionCondition \
<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Vlastnost je vyhodnocen po dokončení všech iterací. Pokud je vyhodnocen jako `true`, pak naplánované zrušení čekající iterací. Pokud není tato vlastnost nastavena, všechny aktivity v kolekci větví spuštěno až do dokončení.

## <a name="example-of-using-parallelforeach"></a>Příklad použití ParallelForEach

Následující kód ukazuje, jak pomocí aktivity ParallelForEach v aplikaci.

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

Návrhář aktivity pro ukázku je podobné jako u vzhled do návrháře k dispozici pro předdefinované <xref:System.Activities.Statements.ParallelForEach%601> aktivity. Návrhář se zobrazí na panelu nástrojů v **ukázky**, **neobecné aktivity** kategorie. Návrháře jmenuje **ParallelForEachWithBodyFactory** v sadě nástrojů, protože zveřejňuje aktivity <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivita pomocí správně nakonfigurovaných <xref:System.Activities.ActivityAction>.

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

1. Nastavte jako projekt po spuštění řešení projekt podle vašeho výběru.

    1. **CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.

    2. **DesignerTestClient** ukazuje, jak pomocí aktivity v návrháři.

2. Sestavte a spusťte projekt.

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
