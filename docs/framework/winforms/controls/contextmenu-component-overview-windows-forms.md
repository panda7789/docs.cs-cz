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
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090560"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu – přehled komponenty (Windows Forms)
> [!IMPORTANT]
>  I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.  
  
 Pomocí Windows Forms <xref:System.Windows.Forms.ContextMenu> součásti, můžete poskytnout uživatelům snadno k dispozici nabídku s často používanými příkazy, které jsou spojeny s vybraným objektem. Položky v místní nabídce jsou často podmnožinou položky z hlavní nabídky, které jsou zobrazeny jinde v aplikaci. Uživatel obvykle můžete přistupovat k místní nabídce kliknutím pravým tlačítkem myši. Ve Windows Forms jsou spojeny s ovládacími prvky místní nabídky.  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Můžete přidružit místní nabídku ovládacího prvku tak, že nastavíte ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenu%2A> vlastnost <xref:System.Windows.Forms.ContextMenu> komponenty. Jeden místní nabídky můžou být spojené s více ovládacích prvků, ale každý ovládací prvek může mít pouze jednu nabídku.  
  
 Klíčové vlastnosti <xref:System.Windows.Forms.ContextMenu> komponenta je <xref:System.Windows.Forms.Menu.MenuItems%2A> vlastnost. Můžete přidat položky nabídky programové vytvoření <xref:System.Windows.Forms.MenuItem> objekty a jejich přidání na <xref:System.Windows.Forms.Menu.MenuItemCollection> v místní nabídce. Protože položek v místní nabídce jsou obvykle nakreslen z jiných nabídek, nejčastěji přidáte položky místní nabídky jejich zkopírováním.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
