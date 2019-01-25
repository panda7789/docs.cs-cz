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
ms.openlocfilehash: db83d03d38acebfe42d383efdb2caa550bc2013a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636102"
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="75f0f-102">Postupy: Tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75f0f-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="75f0f-103">Často bude chtít tisk grafiky v aplikaci založené na Windows.</span><span class="sxs-lookup"><span data-stu-id="75f0f-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="75f0f-104"><xref:System.Drawing.Graphics> Třída poskytuje metody pro vykreslení objektů do zařízení, jako je obrazovka nebo tiskárny.</span><span class="sxs-lookup"><span data-stu-id="75f0f-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="75f0f-105">Tisk grafiky</span><span class="sxs-lookup"><span data-stu-id="75f0f-105">To print graphics</span></span>  
  
1.  <span data-ttu-id="75f0f-106">Přidat <xref:System.Drawing.Printing.PrintDocument> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="75f0f-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="75f0f-107">V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužná rutina události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy dáte pokyn, aby tiskárny, na jaký typ grafiky k vytištění.</span><span class="sxs-lookup"><span data-stu-id="75f0f-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="75f0f-108">Následující příklad kódu ukazuje obslužné rutiny události použít k vytvoření modré tři tečky v rámci ohraničující obdélník.</span><span class="sxs-lookup"><span data-stu-id="75f0f-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="75f0f-109">Obdélník má následující umístění a dimenze: začínající na 100, 150 šířka 250 a výška 250.</span><span class="sxs-lookup"><span data-stu-id="75f0f-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="75f0f-110">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="75f0f-110">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75f0f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75f0f-111">See also</span></span>
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="75f0f-112">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75f0f-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
