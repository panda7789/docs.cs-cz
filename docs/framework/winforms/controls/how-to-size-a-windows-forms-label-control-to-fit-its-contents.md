---
title: 'Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu
Windows Forms <xref:System.Windows.Forms.Label> ovládací prvek může být v jednom nebo více řádky, a může být buď pevnou velikost nebo můžete automaticky měnit velikost pro umístění titulek. <xref:System.Windows.Forms.Label.AutoSize%2A> Vlastnost umožňuje ovládacích prvků k přizpůsobení titulků větší nebo menší velikost, která je zvlášť užitečné, pokud titulek se změní za běhu.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Chcete-li ovládací prvek popisek dynamicky Změna velikosti podle obsahu  
  
1.  Nastavte její <xref:System.Windows.Forms.Label.AutoSize%2A> vlastnost `true`.  
  
 Pokud <xref:System.Windows.Forms.Label.AutoSize%2A> je nastaven na `false`, slova zadaný v <xref:System.Windows.Forms.Label.Text%2A> vlastnost budou zahrnovat na další řádek Pokud je to možné, ale ovládací prvek nebude zvětšovat.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Přehled ovládacího prvku Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Ovládací prvek Label](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
