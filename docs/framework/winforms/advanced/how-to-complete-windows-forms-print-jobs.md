---
title: Dokončení tiskových úloh
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746501"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Postupy: Dokončení tiskových úloh Windows Forms
Často používané wordové procesory a další aplikace, které zahrnují tisk, poskytují možnost Zobrazit zprávu uživatelům, že se tisková úloha dokončila. Tuto funkci můžete ve svém model Windows Forms poskytnout tak, že provedete událost <xref:System.Drawing.Printing.PrintDocument.EndPrint> součásti <xref:System.Drawing.Printing.PrintDocument>.  
  
 Následující postup vyžaduje, abyste vytvořili aplikaci založenou na systému Windows s <xref:System.Drawing.Printing.PrintDocument> komponentou, což je standardní způsob, jak povolit tisk z aplikace založené na systému Windows. Další informace o tisku z model Windows Forms pomocí komponenty <xref:System.Drawing.Printing.PrintDocument> naleznete v tématu [How to: Create Standard model Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Dokončení tiskové úlohy  
  
1. Nastavte vlastnost <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> komponenty <xref:System.Drawing.Printing.PrintDocument>.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. Napište kód pro zpracování události <xref:System.Drawing.Printing.PrintDocument.EndPrint>.  
  
     V následujícím příkladu kódu se zobrazí okno se zprávou, které indikuje, že dokument dokončil tisk.  
  
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
  
     (Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
