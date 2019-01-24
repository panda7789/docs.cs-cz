---
title: ToolStripContainer – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
ms.openlocfilehash: 1f8d8bf8edd7968ed2d2a5c4ddd654dccf318f71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654045"
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="7cd37-102">ToolStripContainer – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7cd37-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="7cd37-103">A <xref:System.Windows.Forms.ToolStripContainer> má panely na levé, pravé, horní a dolní strana pro umístění a rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="7cd37-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="7cd37-104">Více <xref:System.Windows.Forms.ToolStrip> ovládací prvky zásobníku svisle, pokud je vložíte do doleva nebo doprava <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="7cd37-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="7cd37-105">Jejich řadily vodorovně, pokud je umístíte v horní nebo dolní <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="7cd37-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="7cd37-106">Můžete použít centrální <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> na pozici tradiční ovládací prvky ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="7cd37-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="7cd37-107">Některé nebo všechny <xref:System.Windows.Forms.ToolStripContainer> ovládací prvky jsou přímo vybrat v době návrhu a můžete je odstranit.</span><span class="sxs-lookup"><span data-stu-id="7cd37-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="7cd37-108">Každý panel ovládacího prvku <xref:System.Windows.Forms.ToolStripContainer> je rozšiřitelná a sbalitelný a mění svou velikost ovládacích prvků, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="7cd37-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="7cd37-109">ToolStripContainer – důležité členy</span><span class="sxs-lookup"><span data-stu-id="7cd37-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="7cd37-110">Název</span><span class="sxs-lookup"><span data-stu-id="7cd37-110">Name</span></span>|<span data-ttu-id="7cd37-111">Popis</span><span class="sxs-lookup"><span data-stu-id="7cd37-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="7cd37-112">Získá spodního panelu ovládacího prvku <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="7cd37-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="7cd37-113">Získá nebo nastaví hodnotu označující, zda spodního panelu ovládacího prvku <xref:System.Windows.Forms.ToolStripContainer> je viditelný.</span><span class="sxs-lookup"><span data-stu-id="7cd37-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="7cd37-114">Získá na levém panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="7cd37-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="7cd37-115">Získá nebo nastaví hodnotu označující, zda na levém panelu <xref:System.Windows.Forms.ToolStripContainer> je viditelný.</span><span class="sxs-lookup"><span data-stu-id="7cd37-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="7cd37-116">Získá pravého panelu ovládacího prvku <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="7cd37-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="7cd37-117">Získá nebo nastaví hodnotu označující, zda pravého panelu ovládacího prvku <xref:System.Windows.Forms.ToolStripContainer> je viditelný.</span><span class="sxs-lookup"><span data-stu-id="7cd37-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="7cd37-118">Získá horního panelu ovládacího prvku <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="7cd37-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="7cd37-119">Získá nebo nastaví hodnotu označující, zda horního panelu ovládacího prvku <xref:System.Windows.Forms.ToolStripContainer> je viditelný.</span><span class="sxs-lookup"><span data-stu-id="7cd37-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cd37-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cd37-120">See also</span></span>
- <xref:System.Windows.Forms.ToolStripContainer>
- <xref:System.Windows.Forms.ToolStripContentPanel>
