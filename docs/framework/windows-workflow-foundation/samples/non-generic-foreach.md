---
title: Neobecné ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: c67f6e3c3afb893f7bb5713d64ce2f119eebc157
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="non-generic-foreach"></a>Neobecné ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] se dodává v jeho nástrojů sadu aktivity toku řízení, včetně <xref:System.Activities.Statements.ForEach%601>, což umožňuje iterace v rámci <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekce.  
  
 <xref:System.Activities.Statements.ForEach%601> vyžaduje jeho <xref:System.Activities.Statements.ForEach%601.Values%2A> vlastnost, která má být typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. To vylučuje uživatelé z iterování přes datové struktury, které implementují <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` rozhraní (například <xref:System.Collections.ArrayList>). Verze neobecnou <xref:System.Activities.Statements.ForEach%601> překonává tento požadavek za cenu složitější běhu k zajištění kompatibility typů hodnot v kolekci.  
  
 Tento příklad ukazuje, jak implementovat není obecný <xref:System.Activities.Statements.ForEach%601> aktivita a její designer. Tato aktivita lze použít k iteraci v rámci <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>ForEach aktivity  
 C# / VB. `foreach` příkaz zobrazí prvky kolekce, provádění příkazu embedded pro každý prvek kolekce. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Ekvivalentní činnosti `foreach` jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Aktivity obsahuje seznam hodnoty a text. V době běhu je vstupní seznamu a text je provést pro každou hodnotu v seznamu.  
  
 Pro většině případů obecné verze aktivity musí být upřednostňované řešení, protože pokrývá většinu scénářů, ve kterých se použije a poskytuje typ kontroly v době kompilace. Verze neobecnou lze použít pro iterace v rámci typy, které implementují neobecnou <xref:System.Collections.IEnumerable> rozhraní.  
  
## <a name="class-definition"></a>Definice třídy  
 Následující příklad kódu ukazuje definici není obecný `ForEach` aktivity.  
  
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
 <xref:System.Activities.ActivityAction> Typu <xref:System.Object>, který je spouštěna každý prvek v kolekci. Každý jednotlivý prvek je předána do textu prostřednictvím jeho `Argument` vlastnost.  
  
 Hodnoty (volitelné)  
 Kolekce elementů, které jsou vstupní přes. Zajistíte, že všechny elementy kolekce typů kompatibilní se provádí za běhu.  
  
## <a name="example-of-using-foreach"></a>Příklad použití příkazu ForEach  
 Následující kód ukazuje, jak pomocí příkazu ForEach aktivity v aplikaci.  
  
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
  
|Podmínka|Zpráva|Závažnost|Typ výjimky|  
|---------------|-------------|--------------|--------------------|  
|Je hodnoty `null`|Nebyla zadána hodnota pro argument požadované aktivity 'Hodnoty'.|Chyba|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Návrhář ForEach  
 Návrhář aktivity pro vzorovou se podobá vzhledu s návrháře zadaná pro integrované <xref:System.Activities.Statements.ForEach%601> aktivity. Návrhář se zobrazí v panelu nástrojů v **ukázky**, **aktivity obecného bez** kategorie. Návrhář jmenuje **ForEachWithBodyFactory** v sadě nástrojů, protože zpřístupní aktivity <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivita s správně nakonfigurované <xref:System.Activities.ActivityAction>.  
  
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
  
#### <a name="to-run-this-sample"></a>Chcete tuto ukázku spustit  
  
1.  Nastavte projekt zvoleného jako projekt spuštění řešení:  
  
    1.  **CodeTestClient** ukazuje, jak pomocí aktivity pomocí kódu.  
  
    2.  **DesignerTestClient** ukazuje, jak pomocí aktivity v návrháři.  
  
2.  Sestavte a spusťte projekt.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
