---
title: Kompletní tiskové úlohy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182599"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="07bbf-102">Postupy: Dokončení tiskových úloh Windows Forms</span><span class="sxs-lookup"><span data-stu-id="07bbf-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="07bbf-103">Textové procesory a další aplikace, které zahrnují tisk, často poskytují možnost zobrazit uživatelům zprávu, že tisková úloha je dokončena.</span><span class="sxs-lookup"><span data-stu-id="07bbf-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="07bbf-104">Tuto funkci můžete zadat ve formulářích <xref:System.Drawing.Printing.PrintDocument.EndPrint> systému <xref:System.Drawing.Printing.PrintDocument> Windows zpracováním události součásti.</span><span class="sxs-lookup"><span data-stu-id="07bbf-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="07bbf-105">Následující postup vyžaduje, abyste vytvořili aplikaci <xref:System.Drawing.Printing.PrintDocument> založenou na systému Windows s komponentou, což je standardní způsob povolení tisku z aplikace založené na systému Windows.</span><span class="sxs-lookup"><span data-stu-id="07bbf-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="07bbf-106">Další informace o tisku z <xref:System.Drawing.Printing.PrintDocument> formulářů systému Windows pomocí komponenty naleznete v [tématu Postup: Vytvoření standardních tiskových úloh formulářů systému Windows](how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="07bbf-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="07bbf-107">Dokončení tiskové úlohy</span><span class="sxs-lookup"><span data-stu-id="07bbf-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="07bbf-108">Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost komponenty. <xref:System.Drawing.Printing.PrintDocument></span><span class="sxs-lookup"><span data-stu-id="07bbf-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="07bbf-109">Napište kód <xref:System.Drawing.Printing.PrintDocument.EndPrint> pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="07bbf-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="07bbf-110">V následujícím příkladu kódu se zobrazí okno se zprávou označující, že dokument byl dokončen tisk.</span><span class="sxs-lookup"><span data-stu-id="07bbf-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
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
  
     <span data-ttu-id="07bbf-111">(Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="07bbf-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07bbf-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="07bbf-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="07bbf-113">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="07bbf-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
