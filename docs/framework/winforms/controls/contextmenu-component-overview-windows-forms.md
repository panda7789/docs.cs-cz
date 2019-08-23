---
title: ContextMenu – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962187"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu – přehled komponenty (Windows Forms)
> [!IMPORTANT]
> I <xref:System.Windows.Forms.MenuStrip> když <xref:System.Windows.Forms.ContextMenuStrip> a <xref:System.Windows.Forms.ContextMenu> v <xref:System.Windows.Forms.MainMenu> případě potřeby nahrazují a přidávají funkce do ovládacích prvků <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> v předchozích verzích a jsou zachované pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Pomocí komponenty model Windows Forms <xref:System.Windows.Forms.ContextMenu> můžete uživatelům poskytnout snadno dostupnou místní nabídku často používaných příkazů, které jsou přidruženy k vybranému objektu. Položky v místní nabídce jsou často podmnožinou položek z hlavních nabídek, které se zobrazují jinde v aplikaci. Uživatel má obvykle přístup k místní nabídce kliknutím pravým tlačítkem myši. V model Windows Forms jsou místní nabídky přidruženy k ovládacím prvkům.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Můžete přidružit místní nabídku k ovládacímu prvku nastavením <xref:System.Windows.Forms.Control.ContextMenu%2A> vlastnosti ovládacího prvku <xref:System.Windows.Forms.ContextMenu> na komponentu. Jedna místní nabídka může být přidružena k více ovládacím prvkům, ale každý ovládací prvek může mít pouze jednu místní nabídku.  
  
 Klíčovou vlastností <xref:System.Windows.Forms.ContextMenu> komponenty <xref:System.Windows.Forms.Menu.MenuItems%2A> je vlastnost. Položky nabídky lze přidat programově vytvářením <xref:System.Windows.Forms.MenuItem> objektů a jejich přidáním <xref:System.Windows.Forms.Menu.MenuItemCollection> do místní nabídky. Vzhledem k tomu, že se položky v místní nabídce obvykle vykreslí z jiných nabídek, budete nejčastěji přidávat položky do místní nabídky tak, že je zkopírujete.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
