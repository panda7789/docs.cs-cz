---
title: 'Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 4cb9b351b5ed1ab9cd05be0763d967000791fb46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140644"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek má mnoho možností pro formátování textu se zobrazí. Vybrané odstavce jako seznamy s odrážkami můžete naformátovat tak, že nastavíte <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost. Můžete také použít <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnosti nastavení odsazení odstavce doleva a pravého okraje ovládacího prvku a levým okrajem dalších řádků textu.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>K formátování odstavce jako seznam s odrážkami  
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost `true`.  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>Odsazení odstavce  
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levým okrajem text.  
  
2.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem první řádek textu odstavce a levým okrajem následující řádky ve stejném paragraph. Hodnota <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost platí jenom pro řádky v odstavci zabalené pod první řádek.  
  
3.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravým okrajem text.  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  Všechny tyto vlastnosti ovlivňují všechny odstavce, které obsahují vybraný text a také text, který je zadán po do aktuálního místa vložení. Například když uživatel vybere slova v rámci odstavce a poté nastaví odsazení, nové nastavení bude použito celý odstavec obsahující toto slovo a také všechny odstavce následně zadaných po vybraný odstavec. Informace o výběr textu pomocí programu najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
