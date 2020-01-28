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
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel

Ovládací prvek model Windows Forms <xref:System.Windows.Forms.LinkLabel> umožňuje vytvořit na formuláři odkazy na webové styly. Po kliknutí na odkaz můžete změnit jeho barvu tak, aby označovala, že odkaz byl navštíven. Další informace o změně barvy naleznete v tématu [Postupy: Změna vzhledu model Windows Formsho ovládacího prvku LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).

## <a name="linking-to-another-form"></a>Propojení s jiným formulářem

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Propojení s jiným formulářem pomocí ovládacího prvku LinkLabel

1. Vlastnost <xref:System.Windows.Forms.LinkLabel.Text%2A> nastavte na příslušný titulek.

2. Nastavením vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> určíte, která část popisku bude označena jako odkaz. Jak je uvedeno, závisí na vlastnostech popisku odkazu. Hodnota <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> je reprezentována objektem <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, který obsahuje dvě čísla, počáteční a počet znaků. Vlastnost <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> lze nastavit v okno Vlastnosti nebo v kódu způsobem, který je podobný následujícímu:

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

3. V obslužné rutině události <xref:System.Windows.Forms.LinkLabel.LinkClicked> volejte metodu <xref:System.Windows.Forms.Form.Show%2A> pro otevření jiného formuláře v projektu a vlastnost <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> nastavte na `true`.

    > [!NOTE]
    > Instance třídy <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> přenáší odkaz na ovládací prvek <xref:System.Windows.Forms.LinkLabel>, který byl kliknuto, takže není nutné přetypování objektu `sender`.

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

Ovládací prvek <xref:System.Windows.Forms.LinkLabel> lze také použít k zobrazení webové stránky s výchozím prohlížečem.

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Spuštění aplikace Internet Explorer a propojení s webovou stránkou s ovládacím prvkem LinkLabel

1. Vlastnost <xref:System.Windows.Forms.LinkLabel.Text%2A> nastavte na příslušný titulek.

2. Nastavením vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> určíte, která část popisku bude označena jako odkaz.

3. V obslužné rutině události <xref:System.Windows.Forms.LinkLabel.LinkClicked>, v průběhu bloku zpracování výjimek, zavolejte druhý postup, který nastaví vlastnost <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na hodnotu `true` a pomocí metody <xref:System.Diagnostics.Process.Start%2A> spustí výchozí prohlížeč s adresou URL. Chcete-li použít metodu <xref:System.Diagnostics.Process.Start%2A>, je nutné přidat odkaz na obor názvů <xref:System.Diagnostics?displayProperty=nameWithType>.

    > [!IMPORTANT]
    > Pokud je kód níže spuštěn v prostředí s částečným vztahem důvěryhodnosti (například na sdílené jednotce), kompilátor JIT při volání metody `VisitLink` neproběhne. Příkaz `System.Diagnostics.Process.Start` způsobuje požadavek propojení, který se nezdařil. Zachycením výjimky při volání metody `VisitLink`, kód níže zajišťuje, že pokud dojde k chybě kompilátoru JIT, chyba bude zpracována řádným způsobem.

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
- [Přehled ovládacího prvku LinkLabel](linklabel-control-overview-windows-forms.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [Ovládací prvek LinkLabel](linklabel-control-windows-forms.md)
