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
ms.openlocfilehash: d803c9bec180f45c80e362af49c8eaa12bb9d985
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592954"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku
Je velmi běžné ve Windows Forms programování nabízí náhled tisku kromě tiskové služby. Snadný způsob, jak přidat do svojí aplikace náhledu služby, je použít <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku v kombinaci s <xref:System.Drawing.Printing.PrintDocument.PrintPage> logiku zpracování událostí pro tisk souboru.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Náhled textový dokument s printpreviewdialog – ovládací prvek  
  
1. Přidat <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>a dva řetězce do formuláře.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost v dokumentu, který chcete vytisknout a otevřít a číst obsah dokumentu na řetězec, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. Stejně jako pro tisk dokumentu v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužná rutina události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsah souboru k výpočtu řádků na stránce a vykresluje obsah dokumentu. Po jednotlivých stránkách vykreslením, zkontrolujte, zda se jedná o poslední stránku a nastavit <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Událost se vyvolá, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> je `false`. Po dokončení vykreslení dokumentu resetování řetězec, který má být vykreslen. Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost je přidružena jeho metody zpracování událostí.  
  
    > [!NOTE]
    >  Možná jste už dokončili kroky 2 a 3 Pokud implementujete tisk ve vaší aplikaci.  
  
     V následujícím příkladu kódu se obslužná rutina události používá k vytištění souboru "testPage.txt" ve stejném písmo použité ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. Nastavte <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek <xref:System.Drawing.Printing.PrintDocument> komponenty ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku. Obvykle by volat <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metody zpracování událostí tlačítka. Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolá <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí a vykreslí výstup <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku. Když uživatel klikne na ikonu tisku v dialogovém okně <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost se vyvolá, odesílá výstup na tiskárnu místo dialogové okno náhledu. Z tohoto důvodu řetězec se resetuje na konci samotný proces vykreslování v kroku 3.  
  
     Následující příklad kódu ukazuje <xref:System.Windows.Forms.Control.Click> metody zpracování událostí pro tlačítko na formuláři. Tato metoda zpracování událostí volá metody pro čtení dokumentu a zobrazit okno náhledu.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na systém, System.Windows.Forms, System.Drawing sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Tisk vícestránkového textového souboru ve Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
- [Zabezpečenější tisk ve Windows Forms](../more-secure-printing-in-windows-forms.md)
