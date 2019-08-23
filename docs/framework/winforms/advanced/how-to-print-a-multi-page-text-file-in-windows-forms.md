---
title: 'Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms'
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
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931792"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms
Pro aplikace založené na systému Windows je velmi běžné tisknout text. <xref:System.Drawing.Graphics> Třída poskytuje metody pro kreslení objektů (grafika nebo text) do zařízení, jako je například obrazovka nebo tiskárna.  
  
> [!NOTE]
> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metodypro<xref:System.Windows.Forms.TextRenderer> nejsou podporovány pro tisk. Vždy byste měli použít <xref:System.Drawing.Graphics.DrawString%2A> <xref:System.Drawing.Graphics>metody, jak je znázorněno v následujícím příkladu kódu pro vykreslení textu pro účely tisku.  
  
### <a name="to-print-text"></a>Postup tisku textu  
  
1. <xref:System.Drawing.Printing.PrintDocument> Přidejte komponentu a řetězec do formuláře.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Při tisku dokumentu nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost na dokument, který chcete vytisknout, a otevřete a přečtěte si obsah dokumentů do řetězce, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. V obslužné rutině <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintDocument.PrintPage> události použijte vlastnost třídy a obsah dokumentu k výpočtu délky řádku a řádků na stránce. Po vykreslení každé stránky zkontrolujte, zda se jedná o poslední stránku, a nastavte <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. Událost <xref:System.Drawing.Printing.PrintDocument.PrintPage> je vyvolána, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> není `false`. Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> je událost přidružená ke své metodě zpracování událostí.  
  
     V následujícím příkladu kódu slouží obslužná rutina události k tisku obsahu souboru "testPage. txt" ve stejném písmu, které je použito ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Zavolejte metodu pro vyvolání <xref:System.Drawing.Printing.PrintDocument.PrintPage>události. <xref:System.Drawing.Printing.PrintDocument.Print%2A>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Textový soubor s názvem testPage. txt obsahující text, který se má vytisknout, umístěný v kořenové složce jednotky C\\:. Upravte kód pro tisk jiného souboru.  
  
- Odkazy na sestavení System, System. Windows. Forms, System. Drawing.  
  
- Informace o tom, jak tento příklad sestavit z příkazového řádku pro Visual Basic C#nebo vizuál, najdete v tématu sestavování [z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo při sestavování z [příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad můžete vytvořit také v aplikaci Visual Studio vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
