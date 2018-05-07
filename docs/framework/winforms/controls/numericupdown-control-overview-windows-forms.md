---
title: NumericUpDown – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: b1f32a767d27ef2f4e5629947d67097272695d9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown – přehled ovládacího prvku (Windows Forms)
<xref:System.Windows.Forms.NumericUpDown> Řízení vypadá kombinací textového pole a dvojice šipek, které uživatel můžete kliknutím na Upravit hodnotu. Ovládací prvek zobrazí a nastaví jednu číselnou hodnotu ze seznamu voleb pevné číselné hodnoty. Uživatel může zvýšit a snížit počet kliknutím na tlačítko nahoru a dolů, stisknutím klávesy se šipkami nahoru a dolů, nebo zadáním čísla v části textového pole ovládacího prvku. Kliknutím na tlačítko šipka nahoru přesune číslo směrem k maximální; Kliknutím na tlačítko šipka dolů přesune číslo směrem k minimální.  
  
 Z důvodu jeho univerzální funkce je tento ovládací prvek zřejmé volba, například, pokud chcete vytvořit svazek ovládací prvek pro aplikaci hudební přehrávač. <xref:System.Windows.Forms.NumericUpDown> Řízení se používá v mnoha aplikacích ovládací panely systému Windows.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Čísla zobrazí ovládacího prvku textového pole může být v různých formátech, včetně hexadecimální. Další informace najdete v tématu [postupy: nastavení formátu pro ovládací prvek Windows Forms NumericUpDown](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (výchozí hodnota 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (výchozí hodnota 0), a <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (výchozí hodnota 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> Vlastnost nastaví číslo aktuální vybrané v ovládacím prvku. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> Vlastnost nastaví dobu, že číslo se upraví, když uživatel klikne nahoru nebo šipku dolů. Při zaměření vypnout ovládací prvek, budou všechny zadaný vstup ověřený proti minimální a maximální číselné hodnoty. Můžete zvýšit rychlost, kterou ovládacího prvku prochází přes čísla, když uživatel nepřetržitě stiskem tlačítka nahoru nebo dolů šipku, s <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> vlastnost. Klíče metody ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> a <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.NumericUpDown>  
 [Ovládací prvek NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
