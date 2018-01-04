---
title: "Postupy: Zákaz ToolStripMenuItems pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f60976ffd42c63307a0fe476cb3dc36a7c657e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="be4cb-102">Postupy: Zákaz ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="be4cb-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="be4cb-103">Můžete omezit nebo rozšíří příkazy, které může uživatel provést povolením a deaktivace položek nabídky v reakci na aktivit uživatelů.</span><span class="sxs-lookup"><span data-stu-id="be4cb-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="be4cb-104">Položky nabídky jsou ve výchozím nastavení povolené, pokud byly vytvořeny, ale to se dá upravit pomocí <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="be4cb-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="be4cb-105">Tuto vlastnost můžete upravit v době návrhu v **vlastnosti** okno nebo programově pomocí nastavení v kódu.</span><span class="sxs-lookup"><span data-stu-id="be4cb-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="be4cb-106">Další informace najdete v tématu [postupy: zákaz ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="be4cb-106">For more information, see [How to: Disable ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be4cb-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="be4cb-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="be4cb-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="be4cb-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="be4cb-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="be4cb-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="be4cb-110">Chcete-li zakázat položku nabídky v době návrhu</span><span class="sxs-lookup"><span data-stu-id="be4cb-110">To disable a menu item at design time</span></span>  
  
1.  <span data-ttu-id="be4cb-111">Pomocí položky nabídky ve formuláři, nastavte <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="be4cb-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="be4cb-112">Zakázání položku nabídky první nebo nejvyšší úrovně v nabídce zakáže všechny položky nabídky obsažené v nabídce.</span><span class="sxs-lookup"><span data-stu-id="be4cb-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="be4cb-113">Podobně zakázání položku nabídky, který má položky podnabídky zakáže dílčí položky.</span><span class="sxs-lookup"><span data-stu-id="be4cb-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="be4cb-114">Pokud všechny příkazy dané nabídky jsou k dispozici pro uživatele, považuje programovací vhodné skrýt i zakázat celou nabídku, jak je to představuje čistou uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be4cb-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="be4cb-115">Doporučujeme jak skrýt a zakázat v nabídce jako skryté samostatně nezabrání přístup k příkazu nabídky prostřednictvím klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="be4cb-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="be4cb-116">Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost nabídka nejvyšší úrovně na `false` ke skrytí celé nabídky.</span><span class="sxs-lookup"><span data-stu-id="be4cb-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4cb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="be4cb-117">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="be4cb-118">Postupy: Skrytí ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="be4cb-118">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="be4cb-119">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="be4cb-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
