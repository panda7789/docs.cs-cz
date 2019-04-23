---
title: Používání rozšíření aktivit
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768955"
---
# <a name="using-activity-extensions"></a>Používání rozšíření aktivit
Aktivity můžete pracovat s příponami aplikace pracovního postupu, které povolí hostitelské funkce, která není explicitně modelován v pracovním postupu.  Toto téma popisuje postup vytvoření a použití rozšíření ke zjištění počtu pokusů, které tato aktivity spustí.

### <a name="to-use-an-activity-extension-to-count-executions"></a>Použití rozšíření aktivity mají spočítat počet spuštění

1. Open Visual Studio 2010. Vyberte **nové**, **projektu**. V části **Visual C#** uzlu, vyberte **pracovního postupu**.  Vyberte **Konzolová aplikace pracovního postupu** ze seznamu šablon. Pojmenujte projekt `Extensions`. Klikněte na tlačítko **OK** pro vytvoření projektu.

2. Přidat `using` prohlášení v souboru Program.cs **System.Collections.Generic** oboru názvů.

    ```
    using System.Collections.Generic;
    ```

3. V souboru Program.cs vytvořte novou třídu s názvem **ExecutionCountExtension**. Následující kód vytvoří, který sleduje ID instancí rozšíření pracovního postupu při jeho **zaregistrovat** metoda je volána.

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

4. Vytvořit aktivitu, která využívá **ExecutionCountExtension**. Následující kód definuje aktivitu, která načte **ExecutionCountExtension** objekt z modulu runtime a volání jeho **zaregistrovat** metoda při tato aktivity spustí.

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

5. Implementujte aktivitu v **hlavní** metoda souboru program.cs. Následující kód obsahuje metody pro generování dvě různé pracovní postupy, spouštění každý pracovní postup několikrát a zobrazit Výsledná data, která je obsažena v rozšíření.

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
