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
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="33912-102">Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="33912-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="33912-103">Můžete nakonfigurovat, jak se mají hodnoty zobrazovat v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.NumericUpDown>.</span><span class="sxs-lookup"><span data-stu-id="33912-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="33912-104">Vlastnost <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> určuje, kolik čísel se zobrazí za desetinnou čárkou; Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="33912-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="33912-105">Vlastnost <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> určuje, zda bude mezi každé tři desítkové číslice vložen oddělovač; Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="33912-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="33912-106">Ovládací prvek může zobrazit hodnoty v šestnáctkovém formátu namísto desítkového formátu, pokud je vlastnost <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> nastavena na hodnotu `true`; Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="33912-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="33912-107">Formátování číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="33912-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="33912-108">Zobrazte desítkovou hodnotu nastavením vlastnosti <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> na celé číslo a nastavením vlastnosti <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="33912-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="33912-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="33912-109">-or-</span></span>  
  
- <span data-ttu-id="33912-110">Zobrazte hexadecimální hodnotu nastavením vlastnosti <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="33912-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    > <span data-ttu-id="33912-111">I v případě, že se hodnota ve formuláři zobrazí jako šestnáctková, všechny testy, které provedete u vlastnosti <xref:System.Windows.Forms.NumericUpDown.Value%2A>, budou testovat svou desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="33912-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33912-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="33912-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="33912-113">Ovládací prvek NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="33912-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="33912-114">Přehled ovládacího prvku NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="33912-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
