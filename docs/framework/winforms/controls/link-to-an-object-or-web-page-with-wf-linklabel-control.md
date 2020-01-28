---
title: Odkazování na objekt nebo webovou stránku pomocí ovládacího prvku LinkLabel
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
ms.openlocfilehash: 1669a9d6aba39b02d228c735701ca4e31c8f8291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745204"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="8c00e-102">Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8c00e-102">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>

<span data-ttu-id="8c00e-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.LinkLabel> umožňuje vytvořit na formuláři odkazy na webové styly.</span><span class="sxs-lookup"><span data-stu-id="8c00e-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="8c00e-104">Po kliknutí na odkaz můžete změnit jeho barvu tak, aby označovala, že odkaz byl navštíven.</span><span class="sxs-lookup"><span data-stu-id="8c00e-104">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="8c00e-105">Další informace o změně barvy naleznete v tématu [Postupy: Změna vzhledu model Windows Formsho ovládacího prvku LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span><span class="sxs-lookup"><span data-stu-id="8c00e-105">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>

## <a name="linking-to-another-form"></a><span data-ttu-id="8c00e-106">Propojení s jiným formulářem</span><span class="sxs-lookup"><span data-stu-id="8c00e-106">Linking to Another Form</span></span>

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="8c00e-107">Propojení s jiným formulářem pomocí ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8c00e-107">To link to another form with a LinkLabel control</span></span>

1. <span data-ttu-id="8c00e-108">Vlastnost <xref:System.Windows.Forms.LinkLabel.Text%2A> nastavte na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="8c00e-108">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="8c00e-109">Nastavením vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> určíte, která část popisku bude označena jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="8c00e-109">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="8c00e-110">Jak je uvedeno, závisí na vlastnostech popisku odkazu.</span><span class="sxs-lookup"><span data-stu-id="8c00e-110">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="8c00e-111">Hodnota <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> je reprezentována objektem <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, který obsahuje dvě čísla, počáteční a počet znaků.</span><span class="sxs-lookup"><span data-stu-id="8c00e-111">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="8c00e-112">Vlastnost <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> lze nastavit v okno Vlastnosti nebo v kódu způsobem, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="8c00e-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>

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

3. <span data-ttu-id="8c00e-113">V obslužné rutině události <xref:System.Windows.Forms.LinkLabel.LinkClicked> volejte metodu <xref:System.Windows.Forms.Form.Show%2A> pro otevření jiného formuláře v projektu a vlastnost <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> nastavte na `true`.</span><span class="sxs-lookup"><span data-stu-id="8c00e-113">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8c00e-114">Instance třídy <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> přenáší odkaz na ovládací prvek <xref:System.Windows.Forms.LinkLabel>, který byl kliknuto, takže není nutné přetypování objektu `sender`.</span><span class="sxs-lookup"><span data-stu-id="8c00e-114">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>

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

## <a name="linking-to-a-web-page"></a><span data-ttu-id="8c00e-115">Propojení s webovou stránkou</span><span class="sxs-lookup"><span data-stu-id="8c00e-115">Linking to a Web Page</span></span>

<span data-ttu-id="8c00e-116">Ovládací prvek <xref:System.Windows.Forms.LinkLabel> lze také použít k zobrazení webové stránky s výchozím prohlížečem.</span><span class="sxs-lookup"><span data-stu-id="8c00e-116">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="8c00e-117">Spuštění aplikace Internet Explorer a propojení s webovou stránkou s ovládacím prvkem LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8c00e-117">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>

1. <span data-ttu-id="8c00e-118">Vlastnost <xref:System.Windows.Forms.LinkLabel.Text%2A> nastavte na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="8c00e-118">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="8c00e-119">Nastavením vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> určíte, která část popisku bude označena jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="8c00e-119">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>

3. <span data-ttu-id="8c00e-120">V obslužné rutině události <xref:System.Windows.Forms.LinkLabel.LinkClicked>, v průběhu bloku zpracování výjimek, zavolejte druhý postup, který nastaví vlastnost <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na hodnotu `true` a pomocí metody <xref:System.Diagnostics.Process.Start%2A> spustí výchozí prohlížeč s adresou URL.</span><span class="sxs-lookup"><span data-stu-id="8c00e-120">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="8c00e-121">Chcete-li použít metodu <xref:System.Diagnostics.Process.Start%2A>, je nutné přidat odkaz na obor názvů <xref:System.Diagnostics?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c00e-121">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8c00e-122">Pokud je kód níže spuštěn v prostředí s částečným vztahem důvěryhodnosti (například na sdílené jednotce), kompilátor JIT při volání metody `VisitLink` neproběhne.</span><span class="sxs-lookup"><span data-stu-id="8c00e-122">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="8c00e-123">Příkaz `System.Diagnostics.Process.Start` způsobuje požadavek propojení, který se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="8c00e-123">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="8c00e-124">Zachycením výjimky při volání metody `VisitLink`, kód níže zajišťuje, že pokud dojde k chybě kompilátoru JIT, chyba bude zpracována řádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="8c00e-124">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8c00e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c00e-125">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8c00e-126">Přehled ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8c00e-126">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="8c00e-127">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8c00e-127">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="8c00e-128">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8c00e-128">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
