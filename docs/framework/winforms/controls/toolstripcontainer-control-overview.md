---
title: "ToolStripContainer – přehled ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4abc783961177a55cdb81cefd21ed2d7aefb0620
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="1c692-102">ToolStripContainer – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="1c692-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="1c692-103">A <xref:System.Windows.Forms.ToolStripContainer> má panelů na jeho levé, pravé, horní a dolní straně pro umístění a rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="1c692-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="1c692-104">Více <xref:System.Windows.Forms.ToolStrip> ovládací prvky zásobníku ve svislém směru, pokud jejich umístění v doleva nebo doprava <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="1c692-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="1c692-105">Pokud je uvést do pravého horního nebo dolního jejich vodorovně zásobníku <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="1c692-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="1c692-106">Můžete použít centrální <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> na pozici tradiční ovládací prvky na formuláři.</span><span class="sxs-lookup"><span data-stu-id="1c692-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="1c692-107">Kterékoli nebo všechny <xref:System.Windows.Forms.ToolStripContainer> ovládací prvky jsou přímo vybrat v době návrhu a můžete je odstranit.</span><span class="sxs-lookup"><span data-stu-id="1c692-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="1c692-108">Jednotlivé panely <xref:System.Windows.Forms.ToolStripContainer> je rozšíření a sbalitelné a změní velikost s ovládacími prvky, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="1c692-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="1c692-109">Důležité ToolStripContainer členy</span><span class="sxs-lookup"><span data-stu-id="1c692-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="1c692-110">Název</span><span class="sxs-lookup"><span data-stu-id="1c692-110">Name</span></span>|<span data-ttu-id="1c692-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1c692-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="1c692-112">Získá na dolním panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="1c692-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="1c692-113">Získá nebo nastaví hodnotu, která určuje zda na dolním panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="1c692-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="1c692-114">Získá na levém panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="1c692-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="1c692-115">Získá nebo nastaví hodnotu, která určuje zda na levém panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="1c692-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="1c692-116">Získá na pravém panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="1c692-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="1c692-117">Získá nebo nastaví hodnotu, která určuje zda na pravém panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="1c692-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="1c692-118">Získá na horním panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="1c692-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="1c692-119">Získá nebo nastaví hodnotu, která určuje zda na horním panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelná.</span><span class="sxs-lookup"><span data-stu-id="1c692-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c692-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c692-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
