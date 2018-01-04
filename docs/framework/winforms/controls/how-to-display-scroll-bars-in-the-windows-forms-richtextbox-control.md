---
title: "Postupy: Zobrazení posuvníků v ovládacím prvku Windows Forms RichTextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4645e502544072cbc6268ae07e054ea5450d9c5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Postupy: Zobrazení posuvníků v ovládacím prvku Windows Forms RichTextBox
Ve výchozím nastavení Windows Forms <xref:System.Windows.Forms.RichTextBox> zobrazí vodorovného a svislého posuvníky podle potřeby. Je sedm možných hodnot pro <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> řízení, které jsou popsané v následující tabulce.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Zobrazení posuvníků v ovládacím prvku RichTextBox  
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.Multiline%2A> vlastnost `true`. Žádný typ posuvník, včetně vodorovně, se zobrazí, pokud <xref:System.Windows.Forms.RichTextBox.Multiline%2A> je nastavena na `false`.  
  
2.  Nastavit <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> vlastnost, která má odpovídající hodnotu <xref:System.Windows.Forms.RichTextBoxScrollBars> výčtu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both>(výchozí)|Zobrazí vodorovné nebo svislé posuvníky nebo obojího jenom v případě, že text překračuje šířky nebo délky ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nikdy zobrazí libovolného typu posuvníku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Zobrazí vodorovného posunování panelu pouze když text překračuje šířku ovládacího prvku. (K tomu došlo, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> musí být nastavena na `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Zobrazí svislý posuvník pouze když text překračuje výšku ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Zobrazí vodorovného posuvníku při zpracování <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je nastavena na `false`. Posuvník zobrazeno šedě, když text není delší než šířka ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Vždy zobrazí svislého posuvníku. Když text není delší než délka ovládací prvek typu posuvník šedé.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Vždy zobrazí svislý posuvník. Zobrazí vodorovného posuvníku při zpracování <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je nastavena na `false`. Když text není delší než šířky nebo délky ovládacího prvku zobrazí šedým posuvníky.|  
  
3.  Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |`false`|Text v ovládacím prvku není úpravě automaticky šířku ovládacího prvku, takže ho se posuňte doprava, dokud nebude dosaženo konce řádku. Tuto hodnotu použijte, pokud jste zvolili vodorovné posuvníky nebo obojí, výše.|  
    |`true`(výchozí)|Text v ovládacím prvku je automaticky upravována podle šířky ovládacího prvku. Vodorovný posuvník se nezobrazí. Tuto hodnotu použijte, pokud jste zvolili svislé posuvníky nebo hodnotu none, výše, chcete-li zobrazit jeden nebo více odstavců.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
