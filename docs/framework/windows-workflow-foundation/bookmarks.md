---
title: Záložky - WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: c5bd8130ee623599e80014777baf92986c3b6969
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183013"
---
# <a name="bookmarks"></a><span data-ttu-id="68a82-102">Záložky</span><span class="sxs-lookup"><span data-stu-id="68a82-102">Bookmarks</span></span>
<span data-ttu-id="68a82-103">Záložky jsou mechanismus, který umožňuje aktivitě pasivně čekat na vstup bez držení na vlákno pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="68a82-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="68a82-104">Když aktivita signalizuje, že čeká na podnět, může vytvořit záložku.</span><span class="sxs-lookup"><span data-stu-id="68a82-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="68a82-105">To znamená, že modul runtime, že provádění aktivity by neměly být považovány <xref:System.Activities.Bookmark>za úplné i v případě, že aktuálně spuštěná metoda (která vytvořila ) vrátí.</span><span class="sxs-lookup"><span data-stu-id="68a82-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="68a82-106">Základy záložek</span><span class="sxs-lookup"><span data-stu-id="68a82-106">Bookmark Basics</span></span>  
 <span data-ttu-id="68a82-107">A <xref:System.Activities.Bookmark> představuje bod, ve kterém lze obnovit provádění (a jehož prostřednictvím může být doručen vstup) v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="68a82-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="68a82-108">Obvykle <xref:System.Activities.Bookmark> je uveden název a externí (hostitelský nebo rozšiřující) kód je zodpovědný za obnovení záložky s příslušnými daty.</span><span class="sxs-lookup"><span data-stu-id="68a82-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="68a82-109"><xref:System.Activities.Bookmark> Při obnovení, za běhu pracovního postupu <xref:System.Activities.BookmarkCallback> naplánuje delegáta, který byl přidružen, že <xref:System.Activities.Bookmark> v době jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="68a82-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="68a82-110">Možnosti záložek</span><span class="sxs-lookup"><span data-stu-id="68a82-110">Bookmark Options</span></span>  
 <span data-ttu-id="68a82-111">Třída <xref:System.Activities.BookmarkOptions> určuje typ vytvářeného. <xref:System.Activities.Bookmark></span><span class="sxs-lookup"><span data-stu-id="68a82-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="68a82-112">Možné hodnoty, které se <xref:System.Activities.BookmarkOptions.None>vzájemně <xref:System.Activities.BookmarkOptions.MultipleResume>nevylučují, jsou , a <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="68a82-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="68a82-113">Použití <xref:System.Activities.BookmarkOptions.None>, výchozí, při <xref:System.Activities.Bookmark> vytváření, který se očekává, že bude obnovena přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="68a82-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="68a82-114">Použijte <xref:System.Activities.BookmarkOptions.MultipleResume> při <xref:System.Activities.Bookmark> vytváření, které lze obnovit vícekrát.</span><span class="sxs-lookup"><span data-stu-id="68a82-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="68a82-115">Použijte <xref:System.Activities.BookmarkOptions.NonBlocking> při <xref:System.Activities.Bookmark> vytváření, které nemusí být nikdy obnovena.</span><span class="sxs-lookup"><span data-stu-id="68a82-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="68a82-116">Na rozdíl od záložek <xref:System.Activities.BookmarkOptions.NonBlocking> vytvořených pomocí výchozího nastavení <xref:System.Activities.BookmarkOptions>záložky nebrání dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="68a82-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="68a82-117">Obnovení záložky</span><span class="sxs-lookup"><span data-stu-id="68a82-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="68a82-118">Záložky lze obnovit kódmimo pracovní postup pomocí <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> jednoho z přetížení.</span><span class="sxs-lookup"><span data-stu-id="68a82-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="68a82-119">V tomto příkladu je vytvořena aktivita. `ReadLine`</span><span class="sxs-lookup"><span data-stu-id="68a82-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="68a82-120">Při spuštění aktivity `ReadLine` vytvoří <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom <xref:System.Activities.Bookmark> čeká na obnovení.</span><span class="sxs-lookup"><span data-stu-id="68a82-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="68a82-121">Po obnovení aktivita `ReadLine` přiřadí data, která byla <xref:System.Activities.Bookmark> předána <xref:System.Activities.Activity%601.Result%2A> s jeho argument.</span><span class="sxs-lookup"><span data-stu-id="68a82-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="68a82-122">V tomto příkladu je vytvořen `ReadLine` pracovní postup, který používá aktivitu ke shromáždění jména uživatele a jeho zobrazení v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="68a82-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="68a82-123">Hostitelská aplikace provádí skutečnou práci shromažďování vstupu a předá jej <xref:System.Activities.Bookmark>pracovnímu postupu obnovením .</span><span class="sxs-lookup"><span data-stu-id="68a82-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="68a82-124">Když `ReadLine` je aktivita spuštěna, <xref:System.Activities.Bookmark> `UserName` vytvoří pojmenovaný a pak čeká na záložku, která má být obnovena.</span><span class="sxs-lookup"><span data-stu-id="68a82-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="68a82-125">Hostitel shromažďuje požadovaná data a potom <xref:System.Activities.Bookmark>obnoví .</span><span class="sxs-lookup"><span data-stu-id="68a82-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="68a82-126">Pracovní postup se obnoví, zobrazí název a potom se dokončí.</span><span class="sxs-lookup"><span data-stu-id="68a82-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="68a82-127">Všimněte si, že žádný kód synchronizace je vyžadován s ohledem na obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="68a82-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="68a82-128">A <xref:System.Activities.Bookmark> lze obnovit pouze v případě, že pracovní postup je nečinný <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> a pokud pracovní postup není nečinný, volání bloky, dokud se pracovní postup stane nečinný.</span><span class="sxs-lookup"><span data-stu-id="68a82-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="68a82-129">Výsledek obnovení záložky</span><span class="sxs-lookup"><span data-stu-id="68a82-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="68a82-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>vrátí <xref:System.Activities.BookmarkResumptionResult> hodnotu výčtu označující výsledky požadavku na obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="68a82-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="68a82-131">Možné vrácené <xref:System.Activities.BookmarkResumptionResult.Success>hodnoty <xref:System.Activities.BookmarkResumptionResult.NotReady>jsou <xref:System.Activities.BookmarkResumptionResult.NotFound>, a .</span><span class="sxs-lookup"><span data-stu-id="68a82-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="68a82-132">Hostitelé a rozšíření můžete tuto hodnotu použít k určení, jak postupovat.</span><span class="sxs-lookup"><span data-stu-id="68a82-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
