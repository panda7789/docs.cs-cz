---
title: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728380"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView
Ovládací prvek <xref:System.Windows.Forms.DataGridView> používá šablonu řádku jako základ pro všechny řádky, které přidávají do ovládacího prvku buď prostřednictvím vazby dat, nebo při volání metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> bez určení stávajícího řádku, který se má použít.  
  
 Šablona řádku nabízí větší kontrolu nad tím, jak vzhled a chování řádků, než poskytuje vlastnost <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>. Pomocí šablony řádku můžete nastavit libovolné vlastnosti <xref:System.Windows.Forms.DataGridViewRow>, včetně <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Existují situace, kdy je nutné použít šablonu řádku k dosažení konkrétního efektu. Například informace o výšce řádku nelze uložit do <xref:System.Windows.Forms.DataGridViewCellStyle>, takže je nutné použít šablonu řádku, chcete-li změnit výchozí výšku použitou ve všech řádcích. Šablona řádku je užitečná také v případě, že vytvoříte vlastní třídy odvozené od <xref:System.Windows.Forms.DataGridViewRow> a chcete použít vlastní typ, když jsou do ovládacího prvku přidány nové řádky.  
  
> [!NOTE]
> Šablona řádku se používá pouze v případě, že jsou přidány řádky. Existující řádky nemůžete změnit změnou šablony řádku.  
  
### <a name="to-use-the-row-template"></a>Použití šablony řádku  
  
- Nastavte vlastnosti objektu načteného z vlastnosti <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>a <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
