---
title: Tisk pomocí náhledu tisku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 1975c902fdb56326c763f2e2fc11e381ffc7fbd3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740604"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Postupy: Tisk ve Windows Forms pomocí náhledu tisku
Kromě tiskových služeb je velmi běžné, že model Windows Forms programování nabízí náhled tisku. Snadný způsob, jak do vaší aplikace přidat služby pro tisk ve verzi Preview, je použít ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> v kombinaci s logikou zpracování událostí <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro tisk souboru.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Náhled textového dokumentu pomocí ovládacího prvku PrintPreviewDialog –  
  
1. Přidejte do formuláře <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>a dva řetězce.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Nastavte vlastnost <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentu do řetězce, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Stejně jako při tisku dokumentu použijte v obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs> a obsah souboru pro výpočet řádků na stránku a vykreslení obsahu dokumentu. Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud není <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false`. Po dokončení vykreslování dokumentu resetujte řetězec, který se má vykreslit. Také se ujistěte, že je událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> spojena s metodou zpracování události.  
  
    > [!NOTE]
    > Pokud jste v aplikaci nasadili tisk, možná jste už dokončili kroky 2 a 3.  
  
     V následujícím příkladu kódu slouží obslužná rutina události k vytištění souboru "testPage. txt" ve stejném písmu použitém ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. Nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> na součást <xref:System.Drawing.Printing.PrintDocument> na formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. V ovládacím prvku <xref:System.Windows.Forms.PrintPreviewDialog> volejte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>. Obvykle byste volali <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z metody <xref:System.Windows.Forms.Control.Click> zpracování událostí tlačítka. Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolává událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> a vykresluje výstup do ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>. Když uživatel klikne na ikonu tisku v dialogovém okně, událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> se znovu vyvolá a pošle se výstup do tiskárny místo dialogového okna Preview. To je důvod, proč se řetězec resetuje na konci procesu vykreslování v kroku 3.  
  
     Následující příklad kódu ukazuje metodu zpracování událostí <xref:System.Windows.Forms.Control.Click> pro tlačítko ve formuláři. Tato metoda zpracování události volá metody pro čtení dokumentu a zobrazení dialogového okna Náhled tisku.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Windows. Forms, System. Drawing.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
- [Zabezpečenější tisk ve Windows Forms](../more-secure-printing-in-windows-forms.md)
