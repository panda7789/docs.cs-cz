---
title: Záložky – WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: a15a28cc39a4227765c238a6f2b86c72197f1a39
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868919"
---
# <a name="bookmarks"></a><span data-ttu-id="c1503-102">Záložky</span><span class="sxs-lookup"><span data-stu-id="c1503-102">Bookmarks</span></span>
<span data-ttu-id="c1503-103">Záložky jsou mechanismus, který umožňuje aktivitě dočkat na vstup bez držení do vlákna pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c1503-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="c1503-104">Když aktivita signalizuje, že čeká na podnět, může vytvořit záložku.</span><span class="sxs-lookup"><span data-stu-id="c1503-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="c1503-105">To znamená, že spuštění aktivity by nemělo být považováno za dokončené, a to i v případě, že právě prováděná <xref:System.Activities.Bookmark>metoda (která vytvořila) vrátí.</span><span class="sxs-lookup"><span data-stu-id="c1503-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="c1503-106">Základy záložek</span><span class="sxs-lookup"><span data-stu-id="c1503-106">Bookmark Basics</span></span>  
 <span data-ttu-id="c1503-107"><xref:System.Activities.Bookmark> Představuje bod, ve kterém může být provádění obnoveno (a přes který je možné doručit vstup) v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c1503-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="c1503-108"><xref:System.Activities.Bookmark> Obvykle je předána název a externí (hostitelský nebo příponový) kód, který je zodpovědný za obnovení záložky s relevantními daty.</span><span class="sxs-lookup"><span data-stu-id="c1503-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="c1503-109">Když je obnovený, modul runtime pracovního postupu <xref:System.Activities.BookmarkCallback> naplánuje delegáta, který byl <xref:System.Activities.Bookmark> přidružen k danému okamžiku vytvoření. <xref:System.Activities.Bookmark></span><span class="sxs-lookup"><span data-stu-id="c1503-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="c1503-110">Možnosti záložky</span><span class="sxs-lookup"><span data-stu-id="c1503-110">Bookmark Options</span></span>  
 <span data-ttu-id="c1503-111">Třída určuje typ, který se má vytvořit. <xref:System.Activities.Bookmark> <xref:System.Activities.BookmarkOptions></span><span class="sxs-lookup"><span data-stu-id="c1503-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="c1503-112">Možné nevzájemně vyloučené hodnoty jsou <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>a <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="c1503-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="c1503-113">Použijte <xref:System.Activities.BookmarkOptions.None>výchozí hodnotu při <xref:System.Activities.Bookmark> vytváření, která má být obnovena přesně jednou.</span><span class="sxs-lookup"><span data-stu-id="c1503-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="c1503-114">Použijte <xref:System.Activities.BookmarkOptions.MultipleResume> při<xref:System.Activities.Bookmark> vytváření, která se dá obnovit víckrát.</span><span class="sxs-lookup"><span data-stu-id="c1503-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="c1503-115">Použijte <xref:System.Activities.BookmarkOptions.NonBlocking> při<xref:System.Activities.Bookmark> vytváření, která nemusí být nikdy obnovena.</span><span class="sxs-lookup"><span data-stu-id="c1503-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="c1503-116">Na rozdíl od záložek vytvořených pomocí <xref:System.Activities.BookmarkOptions>výchozího <xref:System.Activities.BookmarkOptions.NonBlocking> nastavení záložky nebrání dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="c1503-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="c1503-117">Pokračování záložky</span><span class="sxs-lookup"><span data-stu-id="c1503-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="c1503-118">Záložky lze obnovit pomocí kódu mimo pracovní postup pomocí jednoho z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> přetížení.</span><span class="sxs-lookup"><span data-stu-id="c1503-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="c1503-119">V tomto příkladu `ReadLine` je vytvořena aktivita.</span><span class="sxs-lookup"><span data-stu-id="c1503-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="c1503-120">Po spuštění `ReadLine` aktivita <xref:System.Activities.Bookmark>vytvoří, zaregistruje zpětné volání a <xref:System.Activities.Bookmark> potom počká, až se obnoví.</span><span class="sxs-lookup"><span data-stu-id="c1503-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="c1503-121">Když je obnovena, `ReadLine` Aktivita přiřadí data, která byla předána <xref:System.Activities.Bookmark> do svého <xref:System.Activities.Activity%601.Result%2A> argumentu.</span><span class="sxs-lookup"><span data-stu-id="c1503-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="c1503-122">V tomto příkladu je vytvořen pracovní postup, který používá `ReadLine` aktivitu ke shromáždění jména uživatele a jeho zobrazení v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c1503-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="c1503-123">Hostitelská aplikace provede skutečnou práci při shromažďování vstupu a předá ji do pracovního postupu obnovením <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="c1503-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="c1503-124">Když se <xref:System.Activities.Bookmark> aktivita spustí, vytvoří se pojmenovaná `UserName` a potom počká, až se záložka obnoví. `ReadLine`</span><span class="sxs-lookup"><span data-stu-id="c1503-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="c1503-125">Hostitel shromáždí požadovaná data a pak obnoví <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="c1503-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="c1503-126">Pracovní postup obnoví, zobrazí název a pak dokončí.</span><span class="sxs-lookup"><span data-stu-id="c1503-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="c1503-127">Všimněte si, že v souvislosti s pokračováním záložky není vyžadován žádný synchronizační kód.</span><span class="sxs-lookup"><span data-stu-id="c1503-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="c1503-128">Může být obnovena pouze v případě, že je pracovní postup nečinný a pracovní postup není nečinný, <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> volání zablokuje, dokud pracovní postup nezůstane nečinný. <xref:System.Activities.Bookmark></span><span class="sxs-lookup"><span data-stu-id="c1503-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="c1503-129">Výsledek pokračování záložky</span><span class="sxs-lookup"><span data-stu-id="c1503-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="c1503-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>Vrátí hodnotu <xref:System.Activities.BookmarkResumptionResult> výčtu, která určuje výsledky žádosti o obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="c1503-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="c1503-131">Možné vrácené hodnoty jsou <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>a <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="c1503-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="c1503-132">Hostitelé a rozšíření mohou tuto hodnotu použít k určení, jak pokračovat.</span><span class="sxs-lookup"><span data-stu-id="c1503-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
