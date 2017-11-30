---
title: "Postupy: Zákaz ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3307da3e0810ea775c799a4b065e1f7484b5779
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="114ab-102">Postupy: Zákaz ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="114ab-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="114ab-103">Můžete omezit nebo rozšíří příkazy, které může uživatel provést povolením a deaktivace položek nabídky v reakci na aktivit uživatelů.</span><span class="sxs-lookup"><span data-stu-id="114ab-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="114ab-104">Položky nabídky jsou ve výchozím nastavení povolené, pokud byly vytvořeny, ale to se dá upravit pomocí <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="114ab-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="114ab-105">Tuto vlastnost můžete upravit v době návrhu v **vlastnosti** okno nebo programově pomocí nastavení v kódu.</span><span class="sxs-lookup"><span data-stu-id="114ab-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="114ab-106">Chcete-li zakázat položku nabídky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="114ab-106">To disable a menu item programmatically</span></span>  
  
-   <span data-ttu-id="114ab-107">V rámci metody, kde nastavíte vlastnosti položky nabídky, přidejte kód pro nastavení <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="114ab-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
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
    >  <span data-ttu-id="114ab-108">Zakázání položku nabídky první nebo nejvyšší úrovně v nabídce skryje všechny položky nabídky obsažené v nabídce, ale není je zakázána.</span><span class="sxs-lookup"><span data-stu-id="114ab-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="114ab-109">Podobně zakázáním položky nabídky, která má položky podnabídky skryje položky podnabídky ale není je zakázána.</span><span class="sxs-lookup"><span data-stu-id="114ab-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="114ab-110">Pokud všechny příkazy dané nabídky jsou k dispozici pro uživatele, považuje programovací vhodné skrýt i zakázat celou nabídku, jak je to představuje čistou uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="114ab-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="114ab-111">Doporučujeme skrýt a zakázat v nabídce a zakázat všechny položky a položku podnabídky v nabídce, protože skrytí samostatně nezabrání přístup k příkazu nabídky prostřednictvím klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="114ab-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="114ab-112">Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost nabídka nejvyšší úrovně na `false` ke skrytí celé nabídky.</span><span class="sxs-lookup"><span data-stu-id="114ab-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114ab-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="114ab-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="114ab-114">Postupy: skrytí ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="114ab-114">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="114ab-115">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="114ab-115">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
