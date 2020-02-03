---
title: Přehled ovládacího prvku NumericUpDown
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 3e24fa543df9028e9866d91ec60c3cf88578ac56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740802"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown – přehled ovládacího prvku (Windows Forms)
Ovládací prvek <xref:System.Windows.Forms.NumericUpDown> vypadá jako kombinace textového pole a dvojice šipek, na které může uživatel kliknout pro úpravu hodnoty. Ovládací prvek zobrazí a nastaví jednu číselnou hodnotu ze seznamu hodnot s pevnou hodnotou. Uživatel může číslo zvýšit a snížit kliknutím na šipky nahoru a dolů tak, že stisknete klávesy se šipkami nahoru a dolů nebo zadáte číslo do textového pole v části ovládacího prvku. Kliknutím na klávesu šipka nahoru posunete číslo směrem k maximálnímu počtu; Kliknutím na klávesu šipka dolů posunete číslo směrem k minimálnímu.  
  
 Z důvodu jeho univerzálních funkcí je tento ovládací prvek zjevné volbou, například pokud chcete vytvořit ovládání hlasitosti pro aplikaci hudebního přehrávače. <xref:System.Windows.Forms.NumericUpDown> ovládací prvek se používá v mnoha aplikacích v Ovládacích panelech Windows.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Čísla zobrazená v textovém poli ovládacího prvku mohou být v nejrůznějších formátech, včetně hexadecimálního formátu. Další informace naleznete v tématu [How to: set a Format for model Windows Forms NumericUpDown Control](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (výchozí hodnota 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (výchozí hodnota 0) a <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (výchozí hodnota 1). Vlastnost <xref:System.Windows.Forms.NumericUpDown.Value%2A> nastaví aktuální číslo vybrané v ovládacím prvku. Vlastnost <xref:System.Windows.Forms.NumericUpDown.Increment%2A> nastaví množství, podle kterého je číslo upraveno, když uživatel klikne na šipku nahoru nebo dolů. Když se fokus přesune mimo ovládací prvek, všechny zadané vstupy se ověří podle minimální a maximální číselné hodnoty. Můžete zvýšit rychlost, kterou ovládací prvek přesouvá pomocí čísel, když uživatel nepřetržitě stiskne šipku nahoru nebo dolů s vlastností <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>. Klíčové metody ovládacího prvku jsou <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> a <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.NumericUpDown>
- [Ovládací prvek NumericUpDown](numericupdown-control-windows-forms.md)
- [Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
