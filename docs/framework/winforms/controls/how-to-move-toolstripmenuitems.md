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
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039800"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="4e18d-102">Postupy: Přesouvání ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="4e18d-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="4e18d-103">V době návrhu můžete přesunout celé nabídky nejvyšší úrovně a jejich položky nabídky na jiné místo na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="4e18d-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="4e18d-104">Můžete také přesunout jednotlivé položky nabídky mezi nabídkami nejvyšší úrovně nebo změnit pozici položek nabídky v rámci nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="4e18d-105">Přesunutí nabídky nejvyšší úrovně a jejích položek nabídky do jiného umístění nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="4e18d-105">To move a top-level menu and its menu items to another top-level location</span></span>

1. <span data-ttu-id="4e18d-106">Klikněte na nabídku, kterou chcete přesunout, a podržte levé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="4e18d-106">Click and hold down the left mouse button on the menu that you want to move.</span></span>

2. <span data-ttu-id="4e18d-107">Přetáhněte kurzor do nabídky nejvyšší úrovně, která je před požadovaným novým umístěním a uvolněte levé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="4e18d-107">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>

     <span data-ttu-id="4e18d-108">Vybraná nabídka se přesune napravo od bodu vložení.</span><span class="sxs-lookup"><span data-stu-id="4e18d-108">The selected menu moves to the right of the insertion point.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="4e18d-109">Přesunutí nabídky nejvyšší úrovně a jejích položek nabídky do rozevíracího umístění</span><span class="sxs-lookup"><span data-stu-id="4e18d-109">To move a top-level menu and its menu items to a drop-down location</span></span>

1. <span data-ttu-id="4e18d-110">Klikněte levým tlačítkem myši na nabídku, kterou chcete přesunout, stiskněte klávesovou zkratku CTRL + X, nebo klikněte pravým tlačítkem myši na nabídku a vyberte **Vyjmout** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-110">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="4e18d-111">V nabídce nejvyšší úrovně cíle klikněte levým tlačítkem myši na položku nabídky nad zamýšleným novým umístěním a stiskněte klávesy CTRL + V, nebo klikněte pravým tlačítkem myši na položku nabídky nad požadovaným novým umístěním a vyberte možnost **Vložit** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-111">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="4e18d-112">Nabídka, kterou vyjmete, je vložena za vybranou položkou nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-112">The menu that you cut is inserted after the selected menu item.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="4e18d-113">Přesunutí položky nabídky v rámci nabídky pomocí editoru kolekce Items</span><span class="sxs-lookup"><span data-stu-id="4e18d-113">To move a menu item within a menu using the Items Collection Editor</span></span>

1. <span data-ttu-id="4e18d-114">Klikněte pravým tlačítkem myši na nabídku obsahující položku nabídky, kterou chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="4e18d-114">Right-click the menu that contains the menu item you want to move.</span></span>

2. <span data-ttu-id="4e18d-115">V místní nabídce vyberte možnost **Upravit vlastnost DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="4e18d-115">From the shortcut menu, choose **Edit DropDownItems**.</span></span>

3. <span data-ttu-id="4e18d-116">V **editoru kolekce položek**klikněte levým na položku nabídky, kterou chcete přesunout.</span><span class="sxs-lookup"><span data-stu-id="4e18d-116">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>

4. <span data-ttu-id="4e18d-117">Kliknutím na klávesy se šipkami nahoru a dolů přesunete položku nabídky v rámci nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-117">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>

5. <span data-ttu-id="4e18d-118">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e18d-118">Click **OK**.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="4e18d-119">Přesunutí položky nabídky v rámci nabídky pomocí klávesnice</span><span class="sxs-lookup"><span data-stu-id="4e18d-119">To move a menu item within a menu using the keyboard</span></span>

1. <span data-ttu-id="4e18d-120">Stiskněte a podržte klávesu ALT.</span><span class="sxs-lookup"><span data-stu-id="4e18d-120">Press and hold down the ALT key.</span></span>

2. <span data-ttu-id="4e18d-121">Klikněte na položku nabídky, kterou chcete přesunout, a podržte levé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="4e18d-121">Click and hold the left mouse button on the menu item that you want to move.</span></span>

3. <span data-ttu-id="4e18d-122">Přetáhněte položku nabídky do nového umístění a uvolněte levé tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="4e18d-122">Drag the menu item to the new location and release the left mouse button.</span></span>

## <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="4e18d-123">Přesunutí položky nabídky do jiné nabídky</span><span class="sxs-lookup"><span data-stu-id="4e18d-123">To move a menu item to another menu</span></span>

1. <span data-ttu-id="4e18d-124">Klikněte levým tlačítkem myši na položku nabídky, kterou chcete přesunout, stiskněte klávesovou zkratku CTRL + X, nebo klikněte pravým tlačítkem myši na položku nabídky a zvolte **Vyjmout** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-124">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="4e18d-125">Klikněte levým na nabídku, která bude obsahovat položku nabídky, kterou vyjmete.</span><span class="sxs-lookup"><span data-stu-id="4e18d-125">Left-click the menu that will contain the menu item that you cut.</span></span>

3. <span data-ttu-id="4e18d-126">Klikněte levým tlačítkem myši na položku nabídky, která je před zamýšleným novým umístěním a stiskněte klávesovou zkratku CTRL + V, nebo klikněte pravým tlačítkem myši na položku nabídky, která je před požadovaným novým umístěním a vyberte možnost **Vložit** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-126">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="4e18d-127">Položka nabídky, kterou vyjmete, je vložena za vybranou položkou nabídky.</span><span class="sxs-lookup"><span data-stu-id="4e18d-127">The menu item that you cut is inserted after the selected menu item.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e18d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e18d-128">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="4e18d-129">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="4e18d-129">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
