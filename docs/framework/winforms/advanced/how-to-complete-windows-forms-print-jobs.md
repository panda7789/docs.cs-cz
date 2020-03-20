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
# <a name="how-to-complete-windows-forms-print-jobs"></a>Postupy: Dokončení tiskových úloh Windows Forms
Textové procesory a další aplikace, které zahrnují tisk, často poskytují možnost zobrazit uživatelům zprávu, že tisková úloha je dokončena. Tuto funkci můžete zadat ve formulářích <xref:System.Drawing.Printing.PrintDocument.EndPrint> systému <xref:System.Drawing.Printing.PrintDocument> Windows zpracováním události součásti.  
  
 Následující postup vyžaduje, abyste vytvořili aplikaci <xref:System.Drawing.Printing.PrintDocument> založenou na systému Windows s komponentou, což je standardní způsob povolení tisku z aplikace založené na systému Windows. Další informace o tisku z <xref:System.Drawing.Printing.PrintDocument> formulářů systému Windows pomocí komponenty naleznete v [tématu Postup: Vytvoření standardních tiskových úloh formulářů systému Windows](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Dokončení tiskové úlohy  
  
1. Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost komponenty. <xref:System.Drawing.Printing.PrintDocument>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. Napište kód <xref:System.Drawing.Printing.PrintDocument.EndPrint> pro zpracování události.  
  
     V následujícím příkladu kódu se zobrazí okno se zprávou označující, že dokument byl dokončen tisk.  
  
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
  
     (Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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

- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
