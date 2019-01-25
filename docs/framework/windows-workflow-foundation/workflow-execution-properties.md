---
title: Vlastnosti spuštění pracovního postupu
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 96f5057986e256f485f60221d1c6ad3d2494be55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566720"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="34077-102">Vlastnosti spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="34077-102">Workflow Execution Properties</span></span>
<span data-ttu-id="34077-103">Pomocí úložiště thread local (TLS) CLR udržuje kontext spuštění pro každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="34077-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="34077-104">Tento kontext spuštění se řídí vlákno dobře známé vlastnosti, jako je identitu vlákna okolí transakce a sadou kromě vlákna uživatelem definované vlastnosti, jako je aktuální oprávnění s názvem sloty.</span><span class="sxs-lookup"><span data-stu-id="34077-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="34077-105">Na rozdíl od programy přímo cílí na modulu CLR pracovní postup programy jsou hierarchicky vymezené stromů aktivit, které jsou spuštěny v prostředí bez ohledu na vlákno.</span><span class="sxs-lookup"><span data-stu-id="34077-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="34077-106">Z toho vyplývá, že standardních mechanismů protokolu TLS nelze přímo použít k určení, jaké kontext je v oboru pro daný pracovní položky.</span><span class="sxs-lookup"><span data-stu-id="34077-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="34077-107">Například dva paralelních větvích provádění použít jiné transakce, ale Plánovač může prokládání jejich spuštění ve stejném vlákně modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="34077-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="34077-108">Vlastnosti spuštění pracovního postupu poskytují mechanismus pro přidání kontextu specifické vlastnosti aktivity prostředí.</span><span class="sxs-lookup"><span data-stu-id="34077-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="34077-109">To umožňuje aktivitu, chcete-li deklarovat vlastnosti, které jsou v oboru pro jeho podstromu a také poskytuje zachytávání pro nastavení a opětné TLS správně zajistit vzájemnou funkční spolupráci s objekty CLR.</span><span class="sxs-lookup"><span data-stu-id="34077-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="34077-110">Vytváření a používání běhové vlastnosti pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="34077-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="34077-111">Vlastnosti spuštění pracovního postupu obvykle implementují <xref:System.Activities.IExecutionProperty> rozhraní, když vlastnosti, zaměřuje na zasílání zpráv může implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo.</span><span class="sxs-lookup"><span data-stu-id="34077-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="34077-112">Pro vytvoření vlastnosti spuštění pracovního postupu, vytvořte třídu, která implementuje <xref:System.Activities.IExecutionProperty> rozhraní a implementovat členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="34077-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="34077-113">Tyto členy, poskytne vlastnost spuštění příležitost správně nastavit a začít odstraňovat úložiště thread local během každé pulse pracovní aktivity, která obsahuje vlastnosti, včetně všechny podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="34077-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="34077-114">V tomto příkladu `ConsoleColorProperty` vytvoření této sady `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="34077-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="34077-115">Aktivita autoři tuto vlastnost můžete použít tak, že zaregistrujete ho v aktivity spuštění přepsat.</span><span class="sxs-lookup"><span data-stu-id="34077-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="34077-116">V tomto příkladu `ConsoleColorScope` aktivity je definován, která se registruje `ConsoleColorProperty` tak, že ji přidáte <xref:System.Activities.NativeActivityContext.Properties%2A> kolekce aktuálního <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="34077-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="34077-117">Při spuštění aktivity tělo pulse práce, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> volání metody, vlastnosti a po dokončení, pulse práce <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="34077-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="34077-118">V tomto příkladu se vytvoří pracovní postup, který používá <xref:System.Activities.Statements.Parallel> aktivity tři větví.</span><span class="sxs-lookup"><span data-stu-id="34077-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="34077-119">Používat nejdřív dvě větve `ConsoleColorScope` aktivity a třetí větve tak není.</span><span class="sxs-lookup"><span data-stu-id="34077-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="34077-120">Všechny tři větve obsahují dva <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.Delay> aktivity.</span><span class="sxs-lookup"><span data-stu-id="34077-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="34077-121">Když <xref:System.Activities.Statements.Parallel> aktivity spustí, aktivity, které jsou obsaženy v větve provést prokládané způsobem, ale protože každá podřízená aktivita spustí barvu správné konzole použití `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="34077-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="34077-122">Když uživatel vyvolá pracovní postup, následující výstup je zapsán do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="34077-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="34077-123">I když není zobrazený ve výstupu předchozí, jednotlivé řádky textu v okně konzoly se zobrazí v označeném barvu.</span><span class="sxs-lookup"><span data-stu-id="34077-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="34077-124">Vlastnosti spuštění pracovního postupu je možné autory vlastní aktivitu, a také poskytují mechanismus pro Správa popisovačů pro aktivity, jako <xref:System.ServiceModel.Activities.CorrelationScope> a <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="34077-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34077-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34077-125">See also</span></span>
- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
