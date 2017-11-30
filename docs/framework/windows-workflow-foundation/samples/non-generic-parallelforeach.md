---
title: "Neobecné ParallelForEach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 266e9468eef0a78f87b37f75ed19c5d5d3b99994
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="non-generic-parallelforeach"></a>Neobecné ParallelForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]se dodává v jeho nástrojů sadu aktivity toku řízení, včetně <xref:System.Activities.Statements.ParallelForEach%601>, což umožňuje iterace v rámci <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` kolekce.  
  
 <xref:System.Activities.Statements.ParallelForEach%601>vyžaduje jeho <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> vlastnost, která má být typu <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. To vylučuje uživatelé z iterování přes datové struktury, které implementují <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` rozhraní (například <xref:System.Collections.ArrayList>). Verze neobecnou <xref:System.Activities.Statements.ParallelForEach%601> překonává tento požadavek za cenu složitější běhu k zajištění kompatibility typů hodnot v kolekci.  
  
 Tento příklad ukazuje, jak implementovat není obecný <xref:System.Activities.Statements.ParallelForEach%601> aktivita a její designer. Tato aktivita lze použít k iteraci v rámci <xref:System.Collections.ArrayList>.  
  
## <a name="parallelforeach-activity"></a>ParallelForEach aktivity  
 C# / VB. `foreach` příkaz zobrazí prvky kolekce, provádění příkazu embedded pro každý prvek kolekce. [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Ekvivalentní aktivity jsou <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.ParallelForEach%601>. <xref:System.Activities.Statements.ForEach%601> Aktivity obsahuje seznam hodnoty a text. V době běhu je vstupní seznamu a text je provést pro každou hodnotu v seznamu.  
  
 <xref:System.Activities.Statements.ParallelForEach%601>má <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>tak, aby <xref:System.Activities.Statements.ParallelForEach%601> aktivity mohli dokončit již v rané fázi, pokud vyhodnocení <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> vrátí `true`. <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Vyhodnotí po dokončení každé iteraci.  
  
 Pro většině případů obecné verze aktivity musí být upřednostňované řešení, protože pokrývá většinu scénářů, ve kterých se používá a poskytuje typ kontroly v době kompilace. Verze neobecnou lze použít pro iterace v rámci typy, které implementují neobecnou <xref:System.Collections.IEnumerable> rozhraní.  
  
## <a name="class-definition"></a>Definice třídy  
 Následující příklad kódu ukazuje definici není obecný `ParallelForEach` aktivita.  
  
```  
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
  
 Text (volitelné)  
 <xref:System.Activities.ActivityAction> Typu <xref:System.Object>, který je spouštěna každý prvek v kolekci. Každý jednotlivý prvek předána do těla jeho vlastnosti argumentu.  
  
 Hodnoty (volitelné)  
 Kolekce elementů, které jsou vstupní přes. Zajistíte, že všechny elementy kolekce typů kompatibilní se provádí za běhu.  
  
 CompletionCondition (volitelné)  
 <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> Vlastnost vyhodnotí po dokončení všech iterací. Pokud je vyhodnocen jako `true`, pak naplánované čeká na opakování došlo ke zrušení. Pokud není tato vlastnost nastavena, všechny aktivity v kolekci větví spustit až do dokončení.  
  
## <a name="example-of-using-parallelforeach"></a>Příklad použití ParallelForEach  
 Následující kód ukazuje, jak pomocí aktivity ParallelForEach v aplikaci.  
  
```  
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
 Návrhář aktivity pro vzorovou se podobá vzhledu s návrháře zadaná pro integrované <xref:System.Activities.Statements.ParallelForEach%601> aktivity. Návrhář se zobrazí v panelu nástrojů v **ukázky**, **aktivity obecného bez** kategorie. Návrhář jmenuje **ParallelForEachWithBodyFactory** v sadě nástrojů, protože zpřístupní aktivity <xref:System.Activities.Presentation.IActivityTemplateFactory> v sadě nástrojů, která vytvoří aktivita s správně nakonfigurované <xref:System.Activities.ActivityAction>.  
  
```  
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
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Nastavte projekt zvoleného jako spouštěný projekt řešení.  
  
    1.  **CodeTestClient** ukazuje, jak pomocí aktivity pomocí kódu.  
  
    2.  **DesignerTestClient** ukazuje, jak pomocí aktivity v návrháři.  
  
2.  Sestavte a spusťte projekt.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
