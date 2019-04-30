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
# <a name="bookmarks"></a>Záložky
Záložky jsou mechanismus, který umožňuje aktivitu pasivně bez podržení do vlákna pracovního postupu počkat na vstup. Pokud aktivita signalizuje, že se čeká na podnětem, může vytvořit záložku. Tím je oznámeno modul runtime, že aktivity spuštění by neměl být považuje za dokončené i v případě aktuálně prováděné metody (které vytvořen <xref:System.Activities.Bookmark>) vrátí.  
  
## <a name="bookmark-basics"></a>Základy (záložky)  
 A <xref:System.Activities.Bookmark> představuje bod při spuštění, které lze obnovit (a přes který vstup může doručit) v rámci instance pracovního postupu. Obvykle <xref:System.Activities.Bookmark> je přiřazen název a externí kód (hostitele nebo rozšíření) zodpovídá za obnovení záložky s relevantními daty. Při <xref:System.Activities.Bookmark> obnoveno, plány modulu runtime pracovního postupu <xref:System.Activities.BookmarkCallback> delegáta, který byl přidružen, který <xref:System.Activities.Bookmark> v okamžiku svého vytvoření.  
  
## <a name="bookmark-options"></a>Zobrazily se možnosti záložek  
 <xref:System.Activities.BookmarkOptions> Třída určuje typ <xref:System.Activities.Bookmark> vytváří. Možné hodnoty bez vzájemně se vylučující <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, a <xref:System.Activities.BookmarkOptions.NonBlocking>. Použití <xref:System.Activities.BookmarkOptions.None>, výchozí, při vytváření <xref:System.Activities.Bookmark> , který má být obnoveno přesně jednou. Použití <xref:System.Activities.BookmarkOptions.MultipleResume> při vytváření <xref:System.Activities.Bookmark> , který lze obnovit více než jednou. Použití <xref:System.Activities.BookmarkOptions.NonBlocking> při vytváření <xref:System.Activities.Bookmark> , který může nikdy být obnoveno. Na rozdíl od záložky vytvořené pomocí výchozí <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> záložky nezabrání aktivitu dokončení.  
  
## <a name="bookmark-resumption"></a>Obnovení (záložky)  
 Záložky lze obnovit kódem mimo pracovní postup pomocí jedné z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> přetížení. V tomto příkladu `ReadLine` vytvoření aktivity. Při spuštění `ReadLine` aktivita vytvoří <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom počká <xref:System.Activities.Bookmark> obnovení. Po obnovení, `ReadLine` aktivity přiřadí data, která byla předána s <xref:System.Activities.Bookmark> k jeho <xref:System.Activities.Activity%601.Result%2A> argument.  
  
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
  
 V tomto příkladu se vytvoří pracovní postup, který používá `ReadLine` aktivity získat uživatelské jméno a zobrazit je v okně konzoly. Hostitelská aplikace provádí vlastní shromažďování vstupu a předává je do pracovního postupu pomocí obnovení <xref:System.Activities.Bookmark>.  
  
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
  
 Když `ReadLine` provádění aktivity, vytvoří <xref:System.Activities.Bookmark> s názvem `UserName` a potom počká na záložku obnovení. Hostitel shromažďuje požadovaná data a potom obnoví <xref:System.Activities.Bookmark>. Pracovní postup bude pokračovat, zobrazí název a potom dokončí. Všimněte si, že se nevyžaduje s ohledem na záložku obnovení synchronizace kód. A <xref:System.Activities.Bookmark> lze obnovit pouze při nečinnosti pracovního postupu, a pokud pracovní postup není nečinný, volání <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blokuje, dokud pracovního postupu změní nečinnosti.  
  
## <a name="bookmark-resumption-result"></a>Obnovení výsledků (záložky)  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> Vrátí <xref:System.Activities.BookmarkResumptionResult> hodnoty výčtu lze označit výsledky žádost o obnovení záložku. Je to možné návratové hodnoty <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, a <xref:System.Activities.BookmarkResumptionResult.NotFound>. Hostitelé a rozšíření můžete tuto hodnotu určit, jak pokračovat dál.
