---
title: 'Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 6927a7118c43ced03623a9764a3ef1e0814c95cb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211632"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Postupy: Nastavení pozadí panelu Windows Forms pomocí návrháře

Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek mohl zobrazit barvu pozadí a obrázek na pozadí. <xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro ovládací prvky, které jsou obsaženy v panelu, jako je například popisky a přepínače. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavená, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní všechny panelu. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je hodnota nastavena, obrázek se zobrazí za ovládací prvky, které jsou obsaženy v panelu.

Následující postup vyžaduje, **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.Panel> ovládacího prvku. Informace o tom, jak nastavit projekt v sadě Visual Studio najdete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Nastavení pozadí v Návrháři formulářů Windows

1. Otevřete projekt v sadě Visual Studio a vyberte <xref:System.Windows.Forms.Panel> ovládacího prvku.

2. V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost pro zobrazení okna se třemi kartami.

3. Vyberte **vlastní** kartu k zobrazení palety barev.

4. Vyberte **webové** nebo **systému** kartě zobrazíte seznam předdefinovaných názvů pro barvy a pak vyberte barvu.

5. V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.

6. V **otevřít** dialogovém okně vyberte soubor, který chcete zobrazit.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Ovládací prvek Panel](panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí návrháře](group-controls-with-wf-panel-control-using-the-designer.md)
