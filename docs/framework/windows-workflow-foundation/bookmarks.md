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
# <a name="bookmarks"></a>Záložky
Záložky jsou mechanismus, který umožňuje aktivitě dočkat na vstup bez držení do vlákna pracovního postupu. Když aktivita signalizuje, že čeká na podnět, může vytvořit záložku. To znamená, že spuštění aktivity by nemělo být považováno za dokončené, a to i v případě, že právě prováděná <xref:System.Activities.Bookmark>metoda (která vytvořila) vrátí.  
  
## <a name="bookmark-basics"></a>Základy záložek  
 <xref:System.Activities.Bookmark> Představuje bod, ve kterém může být provádění obnoveno (a přes který je možné doručit vstup) v rámci instance pracovního postupu. <xref:System.Activities.Bookmark> Obvykle je předána název a externí (hostitelský nebo příponový) kód, který je zodpovědný za obnovení záložky s relevantními daty. Když je obnovený, modul runtime pracovního postupu <xref:System.Activities.BookmarkCallback> naplánuje delegáta, který byl <xref:System.Activities.Bookmark> přidružen k danému okamžiku vytvoření. <xref:System.Activities.Bookmark>  
  
## <a name="bookmark-options"></a>Možnosti záložky  
 Třída určuje typ, který se má vytvořit. <xref:System.Activities.Bookmark> <xref:System.Activities.BookmarkOptions> Možné nevzájemně vyloučené hodnoty jsou <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>a <xref:System.Activities.BookmarkOptions.NonBlocking>. Použijte <xref:System.Activities.BookmarkOptions.None>výchozí hodnotu při <xref:System.Activities.Bookmark> vytváření, která má být obnovena přesně jednou. Použijte <xref:System.Activities.BookmarkOptions.MultipleResume> při<xref:System.Activities.Bookmark> vytváření, která se dá obnovit víckrát. Použijte <xref:System.Activities.BookmarkOptions.NonBlocking> při<xref:System.Activities.Bookmark> vytváření, která nemusí být nikdy obnovena. Na rozdíl od záložek vytvořených pomocí <xref:System.Activities.BookmarkOptions>výchozího <xref:System.Activities.BookmarkOptions.NonBlocking> nastavení záložky nebrání dokončení aktivity.  
  
## <a name="bookmark-resumption"></a>Pokračování záložky  
 Záložky lze obnovit pomocí kódu mimo pracovní postup pomocí jednoho z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> přetížení. V tomto příkladu `ReadLine` je vytvořena aktivita. Po spuštění `ReadLine` aktivita <xref:System.Activities.Bookmark>vytvoří, zaregistruje zpětné volání a <xref:System.Activities.Bookmark> potom počká, až se obnoví. Když je obnovena, `ReadLine` Aktivita přiřadí data, která byla předána <xref:System.Activities.Bookmark> do svého <xref:System.Activities.Activity%601.Result%2A> argumentu.  
  
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
  
 V tomto příkladu je vytvořen pracovní postup, který používá `ReadLine` aktivitu ke shromáždění jména uživatele a jeho zobrazení v okně konzoly. Hostitelská aplikace provede skutečnou práci při shromažďování vstupu a předá ji do pracovního postupu obnovením <xref:System.Activities.Bookmark>.  
  
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
  
 Když se <xref:System.Activities.Bookmark> aktivita spustí, vytvoří se pojmenovaná `UserName` a potom počká, až se záložka obnoví. `ReadLine` Hostitel shromáždí požadovaná data a pak obnoví <xref:System.Activities.Bookmark>. Pracovní postup obnoví, zobrazí název a pak dokončí. Všimněte si, že v souvislosti s pokračováním záložky není vyžadován žádný synchronizační kód. Může být obnovena pouze v případě, že je pracovní postup nečinný a pracovní postup není nečinný, <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> volání zablokuje, dokud pracovní postup nezůstane nečinný. <xref:System.Activities.Bookmark>  
  
## <a name="bookmark-resumption-result"></a>Výsledek pokračování záložky  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>Vrátí hodnotu <xref:System.Activities.BookmarkResumptionResult> výčtu, která určuje výsledky žádosti o obnovení záložky. Možné vrácené hodnoty jsou <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>a <xref:System.Activities.BookmarkResumptionResult.NotFound>. Hostitelé a rozšíření mohou tuto hodnotu použít k určení, jak pokračovat.
