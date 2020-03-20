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
# <a name="bookmarks"></a>Záložky
Záložky jsou mechanismus, který umožňuje aktivitě pasivně čekat na vstup bez držení na vlákno pracovního postupu. Když aktivita signalizuje, že čeká na podnět, může vytvořit záložku. To znamená, že modul runtime, že provádění aktivity by neměly být považovány <xref:System.Activities.Bookmark>za úplné i v případě, že aktuálně spuštěná metoda (která vytvořila ) vrátí.  
  
## <a name="bookmark-basics"></a>Základy záložek  
 A <xref:System.Activities.Bookmark> představuje bod, ve kterém lze obnovit provádění (a jehož prostřednictvím může být doručen vstup) v rámci instance pracovního postupu. Obvykle <xref:System.Activities.Bookmark> je uveden název a externí (hostitelský nebo rozšiřující) kód je zodpovědný za obnovení záložky s příslušnými daty. <xref:System.Activities.Bookmark> Při obnovení, za běhu pracovního postupu <xref:System.Activities.BookmarkCallback> naplánuje delegáta, který byl přidružen, že <xref:System.Activities.Bookmark> v době jeho vytvoření.  
  
## <a name="bookmark-options"></a>Možnosti záložek  
 Třída <xref:System.Activities.BookmarkOptions> určuje typ vytvářeného. <xref:System.Activities.Bookmark> Možné hodnoty, které se <xref:System.Activities.BookmarkOptions.None>vzájemně <xref:System.Activities.BookmarkOptions.MultipleResume>nevylučují, jsou , a <xref:System.Activities.BookmarkOptions.NonBlocking>. Použití <xref:System.Activities.BookmarkOptions.None>, výchozí, při <xref:System.Activities.Bookmark> vytváření, který se očekává, že bude obnovena přesně jednou. Použijte <xref:System.Activities.BookmarkOptions.MultipleResume> při <xref:System.Activities.Bookmark> vytváření, které lze obnovit vícekrát. Použijte <xref:System.Activities.BookmarkOptions.NonBlocking> při <xref:System.Activities.Bookmark> vytváření, které nemusí být nikdy obnovena. Na rozdíl od záložek <xref:System.Activities.BookmarkOptions.NonBlocking> vytvořených pomocí výchozího nastavení <xref:System.Activities.BookmarkOptions>záložky nebrání dokončení aktivity.  
  
## <a name="bookmark-resumption"></a>Obnovení záložky  
 Záložky lze obnovit kódmimo pracovní postup pomocí <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> jednoho z přetížení. V tomto příkladu je vytvořena aktivita. `ReadLine` Při spuštění aktivity `ReadLine` vytvoří <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom <xref:System.Activities.Bookmark> čeká na obnovení. Po obnovení aktivita `ReadLine` přiřadí data, která byla <xref:System.Activities.Bookmark> předána <xref:System.Activities.Activity%601.Result%2A> s jeho argument.  
  
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
  
 V tomto příkladu je vytvořen `ReadLine` pracovní postup, který používá aktivitu ke shromáždění jména uživatele a jeho zobrazení v okně konzoly. Hostitelská aplikace provádí skutečnou práci shromažďování vstupu a předá jej <xref:System.Activities.Bookmark>pracovnímu postupu obnovením .  
  
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
  
 Když `ReadLine` je aktivita spuštěna, <xref:System.Activities.Bookmark> `UserName` vytvoří pojmenovaný a pak čeká na záložku, která má být obnovena. Hostitel shromažďuje požadovaná data a potom <xref:System.Activities.Bookmark>obnoví . Pracovní postup se obnoví, zobrazí název a potom se dokončí. Všimněte si, že žádný kód synchronizace je vyžadován s ohledem na obnovení záložky. A <xref:System.Activities.Bookmark> lze obnovit pouze v případě, že pracovní postup je nečinný <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> a pokud pracovní postup není nečinný, volání bloky, dokud se pracovní postup stane nečinný.  
  
## <a name="bookmark-resumption-result"></a>Výsledek obnovení záložky  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>vrátí <xref:System.Activities.BookmarkResumptionResult> hodnotu výčtu označující výsledky požadavku na obnovení záložky. Možné vrácené <xref:System.Activities.BookmarkResumptionResult.Success>hodnoty <xref:System.Activities.BookmarkResumptionResult.NotReady>jsou <xref:System.Activities.BookmarkResumptionResult.NotFound>, a . Hostitelé a rozšíření můžete tuto hodnotu použít k určení, jak postupovat.
