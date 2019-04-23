---
title: 'Postupy: Přesouvání ToolStripMenuItems'
ms.date: 03/30/2017
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
ms.openlocfilehash: 2203511e91254c270c59b5d298dd87a5b3737109
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308352"
---
# <a name="how-to-move-toolstripmenuitems"></a>Postupy: Přesouvání ToolStripMenuItems
V době návrhu, můžete přesunout celou nabídek nejvyšší úrovně a jejich položky nabídky na jiné místo <xref:System.Windows.Forms.MenuStrip>. Můžete také přesunout jednotlivé položky nabídky mezi nabídek nejvyšší úrovně nebo změní pozici položky nabídky v nabídce.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Chcete-li přesunout nabídek nejvyšší úrovně a jeho položky nabídky do jiného umístění nejvyšší úrovně  
  
1. Klepněte a podržte levé tlačítko myši v nabídce, která chcete přesunout.  
  
2. Přetáhněte kurzor do nejvyšší úrovně nabídky, který je před zamýšlený nové umístění a uvolnění levého tlačítka myši.  
  
     Přesune vybranou nabídku napravo od kurzoru.  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Přesunout nabídek nejvyšší úrovně a jeho položky nabídky do rozevíracího seznamu umístění  
  
1. Klikněte v nabídce, která chcete přesunout a stiskněte klávesy CTRL + X, nebo klikněte pravým tlačítkem myši na nabídku a vyberte **Vyjmout** z místní nabídky.  
  
2. V nabídce nejvyšší úrovně cílové levým tlačítkem myši položku nabídky výše zamýšlený nové umístění a stiskněte klávesy CTRL + V, nebo klikněte pravým tlačítkem na položku nabídky výše zamýšlený nové umístění a vyberte **vložit** z místní nabídky.  
  
     V nabídce, která můžete vyjmout vkládá vybranou položku nabídky.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Chcete-li přesunout položku nabídky v rámci nabídky pomocí Editor kolekce položek  
  
1. Klikněte pravým tlačítkem na nabídku, která obsahuje položky nabídky, kterou chcete přesunout.  
  
2. V místní nabídce zvolte **upravit vlastnost DropDownItems**.  
  
3. V **Editor kolekce položek**, levým tlačítkem myši na položku nabídky, kterou chcete přesunout.  
  
4. Klikněte na tlačítko klávesy se šipkami nahoru a dolů přesunout položku nabídky v rámci nabídky.  
  
5. Klikněte na **OK**.  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Chcete-li přesunout položku nabídky v nabídce pomocí klávesnice  
  
1. Stiskněte a podržte stisknutou klávesu ALT.  
  
2. Klikněte a přidržte levým tlačítkem myši na položku nabídky, kterou chcete přesunout.  
  
3. Přetáhněte položky nabídky do nového umístění a uvolnění levého tlačítka myši.  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>Chcete-li přesunout položku nabídky na jinou nabídku  
  
1. Kliknutím levého tlačítka myši, který chcete přesunout a stiskněte klávesy CTRL + X, nebo klikněte pravým tlačítkem na položku nabídky a zvolte položku nabídky **Vyjmout** z místní nabídky.  
  
2. Klikněte v nabídce, která bude obsahovat položku nabídky, vyjmutí.  
  
3. Levým tlačítkem myši na položku nabídky, je před zamýšlený nové umístění a stiskněte klávesu CTRL + V nebo klikněte pravým tlačítkem na položku nabídky, je před zamýšlený nové umístění a vyberte **vložit** z místní nabídky.  
  
     Položka nabídky, která můžete vyjmout vkládá vybranou položku nabídky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
