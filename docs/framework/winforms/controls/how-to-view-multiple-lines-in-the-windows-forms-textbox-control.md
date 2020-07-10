---
title: Zobrazit více řádků v ovládacím prvku TextBox
description: Přečtěte si, jak zobrazit více řádků v ovládacím prvku model Windows Forms TextBox nastavením vlastností víceřádkových, WordWrap a ScrollBar.
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174468"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox
Ve výchozím nastavení model Windows Forms <xref:System.Windows.Forms.TextBox> ovládací prvek zobrazuje jeden řádek textu a nezobrazuje posuvníky. Pokud je text delší než dostupný prostor, je viditelná pouze část textu. Toto výchozí chování můžete změnit nastavením <xref:System.Windows.Forms.TextBox.Multiline%2A> <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastností, a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> na příslušné hodnoty.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Zobrazení návratového znaku v ovládacím prvku TextBox  
  
- Chcete-li zobrazit návrat vozíku na více řádků <xref:System.Windows.Forms.TextBox> , použijte <xref:System.Environment.NewLine%2A> vlastnost.  
  
     Upozorňujeme, že výklad řídicích znaků ( \\ ) je specifický pro jazyk. Visual Basic používá `Chr$(13) & Chr$(10)` kombinaci znaků pro návrat na začátek řádku a znak odřádkování.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Zobrazení více řádků v ovládacím prvku TextBox  
  
1. Nastavte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost na hodnotu `true` . Pokud <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je `true` (výchozí), pak se text v ovládacím prvku zobrazí jako jeden nebo více odstavců. v opačném případě se zobrazí jako seznam, ve kterém mohou být některé řádky oříznuty na okraji ovládacího prvku.  
  
2. Nastavte <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnost na odpovídající hodnotu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Tuto hodnotu použijte, pokud bude text odstavcem, který téměř vždy odpovídá ovládacímu prvku. Uživatel může použít ukazatel myši k přesunu uvnitř ovládacího prvku, pokud je text příliš dlouhý pro zobrazení všech najednou.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Tuto hodnotu použijte, pokud chcete zobrazit seznam řádků, některé z nich mohou být delší než šířka <xref:System.Windows.Forms.TextBox> ovládacího prvku.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Tuto hodnotu použijte, pokud seznam může být delší než výška ovládacího prvku.|  
  
3. Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |`false`|Text v ovládacím prvku nebude automaticky zabalen, takže se posune doprava, dokud není dosaženo konce řádku. Tuto hodnotu použijte, pokud jste zvolili <xref:System.Windows.Forms.ScrollBars.Horizontal> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.Both> nahoře.|  
    |`true`výchozí|Vodorovný posuvník se nezobrazí. Tuto hodnotu použijte, pokud vyberete <xref:System.Windows.Forms.ScrollBars.Vertical> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.None> nahoře a zobrazíte jeden nebo více odstavců.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox – ovládací prvek](textbox-control-windows-forms.md)
