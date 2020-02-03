---
title: 'Postupy: tisk grafiky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 2435b3bc14747a00d2a0fc03a9ebd21ae43c5369
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740639"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Postupy: Tisk grafiky ve Windows Forms
V aplikaci pro Windows často budete chtít vytisknout grafiky. Třída <xref:System.Drawing.Graphics> poskytuje metody pro kreslení objektů do zařízení, jako je například obrazovka nebo tiskárna.  
  
### <a name="to-print-graphics"></a>Tisk grafiky  
  
1. Přidejte do formuláře komponentu <xref:System.Drawing.Printing.PrintDocument>.  
  
2. V obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> použijte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs> k tomu, abyste si vydávali informace o tom, jaký druh grafiky chcete tisknout.  
  
     Následující příklad kódu ukazuje obslužnou rutinu události použitou k vytvoření modré elipsy v ohraničujícím obdélníku. Obdélník má následující umístění a rozměry: od 100.150 s šířkou 250 a výškou 250.  
  
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
  
     (Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
