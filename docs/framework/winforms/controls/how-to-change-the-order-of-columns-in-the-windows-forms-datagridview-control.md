---
title: Změna pořadí sloupců v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 2aef196e9544a81f42a563783ce6c357869aa247
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746543"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView
Když použijete <xref:System.Windows.Forms.DataGridView> k zobrazení dat ze zdroje dat, sloupce ve schématu zdroje dat se někdy nezobrazí v pořadí, v jakém je chcete zobrazit. Zobrazené pořadí sloupců můžete změnit pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> třídy <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 Následující příklad kódu přemístí některé sloupce automaticky generované při vazbě na tabulku Customers v ukázkové databázi Northwind. Další informace o vázání ovládacího prvku <xref:System.Windows.Forms.DataGridView> k tabulce databáze naleznete v tématu [How to: bind data to the model Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje.  Viz také [Postupy: Změna pořadí sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `customersDataGridView`, který je svázán s tabulkou s označenými názvy sloupců, jako je tabulka `Customers` v ukázkové databázi Northwind.  
  
- Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>a <xref:System.Xml?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
