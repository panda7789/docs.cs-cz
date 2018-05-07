---
title: 'Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 7c4c9362bb5a32bd8d5afc2b1edeb935d505fd19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> spoustu možností pro formátování textu, zobrazí se má ovládací prvek. Lze vytvořit vybrané znaků tučné nebo kurzívy, pomocí <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> vlastnost. Tato vlastnost také můžete změnit velikost a řez písma vybraných znaků. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Vlastnost umožňuje změnit barvu vybrané znaky.  
  
### <a name="to-change-the-appearance-of-characters"></a>Chcete-li změnit vzhled znaků  
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> vlastnost pro příslušné písmo.  
  
     Pokud chcete povolit uživatelům nastavení rodiny písem, velikost a řez písma v aplikaci, obvykle použijete <xref:System.Windows.Forms.FontDialog> součásti. Přehled najdete v tématu [FontDialog – přehled komponenty](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> vlastnost, která má odpovídající barev.  
  
     Pokud chcete povolit uživatelům nastavení barvy v aplikaci, obvykle použijete <xref:System.Windows.Forms.ColorDialog> součásti. Přehled najdete v tématu [ColorDialog – přehled komponenty](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  Tyto vlastnosti ovlivňují jenom vybraný text nebo, pokud není vybraný žádný text, text, který je typu na aktuální pozici kurzoru. Informace o výběr textu pomocí programu najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox>  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
