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
ms.openlocfilehash: 2da4b7483e92b02360bceb886d84a7f729b84dee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800799"
---
# <a name="how-to-resize-windows-forms"></a>Postupy: Změna velikosti Windows Forms
Velikost formuláře Windows můžete zadat několika způsoby. Můžete změnit výšku a šířku formuláře programově tak, že nastavíte novou hodnotu <xref:System.Windows.Forms.Form.Size%2A> vlastnost, nebo upravte <xref:System.Windows.Forms.Control.Height%2A> nebo <xref:System.Windows.Forms.Control.Width%2A> vlastnosti jednotlivě. Pokud používáte Visual Studio, můžete změnit velikost pomocí Návrháře formulářů Windows. Viz také [jak: Změna velikosti Windows Forms pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).  
  
### <a name="to-resize-a-form-programmatically"></a>Změnit velikost formuláře prostřednictvím kódu programu  
  
- Definovat tak, že nastavíte velikost formuláře v době běhu <xref:System.Windows.Forms.Form.Size%2A> vlastnost formuláře.  
  
     Následující příklad kódu ukazuje velikost formuláře nastavte na 100 × 100 pixelů.  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a>Chcete-li změnit výšku a šířku formuláře prostřednictvím kódu programu  
  
- Po <xref:System.Windows.Forms.Form.Size%2A> je definován, změnit šířka nebo výška formuláře pomocí <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.  
  
     Následující příklad kódu ukazuje šířku formuláře nastavte na 300 pixelů od levého okraje formuláře, zatímco výška zůstává konstantní.  
  
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
  
     Jak ukazuje následující příklad kódu, tento přístup je však náročnější než pouhé nastavení <xref:System.Windows.Forms.Control.Width%2A> nebo <xref:System.Windows.Forms.Control.Height%2A> vlastnosti.  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a>Chcete-li změnit velikost formuláře o kousek prostřednictvím kódu programu  
  
- Chcete-li zvýšit velikost formuláře, nastavte <xref:System.Drawing.Size.Width%2A> a <xref:System.Drawing.Size.Height%2A> vlastnosti.  
  
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
    >  Vždy používat <xref:System.Drawing.Size.Height%2A> nebo <xref:System.Drawing.Size.Width%2A> změnit rozměr formuláře, pokud nastavíte výšku a šířku ve stejnou dobu tak, že nastavíte vlastnost <xref:System.Windows.Forms.Form.Size%2A> vlastnost do nového <xref:System.Drawing.Size> struktury. <xref:System.Windows.Forms.Form.Size%2A> Vrátí vlastnost <xref:System.Drawing.Size> struktury, což je typ hodnoty. Nelze přiřadit novou hodnotu pro vlastnost typu hodnoty. Následující příklad kódu proto nebude kompilovat.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Začínáme s Windows Forms](getting-started-with-windows-forms.md)
- [Rozšiřování aplikací Windows Forms](./advanced/index.md)
