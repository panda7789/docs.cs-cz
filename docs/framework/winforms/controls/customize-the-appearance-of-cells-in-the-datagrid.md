---
title: "Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView"
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
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 545a3bff5e810f9c0a995366e7f6460930f9e936
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView
Můžete přizpůsobit vzhled libovolnou buňku zpracování <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CellPainting> událostí. Můžete rozbalit <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Drawing.Graphics> z <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. Pomocí této <xref:System.Drawing.Graphics>, může ovlivnit vzhled celý <xref:System.Windows.Forms.DataGridView> řízení, ale bude obvykle má vliv pouze na vzhled buňku, která je aktuálně probíhá vykresluje. <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> Vlastnost <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> umožňuje omezit na buňku, která je aktuálně probíhá vykresluje vaší Malování operací.  
  
 V následujícím příkladu kódu, bude v buňkách v malování `ContactName` sloupce pomocí <xref:System.Windows.Forms.DataGridView> ovládacího prvku barevné schéma. Obsah textu jednotlivých buněk se vykresluje v <xref:System.Drawing.Color.Crimson%2A>, a inset obdélníku se vykresluje v barvu stejné jako <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.GridColor%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` s `ContactName` sloupců, jako je třeba v tabulce zákazníků v ukázkové databázi Northwind.  
  
-   Odkazy na sestavení systému, System.Windows.Forms a System.Drawing.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellPainting>  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
