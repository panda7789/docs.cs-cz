---
title: "Postupy: Nastavení režimů třídění pro sloupce v ovládacím prvku Windows Forms DataGridView"
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
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a8571209ea0a80a64c1f30336c9a52b1bc79622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Nastavení režimů třídění pro sloupce v ovládacím prvku Windows Forms DataGridView
V <xref:System.Windows.Forms.DataGridView> řízení, textové pole sloupců použít automatické řazení ve výchozím nastavení, zatímco jiné typy sloupců nejsou automaticky seřazeny. Někdy budete chtít přepsat tyto výchozí hodnoty. Například můžete zobrazit obrázky místo textu, čísla nebo hodnoty výčtu buněk. Při bitové kopie nelze řadit, základní hodnoty, které představují lze seřadit.  
  
 V <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> hodnota vlastnosti sloupce určuje jeho řazení chování.  
  
 Následující postup ukazuje `Priority` sloupec z [postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Tento sloupec je sloupec bitové kopie a není ve výchozím nastavení řazení. Obsahuje hodnoty skutečné buněk, které jsou řetězce, ale tak může být seřazeny automaticky.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Chcete-li nastavit režim řazení pro sloupec  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , který obsahuje sloupec s názvem `Priority`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [Řazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
