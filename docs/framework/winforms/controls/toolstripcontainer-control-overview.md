---
title: ToolStripContainer – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
ms.openlocfilehash: 59afb9de3a97545407fe96f5ded60faee9d9f725
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536338"
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="732f8-102">ToolStripContainer – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="732f8-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="732f8-103">A <xref:System.Windows.Forms.ToolStripContainer> má panelů na jeho levé, pravé, horní a dolní straně pro umístění a rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="732f8-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="732f8-104">Více <xref:System.Windows.Forms.ToolStrip> ovládací prvky zásobníku ve svislém směru, pokud jejich umístění v doleva nebo doprava <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="732f8-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="732f8-105">Pokud je uvést do pravého horního nebo dolního jejich vodorovně zásobníku <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="732f8-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="732f8-106">Můžete použít centrální <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> na pozici tradiční ovládací prvky na formuláři.</span><span class="sxs-lookup"><span data-stu-id="732f8-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="732f8-107">Kterékoli nebo všechny <xref:System.Windows.Forms.ToolStripContainer> ovládací prvky jsou přímo vybrat v době návrhu a můžete je odstranit.</span><span class="sxs-lookup"><span data-stu-id="732f8-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="732f8-108">Jednotlivé panely <xref:System.Windows.Forms.ToolStripContainer> je rozšíření a sbalitelné a změní velikost s ovládacími prvky, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="732f8-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="732f8-109">Důležité ToolStripContainer členy</span><span class="sxs-lookup"><span data-stu-id="732f8-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="732f8-110">Název</span><span class="sxs-lookup"><span data-stu-id="732f8-110">Name</span></span>|<span data-ttu-id="732f8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="732f8-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="732f8-112">Získá na dolním panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="732f8-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="732f8-113">Získá nebo nastaví hodnotu, která určuje zda na dolním panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="732f8-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="732f8-114">Získá na levém panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="732f8-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="732f8-115">Získá nebo nastaví hodnotu, která určuje zda na levém panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="732f8-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="732f8-116">Získá na pravém panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="732f8-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="732f8-117">Získá nebo nastaví hodnotu, která určuje zda na pravém panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="732f8-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="732f8-118">Získá na horním panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="732f8-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="732f8-119">Získá nebo nastaví hodnotu, která určuje zda na horním panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="732f8-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="732f8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="732f8-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
