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
# <a name="linq-to-objects-activity"></a>Aktivita LINQ to Objects
Tento příklad ukazuje, jak vytvořit aktivity pomocí LINQ to Objects elementy dotazu v kolekci.  
  
## <a name="activity-details-for-findincollection"></a>Podrobnosti o aktivitě pro FindInCollection  
 Tato aktivita z kolekce v paměti pomocí LINQ to Objects umožňuje uživatelům na elementy dotazu. Je nutné zadat predikát LINQ ve formě lambda výraz k filtrování výsledků. Tato aktivita se dá použít ve spojení s <xref:System.Activities.Statements.AddToCollection%601> aktivity.  
  
 Následující tabulka uvádí vlastnosti a návratové hodnoty pro aktivitu.  
  
|Vlastnost nebo návratová hodnota|Popis|  
|------------------------------|-----------------|  
|`Collection` Vlastnost|Požadovaná vlastnost, která určuje zdrojovou kolekci.|  
|`Predicate` Vlastnost|Požadovaná vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.|  
|Návratová hodnota|Filtrované kolekce.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Vzorový kód, který používá vlastní aktivity  
 Následující příklad kódu používá `FindInCollection` vlastní aktivita pro vyhledání všech řádků v kolekci zaměstnanců, kteří mají `Role` vlastnost nastavena na hodnotu `Manager` a `Location` nastavenou na `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 Následující kód ukazuje, jak vytvořit pracovní postup program, který používá vlastní aktivity FindInCollection <xref:System.Activities.Statements.AddToCollection%601>, a <xref:System.Activities.Statements.ForEach%601> aktivity k naplnění kolekce se zaměstnanci pro oblast, najít všechny zaměstnance role pro vývojáře, jež jsou umístěny v Redmond a potom iterovat v rozevíracím seznamu.  
  
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
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení LinqToObjects.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte klávesu F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=150381)  
 [LINQ to Objects](https://go.microsoft.com/fwlink/?LinkID=150380)
