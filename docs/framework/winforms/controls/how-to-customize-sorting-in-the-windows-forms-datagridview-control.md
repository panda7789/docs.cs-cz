---
title: 'Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f945cd82deeec5ff281ff067cf6be93d00c6810
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení poskytuje automatické řazení, ale podle svých potřeb, možná budete muset přizpůsobit operace řazení. Například můžete programový řazení vytvořit alternativní uživatelské rozhraní (UI). Alternativně může zpracovat <xref:System.Windows.Forms.DataGridView.SortCompare> události nebo volání `Sort(IComparer)` přetížení z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda větší flexibilitu řazení, jako je například řazení více sloupců.  
  
 Následující příklady kódu ukazují tyto tři metody vlastní řazení. Další informace najdete v tématu [režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Programová řazení  
 Následující příklad kódu ukazuje programový řazení pomocí <xref:System.Windows.Forms.DataGridView.SortOrder%2A> a <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> vlastnosti k určení směru řazení a <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> vlastnost ručně nastavit glyfy řazení. `Sort(DataGridViewColumn,ListSortDirection)` Přetížení z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda se používá k řazení dat jenom do jednoho sloupce.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Vlastní řazení pomocí SortCompare události  
 Následující příklad kódu ukazuje vlastní řazení pomocí <xref:System.Windows.Forms.DataGridView.SortCompare> obslužné rutiny události. Vybraný <xref:System.Windows.Forms.DataGridViewColumn> řadí a, pokud existují duplicitní hodnoty ve sloupci, sloupec ID slouží k určení konečného pořadí.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Vlastní řazení pomocí IComparer rozhraní  
 Následující příklad kódu ukazuje vlastní řazení pomocí `Sort(IComparer)` přetížení z <xref:System.Windows.Forms.DataGridView.Sort%2A> metodu, která přebírá implementaci <xref:System.Collections.IComparer> rozhraní provést řazení podle více sloupců.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tyto příklady vyžadují:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření těchto příkladech z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Řazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
