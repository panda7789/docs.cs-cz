---
title: "Postupy: Určení podřízeného prvku aktivního MDI"
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
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c026df631c2ac033594ea86887bb8440a6aa240a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a>Postupy: Určení podřízeného prvku aktivního MDI
V některých případech budete chtít zadat příkaz, který funguje na ovládací prvek, který má právě fokus na formuláři aktuálně aktivních podřízených. Předpokládejme například, že chcete kopírovat vybraný text z textového pole podřízené formuláře do schránky. By vytvoření procedury, která zkopíruje vybraný text do schránky pomocí <xref:System.Windows.Forms.Control.Click> událostí kopírovat položky nabídky v nabídce standardní upravit.  
  
 Vzhledem k tomu, že aplikace MDI může mít velký počet instancí stejného formuláře podřízené, postup je potřeba vědět, jaký typ používat. Pokud chcete zadat správném tvaru, použijte <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, která vrací podřízené formuláře v aktivním nebo který byl nedávno aktivní.  
  
 Pokud máte několik ovládací prvky ve formuláři, musíte také určit, které řízení je aktivní. Podobně jako <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost vrací s fokusem ovládacího prvku na formuláři aktivních podřízených. Následující postup ukazuje postup kopírování, kterou lze volat z podřízené formuláře nabídky, nabídky na formuláře MDI nebo tlačítka panelu nástrojů.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>K určení aktivního podřízeného MDI (Chcete-li do schránky zkopírujte jeho text)  
  
1.  V rámci metodu zkopírujte text active ovládacího prvku formuláře aktivních podřízených do schránky.  
  
    > [!NOTE]
    >  Příklad předpokládá, že je nadřazené formuláře MDI (`Form1`) má jednu nebo více podřízených oken MDI obsahující <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Další informace najdete v tématu [vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Aplikace MDI (Multiple-Document Interface)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Postupy: Vytváření nadřazených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Postupy: Vytváření podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Postupy: Odesílání dat do aktivního podřízeného MDI](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Postupy: Uspořádání podřízených formulářů MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
