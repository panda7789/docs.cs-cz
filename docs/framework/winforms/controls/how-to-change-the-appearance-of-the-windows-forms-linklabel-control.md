---
title: Změna vzhledu ovládacího prvku Popisek odkazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
ms.openlocfilehash: df66991289373a05fc7c27b7768a96643e3bbae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142127"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel
Text zobrazený <xref:System.Windows.Forms.LinkLabel> ovládacím prvkem můžete změnit tak, aby vyhovoval různým účelům. Například je běžnou praxí oznamovat uživateli, že na text lze klepnout nastavením textu tak, aby se zobrazoval v určité barvě s podtržením. Po kliknutí na text se barva změní na jinou barvu. Chcete-li toto chování řídit, můžete <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>nastavit <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>pět <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> různých vlastností: , , a vlastnosti.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Změna vzhledu ovládacího prvku LinkLabel  
  
1. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> vlastnosti a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> na požadované barvy.  
  
     To lze provést programově nebo v době návrhu v okně **Vlastnosti.**  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2. Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost na příslušný titulek.  
  
     To lze provést programově nebo v době návrhu v okně **Vlastnosti.**  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost k určení, která část titulku bude označena jako odkaz.  
  
     Hodnota <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> je reprezentována <xref:System.Windows.Forms.LinkArea> obsahující dvě čísla, počáteční pozici znaku a počet znaků. To lze provést programově nebo v době návrhu v okně **Vlastnosti.**  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnost <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>, nebo .  
  
     Pokud je nastavena na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, část <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> titulku určena bude podtržena pouze tehdy, když ukazatel spočívá na něm.  
  
5. V <xref:System.Windows.Forms.LinkLabel.LinkClicked> obslužné <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> rutině události nastavte vlastnost na `true`.  
  
     Když byl odkaz navštíven, je běžnou praxí změnit jeho vzhled nějakým způsobem, obvykle podle barvy. Text se změní na barvu <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> určenou vlastností.  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [LinkLabel – přehled ovládacího prvku](linklabel-control-overview-windows-forms.md)
- [Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Ovládací prvek LinkLabel](linklabel-control-windows-forms.md)
