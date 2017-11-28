---
title: "Postupy: Přesouvání ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 342eeeb2d156488605f244da0112869a371dfa97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-toolstripmenuitems"></a>Postupy: Přesouvání ToolStripMenuItems
V době návrhu, můžete přesunout celý nabídek nejvyšší úrovně a jejich položky nabídky na jiné místo, <xref:System.Windows.Forms.MenuStrip>. Také můžete přesunout jednotlivé položky nabídky mezi nejvyšší úrovně nabídky nebo změní pozici položek nabídek v rámci nabídky.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Chcete-li přesunout do jiného umístění nejvyšší úrovně nabídek nejvyšší úrovně a jeho položky nabídky  
  
1.  Klikněte na tlačítko a podržte klávesu levým tlačítkem myši v nabídce, který chcete přesunout.  
  
2.  Přetáhněte bod vložení do nabídek nejvyšší úrovně, které je před zamýšlené nové umístění a verzí levé tlačítko.  
  
     Přesune vybranou nabídku napravo od kurzoru.  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Přesunout do umístění rozevíracího seznamu nabídek nejvyšší úrovně a jeho položky nabídky  
  
1.  Klikněte v nabídce, který chcete přesunout a stiskněte klávesu CTRL + X, nebo klikněte pravým tlačítkem na nabídku a vyberte **Vyjmout** z místní nabídky.  
  
2.  V nabídce nejvyšší úrovně cílové levým tlačítkem myši na položku nabídky výše zamýšlené nové umístění a stiskněte klávesy CTRL + V, nebo klikněte pravým tlačítkem na položku nabídky výše zamýšlené nové umístění a vyberte **vložení** z místní nabídky.  
  
     V nabídce, která vyjmete vkládají vybranou položku nabídky.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Chcete-li přesunout položku nabídky v rámci pomocí Editor kolekce položek nabídky  
  
1.  Klikněte pravým tlačítkem v nabídce, která obsahuje položky nabídky, které chcete přesunout.  
  
2.  V místní nabídce vyberte příkaz **upravit vlastnost DropDownItems**.  
  
3.  V **Editor kolekce položek**, levým tlačítkem myši na položku nabídky, které chcete přesunout.  
  
4.  Klikněte na tlačítko nahoru a dolů klávesy se šipkami přesunout položku nabídky v nabídce.  
  
5.  Click **OK**.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Chcete-li přesunout položku nabídky v rámci nabídky pomocí klávesnice  
  
1.  Stiskněte a podržte stisknutou klávesu ALT.  
  
2.  Klikněte na tlačítko a podržením levým tlačítkem myši na položku nabídky, který chcete přesunout.  
  
3.  Přetáhněte položky nabídky do nového umístění a verzí levé tlačítko.  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>Chcete-li přesunout položku nabídky do jiné nabídky  
  
1.  Klikněte na položku nabídky, který chcete přesunout a stiskněte klávesu CTRL + X, nebo klikněte pravým tlačítkem na položku nabídky a zvolte **Vyjmout** z místní nabídky.  
  
2.  Klikněte v nabídce, která bude obsahovat položku nabídky, které jste vyjmout.  
  
3.  Levým tlačítkem myši na položku nabídky, které je před zamýšlené nové umístění a stiskněte klávesy CTRL + V nebo klikněte pravým tlačítkem na položku nabídky, které je před zamýšlené nové umístění a vyberte **vložení** z místní nabídky.  
  
     Položky nabídky, které jste vyjmout vkládají vybranou položku nabídky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Přehled ovládacího prvku MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
