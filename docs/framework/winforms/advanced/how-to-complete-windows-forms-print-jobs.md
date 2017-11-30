---
title: "Postupy: Dokončení tiskových úloh Windows Forms"
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
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9decba052589bfcc3ecd7b2861dad51e9c51378a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="9b73d-102">Postupy: Dokončení tiskových úloh Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b73d-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="9b73d-103">Textové editory a dalších aplikací, které zahrnují tisk často, bude poskytují možnost zobrazit zprávu uživatelům, tisková úloha je dokončena.</span><span class="sxs-lookup"><span data-stu-id="9b73d-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="9b73d-104">Tuto funkci můžete zadat v systému Windows Forms pomocí zpracování <xref:System.Drawing.Printing.PrintDocument.EndPrint> události <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="9b73d-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="9b73d-105">Následující postup vyžaduje, že jste vytvořili aplikace pro systém Windows s <xref:System.Drawing.Printing.PrintDocument> součásti na něm, což je standardní způsob povolení tisku z aplikací se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="9b73d-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="9b73d-106">Další informace o tisk pomocí Windows Forms <xref:System.Drawing.Printing.PrintDocument> součást, najdete v části [postupy: vytvoření standardní tiskových úloh formulářů Windows](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="9b73d-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="9b73d-107">K dokončení tiskových úloh</span><span class="sxs-lookup"><span data-stu-id="9b73d-107">To complete a print job</span></span>  
  
1.  <span data-ttu-id="9b73d-108">Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="9b73d-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  <span data-ttu-id="9b73d-109">Napsat kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.EndPrint> událostí.</span><span class="sxs-lookup"><span data-stu-id="9b73d-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="9b73d-110">V následujícím příkladu kódu se zobrazí okno se zprávou, která udává, že dokončen tisk.</span><span class="sxs-lookup"><span data-stu-id="9b73d-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
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
  
     <span data-ttu-id="9b73d-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9b73d-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b73d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b73d-112">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="9b73d-113">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b73d-113">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
