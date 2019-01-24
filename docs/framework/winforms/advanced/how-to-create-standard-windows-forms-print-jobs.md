---
title: 'Postupy: Vytvoření tiskových úloh standardní Windows Forms'
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
ms.openlocfilehash: 18078c5e6bf518487707a8dc5639b3d6aa8a5783
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723339"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="358f2-102">Postupy: Vytvoření tiskových úloh standardní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="358f2-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="358f2-103">Je základem pro tisk ve Windows Forms <xref:System.Drawing.Printing.PrintDocument> komponenty – přesněji řečeno <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.</span><span class="sxs-lookup"><span data-stu-id="358f2-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="358f2-104">Napsáním kódu pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí, můžete určit, co se má tisknout a jak ho vytisknout.</span><span class="sxs-lookup"><span data-stu-id="358f2-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="358f2-105">Chcete-li vytvořit tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="358f2-105">To create a print job</span></span>  
  
1.  <span data-ttu-id="358f2-106">Přidat <xref:System.Drawing.Printing.PrintDocument> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="358f2-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="358f2-107">Napište kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.</span><span class="sxs-lookup"><span data-stu-id="358f2-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="358f2-108">Budete muset kód tisk logiku.</span><span class="sxs-lookup"><span data-stu-id="358f2-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="358f2-109">Kromě toho budete muset zadat materiál, který se mají vytisknout.</span><span class="sxs-lookup"><span data-stu-id="358f2-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="358f2-110">V následujícím příkladu kódu je vytvořen Ukázkový obrázek v tvar obdélníku red v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužná rutina události tak, aby fungoval jako materiálů, které se mají vytisknout.</span><span class="sxs-lookup"><span data-stu-id="358f2-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="358f2-111">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="358f2-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="358f2-112">Můžete také napsat kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> a <xref:System.Drawing.Printing.PrintDocument.EndPrint> události, například včetně celé číslo představující celkový počet stránek pro tisk, který je snížen vytiskne každou stránku.</span><span class="sxs-lookup"><span data-stu-id="358f2-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="358f2-113">Můžete přidat <xref:System.Windows.Forms.PrintDialog> komponentu do formuláře k uživatelům poskytnout přehledné a efektivnější uživatelského rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="358f2-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="358f2-114">Nastavení <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintDialog> komponenta povoluje vám umožní nastavit vlastnosti související s tisk dokumentu je pracujete na formuláři.</span><span class="sxs-lookup"><span data-stu-id="358f2-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="358f2-115">Další informace o <xref:System.Windows.Forms.PrintDialog> komponenty, naleznete v tématu [komponenty PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="358f2-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="358f2-116">Další informace o podrobnosti Windows Forms tiskové úlohy, včetně vytvoření tiskovou úlohu prostřednictvím kódu programu, najdete v části <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="358f2-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358f2-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="358f2-117">See also</span></span>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="358f2-118">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="358f2-118">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
