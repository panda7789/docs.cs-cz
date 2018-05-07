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
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Ladění výkonu v ovládacím prvku Windows Forms DataGridView
Při práci s velkými objemy dat, `DataGridView` ovládací prvek může využívat velké množství paměti v režijní náklady, pokud pečlivě použít. U klientů s omezenou pamětí se můžete vyhnout některé Tato dodatečná režie vyhnout funkce, které mají vysokou paměti náklady. Můžete také spravovat některé nebo všechny údržby dat a načtení úloh sami pomocí virtuální režim. Chcete-li přizpůsobit využití paměti pro váš scénář.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití `DataGridView` ovládacího prvku tak, aby při práci s velkými objemy dat zabraňuje využití a výkonu postihy nepotřebné paměti.  
  
 [Virtuální režim v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak používat virtuální režim k doplnění nebo nahrazení standardní mechanismus datové vazby.  
  
 [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Popisuje, jak k implementaci obslužné rutiny pro několik událostí Virtuální režim. Také ukazuje, jak implementovat nízkoúrovňové vrácení a potvrzení pro uživatelské úpravy.  
  
 [Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Popisuje, jak načíst data na vyžádání, což je užitečné, když máte další data k zobrazení než paměti k dispozici klienta můžete uložit.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
