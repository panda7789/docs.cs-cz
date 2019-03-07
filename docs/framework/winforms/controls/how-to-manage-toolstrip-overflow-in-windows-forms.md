---
title: 'Postupy: Správa přetečení ToolStrip ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 24304b64b4214f9c15006e4f6cf35fac0bd0ced1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480075"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Postupy: Správa přetečení ToolStrip ve Windows Forms

Při všech položek na <xref:System.Windows.Forms.ToolStrip> ovládací prvek se nevejdou do přiděleného prostoru, můžete povolit funkci přetečení na <xref:System.Windows.Forms.ToolStrip> a zjistit, konkrétní chování přetečení <xref:System.Windows.Forms.ToolStripItem>s.

Po přidání <xref:System.Windows.Forms.ToolStripItem>, které vyžadují více místa, než je přidělený <xref:System.Windows.Forms.ToolStrip> uvedeny formulářovou aktuální velikost, <xref:System.Windows.Forms.ToolStripOverflowButton> automaticky zobrazí na <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ToolStripOverflowButton> Se zobrazí, a položek s povolenou přetečení přesunou do nabídky přetečení rozevíracího seznamu. Díky tomu můžete k přizpůsobení a stanovení priorit jak vaše <xref:System.Windows.Forms.ToolStrip> položky správně nastavit pro různé velikosti. Můžete také změnit vzhled vašich položkách při spadají do přetečení s použitím <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> událostí. Pokud více zvětšit formuláře v době návrhu nebo běhu <xref:System.Windows.Forms.ToolStripItem>s mohou být zobrazeny v hlavním <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripOverflowButton> můžou i zmizet, dokud snížit velikost formuláře.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>Povolit přetečení v ovládacím prvku ToolStrip

- Ujistěte se, <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> vlastnost není nastavena na `false` pro <xref:System.Windows.Forms.ToolStrip>. Výchozí hodnota je `True`.

     Když <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> je `True` (výchozí), <xref:System.Windows.Forms.ToolStripItem> je odeslána do přetečení rozevírací nabídky při obsah <xref:System.Windows.Forms.ToolStripItem> překračuje šířka vodorovného <xref:System.Windows.Forms.ToolStrip> nebo výšku a jsou odděleny svislou <xref:System.Windows.Forms.ToolStrip>.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Chcete-li určit chování přetečení konkrétní ovládací prvek ToolStripItem

- Nastavte <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> vlastnost <xref:System.Windows.Forms.ToolStripItem> na požadovanou hodnotu. Možnosti jsou `Always`, `Never`, a `AsNeeded`. Výchozí hodnota je `AsNeeded`.

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
