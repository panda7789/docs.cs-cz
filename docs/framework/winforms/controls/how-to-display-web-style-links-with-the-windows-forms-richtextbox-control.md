---
title: Zobrazení odkazů ve stylu webu pomocí ovládacího prvku RichTextBox
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
ms.openlocfilehash: 78a07a250744018f121b03f2973b1661ed6bf764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745538"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="8aa42-102">Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8aa42-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="8aa42-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> může zobrazovat webové odkazy jako barevné a podtržené.</span><span class="sxs-lookup"><span data-stu-id="8aa42-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="8aa42-104">Můžete napsat kód, který otevře okno prohlížeče znázorňující web zadaný v textu odkazu po kliknutí na odkaz.</span><span class="sxs-lookup"><span data-stu-id="8aa42-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="8aa42-105">Odkazování na webovou stránku pomocí ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8aa42-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="8aa42-106">Vlastnost <xref:System.Windows.Forms.RichTextBox.Text%2A> nastavte na řetězec, který obsahuje platnou adresu URL (například "http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="8aa42-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>

2. <span data-ttu-id="8aa42-107">Ujistěte se, že je vlastnost <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> nastavena na hodnotu `true` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8aa42-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="8aa42-108">Vytvořte novou globální instanci objektu <xref:System.Diagnostics.Process>.</span><span class="sxs-lookup"><span data-stu-id="8aa42-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="8aa42-109">Napište obslužnou rutinu události pro událost <xref:System.Windows.Forms.RichTextBox.LinkClicked>, která odešle prohlížeči požadovaný text.</span><span class="sxs-lookup"><span data-stu-id="8aa42-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="8aa42-110">V následujícím příkladu událost <xref:System.Windows.Forms.RichTextBox.LinkClicked> otevírá instanci aplikace Internet Explorer na adresu URL zadanou ve vlastnosti <xref:System.Windows.Forms.RichTextBox.Text%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8aa42-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="8aa42-111">Tento příklad předpokládá formulář s ovládacím prvkem <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8aa42-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8aa42-112">Při volání metody <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> narazíte na výjimku <xref:System.Security.SecurityException>, pokud kód spouštíte v kontextu částečného vztahu důvěryhodnosti z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="8aa42-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="8aa42-113">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8aa42-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

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

    <span data-ttu-id="8aa42-114">(Vizuální C++) Je nutné inicializovat `p`procesu, což lze provést vložením následujícího příkazu do konstruktoru formuláře:</span><span class="sxs-lookup"><span data-stu-id="8aa42-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="8aa42-115">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8aa42-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

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

    <span data-ttu-id="8aa42-116">Po dokončení práce s ní je důležité okamžitě zastavit proces, který jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="8aa42-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="8aa42-117">Odkaz na kód, který je uvedený výše, váš kód pro zastavení procesu může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="8aa42-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8aa42-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8aa42-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="8aa42-119">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8aa42-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="8aa42-120">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8aa42-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
