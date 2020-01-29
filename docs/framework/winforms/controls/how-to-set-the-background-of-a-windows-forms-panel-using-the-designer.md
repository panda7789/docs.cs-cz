---
title: Nastavení pozadí panelu pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731916"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Postupy: nastavení pozadí model Windows Forms panelu pomocí návrháře

Ovládací prvek model Windows Forms <xref:System.Windows.Forms.Panel> může zobrazit barvu pozadí i obrázek pozadí. Vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> nastavuje barvu pozadí pro ovládací prvky, které jsou obsaženy na panelu, například popisky a přepínače. Pokud vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A> není nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní celý panel. Pokud je nastavena vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A>, obrázek se zobrazí za ovládacími prvky, které jsou obsaženy na panelu.

Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.Panel>. Informace o tom, jak nastavit takový projekt v aplikaci Visual Studio, naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [: Add controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Nastavení pozadí v Návrhář formulářů

1. Otevřete projekt v aplikaci Visual Studio a vyberte ovládací prvek <xref:System.Windows.Forms.Panel>.

2. V okně **vlastnosti** klikněte na tlačítko se šipkou vedle vlastnosti <xref:System.Windows.Forms.Control.BackColor%2A>. zobrazí se okno se třemi kartami.

3. Vyberte **vlastní** kartu pro zobrazení palety barev.

4. Vyberte kartu **Web** nebo **systém** , chcete-li zobrazit seznam předdefinovaných názvů pro barvy a pak vyberte barvu.

5. V okně **vlastnosti** klikněte na tlačítko se šipkou vedle vlastnosti <xref:System.Windows.Forms.Control.BackgroundImage%2A>.

6. V dialogovém okně **otevřít** vyberte soubor, který chcete zobrazit.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Ovládací prvek Panel](panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře](group-controls-with-wf-panel-control-using-the-designer.md)
