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
ms.openlocfilehash: 4919e94c23b1a67680ea0f360304ee0f75c7f425
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963226"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox
Ovládací prvek <xref:System.Windows.Forms.RichTextBox> model Windows Forms má mnoho možností formátování textu, který zobrazuje. Můžete nastavit vybrané znaky tučně, podtržené nebo kurzívou pomocí <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> vlastnosti. Tuto vlastnost můžete také použít ke změně velikosti a řezu písma vybraných znaků. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Vlastnost umožňuje změnit barvu vybraných znaků.  
  
### <a name="to-change-the-appearance-of-characters"></a>Změna vzhledu znaků  
  
1. <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> Nastavte vlastnost na příslušné písmo.  
  
     Pokud chcete uživatelům umožnit, aby v aplikaci nastavili rodinu písem, velikost a řez písma, obvykle tuto <xref:System.Windows.Forms.FontDialog> komponentu použijete. Přehled naleznete v tématu [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).  
  
2. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Nastavte vlastnost na vhodnou barvu.  
  
     Chcete-li uživatelům povolit nastavení barev v aplikaci, obvykle byste tuto <xref:System.Windows.Forms.ColorDialog> komponentu používali. Přehled naleznete v tématu [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).  
  
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
    > Tyto vlastnosti ovlivní pouze vybraný text, nebo, pokud není vybrán žádný text, text, který je zadán v aktuálním umístění bodu vložení. Informace o tom, jak text programově vybírat <xref:System.Windows.Forms.TextBoxBase.Select%2A>, najdete v tématu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
