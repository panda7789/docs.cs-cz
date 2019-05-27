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
ms.openlocfilehash: a95e07596a10e67d32fdd0af036a14e8d66390c7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053034"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Postupy: Dokončení tiskových úloh v modelu Windows Forms
Často textových editorů a další aplikace, které se týkají tisku bude poskytovat možnost pro zobrazení zprávy pro uživatele, tisková úloha je dokončena. Tuto funkci můžete zadat do svých formulářů Windows pomocí manipulace <xref:System.Drawing.Printing.PrintDocument.EndPrint> událost <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
 Následující postup vyžaduje, že jste vytvořili aplikaci založené na Windows s <xref:System.Drawing.Printing.PrintDocument> komponentu v něm, což je standardní způsob povolení tisku z aplikací se systémem Windows. Další informace o tisk pomocí Windows Forms <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete v tématu [jak: Vytvoření tiskových úloh standardní Windows Forms](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>K dokončení tiskové úlohy  
  
1. Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. Napište kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.EndPrint> událostí.  
  
     V následujícím příkladu kódu se zobrazí okno se zprávou, označující, že dokument dokončení tisku.  
  
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
  
     (Visual C# a vizuální C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
