---
title: Vytvoření standardních tiskových úloh
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
ms.openlocfilehash: 4850dc901630179cc44fefda7e25bbabcfb4725f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741516"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Postupy: Vytváření standardních tiskových úloh Windows Forms
Základem tisku v model Windows Forms je <xref:System.Drawing.Printing.PrintDocument> komponenta – konkrétně událost <xref:System.Drawing.Printing.PrintDocument.PrintPage>. Napsáním kódu pro zpracování události <xref:System.Drawing.Printing.PrintDocument.PrintPage> můžete určit, co se má vytisknout, a jak ho vytisknout.  
  
### <a name="to-create-a-print-job"></a>Vytvoření tiskové úlohy  
  
1. Přidejte do formuláře komponentu <xref:System.Drawing.Printing.PrintDocument>.  
  
2. Napište kód pro zpracování události <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     Budete muset kódovat vlastní logiku tisku. Navíc budete muset určit materiál, který se má vytisknout.  
  
     V následujícím příkladu kódu je v obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> vytvořena ukázková grafika v obrazci červeného obdélníku, která bude fungovat jako materiál pro tisk.  
  
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
  
     Můžete také vytvořit kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> a <xref:System.Drawing.Printing.PrintDocument.EndPrint> události, třeba včetně celého čísla představujícího celkový počet stránek k vytištění, které se sníží při tisku každé stránky.  
  
    > [!NOTE]
    > Do formuláře můžete přidat komponentu <xref:System.Windows.Forms.PrintDialog>, abyste svým uživatelům zajistili čisté a efektivní uživatelské rozhraní (UI). Nastavením vlastnosti <xref:System.Windows.Forms.PrintDialog.Document%2A> komponenty <xref:System.Windows.Forms.PrintDialog> můžete nastavit vlastnosti, které se týkají tiskového dokumentu, se kterými pracujete na formuláři. Další informace o komponentě <xref:System.Windows.Forms.PrintDialog> naleznete v tématu [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Další informace o konkrétních model Windows Forms tiskových úlohách, včetně postupu při programovém vytvoření tiskové úlohy, najdete v tématu <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
