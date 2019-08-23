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
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966493"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView
Ovládací prvek používá šablonu řádku jako základ pro všechny řádky, které přidá do ovládacího prvku buď prostřednictvím vazby dat, nebo při <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> volání metody bez určení stávajícího řádku, který má být použit. <xref:System.Windows.Forms.DataGridView>  
  
 Šablona řádku nabízí větší kontrolu nad tím, jak vzhled a chování řádků, než <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> poskytuje vlastnost. Pomocí šablony řádku můžete nastavit jakékoli <xref:System.Windows.Forms.DataGridViewRow> vlastnosti, včetně. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>  
  
 Existují situace, kdy je nutné použít šablonu řádku k dosažení konkrétního efektu. Například informace o výšce řádku nelze uložit do <xref:System.Windows.Forms.DataGridViewCellStyle>, takže je nutné použít šablonu řádku, chcete-li změnit výchozí výšku použitou ve všech řádcích. Šablona řádku je užitečná také v případě, že vytvoříte vlastní třídy odvozené z <xref:System.Windows.Forms.DataGridViewRow> a chcete použít vlastní typ, když jsou do ovládacího prvku přidány nové řádky.  
  
> [!NOTE]
> Šablona řádku se používá pouze v případě, že jsou přidány řádky. Existující řádky nemůžete změnit změnou šablony řádku.  
  
### <a name="to-use-the-row-template"></a>Použití šablony řádku  
  
- Nastavte vlastnosti objektu načteného z <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> vlastnosti.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView>  
  
- Odkazy na <xref:System?displayProperty=nameWithType>sestavení, <xref:System.Drawing?displayProperty=nameWithType>a. <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
