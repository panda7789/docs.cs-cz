---
title: 'Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 2bde9b3f6934833804866e29c18f3636c65ba069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení používá šablony řádku jako základ pro všechny řádky, které přidá do ovládacího prvku pomocí vazby dat nebo při volání <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metoda bez zadání používat stávající řádek.  
  
 Šablony řádku vám dává větší kontrolu nad vzhled a chování řádků, než <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> vlastnost poskytuje. Pomocí šablony řádku, můžete nastavit některé <xref:System.Windows.Forms.DataGridViewRow> vlastnosti, včetně <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Existují některé situace, kdy je nutné použít šablony řádku k dosažení konkrétní vliv. Například informace výšky řádku nelze uložit do <xref:System.Windows.Forms.DataGridViewCellStyle>, takže je nutné použít šablony řádku Chcete-li změnit výchozí výšku používané všechny řádky. Šablony řádku je užitečné také při vytváření vlastní třídy odvozené od třídy <xref:System.Windows.Forms.DataGridViewRow> a chcete, aby vaše vlastní typ použitý při přidávání řádků do ovládacího prvku.  
  
> [!NOTE]
>  Šablony řádku se používá pouze v případě, že jsou přidány řádky. Stávající řádky nelze změnit tak, že změníte šablony řádku.  
  
### <a name="to-use-the-row-template"></a>K použití šablony řádku  
  
-   Nastavit vlastnosti v objektu načtený ze <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
