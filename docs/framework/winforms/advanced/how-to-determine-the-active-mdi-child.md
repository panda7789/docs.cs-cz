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
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182549"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Postupy: Určení podřízeného prvku aktivního MDI
V některých případech budete chtít poskytnout příkaz, který pracuje na ovládací prvek, který má fokus na aktuálně aktivní podřízený formulář. Předpokládejme například, že chcete zkopírovat vybraný text z textového pole podřízeného formuláře do schránky. Vytvořili byste proceduru, která zkopíruje vybraný <xref:System.Windows.Forms.Control.Click> text do schránky pomocí události položky nabídky Kopírovat ve standardní nabídce Úpravy.  
  
 Vzhledem k tomu, že aplikace MDI může mít mnoho instancí stejnépodřízené ho formuláře, postup potřebuje vědět, který formulář použít. Chcete-li zadat správný <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> formulář, použijte vlastnost, která vrátí podřízený formulář, který má fokus nebo který byl naposledy aktivní.  
  
 Pokud máte ve formuláři několik ovládacích prvků, musíte také určit, který ovládací prvek je aktivní. Stejně <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> jako <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> vlastnost, vlastnost vrátí ovládací prvek se zaměřením na aktivní podřízený formulář. Následující postup ilustruje postup kopírování, který lze volat z nabídky podřízeného formuláře, nabídky ve formuláři MDI nebo tlačítka panelu nástrojů.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Chcete-li zjistit aktivní podřízenou položku MDI (zkopírovat jeho text do schránky)  
  
1. V rámci metody zkopírujte text aktivního ovládacího prvku aktivního podřízeného formuláře do schránky.  
  
    > [!NOTE]
    > Tento příklad předpokládá, že existuje nadřazený formulář MDI (`Form1`), <xref:System.Windows.Forms.RichTextBox> který má jedno nebo více podřízených oken MDI obsahující chod ovládacího prvku. Další informace naleznete v [tématu Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md).  
  
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

- [Aplikace MDI (Multiple-Document Interface)](multiple-document-interface-mdi-applications.md)
- [Postupy: Vytváření nadřazených formulářů MDI](how-to-create-mdi-parent-forms.md)
- [Postupy: Vytváření podřízených formulářů MDI](how-to-create-mdi-child-forms.md)
- [Postupy: Odesílání dat do aktivního podřízeného MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Postupy: Uspořádání podřízených formulářů MDI](how-to-arrange-mdi-child-forms.md)
