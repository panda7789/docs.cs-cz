---
title: "Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel"
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
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42aaef183178e7170d3046b4c5daefc8647f7cc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel
Můžete změnit textu zobrazovaného <xref:System.Windows.Forms.LinkLabel> ovládacího prvku tak, aby vyhovovala různé účely. Například je běžnou praxí informuje tak uživatele, že text sloužící nastavením text, který se zobrazí v konkrétní barvy s podtržení. Po kliknutí na text, barva se změní na jinou barvu. Za účelem řízení, můžete nastavit různé vlastnosti pět: <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, a <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnosti.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Změna vzhledu ovládacího prvku LinkLabel  
  
1.  Nastavte <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> a <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastnosti pro barev, které chcete.  
  
     To můžete provést buď programově, nebo v době návrhu v **vlastnosti** okno.  
  
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
  
2.  Nastavte <xref:System.Windows.Forms.LinkLabel.Text%2A> vlastnost, která má odpovídající titulek.  
  
     To můžete provést buď programově, nebo v době návrhu v **vlastnosti** okno.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  Nastavte <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnosti k určení, které části titulek bude uveden jako odkaz.  
  
     <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Hodnota je reprezentována pomocí <xref:System.Windows.Forms.LinkArea> obsahující dvě čísla, počáteční pozice znaku a počet znaků. To můžete provést buď programově, nebo v době návrhu v **vlastnosti** okno.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  Nastavte <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnost <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, nebo <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Pokud je nastaven na hodnotu <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, součástí titulek dáno <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bude podtržené pouze při umístění ukazatele myši na něm.  
  
5.  V <xref:System.Windows.Forms.LinkLabel.LinkClicked> nastavit popisovač události <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> vlastnost `true`.  
  
     Při navštívil odkaz je běžnou praxí změnit její vzhled nějakým způsobem, obvykle pomocí barev. Text se změní na barvu určeného <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> vlastnost.  
  
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
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [Linklabel – ovládací prvek – přehled](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Postupy: odkaz na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [Linklabel – ovládací prvek](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
