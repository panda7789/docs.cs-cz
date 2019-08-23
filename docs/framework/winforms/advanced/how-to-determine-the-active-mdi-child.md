---
title: 'Postupy: Určení aktivního podřízeného formuláře MDI'
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
ms.openlocfilehash: 91100b37e4cae9041479b209e40034efe376df5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946223"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Postupy: Určení aktivního podřízeného formuláře MDI
V některých případech budete chtít poskytnout příkaz, který bude fungovat na ovládacím prvku, který má fokus na aktuálně aktivním podřízeném formuláři. Předpokládejme například, že chcete zkopírovat vybraný text z textového pole podřízeného formuláře do schránky. Vytvořili jste proceduru, která zkopíruje vybraný text do schránky pomocí <xref:System.Windows.Forms.Control.Click> události položky nabídky Kopírovat v nabídce standardní úpravy.  
  
 Vzhledem k tomu, že aplikace MDI může mít mnoho instancí stejného podřízeného formuláře, procedura musí znát, který formulář se má použít. Chcete-li zadat správnou formu, <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> použijte vlastnost, která vrátí podřízený formulář, který má fokus nebo který byl naposledy aktivní.  
  
 Pokud máte ve formuláři několik ovládacích prvků, musíte také určit, který ovládací prvek je aktivní. Podobně jako <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost vrátí vlastnost ovládací prvek s fokusem na aktivním podřízeném formuláři. <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> Následující postup ukazuje postup kopírování, který lze volat z podřízené nabídky formuláře, nabídky ve formuláři MDI nebo tlačítka panelu nástrojů.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Určení aktivního podřízeného prvku MDI (zkopírování jeho textu do schránky)  
  
1. V rámci metody zkopírujte text aktivního ovládacího prvku aktivního podřízeného formuláře do schránky.  
  
    > [!NOTE]
    > Tento příklad předpokládá, že existuje nadřazený formulář MDI (`Form1`), který obsahuje jeden nebo více podřízených oken MDI <xref:System.Windows.Forms.RichTextBox> obsahující ovládací prvek. Další informace najdete v tématu [Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).  
  
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
- [Postupy: Vytvoření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Vytvořit podřízené formuláře MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Odeslat data do aktivního podřízeného rozhraní MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádat podřízené formuláře MDI](how-to-arrange-mdi-child-forms.md)
