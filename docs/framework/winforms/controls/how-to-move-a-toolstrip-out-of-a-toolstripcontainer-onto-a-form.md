---
title: "Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02d1e4b105329f3d346168123debbbf73e17b9eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer ve formuláři
Pomocí následujícího postupu přesunutí <xref:System.Windows.Forms.ToolStrip> mimo <xref:System.Windows.Forms.ToolStripContainer> do formuláře.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Přesunutí ToolStrip mimo prvek ToolStripContainer formuláře  
  
1.  Vyberte <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Vyjmout <xref:System.Windows.Forms.ToolStrip> pomocí klávesy CTRL + X, nebo klikněte pravým tlačítkem <xref:System.Windows.Forms.ToolStrip> a zvolte **Vyjmout** v místní nabídce.  
  
3.  Vyberte formuláře.  
  
4.  Vložení <xref:System.Windows.Forms.ToolStrip> pomocí kláves CTRL + V, nebo zvolte **vložení** z **upravit** nabídky.  
  
5.  Nastavte <xref:System.Windows.Forms.ToolStrip.Dock%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> k **horní**.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
