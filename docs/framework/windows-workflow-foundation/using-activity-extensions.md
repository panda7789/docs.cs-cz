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
# <a name="using-activity-extensions"></a><span data-ttu-id="a69e3-102">Používání rozšíření aktivit</span><span class="sxs-lookup"><span data-stu-id="a69e3-102">Using Activity Extensions</span></span>
<span data-ttu-id="a69e3-103">Aktivity můžou pracovat s rozšířeními aplikačních pracovních postupů, která hostiteli umožňují poskytovat další funkce, které nejsou explicitně modelované v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="a69e3-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="a69e3-104">V tomto tématu se dozvíte, jak vytvořit a použít rozšíření k výpočtu počtu vykonání aktivity.</span><span class="sxs-lookup"><span data-stu-id="a69e3-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="a69e3-105">Použití rozšíření aktivity k výpočtu počtu provedení</span><span class="sxs-lookup"><span data-stu-id="a69e3-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="a69e3-106">Otevřete Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="a69e3-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="a69e3-107">Vyberte **Nový**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="a69e3-107">Select **New**, **Project**.</span></span> <span data-ttu-id="a69e3-108">V uzlu **vizuál C#**  vyberte **pracovní postup**.</span><span class="sxs-lookup"><span data-stu-id="a69e3-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="a69e3-109">V seznamu šablon vyberte **Konzolová aplikace pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="a69e3-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="a69e3-110">Pojmenujte `Extensions`projekt.</span><span class="sxs-lookup"><span data-stu-id="a69e3-110">Name the project `Extensions`.</span></span> <span data-ttu-id="a69e3-111">Kliknutím na tlačítko **OK** vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="a69e3-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="a69e3-112">Do souboru program.cs přidejte příkazproobornázvůSystem.Collections.`using` Generic.</span><span class="sxs-lookup"><span data-stu-id="a69e3-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```csharp
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="a69e3-113">V souboru Program.cs vytvořte novou třídu s názvem **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="a69e3-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="a69e3-114">Následující kód vytvoří rozšíření pracovního postupu, které sleduje identifikátory instancí při volání metody **registru** .</span><span class="sxs-lookup"><span data-stu-id="a69e3-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

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

4. <span data-ttu-id="a69e3-115">Vytvoření aktivity, která spotřebovává **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="a69e3-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="a69e3-116">Následující kód definuje aktivitu, která načte objekt **ExecutionCountExtension** z modulu runtime a volá jeho metodu **Register** , když se aktivita spustí.</span><span class="sxs-lookup"><span data-stu-id="a69e3-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

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

5. <span data-ttu-id="a69e3-117">Implementujte aktivitu v metodě **Main** souboru program.cs.</span><span class="sxs-lookup"><span data-stu-id="a69e3-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="a69e3-118">Následující kód obsahuje metody pro vygenerování dvou různých pracovních postupů, spuštění každého pracovního postupu několikrát a zobrazení výsledných dat, která jsou obsažena v rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a69e3-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

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
