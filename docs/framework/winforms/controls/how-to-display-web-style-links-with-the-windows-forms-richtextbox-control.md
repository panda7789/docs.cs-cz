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
ms.openlocfilehash: ce71981f7b233d3e168689c766128646eed3e981
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046189"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a>Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox

Ovládací prvek <xref:System.Windows.Forms.RichTextBox> model Windows Forms může zobrazovat webové odkazy jako barevné a podtržené. Můžete napsat kód, který otevře okno prohlížeče znázorňující web zadaný v textu odkazu po kliknutí na odkaz.

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a>Odkazování na webovou stránku pomocí ovládacího prvku RichTextBox

1. Nastavte vlastnost na řetězec, který obsahuje platnou adresu URL (například "http://www.microsoft.com/"). <xref:System.Windows.Forms.RichTextBox.Text%2A>

2. Ujistěte se, <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> že je vlastnost nastavena `true` na hodnotu (výchozí).

3. Vytvořte novou globální instanci <xref:System.Diagnostics.Process> objektu.

4. Napište obslužnou rutinu události pro <xref:System.Windows.Forms.RichTextBox.LinkClicked> událost, která odešle prohlížeči požadovaný text.

    V následujícím <xref:System.Windows.Forms.RichTextBox.LinkClicked> příkladu událost otevře instanci aplikace Internet Explorer na adresu URL zadanou <xref:System.Windows.Forms.RichTextBox.Text%2A> ve vlastnosti <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Tento příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládacím prvkem.

    > [!IMPORTANT]
    > Při volání <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metody dojde k <xref:System.Security.SecurityException> výjimce, pokud kód spouštíte v kontextu částečného vztahu důvěryhodnosti z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).

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

    (Vizuální C++) Je nutné inicializovat proces `p`, který můžete provést zahrnutím následujícího příkazu do konstruktoru formuláře:

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.

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

    Po dokončení práce s ní je důležité okamžitě zastavit proces, který jste vytvořili. Odkaz na kód, který je uvedený výše, váš kód pro zastavení procesu může vypadat takto:

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

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
