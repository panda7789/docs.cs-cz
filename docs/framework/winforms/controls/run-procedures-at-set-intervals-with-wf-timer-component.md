---
title: Spustit procedury v nastavených intervalech s komponentou časovače
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
ms.openlocfilehash: 52d68a8136551384f67ff6232799600af09f8b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182048"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Postupy: Spouštění procedur v nastavených intervalech pomocí součásti Windows Forms Timer
Někdy můžete chtít vytvořit proceduru, která běží v určitých časových intervalech, dokud není smyčka dokončena nebo která se spustí po uplynutí nastaveného časového intervalu. Součást <xref:System.Windows.Forms.Timer> umožňuje takový postup.  
  
 Tato součást je určena pro prostředí windows forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, naleznete [v tématu Úvod do časovačů založených na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
> [!NOTE]
> Při použití komponenty existují <xref:System.Windows.Forms.Timer> určitá omezení. Další informace naleznete [v tématu Omezení vlastnosti Interval součásti časovače formulářů systému Windows](limitations-of-the-timer-component-interval-property.md).  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Spuštění procedury v nastavených intervalech s komponentou Timer  
  
1. Přidejte <xref:System.Windows.Forms.Timer> a do formuláře. Viz následující příklad části pro ilustraci, jak to udělat programově. Visual Studio má také podporu pro přidávání součástí do formuláře. Viz [také postup: Přidání ovládacích prvků bez uživatelského rozhraní do formulářů systému Windows](how-to-add-controls-without-a-user-interface-to-windows-forms.md).  
  
2. Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost (v milisekundách) pro časovač. Tato vlastnost určuje, kolik času uběhne před znovu spuštěním procedury.  
  
    > [!NOTE]
    > Čím častěji dojde k události časovače, tím více času procesoru se používá v reakci na událost. To může zpomalit celkový výkon. Nenastavovat menší interval, než potřebujete.  
  
3. Napište příslušný <xref:System.Windows.Forms.Timer.Tick> kód do obslužné rutiny události. Kód napíšete v této události bude spuštěn <xref:System.Windows.Forms.Timer.Interval%2A> v intervalu určeném ve vlastnosti.  
  
4. Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true` pro spuštění časovače. K <xref:System.Windows.Forms.Timer.Tick> události začne dojít a postup se spustí v nastaveném intervalu.  
  
5. Ve vhodnou dobu nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost, chcete-li `false` proceduru znovu spustit. Nastavení intervalu `0` na nezpůsobí zastavení časovače.  
  
## <a name="example"></a>Příklad  
 Tento první příklad kódu sleduje denní dobu v přírůstcích po jedné sekundě. Používá ve <xref:System.Windows.Forms.Button>formuláři <xref:System.Windows.Forms.Label>a <xref:System.Windows.Forms.Timer> , a komponentu. Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> je nastavena na 1000 (rovná se jedné sekundě). V <xref:System.Windows.Forms.Timer.Tick> případě, že popisek titulek je nastavena na aktuální čas. Po klepnutí na tlačítko <xref:System.Windows.Forms.Timer.Enabled%2A> je vlastnost `false`nastavena na , což zastaví časovač v aktualizaci titulku popisku. Následující příklad kódu vyžaduje, abyste měli <xref:System.Windows.Forms.Button> formulář `Button1`s <xref:System.Windows.Forms.Timer> názvem `Timer1`ovládacího <xref:System.Windows.Forms.Label> prvku `Label1`, ovládacím prvkem s názvem a ovládacím prvkem s názvem .  
  
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
 Tento druhý příklad kódu spustí proceduru každých 600 milisekund, dokud nebude smyčka dokončena. Následující příklad kódu vyžaduje, abyste měli <xref:System.Windows.Forms.Button> formulář `Button1`s <xref:System.Windows.Forms.Timer> názvem `Timer1`ovládacího <xref:System.Windows.Forms.Label> prvku `Label1`, ovládacím prvkem s názvem a ovládacím prvkem s názvem .  
  
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
- [Přehled součásti Časovač](timer-component-overview-windows-forms.md)
