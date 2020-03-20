---
title: Vytvořit standardní tiskové úlohy
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182571"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Postupy: Vytváření standardních tiskových úloh Windows Forms
Základem tisku ve Windows <xref:System.Drawing.Printing.PrintDocument> Forms je součást <xref:System.Drawing.Printing.PrintDocument.PrintPage> – konkrétně událost. Psaním kódu pro <xref:System.Drawing.Printing.PrintDocument.PrintPage> zpracování události můžete určit, co se má vytisknout a jak ji vytisknout.  
  
### <a name="to-create-a-print-job"></a>Vytvoření tiskové úlohy  
  
1. Přidejte <xref:System.Drawing.Printing.PrintDocument> součást do formuláře.  
  
2. Napište kód <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro zpracování události.  
  
     Budete muset kód vlastní tiskové logiky. Kromě toho budete muset zadat materiál, který má být vytištěn.  
  
     V následujícím příkladu kódu je v obslužné rutině události vytvořena ukázková grafika ve tvaru červeného obdélníku, <xref:System.Drawing.Printing.PrintDocument.PrintPage> která bude sloužit jako materiál, který má být vytištěn.  
  
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
  
     (Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
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
  
     Můžete také napsat kód pro <xref:System.Drawing.Printing.PrintDocument.BeginPrint> <xref:System.Drawing.Printing.PrintDocument.EndPrint> události a, případně včetně celého čísla představujícícelkový počet stránek k tisku, který je při tisku jednotlivých stránek snížen.  
  
    > [!NOTE]
    > Do formuláře <xref:System.Windows.Forms.PrintDialog> můžete přidat komponentu, která uživatelům poskytne čisté a efektivní uživatelské rozhraní. Nastavení <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnosti <xref:System.Windows.Forms.PrintDialog> komponenty umožňuje nastavit vlastnosti související s tiskovým dokumentem, se kterým pracujete ve formuláři. Další informace o <xref:System.Windows.Forms.PrintDialog> součásti naleznete v tématu [PrintDialog Component](../controls/printdialog-component-windows-forms.md).  
  
     Další informace o specifikách tiskových úloh windows forms, včetně programového vytvoření <xref:System.Drawing.Printing.PrintPageEventArgs>tiskové úlohy, naleznete v tématu .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.Printing.PrintDocument>
- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
