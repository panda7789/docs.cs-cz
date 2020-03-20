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
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="258a2-102">Postupy: Tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="258a2-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="258a2-103">Často budete chtít tisknout grafiku v aplikaci systému Windows.</span><span class="sxs-lookup"><span data-stu-id="258a2-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="258a2-104">Třída <xref:System.Drawing.Graphics> poskytuje metody pro kreslení objektů do zařízení, jako je například obrazovka nebo tiskárna.</span><span class="sxs-lookup"><span data-stu-id="258a2-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="258a2-105">Tisk grafiky</span><span class="sxs-lookup"><span data-stu-id="258a2-105">To print graphics</span></span>  
  
1. <span data-ttu-id="258a2-106">Přidejte <xref:System.Drawing.Printing.PrintDocument> součást do formuláře.</span><span class="sxs-lookup"><span data-stu-id="258a2-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="258a2-107">V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> rutině <xref:System.Drawing.Printing.PrintPageEventArgs> události použijte vlastnost třídy k instruování tiskárny o tom, jaký druh grafiky se má tisknout.</span><span class="sxs-lookup"><span data-stu-id="258a2-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="258a2-108">Následující příklad kódu ukazuje obslužnou rutinu události použitou k vytvoření modré elipsy v ohraničujícím obdélníku.</span><span class="sxs-lookup"><span data-stu-id="258a2-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="258a2-109">Obdélník má následující umístění a rozměry: počínaje 100, 150 s šířkou 250 a výškou 250.</span><span class="sxs-lookup"><span data-stu-id="258a2-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="258a2-110">(Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="258a2-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="258a2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="258a2-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="258a2-112">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="258a2-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
