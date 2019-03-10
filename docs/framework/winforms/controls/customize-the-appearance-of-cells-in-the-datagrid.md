---
title: 'Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: add865eedc54253ad257e0e142e555da52f341dd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703345"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView
Můžete přizpůsobit vzhled libovolnou buňku ve zpracování <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CellPainting> událostí. Můžete rozbalit <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Drawing.Graphics> z <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. S tímto <xref:System.Drawing.Graphics>, může mít vliv na vzhled celý <xref:System.Windows.Forms.DataGridView> ovládacího prvku, ale bude obvykle chcete ovlivnit pouze vzhled buňky, která je právě překreslit. <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> Vlastnost <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umožňuje omezit vaše operace Malování na buňku, která je právě překreslit.  
  
 V následujícím příkladu kódu, bude kreslit všechny buňky v `ContactName` pomocí sloupce <xref:System.Windows.Forms.DataGridView> ovládacího prvku barevném schématu. Každá buňka textový obsah vymalováním v <xref:System.Drawing.Color.Crimson%2A>, a inset obdélníku je vykreslen v stejnou barvu jako <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.GridColor%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` s `ContactName` sloupců, jako je třeba v tabulce Zákazníci v ukázkové databázi Northwind.  
  
-   Odkazy na sestavení systému, System.Windows.Forms a System.Drawing.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
