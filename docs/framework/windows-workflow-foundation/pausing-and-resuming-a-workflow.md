---
title: Pozastavení a obnovení pracovního postupu
ms.date: 03/30/2017
ms.assetid: 11f38339-79c7-4295-b610-24a7223bbf6d
ms.openlocfilehash: aa0431b18f6d0e4b96d7494ec2e65acd355992c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860955"
---
# <a name="pausing-and-resuming-a-workflow"></a><span data-ttu-id="664e0-102">Pozastavení a obnovení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="664e0-102">Pausing and Resuming a Workflow</span></span>
<span data-ttu-id="664e0-103">Pracovní postupy budou pozastavení a obnovení v reakci na záložek a blokující aktivity, jako <xref:System.Activities.Statements.Delay>, ale pracovního postupu je také možné explicitně pozastaveno, byla uvolněna a obnovit pomocí trvalosti.</span><span class="sxs-lookup"><span data-stu-id="664e0-103">Workflows will pause and resume in response to bookmarks and blocking activities such as <xref:System.Activities.Statements.Delay>, but a workflow can also be explicitly paused, unloaded, and resumed by using persistence.</span></span>  
  
## <a name="pausing-a-workflow"></a><span data-ttu-id="664e0-104">Pozastavení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="664e0-104">Pausing a Workflow</span></span>  
 <span data-ttu-id="664e0-105">Chcete-li pozastavit pracovní postup, použijte <xref:System.Activities.WorkflowApplication.Unload%2A>.</span><span class="sxs-lookup"><span data-stu-id="664e0-105">To pause a workflow, use <xref:System.Activities.WorkflowApplication.Unload%2A>.</span></span>  <span data-ttu-id="664e0-106">Tato metoda požádá pracovního postupu zachovat a uvolnit a vyvolá výjimku <xref:System.TimeoutException> Pokud pracovní postup neuvolní za 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="664e0-106">This method requests that the workflow persist and unload, and will throw a <xref:System.TimeoutException> if the workflow does not unload in 30 seconds.</span></span>  
  
```csharp  
try  
{  
    // attempt to unload will fail if the workflow is idle within a NoPersistZone  
    application.Unload(TimeSpan.FromSeconds(5));  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
## <a name="resuming-a-workflow"></a><span data-ttu-id="664e0-107">Obnovení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="664e0-107">Resuming a Workflow</span></span>  
 <span data-ttu-id="664e0-108">Dříve pozastavené a uvolnit pracovní postup obnovit, použijte <xref:System.Activities.WorkflowApplication.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="664e0-108">To resume a previously paused and unloaded workflow, use <xref:System.Activities.WorkflowApplication.Load%2A>.</span></span> <span data-ttu-id="664e0-109">Tato metoda načte pracovní postup z trvalého úložiště do paměti.</span><span class="sxs-lookup"><span data-stu-id="664e0-109">This method loads a workflow from a persistence store into memory.</span></span>  
  
```csharp  
WorkflowApplication application = new WorkflowApplication(activity);  
application.InstanceStore = instanceStore;  
application.Load(id);  
```  
  
## <a name="example"></a><span data-ttu-id="664e0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="664e0-110">Example</span></span>  
 <span data-ttu-id="664e0-111">Následující příklad kódu ukazuje, jak pozastavení a obnovení pracovního postupu pomocí trvalosti.</span><span class="sxs-lookup"><span data-stu-id="664e0-111">The following code sample demonstrates how to pause and resume a workflow by using persistence.</span></span>  
  
```csharp  
static string bkName = "bkName";  
static void Main(string[] args)   
{  
    StartAndUnloadInstance();  
}  
  
static void StartAndUnloadInstance()   
{  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    SqlWorkflowInstanceStore instanceStore = SetupSqlpersistenceStore();  
    wfApp.InstanceStore = instanceStore;  
    wfApp.Extensions.Add(SetupMyFileTrackingParticipant);  
    wfApp.PersistableIdle = (e) => {          ///persists application state and remove it from memory   
    return PersistableIdleAction.Unload;  
    };  
    wfApp.Unloaded = (e) => {  
        waitHandler.Set();  
    };  
    Guid id = wfApp.Id;  
    wfApp.Run();  
    waitHandler.WaitOne();  
    LoadAndCompleteInstance(id);  
}  
  
static void LoadAndCompleteInstance(Guid id)   
{            
    Console.WriteLine("Press <enter> to load the persisted workflow");  
    Console.ReadLine();  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    wfApp.InstanceStore =  
        new SqlWorkflowInstanceStore(ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString());  
    wfApp.Completed = (workflowApplicationCompletedEventArgs) => {  
        Console.WriteLine("\nWorkflowApplication has Completed in the {0} state.",  
            workflowApplicationCompletedEventArgs.CompletionState);  
    };  
    wfApp.Unloaded = (workflowApplicationEventArgs) => {  
        Console.WriteLine("WorkflowApplication has Unloaded\n");  
        waitHandler.Set();  
    };  
    wfApp.Load(id);  
    wfApp.Run();  
    waitHandler.WaitOne();  
}  
  
public static Activity GetDelayedWF()   
{  
    return new Sequence {  
        Activities ={  
            new WriteLine{Text="Workflow Started"},  
            new Delay{Duration=TimeSpan.FromSeconds(10)},  
            new WriteLine{Text="Workflow Ended"}  
        }  
    };  
}  
  
private static SqlWorkflowInstanceStore SetupSqlpersistenceStore()   
{   
     string connectionString = ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString();  
    SqlWorkflowInstanceStore sqlWFInstanceStore = new SqlWorkflowInstanceStore(connectionString);  
    sqlWFInstanceStore.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    InstanceHandle handle = sqlWFInstanceStore.CreateInstanceHandle();  
    InstanceView view = sqlWFInstanceStore.Execute(handle, new CreateWorkflowOwnerCommand(), TimeSpan.FromSeconds(5));  
    handle.Free();  
    sqlWFInstanceStore.DefaultInstanceOwner = view.InstanceOwner;  
    return sqlWFInstanceStore;  
}  
```
