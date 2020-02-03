---
title: Přizpůsobení vzhledu řádků v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 099b2104e7a4887aa846c4d65273db2dd4f60559
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744037"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView
Můžete ovládat vzhled <xref:System.Windows.Forms.DataGridView> řádků tím, že zpracujete jednu nebo obě události <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> a <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>. Tyto události jsou navržené tak, aby bylo možné malovat pouze ty, které chcete, a současně umožnit ovládacímu prvku <xref:System.Windows.Forms.DataGridView> malovat zbytek. Například pokud chcete malovat vlastní pozadí, můžete zpracovat událost <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> a nechat jednotlivé buňky malovat vlastní obsah v popředí. Alternativně můžete nechat buňky malovat sami a přidat vlastní obsah v popředí obslužné rutiny pro událost <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>. V obslužné rutině události <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> můžete také zakázat Malování buněk a malovat všechno sami.  
  
 Následující příklad kódu implementuje obslužné rutiny pro obě události, aby bylo možné poskytnout pozadí výběru barevného přechodu a určitý vlastní obsah v popředí, který pokrývá více sloupců.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)
- [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)
