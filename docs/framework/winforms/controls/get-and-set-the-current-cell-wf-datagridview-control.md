---
title: Získání a nastavení aktuální buňky v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745659"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ea08e-102">Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ea08e-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ea08e-103">Interakce se <xref:System.Windows.Forms.DataGridView> často vyžaduje, abyste programově zjistili, která buňka je aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="ea08e-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="ea08e-104">Je také možné, že budete muset změnit aktuální buňku.</span><span class="sxs-lookup"><span data-stu-id="ea08e-104">You may also need to change the current cell.</span></span> <span data-ttu-id="ea08e-105">Tyto úlohy můžete provádět s vlastností <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea08e-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea08e-106">Aktuální buňku nelze nastavit v řádku nebo sloupci s vlastností <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> nastavenou na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="ea08e-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="ea08e-107">V závislosti na režimu výběru ovládacího prvku <xref:System.Windows.Forms.DataGridView> může změna aktuální buňky změnit výběr.</span><span class="sxs-lookup"><span data-stu-id="ea08e-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="ea08e-108">Další informace naleznete v tématu [režimy výběru v ovládacím prvku DataGridView model Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ea08e-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="ea08e-109">Získání aktuální buňky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="ea08e-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="ea08e-110">Použijte vlastnost <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="ea08e-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="ea08e-111">Chcete-li nastavit aktuální buňku programově</span><span class="sxs-lookup"><span data-stu-id="ea08e-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="ea08e-112">Nastavte vlastnost <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="ea08e-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ea08e-113">V následujícím příkladu kódu je aktuální buňka nastavena na řádek 0, sloupec 1.</span><span class="sxs-lookup"><span data-stu-id="ea08e-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea08e-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ea08e-114">Compiling the Code</span></span>  
 <span data-ttu-id="ea08e-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ea08e-115">This example requires:</span></span>  
  
- <span data-ttu-id="ea08e-116"><xref:System.Windows.Forms.Button> ovládací prvky s názvem `getCurrentCellButton` a `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="ea08e-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="ea08e-117">V jazyce C#Visual je nutné připojit události <xref:System.Windows.Forms.Control.Click> pro každé tlačítko k přidružené obslužné rutině události v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ea08e-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="ea08e-118"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="ea08e-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="ea08e-119">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="ea08e-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea08e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea08e-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ea08e-121">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ea08e-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="ea08e-122">Režimy výběru v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ea08e-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
