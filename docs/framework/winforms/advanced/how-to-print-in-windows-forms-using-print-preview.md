---
title: Tisk pomocí náhledu tisku
description: Naučte se, jak do aplikace přidat služby pro tisk ve verzi Preview pomocí ovládacího prvku model Windows Forms PrintPreviewDialog –.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621610"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Postupy: Tisk ve Windows Forms pomocí náhledu tisku
Kromě tiskových služeb je velmi běžné, že model Windows Forms programování nabízí náhled tisku. Snadný způsob, jak do vaší aplikace přidat služby pro tisk ve verzi Preview, je použít <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek v kombinaci s <xref:System.Drawing.Printing.PrintDocument.PrintPage> logikou zpracování událostí pro tisk souboru.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Náhled textového dokumentu pomocí ovládacího prvku PrintPreviewDialog –  
  
1. <xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Drawing.Printing.PrintDocument> Do formuláře přidejte dva řetězce, a.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentu do řetězce, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Stejně jako při tisku dokumentu <xref:System.Drawing.Printing.PrintDocument.PrintPage> použijte v obslužné rutině události <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsah souboru k výpočtu řádků na stránku a vykreslení obsahu dokumentu. Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. <xref:System.Drawing.Printing.PrintDocument.PrintPage>Událost je vyvolána, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> není `false` . Po dokončení vykreslování dokumentu resetujte řetězec, který se má vykreslit. Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> je událost přidružená ke své metodě zpracování událostí.  
  
    > [!NOTE]
    > Pokud jste v aplikaci nasadili tisk, možná jste už dokončili kroky 2 a 3.  
  
     V následujícím příkladu kódu slouží obslužná rutina události k vytištění souboru "testPage.txt" ve stejném písmu, které je použito ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. Nastavte <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku na <xref:System.Drawing.Printing.PrintDocument> součást ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. Zavolejte <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu na <xref:System.Windows.Forms.PrintPreviewDialog> ovládacím prvku. Obvykle byste volali <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro <xref:System.Windows.Forms.Control.Click> zpracování událostí tlačítka. Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolává <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost a vykresluje výstup do <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku. Když uživatel klikne na ikonu tisku v dialogovém okně, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost se znovu vyvolá a pošle se výstup do tiskárny místo dialogového okna Preview. To je důvod, proč se řetězec resetuje na konci procesu vykreslování v kroku 3.  
  
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

- [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
- [Bezpečnější tisk ve Windows Forms](../more-secure-printing-in-windows-forms.md)
