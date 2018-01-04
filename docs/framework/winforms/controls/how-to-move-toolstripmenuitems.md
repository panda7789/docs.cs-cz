---
title: "Postupy: Přesouvání ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc1cb718b3738ac93b284b0b438b08d1e721349
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="aff7e-102">Postupy: Přesouvání ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="aff7e-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="aff7e-103">V době návrhu, můžete přesunout celý nabídek nejvyšší úrovně a jejich položky nabídky na jiné místo, <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="aff7e-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="aff7e-104">Také můžete přesunout jednotlivé položky nabídky mezi nejvyšší úrovně nabídky nebo změní pozici položek nabídek v rámci nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff7e-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="aff7e-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="aff7e-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="aff7e-107">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="aff7e-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="aff7e-108">Chcete-li přesunout do jiného umístění nejvyšší úrovně nabídek nejvyšší úrovně a jeho položky nabídky</span><span class="sxs-lookup"><span data-stu-id="aff7e-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="aff7e-109">Klikněte na tlačítko a podržte klávesu levým tlačítkem myši v nabídce, který chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="aff7e-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="aff7e-110">Přetáhněte bod vložení do nabídek nejvyšší úrovně, které je před zamýšlené nové umístění a verzí levé tlačítko.</span><span class="sxs-lookup"><span data-stu-id="aff7e-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="aff7e-111">Přesune vybranou nabídku napravo od kurzoru.</span><span class="sxs-lookup"><span data-stu-id="aff7e-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="aff7e-112">Přesunout do umístění rozevíracího seznamu nabídek nejvyšší úrovně a jeho položky nabídky</span><span class="sxs-lookup"><span data-stu-id="aff7e-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="aff7e-113">Klikněte v nabídce, který chcete přesunout a stiskněte klávesu CTRL + X, nebo klikněte pravým tlačítkem na nabídku a vyberte **Vyjmout** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="aff7e-114">V nabídce nejvyšší úrovně cílové levým tlačítkem myši na položku nabídky výše zamýšlené nové umístění a stiskněte klávesy CTRL + V, nebo klikněte pravým tlačítkem na položku nabídky výše zamýšlené nové umístění a vyberte **vložení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="aff7e-115">V nabídce, která vyjmete vkládají vybranou položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="aff7e-116">Chcete-li přesunout položku nabídky v rámci pomocí Editor kolekce položek nabídky</span><span class="sxs-lookup"><span data-stu-id="aff7e-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="aff7e-117">Klikněte pravým tlačítkem v nabídce, která obsahuje položky nabídky, které chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="aff7e-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="aff7e-118">V místní nabídce vyberte příkaz **upravit vlastnost DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="aff7e-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="aff7e-119">V **Editor kolekce položek**, levým tlačítkem myši na položku nabídky, které chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="aff7e-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="aff7e-120">Klikněte na tlačítko nahoru a dolů klávesy se šipkami přesunout položku nabídky v nabídce.</span><span class="sxs-lookup"><span data-stu-id="aff7e-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="aff7e-121">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="aff7e-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="aff7e-122">Chcete-li přesunout položku nabídky v rámci nabídky pomocí klávesnice</span><span class="sxs-lookup"><span data-stu-id="aff7e-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="aff7e-123">Stiskněte a podržte stisknutou klávesu ALT.</span><span class="sxs-lookup"><span data-stu-id="aff7e-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="aff7e-124">Klikněte na tlačítko a podržením levým tlačítkem myši na položku nabídky, který chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="aff7e-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="aff7e-125">Přetáhněte položky nabídky do nového umístění a verzí levé tlačítko.</span><span class="sxs-lookup"><span data-stu-id="aff7e-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="aff7e-126">Chcete-li přesunout položku nabídky do jiné nabídky</span><span class="sxs-lookup"><span data-stu-id="aff7e-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="aff7e-127">Klikněte na položku nabídky, který chcete přesunout a stiskněte klávesu CTRL + X, nebo klikněte pravým tlačítkem na položku nabídky a zvolte **Vyjmout** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="aff7e-128">Klikněte v nabídce, která bude obsahovat položku nabídky, které jste vyjmout.</span><span class="sxs-lookup"><span data-stu-id="aff7e-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="aff7e-129">Levým tlačítkem myši na položku nabídky, které je před zamýšlené nové umístění a stiskněte klávesy CTRL + V nebo klikněte pravým tlačítkem na položku nabídky, které je před zamýšlené nové umístění a vyberte **vložení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="aff7e-130">Položky nabídky, které jste vyjmout vkládají vybranou položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="aff7e-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff7e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="aff7e-131">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="aff7e-132">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="aff7e-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
