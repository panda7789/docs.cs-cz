---
title: 'Postupy: tisk vícestránkového textového souboru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740658"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Postupy: Tisk vícestránkového textového souboru ve Windows Forms
Pro aplikace založené na systému Windows je velmi běžné tisknout text. Třída <xref:System.Drawing.Graphics> poskytuje metody pro kreslení objektů (grafika nebo text) do zařízení, jako je například obrazovka nebo tiskárna.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody <xref:System.Windows.Forms.TextRenderer> nejsou podporovány pro tisk. Vždy byste měli použít <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak je znázorněno v následujícím příkladu kódu pro vykreslení textu pro účely tisku.  
  
### <a name="to-print-text"></a>Postup tisku textu  
  
1. Přidejte do formuláře komponentu <xref:System.Drawing.Printing.PrintDocument> a řetězec.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Při tisku dokumentu nastavte vlastnost <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentů do řetězce, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. V obslužné rutině události <xref:System.Drawing.Printing.PrintDocument.PrintPage> použijte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> třídy <xref:System.Drawing.Printing.PrintPageEventArgs> a obsah dokumentu pro výpočet délky řádku a řádků na stránku. Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud není <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false`. Také se ujistěte, že je událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> spojena s metodou zpracování události.  
  
     V následujícím příkladu kódu slouží obslužná rutina události k tisku obsahu souboru "testPage. txt" ve stejném písmu, které je použito ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Zavolejte metodu <xref:System.Drawing.Printing.PrintDocument.Print%2A> pro vyvolání události <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Textový soubor s názvem testPage. txt obsahující text, který se má vytisknout, umístěný v kořenové složce jednotky C:\\. Upravte kód pro tisk jiného souboru.  
  
- Odkazy na sestavení System, System. Windows. Forms, System. Drawing.  
  
- Informace o tom, jak tento příklad sestavit z příkazového řádku pro Visual Basic C#nebo vizuál, najdete v tématu [sestavování z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo při [sestavování z příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad můžete vytvořit také v aplikaci Visual Studio vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
