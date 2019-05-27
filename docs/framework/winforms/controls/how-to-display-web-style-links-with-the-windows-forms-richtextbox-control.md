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
ms.openlocfilehash: 05d9ad4766584b59cca7c31f49b737d4696a9921
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053542"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="ef65c-102">Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ef65c-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="ef65c-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek mohl zobrazit webové odkazy jako barevný a podtržené.</span><span class="sxs-lookup"><span data-stu-id="ef65c-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="ef65c-104">Můžete napsat kód, který se otevře okno prohlížeče zobrazující webu zadané v textu odkazu, po kliknutí na odkaz.</span><span class="sxs-lookup"><span data-stu-id="ef65c-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="ef65c-105">Odkaz na webovou stránku pomocí ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ef65c-105">To link to a Web page with the RichTextBox control</span></span>  
  
1. <span data-ttu-id="ef65c-106">Nastavte <xref:System.Windows.Forms.RichTextBox.Text%2A> nastavte na řetězec, který obsahuje platnou adresu URL (například "http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="ef65c-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2. <span data-ttu-id="ef65c-107">Ujistěte se, <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> je nastavena na `true` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ef65c-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3. <span data-ttu-id="ef65c-108">Vytvořit novou globální instanci <xref:System.Diagnostics.Process> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef65c-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4. <span data-ttu-id="ef65c-109">Zápis obslužné rutiny události <xref:System.Windows.Forms.RichTextBox.LinkClicked> událost, která se odešle do prohlížeče požadovaný text.</span><span class="sxs-lookup"><span data-stu-id="ef65c-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="ef65c-110">V následujícím příkladu <xref:System.Windows.Forms.RichTextBox.LinkClicked> události otevírá instanci aplikace Internet Explorer na adrese URL zadané v <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ef65c-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="ef65c-111">Tento příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ef65c-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ef65c-112">Ve volání funkce <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metoda, se setkají <xref:System.Security.SecurityException> výjimku, pokud používáte kód v kontextu částečným vztahem důvěryhodnosti z důvodu dostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="ef65c-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="ef65c-113">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ef65c-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
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
  
     <span data-ttu-id="ef65c-114">(Visual C++) Je třeba inicializovat proces `p`, což lze provést zahrnutím následujícího příkazu v konstruktoru formuláře:</span><span class="sxs-lookup"><span data-stu-id="ef65c-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="ef65c-115">(Visual C#, Visual C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ef65c-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="ef65c-116">Je důležité ihned zastavte sledovací proces, který jste vytvořili po dokončení práce s ní.</span><span class="sxs-lookup"><span data-stu-id="ef65c-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="ef65c-117">Odkazující na kód uvedený výše, váš kód zastavte sledovací proces může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="ef65c-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef65c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef65c-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="ef65c-119">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ef65c-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="ef65c-120">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef65c-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
