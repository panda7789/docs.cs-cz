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
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Ladění výkonu v ovládacím prvku Windows Forms DataGridView
Při práci s velkým objemem dat může ovládací prvek `DataGridView` spotřebovat velké množství paměti v režii, pokud ho nepoužijete opatrně. Na klientech s omezeným množstvím paměti se můžete vyhnout některé z těchto režijních nákladů a zabránit tak funkcím, které mají vysoké náklady na paměť. Můžete také spravovat některé nebo všechny úlohy údržby a načítání dat sami pomocí virtuálního režimu, aby bylo možné přizpůsobit využití paměti pro váš scénář.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Popisuje způsob použití ovládacího prvku `DataGridView` způsobem, který brání zbytečnému využití paměti a postihům výkonu při práci s velkým objemem dat.  
  
 [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak použít virtuální režim k doplnění nebo nahrazení standardního mechanismu vazby dat.  
  
 [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-wf-datagridview-control.md)  
 Popisuje, jak implementovat obslužné rutiny pro několik událostí s virtuálním režimem. Také ukazuje, jak implementovat vrácení zpět a zápisy na úrovni řádků pro úpravy uživatelů.  
  
 [Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Popisuje, jak načíst data na vyžádání, což je užitečné v případě, že máte větší množství dat, než kolik jich může být dostupných pro klientské úložiště.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
