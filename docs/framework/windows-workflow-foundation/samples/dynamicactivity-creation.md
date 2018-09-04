---
title: Vytvoření dynamické aktivity
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 270066fafd5c71b2a720ca305433159c172872aa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534014"
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="bf84f-102">Vytvoření dynamické aktivity</span><span class="sxs-lookup"><span data-stu-id="bf84f-102">DynamicActivity Creation</span></span>
<span data-ttu-id="bf84f-103">Tento příklad ukazuje dva různé způsoby vytvoření aktivity za běhu pomocí <xref:System.Activities.DynamicActivity> aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf84f-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="bf84f-104">V této ukázce se vytvoří aktivity za běhu pomocí textu, který obsahuje <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje <xref:System.Activities.Statements.ForEach%601> a <xref:System.Activities.Statements.Assign%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf84f-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="bf84f-105">Vstupní seznam celých čísel je předána aktivitě a nastavit jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bf84f-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="bf84f-106"><xref:System.Activities.Statements.ForEach%601> Aktivita pak Iteruje přes seznam hodnot a shromažďuje ho.</span><span class="sxs-lookup"><span data-stu-id="bf84f-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="bf84f-107">V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota se vypočte tak, že je zásobník vydělením počtu prvků v seznamu a přiřadíte ho k průměr.</span><span class="sxs-lookup"><span data-stu-id="bf84f-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="bf84f-108">Vzorek ukazuje použití <xref:System.Activities.DynamicActivity> aktivita, která prochází v proměnné jako vstupní argumenty a vrací hodnoty jako výstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="bf84f-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="bf84f-109">Aktivita má jeden vstupní argument s názvem `Numbers` , který je seznam celá čísla.</span><span class="sxs-lookup"><span data-stu-id="bf84f-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="bf84f-110"><xref:System.Activities.Statements.ForEach%601> Aktivita Iteruje přes seznam hodnot a shromažďuje ho.</span><span class="sxs-lookup"><span data-stu-id="bf84f-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="bf84f-111">V <xref:System.Activities.Statements.Assign%601> aktivity, průměrná hodnota se počítá tak, že je zásobník vydělením počtu prvků v seznamu a přiřadí průměr.</span><span class="sxs-lookup"><span data-stu-id="bf84f-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="bf84f-112">Průměr se vrátí jako výstup argument s názvem `Average`.</span><span class="sxs-lookup"><span data-stu-id="bf84f-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="bf84f-113">Po vytvoření dynamické aktivity prostřednictvím kódu programu vstup a výstup jsou deklarovány, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="bf84f-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="bf84f-114">Následující příklad kódu ukazuje úplnou definici `DynamicActivity` , která vypočítá průměr hodnot v seznamu.</span><span class="sxs-lookup"><span data-stu-id="bf84f-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
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
  
 <span data-ttu-id="bf84f-115">Když v XAML, vstupu a výstupu jsou deklarovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bf84f-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="bf84f-116">XAML je možné vytvářet vizuálně pomocí [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf84f-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="bf84f-117">Pokud je zahrnutý v projektu sady Visual Studio, nezapomeňte nastavit jeho "akce sestavení" na "Žádný" tak, aby se na kompilaci.</span><span class="sxs-lookup"><span data-stu-id="bf84f-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="bf84f-118">XAML je možné načíst potom dynamicky použitím následujícího volání.</span><span class="sxs-lookup"><span data-stu-id="bf84f-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="bf84f-119"><xref:System.Activities.DynamicActivity> Vytvořena instance programově nebo prostřednictvím načítání XAML pracovního postupu je možné, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="bf84f-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="bf84f-120">Mějte prosím na paměti, že "fungovat" předán `WorkflowInvoker.Invoke` je "proces" <xref:System.Activities.Activity> definované v prvním příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="bf84f-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="bf84f-121">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="bf84f-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="bf84f-122">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení DynamicActivityCreation.sln.</span><span class="sxs-lookup"><span data-stu-id="bf84f-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="bf84f-123">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="bf84f-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="bf84f-124">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="bf84f-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="bf84f-125">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="bf84f-125">Command line arguments</span></span>  
 <span data-ttu-id="bf84f-126">Tato ukázka přijímá argumenty příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="bf84f-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="bf84f-127">Uživatelé mohou poskytovat seznam čísel aktivity k výpočtu jejich průměr.</span><span class="sxs-lookup"><span data-stu-id="bf84f-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="bf84f-128">Seznam čísel, který se má použít, je předán jako seznam čísel oddělených mezerou.</span><span class="sxs-lookup"><span data-stu-id="bf84f-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="bf84f-129">Průměr 5, 10 a 32 vyvolání k výpočtu vzorku pomocí následující příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="bf84f-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="bf84f-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="bf84f-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="bf84f-131">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="bf84f-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bf84f-132">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bf84f-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf84f-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bf84f-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf84f-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bf84f-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`