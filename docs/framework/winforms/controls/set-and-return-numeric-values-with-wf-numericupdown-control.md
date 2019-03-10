---
title: 'Postupy: Nastavení a vracení číselných hodnot pomocí ovládacího prvku Windows Forms NumericUpDown'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: 166b14fca2009d0609fa48a5f07912b33f074071
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703198"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a><span data-ttu-id="8fdcc-102">Postupy: Nastavení a vracení číselných hodnot pomocí ovládacího prvku Windows Forms NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="8fdcc-102">How to: Set and Return Numeric Values with the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="8fdcc-103">Číselná hodnota prvku modelu Windows Forms <xref:System.Windows.Forms.NumericUpDown> ovládací prvek je dáno jeho <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-103">The numeric value of the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control is determined by its <xref:System.Windows.Forms.NumericUpDown.Value%2A> property.</span></span> <span data-ttu-id="8fdcc-104">Stejně jako u jakékoli jiné vlastnosti můžete psát podmíněného testy pro hodnotu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-104">You can write conditional tests for the control's value just as with any other property.</span></span> <span data-ttu-id="8fdcc-105">Jednou <xref:System.Windows.Forms.NumericUpDown.Value%2A> je hodnota nastavena, můžete upravit přímo napsáním kódu k provádění operací na něj nebo můžete volat <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> a <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-105">Once the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property is set, you can adjust it directly by writing code to perform operations on it, or you can call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> methods.</span></span>  
  
### <a name="to-set-the-numeric-value"></a><span data-ttu-id="8fdcc-106">Chcete-li nastavit číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="8fdcc-106">To set the numeric value</span></span>  
  
1.  <span data-ttu-id="8fdcc-107">Přiřaďte hodnotu <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastností v kódu nebo v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-107">Assign a value to the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code or in the Properties window.</span></span>  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     <span data-ttu-id="8fdcc-108">-nebo-</span><span class="sxs-lookup"><span data-stu-id="8fdcc-108">-or-</span></span>  
  
2.  <span data-ttu-id="8fdcc-109">Volání <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> nebo <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metoda chcete zvýšit nebo snížit hodnotu zadanou v <xref:System.Windows.Forms.NumericUpDown.Increment%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-109">Call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> or <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> method to increase or decrease the value by the amount specified in the <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property.</span></span>  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a><span data-ttu-id="8fdcc-110">Vrátit číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="8fdcc-110">To return the numeric value</span></span>  
  
-   <span data-ttu-id="8fdcc-111">Přístup <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastností v kódu.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-111">Access the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code.</span></span>  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8fdcc-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fdcc-112">See also</span></span>
- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8fdcc-113">Ovládací prvek NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="8fdcc-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="8fdcc-114">Přehled ovládacího prvku NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="8fdcc-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
