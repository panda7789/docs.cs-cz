---
title: Neobecná aktivita ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 353128d1c313be62222e091c084e5b5e37a92b58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004910"
---
# <a name="non-generic-foreach"></a>Neobecná aktivita ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] ve svých nástrojů se dodává sadu tok řízení aktivit, včetně <xref:System.Activities.Statements.ForEach%601>, který umožňuje procházení <xref:System.Collections.Generic.IEnumerable%601> kolekce.  
  
 <xref:System.Activities.Statements.ForEach%601> vyžaduje jeho <xref:System.Activities.Statements.ForEach%601.Values%2A> vlastnost typu <xref:System.Collections.Generic.IEnumerable%601>. To vylučuje uživatele od iterování celého datové struktury, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní (třeba <xref:System.Collections.ArrayList>). Obecné verzi <xref:System.Activities.Statements.ForEach%601> překonává tento požadavek za cenu za běhu složitější pro zajištění kompatibility typy hodnot v kolekci.  
  
 Tento příklad ukazuje, jak implementovat neobecných <xref:System.Activities.Statements.ForEach%601> aktivita a její návrháře. Tuto aktivitu lze použít k iteraci v rámci <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>Aktivita ForEach  
 C# /VB `foreach` příkaz vytvoří výčet prvků kolekce, provádění vloženým příkazem pro každý prvek kolekce. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Ekvivalentní činnosti `foreach` jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Aktivita obsahuje seznam hodnot a tělo. Za běhu je provést iteraci seznamu a text je provedena pro každou hodnotu v seznamu.  
  
 Pro většinu případů obecné verze aktivity musí být preferovaným řešením, protože zabírá většinu scénářů, ve kterých by se použily a poskytuje kontrolu v době kompilace. Neobecnou verze může být použita pro iterace typy, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.  
  
## <a name="class-definition"></a>Definice třídy  
 Následující příklad kódu ukazuje definice není obecný `ForEach` aktivity.  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Text (volitelné)  
 <xref:System.Activities.ActivityAction> Typu <xref:System.Object>, který je proveden pro každý prvek v kolekci. Každý jednotlivý prvek je předán do datové části prostřednictvím jeho `Argument` vlastnost.  
  
 Hodnoty (volitelné)  
 Kolekce prvků, které jsou provést iteraci. Zajištění, že jsou všechny prvky kolekce typů kompatibilní se provádí v době běhu.  
  
## <a name="example-of-using-foreach"></a>Příklad použití příkazu ForEach  
 Následující kód ukazuje, jak pomocí aktivity ForEach v aplikaci.  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|Podmínka|Zpráva|Severity|Typ výjimky|  
|---------------|-------------|--------------|--------------------|  
|Hodnoty `null`|Nebyla zadána hodnota pro povinný argument aktivity "Hodnoty".|Chyba|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEach Designer  
 Návrhář aktivity pro ukázku je podobné jako u vzhled do návrháře k dispozici pro předdefinované <xref:System.Activities.Statements.ForEach%601> aktivity. Návrhář se zobrazí na panelu nástrojů v **ukázky**, **neobecné aktivity** kategorie. Návrháře jmenuje **ForEachWithBodyFactory** v sadě nástrojů, protože zveřejňuje aktivity <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivita s správně nakonfigurovaný <xref:System.Activities.ActivityAction>.  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a>Tuto ukázku spustit  
  
1. Nastavte projekt podle vašeho výběru jako spouštěcí projekt řešení:  
  
    1. **CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.  
  
    2. **DesignerTestClient** ukazuje, jak pomocí aktivity v návrháři.  
  
2. Sestavte a spusťte projekt.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
