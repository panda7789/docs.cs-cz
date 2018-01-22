---
title: "Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62cb416b311fd3c2c29f8ffc7c513fa6a9dfd8fe
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="eff09-102">Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="eff09-102">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="eff09-103">V některých případech můžete chtít vytvořit proceduru, který se spustí na konkrétní časové intervaly, dokud smyčku dokončil nebo který bude spuštěn po uplynutí časového intervalu sady.</span><span class="sxs-lookup"><span data-stu-id="eff09-103">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="eff09-104"><xref:System.Windows.Forms.Timer> Součást umožňuje tento postup.</span><span class="sxs-lookup"><span data-stu-id="eff09-104">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="eff09-105">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="eff09-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="eff09-106">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="eff09-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eff09-107">Existují určitá omezení při použití <xref:System.Windows.Forms.Timer> součásti.</span><span class="sxs-lookup"><span data-stu-id="eff09-107">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="eff09-108">Další informace najdete v tématu [omezení vlastnosti intervalu součásti serveru Windows Forms Timer](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span><span class="sxs-lookup"><span data-stu-id="eff09-108">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span></span>  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="eff09-109">Chcete-li spustit proceduru v nastavených intervalech pomocí součásti časovač</span><span class="sxs-lookup"><span data-stu-id="eff09-109">To run a procedure at set intervals with the Timer component</span></span>  
  
1.  <span data-ttu-id="eff09-110">Přidat <xref:System.Windows.Forms.Timer> do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="eff09-110">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="eff09-111">Najdete v následující části Příklad obrázek o tom, jak to provést prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="eff09-111">See the following Example section for an illustration of how to do this programmatically.</span></span> [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]<span data-ttu-id="eff09-112">má také podpora pro přidávání součástí do formuláře.</span><span class="sxs-lookup"><span data-stu-id="eff09-112"> also has support for adding components to a form.</span></span> <span data-ttu-id="eff09-113">Viz také [postupy: Přidání ovládacích prvků bez uživatelské rozhraní pro Windows Forms](http://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="eff09-113">Also see [How to: Add Controls Without a User Interface to Windows Forms](http://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span></span>  
  
2.  <span data-ttu-id="eff09-114">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost (v milisekundách) pro časovač.</span><span class="sxs-lookup"><span data-stu-id="eff09-114">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="eff09-115">Tato vlastnost určuje, jak dlouho bude uplynout, než je postup spustit znovu.</span><span class="sxs-lookup"><span data-stu-id="eff09-115">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eff09-116">Čím víc často dochází k událost časovače, reagovat na událost se používá víc času procesoru.</span><span class="sxs-lookup"><span data-stu-id="eff09-116">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="eff09-117">To může zpomalit celkový výkon.</span><span class="sxs-lookup"><span data-stu-id="eff09-117">This can slow down overall performance.</span></span> <span data-ttu-id="eff09-118">Nenastavujte intervalu menší, než budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="eff09-118">Do not set a smaller interval than you need.</span></span>  
  
3.  <span data-ttu-id="eff09-119">Napsat odpovídající kód <xref:System.Windows.Forms.Timer.Tick> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="eff09-119">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="eff09-120">Kód, který vytváříte v tomto případě se spustí v intervalu zadaném v <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eff09-120">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4.  <span data-ttu-id="eff09-121">Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true` spustit časovač.</span><span class="sxs-lookup"><span data-stu-id="eff09-121">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="eff09-122"><xref:System.Windows.Forms.Timer.Tick> Událostí bude spuštěn proběhnout, procedura v intervalu sady.</span><span class="sxs-lookup"><span data-stu-id="eff09-122">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5.  <span data-ttu-id="eff09-123">V příslušnou dobu nastavena <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `false` zastavení procesu z znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="eff09-123">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="eff09-124">Nastavení intervalu `0` nezpůsobí časovač zastavit.</span><span class="sxs-lookup"><span data-stu-id="eff09-124">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff09-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff09-125">Example</span></span>  
 <span data-ttu-id="eff09-126">Tento první příklad kódu sleduje čas, kdy v přírůstcích po jednu sekundu.</span><span class="sxs-lookup"><span data-stu-id="eff09-126">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="eff09-127">Použije <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>a <xref:System.Windows.Forms.Timer> součásti ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="eff09-127">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="eff09-128"><xref:System.Windows.Forms.Timer.Interval%2A> Je nastavena na 1000 (rovno 1 sekunda).</span><span class="sxs-lookup"><span data-stu-id="eff09-128">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="eff09-129">V <xref:System.Windows.Forms.Timer.Tick> událostí, popisek popisek nastavena na aktuální čas.</span><span class="sxs-lookup"><span data-stu-id="eff09-129">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="eff09-130">Při kliknutí na tlačítko <xref:System.Windows.Forms.Timer.Enabled%2A> je nastavena na `false`, časovač z aktualizace popisek popisek.</span><span class="sxs-lookup"><span data-stu-id="eff09-130">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="eff09-131">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.</span><span class="sxs-lookup"><span data-stu-id="eff09-131">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="eff09-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff09-132">Example</span></span>  
 <span data-ttu-id="eff09-133">Tento druhý ukázkový kód spustí procedury každých 600 milisekund dokud nedokončí smyčku.</span><span class="sxs-lookup"><span data-stu-id="eff09-133">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="eff09-134">Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.</span><span class="sxs-lookup"><span data-stu-id="eff09-134">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eff09-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="eff09-135">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="eff09-136">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="eff09-136">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="eff09-137">Přehled komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="eff09-137">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
