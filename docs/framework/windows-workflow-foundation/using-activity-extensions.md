---
title: "Pomocí rozšíření aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd8bde396cd53577a87976f8fe40c0ae3ab3708e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-activity-extensions"></a>Pomocí rozšíření aktivity
Aktivity mohou komunikovat s rozšíření pracovního postupu aplikací, které umožňují na hostiteli a poskytují další funkce, které není explicitně modelován v pracovním postupu.  Toto téma popisuje postup vytvoření a používání rozšíření počítat počet, který provádí aktivity.  
  
### <a name="to-use-an-activity-extension-to-count-executions"></a>Počet spuštěních pomocí rozšíření aktivity  
  
1.  Otevřete [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]. Vyberte **nové**, **projektu**. V části **Visual C#** uzlu, vyberte **pracovního postupu**.  Vyberte **pracovního postupu konzolové aplikace** ze seznamu šablon. Název projektu `Extensions`. Klikněte na tlačítko **OK** a vytvořte tak projekt.  
  
2.  Přidat `using` příkaz v souboru Program.cs **System.Collections.Generic** oboru názvů.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
3.  V souboru Program.cs, vytvořte novou třídu s názvem **ExecutionCountExtension**. Následující kód vytvoří rozšíření pracovního postupu, který sleduje ID instance při jeho **zaregistrovat** metoda je volána.  
  
    ```  
    // This extension collects a list of workflow Ids  
    public class ExecutionCountExtension  
    {  
        IList<Guid> instances = new List<Guid>();  
  
        public int ExecutionCount  
        {  
            get  
            {  
                return this.instances.Count;  
            }  
        }  
  
        public IEnumerable<Guid> InstanceIds  
        {  
            get  
            {  
                return this.instances;  
            }  
        }  
  
        public void Register(Guid activityInstanceId)  
        {  
            if (!this.instances.Contains<Guid>(activityInstanceId))  
            {  
                instances.Add(activityInstanceId);  
            }  
        }  
    }  
    ```  
  
4.  Vytvoření aktivity, která využívá **ExecutionCountExtension**. Následující kód definuje aktivitu, která načte **ExecutionCountExtension** objekt z modulu runtime a volání jeho **zaregistrovat** metoda když aktivita provede.  
  
    ```  
    // Activity that consumes an extension provided by the host. If the extension is available  
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)  
    public class MyActivity: CodeActivity  
    {  
        protected override void Execute(CodeActivityContext context)  
        {  
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();  
            if (ext != null)  
            {  
                ext.Register(context.WorkflowInstanceId);                         
            }  
  
        }  
    }  
    ```  
  
5.  Implementace aktivity v **hlavní** metoda souboru program.cs. Následující kód obsahuje metody pro generování dva různé pracovní postupy, spouštění každý pracovní postup několikrát a zobrazit Výsledná data, která se nachází v rozšíření.  
  
    ```  
    class Program  
    {  
        // Creates a workflow that uses the activity that consumes the extension  
        static Activity CreateWorkflow1()  
        {  
            return new Sequence  
            {  
                Activities =  
                {  
                    new MyActivity()  
                }  
            };  
        }  
  
        // Creates a workflow that uses two instances of the activity that consumes the extension  
        static Activity CreateWorkflow2()  
        {  
            return new Sequence  
            {  
                Activities =  
                {  
                    new MyActivity(),  
                    new MyActivity()  
                }  
            };  
        }  
  
        static void Main(string[] args)  
        {  
            // create the extension   
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();  
  
            // configure the first invoker and execute 3 times  
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());  
            invoker.Extensions.Add(executionCountExt);                          
            invoker.Invoke();  
            invoker.Invoke();  
            invoker.Invoke();  
  
            // configure the second invoker and execute 2 times  
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());  
            invoker2.Extensions.Add(executionCountExt);  
            invoker2.Invoke();  
            invoker2.Invoke();  
  
            // show the data in the extension  
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);  
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));  
        }  
    }  
    ```
