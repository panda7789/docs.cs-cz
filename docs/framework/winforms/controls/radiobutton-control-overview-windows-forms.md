---
title: RadioButton – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: bbc93046b69d39caadde4986ff56f067fc206a9e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741145"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton – přehled ovládacího prvku (Windows Forms)
Model Windows Forms <xref:System.Windows.Forms.RadioButton> ovládací prvky představují sadu dvou nebo více vzájemně se vylučujících možností pro uživatele. I když se může zdát, že přepínače a zaškrtávací políčka budou fungovat podobně, existuje důležitý rozdíl: když uživatel vybere přepínač, ostatní přepínače ve stejné skupině se nedají vybrat taky. Naopak může být vybrán libovolný počet zaškrtávacích políček. Definování skupiny přepínačů upozorní uživatele "tady je sada voleb, ze kterých můžete zvolit jednu a jenom jednu."  
  
## <a name="using-the-control"></a>Použití ovládacího prvku  
 Při kliknutí na ovládací prvek <xref:System.Windows.Forms.RadioButton>, jeho vlastnost <xref:System.Windows.Forms.RadioButton.Checked%2A> je nastavena na `true` a je volána obslužná rutina události <xref:System.Windows.Forms.Control.Click>. Událost <xref:System.Windows.Forms.RadioButton.CheckedChanged> se vyvolá při změně hodnoty vlastnosti <xref:System.Windows.Forms.RadioButton.Checked%2A>. Je-li vlastnost <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> nastavena na hodnotu `true` (výchozí možnost), dojde k automatickému vymazání výběru přepínače všech ostatních skupin ve skupině. Tato vlastnost je obvykle nastavena na hodnotu `false`, pokud se používá ověřovací kód k zajištění toho, že přepínač je vybrán jako přípustný. Text zobrazený v ovládacím prvku je nastaven pomocí vlastnosti <xref:System.Windows.Forms.Control.Text%2A>, která může obsahovat klávesové zkratky pro přístup k klávesám. Přístupový klíč umožňuje uživateli "kliknout na" ovládací prvek stisknutím klávesy ALT s přístupovým klíčem. Další informace naleznete v tématu [Postupy: vytváření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) a [Postupy: nastavení textu zobrazovaného ovládacím prvkem model Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 Ovládací prvek <xref:System.Windows.Forms.RadioButton> se může zobrazit jako příkazové tlačítko, které se zobrazí, pokud je zaškrtnuto, pokud je vlastnost <xref:System.Windows.Forms.RadioButton.Appearance%2A> nastavená na <xref:System.Windows.Forms.Appearance.Button>. Přepínače mohou také zobrazovat obrázky pomocí vlastností <xref:System.Windows.Forms.ButtonBase.Image%2A> a <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Další informace najdete v tématu [Postup: nastavení obrázku zobrazovaného ovládacím prvkem model Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RadioButton>
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Přehled ovládacího prvku GroupBox](groupbox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku CheckBox](checkbox-control-overview-windows-forms.md)
- [Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě sady](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [Ovládací prvek RadioButton](radiobutton-control-windows-forms.md)
