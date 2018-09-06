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
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801700"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer
Někdy můžete chtít vytvořit proceduru, která běží v určitých časových intervalech, dokud dokončení smyčku nebo, který spustí po nastaveném časovém intervalu. <xref:System.Windows.Forms.Timer> Komponenta odešle takový postup je to možné.  
  
 Tato součást je určená pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
> [!NOTE]
>  Existují některá omezení při použití <xref:System.Windows.Forms.Timer> komponenty. Další informace najdete v tématu [omezení vlastnosti intervalu součásti serveru Windows Forms Timer](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Ke spuštění procedury v nastavených intervalech pomocí komponenty Timer  
  
1.  Přidat <xref:System.Windows.Forms.Timer> do formuláře. V části následující příklad pro ilustraci, jak to provést prostřednictvím kódu programu. Visual Studio také poskytuje podporu pro přidání součásti do formuláře. Viz také [postupy: Přidání ovládacích prvků bez uživatelské rozhraní Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).  
  
2.  Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost (v milisekundách) pro časovač. Tato vlastnost určuje, jak dlouho bude uplynout, než je znovu spusťte proces.  
  
    > [!NOTE]
    >  Čím častěji dochází k událost časovače, více procesorového času se používá při reagování na události. To může zpomalit výkon. Nenastavujte intervalem menší, než potřebujete.  
  
3.  Zápis odpovídající kód <xref:System.Windows.Forms.Timer.Tick> obslužné rutiny události. Kód, který píšete v tomto případě se spustí v intervalu určeném v <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost.  
  
4.  Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true` ke spuštění časovače. <xref:System.Windows.Forms.Timer.Tick> Událostí bude spuštěn pravděpodobnější, procedura v nastaveném intervalu.  
  
5.  V příslušnou dobu nastaven <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `false` zastavit proces spuštění znovu. Nastavení intervalu `0` nezpůsobí zastavit časovač.  
  
## <a name="example"></a>Příklad  
 Tento první příklad kódu zjišťuje čas v sekundách. Použije <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>a <xref:System.Windows.Forms.Timer> komponenty ve formuláři. <xref:System.Windows.Forms.Timer.Interval%2A> Je nastavena na 1000 (je rovno jedné sekundy). V <xref:System.Windows.Forms.Timer.Tick> událostí, titulek je nastavena na aktuální čas. Po kliknutí na tlačítko <xref:System.Windows.Forms.Timer.Enabled%2A> je nastavena na `false`, zastavení časovače aktualizace titulek. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.  
  
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
 Tento druhý příklad kódu spuštění procedury každých 600 milisekund až do dokončení smyčku. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.  
  
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
 <xref:System.Windows.Forms.Timer>  
 [Komponenta Timer](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Přehled komponenty Timer](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
