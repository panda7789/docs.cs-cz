---
title: Používání rozšíření aktivit
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321286"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="3e329-102">Používání rozšíření aktivit</span><span class="sxs-lookup"><span data-stu-id="3e329-102">Using Activity Extensions</span></span>
<span data-ttu-id="3e329-103">Aktivity můžete pracovat s příponami aplikace pracovního postupu, které povolí hostitelské funkce, která není explicitně modelován v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="3e329-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="3e329-104">Toto téma popisuje postup vytvoření a použití rozšíření ke zjištění počtu pokusů, které tato aktivity spustí.</span><span class="sxs-lookup"><span data-stu-id="3e329-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="3e329-105">Použití rozšíření aktivity mají spočítat počet spuštění</span><span class="sxs-lookup"><span data-stu-id="3e329-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="3e329-106">Open Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="3e329-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="3e329-107">Vyberte **nové**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="3e329-107">Select **New**, **Project**.</span></span> <span data-ttu-id="3e329-108">V části **Visual C#** uzlu, vyberte **pracovního postupu**.</span><span class="sxs-lookup"><span data-stu-id="3e329-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="3e329-109">Vyberte **Konzolová aplikace pracovního postupu** ze seznamu šablon.</span><span class="sxs-lookup"><span data-stu-id="3e329-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="3e329-110">Pojmenujte projekt `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="3e329-110">Name the project `Extensions`.</span></span> <span data-ttu-id="3e329-111">Klikněte na tlačítko **OK** pro vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="3e329-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="3e329-112">Přidat `using` prohlášení v souboru Program.cs **System.Collections.Generic** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3e329-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="3e329-113">V souboru Program.cs vytvořte novou třídu s názvem **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="3e329-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="3e329-114">Následující kód vytvoří, který sleduje ID instancí rozšíření pracovního postupu při jeho **zaregistrovat** metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="3e329-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

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

4. <span data-ttu-id="3e329-115">Vytvořit aktivitu, která využívá **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="3e329-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="3e329-116">Následující kód definuje aktivitu, která načte **ExecutionCountExtension** objekt z modulu runtime a volání jeho **zaregistrovat** metoda při tato aktivity spustí.</span><span class="sxs-lookup"><span data-stu-id="3e329-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

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

5. <span data-ttu-id="3e329-117">Implementujte aktivitu v **hlavní** metoda souboru program.cs.</span><span class="sxs-lookup"><span data-stu-id="3e329-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="3e329-118">Následující kód obsahuje metody pro generování dvě různé pracovní postupy, spouštění každý pracovní postup několikrát a zobrazit Výsledná data, která je obsažena v rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3e329-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

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
