---
title: "Ladění výkonu v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452c55d38a896ec96e0992a4b9826f08dc4caa0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Ladění výkonu v ovládacím prvku Windows Forms DataGridView
Při práci s velkými objemy dat, `DataGridView` ovládací prvek může využívat velké množství paměti v režijní náklady, pokud pečlivě použít. U klientů s omezenou pamětí se můžete vyhnout některé Tato dodatečná režie vyhnout funkce, které mají vysokou paměti náklady. Můžete také spravovat některé nebo všechny údržby dat a načtení úloh sami pomocí virtuální režim. Chcete-li přizpůsobit využití paměti pro váš scénář.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití `DataGridView` ovládacího prvku tak, aby při práci s velkými objemy dat zabraňuje využití a výkonu postihy nepotřebné paměti.  
  
 [Virtuální režim v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak používat virtuální režim k doplnění nebo nahrazení standardní mechanismus datové vazby.  
  
 [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 Popisuje, jak k implementaci obslužné rutiny pro několik událostí Virtuální režim. Také ukazuje, jak implementovat nízkoúrovňové vrácení a potvrzení pro uživatelské úpravy.  
  
 [Implementace virtuálního režimu s načítáním v ovládacím prvku Windows Forms DataGridView dat za běhu](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Popisuje, jak načíst data na vyžádání, což je užitečné, když máte další data k zobrazení než paměti k dispozici klienta můžete uložit.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
