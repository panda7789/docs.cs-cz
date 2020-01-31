---
title: Nastavení atributů písma pro ovládací prvek RichTextBox
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
ms.openlocfilehash: f27256c155223df576ee3c42e6bf65270c870b0f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744863"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Postupy: Nastavení atributů písma pro ovládací prvek Windows Forms RichTextBox
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> má mnoho možností formátování textu, který zobrazuje. Vybrané znaky můžete nastavit jako tučné, podtržené nebo kurzívu pomocí vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>. Tuto vlastnost můžete také použít ke změně velikosti a řezu písma vybraných znaků. Vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> umožňuje změnit barvu vybraných znaků.  
  
### <a name="to-change-the-appearance-of-characters"></a>Změna vzhledu znaků  
  
1. Vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> nastavte na příslušné písmo.  
  
     Pokud chcete uživatelům umožnit, aby v aplikaci nastavili rodinu písem, velikost a řez písma, obvykle byste použili komponentu <xref:System.Windows.Forms.FontDialog>. Přehled naleznete v tématu [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).  
  
2. Vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> nastavte na odpovídající barvu.  
  
     Chcete-li uživatelům umožnit nastavení barev v aplikaci, obvykle byste použili komponentu <xref:System.Windows.Forms.ColorDialog>. Přehled naleznete v tématu [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).  
  
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
    > Tyto vlastnosti ovlivní pouze vybraný text, nebo, pokud není vybrán žádný text, text, který je zadán v aktuálním umístění bodu vložení. Informace o tom, jak text programově vybírat, najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
