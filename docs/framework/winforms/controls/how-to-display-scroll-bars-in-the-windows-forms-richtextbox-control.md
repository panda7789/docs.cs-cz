---
title: 'Postupy: Zobrazení posuvníků v Windows Forms RichTextBox – ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 6b6cfb8c21c8f3a48bb85a0591f3390d5b5575b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610393"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Postupy: Zobrazení posuvníků v Windows Forms RichTextBox – ovládací prvek
Ve výchozím nastavení, Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek zobrazí vodorovný a svislý posuvník podle potřeby. Existuje sedm možných hodnot <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> vlastnost <xref:System.Windows.Forms.RichTextBox> ovládacího prvku, které jsou popsány v následující tabulce.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Zobrazení posuvníků v ovládacím prvku RichTextBox  
  
1.  Nastavte <xref:System.Windows.Forms.RichTextBox.Multiline%2A> vlastnost `true`. Žádný typ posuvník, včetně vodorovně, se zobrazí, pokud <xref:System.Windows.Forms.RichTextBox.Multiline%2A> je nastavena na `false`.  
  
2.  Nastavit <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> vlastnost na příslušnou hodnotu <xref:System.Windows.Forms.RichTextBoxScrollBars> výčtu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (výchozí)|Zobrazí vodorovný nebo svislý posuvník nebo obojí, jenom v případě, že text přesahuje šířky nebo délky ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nikdy nezobrazí libovolného typu posuvník.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Zobrazí vodorovný posuvník, pouze když text přesahuje šířku ovládacího prvku. (K tomu došlo, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> musí být vlastnost nastavena na `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Zobrazí svislý posuvník, pouze když text překračuje výšku ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Zobrazí vodorovného posuvníku při <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je nastavena na `false`. Posuvníku se zobrazí šedě, když text není delší než šířka ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Vždy zobrazí svislý posuvník. Posuvníku se zobrazí šedě, když text není delší než délka ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Vždy zobrazí svislý posuvník. Zobrazí vodorovného posuvníku při <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je nastavena na `false`. Když text není delší než šířka nebo délka ovládacího prvku se zobrazí šedě posuvníky.|  
  
3.  Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |`false`|Text v ovládacím prvku není automaticky upraven na šířku ovládacího prvku, takže ho se posuňte doprava, dokud nebude dosaženo konce řádku. Tuto hodnotu použijte, pokud jste zvolili vodorovným posuvníkům nebo obojí, výše.|  
    |`true` (výchozí)|Text v ovládacím prvku se automaticky upraví na šířku ovládacího prvku. Vodorovný posuvník nezobrazí. Tuto hodnotu použijte, pokud jste zvolili svislé posuvníky nebo none, výše, chcete-li zobrazit jeden nebo více odstavců.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
