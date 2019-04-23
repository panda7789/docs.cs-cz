---
title: 'Postupy: Dokončení tiskových úloh v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 256b9a3d8842aaa4b032e67ebac9ca6a9e1ef34a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293752"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="c6bd9-102">Postupy: Dokončení tiskových úloh v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6bd9-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="c6bd9-103">Často textových editorů a další aplikace, které se týkají tisku bude poskytovat možnost pro zobrazení zprávy pro uživatele, tisková úloha je dokončena.</span><span class="sxs-lookup"><span data-stu-id="c6bd9-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="c6bd9-104">Tuto funkci můžete zadat do svých formulářů Windows pomocí manipulace <xref:System.Drawing.Printing.PrintDocument.EndPrint> událost <xref:System.Drawing.Printing.PrintDocument> komponenty.</span><span class="sxs-lookup"><span data-stu-id="c6bd9-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="c6bd9-105">Následující postup vyžaduje, že jste vytvořili aplikaci založené na Windows s <xref:System.Drawing.Printing.PrintDocument> komponentu v něm, což je standardní způsob povolení tisku z aplikací se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="c6bd9-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="c6bd9-106">Další informace o tisk pomocí Windows Forms <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete v tématu [jak: Vytvoření tiskových úloh standardní Windows Forms](how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="c6bd9-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="c6bd9-107">K dokončení tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="c6bd9-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="c6bd9-108">Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost <xref:System.Drawing.Printing.PrintDocument> komponenty.</span><span class="sxs-lookup"><span data-stu-id="c6bd9-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="c6bd9-109">Napište kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.EndPrint> událostí.</span><span class="sxs-lookup"><span data-stu-id="c6bd9-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="c6bd9-110">V následujícím příkladu kódu se zobrazí okno se zprávou, označující, že dokument dokončení tisku.</span><span class="sxs-lookup"><span data-stu-id="c6bd9-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     <span data-ttu-id="c6bd9-111">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c6bd9-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c6bd9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6bd9-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="c6bd9-113">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6bd9-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
