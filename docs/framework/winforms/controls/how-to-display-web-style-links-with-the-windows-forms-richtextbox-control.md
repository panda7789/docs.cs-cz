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
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="c36eb-102">Postupy: Zobrazení webových odkazů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c36eb-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="c36eb-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek může zobrazit webové odkazy jako barevný a podtržený.</span><span class="sxs-lookup"><span data-stu-id="c36eb-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="c36eb-104">Můžete napsat kód, který se otevře okno prohlížeče zobrazující Web zadaný text odkazu, při kliknutí na odkaz.</span><span class="sxs-lookup"><span data-stu-id="c36eb-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>  
  
### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="c36eb-105">Chcete-li odkaz na webovou stránku pomocí ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c36eb-105">To link to a Web page with the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="c36eb-106">Nastavte <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost na řetězec, který obsahuje platnou adresu URL (například "http://www.microsoft.com/").</span><span class="sxs-lookup"><span data-stu-id="c36eb-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "http://www.microsoft.com/").</span></span>  
  
2.  <span data-ttu-id="c36eb-107">Zajistěte, aby <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> je nastavena na `true` (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c36eb-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>  
  
3.  <span data-ttu-id="c36eb-108">Vytvořit novou globální instanci <xref:System.Diagnostics.Process> objektu.</span><span class="sxs-lookup"><span data-stu-id="c36eb-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>  
  
4.  <span data-ttu-id="c36eb-109">Zápis obslužné rutiny události pro <xref:System.Windows.Forms.RichTextBox.LinkClicked> událost, která se odešle do prohlížeče požadovaný text.</span><span class="sxs-lookup"><span data-stu-id="c36eb-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>  
  
     <span data-ttu-id="c36eb-110">V následujícím příkladu <xref:System.Windows.Forms.RichTextBox.LinkClicked> událostí otevře instance Internet Exploreru, aby adresa URL zadaná v <xref:System.Windows.Forms.RichTextBox.Text%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c36eb-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="c36eb-111">Tento příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c36eb-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c36eb-112">Ve volání <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> metoda, se setkají <xref:System.Security.SecurityException> výjimka, pokud používáte kód v kontextu částečným vztahem důvěryhodnosti z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c36eb-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="c36eb-113">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c36eb-113">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
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
  
     <span data-ttu-id="c36eb-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Musí inicializovat proces `p`, což lze provést tak, že začleníte následující příkaz v konstruktoru formuláře:</span><span class="sxs-lookup"><span data-stu-id="c36eb-114">([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     <span data-ttu-id="c36eb-115">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c36eb-115">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="c36eb-116">Je důležité okamžitě zastavit proces, který jste vytvořili po dokončení práce s ním.</span><span class="sxs-lookup"><span data-stu-id="c36eb-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="c36eb-117">Odkazy na kód uvedený výše, kódu se zastavit proces může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="c36eb-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c36eb-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c36eb-118">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>  
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="c36eb-119">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="c36eb-119">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="c36eb-120">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c36eb-120">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
