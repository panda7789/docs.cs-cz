---
title: "Postupy: Nastavení odsazení, ukotvených odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox"
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
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1349e86ecd04c0d4e394e7939996c3e717e841e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Postupy: Nastavení odsazení, ukotvených odsazení a odstavců s odrážkami pomocí ovládacího prvku Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> spoustu možností pro formátování textu, zobrazí se má ovládací prvek. Vybrané odstavce dokáže formátovat jako seznamy s odrážkami nastavením <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> vlastnost. Můžete také <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, a <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnosti, které chcete nastavit odsazení odstavce vzhledem ke levé a pravé hrany ovládacího prvku a levý okraj dalších řádků textu.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Formátování odstavce jako seznam s odrážkami  
  
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
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levým okrajem ovládacího prvku a levém okraji textu.  
  
2.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi levý okraj prvního řádku text odstavce a levý okraj následující řádky ve stejné odstavce. Hodnota <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> vlastnost se vztahuje jenom na řádky v odstavci, které mají zabalené pod první řádek.  
  
3.  Nastavte <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> vlastnost na celé číslo představující vzdálenost v pixelech mezi pravým okrajem ovládacího prvku a pravý okraj textu.  
  
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
    >  Všechny tyto vlastnosti ovlivňují všechny odstavců, které obsahují vybraný text a také text, který je zadán po aktuální kurzor. Například pokud uživatel vybere možnost aplikace word v rámci odstavce a pak upraví odsazení, nové nastavení bude použito na celý odstavec, který obsahuje aplikace word a také na všechny odstavce následně zadali po vybraného odstavce. Informace o výběr textu pomocí programu najdete v tématu <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox>  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
