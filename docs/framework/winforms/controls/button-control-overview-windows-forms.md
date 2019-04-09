---
title: Přehled ovládacího prvku Tlačítko (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 1ded871fdfab83407d8022ca0c4ce6b2c8a6c67c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076546"
---
# <a name="button-control-overview-windows-forms"></a>Přehled ovládacího prvku Tlačítko (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Button> ovládací prvek umožňuje uživateli klikněte na něj k provedení akce. Při kliknutí na tlačítko vypadat jako v případě, že je se vložil do a všeobecně dostupné. Pokaždé, když uživatel klikne na tlačítko <xref:System.Windows.Forms.Control.Click> je vyvolána obslužná rutina události. V kódu <xref:System.Windows.Forms.Control.Click> obslužná rutina události provádět veškeré akce zvolíte.  
  
 Text zobrazený na tlačítku pro obsažený v <xref:System.Windows.Forms.Control.Text%2A> vlastnost. Pokud text přesahuje šířku tlačítka, se zalomí na další řádek. Nicméně bude oříznut Pokud ovládací prvek nemůže pojmout celková výška. Další informace najdete v tématu [jak: Nastavit Text, zobrazený Windows Forms ovládací prvek](how-to-set-the-text-displayed-by-a-windows-forms-control.md). <xref:System.Windows.Forms.Control.Text%2A> Vlastnost může obsahovat přístupový kód, který umožňuje uživateli "klikněte" ovládací prvek pomocí klávesy ALT přístupovým klíčem. Podrobnosti najdete v tématu [jak: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md). Řídí vzhled textu <xref:System.Windows.Forms.Control.Font%2A> vlastnost a <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> vlastnost.  
  
 <xref:System.Windows.Forms.Button> Ovládací prvek mohl zobrazit také pomocí bitové kopie <xref:System.Windows.Forms.ButtonBase.Image%2A> a <xref:System.Windows.Forms.ButtonBase.ImageList%2A> vlastnosti. Další informace najdete v tématu [jak: Nastavení obrázku zobrazovaného podle Windows Forms ovládací prvek](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Button>
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
