---
title: Spouštění procedur v nastavených intervalech pomocí komponenty Timer
description: Naučte se, jak používat komponentu časovače formuláře Windows ke spouštění procedur v nastavených intervalech nebo při uplynutí nastaveného časového intervalu.
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
ms.openlocfilehash: 6847819fcec98d01d38b8e44604a259f06be7c02
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325763"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="b9b3e-103">Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="b9b3e-103">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="b9b3e-104">Někdy můžete chtít vytvořit proceduru, která bude spuštěna v určitých časových intervalech, dokud se smyčka nedokončí nebo dokud se nespustí při uplynutí nastaveného časového intervalu.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-104">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="b9b3e-105"><xref:System.Windows.Forms.Timer>Tato součást provádí takový postup.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-105">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="b9b3e-106">Tato součást je navržená pro model Windows Forms prostředí.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-106">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="b9b3e-107">Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b9b3e-107">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9b3e-108">Při použití komponenty existují určitá omezení <xref:System.Windows.Forms.Timer> .</span><span class="sxs-lookup"><span data-stu-id="b9b3e-108">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="b9b3e-109">Další informace najdete v tématu [omezení vlastnosti intervalů součásti časovače model Windows Forms](limitations-of-the-timer-component-interval-property.md).</span><span class="sxs-lookup"><span data-stu-id="b9b3e-109">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](limitations-of-the-timer-component-interval-property.md).</span></span>  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="b9b3e-110">Spuštění procedury v nastavených intervalech pomocí komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="b9b3e-110">To run a procedure at set intervals with the Timer component</span></span>  
  
1. <span data-ttu-id="b9b3e-111">Přidejte <xref:System.Windows.Forms.Timer> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-111">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="b9b3e-112">V následujícím ukázkovém oddílu najdete ukázku toho, jak to provést programově.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-112">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="b9b3e-113">Visual Studio také podporuje přidávání součástí do formuláře.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-113">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="b9b3e-114">Viz také [Postupy: Přidání ovládacích prvků bez uživatelského rozhraní pro model Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b9b3e-114">Also see [How to: Add Controls Without a User Interface to Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="b9b3e-115">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost (v milisekundách) pro časovač.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-115">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="b9b3e-116">Tato vlastnost určuje, kolik času bude před opakováním postupu probíhat znovu.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-116">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b9b3e-117">Častěji dojde k události časovače, při reagování na událost se používá více procesorového času.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-117">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="b9b3e-118">To může zpomalit celkový výkon.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-118">This can slow down overall performance.</span></span> <span data-ttu-id="b9b3e-119">Nenastavte kratší interval, než kolik potřebujete.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-119">Do not set a smaller interval than you need.</span></span>  
  
3. <span data-ttu-id="b9b3e-120">V <xref:System.Windows.Forms.Timer.Tick> obslužné rutině události napište příslušný kód.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-120">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="b9b3e-121">Kód, který zapíšete do této události, bude spuštěn v intervalu zadaném ve <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-121">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4. <span data-ttu-id="b9b3e-122">Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost na hodnotu `true` pro spuštění časovače.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-122">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="b9b3e-123">Dojde <xref:System.Windows.Forms.Timer.Tick> k zahájení události a spustí se procedura v nastaveném intervalu.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-123">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5. <span data-ttu-id="b9b3e-124">Ve vhodné době nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost na hodnotu `false` pro zastavení spuštění procedury.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-124">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="b9b3e-125">Nastavení intervalu `0` nezpůsobí zastavení časovače.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-125">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9b3e-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9b3e-126">Example</span></span>  
 <span data-ttu-id="b9b3e-127">Tento první příklad kódu sleduje denní dobu v přírůstcích po jednom sekundě.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-127">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="b9b3e-128">Používá <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Label> komponentu, a a <xref:System.Windows.Forms.Timer> na formuláři.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-128">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="b9b3e-129"><xref:System.Windows.Forms.Timer.Interval%2A>Vlastnost je nastavena na 1000 (je rovna jedné sekundě).</span><span class="sxs-lookup"><span data-stu-id="b9b3e-129">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="b9b3e-130">V <xref:System.Windows.Forms.Timer.Tick> případě je titulek popisku nastaven na aktuální čas.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-130">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="b9b3e-131">Po kliknutí na tlačítko <xref:System.Windows.Forms.Timer.Enabled%2A> je vlastnost nastavena na hodnotu `false` a zastavením časovače z aktualizace titulku popisku.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-131">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="b9b3e-132">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládacím prvkem s názvem `Button1` , <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1` a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1` .</span><span class="sxs-lookup"><span data-stu-id="b9b3e-132">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b9b3e-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9b3e-133">Example</span></span>  
 <span data-ttu-id="b9b3e-134">Tento druhý příklad kódu spouští proceduru každých 600 milisekund, dokud se smyčka nedokončí.</span><span class="sxs-lookup"><span data-stu-id="b9b3e-134">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="b9b3e-135">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládacím prvkem s názvem `Button1` , <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1` a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1` .</span><span class="sxs-lookup"><span data-stu-id="b9b3e-135">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9b3e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9b3e-136">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="b9b3e-137">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="b9b3e-137">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="b9b3e-138">Přehled součásti Časovač</span><span class="sxs-lookup"><span data-stu-id="b9b3e-138">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
