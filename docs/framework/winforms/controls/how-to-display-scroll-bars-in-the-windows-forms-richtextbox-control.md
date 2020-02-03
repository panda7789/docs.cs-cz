---
title: Zobrazit posuvníky v ovládacím prvku RichTextBox
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 2185b572ef20765043d3df3dbfd8bf5b21cfac28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745565"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Postupy: Zobrazení posuvníků v ovládacím prvku Windows Forms RichTextBox
Ve výchozím nastavení ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> v případě potřeby zobrazuje vodorovně a svisle posuvníky. Pro vlastnost <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox> existuje Sedm možných hodnot, které jsou popsány v následující tabulce.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Zobrazení posuvníků v ovládacím prvku RichTextBox  
  
1. Vlastnost <xref:System.Windows.Forms.RichTextBox.Multiline%2A> nastavte na hodnotu `true`. Pokud je vlastnost <xref:System.Windows.Forms.RichTextBox.Multiline%2A> nastavená na `false`, zobrazí se žádný typ posuvníku, včetně vodorovné čáry.  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> na odpovídající hodnotu výčtu <xref:System.Windows.Forms.RichTextBoxScrollBars>.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (výchozí)|Zobrazí vodorovné nebo svislé posuvníky nebo obojí, pouze když text překračuje šířku nebo délku ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Nikdy nezobrazuje žádný typ posouvanýho posuvníku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Zobrazí vodorovný posuvník pouze v případě, že text přesahuje šířku ovládacího prvku. (Aby k tomu mohlo dojít, vlastnost <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> musí být nastavena na hodnotu `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Zobrazí svislý posuvník pouze v případě, že text překračuje výšku ovládacího prvku.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Zobrazí vodorovný posuvník, pokud je vlastnost <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> nastavena na hodnotu `false`. Pokud text nepřekračuje šířku ovládacího prvku, zobrazí se posuvník šedě.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Vždy zobrazí svislý posuvník. Pokud text nepřekračuje délku ovládacího prvku, zobrazí se posuvník šedě.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Vždy zobrazí svislý posuvník. Zobrazí vodorovný posuvník, pokud je vlastnost <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> nastavena na hodnotu `false`. Pokud text nepřekračuje šířku nebo délku ovládacího prvku, zobrazí se posuvníky šedě.|  
  
3. Vlastnost <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> nastavte na odpovídající hodnotu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |`false`|Text v ovládacím prvku není automaticky upravován tak, aby odpovídal šířce ovládacího prvku, takže se posune napravo, dokud se nedosáhne konce řádku. Tuto hodnotu použijte, pokud jste vybrali vodorovné posuvníky nebo obě.|  
    |`true` (výchozí)|Text v ovládacím prvku se automaticky upraví tak, aby odpovídal šířce ovládacího prvku. Vodorovný posuvník se nezobrazí. Tuto hodnotu použijte, pokud jste vybrali svislé posuvníky nebo žádné, nahoře, aby se zobrazil jeden nebo více odstavců.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
