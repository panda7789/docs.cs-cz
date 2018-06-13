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
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="0fab0-102">Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="0fab0-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="0fab0-103">Můžete nakonfigurovat způsob zobrazení hodnot ve Windows Forms <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0fab0-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="0fab0-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Vlastnost určuje, kolik čísla se zobrazí za desetinnou čárkou; výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="0fab0-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="0fab0-105"><xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Vlastnost určuje, zda bude vložen oddělovač mezi každé tři desetinných míst; výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0fab0-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="0fab0-106">Ovládací prvek můžete zobrazit hodnoty v šestnáctkové soustavě místo formátu desetinného čísla, pokud <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> je nastavena na `true`; výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0fab0-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="0fab0-107">K formátování číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="0fab0-107">To format the numeric value</span></span>  
  
-   <span data-ttu-id="0fab0-108">Zobrazit desítkovou hodnotu podle nastavení <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> vlastnost na celé číslo a nastavení <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> vlastnost `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="0fab0-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="0fab0-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="0fab0-109">-or-</span></span>  
  
-   <span data-ttu-id="0fab0-110">Zobrazit šestnáctkové hodnoty nastavením <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="0fab0-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    >  <span data-ttu-id="0fab0-111">I v případě, že hodnota je zobrazena na formuláři jako hexadecimální, všechny testy, můžete provést na <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost testovat desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0fab0-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fab0-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fab0-112">See Also</span></span>  
 <xref:System.Windows.Forms.NumericUpDown>  
 [<span data-ttu-id="0fab0-113">Ovládací prvek NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="0fab0-113">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [<span data-ttu-id="0fab0-114">Přehled ovládacího prvku NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="0fab0-114">NumericUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
