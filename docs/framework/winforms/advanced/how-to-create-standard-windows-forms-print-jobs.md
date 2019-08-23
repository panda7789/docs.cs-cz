---
title: 'Postupy: Vytváření standardních tiskových úloh v modelu Windows Forms'
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
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938232"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Postupy: Vytváření standardních tiskových úloh v modelu Windows Forms
Základem tisku v model Windows Forms je <xref:System.Drawing.Printing.PrintDocument> komponenta, která se podrobněji <xref:System.Drawing.Printing.PrintDocument.PrintPage> týká události. Napsáním kódu pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> události můžete určit, co se má vytisknout, a jak ho vytisknout.  
  
### <a name="to-create-a-print-job"></a>Vytvoření tiskové úlohy  
  
1. <xref:System.Drawing.Printing.PrintDocument> Přidejte komponentu do formuláře.  
  
2. Napište kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> události.  
  
     Budete muset kódovat vlastní logiku tisku. Navíc budete muset určit materiál, který se má vytisknout.  
  
     V následujícím příkladu kódu se v obslužné rutině <xref:System.Drawing.Printing.PrintDocument.PrintPage> události vytvoří ukázková grafika v obrazci červeného obdélníku, která bude fungovat jako materiál k vytištění.  
  
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
  
     (Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
     Můžete také chtít napsat kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> události a <xref:System.Drawing.Printing.PrintDocument.EndPrint> , případně včetně celého čísla představujícího celkový počet stránek k vytištění, které se sníží při tisku každé stránky.  
  
    > [!NOTE]
    > Do formuláře můžete přidat <xref:System.Windows.Forms.PrintDialog> komponentu, která uživatelům poskytuje čisté a efektivní uživatelské rozhraní (UI). <xref:System.Windows.Forms.PrintDialog.Document%2A> Nastavení vlastnosti <xref:System.Windows.Forms.PrintDialog> komponenty vám umožní nastavit vlastnosti týkající se tiskového dokumentu, se kterým pracujete na formuláři. Další informace o <xref:System.Windows.Forms.PrintDialog> komponentě naleznete v tématu [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Další informace o konkrétních model Windows Forms tiskových úlohách, včetně postupu vytvoření tiskové úlohy programově, najdete v tématu <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
