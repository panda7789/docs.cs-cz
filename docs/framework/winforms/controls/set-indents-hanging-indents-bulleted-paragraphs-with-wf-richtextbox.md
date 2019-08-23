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
ms.openlocfilehash: 9d095e3561cd346e6dbd99d1be7468f6ad5725a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960457"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Postupy: Nastavení odsazení, předsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox
Ovládací prvek <xref:System.Windows.Forms.RichTextBox> model Windows Forms má mnoho možností formátování textu, který zobrazuje. Vybrané odstavce můžete formátovat jako seznamy s odrážkami nastavením <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnosti. Pomocí <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>vlastností, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> můžete také nastavit odsazení odstavců vzhledem k levému a pravému okraji ovládacího prvku a levý okraj dalších řádků textu.  
  
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
  
1. <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> Nastavte vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levým okrajem textu.  
  
2. <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> Nastavte vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem prvního řádku textu v odstavci a levým okrajem dalších řádků ve stejném odstavci. Hodnota <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnosti se vztahuje pouze na řádky v odstavci, které jsou zabaleny pod prvním řádkem.  
  
3. <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> Nastavte vlastnost na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravým okrajem textu.  
  
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
    > Všechny tyto vlastnosti mají vliv na všechny odstavce obsahující vybraný text a také na text, který je zadán po aktuálním místě vložení. Když třeba uživatel vybere slovo v rámci odstavce a pak upraví odsazení, bude se nové nastavení vztahovat na celý odstavec, který obsahuje toto slovo, a také na jakékoli odstavce, které se následně zadaly po vybraném odstavci. Informace o tom, jak text programově vybírat <xref:System.Windows.Forms.TextBoxBase.Select%2A>, najdete v tématu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
