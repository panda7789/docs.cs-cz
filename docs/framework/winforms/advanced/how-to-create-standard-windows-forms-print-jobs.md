---
title: "Postupy: Vytváření standardních tiskových úloh Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2b0ce30f76fe7f8cbdc156c4a8ff5abffafae10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="64e7c-102">Postupy: Vytváření standardních tiskových úloh Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64e7c-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="64e7c-103">Základ pro tisk ve Windows Forms je <xref:System.Drawing.Printing.PrintDocument> součást – přesněji řečeno, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.</span><span class="sxs-lookup"><span data-stu-id="64e7c-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="64e7c-104">Vytvořením kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí, můžete zadat, tisknout, jak můžete k jeho tisku.</span><span class="sxs-lookup"><span data-stu-id="64e7c-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="64e7c-105">Chcete-li vytvořit tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="64e7c-105">To create a print job</span></span>  
  
1.  <span data-ttu-id="64e7c-106">Přidat <xref:System.Drawing.Printing.PrintDocument> součásti do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="64e7c-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="64e7c-107">Napsat kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.</span><span class="sxs-lookup"><span data-stu-id="64e7c-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="64e7c-108">Budete muset code tisk logiky.</span><span class="sxs-lookup"><span data-stu-id="64e7c-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="64e7c-109">Kromě toho budete muset zadat materiálu k tisku.</span><span class="sxs-lookup"><span data-stu-id="64e7c-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="64e7c-110">V následujícím příkladu kódu je vytvořen obrázek ukázkové ve tvaru red obdélníku v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události tak, aby fungoval jako materiálu k tisku.</span><span class="sxs-lookup"><span data-stu-id="64e7c-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="64e7c-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="64e7c-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="64e7c-112">Můžete také psát kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> a <xref:System.Drawing.Printing.PrintDocument.EndPrint> události, případně včetně celé číslo představující celkový počet stránek tisknout, se odečte jako vytiskne každé stránce.</span><span class="sxs-lookup"><span data-stu-id="64e7c-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64e7c-113">Můžete přidat <xref:System.Windows.Forms.PrintDialog> součásti do svého formuláře zajistit vyčištění a efektivní uživatelské rozhraní (UI) pro vaše uživatele.</span><span class="sxs-lookup"><span data-stu-id="64e7c-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="64e7c-114">Nastavení <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintDialog> součást umožňuje vám umožní nastavit vlastnosti související s print dokladu, ve kterém pracujete s svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="64e7c-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="64e7c-115">Další informace o <xref:System.Windows.Forms.PrintDialog> součást, najdete v části [PrintDialog – komponenta](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="64e7c-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="64e7c-116">Další informace o jaké jsou specifikace Windows Forms tiskové úlohy, včetně toho, jak vytvořit tiskové úlohy prostřednictvím kódu programu, najdete v části <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="64e7c-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e7c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="64e7c-117">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="64e7c-118">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64e7c-118">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
