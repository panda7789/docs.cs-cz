---
title: Zobrazení obrázků v buňkách ovládacího prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740287"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView
Obrázek nebo obrázek je jednou z hodnot, které lze zobrazit v řádku dat. Tyto grafiky mají často formu fotografie zaměstnance nebo loga společnosti.  
  
 Zahrnutí obrázků je jednoduché při zobrazení dat v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Ovládací prvek <xref:System.Windows.Forms.DataGridView> nativně zpracovává libovolný formát obrázku podporovaný <xref:System.Drawing.Image> třídou a také formát obrázku OLE používaný některými databázemi.  
  
 Pokud zdroj dat ovládacího prvku <xref:System.Windows.Forms.DataGridView> obsahuje sloupec obrázků, bude automaticky zobrazen pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView>.  
  
 Následující příklad kódu ukazuje, jak extrahovat ikonu z vloženého zdroje a převést ji na rastrový obrázek pro zobrazení v každé buňce sloupce obrázku. Další příklad, který nahradí hodnoty textové buňky odpovídajícími obrázky, naleznete v tématu [How to: Customizing Data Formatting in model Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Vložený prostředek ikony s názvem `tree.ico`.  
  
- Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>a <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
