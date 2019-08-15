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
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039800"
---
# <a name="how-to-move-toolstripmenuitems"></a>Postupy: Přesouvání ToolStripMenuItems
V době návrhu můžete přesunout celé nabídky nejvyšší úrovně a jejich položky nabídky na jiné místo na <xref:System.Windows.Forms.MenuStrip>. Můžete také přesunout jednotlivé položky nabídky mezi nabídkami nejvyšší úrovně nebo změnit pozici položek nabídky v rámci nabídky.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>Přesunutí nabídky nejvyšší úrovně a jejích položek nabídky do jiného umístění nejvyšší úrovně

1. Klikněte na nabídku, kterou chcete přesunout, a podržte levé tlačítko myši.

2. Přetáhněte kurzor do nabídky nejvyšší úrovně, která je před požadovaným novým umístěním a uvolněte levé tlačítko myši.

     Vybraná nabídka se přesune napravo od bodu vložení.

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>Přesunutí nabídky nejvyšší úrovně a jejích položek nabídky do rozevíracího umístění

1. Klikněte levým tlačítkem myši na nabídku, kterou chcete přesunout, stiskněte klávesovou zkratku CTRL + X, nebo klikněte pravým tlačítkem myši na nabídku a vyberte **Vyjmout** z místní nabídky.

2. V nabídce nejvyšší úrovně cíle klikněte levým tlačítkem myši na položku nabídky nad zamýšleným novým umístěním a stiskněte klávesy CTRL + V, nebo klikněte pravým tlačítkem myši na položku nabídky nad požadovaným novým umístěním a vyberte možnost **Vložit** z místní nabídky.

     Nabídka, kterou vyjmete, je vložena za vybranou položkou nabídky.

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>Přesunutí položky nabídky v rámci nabídky pomocí editoru kolekce Items

1. Klikněte pravým tlačítkem myši na nabídku obsahující položku nabídky, kterou chcete přesunout.

2. V místní nabídce vyberte možnost **Upravit vlastnost DropDownItems**.

3. V **editoru kolekce položek**klikněte levým na položku nabídky, kterou chcete přesunout.

4. Kliknutím na klávesy se šipkami nahoru a dolů přesunete položku nabídky v rámci nabídky.

5. Klikněte na **OK**.

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>Přesunutí položky nabídky v rámci nabídky pomocí klávesnice

1. Stiskněte a podržte klávesu ALT.

2. Klikněte na položku nabídky, kterou chcete přesunout, a podržte levé tlačítko myši.

3. Přetáhněte položku nabídky do nového umístění a uvolněte levé tlačítko myši.

## <a name="to-move-a-menu-item-to-another-menu"></a>Přesunutí položky nabídky do jiné nabídky

1. Klikněte levým tlačítkem myši na položku nabídky, kterou chcete přesunout, stiskněte klávesovou zkratku CTRL + X, nebo klikněte pravým tlačítkem myši na položku nabídky a zvolte **Vyjmout** z místní nabídky.

2. Klikněte levým na nabídku, která bude obsahovat položku nabídky, kterou vyjmete.

3. Klikněte levým tlačítkem myši na položku nabídky, která je před zamýšleným novým umístěním a stiskněte klávesovou zkratku CTRL + V, nebo klikněte pravým tlačítkem myši na položku nabídky, která je před požadovaným novým umístěním a vyberte možnost **Vložit** z místní nabídky.

     Položka nabídky, kterou vyjmete, je vložena za vybranou položkou nabídky.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Přehled ovládacího prvku MenuStrip](menustrip-control-overview-windows-forms.md)
