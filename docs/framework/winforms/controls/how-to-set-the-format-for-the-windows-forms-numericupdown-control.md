---
title: Nastavení formátu pro ovládací prvek NumericUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5ef1c801e96bef7b92e7e69dc36491144c456eeb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742185"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown
Můžete nakonfigurovat, jak se mají hodnoty zobrazovat v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.NumericUpDown>. Vlastnost <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> určuje, kolik čísel se zobrazí za desetinnou čárkou; Výchozí hodnota je 0. Vlastnost <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> určuje, zda bude mezi každé tři desítkové číslice vložen oddělovač; Výchozí hodnota je `false`. Ovládací prvek může zobrazit hodnoty v šestnáctkovém formátu namísto desítkového formátu, pokud je vlastnost <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> nastavena na hodnotu `true`; Výchozí hodnota je `false`.  
  
### <a name="to-format-the-numeric-value"></a>Formátování číselné hodnoty  
  
- Zobrazte desítkovou hodnotu nastavením vlastnosti <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> na celé číslo a nastavením vlastnosti <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> na `true` nebo `false`.  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     -nebo-  
  
- Zobrazte hexadecimální hodnotu nastavením vlastnosti <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> na `true`.  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    > I v případě, že se hodnota ve formuláři zobrazí jako šestnáctková, všechny testy, které provedete u vlastnosti <xref:System.Windows.Forms.NumericUpDown.Value%2A>, budou testovat svou desítkovou hodnotu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.NumericUpDown>
- [Ovládací prvek NumericUpDown](numericupdown-control-windows-forms.md)
- [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md)
