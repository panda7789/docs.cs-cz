---
title: 'Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: 9957eae7e15c99ec259574b435402420c6bcf5f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539630"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="09d4e-102">Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="09d4e-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>
<span data-ttu-id="09d4e-103">Windows Forms <xref:System.Windows.Forms.LinkLabel> řízení vám umožní vytvořit odkazy ve stylu webového formuláře.</span><span class="sxs-lookup"><span data-stu-id="09d4e-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="09d4e-104">Při kliknutí na odkaz, můžete změnit její barvu, která indikuje, že navštívil odkaz.</span><span class="sxs-lookup"><span data-stu-id="09d4e-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="09d4e-105">Další informace o změně barvu najdete v tématu [postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span><span class="sxs-lookup"><span data-stu-id="09d4e-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>  
  
## <a name="linking-to-another-form"></a><span data-ttu-id="09d4e-106">Propojování do jiného formátu</span><span class="sxs-lookup"><span data-stu-id="09d4e-106">Linking to Another Form</span></span>  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="09d4e-107">Propojit s jinou formuláře s linklabel – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="09d4e-107">To link to another form with a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="09d4e-108">Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost, která má odpovídající titulek.</span><span class="sxs-lookup"><span data-stu-id="09d4e-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2.  <span data-ttu-id="09d4e-109">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnosti k určení, které části titulek bude uveden jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="09d4e-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="09d4e-110">Jak je uvedeno, závisí na vlastnosti týkající se vzhledu odkaz popisku.</span><span class="sxs-lookup"><span data-stu-id="09d4e-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="09d4e-111"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Hodnota je reprezentována <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> objekt obsahující dvou čísel, počáteční pozice znaku a počet znaků.</span><span class="sxs-lookup"><span data-stu-id="09d4e-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="09d4e-112"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Vlastnost lze nastavit v okně Vlastnosti nebo v kódu podobné následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="09d4e-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>  
  
    ```vb  
    ' In this code example, the link area has been set to begin  
    ' at the first character and extend for eight characters.  
    ' You may need to modify this based on the text entered in Step 1.  
    LinkLabel1.LinkArea = New LinkArea(0, 8)  
    ```  
  
    ```csharp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1.LinkArea = new LinkArea(0,8);  
    ```  
  
    ```cpp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1->LinkArea = LinkArea(0,8);  
    ```  
  
3.  <span data-ttu-id="09d4e-113">V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné rutiny události, vyvolání <xref:System.Windows.Forms.Form.Show%2A> má metoda otevřít nový formulář v projektu a nastavte <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="09d4e-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09d4e-114">Instance <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> třída přenáší odkaz na <xref:System.Windows.Forms.LinkLabel> ovládací prvek, který označeného, takže není nutné přetypovat `sender` objektu.</span><span class="sxs-lookup"><span data-stu-id="09d4e-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       ' Show another form.  
       Dim f2 As New Form()  
       f2.Show  
       LinkLabel1.LinkVisited = True  
    End Sub  
    ```  
  
    ```csharp  
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       // Show another form.  
       Form f2 = new Form();  
       f2.Show();  
       linkLabel1.LinkVisited = true;  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Show another form.  
          Form ^ f2 = new Form();  
          f2->Show();  
          linkLabel1->LinkVisited = true;  
       }  
    ```  
  
## <a name="linking-to-a-web-page"></a><span data-ttu-id="09d4e-115">Propojení na webovou stránku</span><span class="sxs-lookup"><span data-stu-id="09d4e-115">Linking to a Web Page</span></span>  
 <span data-ttu-id="09d4e-116"><xref:System.Windows.Forms.LinkLabel> Řízení slouží také k zobrazení webové stránky s výchozí prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="09d4e-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="09d4e-117">Spusťte Internet Explorer a odkaz na webovou stránku s linklabel – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="09d4e-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>  
  
1.  <span data-ttu-id="09d4e-118">Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost, která má odpovídající titulek.</span><span class="sxs-lookup"><span data-stu-id="09d4e-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>  
  
2.  <span data-ttu-id="09d4e-119">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnosti k určení, které části titulek bude uveden jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="09d4e-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>  
  
3.  <span data-ttu-id="09d4e-120">V <xref:System.Windows.Forms.LinkLabel.LinkClicked> druhý postup, který nastavuje volání obslužné rutiny události in the midst of bloku zpracování výjimek <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true` a používá <xref:System.Diagnostics.Process.Start%2A> metoda spuštění výchozího prohlížeče s adresou URL.</span><span class="sxs-lookup"><span data-stu-id="09d4e-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="09d4e-121">Použít <xref:System.Diagnostics.Process.Start%2A> metoda budete muset přidat odkaz na <xref:System.Diagnostics?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="09d4e-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="09d4e-122">Pokud následující kód běží v prostředí s částečným vztahem důvěryhodnosti (například na sdílenou jednotku), JIT kompilátoru selže, když `VisitLink` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="09d4e-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="09d4e-123">`System.Diagnostics.Process.Start` Příkaz způsobí, že požadavek na propojení, který selže.</span><span class="sxs-lookup"><span data-stu-id="09d4e-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="09d4e-124">Podle výjimku při `VisitLink` metoda je volána, následující kód zajistí, že v případě selhání kompilátoru za běhu je chyba řádně zpracována.</span><span class="sxs-lookup"><span data-stu-id="09d4e-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>  
  
    ```vb  
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       Try  
          VisitLink()  
       Catch ex As Exception  
          ' The error message  
          MessageBox.Show("Unable to open link that was clicked.")  
       End Try  
    End Sub  
  
    Sub VisitLink()  
       ' Change the color of the link text by setting LinkVisited   
       ' to True.  
       LinkLabel1.LinkVisited = True  
       ' Call the Process.Start method to open the default browser   
       ' with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com")  
    End Sub  
    ```  
  
    ```csharp  
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       try  
       {  
          VisitLink();  
       }  
       catch (Exception ex )  
       {  
          MessageBox.Show("Unable to open link that was clicked.");  
       }  
    }  
  
    private void VisitLink()  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to true.  
       linkLabel1.LinkVisited = true;  
       //Call the Process.Start method to open the default browser   
       //with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com");  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          try  
          {  
             VisitLink();  
          }  
          catch (Exception ^ ex)  
          {  
             MessageBox::Show("Unable to open link that was clicked.");  
          }  
       }  
    private:  
       void VisitLink()  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to true.  
          linkLabel1->LinkVisited = true;  
          // Call the Process.Start method to open the default browser   
          // with a URL:  
          System::Diagnostics::Process::Start("http://www.microsoft.com");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="09d4e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="09d4e-125">See Also</span></span>  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="09d4e-126">Přehled ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="09d4e-126">LinkLabel Control Overview</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [<span data-ttu-id="09d4e-127">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="09d4e-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)  
 [<span data-ttu-id="09d4e-128">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="09d4e-128">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
