---
title: Vytvořit standardní tiskové úlohy
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182571"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="d0238-102">Postupy: Vytváření standardních tiskových úloh Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0238-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="d0238-103">Základem tisku ve Windows <xref:System.Drawing.Printing.PrintDocument> Forms je součást <xref:System.Drawing.Printing.PrintDocument.PrintPage> – konkrétně událost.</span><span class="sxs-lookup"><span data-stu-id="d0238-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="d0238-104">Psaním kódu pro <xref:System.Drawing.Printing.PrintDocument.PrintPage> zpracování události můžete určit, co se má vytisknout a jak ji vytisknout.</span><span class="sxs-lookup"><span data-stu-id="d0238-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="d0238-105">Vytvoření tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="d0238-105">To create a print job</span></span>  
  
1. <span data-ttu-id="d0238-106">Přidejte <xref:System.Drawing.Printing.PrintDocument> součást do formuláře.</span><span class="sxs-lookup"><span data-stu-id="d0238-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="d0238-107">Napište kód <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="d0238-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="d0238-108">Budete muset kód vlastní tiskové logiky.</span><span class="sxs-lookup"><span data-stu-id="d0238-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="d0238-109">Kromě toho budete muset zadat materiál, který má být vytištěn.</span><span class="sxs-lookup"><span data-stu-id="d0238-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="d0238-110">V následujícím příkladu kódu je v obslužné rutině události vytvořena ukázková grafika ve tvaru červeného obdélníku, <xref:System.Drawing.Printing.PrintDocument.PrintPage> která bude sloužit jako materiál, který má být vytištěn.</span><span class="sxs-lookup"><span data-stu-id="d0238-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="d0238-111">(Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d0238-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="d0238-112">Můžete také napsat kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> <xref:System.Drawing.Printing.PrintDocument.EndPrint> události a, případně včetně celého čísla představujícícelkový počet stránek k tisku, který je při tisku jednotlivých stránek snížen.</span><span class="sxs-lookup"><span data-stu-id="d0238-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d0238-113">Do formuláře <xref:System.Windows.Forms.PrintDialog> můžete přidat komponentu, která uživatelům poskytne čisté a efektivní uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d0238-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="d0238-114">Nastavení <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnosti <xref:System.Windows.Forms.PrintDialog> komponenty umožňuje nastavit vlastnosti související s tiskovým dokumentem, se kterým pracujete ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="d0238-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="d0238-115">Další informace o <xref:System.Windows.Forms.PrintDialog> součásti naleznete v tématu [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d0238-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="d0238-116">Další informace o specifikách tiskových úloh windows forms, včetně programového vytvoření <xref:System.Drawing.Printing.PrintPageEventArgs>tiskové úlohy, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="d0238-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0238-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0238-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="d0238-118">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0238-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
