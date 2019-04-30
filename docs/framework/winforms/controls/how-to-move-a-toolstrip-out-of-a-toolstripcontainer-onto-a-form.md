---
title: 'Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 9106a69ea9f28442da6e3270f7cf5abb9374b62d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913652"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři
Pomocí následujícího postupu pro přesun <xref:System.Windows.Forms.ToolStrip> z celkového počtu <xref:System.Windows.Forms.ToolStripContainer> do formuláře.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Přesunutí ToolStrip mimo prvek ToolStripContainer formuláře  
  
1. Vyberte <xref:System.Windows.Forms.ToolStrip>.  
  
2. Vyjmout <xref:System.Windows.Forms.ToolStrip> pomocí klávesy CTRL + X nebo kliknutím pravým tlačítkem <xref:System.Windows.Forms.ToolStrip> a zvolte **Vyjmout** v místní nabídce.  
  
3. Vyberte formulář.  
  
4. Vložit <xref:System.Windows.Forms.ToolStrip> pomocí kláves CTRL + V, nebo zvolte **vložit** z **upravit** nabídky.  
  
5. Nastavte <xref:System.Windows.Forms.ToolStrip.Dock%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k **horní**.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
