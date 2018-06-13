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
ms.openlocfilehash: 1cb8f8b7d2f86125736c08cd9eadf4eee30063bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533954"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown
Můžete nakonfigurovat způsob zobrazení hodnot ve Windows Forms <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Vlastnost určuje, kolik čísla se zobrazí za desetinnou čárkou; výchozí hodnota je 0. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Vlastnost určuje, zda bude vložen oddělovač mezi každé tři desetinných míst; výchozí hodnota je `false`. Ovládací prvek můžete zobrazit hodnoty v šestnáctkové soustavě místo formátu desetinného čísla, pokud <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> je nastavena na `true`; výchozí hodnota je `false`.  
  
### <a name="to-format-the-numeric-value"></a>K formátování číselná hodnota  
  
-   Zobrazit desítkovou hodnotu podle nastavení <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> vlastnost na celé číslo a nastavení <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> vlastnost `true` nebo `false`.  
  
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
  
-   Zobrazit šestnáctkové hodnoty nastavením <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> vlastnost `true`.  
  
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
    >  I v případě, že hodnota je zobrazena na formuláři jako hexadecimální, všechny testy, můžete provést na <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost testovat desítkovou hodnotu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.NumericUpDown>  
 [Ovládací prvek NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [Přehled ovládacího prvku NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
