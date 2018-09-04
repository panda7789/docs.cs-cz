---
title: 'Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 86ab8bc979765fe79ccc76db9a0566459fde6e46
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499910"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek mohl zobrazit barvu pozadí a obrázek na pozadí. <xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro ovládací prvky, které jsou obsaženy v panelu, jako je například popisky a přepínače. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavená, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní všechny panelu. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je hodnota nastavena, obrázek se zobrazí za ovládací prvky, které jsou obsaženy v panelu.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.Panel> ovládacího prvku. Informace o tom, jak nastavit takový projekt, naleznete v tématu [postupy: vytvoření projektu aplikace Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Chcete-li nastavit na pozadí v Návrháři formulářů Windows  
  
1.  Vyberte <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
2.  V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost pro zobrazení okna se třemi kartami.  
  
3.  Vyberte **vlastní** kartu k zobrazení palety barev.  
  
4.  Vyberte **webové** nebo **systému** kartě zobrazíte seznam předdefinovaných názvů pro barvy a pak vyberte barvu.  
  
5.  V **vlastnosti** okna, klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.  
  
6.  V **otevřít** dialogovém okně vyberte soubor, který chcete zobrazit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [Ovládací prvek Panel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Přehled ovládacího prvku Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
