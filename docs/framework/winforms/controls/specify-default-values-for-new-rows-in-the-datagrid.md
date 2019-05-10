---
title: 'Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 879c035366c4686ceff3250a63c6ae8d8d3cfec4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651949"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView
Zadávání dat můžete provést pohodlnější, když aplikace vyplní ve výchozí hodnoty pro nově přidané řádky. S <xref:System.Windows.Forms.DataGridView> třídy, můžete přejít k vyplnění ve výchozí hodnoty <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí. Tato událost je aktivována, když uživatel zadá řádek pro nové záznamy. Když váš kód zpracovává tuto událost, která můžete naplnit požadované buňky s hodnotami, které si vyberete.  
  
 Následující příklad kódu ukazuje, jak určit výchozí hodnoty pro nové řádky pomocí <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- A `NewCustomerId` funkce generuje jedinečný `CustomerID` hodnoty.  
  
- Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
