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
ms.openlocfilehash: 95fab00555231f7605e9104e8264f88b0909785a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671431"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown – přehled ovládacího prvku (Windows Forms)
<xref:System.Windows.Forms.NumericUpDown> Ovládací prvek vypadá jako kombinace textové pole a dvojice šipek, které může uživatel kliknout na Upravit hodnotu. Ovládací prvek zobrazí a nastaví jednu číselnou hodnotu ze seznamu voleb pevné číselné hodnoty. Uživatel může zvýšit a snížit počet kliknutím na tlačítko nahoru a dolů šipkami, stisknutím klávesy se šipkami nahoru a dolů nebo zadáním čísla v části textového pole ovládacího prvku. Kliknutím na klávesu šipka nahoru přesune číslo směrem k maximální; Kliknutím na klávesu šipka dolů přesune číslo směrem k minimální.  
  
 Z důvodu jeho univerzální funkce je tento ovládací prvek jasnou volbou, například pokud budete chtít vytvořit ovládání hlasitosti pro aplikaci hudební přehrávač. <xref:System.Windows.Forms.NumericUpDown> Ovládací prvek se používá v mnoha aplikacích ovládacích panelech Windows.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Čísla zobrazená ovládacího prvku textového pole může být v různých formátech, včetně šestnáctkové. Další informace najdete v tématu [jak: Nastavení formátu pro Windows Forms NumericUpDown – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Jsou klíčové vlastnosti ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (výchozí hodnota 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (výchozí hodnota 0), a <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (výchozí hodnota 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> Vlastnost nastaví aktuální počet vybraných v ovládacím prvku. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> Vlastnost nastaví dobu, že číslo je upraven, když uživatel klepne nahoru nebo šipka dolů. Když fokus přesunete mimo ovládací prvek, žádné typy vstupu bude ověřovat na minimální a maximální číselnou hodnotu. Můžete zvýšit rychlost, kterou ovládací prvek prochází přes čísla, když uživatel stiskne průběžně nahoru nebo šipku dolů, se <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> vlastnost. Jsou klíčové metody ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> a <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.NumericUpDown>
- [Ovládací prvek NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)
- [Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
