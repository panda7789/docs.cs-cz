---
title: Zobrazení webové stránky z ovládacího prvku LinkLabel (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: 75373d55b7bc5ef11e39d5b9546996cb1c4f6f7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745929"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Postupy: Zobrazení webové stránky z ovládacího prvku Windows Forms LinkLabel (Visual Basic)
Tento příklad zobrazí webovou stránku ve výchozím prohlížeči, když uživatel klikne na ovládací prvek <xref:System.Windows.Forms.LinkLabel> model Windows Forms.  
  
## <a name="example"></a>Příklad  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Formulář Windows s názvem `Form1`.  
  
- <xref:System.Windows.Forms.LinkLabel> ovládací prvek s názvem `LinkLabel1`.  
  
- Aktivní připojení k Internetu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání metody <xref:System.Diagnostics.Process.Start%2A> vyžaduje úplný vztah důvěryhodnosti. Další informace najdete v tématu <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.LinkLabel>
- [Ovládací prvek LinkLabel](linklabel-control-windows-forms.md)
