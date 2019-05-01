---
title: Ladění výkonu v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 79f74db4ebd095156207a6218f59c0e9ae423085
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012643"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Ladění výkonu v ovládacím prvku Windows Forms DataGridView
Při práci s velkými objemy dat, `DataGridView` ovládací prvek může spotřebovat velké množství paměti zátěž, pokud nepoužíváte pečlivě. U klientů s omezenou pamětí můžete zabránit této režie vyloučením funkcí, které mají velkého množství paměti nákladů. Můžete také spravovat některé nebo všechny údržby dat a načítání úloh sami pomocí virtuální režim dokážeme využití paměti pro váš scénář.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití `DataGridView` ovládacího prvku tak, aby při práci s velkými objemy dat se vyhnete zbytečného snížení využití a výkonu.  
  
 [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití doplňují nebo nahradit standardní mechanismus datová vazba virtuálního režimu.  
  
 [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-wf-datagridview-control.md)  
 Popisuje, jak implementovat obslužné rutiny pro několik událostí virtuálním režimu. Také ukazuje, jak implementovat vrácení zpět na úrovni řádků a potvrzení pro uživatelské úpravy.  
  
 [Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Popisuje, jak načíst data na vyžádání, což je užitečné, pokud máte další data k zobrazení, než může ukládat paměti k dispozici klienta.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
