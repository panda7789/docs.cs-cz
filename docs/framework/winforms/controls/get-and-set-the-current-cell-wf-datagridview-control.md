---
title: 'Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: f60acbfa73ef363d58c57e1c01bdce8cf3337e48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619668"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a96f9-102">Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a96f9-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a96f9-103">Interakce s <xref:System.Windows.Forms.DataGridView> často vyžaduje prostřednictvím kódu programu zjistit buňky, která je aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="a96f9-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="a96f9-104">Také budete muset změnit aktuální buňky.</span><span class="sxs-lookup"><span data-stu-id="a96f9-104">You may also need to change the current cell.</span></span> <span data-ttu-id="a96f9-105">Můžete provádět tyto úlohy se <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a96f9-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a96f9-106">Nelze nastavit aktuální buňky v řádku nebo sloupce, který má jeho <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="a96f9-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="a96f9-107">V závislosti na tom <xref:System.Windows.Forms.DataGridView> režimu výběru ovládacího prvku, změna aktuální buňky můžete změnit výběr.</span><span class="sxs-lookup"><span data-stu-id="a96f9-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="a96f9-108">Další informace najdete v tématu [režimy výběru v ovládacím prvku Windows Forms DataGridView](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a96f9-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="a96f9-109">Chcete-li získat aktuální buňky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="a96f9-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="a96f9-110">Použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a96f9-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="a96f9-111">K nastavení aktuální buňky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="a96f9-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="a96f9-112">Nastavte <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a96f9-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a96f9-113">V následujícím příkladu kódu aktuální buňky je nastavena na 0, sloupec 1 řádek.</span><span class="sxs-lookup"><span data-stu-id="a96f9-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a96f9-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a96f9-114">Compiling the Code</span></span>  
 <span data-ttu-id="a96f9-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a96f9-115">This example requires:</span></span>  
  
- <span data-ttu-id="a96f9-116"><xref:System.Windows.Forms.Button> ovládací prvky s názvem `getCurrentCellButton` a `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="a96f9-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="a96f9-117">Ve Vizuálu C#, je nutné připojit <xref:System.Windows.Forms.Control.Click> události pro každé tlačítko obslužné rutiny související události v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="a96f9-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="a96f9-118">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a96f9-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="a96f9-119">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="a96f9-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96f9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a96f9-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a96f9-121">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a96f9-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="a96f9-122">Režimy výběru v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a96f9-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
