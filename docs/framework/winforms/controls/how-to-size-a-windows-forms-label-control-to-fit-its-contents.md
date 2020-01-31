---
title: Velikost ovládacího prvku popisek podle jeho obsahu
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743782"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.Label> může být jednořádkový nebo víceřádkový a může být buď pevně stanovený, nebo se může automaticky změnit jeho velikost tak, aby odpovídala jeho titulku. Vlastnost <xref:System.Windows.Forms.Label.AutoSize%2A> pomáhá nastavit velikost ovládacích prvků tak, aby vyhovovala větším nebo menším titulkům, což je zvláště užitečné, pokud se titulek v době běhu změní.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Chcete-li změnit velikost ovládacího prvku popisku dynamicky tak, aby odpovídal jeho obsahu  
  
1. Vlastnost <xref:System.Windows.Forms.Label.AutoSize%2A> nastavte na `true`.  
  
 Pokud je <xref:System.Windows.Forms.Label.AutoSize%2A> nastaveno na hodnotu `false`, slova zadaná ve vlastnosti <xref:System.Windows.Forms.Label.Text%2A> budou zabalena do dalšího řádku, pokud je to možné, ale ovládací prvek se nebude zvětšovat.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Přehled ovládacího prvku Label](label-control-overview-windows-forms.md)
- [Ovládací prvek Label](label-control-windows-forms.md)
