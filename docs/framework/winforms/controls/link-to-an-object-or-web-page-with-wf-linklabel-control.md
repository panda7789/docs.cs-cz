---
title: Odkazování na objekt nebo webovou stránku pomocí ovládacího prvku LinkLabel
description: Naučte se, jak vytvořit odkazy na webový styl na objekt nebo webovou stránku pomocí ovládacího prvku model Windows Forms LinkLabel.
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
ms.openlocfilehash: a5fb1c03e9a8d82fe77f4133ba04c42114787d23
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618309"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a><span data-ttu-id="88264-103">Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="88264-103">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>

<span data-ttu-id="88264-104"><xref:System.Windows.Forms.LinkLabel>Ovládací prvek model Windows Forms umožňuje vytvořit na formuláři odkazy na webové styly.</span><span class="sxs-lookup"><span data-stu-id="88264-104">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to create Web-style links on your form.</span></span> <span data-ttu-id="88264-105">Po kliknutí na odkaz můžete změnit jeho barvu tak, aby označovala, že odkaz byl navštíven.</span><span class="sxs-lookup"><span data-stu-id="88264-105">When the link is clicked, you can change its color to indicate the link has been visited.</span></span> <span data-ttu-id="88264-106">Další informace o změně barvy naleznete v tématu [Postupy: Změna vzhledu model Windows Formsho ovládacího prvku LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span><span class="sxs-lookup"><span data-stu-id="88264-106">For more information on changing the color, see [How to: Change the Appearance of the Windows Forms LinkLabel Control](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).</span></span>

## <a name="linking-to-another-form"></a><span data-ttu-id="88264-107">Propojení s jiným formulářem</span><span class="sxs-lookup"><span data-stu-id="88264-107">Linking to Another Form</span></span>

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a><span data-ttu-id="88264-108">Propojení s jiným formulářem pomocí ovládacího prvku LinkLabel</span><span class="sxs-lookup"><span data-stu-id="88264-108">To link to another form with a LinkLabel control</span></span>

1. <span data-ttu-id="88264-109">Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="88264-109">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="88264-110">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost tak, aby určovala, která část titulku bude označena jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="88264-110">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span> <span data-ttu-id="88264-111">Jak je uvedeno, závisí na vlastnostech popisku odkazu.</span><span class="sxs-lookup"><span data-stu-id="88264-111">How it is indicated depends on the appearance-related properties of the link label.</span></span> <span data-ttu-id="88264-112"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>Hodnota je reprezentována <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> objektem, který obsahuje dvě čísla, počáteční pozice znaku a počet znaků.</span><span class="sxs-lookup"><span data-stu-id="88264-112">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> value is represented by a <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> object containing two numbers, the starting character position and the number of characters.</span></span> <span data-ttu-id="88264-113"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>Vlastnost lze nastavit v okno Vlastnosti nebo v kódu způsobem, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="88264-113">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property can be set in the Properties window or in code in a manner similar to the following:</span></span>

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

3. <span data-ttu-id="88264-114">V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné rutině události volejte <xref:System.Windows.Forms.Form.Show%2A> metodu pro otevření jiného formuláře v projektu a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost nastavte na `true` .</span><span class="sxs-lookup"><span data-stu-id="88264-114">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, invoke the <xref:System.Windows.Forms.Form.Show%2A> method to open another form in the project, and set the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="88264-115">Instance <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> třídy přenáší odkaz na <xref:System.Windows.Forms.LinkLabel> ovládací prvek, který byl kliknuto, takže není nutné přetypování `sender` objektu.</span><span class="sxs-lookup"><span data-stu-id="88264-115">An instance of the <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> class carries a reference to the <xref:System.Windows.Forms.LinkLabel> control that was clicked, so there is no need to cast the `sender` object.</span></span>

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

## <a name="linking-to-a-web-page"></a><span data-ttu-id="88264-116">Propojení s webovou stránkou</span><span class="sxs-lookup"><span data-stu-id="88264-116">Linking to a Web Page</span></span>

<span data-ttu-id="88264-117"><xref:System.Windows.Forms.LinkLabel>Ovládací prvek lze také použít k zobrazení webové stránky s výchozím prohlížečem.</span><span class="sxs-lookup"><span data-stu-id="88264-117">The <xref:System.Windows.Forms.LinkLabel> control can also be used to display a Web page with the default browser.</span></span>

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a><span data-ttu-id="88264-118">Spuštění aplikace Internet Explorer a propojení s webovou stránkou s ovládacím prvkem LinkLabel</span><span class="sxs-lookup"><span data-stu-id="88264-118">To start Internet Explorer and link to a Web page with a LinkLabel control</span></span>

1. <span data-ttu-id="88264-119">Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost na příslušný titulek.</span><span class="sxs-lookup"><span data-stu-id="88264-119">Set the <xref:System.Windows.Forms.LinkLabel.Text%2A> property to an appropriate caption.</span></span>

2. <span data-ttu-id="88264-120">Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost tak, aby určovala, která část titulku bude označena jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="88264-120">Set the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property to determine which part of the caption will be indicated as a link.</span></span>

3. <span data-ttu-id="88264-121">V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné rutině události v průběhu bloku zpracování výjimek volejte druhý postup, který nastaví <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost na `true` a používá <xref:System.Diagnostics.Process.Start%2A> metodu ke spuštění výchozího prohlížeče s adresou URL.</span><span class="sxs-lookup"><span data-stu-id="88264-121">In the <xref:System.Windows.Forms.LinkLabel.LinkClicked> event handler, in the midst of an exception-handling block, call a second procedure that sets the <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> property to `true` and uses the <xref:System.Diagnostics.Process.Start%2A> method to start the default browser with a URL.</span></span> <span data-ttu-id="88264-122">Chcete-li použít <xref:System.Diagnostics.Process.Start%2A> metodu, kterou potřebujete přidat odkaz na <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="88264-122">To use the <xref:System.Diagnostics.Process.Start%2A> method you need to add a reference to the <xref:System.Diagnostics?displayProperty=nameWithType> namespace.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="88264-123">Pokud je kód níže spuštěn v prostředí s částečným vztahem důvěryhodnosti (například na sdílené jednotce), kompilátor JIT při volání metody dojde k chybě `VisitLink` .</span><span class="sxs-lookup"><span data-stu-id="88264-123">If the code below is run in a partial-trust environment (such as on a shared drive), the JIT compiler fails when the `VisitLink` method is called.</span></span> <span data-ttu-id="88264-124">`System.Diagnostics.Process.Start`Příkaz způsobí požadavek propojení, který se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="88264-124">The `System.Diagnostics.Process.Start` statement causes a link demand that fails.</span></span> <span data-ttu-id="88264-125">Zachycením výjimky při `VisitLink` volání metody kód níže zajišťuje, že pokud dojde k chybě kompilátoru JIT, chyba je zpracována řádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="88264-125">By catching the exception when the `VisitLink` method is called, the code below ensures that if the JIT compiler fails, the error is handled gracefully.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="88264-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88264-126">See also</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="88264-127">LinkLabel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="88264-127">LinkLabel Control Overview</span></span>](linklabel-control-overview-windows-forms.md)
- [<span data-ttu-id="88264-128">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="88264-128">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [<span data-ttu-id="88264-129">Ovládací prvek LinkLabel</span><span class="sxs-lookup"><span data-stu-id="88264-129">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
