---
title: Přehled komponenty MainMenu
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745111"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="8aaf3-102">MainMenu – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8aaf3-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="8aaf3-103">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahrazují a přidává funkce do <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu>ových ovládacích prvků předchozích verzí, <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="8aaf3-104">Komponenta model Windows Forms <xref:System.Windows.Forms.MainMenu> zobrazí v době běhu nabídku.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="8aaf3-105">Všechny podnabídky hlavní nabídky a jednotlivé položky jsou <xref:System.Windows.Forms.MenuItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="8aaf3-106">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8aaf3-106">Key Properties</span></span>  
 <span data-ttu-id="8aaf3-107">Položka nabídky se dá určit jako výchozí položka nastavením vlastnosti <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="8aaf3-108">Výchozí položka se při kliknutí na nabídku zobrazí tučným textem.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="8aaf3-109">Vlastnost <xref:System.Windows.Forms.MenuItem.Checked%2A> položky nabídky je buď `true` nebo `false`, a označuje, zda je vybrána položka nabídky.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="8aaf3-110">Vlastnost <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> položky nabídky přizpůsobí vzhled vybrané položky: je-li <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> nastavena na `true`, zobrazí se vedle položky přepínač. Pokud je <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> nastaveno na `false`, vedle položky se zobrazí označení zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="8aaf3-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aaf3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8aaf3-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="8aaf3-112">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="8aaf3-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
