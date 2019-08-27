---
title: Neobecná aktivita ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: e467534ba2b233f1f3c279e89badf12846c6b7f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038066"
---
# <a name="non-generic-foreach"></a>Neobecná aktivita ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]dodá v sadě nástrojů sadu aktivit toku řízení, včetně <xref:System.Activities.Statements.ForEach%601>, což umožňuje iterace prostřednictvím <xref:System.Collections.Generic.IEnumerable%601> kolekcí.  
  
 <xref:System.Activities.Statements.ForEach%601>vyžaduje, <xref:System.Activities.Statements.ForEach%601.Values%2A> aby jeho vlastnost byla typu <xref:System.Collections.Generic.IEnumerable%601>. To uživatelům brání v iteracích v datových strukturách, <xref:System.Collections.Generic.IEnumerable%601> které implementují rozhraní ( <xref:System.Collections.ArrayList>například). Neobecnou verzi <xref:System.Activities.Statements.ForEach%601> přenese tento požadavek, na úkor více složitosti za běhu za účelem zajištění kompatibility typů hodnot v kolekci.  
  
 Tento příklad ukazuje, jak implementovat neobecnou <xref:System.Activities.Statements.ForEach%601> aktivitu a její Návrhář. Tato aktivita se dá použít k iteraci <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>Aktivita ForEach  
 Příkaz C#/VB `foreach` vytvoří výčet prvků kolekce a spustí vložený příkaz pro každý prvek kolekce. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Ekvivalentní`foreach` aktivity jsou<xref:System.Activities.Statements.ForEach%601> a .<xref:System.Activities.Statements.ParallelForEach%601> <xref:System.Activities.Statements.ForEach%601> Aktivita obsahuje seznam hodnot a textů. V době běhu se seznam opakuje a text se spustí pro každou hodnotu v seznamu.  
  
 Ve většině případů by měla být obecná verze aktivity upřednostňovaným řešením, protože pokrývá většinu scénářů, ve kterých by se použily, a poskytuje kontrolu typu v době kompilace. Neobecnou verzi lze použít pro iteraci v rámci typů, které implementují neobecné <xref:System.Collections.IEnumerable> rozhraní.  
  
## <a name="class-definition"></a>Definice třídy  
 Následující příklad kódu ukazuje definici neobecné `ForEach` aktivity.  
  
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
  
 Tělo (volitelné)  
 <xref:System.Activities.ActivityAction> Typ<xref:System.Object>, který je spuštěn pro každý prvek v kolekci. Každý jednotlivý prvek je předán do těla prostřednictvím jeho `Argument` vlastnosti.  
  
 Hodnoty (volitelné)  
 Kolekce prvků, které jsou iterované přes. Zajistěte, aby všechny prvky kolekce byly kompatibilní typy v době běhu.  
  
## <a name="example-of-using-foreach"></a>Příklad použití příkazu ForEach  
 Následující kód ukazuje, jak použít aktivitu ForEach v aplikaci.  
  
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
  
|Podmínka|Message|severity|Typ výjimky|  
|---------------|-------------|--------------|--------------------|  
|Hodnoty jsou`null`|Hodnota argumentu ' Values ' pro požadovanou aktivitu nebyla zadána.|Chyba|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Návrhář ForEach  
 Návrhář aktivity pro ukázku je podobný vzhledu pro návrháře poskytovaného pro integrovanou <xref:System.Activities.Statements.ForEach%601> aktivitu. Návrhář se zobrazí v sadě nástrojů v kategorii **ukázky**, **neobecné aktivity** . Návrhář má název **ForEachWithBodyFactory** v sadě nástrojů, protože aktivita zpřístupňuje ovládací prvek <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, který vytvoří aktivitu se správně nakonfigurovanou <xref:System.Activities.ActivityAction>.  
  
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
  
#### <a name="to-run-this-sample"></a>Spuštění této ukázky  
  
1. Nastavte projekt podle svého výběru jako spouštěcí projekt řešení:  
  
    1. **CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.  
  
    2. **DesignerTestClient** ukazuje, jak používat aktivitu v návrháři.  
  
2. Sestavte a spusťte projekt.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
