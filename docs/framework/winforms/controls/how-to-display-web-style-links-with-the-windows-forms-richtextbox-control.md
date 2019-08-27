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
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="833ad-102">Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="833ad-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="833ad-103">Ovládací prvek <xref:System.Windows.Forms.RichTextBox> model Windows Forms může zobrazovat webové odkazy jako barevné a podtržené.</span><span class="sxs-lookup"><span data-stu-id="833ad-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="833ad-104">Můžete napsat kód, který otevře okno prohlížeče znázorňující web zadaný v textu odkazu po kliknutí na odkaz.</span><span class="sxs-lookup"><span data-stu-id="833ad-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="833ad-105">Odkazování na webovou stránku pomocí ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="833ad-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="833ad-106">Nastavte vlastnost na řetězec, který obsahuje platnou adresu URL (například "http://www.microsoft.com/"). <xref:System.Windows.Forms.RichTextBox.Text%2A></span><span class="sxs-lookup"><span data-stu-id="833ad-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>

2. <span data-ttu-id="833ad-107">Ujistěte se, <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> že je vlastnost nastavena `true` na hodnotu (výchozí).</span><span class="sxs-lookup"><span data-stu-id="833ad-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="833ad-108">Vytvořte novou globální instanci <xref:System.Diagnostics.Process> objektu.</span><span class="sxs-lookup"><span data-stu-id="833ad-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="833ad-109">Napište obslužnou rutinu události pro <xref:System.Windows.Forms.RichTextBox.LinkClicked> událost, která odešle prohlížeči požadovaný text.</span><span class="sxs-lookup"><span data-stu-id="833ad-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="833ad-110">V následujícím <xref:System.Windows.Forms.RichTextBox.LinkClicked> příkladu událost otevře instanci aplikace Internet Explorer na adresu URL zadanou <xref:System.Windows.Forms.RichTextBox.Text%2A> ve vlastnosti <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="833ad-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="833ad-111">Tento příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="833ad-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="833ad-112">Při volání <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metody dojde k <xref:System.Security.SecurityException> výjimce, pokud kód spouštíte v kontextu částečného vztahu důvěryhodnosti z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="833ad-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="833ad-113">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="833ad-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

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

    <span data-ttu-id="833ad-114">(Vizuální C++) Je nutné inicializovat proces `p`, který můžete provést zahrnutím následujícího příkazu do konstruktoru formuláře:</span><span class="sxs-lookup"><span data-stu-id="833ad-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="833ad-115">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="833ad-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

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

    <span data-ttu-id="833ad-116">Po dokončení práce s ní je důležité okamžitě zastavit proces, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="833ad-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="833ad-117">Odkaz na kód, který je uvedený výše, váš kód pro zastavení procesu může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="833ad-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="833ad-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="833ad-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="833ad-119">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="833ad-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="833ad-120">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="833ad-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
