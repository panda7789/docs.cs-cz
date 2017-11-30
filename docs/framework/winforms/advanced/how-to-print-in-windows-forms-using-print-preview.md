---
title: "Postupy: Tisk ve Windows Forms pomocí náhledu tisku"
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
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08ed914ebd868390233cead97de5d326eb77e390
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>Postupy: Tisk ve Windows Forms pomocí náhledu tisku
Je velmi běžné ve Windows Forms programování nabízet náhledu tisku kromě tisk služby. Snadný způsob, jak do aplikace přidat náhledu tisku služby je použití <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek v kombinaci s <xref:System.Drawing.Printing.PrintDocument.PrintPage> logiku zpracování událostí pro tisk souboru.  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>Zobrazte náhled textový dokument s printpreviewdialog – ovládací prvek  
  
1.  Přidat <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>a dva řetězce do svého formuláře.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  Nastavte <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> vlastnost k tomuto dokumentu chcete vytisknout a otevírat a číst obsah dokumentu na řetězec, který jste přidali dříve.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  Stejně jako pro tisk dokumentu v <xref:System.Drawing.Printing.PrintDocument.PrintPage> obslužné rutiny události, použijte <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> třídy a obsah souboru vypočítat řádků na stránce a vykreslit obsah dokumentu. Po každé stránce vykreslením, zkontrolujte, zda se jedná o poslední stránku a nastavit <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> odpovídajícím způsobem. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Událost se vyvolá, dokud <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> je `false`. Po dokončení vykreslování dokumentu resetovat řetězec, který má být vykreslen. Ujistěte se také, <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost souvisí s příslušnou metodu zpracování událostí.  
  
    > [!NOTE]
    >  Možná jste již dokončili kroky 2 a 3 Pokud jste implementovali tisk ve vaší aplikaci.  
  
     V následujícím příkladu kódu obslužné rutiny události se používá k vytištění souboru "testPage.txt" ve stejném písmo použité ve formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  Nastavte <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintPreviewDialog> řídit k <xref:System.Drawing.Printing.PrintDocument> součásti na formuláři.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  Volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku. By obvykle volání <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metodu události tlačítka. Volání metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> vyvolá <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí a vykreslí výstup k <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku. Když uživatel klikne na ikonu tisku v dialogovém okně <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost se vyvolá, odesílá výstup na tiskárnu místo dialogové okno náhledu. Z tohoto důvodu řetězec se resetuje na konci procesu vykreslování v kroku 3.  
  
     Následující příklad kódu ukazuje <xref:System.Windows.Forms.Control.Click> metodu události pro tlačítko ve formuláři. Tato metoda zpracování událostí volá metody pro čtení dokumentu a zobrazit dialogové okno náhledu tisku.  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Windows.Forms, System.Drawing sestavení.  
  
-   Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Tisk vícestránkového textového souboru v systému Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Podpora tisku ve Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Bezpečnější tisk ve Windows Forms](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)
