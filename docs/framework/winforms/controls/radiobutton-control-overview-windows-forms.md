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
ms.openlocfilehash: 397808c055fd5ba5e8a73d47dfc7fee6c0cf2975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540074"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RadioButton> ovládacích prvků k dispozici dvě nebo více vzájemně se vylučujících voleb pro uživatele. A přepínací tlačítka a zaškrtávací políčka mohou být zobrazeny, podobně jako funkci, je důležitý rozdíl: když uživatel vybere přepínače, přepínací tlačítka ve stejné skupině není k dispozici také. Naopak můžete vybrat libovolný počet zaškrtávací políčka. Definování skupina přepínacích tlačítek informuje uživatele, "Zde je sada parametrů, ze kterých můžete vybrat pouze jeden."  
  
## <a name="using-the-control"></a>Použití ovládacího prvku  
 Když <xref:System.Windows.Forms.RadioButton> po kliknutí na ovládací prvek, jeho <xref:System.Windows.Forms.RadioButton.Checked%2A> je nastavena na `true` a <xref:System.Windows.Forms.Control.Click> je volána obslužná rutina události. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Událost se vyvolá, když hodnota <xref:System.Windows.Forms.RadioButton.Checked%2A> změny vlastností. Pokud <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> je nastavena na `true` (výchozí), pokud je vybrána přepínač všechny ostatní ve skupině jsou automaticky vymazány. Tato vlastnost je obvykle nastavit pouze na `false` při ověření kódu používá zajistit vybraný přepínač je povolená možnost. Text zobrazovaný v ovládacím prvku nastavena <xref:System.Windows.Forms.Control.Text%2A> vlastnosti, která může obsahovat klíče zástupce přístup. Přístupový klíč umožňuje uživatelům "Kliknutím" ovládacího prvku stisknutím klávesy ALT přístupovým klíčem. Další informace najdete v tématu [postupy: vytvoření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) a [postupy: nastavení zobrazí Text pomocí ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 <xref:System.Windows.Forms.RadioButton> Řízení může vyskytovat jako příkazového tlačítka, která se zobrazí, že byl stisknuté, pokud je vybrána, pokud <xref:System.Windows.Forms.RadioButton.Appearance%2A> je nastavena na <xref:System.Windows.Forms.Appearance.Button>. Přepínací tlačítka lze také zobrazit obrázky pomocí <xref:System.Windows.Forms.ButtonBase.Image%2A> a <xref:System.Windows.Forms.ButtonBase.ImageList%2A> vlastnosti. Další informace najdete v tématu [postupy: nastavení obrázek zobrazit pomocí ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RadioButton>  
 [Přehled ovládacího prvku Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Přehled ovládacího prvku GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [Přehled ovládacího prvku CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě sady](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 [Ovládací prvek RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
