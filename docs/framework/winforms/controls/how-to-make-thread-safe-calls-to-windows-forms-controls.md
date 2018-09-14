---
title: 'Postupy: Volání (s bezpečným vlákny) ovládacích prvků Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: f2716db441380138e6058ec45d9ae9c07f0e21a7
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527081"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="5f23e-102">Postupy: Volání (s bezpečným vlákny) ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5f23e-102">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>

<span data-ttu-id="5f23e-103">Pokud používáte multithreading můžete zvýšit výkon vašich aplikací Windows Forms, je nutné provést volání k ovládacím prvkům způsobem bezpečným pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="5f23e-103">If you use multithreading to improve the performance of your Windows Forms applications, you must make sure that you make calls to your controls in a thread-safe way.</span></span>

<span data-ttu-id="5f23e-104">Přístup k ovládacím prvkům Windows Forms není ze své podstaty bezpečné pro vlákna.</span><span class="sxs-lookup"><span data-stu-id="5f23e-104">Access to Windows Forms controls is not inherently thread safe.</span></span> <span data-ttu-id="5f23e-105">Pokud máte dva nebo více podprocesů manipulaci se stavem ovládacího prvku, je možné vynutit ovládacího prvku do nekonzistentního stavu.</span><span class="sxs-lookup"><span data-stu-id="5f23e-105">If you have two or more threads manipulating the state of a control, it is possible to force the control into an inconsistent state.</span></span> <span data-ttu-id="5f23e-106">Jiné chyby související vlákna je možné, například ke konfliktům časování a zablokování.</span><span class="sxs-lookup"><span data-stu-id="5f23e-106">Other thread-related bugs are possible, such as race conditions and deadlocks.</span></span> <span data-ttu-id="5f23e-107">Je důležité, abyste měli jistotu, že se provádí přístup k ovládacím prvkům způsobem bezpečným pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="5f23e-107">It is important to make sure that access to your controls is performed in a thread-safe way.</span></span>

<span data-ttu-id="5f23e-108">Není bezpečné volat z vlákna, než je ten, který vytváří ovládací prvek bez použití ovládacího prvku <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5f23e-108">It is unsafe to call a control from a thread other than the one that created the control without using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="5f23e-109">Následuje příklad, který není bezpečné pro vlákna volání.</span><span class="sxs-lookup"><span data-stu-id="5f23e-109">The following is an example of a call that is not thread safe.</span></span>

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

<span data-ttu-id="5f23e-110">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Pomůže vám rozpoznat, kdy přistupujete ovládacích prvků v podobě, která není bezpečné pro vlákna.</span><span class="sxs-lookup"><span data-stu-id="5f23e-110">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] helps you detect when you are accessing your controls in a manner that is not thread safe.</span></span> <span data-ttu-id="5f23e-111">Pokud vaše aplikace běží v ladicím programu a vlákna, než je ten, který vytvoří ovládací prvek se pokusí zavolat, že ovládací prvek, ladicí program vyvolá <xref:System.InvalidOperationException> s touto zprávou "ovládací prvek *název ovládacího prvku* k němu přistupovat z vlákna kromě vlákna, který byl vytvořen."</span><span class="sxs-lookup"><span data-stu-id="5f23e-111">When you are running your application in the debugger, and a thread other than the one which created a control tries to call that control, the debugger raises an <xref:System.InvalidOperationException> with the message, "Control *control name* accessed from a thread other than the thread it was created on."</span></span>

