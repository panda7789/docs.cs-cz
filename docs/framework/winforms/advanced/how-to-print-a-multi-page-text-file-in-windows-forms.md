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
ms.openlocfilehash: b17ddcb22f3e1b7dc181e977a0227db5490b66fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330197"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms
Je velmi běžné, že aplikace založené na Windows pro tisk textu. <xref:System.Drawing.Graphics> Třída poskytuje metody pro vykreslení objektů (grafiky nebo text) na zařízení, jako je obrazovka nebo tiskárny.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> nejsou podporovány pro tisk. Vždycky byste měli použít <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak je znázorněno v následujícím příkladu kódu, chcete-li nakreslit text pro účely tisku.  
  
### <a name="to-print-text"></a>Tisk textu  
  
1. Přidat <xref:System.Drawing.Printing.PrintDocument> komponenty a řetězec do formuláře.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Pokud tisk dokumentu, nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost v dokumentu, který chcete vytisknout a otevřít a číst obsah dokumentů na řetězec, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužná rutina události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třída a dokument obsah k výpočtu délky a řádky na jedné stránce řádků. Po jednotlivých stránkách vykreslením, zkontrolujte, zda se jedná o poslední stránku a nastavit <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Událost se vyvolá, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> je `false`. Také se ujistěte, že <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost je přidružena jeho metody zpracování událostí.  
  
     V následujícím příkladu kódu obslužné rutiny události umožňuje vytisknout obsah souboru "testPage.txt" ve stejném písma se používá ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Volání <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda k vyvolání <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Textový soubor s názvem testPage.txt obsahující text pro tisk, umístěn v kořenové složce jednotky C:\\. Upravte kód pro tisk jiný soubor.  
  
-   Odkazy na systém, System.Windows.Forms, System.Drawing sestavení.  
  
-   Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Podpora tisku v modelu Windows Forms](windows-forms-print-support.md)
