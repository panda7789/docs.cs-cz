---
title: "Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView"
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
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b312dca036b327ee86527607db8b73d4545500d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView
Když povolíte kopírování buňky, provedete dat ve vaší <xref:System.Windows.Forms.DataGridView> snadno dostupný k ostatním aplikacím prostřednictvím ovládacího prvku <xref:System.Windows.Forms.Clipboard>. Hodnoty vybraných buněk jsou převedeny na řetězce a přidat do schránky jako text oddělený tabulátory hodnot pro vložení do aplikace, jako je Poznámkový blok a aplikace Excel a jako tabulku ve formátu HTML pro vložení do aplikace, jako je Word.  
  
 Můžete nakonfigurovat buňky kopírování ke kopírování hodnot v buňkách, zahrnout text záhlaví řádků a sloupců do dat ze schránky nebo zahrnovat text záhlaví jenom v případě, že uživatelé vybrat celé řádky nebo sloupce.  
  
 V závislosti na režimu výběru uživatelé mohou vybrat více skupin odpojené buněk. Když uživatel kopie buněk do schránky, nebudou zkopírovány řádků a sloupců s žádné vybraných buněk. Všechny ostatní řádky nebo sloupce stát řádků a sloupců v tabulce dat zkopírován do schránky. Nezaškrtnuté buněk v tyto řádky a sloupce se zástupnými symboly prázdné zkopírován do schránky.  
  
### <a name="to-enable-cell-copying"></a>Povolit kopírování buňky  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kompletní kód ukazuje, jak jsou buněk zkopírován do schránky. Tento příklad obsahuje tlačítko, které zkopíruje vybrané buňky do schránky pomocí <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> metoda a zobrazí obsah schránky do textového pole.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód vyžaduje:  
  
-   Odkazy na sestavení n: System a N:System.Windows.Forms.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>  
 [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
