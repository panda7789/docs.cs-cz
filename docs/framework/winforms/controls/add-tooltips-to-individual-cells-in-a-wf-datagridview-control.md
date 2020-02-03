---
title: Přidání popisů do jednotlivých buněk v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732178"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView
Ve výchozím nastavení se pro zobrazení jejich celého obsahu používají popisy tlačítek pro zobrazení hodnot <xref:System.Windows.Forms.DataGridView> buněk, které jsou příliš malé. Toto chování však můžete přepsat pro nastavení textových hodnot popisku pro jednotlivé buňky. To je užitečné, když chcete uživatelům zobrazit další informace o buňce nebo uživatelům poskytnout alternativní popis obsahu buňky. Například pokud máte řádek, který zobrazuje ikony stavu, možná budete chtít zadat vysvětlení textu pomocí popisů tlačítek.  
  
 Zobrazení popisků na úrovni buňky můžete také zakázat nastavením vlastnosti <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> na `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Přidání popisu k buňce  
  
- Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`, který obsahuje sloupec s názvem `Rating` pro zobrazení hodnot řetězce na jednom až čtyř symbol hvězdičky ("*"). Událost <xref:System.Windows.Forms.DataGridView.CellFormatting> ovládacího prvku musí být přidružena k metodě obslužné rutiny události zobrazené v příkladu.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Při vázání ovládacího prvku <xref:System.Windows.Forms.DataGridView> k externímu zdroji dat nebo poskytnutí vlastního zdroje dat implementací virtuálního režimu může dojít k problémům s výkonem. Aby se zabránilo snížení výkonu při práci s velkým množstvím dat, zpracujte <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> událost namísto nastavení vlastnosti <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> více buněk. Při zpracování této události, získání hodnoty vlastnosti <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> buňky vyvolá událost a vrátí hodnotu vlastnosti <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>, jak je uvedeno v obslužné rutině události.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView](programming-with-cells-rows-and-columns-in-the-datagrid.md)
