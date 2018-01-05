---
title: "Vlastnosti pracovního postupu provádění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c541ebf83babcbdbda86c5b6f3862727d49d8679
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="b63cf-102">Vlastnosti pracovního postupu provádění</span><span class="sxs-lookup"><span data-stu-id="b63cf-102">Workflow Execution Properties</span></span>
<span data-ttu-id="b63cf-103">Pomocí místní úložiště vláken (TLS) modul CLR udržuje kontextu spuštění pro každé vlákno.</span><span class="sxs-lookup"><span data-stu-id="b63cf-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="b63cf-104">Tento kontext spuštění řídí vlastnosti dobře známé vlákna například identity vláken vedlejším transakce a sadou kromě vlákno uživatelem definované vlastnosti jako aktuální oprávnění s názvem sloty.</span><span class="sxs-lookup"><span data-stu-id="b63cf-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="b63cf-105">Na rozdíl od přímo cílení na modulu CLR programů jsou programy pracovního postupu hierarchicky vymezená stromy aktivit, které se spouští v prostředí bez ohledu na vlákno.</span><span class="sxs-lookup"><span data-stu-id="b63cf-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="b63cf-106">To znamená, že standardních mechanismů TLS nelze použít přímo k určení, jaké kontext je v oboru pro daný pracovní položku.</span><span class="sxs-lookup"><span data-stu-id="b63cf-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="b63cf-107">Například dvě paralelních větvích provádění může používat jinou transakcí, ale Plánovač může interleave jejich spuštění ve stejném vlákně, CLR.</span><span class="sxs-lookup"><span data-stu-id="b63cf-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="b63cf-108">Pracovní postup provádění vlastnosti poskytují mechanismus k přidání konkrétních vlastností kontextu do prostředí aktivity.</span><span class="sxs-lookup"><span data-stu-id="b63cf-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="b63cf-109">To umožňuje aktivitu deklarovat, vlastnosti, které jsou v oboru pro jeho podstromu a také poskytuje háky pro nastavení a zrušení TLS správně vzájemnou spolupráci s objekty CLR.</span><span class="sxs-lookup"><span data-stu-id="b63cf-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="b63cf-110">Vytvoření a použití vlastností pracovního postupu provádění</span><span class="sxs-lookup"><span data-stu-id="b63cf-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="b63cf-111">Pracovní postup provádění vlastnosti obvykle implementovat <xref:System.Activities.IExecutionProperty> rozhraní, i když vlastnosti, které jsou zaměřené na zasílání zpráv může implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo.</span><span class="sxs-lookup"><span data-stu-id="b63cf-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="b63cf-112">Pokud chcete vytvořit vlastnost spuštění pracovního postupu, vytvořte třídu, která implementuje <xref:System.Activities.IExecutionProperty> rozhraní a implementovat členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="b63cf-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="b63cf-113">Tito členové poskytnout vlastnost provádění příležitost správně nastavit a přerušit lokální úložiště vláken při každé pulse pracovní aktivity, která obsahuje vlastnosti, včetně žádné podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b63cf-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="b63cf-114">V tomto příkladu `ConsoleColorProperty` této sady je vytvořena `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="b63cf-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b63cf-115">Následující příklad kódu v tomto tématu podle [provádění vlastnosti](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="b63cf-115">The following example code in this topic is based on the [Execution Properties](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) sample.</span></span>  
  
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
  
 <span data-ttu-id="b63cf-116">Autoři aktivitu můžete použít tuto vlastnost tak, že zaregistrujete v aktivity spustit přepsání.</span><span class="sxs-lookup"><span data-stu-id="b63cf-116">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="b63cf-117">V tomto příkladu `ConsoleColorScope` aktivity je definován, se zaregistruje `ConsoleColorProperty` přidáním jeho <xref:System.Activities.NativeActivityContext.Properties%2A> kolekce aktuální <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="b63cf-117">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="b63cf-118">Při spuštění aktivity textu pulse práce, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> je volána metoda vlastnosti a po dokončení, pulse práce <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="b63cf-118">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="b63cf-119">V tomto příkladu se vytvoří pracovní postup používající <xref:System.Activities.Statements.Parallel> aktivitu tři větve.</span><span class="sxs-lookup"><span data-stu-id="b63cf-119">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="b63cf-120">Použít první dvě pobočky `ConsoleColorScope` aktivity a třetí větev neexistuje.</span><span class="sxs-lookup"><span data-stu-id="b63cf-120">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="b63cf-121">Všechny tři větve obsahovat dvě <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.Delay> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b63cf-121">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="b63cf-122">Když <xref:System.Activities.Statements.Parallel> provádí aktivity, aktivity, které jsou obsaženy v větve provést prokládaná způsobem, ale jako provádí každou aktivitu podřízené barvu konzoly správné použití je `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="b63cf-122">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="b63cf-123">Po vyvolání pracovní postup je následující výstup zapsán do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="b63cf-123">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="b63cf-124">I když ho není zobrazené ve výstupu předchozí, každý řádek textu v okně konzoly se zobrazí v barvu uvedené.</span><span class="sxs-lookup"><span data-stu-id="b63cf-124">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="b63cf-125">Vlastnosti pracovního postupu provádění lze použít autory vlastní aktivitu, a také poskytují mechanismus pro Správa popisovačů pro aktivity, jako <xref:System.ServiceModel.Activities.CorrelationScope> a <xref:System.Activities.Statements.TransactionScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b63cf-125">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63cf-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b63cf-126">See Also</span></span>  
 <xref:System.Activities.IExecutionProperty>  
 <xref:System.Activities.IPropertyRegistrationCallback>  
 <xref:System.Activities.RegistrationContext>
