---
title: 'Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: bf0e22eab3b6517521dbe06a73f63af232746df1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529004"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="dd2cc-102">Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="dd2cc-102">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="dd2cc-103">Někdy můžete chtít vytvořit proceduru, která běží v určitých časových intervalech, dokud dokončení smyčku nebo, který spustí po nastaveném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-103">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="dd2cc-104"><xref:System.Windows.Forms.Timer> Komponenta odešle takový postup je to možné.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-104">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="dd2cc-105">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="dd2cc-106">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="dd2cc-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd2cc-107">Existují některá omezení při použití <xref:System.Windows.Forms.Timer> komponenty.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-107">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="dd2cc-108">Další informace najdete v tématu [omezení vlastnosti intervalu součásti serveru Windows Forms Timer](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span><span class="sxs-lookup"><span data-stu-id="dd2cc-108">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span></span>  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="dd2cc-109">Ke spuštění procedury v nastavených intervalech pomocí komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="dd2cc-109">To run a procedure at set intervals with the Timer component</span></span>  
  
1.  <span data-ttu-id="dd2cc-110">Přidat <xref:System.Windows.Forms.Timer> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-110">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="dd2cc-111">V části následující příklad pro ilustraci, jak to provést prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-111">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="dd2cc-112">Visual Studio také poskytuje podporu pro přidání součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-112">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="dd2cc-113">Viz také [postupy: Přidání ovládacích prvků bez uživatelské rozhraní Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="dd2cc-113">Also see [How to: Add Controls Without a User Interface to Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span></span>  
  
2.  <span data-ttu-id="dd2cc-114">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost (v milisekundách) pro časovač.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-114">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="dd2cc-115">Tato vlastnost určuje, jak dlouho bude uplynout, než je znovu spusťte proces.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-115">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd2cc-116">Čím častěji dochází k událost časovače, více procesorového času se používá při reagování na události.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-116">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="dd2cc-117">To může zpomalit výkon.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-117">This can slow down overall performance.</span></span> <span data-ttu-id="dd2cc-118">Nenastavujte intervalem menší, než potřebujete.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-118">Do not set a smaller interval than you need.</span></span>  
  
3.  <span data-ttu-id="dd2cc-119">Zápis odpovídající kód <xref:System.Windows.Forms.Timer.Tick> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-119">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="dd2cc-120">Kód, který píšete v tomto případě se spustí v intervalu určeném v <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-120">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4.  <span data-ttu-id="dd2cc-121">Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true` ke spuštění časovače.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-121">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="dd2cc-122"><xref:System.Windows.Forms.Timer.Tick> Událostí bude spuštěn pravděpodobnější, procedura v nastaveném intervalu.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-122">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5.  <span data-ttu-id="dd2cc-123">V příslušnou dobu nastaven <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `false` zastavit proces spuštění znovu.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-123">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="dd2cc-124">Nastavení intervalu `0` nezpůsobí zastavit časovač.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-124">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd2cc-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd2cc-125">Example</span></span>  
 <span data-ttu-id="dd2cc-126">Tento první příklad kódu zjišťuje čas v sekundách.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-126">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="dd2cc-127">Použije <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>a <xref:System.Windows.Forms.Timer> komponenty ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-127">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="dd2cc-128"><xref:System.Windows.Forms.Timer.Interval%2A> Je nastavena na 1000 (je rovno jedné sekundy).</span><span class="sxs-lookup"><span data-stu-id="dd2cc-128">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="dd2cc-129">V <xref:System.Windows.Forms.Timer.Tick> událostí, titulek je nastavena na aktuální čas.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-129">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="dd2cc-130">Po kliknutí na tlačítko <xref:System.Windows.Forms.Timer.Enabled%2A> je nastavena na `false`, zastavení časovače aktualizace titulek.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-130">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="dd2cc-131">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-131">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a><span data-ttu-id="dd2cc-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd2cc-132">Example</span></span>  
 <span data-ttu-id="dd2cc-133">Tento druhý příklad kódu spuštění procedury každých 600 milisekund až do dokončení smyčku.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-133">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="dd2cc-134">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.</span><span class="sxs-lookup"><span data-stu-id="dd2cc-134">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd2cc-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd2cc-135">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="dd2cc-136">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="dd2cc-136">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="dd2cc-137">Přehled komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="dd2cc-137">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
