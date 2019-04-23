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
ms.openlocfilehash: 5957a44c7b07aa1b8d8df32667f023c0873ec1de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186135"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown
Můžete nakonfigurovat způsob zobrazení hodnot ve Windows Forms <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Vlastnost určuje, kolik čísla se zobrazí za desetinnou čárkou; výchozí hodnota je 0. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Vlastnost určuje, zda bude mezi každé tři desítkové číslice vložen oddělovač; výchozí hodnota je `false`. Ovládací prvek můžete zobrazit hodnoty v šestnáctkové soustavě namísto formátu desítkové soustavy, pokud <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> je nastavena na `true`; výchozí hodnota je `false`.  
  
### <a name="to-format-the-numeric-value"></a>K formátování číselné hodnoty  
  
-   Zobrazit desítkovou hodnotu tak, že nastavíte <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> vlastnost na celé číslo a nastavení <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> vlastnost `true` nebo `false`.  
  
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
  
-   Zobrazení šestnáctkové hodnoty tak, že nastavíte <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> vlastnost `true`.  
  
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
    >  I v případě, že hodnota se zobrazí ve formuláři jako šestnáctkové číslo, všechny testy, můžete provést na <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost budete testovat desítkovou hodnotu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.NumericUpDown>
- [Ovládací prvek NumericUpDown](numericupdown-control-windows-forms.md)
- [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md)
