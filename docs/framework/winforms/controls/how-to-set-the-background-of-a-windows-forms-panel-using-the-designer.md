---
title: 'Postupy: Nastavení pozadí panelu Windows Forms pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 73b09b9240f417dbe80546e89f2fdfb1e4e4a483
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711912"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Postupy: Nastavení pozadí panelu Windows Forms pomocí návrháře
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek mohl zobrazit barvu pozadí a obrázek na pozadí. <xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro ovládací prvky, které jsou obsaženy v panelu, jako je například popisky a přepínače. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavená, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní všechny panelu. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je hodnota nastavena, obrázek se zobrazí za ovládací prvky, které jsou obsaženy v panelu.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.Panel> ovládacího prvku. Informace o tom, jak nastavit takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Chcete-li nastavit na pozadí v Návrháři formulářů Windows  
  
1.  Vyberte <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
2.  V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost pro zobrazení okna se třemi kartami.  
  
3.  Vyberte **vlastní** kartu k zobrazení palety barev.  
  
4.  Vyberte **webové** nebo **systému** kartě zobrazíte seznam předdefinovaných názvů pro barvy a pak vyberte barvu.  
  
5.  V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.  
  
6.  V **otevřít** dialogovém okně vyberte soubor, který chcete zobrazit.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Ovládací prvek Panel](panel-control-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí návrháře](group-controls-with-wf-panel-control-using-the-designer.md)
