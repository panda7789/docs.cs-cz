---
title: Spouštění procedur v nastavených intervalech pomocí komponenty Timer
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
ms.openlocfilehash: dcc88beee947e2a83b426dcd2f3fd9d70c20fb67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743114"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer
Někdy můžete chtít vytvořit proceduru, která bude spuštěna v určitých časových intervalech, dokud se smyčka nedokončí nebo dokud se nespustí při uplynutí nastaveného časového intervalu. Komponenta <xref:System.Windows.Forms.Timer> provádí takový postup.  
  
 Tato součást je navržená pro model Windows Forms prostředí. Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
> [!NOTE]
> Při použití součásti <xref:System.Windows.Forms.Timer> je potřeba mít určitá omezení. Další informace najdete v tématu [omezení vlastnosti intervalů součásti časovače model Windows Forms](limitations-of-the-timer-component-interval-property.md).  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Spuštění procedury v nastavených intervalech pomocí komponenty Timer  
  
1. Přidejte <xref:System.Windows.Forms.Timer> do formuláře. V následujícím ukázkovém oddílu najdete ukázku toho, jak to provést programově. Visual Studio také podporuje přidávání součástí do formuláře. Viz také [Postupy: Přidání ovládacích prvků bez uživatelského rozhraní pro model Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> (v milisekundách) pro časovač. Tato vlastnost určuje, kolik času bude před opakováním postupu probíhat znovu.  
  
    > [!NOTE]
    > Častěji dojde k události časovače, při reagování na událost se používá více procesorového času. To může zpomalit celkový výkon. Nenastavte kratší interval, než kolik potřebujete.  
  
3. V obslužné rutině události <xref:System.Windows.Forms.Timer.Tick> napište příslušný kód. Kód, který zadáte do této události, se spustí v intervalu zadaném ve vlastnosti <xref:System.Windows.Forms.Timer.Interval%2A>.  
  
4. Nastavte vlastnost <xref:System.Windows.Forms.Timer.Enabled%2A> na `true` pro spuštění časovače. Spustí se událost <xref:System.Windows.Forms.Timer.Tick> a spustí se procedura v nastaveném intervalu.  
  
5. Ve stanovenou dobu nastavte vlastnost <xref:System.Windows.Forms.Timer.Enabled%2A> na `false`, aby se zastavil postup znovu spustit. Nastavení intervalu pro `0` nezpůsobí zastavení časovače.  
  
## <a name="example"></a>Příklad  
 Tento první příklad kódu sleduje denní dobu v přírůstcích po jednom sekundě. Používá <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>a <xref:System.Windows.Forms.Timer> komponentu na formuláři. Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> je nastavena na 1000 (je rovna jedné sekundě). V události <xref:System.Windows.Forms.Timer.Tick> je popisek popisku nastaven na aktuální čas. Po kliknutí na tlačítko je vlastnost <xref:System.Windows.Forms.Timer.Enabled%2A> nastavena na hodnotu `false`a zastavuje časovač z aktualizace titulku popisku. Následující příklad kódu vyžaduje, abyste měli formulář s ovládacím prvkem <xref:System.Windows.Forms.Button> nazvaný `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.  
  
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
  
## <a name="example"></a>Příklad  
 Tento druhý příklad kódu spouští proceduru každých 600 milisekund, dokud se smyčka nedokončí. Následující příklad kódu vyžaduje, abyste měli formulář s ovládacím prvkem <xref:System.Windows.Forms.Button> nazvaný `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Timer>
- [Komponenta Timer](timer-component-windows-forms.md)
- [Přehled komponenty Timer](timer-component-overview-windows-forms.md)
