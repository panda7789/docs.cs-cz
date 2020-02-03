---
title: Přehled ovládacího prvku Button
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 4ba7b333e5414efb4814d64ce50c55e08b27f859
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747078"
---
# <a name="button-control-overview-windows-forms"></a>Přehled ovládacího prvku Tlačítko (Windows Forms)
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.Button> umožňuje uživateli kliknout na něj a provést akci. Po kliknutí na tlačítko vypadá jako při vložení a vydání. Vždy, když uživatel klikne na tlačítko, je vyvolána obslužná rutina události <xref:System.Windows.Forms.Control.Click>. Do obslužné rutiny události <xref:System.Windows.Forms.Control.Click> umístíte kód pro provedení libovolné akce, kterou zvolíte.  
  
 Text zobrazený na tlačítku je obsažený ve vlastnosti <xref:System.Windows.Forms.Control.Text%2A>. Pokud text přesahuje šířku tlačítka, bude zalomen na další řádek. Ale bude oříznutý, pokud ovládací prvek nemůže přizpůsobit svou celkovou výšku. Další informace naleznete v tématu [How to: set a text zobrazený ovládacím prvkem model Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md). Vlastnost <xref:System.Windows.Forms.Control.Text%2A> může obsahovat přístupový klíč, který uživateli umožňuje "kliknout" na ovládací prvek stisknutím klávesy ALT s přístupovým klíčem. Podrobnosti najdete v tématu [Postupy: vytváření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md). Vzhled textu je řízen vlastností <xref:System.Windows.Forms.Control.Font%2A> a vlastností <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>.  
  
 <xref:System.Windows.Forms.Button> ovládací prvek lze také použít k zobrazení obrázků pomocí vlastností <xref:System.Windows.Forms.ButtonBase.Image%2A> a <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Další informace najdete v tématu [Postup: nastavení obrázku zobrazovaného ovládacím prvkem model Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Button>
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
