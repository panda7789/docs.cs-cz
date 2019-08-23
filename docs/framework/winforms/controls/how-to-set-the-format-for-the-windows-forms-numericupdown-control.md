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
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="10699-102">Postupy: Nastavení formátu pro ovládací prvek Windows Forms NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="10699-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="10699-103">Můžete nakonfigurovat, jak se mají hodnoty zobrazovat v ovládacím <xref:System.Windows.Forms.NumericUpDown> prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="10699-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="10699-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Vlastnost určuje, kolik čísel se zobrazí za desetinnou čárkou; výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="10699-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="10699-105">Vlastnost určuje, zda bude mezi každé tři desítkové číslice vložen oddělovač; výchozí hodnota je `false`. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A></span><span class="sxs-lookup"><span data-stu-id="10699-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="10699-106">Ovládací prvek může zobrazit hodnoty v šestnáctkovém formátu namísto desítkového formátu, <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Pokud je vlastnost nastavena `true`na hodnotu; výchozí `false`hodnota je.</span><span class="sxs-lookup"><span data-stu-id="10699-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="10699-107">Formátování číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="10699-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="10699-108">Zobrazte desítkovou hodnotu <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> nastavením vlastnosti na celé číslo a <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> nastavením vlastnosti na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="10699-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="10699-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="10699-109">-or-</span></span>  
  
- <span data-ttu-id="10699-110">Zobrazte hexadecimální hodnotu <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> nastavením vlastnosti na `true`.</span><span class="sxs-lookup"><span data-stu-id="10699-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    > <span data-ttu-id="10699-111">I v případě, že se hodnota ve formuláři zobrazí jako šestnáctková, všechny testy, které <xref:System.Windows.Forms.NumericUpDown.Value%2A> u vlastnosti provedete, budou testovat svou desítkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="10699-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10699-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10699-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="10699-113">Ovládací prvek NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="10699-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="10699-114">Přehled ovládacího prvku NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="10699-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
