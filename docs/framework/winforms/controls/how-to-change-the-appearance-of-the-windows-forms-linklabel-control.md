---
title: Změna vzhledu ovládacího prvku LinkLabel
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
ms.openlocfilehash: 0b38722fb1647ea215c3bb8978dd3f54b300a0e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746628"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel
Text zobrazený ovládacím prvkem <xref:System.Windows.Forms.LinkLabel> můžete změnit tak, aby vyhovoval různým účelům. Například je běžné, že uživateli označit, že se dá text kliknout, nastavením textu, který se má zobrazit v konkrétní barvě podtržením. Jakmile uživatel klikne na text, změní se barva na jinou barvu. Pro řízení tohoto chování můžete nastavit pět různých vlastností: vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Změna vzhledu ovládacího prvku LinkLabel  
  
1. Nastavte vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> na barvy, které chcete.  
  
     To lze provést buď programově, nebo v době návrhu v okně **vlastnosti** .  
  
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
  
2. Vlastnost <xref:System.Windows.Forms.LinkLabel.Text%2A> nastavte na příslušný titulek.  
  
     To lze provést buď programově, nebo v době návrhu v okně **vlastnosti** .  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Nastavením vlastnosti <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> určíte, která část popisku bude označena jako odkaz.  
  
     Hodnota <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> je reprezentovaná <xref:System.Windows.Forms.LinkArea>, která obsahuje dvě čísla, počáteční pozici znaku a počet znaků. To lze provést buď programově, nebo v době návrhu v okně **vlastnosti** .  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Vlastnost <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> nastavte na <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>nebo <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Pokud je nastavená na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, část titulu určená pomocí <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bude podtržená jenom v případě, že se ukazatel myši nachází na jeho umístění.  
  
5. V obslužné rutině události <xref:System.Windows.Forms.LinkLabel.LinkClicked> nastavte vlastnost <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> na `true`.  
  
     V případě, že byl odkaz navštíven, je běžné jeho vzhled snadno měnit, obvykle pomocí barvy. Text se změní na barvu určenou vlastností <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>
- <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>
- [Přehled ovládacího prvku LinkLabel](linklabel-control-overview-windows-forms.md)
- [Postupy: Odkázání na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Ovládací prvek LinkLabel](linklabel-control-windows-forms.md)
