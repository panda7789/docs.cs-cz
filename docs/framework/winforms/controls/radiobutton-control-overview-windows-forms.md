---
title: RadioButton – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: 1210658226d9bcacbf4904fdc90a9908c34f5b73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129113"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> ovládací prvky poskytují sadu vzájemně se vylučující možnosti dva nebo více uživateli. Zatímco přepínací tlačítka a zaškrtávací políčka může zdát, podobně jako funkce, je důležitý rozdíl: když uživatel vybere přepínací tlačítko, také nelze vybrat dalších přepínacích tlačítek ve stejné skupině. Naopak můžete vybrat libovolný počet zaškrtávací políčka. Definování skupina přepínacích tlačítek uživatele vyzve, "Následuje sadu voleb, ze kterých můžete vybrat jeden a pouze jeden."  
  
## <a name="using-the-control"></a>Použití ovládacího prvku  
 Když <xref:System.Windows.Forms.RadioButton> dojde ke kliknutí na ovládací prvek, jeho <xref:System.Windows.Forms.RadioButton.Checked%2A> je nastavena na `true` a <xref:System.Windows.Forms.Control.Click> obslužná rutina události je volána. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Událost se vyvolá, když hodnota <xref:System.Windows.Forms.RadioButton.Checked%2A> změny vlastností. Pokud <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> je nastavena na `true` (výchozí), když je přepínací tlačítko vybrané všechny ostatní ve skupině automaticky vymaže. Tato vlastnost je obvykle nastavena pouze na `false` při ověřování kódu používá k Ujistěte se, že vybraný přepínač je povolená možnost. Text zobrazený v ovládacím prvku nastavená <xref:System.Windows.Forms.Control.Text%2A> vlastnost, která může obsahovat přístup klávesové zkratky. Přístupový klíč umožňuje uživateli "klikněte" ovládací prvek pomocí klávesy ALT přístupovým klíčem. Další informace najdete v tématu [jak: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) a [jak: Nastavit Text, zobrazený Windows Forms ovládací prvek](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 <xref:System.Windows.Forms.RadioButton> Ovládací prvek může vypadat příkazového tlačítka, které se zobrazí, že byl stisknuté, pokud je vybrána, pokud <xref:System.Windows.Forms.RadioButton.Appearance%2A> je nastavena na <xref:System.Windows.Forms.Appearance.Button>. Přepínací tlačítka můžete také zobrazit obrázky pomocí <xref:System.Windows.Forms.ButtonBase.Image%2A> a <xref:System.Windows.Forms.ButtonBase.ImageList%2A> vlastnosti. Další informace najdete v tématu [jak: Nastavení obrázku zobrazovaného podle Windows Forms ovládací prvek](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RadioButton>
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Přehled ovládacího prvku GroupBox](groupbox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku CheckBox](checkbox-control-overview-windows-forms.md)
- [Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě sady](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [Ovládací prvek RadioButton](radiobutton-control-windows-forms.md)
