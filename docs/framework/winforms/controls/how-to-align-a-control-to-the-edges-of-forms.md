---
title: 'Postupy: Zarovnávání ovládacího prvku k okrajům formulářů'
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
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015947"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Postupy: Zarovnávání ovládacího prvku k okrajům formulářů

Můžete nastavit, aby se ovládací prvek na okraji formulářů narovnal nastavením <xref:System.Windows.Forms.Control.Dock%2A> vlastnosti. Tato vlastnost určuje, kde se ovládací prvek nachází ve formuláři. <xref:System.Windows.Forms.Control.Dock%2A> Vlastnost může být nastavena na následující hodnoty:

|Nastavení|Vliv na ovládací prvek|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Docker do dolní části formuláře.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Vyplní všechny zbývající místo ve formuláři.|
|<xref:System.Windows.Forms.DockStyle.Left>|Dockers na levou stranu formuláře.|
|<xref:System.Windows.Forms.DockStyle.None>|Není ukotven kdekoli a zobrazí se v umístění určeném <xref:System.Windows.Forms.Control.Location%2A> vlastností.|
|<xref:System.Windows.Forms.DockStyle.Right>|Dockers na pravou stranu formuláře.|
|<xref:System.Windows.Forms.DockStyle.Top>|Docker do horní části formuláře.|

Pro tuto funkci v aplikaci Visual Studio je podporována podpora v době návrhu.

## <a name="set-the-dock-property-for-your-control-at-run-time"></a>Nastavit vlastnost Dock pro váš ovládací prvek v době běhu

<xref:System.Windows.Forms.Control.Dock%2A> Nastavte vlastnost na odpovídající hodnotu v kódu.

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
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Postupy: Podřízené ovládací prvky ukotvení a ukotvení v ovládacím prvku FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Postupy: Podřízené ovládací prvky ukotvení a ukotvení v ovládacím prvku TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Přehled vlastnosti AutoSize](autosize-property-overview.md)
