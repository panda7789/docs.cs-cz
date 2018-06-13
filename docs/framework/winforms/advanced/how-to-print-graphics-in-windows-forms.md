---
title: 'Postupy: Tisk grafiky ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 8281e1e0a3d350c3b81e26bbe59c098536ef064e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521495"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Postupy: Tisk grafiky ve Windows Forms
Často budete chtít tisk grafiky ve vaší aplikaci systému Windows. <xref:System.Drawing.Graphics> Třída poskytuje metody pro kreslení objekty do zařízení, jako je například obrazovky nebo tiskárny.  
  
### <a name="to-print-graphics"></a>Pro tisk grafiky  
  
1.  Přidat <xref:System.Drawing.Printing.PrintDocument> součásti do svého formuláře.  
  
2.  V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třída dáte pokyn, aby tiskárny, na jaký druh grafiky k vytištění.  
  
     Následující příklad kódu ukazuje obslužné rutiny události použít k vytvoření blue elipsy v rámci ohraničující obdélník. Rámeček má následující umístění a dimenze: začínající na 100, 150 s šířka 250 a výška 250.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
