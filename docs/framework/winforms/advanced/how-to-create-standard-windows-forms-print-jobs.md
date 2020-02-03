---
title: Vytvoření standardních tiskových úloh
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
ms.openlocfilehash: 4850dc901630179cc44fefda7e25bbabcfb4725f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741516"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="7b45b-102">Postupy: Vytváření standardních tiskových úloh Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b45b-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="7b45b-103">Základem tisku v model Windows Forms je <xref:System.Drawing.Printing.PrintDocument> komponenta – konkrétně událost <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="7b45b-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="7b45b-104">Napsáním kódu pro zpracování události <xref:System.Drawing.Printing.PrintDocument.PrintPage> můžete určit, co se má vytisknout, a jak ho vytisknout.</span><span class="sxs-lookup"><span data-stu-id="7b45b-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="7b45b-105">Vytvoření tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="7b45b-105">To create a print job</span></span>  
  
1. <span data-ttu-id="7b45b-106">Přidejte do formuláře komponentu <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="7b45b-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="7b45b-107">Napište kód pro zpracování události <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="7b45b-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="7b45b-108">Budete muset kódovat vlastní logiku tisku.</span><span class="sxs-lookup"><span data-stu-id="7b45b-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="7b45b-109">Navíc budete muset určit materiál, který se má vytisknout.</span><span class="sxs-lookup"><span data-stu-id="7b45b-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="7b45b-110">V následujícím příkladu kódu je v obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> vytvořena ukázková grafika v obrazci červeného obdélníku, která bude fungovat jako materiál pro tisk.</span><span class="sxs-lookup"><span data-stu-id="7b45b-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="7b45b-111">(Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7b45b-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="7b45b-112">Můžete také vytvořit kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> a <xref:System.Drawing.Printing.PrintDocument.EndPrint> události, třeba včetně celého čísla představujícího celkový počet stránek k vytištění, které se sníží při tisku každé stránky.</span><span class="sxs-lookup"><span data-stu-id="7b45b-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b45b-113">Do formuláře můžete přidat komponentu <xref:System.Windows.Forms.PrintDialog>, abyste svým uživatelům zajistili čisté a efektivní uživatelské rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="7b45b-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="7b45b-114">Nastavením vlastnosti <xref:System.Windows.Forms.PrintDialog.Document%2A> komponenty <xref:System.Windows.Forms.PrintDialog> můžete nastavit vlastnosti, které se týkají tiskového dokumentu, se kterými pracujete na formuláři.</span><span class="sxs-lookup"><span data-stu-id="7b45b-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="7b45b-115">Další informace o komponentě <xref:System.Windows.Forms.PrintDialog> naleznete v tématu [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7b45b-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="7b45b-116">Další informace o konkrétních model Windows Forms tiskových úlohách, včetně postupu při programovém vytvoření tiskové úlohy, najdete v tématu <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="7b45b-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b45b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b45b-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="7b45b-118">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b45b-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
