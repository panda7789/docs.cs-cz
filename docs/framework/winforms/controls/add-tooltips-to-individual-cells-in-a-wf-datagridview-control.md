---
title: 'Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: baa6f79f2e0d454412992d9c951734a3437a96cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517640"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView
Ve výchozím nastavení, popisy slouží k zobrazení hodnoty <xref:System.Windows.Forms.DataGridView> buňky, které jsou příliš malé a zobrazit jejich celý obsah. Toto chování můžete přepsat však můžete nastavit text popisku hodnoty jednotlivých buněk. To je užitečné, chcete-li zobrazit uživatelům další informace o buňku nebo můžete uživatelům poskytnout alternativní popis obsah buňky. Například pokud máte řádek, který zobrazuje ikony stavu, můžete zadat text vysvětlení použití popisů tlačítek.  
  
 Zobrazit popisky na úrovni buněk můžete také zakázat nastavením <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> vlastnost `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Chcete-li přidat popisek buňky  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , která obsahuje sloupec s názvem `Rating` pro zobrazení hodnoty řetězců jeden až čtyři hvězdičky ("*") symboly. <xref:System.Windows.Forms.DataGridView.CellFormatting> Události ovládacího prvku musí být přidružená k metodě obslužné rutiny události v příkladu.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> řízení k externímu zdroji dat nebo poskytnutí zdroje dat tak, že implementace virtuálního režimu, může dojít problémům s výkonem. Aby se zabránilo snížení výkonu při práci s velkými objemy dat, zpracovat <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> události spíše než nastavení <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> vlastnost více buněk. Při zpracování této události, získání vyšší hodnoty buňky <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> vlastnost vyvolá událost a vrátí hodnotu <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> vlastnost jako uvedené v události obslužné rutiny.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
