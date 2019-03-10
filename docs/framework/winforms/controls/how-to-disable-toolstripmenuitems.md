---
title: 'Postupy: Zákaz ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: 3c18935239a4355d5416a0a79d0fa9f5c504cc7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720209"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="e7729-102">Postupy: Zákaz ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="e7729-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="e7729-103">Můžete omezit nebo rozšířit příkazy, které uživatel může díky povolování a zakazování položky nabídky v reakci na aktivity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="e7729-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="e7729-104">Položky nabídky jsou ve výchozím nastavení povolená, když se vytvoří, ale tuto možnost lze upravit pomocí <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e7729-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="e7729-105">Tuto vlastnost můžete upravit v době návrhu **vlastnosti** okno nebo programově podle nastavení v kódu.</span><span class="sxs-lookup"><span data-stu-id="e7729-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="e7729-106">Chcete-li zakázat položku nabídky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e7729-106">To disable a menu item programmatically</span></span>  
  
-   <span data-ttu-id="e7729-107">V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="e7729-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="e7729-108">Zakázání nabídek nejvyšší úrovně nebo první položku v nabídce skryje všechny položky nabídky obsažené v nabídce, ale je nezakáže.</span><span class="sxs-lookup"><span data-stu-id="e7729-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="e7729-109">Podobně zakázání položku nabídky, která má položky podnabídky skryje položky podnabídky, ale není je vypnout.</span><span class="sxs-lookup"><span data-stu-id="e7729-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="e7729-110">Pokud všechny příkazy v dané nabídky jsou k dispozici pro uživatele, programovací vhodné skrýt i zakázat celou nabídku, bude považován, jak to představuje čisté uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e7729-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="e7729-111">By měl skrýt a zakázat v nabídce a zakažte každé položky a podnabídky položky v nabídce, protože skrytí samostatně nezabraňuje přístup k příkazu nabídky prostřednictvím klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="e7729-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="e7729-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnosti položky nabídek nejvyšší úrovně na `false` skrýt celé nabídky.</span><span class="sxs-lookup"><span data-stu-id="e7729-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7729-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7729-113">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="e7729-114">Postupy: Skrytí ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="e7729-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="e7729-115">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="e7729-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
