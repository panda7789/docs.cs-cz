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
ms.openlocfilehash: 816da93218e20f73f16c14769ed1a549dd3d8eb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335404"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Postupy: Vytváření standardních tiskových úloh v modelu Windows Forms
Je základem pro tisk ve Windows Forms <xref:System.Drawing.Printing.PrintDocument> komponenty – přesněji řečeno <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí. Napsáním kódu pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí, můžete určit, co se má tisknout a jak ho vytisknout.  
  
### <a name="to-create-a-print-job"></a>Chcete-li vytvořit tiskové úlohy  
  
1. Přidat <xref:System.Drawing.Printing.PrintDocument> komponentu do formuláře.  
  
2. Napište kód pro zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.  
  
     Budete muset kód tisk logiku. Kromě toho budete muset zadat materiál, který se mají vytisknout.  
  
     V následujícím příkladu kódu je vytvořen Ukázkový obrázek v tvar obdélníku red v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužná rutina události tak, aby fungoval jako materiálů, které se mají vytisknout.  
  
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
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
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
  
     Můžete také napsat kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> a <xref:System.Drawing.Printing.PrintDocument.EndPrint> události, například včetně celé číslo představující celkový počet stránek pro tisk, který je snížen vytiskne každou stránku.  
  
    > [!NOTE]
    >  Můžete přidat <xref:System.Windows.Forms.PrintDialog> komponentu do formuláře k uživatelům poskytnout přehledné a efektivnější uživatelského rozhraní (UI). Nastavení <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintDialog> komponenta povoluje vám umožní nastavit vlastnosti související s tisk dokumentu je pracujete na formuláři. Další informace o <xref:System.Windows.Forms.PrintDialog> komponenty, naleznete v tématu [komponenty PrintDialog](../controls/printdialog-component-windows-forms.md).  
  
     Další informace o podrobnosti Windows Forms tiskové úlohy, včetně vytvoření tiskovou úlohu prostřednictvím kódu programu, najdete v části <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
