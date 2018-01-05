---
title: LINQ na objekty aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff77211000cfdda9c35e5a0dcbc69fc0eaf5c3be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="d64bd-102">LINQ na objekty aktivity</span><span class="sxs-lookup"><span data-stu-id="d64bd-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="d64bd-103">Tento příklad znázorňuje postup vytvoření aktivitu pomocí LINQ na objekty dotazu elementů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d64bd-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="d64bd-104">Podrobnosti o aktivitě pro FindInCollection</span><span class="sxs-lookup"><span data-stu-id="d64bd-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="d64bd-105">Tato aktivita umožňuje uživatelům na dotaz elementy z kolekce v paměti pomocí LINQ na objekty.</span><span class="sxs-lookup"><span data-stu-id="d64bd-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="d64bd-106">Je nutné zadat predikát LINQ ve formě výrazu lambda filtrování výsledků.</span><span class="sxs-lookup"><span data-stu-id="d64bd-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="d64bd-107">Tato aktivita lze použít ve spojení s <xref:System.Activities.Statements.AddToCollection%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="d64bd-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="d64bd-108">V následující tabulce jsou hodnoty vlastností a vraťte se pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="d64bd-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="d64bd-109">Vlastnost nebo vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="d64bd-109">Property or Return Value</span></span>|<span data-ttu-id="d64bd-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d64bd-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="d64bd-111">`Collection`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d64bd-111">`Collection` property</span></span>|<span data-ttu-id="d64bd-112">Povinnou vlastnost, která určuje zdrojové kolekci.</span><span class="sxs-lookup"><span data-stu-id="d64bd-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="d64bd-113">`Predicate`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d64bd-113">`Predicate` property</span></span>|<span data-ttu-id="d64bd-114">Povinnou vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="d64bd-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="d64bd-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d64bd-115">Return Value</span></span>|<span data-ttu-id="d64bd-116">Filtrované kolekce.</span><span class="sxs-lookup"><span data-stu-id="d64bd-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="d64bd-117">Ukázka kódu, který používá vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="d64bd-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="d64bd-118">Následující příklad kódu používá `FindInCollection` vlastní aktivity najít všechny řádky v kolekci zaměstnanců, kteří mají `Role` vlastnost nastavena na hodnotu `Manager` a `Location` vlastnost nastavena na hodnotu `Redmond`.</span><span class="sxs-lookup"><span data-stu-id="d64bd-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="d64bd-119">Následující kód ukazuje, jak vytvořit program pracovního postupu, který používá vlastní aktivity FindInCollection <xref:System.Activities.Statements.AddToCollection%601>, a <xref:System.Activities.Statements.ForEach%601> aktivity k naplnění kolekce se zaměstnanci, najít všechny zaměstnance, kteří mají vývojáře role a jsou umístěny v Redmond a pak iterace v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="d64bd-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
```csharp  
// Create the Linq predicate for the find expression  
  
Func<Employee, bool> predicate = e => e.Role == "DEV" && e.Location.Equals("Redmond");  
  
// Create workflow program  
Activity sampleWorkflow = new Sequence  
{  
    Variables = { employees, devsFromRedmond },  
    Activities =  
    {  
        new Assign<IList<Employee>>  
        {  
            To = employees,  
            Value = new LambdaValue<IList<Employee>>(c => new List<Employee>())  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(1, "Employee 1", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(2, "Employee 2", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(3, "Employee 3", "PM", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(4, "Employee 4", "PM", "China"))  
        },  
        new FindInCollection<Employee>  
        {  
            Collections = new InArgument<IEnumerable<Employee>>(employees),  
            Predicate = new LambdaValue<Func<Employee, bool>>(c => predicate),  
            Result = new OutArgument<IList<Employee>>(devsFromRedmond)  
        },  
        new ForEach<Employee>  
        {  
            Values = new InArgument<IEnumerable<Employee>>(devsFromRedmond),  
            Body = new ActivityAction<Employee>  
            {  
                Argument = iterationVariable,  
                Handler = new WriteLine  
                {  
                    Text = new InArgument<string>(env => iterationVariable.Get(env).ToString())  
                }  
            }  
        }  
    }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d64bd-120">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="d64bd-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="d64bd-121">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LinqToObjects.sln.</span><span class="sxs-lookup"><span data-stu-id="d64bd-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d64bd-122">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="d64bd-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d64bd-123">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="d64bd-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d64bd-124">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d64bd-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d64bd-125">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d64bd-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d64bd-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d64bd-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d64bd-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d64bd-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="d64bd-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d64bd-128">See Also</span></span>  
 [<span data-ttu-id="d64bd-129">Lambda – výrazy (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="d64bd-129">Lambda Expressions (C# Programming Guide)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="d64bd-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="d64bd-130">LINQ to Objects</span></span>](http://go.microsoft.com/fwlink/?LinkID=150380)
