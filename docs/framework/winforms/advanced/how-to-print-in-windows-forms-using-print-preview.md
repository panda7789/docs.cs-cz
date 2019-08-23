---
title: 'Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 07137d03dd9a20d8eab564757618e48e25b45353
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931757"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku
Kromě tiskových služeb je velmi běžné, že model Windows Forms programování nabízí náhled tisku. Snadný způsob, jak do vaší aplikace přidat služby pro tisk ve verzi Preview, <xref:System.Windows.Forms.PrintPreviewDialog> je použít ovládací prvek v <xref:System.Drawing.Printing.PrintDocument.PrintPage> kombinaci s logikou zpracování událostí pro tisk souboru.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Náhled textového dokumentu pomocí ovládacího prvku PrintPreviewDialog –  
  
1. Do formuláře přidejte <xref:System.Drawing.Printing.PrintDocument>dva řetězce ,a.<xref:System.Windows.Forms.PrintPreviewDialog>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> Nastavte vlastnost na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentu do řetězce, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Stejně jako při tisku dokumentu <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> použijte v obslužné rutině události vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsah souboru k výpočtu řádků na stránku a vykreslení obsahu dokumentu. Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> není `false`. Po dokončení vykreslování dokumentu resetujte řetězec, který se má vykreslit. Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> je událost přidružená ke své metodě zpracování událostí.  
  
    > [!NOTE]
    > Pokud jste v aplikaci nasadili tisk, možná jste už dokončili kroky 2 a 3.  
  
     V následujícím příkladu kódu slouží obslužná rutina události k vytištění souboru "testPage. txt" ve stejném písmu použitém ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> Nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku<xref:System.Drawing.Printing.PrintDocument> na součást ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Zavolejte metodu<xref:System.Windows.Forms.PrintPreviewDialog> na ovládacím prvku. Obvykle byste volali <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> <xref:System.Windows.Forms.Control.Click> metodu pro zpracování událostí tlačítka. Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolává<xref:System.Drawing.Printing.PrintDocument.PrintPage> událost a<xref:System.Windows.Forms.PrintPreviewDialog> vykresluje výstup do ovládacího prvku. Když uživatel klikne na ikonu tisku v dialogovém okně, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost se znovu vyvolá a pošle se výstup do tiskárny místo dialogového okna Preview. To je důvod, proč se řetězec resetuje na konci procesu vykreslování v kroku 3.  
  
     Následující příklad kódu ukazuje <xref:System.Windows.Forms.Control.Click> metodu zpracování událostí pro tlačítko ve formuláři. Tato metoda zpracování události volá metody pro čtení dokumentu a zobrazení dialogového okna Náhled tisku.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Windows. Forms, System. Drawing.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytiskněte textový soubor s více stránkami v model Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
- [Zabezpečenější tisk ve Windows Forms](../more-secure-printing-in-windows-forms.md)
