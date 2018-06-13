---
title: 'Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: bd813d479cd4dfb61a08d9a8c4a4e7612084e878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532604"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek může zobrazit webové odkazy jako barevný a podtržený. Můžete napsat kód, který se otevře okno prohlížeče zobrazující Web zadaný text odkazu, při kliknutí na odkaz.  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Chcete-li odkaz na webovou stránku pomocí ovládacího prvku RichTextBox  
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost na řetězec, který obsahuje platnou adresu URL (například "http://www.microsoft.com/").  
  
2.  Zajistěte, aby <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> je nastavena na `true` (výchozí).  
  
3.  Vytvořit novou globální instanci <xref:System.Diagnostics.Process> objektu.  
  
4.  Zápis obslužné rutiny události pro <xref:System.Windows.Forms.RichTextBox.LinkClicked> událost, která se odešle do prohlížeče požadovaný text.  
  
     V následujícím příkladu <xref:System.Windows.Forms.RichTextBox.LinkClicked> událostí otevře instance Internet Exploreru, aby adresa URL zadaná v <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Tento příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.  
  
    > [!IMPORTANT]
    >  Ve volání <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metoda, se setkají <xref:System.Security.SecurityException> výjimka, pokud používáte kód v kontextu částečným vztahem důvěryhodnosti z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Musí inicializovat proces `p`, což lze provést tak, že začleníte následující příkaz v konstruktoru formuláře:  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     Je důležité okamžitě zastavit proces, který jste vytvořili po dokončení práce s ním. Odkazy na kód uvedený výše, kódu se zastavit proces může vypadat například takto:  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>  
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>  
 <xref:System.Windows.Forms.RichTextBox>  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
