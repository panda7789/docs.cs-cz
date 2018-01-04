---
title: "Postupy: Tisk vícestránkového textového souboru ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4576e969ba917b845cc8fbd6420741e2b24062fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Postupy: Tisk vícestránkového textového souboru ve Windows Forms
Je velmi běžné aplikace založené na systému Windows k vytištění textu. <xref:System.Drawing.Graphics> Třída poskytuje metody pro kreslení objekty (grafiky nebo text) na zařízení, jako je například obrazovky nebo tiskárny.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> nejsou podporovány pro tisk. Je třeba použít <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak je znázorněno v následujícím příkladu kódu kreslení textu pro účely tisku.  
  
### <a name="to-print-text"></a>Tisk textu  
  
1.  Přidat <xref:System.Drawing.Printing.PrintDocument> řetězec do svého formuláře a součást.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  Pokud tisk dokumentu, nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost k tomuto dokumentu chcete vytisknout a otevřít a přečíst obsah dokumentů na řetězec, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  V <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsahu dokumentu vypočítat řádek délku a řádků na stránce. Po každé stránce vykreslením, zkontrolujte, zda se jedná o poslední stránku a nastavit <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Událost se vyvolá, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> je `false`. Ujistěte se také, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost souvisí s příslušnou metodu zpracování událostí.  
  
     V následujícím příkladu kódu obslužné rutiny události se používá k vytištění obsahu souboru "testPage.txt" ve stejném písmo, jako se používá ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  Volání <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda zvýšit <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Textový soubor s názvem testPage.txt obsahující text, který se tisknout, umístěný v kořenovém adresáři jednotky C:\\. Úprava kódu k tisku jiný soubor.  
  
-   Odkazy na systém, System.Windows.Forms, System.Drawing sestavení.  
  
-   Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
