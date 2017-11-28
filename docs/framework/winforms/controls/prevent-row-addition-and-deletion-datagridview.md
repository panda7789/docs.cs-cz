---
title: "Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView"
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
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e90e36ef8a74caf58f6454027971f0711c406d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView
Někdy budete chtít zabránit uživatelům ve zadáním nové řádky dat nebo odstranění existující řádků ve vaší <xref:System.Windows.Forms.DataGridView> ovládacího prvku. <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> Vlastnost určuje, zda je k dispozici v dolní části ovládacího prvku řádek pro nové záznamy, při <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> vlastnost určuje, zda lze odebrat řádky. Následující příklad kódu používá tyto vlastnosti a také nastaví <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> vlastnost aby ovládacího prvku zcela jen pro čtení.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [postupy: zabránění přidávání řádků a mazání v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
