---
title: 'Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: 47ccd88ed30341e609b0569aaebc2db4dda3e40e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873861"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Postupy: Povolení kopírování více buněk do schránky z ovládacího prvku Windows Forms DataGridView
Když povolíte kopírování buňky, provedete data ve vaší <xref:System.Windows.Forms.DataGridView> snadný přístup k ostatním aplikacím prostřednictvím ovládacího prvku <xref:System.Windows.Forms.Clipboard>. Hodnoty vybrané buňky jsou převedeny na řetězce a přidali do schránky jako text oddělený tabulátory hodnoty pro vkládání do aplikací, jako je Poznámkový blok a Excel a jako tabulka ve formátu HTML pro vkládání do aplikací, jako je Word.  
  
 Můžete nakonfigurovat buňky kopírování ke kopírování hodnot v buňkách, zahrnout text záhlaví řádků a sloupců do schránky dat nebo obsahovat text záhlaví jenom v případě, že uživatelé vybrat celé řádky nebo sloupce.  
  
 V závislosti na režimu výběru mohou uživatelé vybrat více skupin odpojené buněk. Když uživatel zkopíruje do schránky buněk, řádků a sloupců s žádné vybrané buňky nejsou zkopírovány. Všechny ostatní řádky nebo sloupce se stanou řádků a sloupců v tabulce dat zkopírována do schránky. Nevybrané buňky v těchto řádcích nebo sloupcích se zkopírují jako prázdné zástupné symboly do schránky.  
  
### <a name="to-enable-cell-copying"></a>Povolit kopírování buňky  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kompletní kód ukazuje, jak se zkopírují buněk do schránky. Tento příklad obsahuje tlačítko, které se zkopíruje do schránky pomocí vybrané buňky <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> metoda a zobrazí obsah schránky do textového pole.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód vyžaduje:  
  
-   Odkazy na sestavení n: System a N:System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>  
 [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
