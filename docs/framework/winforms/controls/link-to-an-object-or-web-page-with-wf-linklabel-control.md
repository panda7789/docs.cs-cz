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
ms.openlocfilehash: edebfaee6f0da6826f4b757568408662f3208d41
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344010"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel
Windows Forms <xref:System.Windows.Forms.LinkLabel> ovládacího prvku umožňuje vytvořit webových odkazů na formuláři. Při kliknutí na odkaz můžete změnit jeho barvu označující, že uživatel odkaz. Další informace o změně barvy, naleznete v tématu [jak: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).  
  
## <a name="linking-to-another-form"></a>Propojování do jiného formuláře  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Odkaz na jiný formulář pomocí ovládacího prvku LinkLabel  
  
1. Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnosti k odpovídající titulek.  
  
2. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> a určí, které části popisek bude uveden jako odkaz. Jak je uvedeno, závisí na vlastnostech související vzhled popisku odkazu. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Hodnotu je reprezentována <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> objekt, který obsahuje dvě čísla, počáteční pozici znaku a počet znaků. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Vlastnost lze nastavit v okně Vlastnosti nebo v kódu podobně jako následujícím způsobem:  
  
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
  
3. V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužná rutina události vyvolat <xref:System.Windows.Forms.Form.Show%2A> metoda otevřít nový formulář v projektu, a nastavit <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true`.  
  
    > [!NOTE]
    >  Instance <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> třída představuje odkaz na <xref:System.Windows.Forms.LinkLabel> ovládací prvek, který bylo kliknuto, takže není nutné přetypovat `sender` objektu.  
  
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
  
## <a name="linking-to-a-web-page"></a>Propojení na webovou stránku  
 <xref:System.Windows.Forms.LinkLabel> Ovládací prvek slouží také k zobrazení webové stránky s výchozím prohlížeči.  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Chcete-li spustit aplikaci Internet Explorer a odkaz na webovou stránku pomocí ovládacího prvku LinkLabel  
  
1. Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnosti k odpovídající titulek.  
  
2. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> a určí, které části popisek bude uveden jako odkaz.  
  
3. V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužná rutina události, uprostřed z bloku zpracování výjimek, volání druhý postup, který nastaví <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true` a používá <xref:System.Diagnostics.Process.Start%2A> metodu spustit výchozí prohlížeč s adresou URL. Použít <xref:System.Diagnostics.Process.Start%2A> budete muset přidat odkaz na metodu <xref:System.Diagnostics?displayProperty=nameWithType> oboru názvů.  
  
    > [!IMPORTANT]
    >  Pokud následující kód se spustí v prostředí částečné důvěryhodnosti (například na sdílené jednotky), kompilátor JIT není úspěšné při `VisitLink` metoda je volána. `System.Diagnostics.Process.Start` Příkaz způsobí, že požadavek na propojení, které se nedaří. Podle výjimku při `VisitLink` metoda je volána, následující kód zajistí, že pokud se kompilátor JIT nezdaří, je chyba řádně zpracována.  
  
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
