---
title: "Postupy: Kopírování ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77f48d7af76cc65092e9045ab76654c96a1a7c02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="e71fd-102">Postupy: Kopírování ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="e71fd-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="e71fd-103">V době návrhu, můžete zkopírovat celý nabídek nejvyšší úrovně a jejich položky podnabídky na jiné místo, na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="e71fd-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="e71fd-104">Můžete také zkopírovat jednotlivé položky nabídky mezi nejvyšší úrovně nabídky nebo změní pozici položek nabídky v rámci nabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="e71fd-105">Kopírování nabídek nejvyšší úrovně a jeho dílčí položky do jiného umístění nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="e71fd-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="e71fd-106">Klikněte v nabídce, kterou chcete zkopírovat a stisknutím CTRL + C, nebo klikněte pravým tlačítkem na nabídku a vyberte **kopie** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e71fd-107">Klikněte v nabídce nejvyšší úrovně, které následuje po určený nové umístění a stiskněte klávesy CTRL + V nebo klikněte pravým tlačítkem na položku nabídky nejvyšší úrovně, které je před zamýšlené nové umístění a vyberte **vložení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="e71fd-108">V nabídce, který jste zkopírovali vložen před vybrané nabídek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="e71fd-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="e71fd-109">Kopírování nabídek nejvyšší úrovně a jeho dílčí položky do umístění rozevíracího seznamu</span><span class="sxs-lookup"><span data-stu-id="e71fd-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="e71fd-110">Klikněte v nabídce, který chcete přesunout a stisknutím CTRL + C, nebo klikněte pravým tlačítkem na nabídku a vyberte **kopie** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e71fd-111">V nabídce nejvyšší úrovně cílové levým tlačítkem myši položku podnabídky nad určený nové umístění a stiskněte klávesy CTRL + V nebo klikněte pravým tlačítkem na položku podnabídky nad určený nové umístění a vyberte **vložení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="e71fd-112">V nabídce, který jste zkopírovali vložen před položce vybrané podnabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="e71fd-113">Zkopírovat položku podnabídky do jiné nabídky</span><span class="sxs-lookup"><span data-stu-id="e71fd-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="e71fd-114">Levým tlačítkem myši, kterou chcete zkopírovat a stisknutím CTRL + C, nebo klikněte pravým tlačítkem na položku podnabídky a zvolte položku podnabídky **kopie** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e71fd-115">Klikněte v nabídce, která bude obsahovat dílčí položky, která vyjmete.</span><span class="sxs-lookup"><span data-stu-id="e71fd-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="e71fd-116">Levým tlačítkem myši položku dílčí, které je před zamýšlené nové umístění a stiskněte klávesy CTRL + V nebo klikněte pravým tlačítkem na položku podnabídky před zamýšlené nové umístění a vyberte **vložení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="e71fd-117">Dílčí položka, kterou jste zkopírovali vložen před položce vybrané podnabídky.</span><span class="sxs-lookup"><span data-stu-id="e71fd-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71fd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e71fd-118">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="e71fd-119">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="e71fd-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
