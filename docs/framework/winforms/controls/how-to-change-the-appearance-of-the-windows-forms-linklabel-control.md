---
title: 'Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel'
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
ms.openlocfilehash: f0a5805561509501ca38a7fec6b4731af190e3c3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322014"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel
Můžete změnit text, zobrazený <xref:System.Windows.Forms.LinkLabel> ovládacího prvku tak, aby odpovídala různé účely. Například je běžnou praxí do značí, že text dá kliknout nastavením text, který se zobrazí v určité barvy s podtržení. Po kliknutí text, barva se změní na jinou barvu. A řídit tak toto chování, můžete nastavit různé vlastnosti pět: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnosti.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Chcete-li změnit vzhled ovládacího prvku LinkLabel  
  
1. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastností požadované barvy.  
  
     To lze provést buď programově, nebo v době návrhu v **vlastnosti** okna.  
  
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
  
2. Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnosti k odpovídající titulek.  
  
     To lze provést buď programově, nebo v době návrhu v **vlastnosti** okna.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> a určí, které části popisek bude uveden jako odkaz.  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Hodnota je vyjádřena pomocí <xref:System.Windows.Forms.LinkArea> obsahující dvě čísla, počáteční pozici znaku a počet znaků. To lze provést buď programově, nebo v době návrhu v **vlastnosti** okna.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4. Nastavte <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnost <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, nebo <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Pokud je nastavena na <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, část titulek určené <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bude podtržené pouze při umístění ukazatele myši na něj.  
  
5. V <xref:System.Windows.Forms.LinkLabel.LinkClicked> nastavena obslužná rutina události, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true`.  
  
     Při odkazu po navštívení, je obvyklé, chcete-li změnit její vzhled nějakým způsobem, obvykle pomocí barev. Text se změní barva určená <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastnost.  
  
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
