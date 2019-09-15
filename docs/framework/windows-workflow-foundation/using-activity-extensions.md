---
title: Používání rozšíření aktivit
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 551ce24db8c0adc8225ac94a1d05f998a26873a9
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988636"
---
# <a name="using-activity-extensions"></a>Používání rozšíření aktivit
Aktivity můžou pracovat s rozšířeními aplikačních pracovních postupů, která hostiteli umožňují poskytovat další funkce, které nejsou explicitně modelované v pracovním postupu.  V tomto tématu se dozvíte, jak vytvořit a použít rozšíření k výpočtu počtu vykonání aktivity.

### <a name="to-use-an-activity-extension-to-count-executions"></a>Použití rozšíření aktivity k výpočtu počtu provedení

1. Otevřete Visual Studio 2010. Vyberte **Nový**, **projekt**. V uzlu **vizuál C#**  vyberte **pracovní postup**.  V seznamu šablon vyberte **Konzolová aplikace pracovního postupu** . Pojmenujte `Extensions`projekt. Kliknutím na tlačítko **OK** vytvořte projekt.

2. Do souboru program.cs přidejte příkazproobornázvůSystem.Collections.`using` Generic.

    ```csharp
    using System.Collections.Generic;
    ```

3. V souboru Program.cs vytvořte novou třídu s názvem **ExecutionCountExtension**. Následující kód vytvoří rozšíření pracovního postupu, které sleduje identifikátory instancí při volání metody **registru** .

    ```csharp
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

4. Vytvoření aktivity, která spotřebovává **ExecutionCountExtension**. Následující kód definuje aktivitu, která načte objekt **ExecutionCountExtension** z modulu runtime a volá jeho metodu **Register** , když se aktivita spustí.

    ```csharp
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

5. Implementujte aktivitu v metodě **Main** souboru program.cs. Následující kód obsahuje metody pro vygenerování dvou různých pracovních postupů, spuštění každého pracovního postupu několikrát a zobrazení výsledných dat, která jsou obsažena v rozšíření.

    ```csharp
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
