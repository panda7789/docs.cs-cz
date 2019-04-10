---
title: 'Postupy: Kopírování ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: c59af175a6ee23395e19247efd8fa15e6d19ae66
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334338"
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="6a007-102">Postupy: Kopírování ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="6a007-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="6a007-103">V době návrhu, můžete zkopírovat celý nabídek nejvyšší úrovně a jejich položky podnabídky na jiné místo na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6a007-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="6a007-104">Můžete také zkopírovat jednotlivé položky nabídky mezi nabídek nejvyšší úrovně nebo změní pozici položky nabídky v nabídce.</span><span class="sxs-lookup"><span data-stu-id="6a007-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="6a007-105">Kopírování nabídek nejvyšší úrovně a jeho podnabídky položek do jiného umístění nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="6a007-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1. <span data-ttu-id="6a007-106">Klikněte v nabídce, která chcete kopírovat a stisknutím kláves CTRL + C, nebo klikněte pravým tlačítkem myši na nabídku a vyberte **kopírování** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6a007-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="6a007-107">Kliknutím levého tlačítka myši nejvyšší úrovně nabídky, která je po zamýšlený nové umístění a stiskněte klávesu CTRL + V nebo klikněte pravým tlačítkem na položku nejvyšší úrovně nabídky, je před zamýšlený nové umístění a vyberte **vložit** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6a007-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="6a007-108">V nabídce, která jste si zkopírovali se vloží před vybrané nabídek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="6a007-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="6a007-109">Kopírování nabídek nejvyšší úrovně a její podnabídku položky do umístění rozevíracího seznamu</span><span class="sxs-lookup"><span data-stu-id="6a007-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1. <span data-ttu-id="6a007-110">Klikněte v nabídce, která chcete přesunout a stisknutím kláves CTRL + C, nebo klikněte pravým tlačítkem myši na nabídku a vyberte **kopírování** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6a007-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="6a007-111">V nabídce nejvyšší úrovně cílové levým tlačítkem myši na položku dílčí nabídky, která je větší než zamýšlené nové umístění a stiskněte klávesy CTRL + V nebo klikněte pravým tlačítkem na položku dílčí nabídky, která je větší než zamýšlené nové umístění a vyberte **vložit** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6a007-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="6a007-112">V nabídce, která jste si zkopírovali se vloží před podnabídky vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="6a007-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="6a007-113">Zkopírovat položku podnabídky do jiné nabídky</span><span class="sxs-lookup"><span data-stu-id="6a007-113">To copy a submenu item to another menu</span></span>  
  
1. <span data-ttu-id="6a007-114">Kliknutím levého tlačítka myši, který chcete kopírovat a stisknutím kláves CTRL + C, nebo klikněte pravým tlačítkem na položku dílčí nabídky a zvolte položku podnabídky **kopírování** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6a007-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="6a007-115">Klikněte v nabídce, která bude obsahovat položku dílčí nabídky, která vyjmutí.</span><span class="sxs-lookup"><span data-stu-id="6a007-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3. <span data-ttu-id="6a007-116">Levým tlačítkem myši položku podnabídky, který je před zamýšlený nové umístění a stiskněte klávesu CTRL + V nebo klikněte pravým tlačítkem na položku dílčí nabídky, který je před zamýšlený nové umístění a vyberte **vložit** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6a007-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="6a007-117">Položku dílčí nabídky, který jste zkopírovali se vloží před podnabídky vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="6a007-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a007-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a007-118">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="6a007-119">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="6a007-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
