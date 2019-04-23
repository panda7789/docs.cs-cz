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
ms.openlocfilehash: 218eb685e546acac76a18450612a1601ab87276b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109873"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown – přehled ovládacího prvku (Windows Forms)
<xref:System.Windows.Forms.NumericUpDown> Ovládací prvek vypadá jako kombinace textové pole a dvojice šipek, které může uživatel kliknout na Upravit hodnotu. Ovládací prvek zobrazí a nastaví jednu číselnou hodnotu ze seznamu voleb pevné číselné hodnoty. Uživatel může zvýšit a snížit počet kliknutím na tlačítko nahoru a dolů šipkami, stisknutím klávesy se šipkami nahoru a dolů nebo zadáním čísla v části textového pole ovládacího prvku. Kliknutím na klávesu šipka nahoru přesune číslo směrem k maximální; Kliknutím na klávesu šipka dolů přesune číslo směrem k minimální.  
  
 Z důvodu jeho univerzální funkce je tento ovládací prvek jasnou volbou, například pokud budete chtít vytvořit ovládání hlasitosti pro aplikaci hudební přehrávač. <xref:System.Windows.Forms.NumericUpDown> Ovládací prvek se používá v mnoha aplikacích ovládacích panelech Windows.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Čísla zobrazená ovládacího prvku textového pole může být v různých formátech, včetně šestnáctkové. Další informace najdete v tématu [jak: Nastavení formátu pro Windows Forms NumericUpDown – ovládací prvek](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Jsou klíčové vlastnosti ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (výchozí hodnota 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (výchozí hodnota 0), a <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (výchozí hodnota 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> Vlastnost nastaví aktuální počet vybraných v ovládacím prvku. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> Vlastnost nastaví dobu, že číslo je upraven, když uživatel klepne nahoru nebo šipka dolů. Když fokus přesunete mimo ovládací prvek, žádné typy vstupu bude ověřovat na minimální a maximální číselnou hodnotu. Můžete zvýšit rychlost, kterou ovládací prvek prochází přes čísla, když uživatel stiskne průběžně nahoru nebo šipku dolů, se <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> vlastnost. Jsou klíčové metody ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> a <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NumericUpDown>
- [Ovládací prvek NumericUpDown](numericupdown-control-windows-forms.md)
- [Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
