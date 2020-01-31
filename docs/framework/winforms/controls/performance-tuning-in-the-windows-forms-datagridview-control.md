---
title: Ladění výkonu v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 77ad86c4cd606bcf074473c97371ec27bcc5605b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744271"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9543b-102">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9543b-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9543b-103">Při práci s velkým objemem dat může ovládací prvek `DataGridView` spotřebovat velké množství paměti v režii, pokud ho nepoužijete opatrně.</span><span class="sxs-lookup"><span data-stu-id="9543b-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="9543b-104">Na klientech s omezeným množstvím paměti se můžete vyhnout některé z těchto režijních nákladů a zabránit tak funkcím, které mají vysoké náklady na paměť.</span><span class="sxs-lookup"><span data-stu-id="9543b-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="9543b-105">Můžete také spravovat některé nebo všechny úlohy údržby a načítání dat sami pomocí virtuálního režimu, aby bylo možné přizpůsobit využití paměti pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="9543b-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9543b-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9543b-106">In This Section</span></span>  
 [<span data-ttu-id="9543b-107">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9543b-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9543b-108">Popisuje způsob použití ovládacího prvku `DataGridView` způsobem, který brání zbytečnému využití paměti a postihům výkonu při práci s velkým objemem dat.</span><span class="sxs-lookup"><span data-stu-id="9543b-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="9543b-109">Virtuální režim v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9543b-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9543b-110">Popisuje, jak použít virtuální režim k doplnění nebo nahrazení standardního mechanismu vazby dat.</span><span class="sxs-lookup"><span data-stu-id="9543b-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="9543b-111">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9543b-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="9543b-112">Popisuje, jak implementovat obslužné rutiny pro několik událostí s virtuálním režimem.</span><span class="sxs-lookup"><span data-stu-id="9543b-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="9543b-113">Také ukazuje, jak implementovat vrácení zpět a zápisy na úrovni řádků pro úpravy uživatelů.</span><span class="sxs-lookup"><span data-stu-id="9543b-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="9543b-114">Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9543b-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="9543b-115">Popisuje, jak načíst data na vyžádání, což je užitečné v případě, že máte větší množství dat, než kolik jich může být dostupných pro klientské úložiště.</span><span class="sxs-lookup"><span data-stu-id="9543b-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9543b-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9543b-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="9543b-117">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9543b-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="9543b-118">Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="9543b-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9543b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9543b-119">See also</span></span>

- [<span data-ttu-id="9543b-120">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="9543b-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="9543b-121">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9543b-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
