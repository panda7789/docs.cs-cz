---
title: "Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3921c15de59deaa68b63d7dbfbfeb18c776d31f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel
Windows Forms <xref:System.Windows.Forms.LinkLabel> řízení vám umožní vytvořit odkazy ve stylu webového formuláře. Při kliknutí na odkaz, můžete změnit její barvu, která indikuje, že navštívil odkaz. Další informace o změně barvu najdete v tématu [postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).  
  
## <a name="linking-to-another-form"></a>Propojování do jiného formátu  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Propojit s jinou formuláře s linklabel – ovládací prvek  
  
1.  Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost, která má odpovídající titulek.  
  
2.  Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnosti k určení, které části titulek bude uveden jako odkaz. Jak je uvedeno, závisí na vlastnosti týkající se vzhledu odkaz popisku. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Hodnota je reprezentována <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> objekt obsahující dvou čísel, počáteční pozice znaku a počet znaků. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Vlastnost lze nastavit v okně Vlastnosti nebo v kódu podobné následujícím způsobem:  
  
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
  
3.  V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné rutiny události, vyvolání <xref:System.Windows.Forms.Form.Show%2A> má metoda otevřít nový formulář v projektu a nastavte <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true`.  
  
    > [!NOTE]
    >  Instance <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> třída přenáší odkaz na <xref:System.Windows.Forms.LinkLabel> ovládací prvek, který označeného, takže není nutné přetypovat `sender` objektu.  
  
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
 <xref:System.Windows.Forms.LinkLabel> Řízení slouží také k zobrazení webové stránky s výchozí prohlížeč.  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Spusťte Internet Explorer a odkaz na webovou stránku s linklabel – ovládací prvek  
  
1.  Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost, která má odpovídající titulek.  
  
2.  Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnosti k určení, které části titulek bude uveden jako odkaz.  
  
3.  V <xref:System.Windows.Forms.LinkLabel.LinkClicked> druhý postup, který nastavuje volání obslužné rutiny události in the midst of bloku zpracování výjimek <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true` a používá <xref:System.Diagnostics.Process.Start%2A> metoda spuštění výchozího prohlížeče s adresou URL. Použít <xref:System.Diagnostics.Process.Start%2A> metoda budete muset přidat odkaz na <xref:System.Diagnostics?displayProperty=nameWithType> oboru názvů.  
  
    > [!IMPORTANT]
    >  Pokud následující kód běží v prostředí s částečným vztahem důvěryhodnosti (například na sdílenou jednotku), JIT kompilátoru selže, když `VisitLink` metoda je volána. `System.Diagnostics.Process.Start` Příkaz způsobí, že požadavek na propojení, který selže. Podle výjimku při `VisitLink` metoda je volána, následující kód zajistí, že v případě selhání kompilátoru za běhu je chyba řádně zpracována.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>  
 [Přehled ovládacího prvku LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)  
 [Ovládací prvek LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
