---
title: 'Postupy: Tisk grafiky v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: ab2a230b7c6e303d712df058f450334b50c8a676
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167203"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Postupy: Tisk grafiky v modelu Windows Forms
Často bude chtít tisk grafiky v aplikaci založené na Windows. <xref:System.Drawing.Graphics> Třída poskytuje metody pro vykreslení objektů do zařízení, jako je obrazovka nebo tiskárny.  
  
### <a name="to-print-graphics"></a>Tisk grafiky  
  
1.  Přidat <xref:System.Drawing.Printing.PrintDocument> komponentu do formuláře.  
  
2.  V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužná rutina události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy dáte pokyn, aby tiskárny, na jaký typ grafiky k vytištění.  
  
     Následující příklad kódu ukazuje obslužné rutiny události použít k vytvoření modré tři tečky v rámci ohraničující obdélník. Obdélník má následující umístění a dimenze: začínající na 100, 150 šířka 250 a výška 250.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
