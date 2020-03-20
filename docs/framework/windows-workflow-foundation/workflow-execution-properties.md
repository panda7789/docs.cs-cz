---
title: Vlastnosti spuštění pracovního postupu
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f958e7e112bfddc2740c2605d446493f2d49010
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182667"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="5c960-102">Vlastnosti spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="5c960-102">Workflow Execution Properties</span></span>
<span data-ttu-id="5c960-103">Prostřednictvím místního úložiště vlákna (TLS) clr udržuje kontext spuštění pro každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="5c960-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="5c960-104">Tento kontext spuštění řídí známé vlastnosti vlákna, jako je například identita vlákna, transakce okolí a aktuální sada oprávnění kromě uživatelem definovaných vlastností vlákna, jako jsou pojmenované sloty.</span><span class="sxs-lookup"><span data-stu-id="5c960-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="5c960-105">Na rozdíl od programů, které přímo cílí na CLR, jsou programy pracovního postupu hierarchicky vymezené stromy aktivit, které se provádějí v prostředí bez ohledu na vlákno.</span><span class="sxs-lookup"><span data-stu-id="5c960-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="5c960-106">To znamená, že standardní tls mechanismy nelze přímo použít k určení, jaký kontext je v oboru pro danou pracovní položku.</span><span class="sxs-lookup"><span data-stu-id="5c960-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="5c960-107">Například dvě paralelní větve provádění může používat různé transakce, ale plánovač může proložit jejich provádění ve stejném vlákně CLR.</span><span class="sxs-lookup"><span data-stu-id="5c960-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="5c960-108">Vlastnosti spuštění pracovního postupu poskytují mechanismus pro přidání vlastností specifických pro kontext do prostředí aktivity.</span><span class="sxs-lookup"><span data-stu-id="5c960-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="5c960-109">To umožňuje aktivitu deklarovat, které vlastnosti jsou v oboru pro jeho podstrom a také poskytuje háčky pro nastavení a stržení TLS správně spolupracovat s objekty CLR.</span><span class="sxs-lookup"><span data-stu-id="5c960-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="5c960-110">Vytváření a používání vlastností spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="5c960-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="5c960-111">Vlastnosti spuštění pracovního postupu obvykle implementují <xref:System.Activities.IExecutionProperty> rozhraní, i když vlastnosti zaměřené na zasílání zpráv mohou implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo toho.</span><span class="sxs-lookup"><span data-stu-id="5c960-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="5c960-112">Chcete-li vytvořit vlastnost spuštění pracovního postupu, vytvořte třídu, která implementuje <xref:System.Activities.IExecutionProperty> rozhraní a implementuje členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c960-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="5c960-113">Tyto členy poskytují spuštění vlastnost s možností správně nastavit a strhnout místní úložiště podprocesu během každého impulsu práce aktivity, která obsahuje vlastnost, včetně všech podřízených aktivit.</span><span class="sxs-lookup"><span data-stu-id="5c960-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="5c960-114">V tomto příkladu je vytvořen a, `ConsoleColorProperty` který nastaví `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="5c960-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 <span data-ttu-id="5c960-115">Autoři aktivity můžete použít tuto vlastnost registrací v přepsání spuštění aktivity.</span><span class="sxs-lookup"><span data-stu-id="5c960-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="5c960-116">V tomto příkladu je `ConsoleColorScope` definována `ConsoleColorProperty` aktivita, která <xref:System.Activities.NativeActivityContext.Properties%2A> registruje <xref:System.Activities.NativeActivityContext>přidáním do kolekce aktuální .</span><span class="sxs-lookup"><span data-stu-id="5c960-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="5c960-117">Když tělo aktivity spustí puls práce, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> volá se metoda vlastnosti a po dokončení pulzu práce <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> se nazývá.</span><span class="sxs-lookup"><span data-stu-id="5c960-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="5c960-118">V tomto příkladu je vytvořen <xref:System.Activities.Statements.Parallel> pracovní postup, který používá aktivitu se třemi větvemi.</span><span class="sxs-lookup"><span data-stu-id="5c960-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="5c960-119">První dvě větve používají `ConsoleColorScope` aktivitu a třetí větev nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="5c960-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="5c960-120">Všechny tři větve <xref:System.Activities.Statements.WriteLine> obsahují dvě <xref:System.Activities.Statements.Delay> aktivity a aktivitu.</span><span class="sxs-lookup"><span data-stu-id="5c960-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="5c960-121">Při <xref:System.Activities.Statements.Parallel> provádění aktivity aktivity, které jsou obsaženy v větvích provést proloženým způsobem, ale jako každá `ConsoleColorProperty`podřízená aktivita provede správnou barvu konzoly je použita .</span><span class="sxs-lookup"><span data-stu-id="5c960-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="5c960-122">Při vyvolání pracovního postupu je do okna konzoly zapsán následující výstup.</span><span class="sxs-lookup"><span data-stu-id="5c960-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="5c960-123">Přestože není zobrazen v předchozím výstupu, každý řádek textu v okně konzoly se zobrazí v uvedené barvě.</span><span class="sxs-lookup"><span data-stu-id="5c960-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="5c960-124">Vlastnosti spuštění pracovního postupu mohou používat vlastní autoři aktivit a poskytují také <xref:System.ServiceModel.Activities.CorrelationScope> <xref:System.Activities.Statements.TransactionScope> mechanismus pro správu popisovače pro aktivity, jako jsou aktivity a.</span><span class="sxs-lookup"><span data-stu-id="5c960-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c960-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c960-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
