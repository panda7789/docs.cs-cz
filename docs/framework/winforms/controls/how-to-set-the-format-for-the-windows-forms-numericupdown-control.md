---
title: 'Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949153"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown
Můžete nakonfigurovat, jak se mají hodnoty zobrazovat v ovládacím <xref:System.Windows.Forms.NumericUpDown> prvku model Windows Forms. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Vlastnost určuje, kolik čísel se zobrazí za desetinnou čárkou; výchozí hodnota je 0. Vlastnost určuje, zda bude mezi každé tři desítkové číslice vložen oddělovač; výchozí hodnota je `false`. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Ovládací prvek může zobrazit hodnoty v šestnáctkovém formátu namísto desítkového formátu, <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Pokud je vlastnost nastavena `true`na hodnotu; výchozí `false`hodnota je.  
  
### <a name="to-format-the-numeric-value"></a>Formátování číselné hodnoty  
  
- Zobrazte desítkovou hodnotu <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> nastavením vlastnosti na celé číslo a <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> nastavením vlastnosti na `true` nebo `false`.  
  
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
  
- Zobrazte hexadecimální hodnotu <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> nastavením vlastnosti na `true`.  
  
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
    > I v případě, že se hodnota ve formuláři zobrazí jako šestnáctková, všechny testy, které <xref:System.Windows.Forms.NumericUpDown.Value%2A> u vlastnosti provedete, budou testovat svou desítkovou hodnotu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NumericUpDown>
- [Ovládací prvek NumericUpDown](numericupdown-control-windows-forms.md)
- [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md)
