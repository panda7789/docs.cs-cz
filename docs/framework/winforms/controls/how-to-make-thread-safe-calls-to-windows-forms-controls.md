---
title: "Postupy: Volání (s bezpečným vlákny) ovládacích prvků Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cca363be57e5c5022c70c62d876f62cebc6e9c0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="1efff-102">Postupy: Volání (s bezpečným vlákny) ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1efff-102">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>
<span data-ttu-id="1efff-103">Pokud používáte více vláken zlepšit výkon aplikací Windows Forms, ujistěte se, abyste vytvořili volání pro vaše ovládací prvky způsobem bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-103">If you use multithreading to improve the performance of your Windows Forms applications, you must make sure that you make calls to your controls in a thread-safe way.</span></span>  
  
 <span data-ttu-id="1efff-104">Přístup k ovládacím prvkům Windows Forms ze své podstaty není bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-104">Access to Windows Forms controls is not inherently thread safe.</span></span> <span data-ttu-id="1efff-105">Pokud máte dva nebo více podprocesů manipulace s stavu ovládacího prvku, je možné vynutit ovládacího prvku v nekonzistentním stavu.</span><span class="sxs-lookup"><span data-stu-id="1efff-105">If you have two or more threads manipulating the state of a control, it is possible to force the control into an inconsistent state.</span></span> <span data-ttu-id="1efff-106">Je možné, například časování a blokování jiných chyby související s přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-106">Other thread-related bugs are possible, such as race conditions and deadlocks.</span></span> <span data-ttu-id="1efff-107">Je důležité se ujistit, že se provádí přístup k ovládacím prvkům způsobem bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-107">It is important to make sure that access to your controls is performed in a thread-safe way.</span></span>  
  
 <span data-ttu-id="1efff-108">Není bezpečné volat z vlákna, než ten, který vytvořil ovládacího prvku bez použití ovládacího prvku <xref:System.Windows.Forms.Control.Invoke%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1efff-108">It is unsafe to call a control from a thread other than the one that created the control without using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="1efff-109">Následuje příklad volání, která není bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-109">The following is an example of a call that is not thread safe.</span></span>  
  
```csharp  
// This event handler creates a thread that calls a   
// Windows Forms control in an unsafe way.  
private void setTextUnsafeBtn_Click(  
    object sender,   
    EventArgs e)  
{  
    this.demoThread =   
        new Thread(new ThreadStart(this.ThreadProcUnsafe));  
  
    this.demoThread.Start();  
}  
  
// This method is executed on the worker thread and makes  
// an unsafe call on the TextBox control.  
private void ThreadProcUnsafe()  
{  
    this.textBox1.Text = "This text was set unsafely.";  
}  
```  
  
```vb  
' This event handler creates a thread that calls a   
' Windows Forms control in an unsafe way.  
 Private Sub setTextUnsafeBtn_Click( _  
 ByVal sender As Object, _  
 ByVal e As EventArgs) Handles setTextUnsafeBtn.Click  
  
     Me.demoThread = New Thread( _  
     New ThreadStart(AddressOf Me.ThreadProcUnsafe))  
  
     Me.demoThread.Start()  
 End Sub  
  
' This method is executed on the worker thread and makes  
' an unsafe call on the TextBox control.  
Private Sub ThreadProcUnsafe()  
   Me.textBox1.Text = "This text was set unsafely."  
End Sub  
```  
  
