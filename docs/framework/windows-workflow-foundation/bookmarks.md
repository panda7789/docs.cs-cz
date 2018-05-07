---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bookmarks"></a>Záložky
Záložky jsou mechanismus, který umožňuje aktivitu pasivně čekání na vstup bez podržíte do pracovního postupu vlákno. Pokud aktivita signalizuje, že se čeká na podnětem, může vytvořit záložky. To znamená modulu runtime, že provádění aktivity by neměl být považováno za dokončené i v případě metodu aktuálně prováděné (které vytvořili <xref:System.Activities.Bookmark>) vrátí.  
  
## <a name="bookmark-basics"></a>BOOKMARK – základy  
 A <xref:System.Activities.Bookmark> představuje bod při spuštění, které může být obnoven, (a prostřednictvím které vstup mohou být zajišťovány) v rámci instance pracovního postupu. Obvykle <xref:System.Activities.Bookmark> je zadaný název a externí kód (hostitele nebo rozšíření) zodpovídá za obnovení záložku s příslušnými daty. Když <xref:System.Activities.Bookmark> obnovena, plány modulu runtime pracovního postupu <xref:System.Activities.BookmarkCallback> delegáta, který je přidružen, <xref:System.Activities.Bookmark> při jeho vytvoření.  
  
## <a name="bookmark-options"></a>BOOKMARK – možnosti  
 <xref:System.Activities.BookmarkOptions> Třída určuje typ <xref:System.Activities.Bookmark> vytváří. Možné hodnoty bez vzájemně se vylučující jsou <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, a <xref:System.Activities.BookmarkOptions.NonBlocking>. Použití <xref:System.Activities.BookmarkOptions.None>, výchozí, při vytváření <xref:System.Activities.Bookmark> , musí být obnoven, právě jednou. Použití <xref:System.Activities.BookmarkOptions.MultipleResume> při vytváření <xref:System.Activities.Bookmark> , může být obnoven vícekrát. Použití <xref:System.Activities.BookmarkOptions.NonBlocking> při vytváření <xref:System.Activities.Bookmark> , může být nikdy obnovit. Na rozdíl od záložky vytvoří pomocí výchozího <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> záložky nezabrání aktivitu dokončení.  
  
## <a name="bookmark-resumption"></a>BOOKMARK – obnovení  
 Záložky lze obnovit kódem mimo pracovní postup pomocí jedné z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> přetížení. V tomto příkladu `ReadLine` vytvoření aktivity. Po provedení `ReadLine` vytvoří aktivity <xref:System.Activities.Bookmark>, zaregistruje zpětné volání a potom počká, než <xref:System.Activities.Bookmark> být obnoven. Při obnovení, `ReadLine` aktivity přiřadí data, která byla předána s <xref:System.Activities.Bookmark> k jeho <xref:System.Activities.Activity%601.Result%2A> argument.  
  
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
  
 V tomto příkladu se vytvoří pracovní postup používající `ReadLine` aktivity shromažďovat uživatelské jméno a zobrazit ji do okna konzoly. Hostitelskou aplikaci provádí samotnou práci shromažďování vstupu a předá ji do pracovního postupu pomocí obnovení <xref:System.Activities.Bookmark>.  
  
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
  
 Když `ReadLine` aktivita se spustí, vytvoří <xref:System.Activities.Bookmark> s názvem `UserName` a potom počká, než záložku být obnoven. Hostitel shromažďuje k požadovaným datům a potom obnoví <xref:System.Activities.Bookmark>. Pracovní postup obnoví, zobrazí název a potom dokončí. Všimněte si, že žádný kód synchronizace je vyžadována s ohledem na obnovení záložky. A <xref:System.Activities.Bookmark> lze obnovit pouze při nečinnosti pracovního postupu, a pokud pracovní postup není nečinnosti, volání <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> zablokuje, dokud nebude nečinnosti pracovního postupu.  
  
## <a name="bookmark-resumption-result"></a>Výsledek obnovení záložek  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> Vrátí <xref:System.Activities.BookmarkResumptionResult> hodnota výčtu lze označit výsledky záložku obnovení žádosti. Návratové hodnoty jsou <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, a <xref:System.Activities.BookmarkResumptionResult.NotFound>. Hostitelé a rozšíření můžete použít tuto hodnotu určit, jak pokračovat.
