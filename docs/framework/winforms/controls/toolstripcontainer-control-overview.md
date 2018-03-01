---
title: "ToolStripContainer – přehled ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a1a4c9c77e1f347f95c0a5e17ab0d37e0013d6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="bb56d-102">ToolStripContainer – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="bb56d-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="bb56d-103">A <xref:System.Windows.Forms.ToolStripContainer> má panelů na jeho levé, pravé, horní a dolní straně pro umístění a rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="bb56d-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="bb56d-104">Více <xref:System.Windows.Forms.ToolStrip> ovládací prvky zásobníku ve svislém směru, pokud jejich umístění v doleva nebo doprava <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="bb56d-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="bb56d-105">Pokud je uvést do pravého horního nebo dolního jejich vodorovně zásobníku <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="bb56d-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="bb56d-106">Můžete použít centrální <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> na pozici tradiční ovládací prvky na formuláři.</span><span class="sxs-lookup"><span data-stu-id="bb56d-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="bb56d-107">Kterékoli nebo všechny <xref:System.Windows.Forms.ToolStripContainer> ovládací prvky jsou přímo vybrat v době návrhu a můžete je odstranit.</span><span class="sxs-lookup"><span data-stu-id="bb56d-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="bb56d-108">Jednotlivé panely <xref:System.Windows.Forms.ToolStripContainer> je rozšíření a sbalitelné a změní velikost s ovládacími prvky, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="bb56d-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="bb56d-109">Důležité ToolStripContainer členy</span><span class="sxs-lookup"><span data-stu-id="bb56d-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="bb56d-110">Název</span><span class="sxs-lookup"><span data-stu-id="bb56d-110">Name</span></span>|<span data-ttu-id="bb56d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="bb56d-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="bb56d-112">Získá na dolním panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="bb56d-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="bb56d-113">Získá nebo nastaví hodnotu, která určuje zda na dolním panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="bb56d-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="bb56d-114">Získá na levém panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="bb56d-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="bb56d-115">Získá nebo nastaví hodnotu, která určuje zda na levém panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="bb56d-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="bb56d-116">Získá na pravém panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="bb56d-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="bb56d-117">Získá nebo nastaví hodnotu, která určuje zda na pravém panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="bb56d-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="bb56d-118">Získá na horním panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="bb56d-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="bb56d-119">Získá nebo nastaví hodnotu, která určuje zda na horním panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="bb56d-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb56d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb56d-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
