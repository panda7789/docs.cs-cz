---
title: Automaticky měnit velikost buněk při změně obsahu v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: 86e3bce993aa06546e301c6d7a7e03a31013c337
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732070"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView
Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládacímu prvku, aby při každé změně obsahu automaticky změnil velikost jeho řádků, sloupců a hlaviček, takže jsou buňky vždycky dostatečně velké, aby se zobrazily jejich hodnoty bez omezení.  
  
 Máte spoustu možností, jak omezit, které buňky se používají k určení nových velikostí. Můžete například nakonfigurovat ovládací prvek tak, aby automaticky změnil šířku sloupce na základě hodnot v aktuálně zobrazených řádcích. Díky tomu se můžete vyhnout neefektivitě při práci s velkým počtem řádků, i když v takovém případě můžete chtít použít metody změny velikosti, například <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>, a upravit velikosti v době, kdy zvolíte.  
  
 Další informace o automatické změně velikosti najdete v tématu [Možnosti změny velikosti v ovládacím prvku DataGridView model Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 Následující příklad kódu ukazuje možnosti, které jsou k dispozici pro automatickou změnu velikosti.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Možnosti změny velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Postupy: Programová změna velikosti buněk k zobrazení celého obsahu v ovládacím prvku Windows Forms DataGridView](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
