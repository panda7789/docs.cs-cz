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
ms.openlocfilehash: e214f556224577c3029b2b742784e58932d792f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535558"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a><span data-ttu-id="4bc76-102">Postupy: Nastavení a vracení číselných hodnot pomocí ovládacího prvku Windows Forms NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="4bc76-102">How to: Set and Return Numeric Values with the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="4bc76-103">Číselná hodnota modelu Windows Forms <xref:System.Windows.Forms.NumericUpDown> ovládací prvek je dáno jeho <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bc76-103">The numeric value of the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control is determined by its <xref:System.Windows.Forms.NumericUpDown.Value%2A> property.</span></span> <span data-ttu-id="4bc76-104">Můžete napsat podmíněného testů pro hodnotu ovládacího prvku stejně jako v žádné jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4bc76-104">You can write conditional tests for the control's value just as with any other property.</span></span> <span data-ttu-id="4bc76-105">Jednou <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost nastavena, můžete jej přizpůsobit přímo z psaní kódu k provádění operací na něm nebo můžete volat <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> a <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4bc76-105">Once the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property is set, you can adjust it directly by writing code to perform operations on it, or you can call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> methods.</span></span>  
  
### <a name="to-set-the-numeric-value"></a><span data-ttu-id="4bc76-106">Chcete-li nastavit číselná hodnota</span><span class="sxs-lookup"><span data-stu-id="4bc76-106">To set the numeric value</span></span>  
  
1.  <span data-ttu-id="4bc76-107">Přiřazení hodnoty k <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastností v kódu nebo v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4bc76-107">Assign a value to the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code or in the Properties window.</span></span>  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     <span data-ttu-id="4bc76-108">-nebo-</span><span class="sxs-lookup"><span data-stu-id="4bc76-108">-or-</span></span>  
  
2.  <span data-ttu-id="4bc76-109">Volání <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> nebo <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metodou zvyšte nebo snižte hodnotu zadanou v velikost <xref:System.Windows.Forms.NumericUpDown.Increment%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4bc76-109">Call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> or <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> method to increase or decrease the value by the amount specified in the <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property.</span></span>  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a><span data-ttu-id="4bc76-110">Vrátit číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="4bc76-110">To return the numeric value</span></span>  
  
-   <span data-ttu-id="4bc76-111">Přístup <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastností v kódu.</span><span class="sxs-lookup"><span data-stu-id="4bc76-111">Access the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4bc76-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bc76-112">See Also</span></span>  
 <xref:System.Windows.Forms.NumericUpDown>  
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4bc76-113">Ovládací prvek NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="4bc76-113">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [<span data-ttu-id="4bc76-114">Přehled ovládacího prvku NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="4bc76-114">NumericUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
