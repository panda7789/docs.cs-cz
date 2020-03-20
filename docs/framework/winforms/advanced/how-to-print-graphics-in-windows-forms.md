---
title: 'Postup: Tisk grafiky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 15f3a507839430ce058302e7f5abd317ef84626f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182526"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Postupy: Tisk grafiky ve Windows Forms
Často budete chtít tisknout grafiku v aplikaci systému Windows. Třída <xref:System.Drawing.Graphics> poskytuje metody pro kreslení objektů do zařízení, jako je například obrazovka nebo tiskárna.  
  
### <a name="to-print-graphics"></a>Tisk grafiky  
  
1. Přidejte <xref:System.Drawing.Printing.PrintDocument> součást do formuláře.  
  
2. V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> rutině <xref:System.Drawing.Printing.PrintPageEventArgs> události použijte vlastnost třídy k instruování tiskárny o tom, jaký druh grafiky se má tisknout.  
  
     Následující příklad kódu ukazuje obslužnou rutinu události použitou k vytvoření modré elipsy v ohraničujícím obdélníku. Obdélník má následující umístění a rozměry: počínaje 100, 150 s šířkou 250 a výškou 250.  
  
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
  
     (Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
