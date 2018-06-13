---
title: Vytvoření DynamicActivity
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 93435be69f90ca0b74dae6b934cb145fabb7afff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518099"
---
# <a name="dynamicactivity-creation"></a>Vytvoření DynamicActivity
Tento příklad ukazuje dva různé způsoby vytvoření aktivitu pomocí modulu runtime <xref:System.Activities.DynamicActivity> aktivity.  
  
 V této ukázce je aktivita vytvoří za běhu pomocí textu, který obsahuje <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.Assign%601> aktivity. Vstupní seznam celých čísel, je předaná do aktivity a nastavit jako vlastnost. <xref:System.Activities.Statements.ForEach%601> Aktivita pak iteruje nad seznam hodnot a shromažďuje ho. V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota se vypočítá jako podíl je zásobník a počet elementů v seznamu a přiřaďte ho ke průměr.  
  
 Ukázka ukazuje použití <xref:System.Activities.DynamicActivity> výstupní aktivity, která se zobrazí v seznamu proměnných jako vstupní argumenty a vrácení hodnot jako argumenty. Aktivita má jeden vstupní argument s názvem `Numbers` tedy seznam celých čísel. <xref:System.Activities.Statements.ForEach%601> Aktivita iteruje nad seznam hodnot a shromažďuje ho. V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota je vypočítána dělení je zásobník počet elementů v seznamu a jeho přiřazení k průměr. Průměr je vrácen jako výstup argument s názvem `Average`.  
  
 Při vytvoření prostřednictvím kódu programu dynamické aktivity, vstupní a výstupní jsou deklarovány, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 Následující příklad kódu ukazuje dokončení definice `DynamicActivity` , vypočítá průměrnou hodnotu hodnot v seznamu.  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 Při vytvoření v jazyce XAML, vstupní a výstupní jsou deklarovány, jak je znázorněno v následujícím příkladu.  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 XAML lze vytvořit vizuálně pomocí [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]. Pokud je zahrnutý v projektu sady Visual Studio, nezapomeňte nastavit jeho "sestavení Action" na "Žádný" zabráníte kompilován. XAML můžete načíst pak dynamicky pomocí následující volání.  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <xref:System.Activities.DynamicActivity> Instance vytvořené prostřednictvím kódu programu, nebo prostřednictvím načítání XAML lze použít pracovní postup, jak je znázorněno v následujícím příkladu kódu. Upozorňujeme, že "jednat" předaný `WorkflowInvoker.Invoke` je "akce" <xref:System.Activities.Activity> definované v prvním příkladu kódu.  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení DynamicActivityCreation.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
## <a name="command-line-arguments"></a>Argumenty příkazového řádku.  
 Tato ukázka je možné zadat argumenty příkazového řádku. Uživatelé mohou poskytovat seznam čísel aktivity pro výpočet svoje průměru. Seznam čísel, který se má použít se předá jako seznam čísel oddělené mezerou. Například vypočítat průměr 5, 10 a 32 vyvolat ukázku pomocí následující příkazový řádek.  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`