```cpp  
// This event handler creates a thread that calls a  
    // Windows Forms control in an unsafe way.  
private:  
    void setTextUnsafeBtn_Click(Object^ sender, EventArgs^ e)  
    {  
        this->demoThread =  
            gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcUnsafe));  
  
        this->demoThread->Start();  
    }  
  
    // This method is executed on the worker thread and makes  
    // an unsafe call on the TextBox control.  
private:  
    void ThreadProcUnsafe()  
    {  
        this->textBox1->Text = "This text was set unsafely.";  
    }  
```  
  
 <span data-ttu-id="1efff-110">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Pomůže vám rozpoznat, kdy se připojujete vaše ovládací prvky způsobem, který není bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-110">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] helps you detect when you are accessing your controls in a manner that is not thread safe.</span></span> <span data-ttu-id="1efff-111">Když aplikace běží v ladicím programu a vlákna než ten, který vytvoří ovládacího prvku se pokusí zavolat, že ovládací prvek, ladicího programu vyvolá <xref:System.InvalidOperationException> se zobrazí zpráva "ovládací prvek *název ovládacího prvku* k němu přistupovat z vlákna než, který byl vytvořen na vlákno."</span><span class="sxs-lookup"><span data-stu-id="1efff-111">When you are running your application in the debugger, and a thread other than the one which created a control tries to call that control, the debugger raises an <xref:System.InvalidOperationException> with the message, "Control *control name* accessed from a thread other than the thread it was created on."</span></span>  
  
 <span data-ttu-id="1efff-112">Tato došlo k výjimce spolehlivě během ladění a za určitých okolností za běhu.</span><span class="sxs-lookup"><span data-stu-id="1efff-112">This exception occurs reliably during debugging and, under some circumstances, at run time.</span></span> <span data-ttu-id="1efff-113">Můžete se setkat výjimku při ladění aplikace, které jste napsali s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] před verzí [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1efff-113">You might see this exception when you debug applications that you wrote with the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] prior to the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="1efff-114">Důrazně doporučujeme o řešení tohoto problému, když se zobrazovat, ale můžete ji zakázat nastavením <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="1efff-114">You are strongly advised to fix this problem when you see it, but you can disable it by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> property to `false`.</span></span> <span data-ttu-id="1efff-115">To způsobí, že vaše řízení spustit jako bude spuštěná v sadě Visual Studio .NET 2003 a [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1efff-115">This causes your control to run like it would run under Visual Studio .NET 2003 and the [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1efff-116">Pokud používáte ovládací prvky ActiveX ve formuláři, může se zobrazit mezi vlákny <xref:System.InvalidOperationException> při spuštění v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1efff-116">If you are using ActiveX controls on a form, you may receive the cross-thread <xref:System.InvalidOperationException> when you run under the debugger.</span></span> <span data-ttu-id="1efff-117">V takovém případě ovládací prvek ActiveX nepodporuje více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-117">When this occurs, the ActiveX control does not support multithreading.</span></span> <span data-ttu-id="1efff-118">Další informace o pomocí Windows Forms – ovládací prvky ActiveX, najdete v části [Windows Forms a nespravované aplikace](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1efff-118">For more information about using ActiveX controls with Windows Forms, see [Windows Forms and Unmanaged Applications](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md).</span></span> <span data-ttu-id="1efff-119">Pokud používáte Visual Studio, můžete zabránit výjimku zakázáním proces hostování sady Visual Studio najdete v tématu [postupy: zákaz procesu hostování](/visualstudio/ide/how-to-disable-the-hosting-process).</span><span class="sxs-lookup"><span data-stu-id="1efff-119">If you are using Visual Studio, you can prevent this exception by disabling the Visual Studio hosting process, see [How to: Disable the Hosting Process](/visualstudio/ide/how-to-disable-the-hosting-process).</span></span>  
  
## <a name="making-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="1efff-120">Volání bezpečného přístupu do Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="1efff-120">Making Thread-Safe Calls to Windows Forms Controls</span></span>  
  
#### <a name="to-make-a-thread-safe-call-to-a-windows-forms-control"></a><span data-ttu-id="1efff-121">K volání bezpečného přístupu do ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1efff-121">To make a thread-safe call to a Windows Forms control</span></span>  
  
1.  <span data-ttu-id="1efff-122">Dotaz ovládacího prvku <xref:System.Windows.Forms.Control.InvokeRequired%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1efff-122">Query the control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> property.</span></span>  
  
2.  <span data-ttu-id="1efff-123">Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true`, volání <xref:System.Windows.Forms.Control.Invoke%2A> s delegáta, který umožňuje vlastní volání do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1efff-123">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, call <xref:System.Windows.Forms.Control.Invoke%2A> with a delegate that makes the actual call to the control.</span></span>  
  
3.  <span data-ttu-id="1efff-124">Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `false`, ovládacího prvku volat přímo.</span><span class="sxs-lookup"><span data-stu-id="1efff-124">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, call the control directly.</span></span>  
  
 <span data-ttu-id="1efff-125">V následujícím příkladu kódu je implementována volání bezpečné pro přístup z více vláken ve `ThreadProcSafe` metodu, která se spustí ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1efff-125">In the following code example, a thread-safe call is implemented in the `ThreadProcSafe` method, which is executed by the background thread.</span></span> <span data-ttu-id="1efff-126">Pokud <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true`, `ThreadProcSafe` metoda vytvoří instanci `StringArgReturningVoidDelegate` a který předává do formuláře <xref:System.Windows.Forms.Control.Invoke%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1efff-126">If the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, the `ThreadProcSafe` method creates an instance of `StringArgReturningVoidDelegate` and passes that to the form's <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="1efff-127">To způsobí, že `SetText` metoda k volání na vlákno, které vytvořili <xref:System.Windows.Forms.TextBox> řízení a v tomto kontextu vláken <xref:System.Windows.Forms.Control.Text%2A> vlastnost je nastavena přímo.</span><span class="sxs-lookup"><span data-stu-id="1efff-127">This causes the `SetText` method to be called on the thread that created the <xref:System.Windows.Forms.TextBox> control, and in this thread context the <xref:System.Windows.Forms.Control.Text%2A> property is set directly.</span></span>  
  
```csharp  
// This event handler creates a thread that calls a   
// Windows Forms control in a thread-safe way.  
private void setTextSafeBtn_Click(  
    object sender,   
    EventArgs e)  
{  
    this.demoThread =   
        new Thread(new ThreadStart(this.ThreadProcSafe));  
  
    this.demoThread.Start();  
}  
  
// This method is executed on the worker thread and makes  
// a thread-safe call on the TextBox control.  
private void ThreadProcSafe()  
{  
    this.SetText("This text was set safely.");  
}  
```  
  
```vb  
' This event handler creates a thread that calls a   
' Windows Forms control in a thread-safe way.  
 Private Sub setTextSafeBtn_Click( _  
 ByVal sender As Object, _  
 ByVal e As EventArgs) Handles setTextSafeBtn.Click  
  
     Me.demoThread = New Thread( _  
     New ThreadStart(AddressOf Me.ThreadProcSafe))  
  
     Me.demoThread.Start()  
 End Sub  
  
' This method is executed on the worker thread and makes  
' a thread-safe call on the TextBox control.  
Private Sub ThreadProcSafe()  
   Me.SetText("This text was set safely.")  
 End Sub  
```  
  
```cpp  
// This event handler creates a thread that calls a  
    // Windows Forms control in a thread-safe way.  
private:  
    void setTextSafeBtn_Click(Object^ sender, EventArgs^ e)  
    {  
        this->demoThread =  
            gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcSafe));  
  
        this->demoThread->Start();  
    }  
  
    // This method is executed on the worker thread and makes  
    // a thread-safe call on the TextBox control.  
private:  
    void ThreadProcSafe()  
    {  
        this->SetText("This text was set safely.");  
    }  
```  
  
```csharp  
// This delegate enables asynchronous calls for setting  
// the text property on a TextBox control.  
delegate void StringArgReturningVoidDelegate(string text);  
```  
  
```vb  
' This delegate enables asynchronous calls for setting  
' the text property on a TextBox control.  
Delegate Sub StringArgReturningVoidDelegate([text] As String)  
```  
  
```cpp  
// This delegate enables asynchronous calls for setting  
// the text property on a TextBox control.  
delegate void StringArgReturningVoidDelegate(String^ text);  
```  
  
```csharp  
// This method demonstrates a pattern for making thread-safe  
// calls on a Windows Forms control.   
//  
// If the calling thread is different from the thread that  
// created the TextBox control, this method creates a  
// StringArgReturningVoidDelegate and calls itself asynchronously using the  
// Invoke method.  
//  
// If the calling thread is the same as the thread that created  
// the TextBox control, the Text property is set directly.   
  
private void SetText(string text)  
{  
    // InvokeRequired required compares the thread ID of the  
    // calling thread to the thread ID of the creating thread.  
    // If these threads are different, it returns true.  
    if (this.textBox1.InvokeRequired)  
    {     
        StringArgReturningVoidDelegate d = new StringArgReturningVoidDelegate(SetText);  
        this.Invoke(d, new object[] { text });  
    }  
    else  
    {  
        this.textBox1.Text = text;  
    }  
}  
```  
  
```vb  
' This method demonstrates a pattern for making thread-safe  
' calls on a Windows Forms control.   
'  
' If the calling thread is different from the thread that  
' created the TextBox control, this method creates a  
' StringArgReturningVoidDelegate and calls itself asynchronously using the  
' Invoke method.  
'  
' If the calling thread is the same as the thread that created  
 ' the TextBox control, the Text property is set directly.  
  
 Private Sub SetText(ByVal [text] As String)  
  
     ' InvokeRequired required compares the thread ID of the  
     ' calling thread to the thread ID of the creating thread.  
     ' If these threads are different, it returns true.  
     If Me.textBox1.InvokeRequired Then  
         Dim d As New StringArgReturningVoidDelegate(AddressOf SetText)  
         Me.Invoke(d, New Object() {[text]})  
     Else  
         Me.textBox1.Text = [text]  
     End If  
 End Sub  
```  
  
```cpp  
// This method demonstrates a pattern for making thread-safe  
    // calls on a Windows Forms control.  
    //  
    // If the calling thread is different from the thread that  
    // created the TextBox control, this method creates a  
    // StringArgReturningVoidDelegate and calls itself asynchronously using the  
    // Invoke method.  
    //  
    // If the calling thread is the same as the thread that created  
    // the TextBox control, the Text property is set directly.  
  
private:  
    void SetText(String^ text)  
    {  
        // InvokeRequired required compares the thread ID of the  
        // calling thread to the thread ID of the creating thread.  
        // If these threads are different, it returns true.  
        if (this->textBox1->InvokeRequired)  
        {  
            StringArgReturningVoidDelegate^ d =   
                gcnew StringArgReturningVoidDelegate(this, &Form1::SetText);  
            this->Invoke(d, gcnew array<Object^> { text });  
        }  
        else  
        {  
            this->textBox1->Text = text;  
        }  
    }  
```  
  
## <a name="making-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="1efff-128">BackgroundWorker – pomocí volání bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="1efff-128">Making Thread-Safe Calls by using BackgroundWorker</span></span>  
 <span data-ttu-id="1efff-129">Upřednostňovaný způsob implementace více vláken ve vaší aplikaci, je použití <xref:System.ComponentModel.BackgroundWorker> součásti.</span><span class="sxs-lookup"><span data-stu-id="1efff-129">The preferred way to implement multithreading in your application is to use the <xref:System.ComponentModel.BackgroundWorker> component.</span></span> <span data-ttu-id="1efff-130"><xref:System.ComponentModel.BackgroundWorker> Součást používá model založeného na událostech pro více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-130">The <xref:System.ComponentModel.BackgroundWorker> component uses an event-driven model for multithreading.</span></span> <span data-ttu-id="1efff-131">Vlákně na pozadí běží vaše <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události a vlákno, které vytváří vaše ovládací prvky běží vaše <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="1efff-131">The background thread runs your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, and the thread that creates your controls runs your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span> <span data-ttu-id="1efff-132">Můžete volat vaše ovládací prvky z vaší <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="1efff-132">You can call your controls from your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span>  
  
#### <a name="to-make-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="1efff-133">BackgroundWorker – pomocí volání bezpečné pro přístup z více vláken</span><span class="sxs-lookup"><span data-stu-id="1efff-133">To make thread-safe calls by using BackgroundWorker</span></span>  
  
1.  <span data-ttu-id="1efff-134">Vytvoření metody, které udělají tuto práci, který chcete provést ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1efff-134">Create a method to do the work that you want done in the background thread.</span></span> <span data-ttu-id="1efff-135">Ovládací prvky vytvořené pomocí hlavní vlákno v tato metoda není volána.</span><span class="sxs-lookup"><span data-stu-id="1efff-135">Do not call controls created by the main thread in this method.</span></span>  
  
2.  <span data-ttu-id="1efff-136">Vytvořte metodu pro sestavy o výsledcích práce pozadí po jejím dokončení.</span><span class="sxs-lookup"><span data-stu-id="1efff-136">Create a method to report the results of your background work after it finishes.</span></span> <span data-ttu-id="1efff-137">Ovládací prvky vytvořené pomocí hlavní vlákno v této metody můžete volat.</span><span class="sxs-lookup"><span data-stu-id="1efff-137">You can call controls created by the main thread in this method.</span></span>  
  
3.  <span data-ttu-id="1efff-138">BIND – metoda vytvořené v kroku 1 <xref:System.ComponentModel.BackgroundWorker.DoWork> události instance <xref:System.ComponentModel.BackgroundWorker>a vytvořte vazbu metodu vytvořili v kroku 2 na stejnou instanci <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="1efff-138">Bind the method created in step 1 to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event of an instance of <xref:System.ComponentModel.BackgroundWorker>, and bind the method created in step 2 to the same instance’s <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
4.  <span data-ttu-id="1efff-139">Chcete-li spustit vlákně na pozadí, zavolejte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu <xref:System.ComponentModel.BackgroundWorker> instance.</span><span class="sxs-lookup"><span data-stu-id="1efff-139">To start the background thread, call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of the <xref:System.ComponentModel.BackgroundWorker> instance.</span></span>  
  
 <span data-ttu-id="1efff-140">V následujícím příkladu kódu <xref:System.ComponentModel.BackgroundWorker.DoWork> používá obslužné rutiny události <xref:System.Threading.Thread.Sleep%2A> k simulaci práci, kterou nějakou dobu trvá.</span><span class="sxs-lookup"><span data-stu-id="1efff-140">In the following code example, the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler uses <xref:System.Threading.Thread.Sleep%2A> to simulate work that takes some time.</span></span> <span data-ttu-id="1efff-141">Nevyvolá formuláře <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1efff-141">It does not call the form’s <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="1efff-142"><xref:System.Windows.Forms.TextBox> Ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> přímo v je hodnota nastavena <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1efff-142">The <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.Text%2A> property is set directly in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
```csharp  
// This BackgroundWorker is used to demonstrate the   
// preferred way of performing asynchronous operations.  
private BackgroundWorker backgroundWorker1;  
```  
  
```vb  
' This BackgroundWorker is used to demonstrate the   
' preferred way of performing asynchronous operations.  
Private WithEvents backgroundWorker1 As BackgroundWorker  
```  
  
```cpp  
// This BackgroundWorker is used to demonstrate the  
    // preferred way of performing asynchronous operations.  
private:  
    BackgroundWorker^ backgroundWorker1;  
```  
  
```csharp  
// This event handler starts the form's   
// BackgroundWorker by calling RunWorkerAsync.  
//  
// The Text property of the TextBox control is set  
// when the BackgroundWorker raises the RunWorkerCompleted  
// event.  
private void setTextBackgroundWorkerBtn_Click(  
    object sender,   
    EventArgs e)  
{  
    this.backgroundWorker1.RunWorkerAsync();  
}  
  
// This event handler sets the Text property of the TextBox  
// control. It is called on the thread that created the   
// TextBox control, so the call is thread-safe.  
//  
// BackgroundWorker is the preferred way to perform asynchronous  
// operations.  
  
private void backgroundWorker1_RunWorkerCompleted(  
    object sender,   
    RunWorkerCompletedEventArgs e)  
{  
    this.textBox1.Text =   
        "This text was set safely by BackgroundWorker.";  
}  
```  
  
```vb  
' This event handler starts the form's   
' BackgroundWorker by calling RunWorkerAsync.  
'  
' The Text property of the TextBox control is set  
' when the BackgroundWorker raises the RunWorkerCompleted  
' event.  
 Private Sub setTextBackgroundWorkerBtn_Click( _  
 ByVal sender As Object, _  
 ByVal e As EventArgs) Handles setTextBackgroundWorkerBtn.Click  
     Me.backgroundWorker1.RunWorkerAsync()  
 End Sub  
  
' This event handler sets the Text property of the TextBox  
' control. It is called on the thread that created the   
' TextBox control, so the call is thread-safe.  
'  
' BackgroundWorker is the preferred way to perform asynchronous  
' operations.  
 Private Sub backgroundWorker1_RunWorkerCompleted( _  
 ByVal sender As Object, _  
 ByVal e As RunWorkerCompletedEventArgs) _  
 Handles backgroundWorker1.RunWorkerCompleted  
     Me.textBox1.Text = _  
     "This text was set safely by BackgroundWorker."  
 End Sub  
```  
  
```cpp  
// This event handler starts the form's  
    // BackgroundWorker by calling RunWorkerAsync.  
    //  
    // The Text property of the TextBox control is set  
    // when the BackgroundWorker raises the RunWorkerCompleted  
    // event.  
private:  
    void setTextBackgroundWorkerBtn_Click(Object^ sender, EventArgs^ e)  
    {  
        this->backgroundWorker1->RunWorkerAsync();  
    }  
  
    // This event handler sets the Text property of the TextBox  
    // control. It is called on the thread that created the  
    // TextBox control, so the call is thread-safe.  
    //  
    // BackgroundWorker is the preferred way to perform asynchronous  
    // operations.  
  
private:  
    void backgroundWorker1_RunWorkerCompleted(  
        Object^ sender,  
        RunWorkerCompletedEventArgs^ e)  
    {  
        this->textBox1->Text =  
            "This text was set safely by BackgroundWorker.";  
    }  
```  
  
 <span data-ttu-id="1efff-143">Můžete také hlášení průběhu úlohy na pozadí pomocí <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="1efff-143">You can also report the progress of a background task by using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="1efff-144">Příklad, která zahrnuje tuto událost, naleznete v části <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="1efff-144">For an example that incorporates that event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1efff-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="1efff-145">Example</span></span>  
 <span data-ttu-id="1efff-146">Následující příklad kódu je kompletní aplikace Windows Forms, která se skládá z formulář, který má tři tlačítka a jedno textové pole.</span><span class="sxs-lookup"><span data-stu-id="1efff-146">The following code example is a complete Windows Forms application that consists of a form with three buttons and one text box.</span></span> <span data-ttu-id="1efff-147">Na první tlačítko ukazuje unsafe přístupu mezi vlákny, druhý tlačítko ukazuje bezpečný přístup pomocí <xref:System.Windows.Forms.Control.Invoke%2A>, a třetí tlačítko ukazuje bezpečný přístup pomocí <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="1efff-147">The first button demonstrates unsafe cross-thread access, the second button demonstrates safe access by using <xref:System.Windows.Forms.Control.Invoke%2A>, and the third button demonstrates safe access by using <xref:System.ComponentModel.BackgroundWorker>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1efff-148">Pokyny o tom, jak spustit v příkladu najdete v tématu [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416).</span><span class="sxs-lookup"><span data-stu-id="1efff-148">For instructions on how to run the example, see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416).</span></span> <span data-ttu-id="1efff-149">Tento příklad vyžaduje odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1efff-149">This example requires references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.Threading;  
using System.Windows.Forms;  
  
namespace CrossThreadDemo  
{  
    public class Form1 : Form  
    {  
        // This delegate enables asynchronous calls for setting  
        // the text property on a TextBox control.  
        delegate void StringArgReturningVoidDelegate(string text);  
  
        // This thread is used to demonstrate both thread-safe and  
        // unsafe ways to call a Windows Forms control.  
        private Thread demoThread = null;  
  
        // This BackgroundWorker is used to demonstrate the   
        // preferred way of performing asynchronous operations.  
        private BackgroundWorker backgroundWorker1;  
  
        private TextBox textBox1;  
        private Button setTextUnsafeBtn;  
        private Button setTextSafeBtn;  
        private Button setTextBackgroundWorkerBtn;  
  
        private System.ComponentModel.IContainer components = null;  
  
        public Form1()  
        {  
            InitializeComponent();  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (disposing && (components != null))  
            {  
                components.Dispose();  
            }  
            base.Dispose(disposing);  
        }  
  
        // This event handler creates a thread that calls a   
        // Windows Forms control in an unsafe way.  
        private void setTextUnsafeBtn_Click(  
            object sender,   
            EventArgs e)  
        {  
            this.demoThread =   
                new Thread(new ThreadStart(this.ThreadProcUnsafe));  
  
            this.demoThread.Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // an unsafe call on the TextBox control.  
        private void ThreadProcUnsafe()  
        {  
            this.textBox1.Text = "This text was set unsafely.";  
        }  
  
        // This event handler creates a thread that calls a   
        // Windows Forms control in a thread-safe way.  
        private void setTextSafeBtn_Click(  
            object sender,   
            EventArgs e)  
        {  
            this.demoThread =   
                new Thread(new ThreadStart(this.ThreadProcSafe));  
  
            this.demoThread.Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // a thread-safe call on the TextBox control.  
        private void ThreadProcSafe()  
        {  
            this.SetText("This text was set safely.");  
        }  
  
        // This method demonstrates a pattern for making thread-safe  
        // calls on a Windows Forms control.   
        //  
        // If the calling thread is different from the thread that  
        // created the TextBox control, this method creates a  
        // StringArgReturningVoidDelegate and calls itself asynchronously using the  
        // Invoke method.  
        //  
        // If the calling thread is the same as the thread that created  
        // the TextBox control, the Text property is set directly.   
  
        private void SetText(string text)  
        {  
            // InvokeRequired required compares the thread ID of the  
            // calling thread to the thread ID of the creating thread.  
            // If these threads are different, it returns true.  
            if (this.textBox1.InvokeRequired)  
            {     
                StringArgReturningVoidDelegate d = new StringArgReturningVoidDelegate(SetText);  
                this.Invoke(d, new object[] { text });  
            }  
            else  
            {  
                this.textBox1.Text = text;  
            }  
        }  
  
        // This event handler starts the form's   
        // BackgroundWorker by calling RunWorkerAsync.  
        //  
        // The Text property of the TextBox control is set  
        // when the BackgroundWorker raises the RunWorkerCompleted  
        // event.  
        private void setTextBackgroundWorkerBtn_Click(  
            object sender,   
            EventArgs e)  
        {  
            this.backgroundWorker1.RunWorkerAsync();  
        }  
  
        // This event handler sets the Text property of the TextBox  
        // control. It is called on the thread that created the   
        // TextBox control, so the call is thread-safe.  
        //  
        // BackgroundWorker is the preferred way to perform asynchronous  
        // operations.  
  
        private void backgroundWorker1_RunWorkerCompleted(  
            object sender,   
            RunWorkerCompletedEventArgs e)  
        {  
            this.textBox1.Text =   
                "This text was set safely by BackgroundWorker.";  
        }  
  
        #region Windows Form Designer generated code  
  
        private void InitializeComponent()  
        {  
            this.textBox1 = new System.Windows.Forms.TextBox();  
            this.setTextUnsafeBtn = new System.Windows.Forms.Button();  
            this.setTextSafeBtn = new System.Windows.Forms.Button();  
            this.setTextBackgroundWorkerBtn = new System.Windows.Forms.Button();  
            this.backgroundWorker1 = new System.ComponentModel.BackgroundWorker();  
            this.SuspendLayout();  
            //   
            // textBox1  
            //   
            this.textBox1.Location = new System.Drawing.Point(12, 12);  
            this.textBox1.Name = "textBox1";  
            this.textBox1.Size = new System.Drawing.Size(240, 20);  
            this.textBox1.TabIndex = 0;  
            //   
            // setTextUnsafeBtn  
            //   
            this.setTextUnsafeBtn.Location = new System.Drawing.Point(15, 55);  
            this.setTextUnsafeBtn.Name = "setTextUnsafeBtn";  
            this.setTextUnsafeBtn.TabIndex = 1;  
            this.setTextUnsafeBtn.Text = "Unsafe Call";  
            this.setTextUnsafeBtn.Click += new System.EventHandler(this.setTextUnsafeBtn_Click);  
            //   
            // setTextSafeBtn  
            //   
            this.setTextSafeBtn.Location = new System.Drawing.Point(96, 55);  
            this.setTextSafeBtn.Name = "setTextSafeBtn";  
            this.setTextSafeBtn.TabIndex = 2;  
            this.setTextSafeBtn.Text = "Safe Call";  
            this.setTextSafeBtn.Click += new System.EventHandler(this.setTextSafeBtn_Click);  
            //   
            // setTextBackgroundWorkerBtn  
            //   
            this.setTextBackgroundWorkerBtn.Location = new System.Drawing.Point(177, 55);  
            this.setTextBackgroundWorkerBtn.Name = "setTextBackgroundWorkerBtn";  
            this.setTextBackgroundWorkerBtn.TabIndex = 3;  
            this.setTextBackgroundWorkerBtn.Text = "Safe BW Call";  
            this.setTextBackgroundWorkerBtn.Click += new System.EventHandler(this.setTextBackgroundWorkerBtn_Click);  
            //   
            // backgroundWorker1  
            //   
            this.backgroundWorker1.RunWorkerCompleted += new System.ComponentModel.RunWorkerCompletedEventHandler(this.backgroundWorker1_RunWorkerCompleted);  
            //   
            // Form1  
            //   
            this.ClientSize = new System.Drawing.Size(268, 96);  
            this.Controls.Add(this.setTextBackgroundWorkerBtn);  
            this.Controls.Add(this.setTextSafeBtn);  
            this.Controls.Add(this.setTextUnsafeBtn);  
            this.Controls.Add(this.textBox1);  
            this.Name = "Form1";  
            this.Text = "Form1";  
            this.ResumeLayout(false);  
            this.PerformLayout();  
  
        }  
  
        #endregion  
  
        [STAThread]  
        static void Main()  
        {  
            Application.EnableVisualStyles();  
            Application.Run(new Form1());  
        }  
  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.ComponentModel  
Imports System.Threading  
Imports System.Windows.Forms  
  
Public Class Form1  
   Inherits Form  
  
   ' This delegate enables asynchronous calls for setting  
   ' the text property on a TextBox control.  
   Delegate Sub StringArgReturningVoidDelegate([text] As String)  
  
   ' This thread is used to demonstrate both thread-safe and  
   ' unsafe ways to call a Windows Forms control.  
   Private demoThread As Thread = Nothing  
  
   ' This BackgroundWorker is used to demonstrate the   
   ' preferred way of performing asynchronous operations.  
   Private WithEvents backgroundWorker1 As BackgroundWorker  
  
   Private textBox1 As TextBox  
   Private WithEvents setTextUnsafeBtn As Button  
   Private WithEvents setTextSafeBtn As Button  
   Private WithEvents setTextBackgroundWorkerBtn As Button  
  
   Private components As System.ComponentModel.IContainer = Nothing  
  
   Public Sub New()  
      InitializeComponent()  
    End Sub  
  
   Protected Overrides Sub Dispose(disposing As Boolean)  
      If disposing AndAlso (components IsNot Nothing) Then  
         components.Dispose()  
      End If  
      MyBase.Dispose(disposing)  
    End Sub  
  
   ' This event handler creates a thread that calls a   
   ' Windows Forms control in an unsafe way.  
    Private Sub setTextUnsafeBtn_Click( _  
    ByVal sender As Object, _  
    ByVal e As EventArgs) Handles setTextUnsafeBtn.Click  
  
        Me.demoThread = New Thread( _  
        New ThreadStart(AddressOf Me.ThreadProcUnsafe))  
  
        Me.demoThread.Start()  
    End Sub  
  
   ' This method is executed on the worker thread and makes  
   ' an unsafe call on the TextBox control.  
   Private Sub ThreadProcUnsafe()  
      Me.textBox1.Text = "This text was set unsafely."  
   End Sub   
  
   ' This event handler creates a thread that calls a   
   ' Windows Forms control in a thread-safe way.  
    Private Sub setTextSafeBtn_Click( _  
    ByVal sender As Object, _  
    ByVal e As EventArgs) Handles setTextSafeBtn.Click  
  
        Me.demoThread = New Thread( _  
        New ThreadStart(AddressOf Me.ThreadProcSafe))  
  
        Me.demoThread.Start()  
    End Sub  
  
   ' This method is executed on the worker thread and makes  
   ' a thread-safe call on the TextBox control.  
   Private Sub ThreadProcSafe()  
      Me.SetText("This text was set safely.")  
    End Sub  
  
   ' This method demonstrates a pattern for making thread-safe  
   ' calls on a Windows Forms control.   
   '  
   ' If the calling thread is different from the thread that  
   ' created the TextBox control, this method creates a  
   ' StringArgReturningVoidDelegate and calls itself asynchronously using the  
   ' Invoke method.  
   '  
   ' If the calling thread is the same as the thread that created  
    ' the TextBox control, the Text property is set directly.   
  
    Private Sub SetText(ByVal [text] As String)  
  
        ' InvokeRequired required compares the thread ID of the  
        ' calling thread to the thread ID of the creating thread.  
        ' If these threads are different, it returns true.  
        If Me.textBox1.InvokeRequired Then  
            Dim d As New StringArgReturningVoidDelegate(AddressOf SetText)  
            Me.Invoke(d, New Object() {[text]})  
        Else  
            Me.textBox1.Text = [text]  
        End If  
    End Sub  
  
   ' This event handler starts the form's   
   ' BackgroundWorker by calling RunWorkerAsync.  
   '  
   ' The Text property of the TextBox control is set  
   ' when the BackgroundWorker raises the RunWorkerCompleted  
   ' event.  
    Private Sub setTextBackgroundWorkerBtn_Click( _  
    ByVal sender As Object, _  
    ByVal e As EventArgs) Handles setTextBackgroundWorkerBtn.Click  
        Me.backgroundWorker1.RunWorkerAsync()  
    End Sub  
  
   ' This event handler sets the Text property of the TextBox  
   ' control. It is called on the thread that created the   
   ' TextBox control, so the call is thread-safe.  
   '  
   ' BackgroundWorker is the preferred way to perform asynchronous  
   ' operations.  
    Private Sub backgroundWorker1_RunWorkerCompleted( _  
    ByVal sender As Object, _  
    ByVal e As RunWorkerCompletedEventArgs) _  
    Handles backgroundWorker1.RunWorkerCompleted  
        Me.textBox1.Text = _  
        "This text was set safely by BackgroundWorker."  
    End Sub  
  
   #Region "Windows Form Designer generated code"  
  
   Private Sub InitializeComponent()  
      Me.textBox1 = New System.Windows.Forms.TextBox()  
      Me.setTextUnsafeBtn = New System.Windows.Forms.Button()  
      Me.setTextSafeBtn = New System.Windows.Forms.Button()  
      Me.setTextBackgroundWorkerBtn = New System.Windows.Forms.Button()  
      Me.backgroundWorker1 = New System.ComponentModel.BackgroundWorker()  
      Me.SuspendLayout()  
      '   
      ' textBox1  
      '   
      Me.textBox1.Location = New System.Drawing.Point(12, 12)  
      Me.textBox1.Name = "textBox1"  
      Me.textBox1.Size = New System.Drawing.Size(240, 20)  
      Me.textBox1.TabIndex = 0  
      '   
      ' setTextUnsafeBtn  
      '   
      Me.setTextUnsafeBtn.Location = New System.Drawing.Point(15, 55)  
      Me.setTextUnsafeBtn.Name = "setTextUnsafeBtn"  
      Me.setTextUnsafeBtn.TabIndex = 1  
      Me.setTextUnsafeBtn.Text = "Unsafe Call"  
      '   
      ' setTextSafeBtn  
      '   
      Me.setTextSafeBtn.Location = New System.Drawing.Point(96, 55)  
      Me.setTextSafeBtn.Name = "setTextSafeBtn"  
      Me.setTextSafeBtn.TabIndex = 2  
      Me.setTextSafeBtn.Text = "Safe Call"  
      '   
      ' setTextBackgroundWorkerBtn  
      '   
      Me.setTextBackgroundWorkerBtn.Location = New System.Drawing.Point(177, 55)  
      Me.setTextBackgroundWorkerBtn.Name = "setTextBackgroundWorkerBtn"  
      Me.setTextBackgroundWorkerBtn.TabIndex = 3  
      Me.setTextBackgroundWorkerBtn.Text = "Safe BW Call"  
      '   
      ' backgroundWorker1  
      '   
      '   
      ' Form1  
      '   
      Me.ClientSize = New System.Drawing.Size(268, 96)  
      Me.Controls.Add(setTextBackgroundWorkerBtn)  
      Me.Controls.Add(setTextSafeBtn)  
      Me.Controls.Add(setTextUnsafeBtn)  
      Me.Controls.Add(textBox1)  
      Me.Name = "Form1"  
      Me.Text = "Form1"  
      Me.ResumeLayout(False)  
      Me.PerformLayout()  
   End Sub 'InitializeComponent   
  
   #End Region  
  
   <STAThread()>  _  
   Shared Sub Main()  
      Application.EnableVisualStyles()  
      Application.Run(New Form1())  
    End Sub  
End Class  
```  
  
```cpp  
#using <System.dll>  
#using <System.Windows.Forms.dll>  
#using <System.Drawing.dll>  
  
using namespace System;  
using namespace System::ComponentModel;  
using namespace System::Threading;  
using namespace System::Windows::Forms;  
  
namespace CrossThreadDemo  
{  
    public ref class Form1 : public Form  
    {  
        // This delegate enables asynchronous calls for setting  
        // the text property on a TextBox control.  
        delegate void StringArgReturningVoidDelegate(String^ text);  
  
        // This thread is used to demonstrate both thread-safe and  
        // unsafe ways to call a Windows Forms control.  
    private:  
        Thread^ demoThread;  
  
        // This BackgroundWorker is used to demonstrate the  
        // preferred way of performing asynchronous operations.  
    private:  
        BackgroundWorker^ backgroundWorker1;  
  
    private:  
        TextBox^ textBox1;  
    private:  
        Button^ setTextUnsafeBtn;  
    private:  
        Button^ setTextSafeBtn;  
    private:  
        Button^ setTextBackgroundWorkerBtn;  
  
    private:  
        System::ComponentModel::IContainer^ components;  
  
    public:  
        Form1()  
        {  
            components = nullptr;  
            InitializeComponent();  
        }  
  
    protected:  
        ~Form1()  
        {  
            if (components != nullptr)  
            {  
                delete components;  
            }  
        }  
  
        // This event handler creates a thread that calls a  
        // Windows Forms control in an unsafe way.  
    private:  
        void setTextUnsafeBtn_Click(Object^ sender, EventArgs^ e)  
        {  
            this->demoThread =  
                gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcUnsafe));  
  
            this->demoThread->Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // an unsafe call on the TextBox control.  
    private:  
        void ThreadProcUnsafe()  
        {  
            this->textBox1->Text = "This text was set unsafely.";  
        }  
  
        // This event handler creates a thread that calls a  
        // Windows Forms control in a thread-safe way.  
    private:  
        void setTextSafeBtn_Click(Object^ sender, EventArgs^ e)  
        {  
            this->demoThread =  
                gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcSafe));  
  
            this->demoThread->Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // a thread-safe call on the TextBox control.  
    private:  
        void ThreadProcSafe()  
        {  
            this->SetText("This text was set safely.");  
        }  
  
        // This method demonstrates a pattern for making thread-safe  
        // calls on a Windows Forms control.  
        //  
        // If the calling thread is different from the thread that  
        // created the TextBox control, this method creates a  
        // StringArgReturningVoidDelegate and calls itself asynchronously using the  
        // Invoke method.  
        //  
        // If the calling thread is the same as the thread that created  
        // the TextBox control, the Text property is set directly.  
  
    private:  
        void SetText(String^ text)  
        {  
            // InvokeRequired required compares the thread ID of the  
            // calling thread to the thread ID of the creating thread.  
            // If these threads are different, it returns true.  
            if (this->textBox1->InvokeRequired)  
            {  
                StringArgReturningVoidDelegate^ d =   
                    gcnew StringArgReturningVoidDelegate(this, &Form1::SetText);  
                this->Invoke(d, gcnew array<Object^> { text });  
            }  
            else  
            {  
                this->textBox1->Text = text;  
            }  
        }  
  
        // This event handler starts the form's  
        // BackgroundWorker by calling RunWorkerAsync.  
        //  
        // The Text property of the TextBox control is set  
        // when the BackgroundWorker raises the RunWorkerCompleted  
        // event.  
    private:  
        void setTextBackgroundWorkerBtn_Click(Object^ sender, EventArgs^ e)  
        {  
            this->backgroundWorker1->RunWorkerAsync();  
        }  
  
        // This event handler sets the Text property of the TextBox  
        // control. It is called on the thread that created the  
        // TextBox control, so the call is thread-safe.  
        //  
        // BackgroundWorker is the preferred way to perform asynchronous  
        // operations.  
  
    private:  
        void backgroundWorker1_RunWorkerCompleted(  
            Object^ sender,  
            RunWorkerCompletedEventArgs^ e)  
        {  
            this->textBox1->Text =  
                "This text was set safely by BackgroundWorker.";  
        }  
  
        #pragma region Windows Form Designer generated code  
  
    private:  
        void InitializeComponent()  
        {  
            this->textBox1 = gcnew System::Windows::Forms::TextBox();  
            this->setTextUnsafeBtn = gcnew System::Windows::Forms::Button();  
            this->setTextSafeBtn = gcnew System::Windows::Forms::Button();  
            this->setTextBackgroundWorkerBtn =   
                gcnew System::Windows::Forms::Button();  
            this->backgroundWorker1 =   
                gcnew System::ComponentModel::BackgroundWorker();  
            this->SuspendLayout();  
            //  
            // textBox1  
            //  
            this->textBox1->Location = System::Drawing::Point(12, 12);  
            this->textBox1->Name = "textBox1";  
            this->textBox1->Size = System::Drawing::Size(240, 20);  
            this->textBox1->TabIndex = 0;  
            //  
            // setTextUnsafeBtn  
            //  
            this->setTextUnsafeBtn->Location = System::Drawing::Point(15, 55);  
            this->setTextUnsafeBtn->Name = "setTextUnsafeBtn";  
            this->setTextUnsafeBtn->TabIndex = 1;  
            this->setTextUnsafeBtn->Text = "Unsafe Call";  
            this->setTextUnsafeBtn->Click +=   
                gcnew System::EventHandler(  
                this,&Form1::setTextUnsafeBtn_Click);  
            //  
            // setTextSafeBtn  
            //  
            this->setTextSafeBtn->Location = System::Drawing::Point(96, 55);  
            this->setTextSafeBtn->Name = "setTextSafeBtn";  
            this->setTextSafeBtn->TabIndex = 2;  
            this->setTextSafeBtn->Text = "Safe Call";  
            this->setTextSafeBtn->Click +=   
                gcnew System::EventHandler(this,&Form1::setTextSafeBtn_Click);  
            //  
            // setTextBackgroundWorkerBtn  
            //  
            this->setTextBackgroundWorkerBtn->Location =   
                System::Drawing::Point(177, 55);  
            this->setTextBackgroundWorkerBtn->Name =   
                "setTextBackgroundWorkerBtn";  
            this->setTextBackgroundWorkerBtn->TabIndex = 3;  
            this->setTextBackgroundWorkerBtn->Text = "Safe BW Call";  
            this->setTextBackgroundWorkerBtn->Click +=   
                gcnew System::EventHandler(  
                this,&Form1::setTextBackgroundWorkerBtn_Click);  
            //  
            // backgroundWorker1  
            //  
            this->backgroundWorker1->RunWorkerCompleted +=   
                gcnew System::ComponentModel::RunWorkerCompletedEventHandler(  
                this,&Form1::backgroundWorker1_RunWorkerCompleted);  
            //  
            // Form1  
            //  
            this->ClientSize = System::Drawing::Size(268, 96);  
            this->Controls->Add(this->setTextBackgroundWorkerBtn);  
            this->Controls->Add(this->setTextSafeBtn);  
            this->Controls->Add(this->setTextUnsafeBtn);  
            this->Controls->Add(this->textBox1);  
            this->Name = "Form1";  
            this->Text = "Form1";  
            this->ResumeLayout(false);  
            this->PerformLayout();  
  
        }  
  
        #pragma endregion  
    };  
}  
  
[STAThread]  
int main()  
{  
    Application::EnableVisualStyles();  
    Application::Run(gcnew CrossThreadDemo::Form1());  
}  
```  
  
 <span data-ttu-id="1efff-150">Při spuštění aplikace a klikněte na tlačítko **Unsafe volání** tlačítko, můžete okamžitě najdete v části "Written hlavní vlákno" v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="1efff-150">When you run the application and click the **Unsafe Call** button, you immediately see "Written by the main thread" in the text box.</span></span> <span data-ttu-id="1efff-151">Později, dvou sekund pokusem unsafe volání ladicího programu sady Visual Studio označuje, že došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="1efff-151">Two seconds later, when the unsafe call is attempted, the Visual Studio debugger indicates that an exception occurred.</span></span> <span data-ttu-id="1efff-152">Ladicí program zastaví na řádku ve vlákně na pozadí, který se pokusil o zápis přímo do textového pole.</span><span class="sxs-lookup"><span data-stu-id="1efff-152">The debugger stops at the line in the background thread that attempted to write directly to the text box.</span></span> <span data-ttu-id="1efff-153">Je nutné restartovat aplikaci otestovat další dvě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="1efff-153">You will have to restart the application to test the other two buttons.</span></span> <span data-ttu-id="1efff-154">Když kliknete **bezpečné volat** tlačítko "Napsané pomocí hlavního vlákna" se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="1efff-154">When you click the **Safe Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="1efff-155">Později, dvou sekund textového pole je nastavena na "Written ve vlákně na pozadí (Invoke)", což znamená, že <xref:System.Windows.Forms.Control.Invoke%2A> byla volána metoda.</span><span class="sxs-lookup"><span data-stu-id="1efff-155">Two seconds later, the text box is set to "Written by the background thread (Invoke)", which indicates that the <xref:System.Windows.Forms.Control.Invoke%2A> method was called.</span></span> <span data-ttu-id="1efff-156">Když kliknete **bezpečné volat BW** tlačítko "Napsané pomocí hlavního vlákna" se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="1efff-156">When you click the **Safe BW Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="1efff-157">Později, dvou sekund textového pole je nastavena na "Written hlavní vlákno po dokončení vlákně na pozadí", což znamená, že obslužnou rutinu pro <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> události <xref:System.ComponentModel.BackgroundWorker> byla volána.</span><span class="sxs-lookup"><span data-stu-id="1efff-157">Two seconds later, the text box is set to "Written by the main thread after the background thread completed", which indicates that the handler for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event of <xref:System.ComponentModel.BackgroundWorker> was called.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1efff-158">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1efff-158">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1efff-159">Při použití více vláken jakéhokoli druhu, mohou být zpřístupněny kódu chyby velmi závažnou a komplexní.</span><span class="sxs-lookup"><span data-stu-id="1efff-159">When you use multithreading of any sort, your code can be exposed to very serious and complex bugs.</span></span> <span data-ttu-id="1efff-160">Další informace najdete v tématu [spravované dělení na vlákna osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací řešení, která používá více vláken.</span><span class="sxs-lookup"><span data-stu-id="1efff-160">For more information, see [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before you implement any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efff-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="1efff-161">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="1efff-162">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="1efff-162">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="1efff-163">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="1efff-163">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="1efff-164">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1efff-164">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="1efff-165">Model Windows Forms a nespravované aplikace</span><span class="sxs-lookup"><span data-stu-id="1efff-165">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
