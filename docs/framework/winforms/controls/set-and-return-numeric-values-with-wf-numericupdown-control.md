---
title: "Postupy: Nastavení a vracení číselných hodnot pomocí ovládacího prvku Windows Forms NumericUpDown"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f31f0b247c882b8ccba84930f7e21f5eea088a35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Postupy: Nastavení a vracení číselných hodnot pomocí ovládacího prvku Windows Forms NumericUpDown
Číselná hodnota modelu Windows Forms <xref:System.Windows.Forms.NumericUpDown> ovládací prvek je dáno jeho <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost. Můžete napsat podmíněného testů pro hodnotu ovládacího prvku stejně jako v žádné jiné vlastnosti. Jednou <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastnost nastavena, můžete jej přizpůsobit přímo z psaní kódu k provádění operací na něm nebo můžete volat <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> a <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metody.  
  
### <a name="to-set-the-numeric-value"></a>Chcete-li nastavit číselná hodnota  
  
1.  Přiřazení hodnoty k <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastností v kódu nebo v okně Vlastnosti.  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     -nebo-  
  
2.  Volání <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> nebo <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metodou zvyšte nebo snižte hodnotu zadanou v velikost <xref:System.Windows.Forms.NumericUpDown.Increment%2A> vlastnost.  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>Vrátit číselnou hodnotu  
  
-   Přístup <xref:System.Windows.Forms.NumericUpDown.Value%2A> vlastností v kódu.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.NumericUpDown>  
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>  
 [Ovládací prvek NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [Přehled ovládacího prvku NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
