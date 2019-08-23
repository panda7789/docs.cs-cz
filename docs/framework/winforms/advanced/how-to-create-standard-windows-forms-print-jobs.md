---
title: 'Postupy: Vytváření standardních tiskových úloh v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938232"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="cdcaf-102">Postupy: Vytváření standardních tiskových úloh v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdcaf-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="cdcaf-103">Základem tisku v model Windows Forms je <xref:System.Drawing.Printing.PrintDocument> komponenta, která se podrobněji <xref:System.Drawing.Printing.PrintDocument.PrintPage> týká události.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="cdcaf-104">Napsáním kódu pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> události můžete určit, co se má vytisknout, a jak ho vytisknout.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="cdcaf-105">Vytvoření tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="cdcaf-105">To create a print job</span></span>  
  
1. <span data-ttu-id="cdcaf-106"><xref:System.Drawing.Printing.PrintDocument> Přidejte komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="cdcaf-107">Napište kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> události.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="cdcaf-108">Budete muset kódovat vlastní logiku tisku.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="cdcaf-109">Navíc budete muset určit materiál, který se má vytisknout.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="cdcaf-110">V následujícím příkladu kódu se v obslužné rutině <xref:System.Drawing.Printing.PrintDocument.PrintPage> události vytvoří ukázková grafika v obrazci červeného obdélníku, která bude fungovat jako materiál k vytištění.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="cdcaf-111">(Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     <span data-ttu-id="cdcaf-112">Můžete také chtít napsat kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> události a <xref:System.Drawing.Printing.PrintDocument.EndPrint> , případně včetně celého čísla představujícího celkový počet stránek k vytištění, které se sníží při tisku každé stránky.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cdcaf-113">Do formuláře můžete přidat <xref:System.Windows.Forms.PrintDialog> komponentu, která uživatelům poskytuje čisté a efektivní uživatelské rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="cdcaf-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="cdcaf-114"><xref:System.Windows.Forms.PrintDialog.Document%2A> Nastavení vlastnosti <xref:System.Windows.Forms.PrintDialog> komponenty vám umožní nastavit vlastnosti týkající se tiskového dokumentu, se kterým pracujete na formuláři.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="cdcaf-115">Další informace o <xref:System.Windows.Forms.PrintDialog> komponentě naleznete v tématu [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cdcaf-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="cdcaf-116">Další informace o konkrétních model Windows Forms tiskových úlohách, včetně postupu vytvoření tiskové úlohy programově, najdete v tématu <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="cdcaf-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdcaf-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdcaf-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="cdcaf-118">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdcaf-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
