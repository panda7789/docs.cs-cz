---
title: 'Postupy: Zakázání ToolStripMenuItems pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 38a366003a856adaf0840d0d8911263bc40dfe23
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151408"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="c8464-102">Postupy: Zakázání ToolStripMenuItems pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="c8464-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="c8464-103">Můžete omezit nebo rozšířit příkazy, které uživatel může díky povolování a zakazování položky nabídky v reakci na aktivity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="c8464-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="c8464-104">Položky nabídky jsou ve výchozím nastavení povolená, když se vytvoří, ale tuto možnost lze upravit pomocí <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c8464-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="c8464-105">Tuto vlastnost můžete upravit v době návrhu **vlastnosti** okno nebo programově podle nastavení v kódu.</span><span class="sxs-lookup"><span data-stu-id="c8464-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="c8464-106">Další informace najdete v tématu [jak: Zákaz ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="c8464-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8464-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c8464-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c8464-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c8464-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c8464-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c8464-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="c8464-110">Chcete-li zakázat položku nabídky v době návrhu</span><span class="sxs-lookup"><span data-stu-id="c8464-110">To disable a menu item at design time</span></span>  
  
1.  <span data-ttu-id="c8464-111">Pomocí položky nabídky na formuláři, nastavit <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="c8464-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c8464-112">Zakázání nabídek nejvyšší úrovně nebo první položku v nabídce zakáže všechny položky nabídky obsažené v rámci nabídky.</span><span class="sxs-lookup"><span data-stu-id="c8464-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="c8464-113">Obdobně zakázání položku nabídky, která má položky podnabídky zakáže položky podnabídky.</span><span class="sxs-lookup"><span data-stu-id="c8464-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="c8464-114">Pokud všechny příkazy v dané nabídky jsou k dispozici pro uživatele, programovací vhodné skrýt i zakázat celou nabídku, bude považován, jak to představuje čisté uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c8464-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="c8464-115">By měl jak skrýt a zakázat v nabídce skrytí samostatně nezabraňuje přístup k příkazu nabídky prostřednictvím klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="c8464-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="c8464-116">Nastavte <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnosti položky nabídek nejvyšší úrovně na `false` skrýt celé nabídky.</span><span class="sxs-lookup"><span data-stu-id="c8464-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8464-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8464-117">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="c8464-118">Postupy: Skrytí ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="c8464-118">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="c8464-119">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="c8464-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
