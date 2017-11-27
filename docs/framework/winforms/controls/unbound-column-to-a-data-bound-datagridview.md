---
title: "Postupy: Přidání nepřipojeného sloupce do daty připojeného ovládacího prvku Windows Forms DataGridView"
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
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cd6a1494a98d912469f7e45c7751a0a9741ff17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Postupy: Přidání nepřipojeného sloupce do daty připojeného ovládacího prvku Windows Forms DataGridView
Data můžete zobrazit v <xref:System.Windows.Forms.DataGridView> ovládací prvek bude obvykle pocházet ze zdroje dat určitého druhu, ale můžete chtít zobrazit sloupce dat, které nepochází ze zdroje dat. Tento druh sloupec se nazývá nepřipojeného sloupce. Nevázaných sloupců mohou mít mnoho forem. Často se používají k poskytování přístupu k podrobnosti o data v řádku.  
  
 Následující příklad kódu ukazuje, jak vytvořit nepřipojeného sloupce z **podrobnosti** tlačítka zobrazíte podřízené tabulky související s konkrétního řádku v nadřazené tabulce při implementaci scénáři a podrobností. Reagovat na kliknutí na tlačítko, implementovat <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> obslužné rutiny události, které zobrazí formulář obsahující podřízenou tabulku.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [postupy: Přidání a odebrání sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
