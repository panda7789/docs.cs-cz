---
title: 'Postupy: Velikost ovládacího prvku Windows Forms Label k zobrazení jeho obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 5771b232d77e3e5a792b179ebffd3fa0edda7c9b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702191"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Postupy: Velikost ovládacího prvku Windows Forms Label k zobrazení jeho obsahu
Windows Forms <xref:System.Windows.Forms.Label> ovládací prvek může být jednořádkové nebo víceřádkové, a může být buď pevnou velikost nebo můžete automaticky měnit velikost tak, aby vyhovovaly titulek. <xref:System.Windows.Forms.Label.AutoSize%2A> Vlastnost umožňuje velikost ovládacích prvků podle větší nebo menší popisky, které je zvláště užitečný, pokud popisek se změní za běhu.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Chcete-li změnit dynamicky velikost podle svého obsahu ovládacího prvku popisek  
  
1.  Nastavte jeho <xref:System.Windows.Forms.Label.AutoSize%2A> vlastnost `true`.  
  
 Pokud <xref:System.Windows.Forms.Label.AutoSize%2A> je nastavena na `false`, v zadaných slov <xref:System.Windows.Forms.Label.Text%2A> vlastnost se zalomí na další řádek Pokud je to možné, ale nebude zvětšovat ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Přehled ovládacího prvku Label](label-control-overview-windows-forms.md)
- [Ovládací prvek Label](label-control-windows-forms.md)
