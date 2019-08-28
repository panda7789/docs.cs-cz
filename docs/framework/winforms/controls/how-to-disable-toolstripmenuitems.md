---
title: 'Postupy: Zakázání ToolStripMenuItems'
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
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046229"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="00b7d-102">Postupy: Zakázání ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="00b7d-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="00b7d-103">Můžete omezit nebo rozšířit příkazy, které může uživatel provést, povolením a zakázáním položek nabídky v reakci na aktivity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="00b7d-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="00b7d-104">Položky nabídky jsou ve výchozím nastavení povoleny při jejich vytvoření, ale lze je upravit prostřednictvím <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="00b7d-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="00b7d-105">Tuto vlastnost můžete manipulovat v době návrhu v okně **vlastnosti** nebo programově jejich nastavením v kódu.</span><span class="sxs-lookup"><span data-stu-id="00b7d-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="00b7d-106">Chcete-li zakázat položku nabídky programově</span><span class="sxs-lookup"><span data-stu-id="00b7d-106">To disable a menu item programmatically</span></span>  
  
- <span data-ttu-id="00b7d-107">V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> `false`vlastnosti na.</span><span class="sxs-lookup"><span data-stu-id="00b7d-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
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
    > <span data-ttu-id="00b7d-108">Zakázáním první nebo nejvyšší úrovně položky nabídky v nabídce se skryjí všechny položky nabídky obsažené v nabídce, ale nezakáže se.</span><span class="sxs-lookup"><span data-stu-id="00b7d-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="00b7d-109">Podobně zakázání položky nabídky, která má položky podnabídky, skryje položky podnabídky, ale nezakáže je.</span><span class="sxs-lookup"><span data-stu-id="00b7d-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="00b7d-110">Nejsou-li pro uživatele k dispozici všechny příkazy v dané nabídce, považuje se za dobrý postup programování pro skrytí a vypnutí celé nabídky, protože to představuje čisté uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00b7d-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="00b7d-111">Nabídku byste měli skrýt a zakázat a v nabídce zakázat každou položku a položku podnabídky, protože skrytím samotné neznemožníte přístup k příkazu nabídky prostřednictvím klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="00b7d-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="00b7d-112">Nastavte vlastnost položky nabídky nejvyšší úrovně na `false` hodnotu pro skrytí celé nabídky. <xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="00b7d-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b7d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00b7d-113">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="00b7d-114">Postupy: Skrýt ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="00b7d-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="00b7d-115">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="00b7d-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
