---
title: Aktivita LINQ to Objects
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: fca4a94a951c9713a61914de6ef33e0cbb74f75e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891577"
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="a8b41-102">Aktivita LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="a8b41-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="a8b41-103">Tento příklad ukazuje, jak vytvořit aktivity pomocí LINQ to Objects elementy dotazu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8b41-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="a8b41-104">Podrobnosti o aktivitě pro FindInCollection</span><span class="sxs-lookup"><span data-stu-id="a8b41-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="a8b41-105">Tato aktivita z kolekce v paměti pomocí LINQ to Objects umožňuje uživatelům na elementy dotazu.</span><span class="sxs-lookup"><span data-stu-id="a8b41-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="a8b41-106">Je nutné zadat predikát LINQ ve formě lambda výraz k filtrování výsledků.</span><span class="sxs-lookup"><span data-stu-id="a8b41-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="a8b41-107">Tato aktivita se dá použít ve spojení s <xref:System.Activities.Statements.AddToCollection%601> aktivity.</span><span class="sxs-lookup"><span data-stu-id="a8b41-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="a8b41-108">Následující tabulka uvádí vlastnosti a návratové hodnoty pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="a8b41-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="a8b41-109">Vlastnost nebo návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8b41-109">Property or Return Value</span></span>|<span data-ttu-id="a8b41-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a8b41-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="a8b41-111">`Collection` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a8b41-111">`Collection` property</span></span>|<span data-ttu-id="a8b41-112">Požadovaná vlastnost, která určuje zdrojovou kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8b41-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="a8b41-113">`Predicate` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a8b41-113">`Predicate` property</span></span>|<span data-ttu-id="a8b41-114">Požadovaná vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="a8b41-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="a8b41-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8b41-115">Return Value</span></span>|<span data-ttu-id="a8b41-116">Filtrované kolekce.</span><span class="sxs-lookup"><span data-stu-id="a8b41-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="a8b41-117">Vzorový kód, který používá vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="a8b41-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="a8b41-118">Následující příklad kódu používá `FindInCollection` vlastní aktivita pro vyhledání všech řádků v kolekci zaměstnanců, kteří mají `Role` vlastnost nastavena na hodnotu `Manager` a `Location` nastavenou na `Redmond`.</span><span class="sxs-lookup"><span data-stu-id="a8b41-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="a8b41-119">Následující kód ukazuje, jak vytvořit pracovní postup program, který používá vlastní aktivity FindInCollection <xref:System.Activities.Statements.AddToCollection%601>, a <xref:System.Activities.Statements.ForEach%601> aktivity k naplnění kolekce se zaměstnanci pro oblast, najít všechny zaměstnance role pro vývojáře, jež jsou umístěny v Redmond a potom iterovat v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="a8b41-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a8b41-120">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a8b41-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="a8b41-121">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LinqToObjects.sln.</span><span class="sxs-lookup"><span data-stu-id="a8b41-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a8b41-122">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a8b41-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a8b41-123">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="a8b41-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8b41-124">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="a8b41-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8b41-125">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a8b41-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a8b41-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a8b41-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8b41-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a8b41-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="a8b41-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8b41-128">See Also</span></span>  
 [<span data-ttu-id="a8b41-129">Výrazy lambda (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a8b41-129">Lambda Expressions (C# Programming Guide)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="a8b41-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="a8b41-130">LINQ to Objects</span></span>](https://go.microsoft.com/fwlink/?LinkID=150380)
