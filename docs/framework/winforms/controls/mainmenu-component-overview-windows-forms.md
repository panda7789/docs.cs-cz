---
title: MainMenu – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: da1b76a7019f364e7463a8345aa80d9a9bd6089e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168477"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="2e27e-102">MainMenu – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2e27e-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="2e27e-103">I když <xref:System.Windows.Forms.MenuStrip> a <xref:System.Windows.Forms.ContextMenuStrip> nahradit a přidání funkce, které <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> ovládací prvky z předchozích verzí <xref:System.Windows.Forms.MainMenu> a <xref:System.Windows.Forms.ContextMenu> se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="2e27e-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="2e27e-104">Windows Forms <xref:System.Windows.Forms.MainMenu> komponenty zobrazí nabídku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2e27e-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="2e27e-105">Všechny dílčích nabídek z hlavní nabídky a jednotlivé položky <xref:System.Windows.Forms.MenuItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="2e27e-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="2e27e-106">Vlastnosti klíče</span><span class="sxs-lookup"><span data-stu-id="2e27e-106">Key Properties</span></span>  
 <span data-ttu-id="2e27e-107">Položka nabídky lze označit jako výchozí položku tak, že nastavíte <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="2e27e-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="2e27e-108">Výchozí položka se zobrazí tučně, když dojde ke kliknutí na nabídky.</span><span class="sxs-lookup"><span data-stu-id="2e27e-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="2e27e-109">Položka nabídky <xref:System.Windows.Forms.MenuItem.Checked%2A> vlastnost je buď `true` nebo `false`a označuje, zda je vybrána položka nabídky.</span><span class="sxs-lookup"><span data-stu-id="2e27e-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="2e27e-110">Položka nabídky <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> vlastnost přizpůsobí vzhledu vybrané položky: Pokud <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> je nastavena na `true`, přepínač se zobrazí vedle položky; v případě <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> je nastavena na `false`, se zobrazí zaškrtávací políčko vedle položky.</span><span class="sxs-lookup"><span data-stu-id="2e27e-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e27e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e27e-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="2e27e-112">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="2e27e-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
