---
title: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku RichTextBox
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
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743015"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Postupy: Nastavení odsazení, ukotvených odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> má mnoho možností formátování textu, který zobrazuje. Vybrané odstavce můžete formátovat jako seznamy s odrážkami nastavením vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>. Pomocí vlastností <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> můžete také nastavit odsazení odstavců vzhledem k levému a pravému okraji ovládacího prvku a levý okraj dalších řádků textu.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Formátování odstavce jako seznamu s odrážkami  
  
1. Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost `true`.  
  
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
  
1. Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levým okrajem textu.  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> na celé číslo představující vzdálenost v pixelech mezi levým okrajem prvního řádku textu v odstavci a levým okrajem dalších řádků ve stejném odstavci. Hodnota vlastnosti <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> se vztahuje pouze na řádky v odstavci, které jsou zabaleny pod prvním řádkem.  
  
3. Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravým okrajem textu.  
  
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
    > Všechny tyto vlastnosti mají vliv na všechny odstavce obsahující vybraný text a také na text, který je zadán po aktuálním místě vložení. Když třeba uživatel vybere slovo v rámci odstavce a pak upraví odsazení, bude se nové nastavení vztahovat na celý odstavec, který obsahuje toto slovo, a také na jakékoli odstavce, které se následně zadaly po vybraném odstavci. Informace o tom, jak text programově vybírat, najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
