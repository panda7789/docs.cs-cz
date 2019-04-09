---
title: 'Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 100e744e6e49fbf214488e9bbb796b5b6fb9591a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142360"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři
Pomocí následujícího postupu pro přesun <xref:System.Windows.Forms.ToolStrip> z celkového počtu <xref:System.Windows.Forms.ToolStripContainer> do formuláře.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Přesunutí ToolStrip mimo prvek ToolStripContainer formuláře  
  
1.  Vyberte <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Vyjmout <xref:System.Windows.Forms.ToolStrip> pomocí klávesy CTRL + X nebo kliknutím pravým tlačítkem <xref:System.Windows.Forms.ToolStrip> a zvolte **Vyjmout** v místní nabídce.  
  
3.  Vyberte formulář.  
  
4.  Vložit <xref:System.Windows.Forms.ToolStrip> pomocí kláves CTRL + V, nebo zvolte **vložit** z **upravit** nabídky.  
  
5.  Nastavte <xref:System.Windows.Forms.ToolStrip.Dock%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k **horní**.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
