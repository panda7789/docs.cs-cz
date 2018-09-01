---
title: Vytvoření dynamické aktivity
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 270066fafd5c71b2a720ca305433159c172872aa
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385258"
---
# <a name="dynamicactivity-creation"></a>Vytvoření dynamické aktivity
Tento příklad ukazuje dva různé způsoby vytvoření aktivity za běhu pomocí <xref:System.Activities.DynamicActivity> aktivity.  
  
 V této ukázce se vytvoří aktivity za běhu pomocí textu, který obsahuje <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.Assign%601> aktivity. Vstupní seznam celých čísel je předána aktivitě a nastavit jako vlastnost. <xref:System.Activities.Statements.ForEach%601> Aktivita pak Iteruje přes seznam hodnot a shromažďuje ho. V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota se vypočte tak, že je zásobník vydělením počtu prvků v seznamu a přiřadíte ho k průměr.  
  
 Vzorek ukazuje použití <xref:System.Activities.DynamicActivity> aktivita, která prochází v proměnné jako vstupní argumenty a vrací hodnoty jako výstupní argumenty. Aktivita má jeden vstupní argument s názvem `Numbers` , který je seznam celá čísla. <xref:System.Activities.Statements.ForEach%601> Aktivita Iteruje přes seznam hodnot a shromažďuje ho. V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota se počítá tak, že je zásobník vydělením počtu prvků v seznamu a přiřadí průměr. Průměr se vrátí jako výstup argument s názvem `Average`.  
  
 Po vytvoření dynamické aktivity prostřednictvím kódu programu vstup a výstup jsou deklarovány, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Následující příklad kódu ukazuje úplnou definici `DynamicActivity` , která vypočítá průměr hodnot v seznamu.  
  
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
  
 Když v XAML, vstupu a výstupu jsou deklarovány, jak je znázorněno v následujícím příkladu.  
  
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
  
 XAML je možné vytvářet vizuálně pomocí [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]. Pokud je zahrnutý v projektu sady Visual Studio, nezapomeňte nastavit jeho "akce sestavení" na "Žádný" tak, aby se na kompilaci. XAML je možné načíst potom dynamicky použitím následujícího volání.  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <xref:System.Activities.DynamicActivity> Vytvořena instance programově nebo prostřednictvím načítání XAML pracovního postupu je možné, jak je znázorněno v následujícím příkladu kódu. Mějte prosím na paměti, že "fungovat" předán `WorkflowInvoker.Invoke` je "proces" <xref:System.Activities.Activity> definované v prvním příkladu kódu.  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení DynamicActivityCreation.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
## <a name="command-line-arguments"></a>Argumenty příkazového řádku  
 Tato ukázka přijímá argumenty příkazového řádku. Uživatelé mohou poskytovat seznam čísel aktivity k výpočtu jejich průměr. Seznam čísel, který se má použít, je předán jako seznam čísel oddělených mezerou. Průměr 5, 10 a 32 vyvolání k výpočtu vzorku pomocí následující příkazový řádek.  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`