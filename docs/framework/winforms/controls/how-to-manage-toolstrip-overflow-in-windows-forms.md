---
title: 'Postupy: Správa přetečení ToolStrip'
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
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736142"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Postupy: Správa přetečení ToolStrip ve Windows Forms

Pokud se všechny položky v ovládacím prvku <xref:System.Windows.Forms.ToolStrip> nevejdou do přiděleného místa, můžete povolit funkci přetečení na <xref:System.Windows.Forms.ToolStrip> a určit chování přetečení u určitých <xref:System.Windows.Forms.ToolStripItem>s.

Když přidáte <xref:System.Windows.Forms.ToolStripItem>s, které vyžadují více místa, než se přiděluje <xref:System.Windows.Forms.ToolStrip>, která má aktuální velikost formuláře, <xref:System.Windows.Forms.ToolStripOverflowButton> se automaticky zobrazí na <xref:System.Windows.Forms.ToolStrip>. Zobrazí se <xref:System.Windows.Forms.ToolStripOverflowButton> a položky s povoleným přetečením se přesunou do nabídky přetečení rozevíracího seznamu. Díky tomu můžete přizpůsobit a nastavit prioritu způsobu, jakým se <xref:System.Windows.Forms.ToolStrip> položky správně přizpůsobí různým velikostem formuláře. Můžete také změnit vzhled položek, když spadají do přetečení pomocí vlastností <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> a události <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>. Pokud zvětšíte formulář buď v době návrhu, nebo v době běhu, může se v hlavním <xref:System.Windows.Forms.ToolStrip> Zobrazit více <xref:System.Windows.Forms.ToolStripItem>s a <xref:System.Windows.Forms.ToolStripOverflowButton> může dokonce zmizet, dokud nezmenšíte velikost formuláře.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>Povolení přetečení ovládacího prvku ToolStrip

- Ujistěte se, že vlastnost <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> není nastavena na `false` pro <xref:System.Windows.Forms.ToolStrip>. Výchozí formát je `True`.

     Pokud je <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> `True` (výchozí nastavení), do rozevírací nabídky přetečení se pošle <xref:System.Windows.Forms.ToolStripItem>, když obsah <xref:System.Windows.Forms.ToolStripItem> překračuje šířku vodorovného <xref:System.Windows.Forms.ToolStrip>u nebo výšku vertikálního <xref:System.Windows.Forms.ToolStrip>.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Určení chování přetečení konkrétního prvku ToolStripItem

- Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> <xref:System.Windows.Forms.ToolStripItem> na požadovanou hodnotu. Možnosti jsou `Always`, `Never`a `AsNeeded`. Výchozí formát je `AsNeeded`.

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
