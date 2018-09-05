---
title: Emulace zastavení v nějakou aktivitu
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 4938e07364609520f6528688877bce112be26d3f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773929"
---
# <a name="emulating-breaking-in-a-while-activity"></a>Emulace zastavení v nějakou aktivitu
Tato ukázka předvádí, jak přerušení mechanismu opakování z následujících aktivit: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, a <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 To je užitečné, protože Windows Workflow Foundation (WF) neobsahuje žádnou aktivitu přerušení provádění těchto smyčky.  
  
## <a name="scenario"></a>Scénář  
 Vzorek najde první spolehlivé dodavatele ze seznamu dodavatelů (instance `Vendor` třídy). Jednotlivých dodavatelů má `ID`, `Name` a spolehlivost číselná hodnota, která určuje, jak spolehlivé dodavatel je. Ukázka vytvoří vlastní aktivity volá `FindReliableVendor` , který přijímá dva vstupní parametry (seznam dodavatelů a hodnotu minimální spolehlivost) a vrátí první dodavatele tohoto seznamu, který odpovídá zadaným kritériím.  
  
## <a name="breaking-a-loop"></a>Přerušení smyčky  
 Windows Workflow Foundation (WF) neobsahuje aktivitu pro přerušení smyčky. Vzorový kód provede přerušení smyčky s použitím <xref:System.Activities.Statements.If> aktivity a několik proměnných. V ukázce <xref:System.Activities.Statements.While> aktivit dojde k přerušení jednou `reliableVendor` proměnná má přiřazenou hodnotu jiné než `null`.  
  
 Následující příklad kódu ukazuje, jak ukázku přeruší nějakou smyčky.  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení EmulatingBreakInWhile.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`