---
title: 'Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 3411b68b4dcc64dba86cd9fa8804e0a487cec76d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586640"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>Postupy: Automatická změna velikosti buněk při změně obsahu v ovládacím prvku Windows Forms DataGridView
Můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> řízení ke změně velikosti jeho řádky, sloupce a záhlaví automaticky pokaždé, když obsah změny, tak, aby buňky jsou vždy dostatečně velký pro zobrazení jejich hodnoty bez oříznutí.  
  
 Máte řadu možností pro omezení buněk, které se používají k určení nové velikosti. Můžete například nakonfigurovat ovládací prvek automaticky změní velikost šířku sloupce pouze na základě hodnot v řádcích, které jsou aktuálně zobrazeny. Díky tomu se můžete vyhnout neefektivnost při práci s velkým počtem řádků, i když se v takovém případě můžete chtít použít nastavení velikosti metody, jako <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> upravit velikost v době podle vašeho výběru.  
  
 Další informace o automatickou změnu velikosti najdete v tématu [možnosti nastavení velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 Následující příklad kódu ukazuje možnosti dostupné pro automatickou změnu velikosti.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
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
