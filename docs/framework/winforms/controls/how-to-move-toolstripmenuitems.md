---
title: 'Postupy: Přesouvání ToolStripMenuItems'
ms.date: 03/30/2017
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
ms.openlocfilehash: 12554ee2225dbb186392b910ddfd7c2f69695e7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660213"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="97d62-102">Postupy: Přesouvání ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="97d62-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="97d62-103">V době návrhu, můžete přesunout celou nabídek nejvyšší úrovně a jejich položky nabídky na jiné místo <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="97d62-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="97d62-104">Můžete také přesunout jednotlivé položky nabídky mezi nabídek nejvyšší úrovně nebo změní pozici položky nabídky v nabídce.</span><span class="sxs-lookup"><span data-stu-id="97d62-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97d62-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="97d62-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="97d62-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="97d62-107">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="97d62-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="97d62-108">Chcete-li přesunout nabídek nejvyšší úrovně a jeho položky nabídky do jiného umístění nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="97d62-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="97d62-109">Klepněte a podržte levé tlačítko myši v nabídce, která chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="97d62-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="97d62-110">Přetáhněte kurzor do nejvyšší úrovně nabídky, který je před zamýšlený nové umístění a uvolnění levého tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="97d62-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="97d62-111">Přesune vybranou nabídku napravo od kurzoru.</span><span class="sxs-lookup"><span data-stu-id="97d62-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="97d62-112">Přesunout nabídek nejvyšší úrovně a jeho položky nabídky do rozevíracího seznamu umístění</span><span class="sxs-lookup"><span data-stu-id="97d62-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="97d62-113">Klikněte v nabídce, která chcete přesunout a stiskněte klávesy CTRL + X, nebo klikněte pravým tlačítkem myši na nabídku a vyberte **Vyjmout** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="97d62-114">V nabídce nejvyšší úrovně cílové levým tlačítkem myši položku nabídky výše zamýšlený nové umístění a stiskněte klávesy CTRL + V, nebo klikněte pravým tlačítkem na položku nabídky výše zamýšlený nové umístění a vyberte **vložit** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="97d62-115">V nabídce, která můžete vyjmout vkládá vybranou položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="97d62-116">Chcete-li přesunout položku nabídky v rámci nabídky pomocí Editor kolekce položek</span><span class="sxs-lookup"><span data-stu-id="97d62-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="97d62-117">Klikněte pravým tlačítkem na nabídku, která obsahuje položky nabídky, kterou chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="97d62-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="97d62-118">V místní nabídce zvolte **upravit vlastnost DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="97d62-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="97d62-119">V **Editor kolekce položek**, levým tlačítkem myši na položku nabídky, kterou chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="97d62-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="97d62-120">Klikněte na tlačítko klávesy se šipkami nahoru a dolů přesunout položku nabídky v rámci nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="97d62-121">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="97d62-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="97d62-122">Chcete-li přesunout položku nabídky v nabídce pomocí klávesnice</span><span class="sxs-lookup"><span data-stu-id="97d62-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="97d62-123">Stiskněte a podržte stisknutou klávesu ALT.</span><span class="sxs-lookup"><span data-stu-id="97d62-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="97d62-124">Klikněte a přidržte levým tlačítkem myši na položku nabídky, kterou chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="97d62-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="97d62-125">Přetáhněte položky nabídky do nového umístění a uvolnění levého tlačítka myši.</span><span class="sxs-lookup"><span data-stu-id="97d62-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="97d62-126">Chcete-li přesunout položku nabídky na jinou nabídku</span><span class="sxs-lookup"><span data-stu-id="97d62-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="97d62-127">Kliknutím levého tlačítka myši, který chcete přesunout a stiskněte klávesy CTRL + X, nebo klikněte pravým tlačítkem na položku nabídky a zvolte položku nabídky **Vyjmout** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="97d62-128">Klikněte v nabídce, která bude obsahovat položku nabídky, vyjmutí.</span><span class="sxs-lookup"><span data-stu-id="97d62-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="97d62-129">Levým tlačítkem myši na položku nabídky, je před zamýšlený nové umístění a stiskněte klávesu CTRL + V nebo klikněte pravým tlačítkem na položku nabídky, je před zamýšlený nové umístění a vyberte **vložit** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="97d62-130">Položka nabídky, která můžete vyjmout vkládá vybranou položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="97d62-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d62-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97d62-131">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="97d62-132">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="97d62-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
