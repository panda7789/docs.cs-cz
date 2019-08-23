---
title: Vlastnosti spuštění pracovního postupu
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 61bf53d9cab3ddefae3709958bd1e445fb4e69dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913612"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="88f77-102">Vlastnosti spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="88f77-102">Workflow Execution Properties</span></span>
<span data-ttu-id="88f77-103">Pomocí protokolu thread local Storage (TLS) udržuje modul CLR kontext spuštění pro každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="88f77-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="88f77-104">Tento kontext spuštění řídí dobře známé vlastnosti vlákna, jako je například identita vlákna, ambientní transakce a současná sada oprávnění kromě uživatelsky definovaných vlastností vlákna, jako jsou pojmenované sloty.</span><span class="sxs-lookup"><span data-stu-id="88f77-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="88f77-105">Na rozdíl od programů přímo cílících na CLR jsou programy pracovních postupů hierarchicky vymezené stromy aktivit, které se spouštějí v prostředí s nezávislá vláknem.</span><span class="sxs-lookup"><span data-stu-id="88f77-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="88f77-106">To znamená, že standardní mechanismy TLS nelze přímo použít k určení kontextu, který je v rozsahu pro danou pracovní položku.</span><span class="sxs-lookup"><span data-stu-id="88f77-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="88f77-107">Například dvě paralelní větve provádění mohou používat různé transakce, přesto může Plánovač prokládat jejich spuštění ve stejném vlákně CLR.</span><span class="sxs-lookup"><span data-stu-id="88f77-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="88f77-108">Vlastnosti spuštění pracovního postupu poskytují mechanismus pro přidání specifických vlastností kontextu do prostředí aktivity.</span><span class="sxs-lookup"><span data-stu-id="88f77-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="88f77-109">To umožňuje aktivitě deklarovat, které vlastnosti jsou v oboru pro jeho podstromy, a také poskytuje zapojování pro nastavení a odtržení protokolu TLS pro správné spolupráci s objekty CLR.</span><span class="sxs-lookup"><span data-stu-id="88f77-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="88f77-110">Vytváření a používání vlastností spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="88f77-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="88f77-111">Vlastnosti spuštění pracovního postupu obvykle implementují <xref:System.Activities.IExecutionProperty> rozhraní, ale vlastnosti zaměřené na zasílání zpráv mohou implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo toho.</span><span class="sxs-lookup"><span data-stu-id="88f77-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="88f77-112">Chcete-li vytvořit vlastnost spuštění pracovního postupu, vytvořte třídu, která <xref:System.Activities.IExecutionProperty> implementuje rozhraní a implementuje členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="88f77-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="88f77-113">Tito členové poskytují vlastnost spuštění s příležitostí ke správnému nastavení a odtrhnout thread local úložiště během každé pulsace práce aktivity obsahující vlastnost, včetně všech podřízených aktivit.</span><span class="sxs-lookup"><span data-stu-id="88f77-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="88f77-114">V tomto příkladu je vytvořena `ConsoleColorProperty` sada, která `Console.ForegroundColor`nastavuje.</span><span class="sxs-lookup"><span data-stu-id="88f77-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="88f77-115">Autoři aktivity mohou tuto vlastnost používat tak, že ji zaregistrují v přepsání Execute aktivity.</span><span class="sxs-lookup"><span data-stu-id="88f77-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="88f77-116">V tomto příkladu `ConsoleColorScope` je definována aktivita, která `ConsoleColorProperty` registruje přidáním do <xref:System.Activities.NativeActivityContext.Properties%2A> kolekce aktuálního <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="88f77-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="88f77-117">Když tělo aktivity začne pracovat na Pulse, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> je volána metoda vlastnosti a když je Pulse práce dokončena <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> , je volána.</span><span class="sxs-lookup"><span data-stu-id="88f77-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="88f77-118">V tomto příkladu se vytvoří pracovní postup, který používá <xref:System.Activities.Statements.Parallel> aktivitu se třemi větvemi.</span><span class="sxs-lookup"><span data-stu-id="88f77-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="88f77-119">První dvě větve používají `ConsoleColorScope` aktivitu a třetí větev ne.</span><span class="sxs-lookup"><span data-stu-id="88f77-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="88f77-120">Všechny tři větve obsahují dvě <xref:System.Activities.Statements.WriteLine> aktivity <xref:System.Activities.Statements.Delay> a aktivitu.</span><span class="sxs-lookup"><span data-stu-id="88f77-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="88f77-121">Když se <xref:System.Activities.Statements.Parallel> aktivita spustí, aktivity, které jsou obsaženy v větvích, se spustí způsobem prokládaným způsobem, ale každá podřízená aktivita spustí správnou barvu `ConsoleColorProperty`konzoly, kterou používá.</span><span class="sxs-lookup"><span data-stu-id="88f77-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="88f77-122">Po vyvolání pracovního postupu se do okna konzoly zapíše následující výstup.</span><span class="sxs-lookup"><span data-stu-id="88f77-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="88f77-123">I když není zobrazený v předchozím výstupu, zobrazí se v označené barvě každý řádek textu v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="88f77-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="88f77-124">Vlastnosti spuštění pracovního postupu můžou použít vlastní autoři aktivity a také poskytují mechanismus pro správu pro aktivity, jako jsou <xref:System.ServiceModel.Activities.CorrelationScope> aktivity a. <xref:System.Activities.Statements.TransactionScope></span><span class="sxs-lookup"><span data-stu-id="88f77-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f77-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88f77-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
