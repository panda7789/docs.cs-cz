---
title: "Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView"
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
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a533f4cbf5000489e774ba8661c3ab03cea4948a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Postupy: Přidání ToolTips do jednotlivých buněk v ovládacím prvku Windows Forms DataGridView
Ve výchozím nastavení, popisy tlačítek slouží k zobrazení hodnot z <xref:System.Windows.Forms.DataGridView> buněk, které jsou příliš malé a zobrazit jejich celý obsah. Toto chování můžete přepsat však můžete nastavit text popisu tlačítka hodnoty jednotlivých buněk. To je užitečné k zobrazení na uživatele Další informace o buňku nebo poskytovat uživatelům alternativní popis obsah buňky. Například pokud máte řádek, který zobrazí stav ikony, můžete zadat text vysvětlení použití popisů tlačítek.  
  
 Můžete také zakázat zobrazení popisů tlačítek úrovni buněk nastavením <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> vlastnost `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Chcete-li přidat popis tlačítka do buňky  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , který obsahuje sloupec s názvem `Rating` pro zobrazení řetězcové hodnoty jednoho prostřednictvím čtyři hvězdičky ("*") symboly. <xref:System.Windows.Forms.DataGridView.CellFormatting> Události ovládacího prvku musí být přidruženy k obslužná rutina události v příkladu.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> řídit k externímu zdroji dat nebo poskytnout vlastní zdroj dat tím, že implementace virtuálního režimu, může dojít problémům s výkonem. Aby se zabránilo snížení výkonu při práci s velkými objemy dat, zpracování <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> událostí spíše než nastavení <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> vlastnost více buněk. Při zpracování této události, získávání hodnotu buňky <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> vlastnost vyvolá událost a vrátí hodnotu <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> vlastnost jako uvedené v události obslužné rutiny.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
