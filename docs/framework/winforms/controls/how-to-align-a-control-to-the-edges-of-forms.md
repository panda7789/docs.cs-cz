---
title: 'Postupy: Zarovnání ovládacího prvku k okrajům formulářů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: ba5e9fc92f2805206f6c3796689898f3ff845896
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610406"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Postupy: Zarovnání ovládacího prvku k okrajům formulářů
Můžete provést ovládacího prvku zarovná na hraničních zařízeních formulářů tím, že nastavíte <xref:System.Windows.Forms.Control.Dock%2A> vlastnost. Tato vlastnost určuje, kde se nachází váš ovládací prvek ve formuláři. <xref:System.Windows.Forms.Control.Dock%2A> Vlastnost lze nastavit následující hodnoty:  
  
|Nastavení|Vliv na váš ovládací prvek|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Ukotví do dolní části formuláře.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Vyplní veškerý zbývající prostor ve formuláři.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Ukotví na levou stranu formuláře.|  
|<xref:System.Windows.Forms.DockStyle.None>|Fakturuje se u není dock kdekoli a zobrazí se v umístění určeném jeho <xref:System.Windows.Forms.Control.Location%2A> vlastnost.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Ukotví na pravou stranu formuláře.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Ukotví do horní části formuláře.|  
  
 Není poskytována podpora návrhu pro tuto funkci v sadě Visual Studio.  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a>Chcete-li nastavit vlastnosti Dock ovládacího prvku za běhu  
  
1.  Nastavte <xref:System.Windows.Forms.Control.Dock%2A> k odpovídající hodnotě v kódu.  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
