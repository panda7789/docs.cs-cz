---
title: 'Postupy: Určení podřízeného prvku aktivního MDI'
ms.date: 03/30/2017
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
ms.openlocfilehash: 95958491d624052922df9af37b188b9515480397
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714320"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Postupy: Určení podřízeného prvku aktivního MDI
V některých případech budete chtít zadat příkaz, který funguje na ovládací prvek, který má fokus na aktuálně aktivní podřízený formulář. Předpokládejme například, že chcete Zkopírování vybraného textu do schránky z podřízeného formuláře, textového pole. Vytvoříte procedury, která zkopíruje vybraný text do schránky pomocí <xref:System.Windows.Forms.Control.Click> události položky nabídky kopírování ve standardní nabídce Úpravy.  
  
 Protože aplikace MDI může mít mnoho instancí stejné podřízeného formuláře, postup je potřeba vědět, jaký tvar používat. Chcete-li určit správný tvar, použijte <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, která vrací podřízeného formuláře, který má fokus nebo, který byl nedávno aktivní.  
  
 Až budete mít několik ovládacích prvků ve formuláři, musíte také určit, který ovládací prvek je aktivní. Podobně jako <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> vlastnost, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vrátí vlastnost ovládacího prvku se zaměřuje na aktivní podřízený formulář. Následující postup ukazuje kopírování procedury, která může být volána z podřízených nabídky formuláře nabídek MDI formuláře nebo tlačítko panelu nástrojů.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>K určení podřízeného prvku aktivního MDI (ke zkopírování textu do schránky.)  
  
1.  V rámci metody zkopírujte text aktivním ovládacím prvkem aktivní podřízený formulář do schránky.  
  
    > [!NOTE]
    >  Tento příklad předpokládá, že je nadřazený formulář MDI (`Form1`), který má jeden nebo více podřízených oken MDI obsahující <xref:System.Windows.Forms.RichTextBox> ovládacího prvku. Další informace najdete v tématu [vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Viz také:
- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)
