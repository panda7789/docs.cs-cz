---
title: "Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView"
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
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56c8558f34c895567c3eebfbb5a89612c4b56224
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView
Obrázek nebo grafiku je jedna z hodnot, které můžete zobrazit v řádku dat. Tato grafika často, mít formu zaměstnance fotografie nebo logo společnosti.  
  
 Zařadit obrázky je jednoduchá, při zobrazení dat v rámci <xref:System.Windows.Forms.DataGridView> ovládacího prvku. <xref:System.Windows.Forms.DataGridView> Nativně zpracovává všechny formát obrázku podporuje ovládací prvek <xref:System.Drawing.Image> třídy a také OLE obrázek formát používaný některé databáze.  
  
 Pokud <xref:System.Windows.Forms.DataGridView> ovládacího prvku zdroj dat má sloupec bitových kopií, zobrazí se automaticky pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek.  
  
 Následující příklad kódu ukazuje, jak k extrahování ikony ze vloženého prostředku a ho převést na rastrový obrázek pro zobrazení v každé buňce sloupce obrázku. Další příklad, který nahrazuje hodnoty textovou buněk s odpovídající obrázky, naleznete v části [postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Na ikonu vloženého prostředek s názvem `tree.ico`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Drawing?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
