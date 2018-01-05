---
title: "Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dca8d0f869702dee50bf851a2099317c45aa842
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox
Ve výchozím nastavení Windows Forms <xref:System.Windows.Forms.TextBox> řízení pouze jeden řádek textu a nemá zobrazovat posuvníky. Je-li text je delší než dostupné místo, zobrazí se jenom část textu. Toto výchozí chování můžete změnit nastavením <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnosti odpovídající hodnoty.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Chcete-li zobrazit návrat v ovládacím prvku TextBox  
  
-   K zobrazení návrat více řádků <xref:System.Windows.Forms.TextBox>, použijte <xref:System.Environment.NewLine%2A> vlastnost.  
  
     Mějte na paměti, výklad řídicí znaky (\\) je konkrétní jazyk. Visual Basic používá `Chr$(13) & Chr$(10)` pro kombinace znaků CR vrátit a konce řádku znak.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Chcete-li zobrazit více řádků v ovládacím prvku TextBox  
  
1.  Nastavte <xref:System.Windows.Forms.TextBox.Multiline%2A> vlastnost `true`. Pokud <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> je `true` (výchozí), pak bude v ovládacím prvku text jako jeden nebo více odstavců; v opačném případě se zobrazí jako seznam, ve kterém mohou být některé řádky oříznut na hranici řízení.  
  
2.  Nastavte <xref:System.Windows.Forms.TextBox.ScrollBars%2A> vlastnost na odpovídající hodnotu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Tuto hodnotu použijte, pokud má být tento text odstavce, téměř vždy vyhovuje ovládacího prvku. Uživatel může použít ukazatel myši pohyb v prvku, pokud je text příliš dlouhý pro zobrazení všechny najednou.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Tuto hodnotu použijte, pokud chcete zobrazit seznam řádků, některé z nich může být delší než šířka <xref:System.Windows.Forms.TextBox> ovládacího prvku.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Tuto hodnotu použijte, pokud v seznamu může být delší než výška ovládacího prvku.|  
  
3.  Nastavte <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> vlastnost na odpovídající hodnotu.  
  
    |Hodnota|Popis|  
    |-----------|-----------------|  
    |`false`|Text v ovládacím prvku nebude automaticky zabalená, takže ho se posuňte doprava, dokud nebude dosaženo konce řádku. Tuto hodnotu použijte, pokud jste zvolili <xref:System.Windows.Forms.ScrollBars.Horizontal> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.Both>výše.|  
    |`true`(výchozí)|Vodorovný posuvník se nezobrazí. Tuto hodnotu použijte, pokud jste zvolili <xref:System.Windows.Forms.ScrollBars.Vertical> posuvníky nebo <xref:System.Windows.Forms.ScrollBars.None>, výše a zobrazte jeden nebo více odstavců.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 [Přehled ovládacího prvku TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole určeného jen pro čtení](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Postupy: Vkládání uvozovek do řetězce](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
