---
title: 'Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 6ec3765eb667f8a249afa815400eb7f1edbec3dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632943"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView
Můžete řídit vzhled <xref:System.Windows.Forms.DataGridView> řádky podle jednoho nebo obou zpracování <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> události. Tyto události jsou navržené tak, aby můžete vykreslení pouze co byste chtěli while s informacemi <xref:System.Windows.Forms.DataGridView> zbývající vykreslení ovládacího prvku. Například pokud chcete vykreslení vlastní pozadí, můžete zpracovávat <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> událostí a umožňují jednotlivých buněk vykreslení vlastní obsah popředí. Alternativně můžete nechat buněk se a přidat vlastní popředí obsah v obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> událostí. Můžete také zakázat vykreslení obsahu buňky a malovat všechno sami <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> obslužné rutiny události.  
  
 Následující příklad kódu implementuje obslužné rutiny pro obě události negace Výběr barevného přechodu pozadí a některé vlastní popředí obsahu, která zahrnuje více sloupců.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
