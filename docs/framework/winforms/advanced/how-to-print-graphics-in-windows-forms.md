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
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="ffe20-102">Postupy: Tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffe20-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="ffe20-103">V aplikaci pro Windows často budete chtít vytisknout grafiky.</span><span class="sxs-lookup"><span data-stu-id="ffe20-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="ffe20-104">Třída <xref:System.Drawing.Graphics> poskytuje metody pro kreslení objektů do zařízení, jako je například obrazovka nebo tiskárna.</span><span class="sxs-lookup"><span data-stu-id="ffe20-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="ffe20-105">Tisk grafiky</span><span class="sxs-lookup"><span data-stu-id="ffe20-105">To print graphics</span></span>  
  
1. <span data-ttu-id="ffe20-106">Přidejte do formuláře komponentu <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="ffe20-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="ffe20-107">V obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> použijte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs> k tomu, abyste si vydávali informace o tom, jaký druh grafiky chcete tisknout.</span><span class="sxs-lookup"><span data-stu-id="ffe20-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="ffe20-108">Následující příklad kódu ukazuje obslužnou rutinu události použitou k vytvoření modré elipsy v ohraničujícím obdélníku.</span><span class="sxs-lookup"><span data-stu-id="ffe20-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="ffe20-109">Obdélník má následující umístění a rozměry: od 100.150 s šířkou 250 a výškou 250.</span><span class="sxs-lookup"><span data-stu-id="ffe20-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="ffe20-110">(Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ffe20-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ffe20-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffe20-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="ffe20-112">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ffe20-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
