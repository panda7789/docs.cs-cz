---
title: 'Postupy: Zakázání ToolStripMenuItems pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040274"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="9ce42-102">Postupy: Zakázání ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9ce42-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="9ce42-103">Můžete omezit nebo rozšířit příkazy, které může uživatel provést, povolením a zakázáním položek nabídky v reakci na aktivity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="9ce42-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="9ce42-104">Položky nabídky jsou ve výchozím nastavení povoleny při jejich vytvoření, ale lze je upravit prostřednictvím <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9ce42-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="9ce42-105">Tuto vlastnost můžete manipulovat v době návrhu v okně **vlastnosti** nebo programově jejich nastavením v kódu.</span><span class="sxs-lookup"><span data-stu-id="9ce42-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="9ce42-106">Další informace najdete v tématu [jak: Zakáže ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="9ce42-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>

## <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="9ce42-107">Zakázání položky nabídky v době návrhu</span><span class="sxs-lookup"><span data-stu-id="9ce42-107">To disable a menu item at design time</span></span>

1. <span data-ttu-id="9ce42-108">Pomocí položky nabídky vybrané ve formuláři nastavte <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost na `false`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9ce42-108">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>

    > [!TIP]
    >  <span data-ttu-id="9ce42-109">Zakázáním první nebo nejvyšší položky nabídky v nabídce zakážete všechny položky nabídky obsažené v nabídce.</span><span class="sxs-lookup"><span data-stu-id="9ce42-109">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="9ce42-110">Podobně zakázání položky nabídky, která má položky podnabídky, zakáže položky podnabídky.</span><span class="sxs-lookup"><span data-stu-id="9ce42-110">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="9ce42-111">Nejsou-li pro uživatele k dispozici všechny příkazy v dané nabídce, považuje se za dobrý postup programování pro skrytí a vypnutí celé nabídky, protože to představuje čisté uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ce42-111">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="9ce42-112">V nabídce byste měli tuto nabídku skrýt a zakázat, protože pokud je skryjete samostatně, nebráníte přístup k příkazu nabídky prostřednictvím klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="9ce42-112">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="9ce42-113">Nastavte vlastnost položky nabídky nejvyšší úrovně na `false` hodnotu pro skrytí celé nabídky. <xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="9ce42-113">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ce42-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ce42-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="9ce42-115">Postupy: Skrýt ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="9ce42-115">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="9ce42-116">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="9ce42-116">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
