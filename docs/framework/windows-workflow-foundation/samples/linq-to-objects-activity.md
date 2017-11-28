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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f34189c8f9911b09017056b22611d27df25c10e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-objects-activity"></a>LINQ na objekty aktivity
Tento příklad znázorňuje postup vytvoření aktivitu pomocí LINQ na objekty dotazu elementů v kolekci.  
  
## <a name="activity-details-for-findincollection"></a>Podrobnosti o aktivitě pro FindInCollection  
 Tato aktivita umožňuje uživatelům na dotaz elementy z kolekce v paměti pomocí LINQ na objekty. Je nutné zadat predikát LINQ ve formě výrazu lambda filtrování výsledků. Tato aktivita lze použít ve spojení s <xref:System.Activities.Statements.AddToCollection%601> aktivity.  
  
 V následující tabulce jsou hodnoty vlastností a vraťte se pro aktivitu.  
  
|Vlastnost nebo vrací hodnotu|Popis|  
|------------------------------|-----------------|  
|`Collection`Vlastnost|Povinnou vlastnost, která určuje zdrojové kolekci.|  
|`Predicate`Vlastnost|Povinnou vlastnost, která určuje filtr pro kolekce v podobě výrazu lambda.|  
|Návratová hodnota|Filtrované kolekce.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Ukázka kódu, který používá vlastní aktivity  
 Následující příklad kódu používá `FindInCollection` vlastní aktivity najít všechny řádky v kolekci zaměstnanců, kteří mají `Role` vlastnost nastavena na hodnotu `Manager` a `Location` vlastnost nastavena na hodnotu `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 Následující kód ukazuje, jak vytvořit program pracovního postupu, který používá vlastní aktivity FindInCollection <xref:System.Activities.Statements.AddToCollection%601>, a <xref:System.Activities.Statements.ForEach%601> aktivity k naplnění kolekce se zaměstnanci, najít všechny zaměstnance, kteří mají vývojáře role a jsou umístěny v Redmond a pak iterace v rozevíracím seznamu.  
  
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
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>Viz také  
 [Lambda – výrazy (C# Průvodce programováním)](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [LINQ na objekty](http://go.microsoft.com/fwlink/?LinkID=150380)
