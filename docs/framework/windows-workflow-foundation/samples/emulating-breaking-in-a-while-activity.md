---
title: "Emulace nejnovější ve chvíli aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22a03c2e7dcc8d024ed407e7df24a4e9db4e2bf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="emulating-breaking-in-a-while-activity"></a>Emulace nejnovější ve chvíli aktivity
Tento příklad ukazuje, jak rozdělit opakování mechanismus z následujících aktivit: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, a <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 To je užitečné, protože [!INCLUDE[wf](../../../../includes/wf-md.md)] neobsahuje žádné aktivity pro přerušení provádění těchto smyčky.  
  
## <a name="scenario"></a>Scénář  
 Ukázka vyhledá první spolehlivé dodavatele ze seznamu dodavatelů (instance `Vendor` třídy). Má jednotlivých dodavatelů `ID`, `Name` a spolehlivost číselnou hodnotu, která určuje, jak spolehlivé dodavatele. Ukázka vytvoří vlastní aktivity volá `FindReliableVendor` který přijímá dva vstupní parametry (seznam dodavateli a hodnotu minimální spolehlivost) a vrátí první dodavatele tohoto seznamu, který odpovídá zadaným kritériím.  
  
## <a name="breaking-a-loop"></a>Pozastavení smyčku  
 [!INCLUDE[wf](../../../../includes/wf-md.md)]nezahrnuje aktivitu pro přerušení smyčku. Ukázka kódu provede nejnovější smyčku pomocí <xref:System.Activities.Statements.If> aktivity a několik proměnné. V ukázce <xref:System.Activities.Statements.While> aktivity je porušený jednou `reliableVendor` proměnné je jiné než přiřazenou hodnotu `null`.  
  
 Následující příklad kódu ukazuje, jak ukázku dělí chvíli smyčky.  
  
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
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`