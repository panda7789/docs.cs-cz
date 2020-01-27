---
title: Určení výchozích hodnot pro nové řádky v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742931"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView
Když aplikace vyplní výchozí hodnoty pro nově přidané řádky, můžete zadat data lépe. Pomocí třídy <xref:System.Windows.Forms.DataGridView> můžete do události <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zadat výchozí hodnoty. Tato událost se vyvolá, když uživatel zadá řádek pro nové záznamy. Když kód zpracovává tuto událost, můžete požadované buňky naplnit hodnotami podle vašeho výběru.  
  
 Následující příklad kódu ukazuje, jak zadat výchozí hodnoty pro nové řádky pomocí události <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Funkce `NewCustomerId` pro generování jedinečných `CustomerID`ch hodnot.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
