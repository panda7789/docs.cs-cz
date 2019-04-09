---
title: 'Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox'
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
ms.openlocfilehash: f7a0e3a14d14f0629bd9995dbecd3f0b98bea1d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190909"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox
Ve výchozím nastavení, Windows Forms <xref:System.Windows.Forms.TextBox> ovládací prvek zobrazí jeden řádek textu a posuvníky nezobrazí. Je-li text je delší než dostupný prostor, zobrazí se pouze část textu. Toto výchozí chování můžete změnit nastavením <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnosti na odpovídající hodnoty.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Chcete-li zobrazit zalomení řádku v ovládacím prvku TextBox  
  
-   Chcete-li zobrazit návrat do více řádků <xref:System.Windows.Forms.TextBox>, použijte <xref:System.Environment.NewLine%2A> vlastnost.  
  
     Mějte na paměti, která výklad řídicí znaky (\\) je specifické pro jazyk. Jazyk Visual Basic používá `Chr$(13) & Chr$(10)` pro návrat na začátek řádku kombinaci znaků vrácených hodnot a znak odřádkování.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Chcete-li zobrazit více řádků v ovládacím prvku TextBox  
  
1.  Nastavte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`. Pokud <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je `true` (výchozí), pak textu v ovládacím prvku se zobrazí jako jeden nebo více odstavců; v opačném případě se zobrazí jako seznam, ve kterém může být některé řádky oříznut na okraji ovládacího prvku.  
  
2.  Nastavte <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnost na odpovídající hodnotu.  
  
    |Value|Popis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Tuto hodnotu použijte, pokud má být tento text odstavce, který téměř vždy vyhovovat ovládacího prvku. Uživatele můžete použít umístění ukazatele myši na pohyb uvnitř ovládacího prvku, pokud je text příliš dlouhý, chcete-li zobrazit všechny najednou.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Tuto hodnotu použijte, pokud chcete zobrazit seznam řádků, z nichž některé mohou být delší než šířka <xref:System.Windows.Forms.TextBox> ovládacího prvku.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Tuto hodnotu použijte, pokud v seznamu může být delší než výška ovládacího prvku.|  
  
3.  Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.  
  
    |Value|Popis|  
    |-----------|-----------------|  
    |`false`|Text v ovládacím prvku nebude automaticky zabalená, takže ho se posuňte doprava, dokud nebude dosaženo konce řádku. Pokud jste zvolili, používejte tuto hodnotu <xref:System.Windows.Forms.ScrollBars.Horizontal> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.Both>výše.|  
    |`true` (výchozí)|Vodorovný posuvník nezobrazí. Pokud jste zvolili, používejte tuto hodnotu <xref:System.Windows.Forms.ScrollBars.Vertical> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.None>, výše a zobrazte jeden nebo více odstavcích.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
