---
title: "ContextMenu – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0db67e8da97f380c3bb2eb9aab951628c4b6487
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu – přehled komponenty (Windows Forms)
> [!IMPORTANT]
>  I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky předchozí verze, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud si zvolíte.  
  
 S Windows Forms <xref:System.Windows.Forms.ContextMenu> součásti, můžete poskytnout uživatelům snadno dostupný místní nabídce často používané příkazy, které jsou přidruženy vybraný objekt. Položky v místní nabídce jsou často podmnožinou položky z hlavní nabídky, které se zobrazují jinde v aplikaci. Místní nabídky moct uživatel přistupovat obvykle kliknutím pravým tlačítkem myši. V rozhraní Windows Forms jsou spojeny s ovládacími prvky místní nabídky.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Místní nabídky můžete přidružit s ovládacím prvkem nastavením ovládacího prvku <xref:System.Windows.Forms.Control.ContextMenu%2A> vlastnost, která má <xref:System.Windows.Forms.ContextMenu> součásti. Jeden místní nabídky může být přidružen více ovládacích prvků, ale každý ovládací prvek může mít pouze jeden místní nabídky.  
  
 Klíčové vlastnosti <xref:System.Windows.Forms.ContextMenu> součást je <xref:System.Windows.Forms.Menu.MenuItems%2A> vlastnost. Položky nabídky můžete přidat prostřednictvím kódu programu vytvořením <xref:System.Windows.Forms.MenuItem> objekty a jejich přidání <xref:System.Windows.Forms.Menu.MenuItemCollection> z místní nabídky. Protože položky v místní nabídce jsou obvykle čerpají z jiných nabídek, budou nejčastěji přidejte položky do místní nabídky zkopírováním.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
