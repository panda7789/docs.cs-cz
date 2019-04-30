---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774109"
---
# <a name="bookmarks"></a><span data-ttu-id="5de65-102">Záložky</span><span class="sxs-lookup"><span data-stu-id="5de65-102">Bookmarks</span></span>
<span data-ttu-id="5de65-103">Záložky jsou mechanismus, který umožňuje aktivitu pasivně bez podržení do vlákna pracovního postupu počkat na vstup.</span><span class="sxs-lookup"><span data-stu-id="5de65-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="5de65-104">Pokud aktivita signalizuje, že se čeká na podnětem, může vytvořit záložku.</span><span class="sxs-lookup"><span data-stu-id="5de65-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="5de65-105">Tím je oznámeno modul runtime, že aktivity spuštění by neměl být považuje za dokončené i v případě aktuálně prováděné metody (které vytvořen <xref:System.Activities.Bookmark>) vrátí.</span><span class="sxs-lookup"><span data-stu-id="5de65-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="5de65-106">Základy (záložky)</span><span class="sxs-lookup"><span data-stu-id="5de65-106">Bookmark Basics</span></span>  
 <span data-ttu-id="5de65-107">A <xref:System.Activities.Bookmark> představuje bod při spuštění, které lze obnovit (a přes který vstup může doručit) v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5de65-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="5de65-108">Obvykle <xref:System.Activities.Bookmark> je přiřazen název a externí kód (hostitele nebo rozšíření) zodpovídá za obnovení záložky s relevantními daty.</span><span class="sxs-lookup"><span data-stu-id="5de65-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="5de65-109">Při <xref:System.Activities.Bookmark> obnoveno, plány modulu runtime pracovního postupu <xref:System.Activities.BookmarkCallback> delegáta, který byl přidružen, který <xref:System.Activities.Bookmark> v okamžiku svého vytvoření.</span><span class="sxs-lookup"><span data-stu-id="5de65-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="5de65-110">Zobrazily se možnosti záložek</span><span class="sxs-lookup"><span data-stu-id="5de65-110">Bookmark Options</span></span>  
 <span data-ttu-id="5de65-111"><xref:System.Activities.BookmarkOptions> Třída určuje typ <xref:System.Activities.Bookmark> vytváří.</span><span class="sxs-lookup"><span data-stu-id="5de65-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="5de65-112">Možné hodnoty bez vzájemně se vylučující <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, a <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="5de65-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="5de65-113">Použití <xref:System.Activities.BookmarkOptions.None>, výchozí, při vytváření <xref:System.Activities.Bookmark> , který má být obnoveno přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="5de65-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="5de65-114">Použití <xref:System.Activities.BookmarkOptions.MultipleResume> při vytváření <xref:System.Activities.Bookmark> , který lze obnovit více než jednou.</span><span class="sxs-lookup"><span data-stu-id="5de65-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="5de65-115">Použití <xref:System.Activities.BookmarkOptions.NonBlocking> při vytváření <xref:System.Activities.Bookmark> , který může nikdy být obnoveno.</span><span class="sxs-lookup"><span data-stu-id="5de65-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="5de65-116">Na rozdíl od záložky vytvořené pomocí výchozí <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> záložky nezabrání aktivitu dokončení.</span><span class="sxs-lookup"><span data-stu-id="5de65-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="5de65-117">Obnovení (záložky)</span><span class="sxs-lookup"><span data-stu-id="5de65-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="5de65-118">Záložky lze obnovit kódem mimo pracovní postup pomocí jedné z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> přetížení.</span><span class="sxs-lookup"><span data-stu-id="5de65-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="5de65-119">V tomto příkladu `ReadLine` vytvoření aktivity.</span><span class="sxs-lookup"><span data-stu-id="5de65-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="5de65-120">Při spuštění `ReadLine` aktivita vytvoří <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom počká <xref:System.Activities.Bookmark> obnovení.</span><span class="sxs-lookup"><span data-stu-id="5de65-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="5de65-121">Po obnovení, `ReadLine` aktivity přiřadí data, která byla předána s <xref:System.Activities.Bookmark> k jeho <xref:System.Activities.Activity%601.Result%2A> argument.</span><span class="sxs-lookup"><span data-stu-id="5de65-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),   
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling   
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext   
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="5de65-122">V tomto příkladu se vytvoří pracovní postup, který používá `ReadLine` aktivity získat uživatelské jméno a zobrazit je v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="5de65-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="5de65-123">Hostitelská aplikace provádí vlastní shromažďování vstupu a předává je do pracovního postupu pomocí obnovení <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="5de65-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="5de65-124">Když `ReadLine` provádění aktivity, vytvoří <xref:System.Activities.Bookmark> s názvem `UserName` a potom počká na záložku obnovení.</span><span class="sxs-lookup"><span data-stu-id="5de65-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="5de65-125">Hostitel shromažďuje požadovaná data a potom obnoví <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="5de65-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="5de65-126">Pracovní postup bude pokračovat, zobrazí název a potom dokončí.</span><span class="sxs-lookup"><span data-stu-id="5de65-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="5de65-127">Všimněte si, že se nevyžaduje s ohledem na záložku obnovení synchronizace kód.</span><span class="sxs-lookup"><span data-stu-id="5de65-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="5de65-128">A <xref:System.Activities.Bookmark> lze obnovit pouze při nečinnosti pracovního postupu, a pokud pracovní postup není nečinný, volání <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blokuje, dokud pracovního postupu změní nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="5de65-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="5de65-129">Obnovení výsledků (záložky)</span><span class="sxs-lookup"><span data-stu-id="5de65-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="5de65-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> Vrátí <xref:System.Activities.BookmarkResumptionResult> hodnoty výčtu lze označit výsledky žádost o obnovení záložku.</span><span class="sxs-lookup"><span data-stu-id="5de65-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="5de65-131">Je to možné návratové hodnoty <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, a <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="5de65-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="5de65-132">Hostitelé a rozšíření můžete tuto hodnotu určit, jak pokračovat dál.</span><span class="sxs-lookup"><span data-stu-id="5de65-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
