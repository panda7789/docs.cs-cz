---
title: Zabránit přidávání a odstraňování řádků v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728719"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView
Někdy budete chtít uživatelům zabránit v zadávání nových řádků dat nebo odstranění existujících řádků v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> označuje, zda je řádek pro nové záznamy přítomen v dolní části ovládacího prvku, zatímco vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> označuje, zda lze odebrat řádky. Následující příklad kódu používá tyto vlastnosti a také nastavuje vlastnost <xref:System.Windows.Forms.DataGridView.ReadOnly%2A>, aby byl ovládací prvek zcela určen jen pro čtení.  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje. Viz také [Postupy: zabránění přidávání a odstraňování řádků v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
