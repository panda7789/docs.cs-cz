---
title: 'Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 07355be0809f3dde480cf14b39e26a4266c4d936
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877394"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře
Ovládací prvky Windows Forms obvykle zobrazí text, který souvisí s primární funkce ovládacího prvku. Například <xref:System.Windows.Forms.Button> ovládací prvek zobrazí obvykle titulek, která určuje, jaká akce se provede při kliknutí na tlačítko. Pro všechny ovládací prvky, můžete nastavit nebo načíst text pomocí <xref:System.Windows.Forms.Control.Text%2A> vlastnost. Můžete změnit písmo pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnost.  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>Chcete-li nastavit text a písma pomocí návrháře  
  
1. V okně Vlastnosti nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost ovládacího prvku na odpovídající řetězec.  
  
     Chcete-li vytvořit podtržené klávesovou zkratku, obsahuje znak ampersand (&) před písmenem, který bude klávesovou zkratku.  
  
2.  V okně Vlastnosti klikněte na tlačítko se třemi tečkami (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle položky <xref:System.Windows.Forms.Control.Font%2A> vlastnost.  
  
     V dialogovém okně Standardní písmo vyberte písmo, styl písma, velikost, efektů (například podtržení nebo přeškrtnutí) a skriptů, které chcete.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Nastavit Text, zobrazený ovládacím prvkem Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Použití písem a textu](../advanced/using-fonts-and-text.md)
- [Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
