---
title: 'Postupy: Změna velikosti Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 0fdd04b444deed0645e823bdac3cfc8f10d0386a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-resize-windows-forms"></a>Postupy: Změna velikosti Windows Forms
Můžete zadat velikost formuláře Windows několika způsoby. Můžete změnit výška a šířka formuláře programově nastavením nové hodnoty pro <xref:System.Windows.Forms.Form.Size%2A> vlastnost, nebo upravit <xref:System.Windows.Forms.Control.Height%2A> nebo <xref:System.Windows.Forms.Control.Width%2A> vlastnosti jednotlivě. Pokud používáte Visual Studio, můžete změnit velikost pomocí Návrhář formulářů Windows. Viz také [postupy: Změna velikosti Windows Forms pomocí návrháře](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).  
  
### <a name="to-resize-a-form-programmatically"></a>Chcete-li změnit velikost formuláře prostřednictvím kódu programu  
  
-   Zadejte velikost formuláře v době běhu nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnost formuláře.  
  
     Následující příklad kódu ukazuje velikost formuláře nastavena na 100 × 100 pixelů.  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a>Chcete-li změnit formuláře šířky a výšky prostřednictvím kódu programu  
  
-   Po <xref:System.Windows.Forms.Form.Size%2A> je definován, změnit šířka nebo výška formuláře pomocí <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.  
  
     Následující příklad kódu ukazuje šířku formuláře nastavena na 300 pixelů od levého okraje formuláře, zatímco výška zůstává konstantní.  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     -nebo-  
  
     Změna <xref:System.Drawing.Size.Width%2A> nebo <xref:System.Drawing.Size.Height%2A> nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnost.  
  
     Jak ukazuje následující příklad kódu, tento postup je však těžkopádnější než jenom nastavení <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a>Chcete-li změnit velikost formuláře po přírůstcích prostřednictvím kódu programu  
  
-   Chcete-li zvýšit velikost formuláře, nastavte <xref:System.Drawing.Size.Width%2A> a <xref:System.Drawing.Size.Height%2A> vlastnosti.  
  
     Následující příklad kódu ukazuje šířku formuláře nastavena na hodnotu 200 pixelů širší než aktuální nastavení.  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  Vždy nutné použít <xref:System.Drawing.Size.Height%2A> nebo <xref:System.Drawing.Size.Width%2A> vlastnost změnit dimenze formuláře, pokud nastavujete výšku a šířku ve stejnou dobu nastavením <xref:System.Windows.Forms.Form.Size%2A> vlastnost na nový <xref:System.Drawing.Size> struktura. <xref:System.Windows.Forms.Form.Size%2A> Vlastnost vrátí <xref:System.Drawing.Size> struktura, což je typ hodnoty. Nelze přiřadit novou hodnotu pro vlastnost typu hodnoty. Proto nebude Zkompilujte následující příklad kódu.  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Rozšiřování aplikací Windows Forms](../../../docs/framework/winforms/advanced/index.md)
