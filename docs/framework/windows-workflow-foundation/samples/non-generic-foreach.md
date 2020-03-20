---
title: Neobecná aktivita ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 08dbac3974915f823a4f6e39f35927453a7c4b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142703"
---
# <a name="non-generic-foreach"></a>Neobecná aktivita ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]do své sady nástrojů dodává soubor činností <xref:System.Activities.Statements.ForEach%601>kontrolního toku, <xref:System.Collections.Generic.IEnumerable%601> včetně , který umožňuje itací prostřednictvím sbírek.  
  
 <xref:System.Activities.Statements.ForEach%601>vyžaduje, <xref:System.Activities.Statements.ForEach%601.Values%2A> aby jeho <xref:System.Collections.Generic.IEnumerable%601>majetek byl typu . To vylučuje uživatelům iterace přes datové <xref:System.Collections.Generic.IEnumerable%601> struktury, <xref:System.Collections.ArrayList>které implementují rozhraní (například). Neobecná verze <xref:System.Activities.Statements.ForEach%601> překonává tento požadavek na úkor další složitosti za běhu pro zajištění kompatibility typů hodnot v kolekci.  
  
 Tato ukázka ukazuje, jak <xref:System.Activities.Statements.ForEach%601> implementovat neobecné aktivity a jeho návrháře. Tuto aktivitu lze použít k <xref:System.Collections.ArrayList>iterátu prostřednictvím .  
  
## <a name="foreach-activity"></a>Foreach aktivity  
 Příkaz jazyka C#/Visual Basic `foreach` obsahuje výčet prvků kolekce a provádí vložený příkaz pro každý prvek kolekce. Rovnocenné [!INCLUDE[wf1](../../../../includes/wf1-md.md)] činnosti `foreach` jsou <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.ParallelForEach%601>a . Aktivita <xref:System.Activities.Statements.ForEach%601> obsahuje seznam hodnot a tělo. Za běhu je seznam iterován a tělo je spuštěno pro každou hodnotu v seznamu.  
  
 Pro většinu případů obecná verze aktivity by měla být upřednostňovaným řešením, protože pokrývá většinu scénářů, ve kterých by se použila, a poskytuje kontrolu typů v době kompilace. Neobecnou verzi lze použít pro iterace prostřednictvím typů, <xref:System.Collections.IEnumerable> které implementují neobecné rozhraní.  
  
## <a name="class-definition"></a>Definice třídy  
 Následující příklad kódu ukazuje definici neobecné `ForEach` aktivity.  
  
```csharp  
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
 Typ <xref:System.Activities.ActivityAction> <xref:System.Object>, který je proveden pro každý prvek v kolekci. Každý jednotlivý prvek je předán `Argument` do těla prostřednictvím své vlastnosti.  
  
 Hodnoty (volitelné)  
 Kolekce prvků, které jsou iterovány nad. Zajištění, že všechny prvky kolekce jsou kompatibilní typy se provádí za běhu.  
  
## <a name="example-of-using-foreach"></a>Příklad použití ForEach  
 Následující kód ukazuje, jak používat ForEach aktivity v aplikaci.  
  
```csharp  
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
|Hodnoty jsou`null`|Hodnota pro argument požadované aktivity "Hodnoty" nebyla zadána.|Chyba|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Návrhář Foreach  
 Návrhář aktivity pro ukázku má podobný vzhled jako návrhář, <xref:System.Activities.Statements.ForEach%601> který je k dispozici pro předdefinovanou aktivitu. Návrhář se zobrazí v panelu nástrojů v kategorii **Ukázky**, **Neobecné aktivity.** Návrhář se nazývá **ForEachWithBodyFactory** v panelu nástrojů, <xref:System.Activities.Presentation.IActivityTemplateFactory> protože aktivita zpřístupňuje v panelu <xref:System.Activities.ActivityAction>nástrojů, který vytvoří aktivitu s správně nakonfigurované .  
  
```csharp  
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
  
1. Nastavte projekt podle svého výběru jako počáteční projekt řešení:  
  
    1. **CodeTestClient** ukazuje, jak používat aktivitu pomocí kódu.  
  
    2. **DesignerTestClient** ukazuje, jak používat aktivitu v rámci návrháře.  
  
2. Sestavení a spuštění projektu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
