---
title: Ladění výkonu v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 79f74db4ebd095156207a6218f59c0e9ae423085
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076585"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="51019-102">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="51019-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="51019-103">Při práci s velkými objemy dat, `DataGridView` ovládací prvek může spotřebovat velké množství paměti zátěž, pokud nepoužíváte pečlivě.</span><span class="sxs-lookup"><span data-stu-id="51019-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="51019-104">U klientů s omezenou pamětí můžete zabránit této režie vyloučením funkcí, které mají velkého množství paměti nákladů.</span><span class="sxs-lookup"><span data-stu-id="51019-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="51019-105">Můžete také spravovat některé nebo všechny údržby dat a načítání úloh sami pomocí virtuální režim dokážeme využití paměti pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="51019-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51019-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="51019-106">In This Section</span></span>  
 [<span data-ttu-id="51019-107">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="51019-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="51019-108">Popisuje způsob použití `DataGridView` ovládacího prvku tak, aby při práci s velkými objemy dat se vyhnete zbytečného snížení využití a výkonu.</span><span class="sxs-lookup"><span data-stu-id="51019-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="51019-109">Virtuální režim v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="51019-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="51019-110">Popisuje způsob použití doplňují nebo nahradit standardní mechanismus datová vazba virtuálního režimu.</span><span class="sxs-lookup"><span data-stu-id="51019-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="51019-111">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="51019-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="51019-112">Popisuje, jak implementovat obslužné rutiny pro několik událostí virtuálním režimu.</span><span class="sxs-lookup"><span data-stu-id="51019-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="51019-113">Také ukazuje, jak implementovat vrácení zpět na úrovni řádků a potvrzení pro uživatelské úpravy.</span><span class="sxs-lookup"><span data-stu-id="51019-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="51019-114">Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="51019-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="51019-115">Popisuje, jak načíst data na vyžádání, což je užitečné, pokud máte další data k zobrazení, než může ukládat paměti k dispozici klienta.</span><span class="sxs-lookup"><span data-stu-id="51019-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="51019-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="51019-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="51019-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="51019-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="51019-118">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="51019-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51019-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51019-119">See also</span></span>

- [<span data-ttu-id="51019-120">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="51019-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="51019-121">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="51019-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
