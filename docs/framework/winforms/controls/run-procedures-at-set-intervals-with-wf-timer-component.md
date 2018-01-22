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
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer
V některých případech můžete chtít vytvořit proceduru, který se spustí na konkrétní časové intervaly, dokud smyčku dokončil nebo který bude spuštěn po uplynutí časového intervalu sady. <xref:System.Windows.Forms.Timer> Součást umožňuje tento postup.  
  
 Tato součást je určená pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
> [!NOTE]
>  Existují určitá omezení při použití <xref:System.Windows.Forms.Timer> součásti. Další informace najdete v tématu [omezení vlastnosti intervalu součásti serveru Windows Forms Timer](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Chcete-li spustit proceduru v nastavených intervalech pomocí součásti časovač  
  
1.  Přidat <xref:System.Windows.Forms.Timer> do svého formuláře. Najdete v následující části Příklad obrázek o tom, jak to provést prostřednictvím kódu programu. [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]má také podpora pro přidávání součástí do formuláře. Viz také [postupy: Přidání ovládacích prvků bez uživatelské rozhraní pro Windows Forms](http://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).  
  
2.  Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost (v milisekundách) pro časovač. Tato vlastnost určuje, jak dlouho bude uplynout, než je postup spustit znovu.  
  
    > [!NOTE]
    >  Čím víc často dochází k událost časovače, reagovat na událost se používá víc času procesoru. To může zpomalit celkový výkon. Nenastavujte intervalu menší, než budete potřebovat.  
  
3.  Napsat odpovídající kód <xref:System.Windows.Forms.Timer.Tick> obslužné rutiny události. Kód, který vytváříte v tomto případě se spustí v intervalu zadaném v <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost.  
  
4.  Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true` spustit časovač. <xref:System.Windows.Forms.Timer.Tick> Událostí bude spuštěn proběhnout, procedura v intervalu sady.  
  
5.  V příslušnou dobu nastavena <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `false` zastavení procesu z znovu spustit. Nastavení intervalu `0` nezpůsobí časovač zastavit.  
  
## <a name="example"></a>Příklad  
 Tento první příklad kódu sleduje čas, kdy v přírůstcích po jednu sekundu. Použije <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>a <xref:System.Windows.Forms.Timer> součásti ve formuláři. <xref:System.Windows.Forms.Timer.Interval%2A> Je nastavena na 1000 (rovno 1 sekunda). V <xref:System.Windows.Forms.Timer.Tick> událostí, popisek popisek nastavena na aktuální čas. Při kliknutí na tlačítko <xref:System.Windows.Forms.Timer.Enabled%2A> je nastavena na `false`, časovač z aktualizace popisek popisek. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.  
  
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
 Tento druhý ukázkový kód spustí procedury každých 600 milisekund dokud nedokončí smyčku. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1`, <xref:System.Windows.Forms.Timer> ovládací prvek s názvem `Timer1`a <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1`.  
  
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
