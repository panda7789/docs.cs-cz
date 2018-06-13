---
title: Ladění výkonu v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 97bf6f36ce029f879c3524fa92df08a483c2cb77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536979"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5ab78-102">Ladění výkonu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ab78-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5ab78-103">Při práci s velkými objemy dat, `DataGridView` ovládací prvek může využívat velké množství paměti v režijní náklady, pokud pečlivě použít.</span><span class="sxs-lookup"><span data-stu-id="5ab78-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="5ab78-104">U klientů s omezenou pamětí se můžete vyhnout některé Tato dodatečná režie vyhnout funkce, které mají vysokou paměti náklady.</span><span class="sxs-lookup"><span data-stu-id="5ab78-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="5ab78-105">Můžete také spravovat některé nebo všechny údržby dat a načtení úloh sami pomocí virtuální režim. Chcete-li přizpůsobit využití paměti pro váš scénář.</span><span class="sxs-lookup"><span data-stu-id="5ab78-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ab78-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5ab78-106">In This Section</span></span>  
 [<span data-ttu-id="5ab78-107">Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ab78-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5ab78-108">Popisuje způsob použití `DataGridView` ovládacího prvku tak, aby při práci s velkými objemy dat zabraňuje využití a výkonu postihy nepotřebné paměti.</span><span class="sxs-lookup"><span data-stu-id="5ab78-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="5ab78-109">Virtuální režim v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ab78-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5ab78-110">Popisuje, jak používat virtuální režim k doplnění nebo nahrazení standardní mechanismus datové vazby.</span><span class="sxs-lookup"><span data-stu-id="5ab78-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="5ab78-111">Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ab78-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="5ab78-112">Popisuje, jak k implementaci obslužné rutiny pro několik událostí Virtuální režim.</span><span class="sxs-lookup"><span data-stu-id="5ab78-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="5ab78-113">Také ukazuje, jak implementovat nízkoúrovňové vrácení a potvrzení pro uživatelské úpravy.</span><span class="sxs-lookup"><span data-stu-id="5ab78-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="5ab78-114">Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ab78-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="5ab78-115">Popisuje, jak načíst data na vyžádání, což je užitečné, když máte další data k zobrazení než paměti k dispozici klienta můžete uložit.</span><span class="sxs-lookup"><span data-stu-id="5ab78-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5ab78-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5ab78-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="5ab78-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5ab78-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="5ab78-118">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5ab78-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab78-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ab78-119">See Also</span></span>  
 [<span data-ttu-id="5ab78-120">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ab78-120">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="5ab78-121">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5ab78-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
