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
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel

<xref:System.Windows.Forms.LinkLabel>Ovládací prvek model Windows Forms umožňuje vytvořit na formuláři odkazy na webové styly. Po kliknutí na odkaz můžete změnit jeho barvu tak, aby označovala, že odkaz byl navštíven. Další informace o změně barvy naleznete v tématu [Postupy: Změna vzhledu model Windows Formsho ovládacího prvku LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).

## <a name="linking-to-another-form"></a>Propojení s jiným formulářem

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Propojení s jiným formulářem pomocí ovládacího prvku LinkLabel

1. Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost na příslušný titulek.

2. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost tak, aby určovala, která část titulku bude označena jako odkaz. Jak je uvedeno, závisí na vlastnostech popisku odkazu. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>Hodnota je reprezentována <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> objektem, který obsahuje dvě čísla, počáteční pozice znaku a počet znaků. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>Vlastnost lze nastavit v okno Vlastnosti nebo v kódu způsobem, který je podobný následujícímu:

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

3. V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné rutině události volejte <xref:System.Windows.Forms.Form.Show%2A> metodu pro otevření jiného formuláře v projektu a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost nastavte na `true` .

    > [!NOTE]
    > Instance <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> třídy přenáší odkaz na <xref:System.Windows.Forms.LinkLabel> ovládací prvek, který byl kliknuto, takže není nutné přetypování `sender` objektu.

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

## <a name="linking-to-a-web-page"></a>Propojení s webovou stránkou

<xref:System.Windows.Forms.LinkLabel>Ovládací prvek lze také použít k zobrazení webové stránky s výchozím prohlížečem.

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Spuštění aplikace Internet Explorer a propojení s webovou stránkou s ovládacím prvkem LinkLabel

1. Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost na příslušný titulek.

2. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost tak, aby určovala, která část titulku bude označena jako odkaz.

3. V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné rutině události v průběhu bloku zpracování výjimek volejte druhý postup, který nastaví <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost na `true` a používá <xref:System.Diagnostics.Process.Start%2A> metodu ke spuštění výchozího prohlížeče s adresou URL. Chcete-li použít <xref:System.Diagnostics.Process.Start%2A> metodu, kterou potřebujete přidat odkaz na <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů.

    > [!IMPORTANT]
    > Pokud je kód níže spuštěn v prostředí s částečným vztahem důvěryhodnosti (například na sdílené jednotce), kompilátor JIT při volání metody dojde k chybě `VisitLink` . `System.Diagnostics.Process.Start`Příkaz způsobí požadavek propojení, který se nezdařil. Zachycením výjimky při `VisitLink` volání metody kód níže zajišťuje, že pokud dojde k chybě kompilátoru JIT, chyba je zpracována řádným způsobem.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [LinkLabel – přehled ovládacího prvku](linklabel-control-overview-windows-forms.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [Ovládací prvek LinkLabel](linklabel-control-windows-forms.md)
