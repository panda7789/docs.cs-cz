---
title: Získání a nastavení aktuální buňky v ovládacím prvku DataGridView
description: Naučte se programově zjistit, která buňka je aktuálně aktivní, získáním a nastavením aktuální buňky v ovládacím prvku DataGridView model Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622208"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5956a-103">Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5956a-103">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5956a-104">Interakce s <xref:System.Windows.Forms.DataGridView> často vyžaduje, abyste programově zjistili, která buňka je aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="5956a-104">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="5956a-105">Je také možné, že budete muset změnit aktuální buňku.</span><span class="sxs-lookup"><span data-stu-id="5956a-105">You may also need to change the current cell.</span></span> <span data-ttu-id="5956a-106">Tyto úlohy můžete provádět s <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="5956a-106">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5956a-107">Nemůžete nastavit aktuální buňku v řádku nebo sloupci, kde má <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> vlastnost nastavenou na `false` .</span><span class="sxs-lookup"><span data-stu-id="5956a-107">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="5956a-108">V závislosti na <xref:System.Windows.Forms.DataGridView> režimu výběru ovládacího prvku může změna aktuální buňky změnit výběr.</span><span class="sxs-lookup"><span data-stu-id="5956a-108">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="5956a-109">Další informace naleznete v tématu [režimy výběru v ovládacím prvku DataGridView model Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5956a-109">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="5956a-110">Získání aktuální buňky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5956a-110">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="5956a-111">Použijte <xref:System.Windows.Forms.DataGridView> vlastnost ovládacího prvku <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .</span><span class="sxs-lookup"><span data-stu-id="5956a-111">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="5956a-112">Chcete-li nastavit aktuální buňku programově</span><span class="sxs-lookup"><span data-stu-id="5956a-112">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="5956a-113">Nastavte <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5956a-113">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5956a-114">V následujícím příkladu kódu je aktuální buňka nastavena na řádek 0, sloupec 1.</span><span class="sxs-lookup"><span data-stu-id="5956a-114">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5956a-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5956a-115">Compiling the Code</span></span>  
 <span data-ttu-id="5956a-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5956a-116">This example requires:</span></span>  
  
- <span data-ttu-id="5956a-117"><xref:System.Windows.Forms.Button>ovládací prvky s názvem `getCurrentCellButton` a `setCurrentCellButton` .</span><span class="sxs-lookup"><span data-stu-id="5956a-117"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="5956a-118">V jazyce Visual C# je nutné připojit <xref:System.Windows.Forms.Control.Click> události pro každé tlačítko k přidružené obslužné rutině události v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5956a-118">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="5956a-119"><xref:System.Windows.Forms.DataGridView>Ovládací prvek s názvem `dataGridView1` .</span><span class="sxs-lookup"><span data-stu-id="5956a-119">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="5956a-120">Odkazy na <xref:System?displayProperty=nameWithType> sestavení a <xref:System.Windows.Forms?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5956a-120">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5956a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5956a-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5956a-122">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5956a-122">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="5956a-123">Režimy výběru v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5956a-123">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
