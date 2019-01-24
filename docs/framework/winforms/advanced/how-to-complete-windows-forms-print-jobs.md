---
title: 'Postupy: Kompletní Windows Forms tiskové úlohy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: f7504d645ea1fca6f45b17f79eb576919b782263
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572822"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Postupy: Kompletní Windows Forms tiskové úlohy
Často textových editorů a další aplikace, které se týkají tisku bude poskytovat možnost pro zobrazení zprávy pro uživatele, tisková úloha je dokončena. Tuto funkci můžete zadat do svých formulářů Windows pomocí manipulace <xref:System.Drawing.Printing.PrintDocument.EndPrint> událost <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
 Následující postup vyžaduje, že jste vytvořili aplikaci založené na Windows s <xref:System.Drawing.Printing.PrintDocument> komponentu v něm, což je standardní způsob povolení tisku z aplikací se systémem Windows. Další informace o tisk pomocí Windows Forms <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete v tématu [jak: Vytvoření tiskových úloh standardní Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>K dokončení tiskové úlohy  
  
1.  Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  Napište kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.EndPrint> událostí.  
  
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
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
- [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
