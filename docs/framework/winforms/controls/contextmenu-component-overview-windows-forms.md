---
title: ContextMenu – přehled komponenty
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746197"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu – přehled komponenty (Windows Forms)
> [!IMPORTANT]
> I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Pomocí součásti model Windows Forms <xref:System.Windows.Forms.ContextMenu> můžete uživatelům poskytnout snadno dostupnou místní nabídku často používaných příkazů, které jsou přidruženy k vybranému objektu. Položky v místní nabídce jsou často podmnožinou položek z hlavních nabídek, které se zobrazují jinde v aplikaci. Uživatel má obvykle přístup k místní nabídce kliknutím pravým tlačítkem myši. V model Windows Forms jsou místní nabídky přidruženy k ovládacím prvkům.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Místní nabídku můžete přidružit ovládacím prvkem nastavením vlastnosti <xref:System.Windows.Forms.Control.ContextMenu%2A> ovládacího prvku na součást <xref:System.Windows.Forms.ContextMenu>. Jedna místní nabídka může být přidružena k více ovládacím prvkům, ale každý ovládací prvek může mít pouze jednu místní nabídku.  
  
 Klíčovou vlastností součásti <xref:System.Windows.Forms.ContextMenu> je vlastnost <xref:System.Windows.Forms.Menu.MenuItems%2A>. Položky nabídky můžete přidat programově vytvářením <xref:System.Windows.Forms.MenuItem> objektů a jejich přidáním do <xref:System.Windows.Forms.Menu.MenuItemCollection> místní nabídky. Vzhledem k tomu, že se položky v místní nabídce obvykle vykreslí z jiných nabídek, budete nejčastěji přidávat položky do místní nabídky tak, že je zkopírujete.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