<span data-ttu-id="5f23e-112">Tato dojde k výjimce spolehlivě během ladění a za určitých okolností v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5f23e-112">This exception occurs reliably during debugging and, under some circumstances, at run time.</span></span> <span data-ttu-id="5f23e-113">Může se zobrazit tato výjimka při ladění aplikace, které jste naprogramovali proto, že se [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] před verzí [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f23e-113">You might see this exception when you debug applications that you wrote with the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] prior to the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="5f23e-114">Důrazně doporučujeme tento problém vyřešit, když se zobrazí, ale můžete jej zakázat nastavením <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="5f23e-114">You are strongly advised to fix this problem when you see it, but you can disable it by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> property to `false`.</span></span> <span data-ttu-id="5f23e-115">To způsobí, že ovládací prvek spustit jako bude spuštěná v aplikaci Visual Studio .NET 2003 a [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f23e-115">This causes your control to run like it would run under Visual Studio .NET 2003 and the [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="5f23e-116">Pokud používáte ovládací prvky ActiveX ve formuláři, může se zobrazit mezi vlákny <xref:System.InvalidOperationException> při spuštění v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="5f23e-116">If you are using ActiveX controls on a form, you may receive the cross-thread <xref:System.InvalidOperationException> when you run under the debugger.</span></span> <span data-ttu-id="5f23e-117">V tomto případě nepodporuje ovládací prvek ActiveX multithreadingu.</span><span class="sxs-lookup"><span data-stu-id="5f23e-117">When this occurs, the ActiveX control does not support multithreading.</span></span> <span data-ttu-id="5f23e-118">Další informace o použití pomocí Windows Forms – ovládací prvky ActiveX naleznete v tématu [Windows Forms a nespravované aplikace](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md).</span><span class="sxs-lookup"><span data-stu-id="5f23e-118">For more information about using ActiveX controls with Windows Forms, see [Windows Forms and Unmanaged Applications](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md).</span></span>

## <a name="making-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="5f23e-119">Ovládací prvky bezpečné pro vlákna volání do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5f23e-119">Making Thread-Safe Calls to Windows Forms Controls</span></span>

### <a name="to-make-a-thread-safe-call-to-a-windows-forms-control"></a><span data-ttu-id="5f23e-120">Chcete-li bezpečné pro vlákna volání ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5f23e-120">To make a thread-safe call to a Windows Forms control</span></span>

1.  <span data-ttu-id="5f23e-121">Dotazování ovládacího prvku <xref:System.Windows.Forms.Control.InvokeRequired%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f23e-121">Query the control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> property.</span></span>

2.  <span data-ttu-id="5f23e-122">Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true`, volání <xref:System.Windows.Forms.Control.Invoke%2A> delegátem, která provádí skutečné volání do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5f23e-122">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, call <xref:System.Windows.Forms.Control.Invoke%2A> with a delegate that makes the actual call to the control.</span></span>

3.  <span data-ttu-id="5f23e-123">Pokud <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `false`, ovládací prvek volat přímo.</span><span class="sxs-lookup"><span data-stu-id="5f23e-123">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, call the control directly.</span></span>

<span data-ttu-id="5f23e-124">V následujícím příkladu kódu je bezpečné pro vlákna volání implementované v `ThreadProcSafe` metodu, která provádí ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5f23e-124">In the following code example, a thread-safe call is implemented in the `ThreadProcSafe` method, which is executed by the background thread.</span></span> <span data-ttu-id="5f23e-125">Pokud <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.Control.InvokeRequired%2A> vrátí `true`, `ThreadProcSafe` metoda vytvoří instanci `StringArgReturningVoidDelegate` a, který předá do formuláře <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5f23e-125">If the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, the `ThreadProcSafe` method creates an instance of `StringArgReturningVoidDelegate` and passes that to the form's <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="5f23e-126">To způsobí, že `SetText` metoda k volání na vlákno, které vytvořili <xref:System.Windows.Forms.TextBox> ovládacího prvku a v tomto kontextu vlákna <xref:System.Windows.Forms.Control.Text%2A> vlastnost nastavena přímo.</span><span class="sxs-lookup"><span data-stu-id="5f23e-126">This causes the `SetText` method to be called on the thread that created the <xref:System.Windows.Forms.TextBox> control, and in this thread context the <xref:System.Windows.Forms.Control.Text%2A> property is set directly.</span></span>

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

## <a name="making-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="5f23e-127">Bezpečné pro vlákna volání pomocí podproces BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="5f23e-127">Making Thread-Safe Calls by using BackgroundWorker</span></span>
 <span data-ttu-id="5f23e-128">Preferovaný způsob, jak implementovat multithreadingu ve vaší aplikaci, je použít <xref:System.ComponentModel.BackgroundWorker> komponenty.</span><span class="sxs-lookup"><span data-stu-id="5f23e-128">The preferred way to implement multithreading in your application is to use the <xref:System.ComponentModel.BackgroundWorker> component.</span></span> <span data-ttu-id="5f23e-129"><xref:System.ComponentModel.BackgroundWorker> Komponenty používá model založený na událostech pro multithreading.</span><span class="sxs-lookup"><span data-stu-id="5f23e-129">The <xref:System.ComponentModel.BackgroundWorker> component uses an event-driven model for multithreading.</span></span> <span data-ttu-id="5f23e-130">Vlákno na pozadí spouští vaše <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužná rutina události a vlákna, které vytvoří spuštěních ovládací prvky vaší <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="5f23e-130">The background thread runs your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, and the thread that creates your controls runs your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span> <span data-ttu-id="5f23e-131">Můžete volat své ovládací prvky z vašich <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="5f23e-131">You can call your controls from your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span>

#### <a name="to-make-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="5f23e-132">Pro bezpečné pro vlákna volání pomocí podproces BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="5f23e-132">To make thread-safe calls by using BackgroundWorker</span></span>

1.  <span data-ttu-id="5f23e-133">Vytvoření metody pro práci, která se má provést ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5f23e-133">Create a method to do the work that you want done in the background thread.</span></span> <span data-ttu-id="5f23e-134">Nevolejte ovládací prvky vytvořené pomocí hlavního vlákna v této metodě.</span><span class="sxs-lookup"><span data-stu-id="5f23e-134">Do not call controls created by the main thread in this method.</span></span>

2.  <span data-ttu-id="5f23e-135">Vytvořte metodu ke sestavy o výsledcích práce na pozadí po jejím dokončení.</span><span class="sxs-lookup"><span data-stu-id="5f23e-135">Create a method to report the results of your background work after it finishes.</span></span> <span data-ttu-id="5f23e-136">Můžete volat ovládací prvky vytvořené pomocí hlavního vlákna v této metodě.</span><span class="sxs-lookup"><span data-stu-id="5f23e-136">You can call controls created by the main thread in this method.</span></span>

3.  <span data-ttu-id="5f23e-137">BIND – metoda vytvořené v kroku 1, a <xref:System.ComponentModel.BackgroundWorker.DoWork> události instance <xref:System.ComponentModel.BackgroundWorker>a vytvořit vazbu metoda vytvořili v kroku 2 na stejnou instanci <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="5f23e-137">Bind the method created in step 1 to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event of an instance of <xref:System.ComponentModel.BackgroundWorker>, and bind the method created in step 2 to the same instance’s <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>

4.  <span data-ttu-id="5f23e-138">Chcete-li spustit vlákno na pozadí, zavolejte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu <xref:System.ComponentModel.BackgroundWorker> instance.</span><span class="sxs-lookup"><span data-stu-id="5f23e-138">To start the background thread, call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of the <xref:System.ComponentModel.BackgroundWorker> instance.</span></span>

<span data-ttu-id="5f23e-139">V následujícím příkladu kódu <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužná rutina události používá <xref:System.Threading.Thread.Sleep%2A> simulace práce, která se nějakou dobu trvá.</span><span class="sxs-lookup"><span data-stu-id="5f23e-139">In the following code example, the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler uses <xref:System.Threading.Thread.Sleep%2A> to simulate work that takes some time.</span></span> <span data-ttu-id="5f23e-140">Nevolá formuláře <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5f23e-140">It does not call the form’s <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="5f23e-141"><xref:System.Windows.Forms.TextBox> Ovládacího prvku <xref:System.Windows.Forms.Control.Text%2A> je vlastnost nastavena přímo v <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="5f23e-141">The <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.Text%2A> property is set directly in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

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

 <span data-ttu-id="5f23e-142">Průběh úlohy na pozadí můžete nahlásit také pomocí <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="5f23e-142">You can also report the progress of a background task by using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="5f23e-143">Příklad, který zahrnuje tuto událost, naleznete v tématu <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="5f23e-143">For an example that incorporates that event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span>

## <a name="example"></a><span data-ttu-id="5f23e-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f23e-144">Example</span></span>
 <span data-ttu-id="5f23e-145">Následující příklad kódu je dokončené aplikace Windows Forms, který se skládá z formuláře s tři tlačítka a textová pole.</span><span class="sxs-lookup"><span data-stu-id="5f23e-145">The following code example is a complete Windows Forms application that consists of a form with three buttons and one text box.</span></span> <span data-ttu-id="5f23e-146">Ukazuje na první tlačítko nezabezpečený přístup mezi vlákny, druhé tlačítko ukazuje bezpečný přístup s použitím <xref:System.Windows.Forms.Control.Invoke%2A>, a na třetí tlačítko ukazuje bezpečný přístup s použitím <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="5f23e-146">The first button demonstrates unsafe cross-thread access, the second button demonstrates safe access by using <xref:System.Windows.Forms.Control.Invoke%2A>, and the third button demonstrates safe access by using <xref:System.ComponentModel.BackgroundWorker>.</span></span>

> [!NOTE]
> <span data-ttu-id="5f23e-147">Pokyny o tom, jak spustit v příkladu najdete v tématu [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416).</span><span class="sxs-lookup"><span data-stu-id="5f23e-147">For instructions on how to run the example, see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416).</span></span> <span data-ttu-id="5f23e-148">Tento příklad vyžaduje odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5f23e-148">This example requires references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

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

<span data-ttu-id="5f23e-149">Při spuštění aplikace a klikněte na tlačítko **nebezpečné volat** tlačítko, můžete okamžitě naleznete v tématu "Written pomocí hlavního vlákna" v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="5f23e-149">When you run the application and click the **Unsafe Call** button, you immediately see "Written by the main thread" in the text box.</span></span> <span data-ttu-id="5f23e-150">Dvou sekund později, když nebezpečné volání dojde k pokusu o, ladicího programu sady Visual Studio znamená, že došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="5f23e-150">Two seconds later, when the unsafe call is attempted, the Visual Studio debugger indicates that an exception occurred.</span></span> <span data-ttu-id="5f23e-151">Ladicí program se zastaví na řádku ve vlákně na pozadí, která se pokusila zapisovat přímo do textového pole.</span><span class="sxs-lookup"><span data-stu-id="5f23e-151">The debugger stops at the line in the background thread that attempted to write directly to the text box.</span></span> <span data-ttu-id="5f23e-152">Budete muset restartovat aplikaci k testování dvě tlačítka.</span><span class="sxs-lookup"><span data-stu-id="5f23e-152">You will have to restart the application to test the other two buttons.</span></span> <span data-ttu-id="5f23e-153">Když kliknete **bezpečné volat** tlačítko, "Zapsaných pomocí hlavního vlákna" se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="5f23e-153">When you click the **Safe Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="5f23e-154">Do textového pole dvou sekund později, je nastavena na "Written ve vlákně na pozadí (Invoke)", což znamená, že <xref:System.Windows.Forms.Control.Invoke%2A> byla volána metoda.</span><span class="sxs-lookup"><span data-stu-id="5f23e-154">Two seconds later, the text box is set to "Written by the background thread (Invoke)", which indicates that the <xref:System.Windows.Forms.Control.Invoke%2A> method was called.</span></span> <span data-ttu-id="5f23e-155">Když kliknete **bezpečné volat BW** tlačítko, "Zapsaných pomocí hlavního vlákna" se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="5f23e-155">When you click the **Safe BW Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="5f23e-156">Do textového pole dvou sekund později, je nastavena na "Written hlavní vlákno po vlákně na pozadí dokončení", což znamená, že obslužné rutiny pro <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událost <xref:System.ComponentModel.BackgroundWorker> byla volána.</span><span class="sxs-lookup"><span data-stu-id="5f23e-156">Two seconds later, the text box is set to "Written by the main thread after the background thread completed", which indicates that the handler for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event of <xref:System.ComponentModel.BackgroundWorker> was called.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="5f23e-157">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="5f23e-157">Robust Programming</span></span>

> [!CAUTION]
> <span data-ttu-id="5f23e-158">Pokud používáte multithreading jakéhokoli druhu, váš kód může být vystavena velmi závažných a složitých chyb.</span><span class="sxs-lookup"><span data-stu-id="5f23e-158">When you use multithreading of any sort, your code can be exposed to very serious and complex bugs.</span></span> <span data-ttu-id="5f23e-159">Další informace najdete v tématu [spravovaných vláken osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací jakéhokoli řešení, které používá multithreadingu.</span><span class="sxs-lookup"><span data-stu-id="5f23e-159">For more information, see [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before you implement any solution that uses multithreading.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f23e-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f23e-160">See Also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="5f23e-161">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="5f23e-161">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="5f23e-162">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="5f23e-162">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="5f23e-163">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5f23e-163">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="5f23e-164">Model Windows Forms a nespravované aplikace</span><span class="sxs-lookup"><span data-stu-id="5f23e-164">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
