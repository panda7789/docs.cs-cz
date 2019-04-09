---
title: 'Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 90aaff419ecc2c890a8b3802f3aaf12092febb73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082994"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView
Obrázek nebo obrázek je jedna z hodnot zobrazených dat za sebou. Často tyto grafiky podobu zaměstnance fotografie nebo logo společnosti.  
  
 Zahrnutí obrázky je jednoduché, pokud zobrazení dat v rámci <xref:System.Windows.Forms.DataGridView> ovládacího prvku. <xref:System.Windows.Forms.DataGridView> Nativně zpracovává všechny formát obrázku, který podporuje ovládací prvek <xref:System.Drawing.Image> třídy, jakož i OLE obrázek formát používaný některé databáze.  
  
 Pokud <xref:System.Windows.Forms.DataGridView> zdroj dat ovládacího prvku má sloupec bitových kopií, budou automaticky zobrazeny <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Následující příklad kódu ukazuje, jak extrahovat ikonu ze vloženého prostředku a převod na rastrový obrázek pro zobrazení v každé buňce sloupce obrázku. Další příklad, který nahradí hodnoty textovou buňky odpovídající Image, najdete v části [jak: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Na ikonu vloženého prostředek s názvem `tree.ico`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Drawing?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
