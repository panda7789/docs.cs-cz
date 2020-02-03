---
title: Přizpůsobení vzhledu buněk v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744050"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView
Můžete přizpůsobit vzhled libovolné buňky zpracováním události <xref:System.Windows.Forms.DataGridView.CellPainting> ovládacího prvku <xref:System.Windows.Forms.DataGridView>. <xref:System.Drawing.Graphics> ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete extrahovat z vlastnosti <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. V tomto <xref:System.Drawing.Graphics>můžete ovlivnit vzhled celého ovládacího prvku <xref:System.Windows.Forms.DataGridView>, ale obvykle budete chtít mít vliv pouze na vzhled buňky, která je právě vykreslena. Vlastnost <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umožňuje omezit operace malování na buňku, která je právě vykreslena.  
  
 V následujícím příkladu kódu budete malovat všechny buňky ve sloupci `ContactName` pomocí barevného schématu ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Textový obsah každé buňky se vykresluje <xref:System.Drawing.Color.Crimson%2A>a vsazený obdélník se vykreslí stejnou barvou jako vlastnost <xref:System.Windows.Forms.DataGridView.GridColor%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` se sloupcem `ContactName`, jako je například ten v tabulce Customers v ukázkové databázi Northwind.  
  
- Odkazy na sestavení System, System. Windows. Forms a System. Drawing.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
