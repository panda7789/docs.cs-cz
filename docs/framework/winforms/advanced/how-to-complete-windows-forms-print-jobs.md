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
ms.workload: dotnet
ms.openlocfilehash: 00c43ff4ca418d272dc00132907c5bcbc0c5bc8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Postupy: Dokončení tiskových úloh Windows Forms
Textové editory a dalších aplikací, které zahrnují tisk často, bude poskytují možnost zobrazit zprávu uživatelům, tisková úloha je dokončena. Tuto funkci můžete zadat v systému Windows Forms pomocí zpracování <xref:System.Drawing.Printing.PrintDocument.EndPrint> události <xref:System.Drawing.Printing.PrintDocument> součásti.  
  
 Následující postup vyžaduje, že jste vytvořili aplikace pro systém Windows s <xref:System.Drawing.Printing.PrintDocument> součásti na něm, což je standardní způsob povolení tisku z aplikací se systémem Windows. Další informace o tisk pomocí Windows Forms <xref:System.Drawing.Printing.PrintDocument> součást, najdete v části [postupy: vytvoření standardní tiskových úloh formulářů Windows](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>K dokončení tiskových úloh  
  
1.  Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost <xref:System.Drawing.Printing.PrintDocument> součásti.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  Napsat kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.EndPrint> událostí.  
  
     V následujícím příkladu kódu se zobrazí okno se zprávou, která udává, že dokončen tisk.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
