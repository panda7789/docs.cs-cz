---
title: "Vytvoření DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a579606bd3ee9d3f11669d59c6e7c9767b6eaf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="0b5fa-102">Vytvoření DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="0b5fa-102">DynamicActivity Creation</span></span>
<span data-ttu-id="0b5fa-103">Tento příklad ukazuje dva různé způsoby vytvoření aktivitu pomocí modulu runtime <xref:System.Activities.DynamicActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="0b5fa-104">V této ukázce je aktivita vytvoří za běhu pomocí textu, který obsahuje <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.Assign%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="0b5fa-105">Vstupní seznam celých čísel, je předaná do aktivity a nastavit jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="0b5fa-106"><xref:System.Activities.Statements.ForEach%601> Aktivita pak iteruje nad seznam hodnot a shromažďuje ho.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="0b5fa-107">V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota se vypočítá jako podíl je zásobník a počet elementů v seznamu a přiřaďte ho ke průměr.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="0b5fa-108">Ukázka ukazuje použití <xref:System.Activities.DynamicActivity> výstupní aktivity, která se zobrazí v seznamu proměnných jako vstupní argumenty a vrácení hodnot jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="0b5fa-109">Aktivita má jeden vstupní argument s názvem `Numbers` tedy seznam celých čísel.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="0b5fa-110"><xref:System.Activities.Statements.ForEach%601> Aktivita iteruje nad seznam hodnot a shromažďuje ho.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="0b5fa-111">V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota je vypočítána dělení je zásobník počet elementů v seznamu a jeho přiřazení k průměr.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="0b5fa-112">Průměr je vrácen jako výstup argument s názvem `Average`.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="0b5fa-113">Při vytvoření prostřednictvím kódu programu dynamické aktivity, vstupní a výstupní jsou deklarovány, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="0b5fa-114">Následující příklad kódu ukazuje dokončení definice `DynamicActivity` , vypočítá průměrnou hodnotu hodnot v seznamu.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
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
  
 <span data-ttu-id="0b5fa-115">Při vytvoření v jazyce XAML, vstupní a výstupní jsou deklarovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0b5fa-116">XAML lze vytvořit vizuálně pomocí [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b5fa-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="0b5fa-117">Pokud je zahrnutý v projektu sady Visual Studio, nezapomeňte nastavit jeho "sestavení Action" na "Žádný" zabráníte kompilován.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="0b5fa-118">XAML můžete načíst pak dynamicky pomocí následující volání.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="0b5fa-119"><xref:System.Activities.DynamicActivity> Instance vytvořené prostřednictvím kódu programu, nebo prostřednictvím načítání XAML lze použít pracovní postup, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="0b5fa-120">Upozorňujeme, že "jednat" předaný `WorkflowInvoker.Invoke` je "akce" <xref:System.Activities.Activity> definované v prvním příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0b5fa-121">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="0b5fa-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="0b5fa-122">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení DynamicActivityCreation.sln.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="0b5fa-123">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0b5fa-124">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="0b5fa-125">Argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-125">Command line arguments</span></span>  
 <span data-ttu-id="0b5fa-126">Tato ukázka je možné zadat argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="0b5fa-127">Uživatelé mohou poskytovat seznam čísel aktivity pro výpočet svoje průměru.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="0b5fa-128">Seznam čísel, který se má použít se předá jako seznam čísel oddělené mezerou.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="0b5fa-129">Například vypočítat průměr 5, 10 a 32 vyvolat ukázku pomocí následující příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="0b5fa-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="0b5fa-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="0b5fa-131">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b5fa-132">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0b5fa-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b5fa-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b5fa-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0b5fa-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`  
  
## <a name="see-also"></a><span data-ttu-id="0b5fa-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b5fa-135">See Also</span></span>
