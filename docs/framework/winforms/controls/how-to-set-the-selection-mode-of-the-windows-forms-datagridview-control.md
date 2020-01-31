---
title: Nastavení režimu výběru ovládacího prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: da866aac3ac5b08a06ec71744aadb4260bd0cfc4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743500"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="cc06a-102">Postupy: Nastavení režimu výběru ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="cc06a-102">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="cc06a-103">Následující příklad kódu ukazuje, jak nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládací prvek tak, aby se při kliknutí kamkoli v rámci řádku automaticky vybral celý řádek, a to tak, aby bylo možné vybrat pouze jeden řádek najednou.</span><span class="sxs-lookup"><span data-stu-id="cc06a-103">The following code example demonstrates how to configure a <xref:System.Windows.Forms.DataGridView> control so that clicking anywhere within a row automatically selects the entire row, and so that only one row at a time can be selected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc06a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc06a-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc06a-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cc06a-105">Compiling the Code</span></span>  
 <span data-ttu-id="cc06a-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cc06a-106">This example requires:</span></span>  
  
- <span data-ttu-id="cc06a-107"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="cc06a-107">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="cc06a-108">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc06a-108">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc06a-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc06a-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [<span data-ttu-id="cc06a-110">Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="cc06a-110">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="cc06a-111">Režimy výběru v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="cc06a-111">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
