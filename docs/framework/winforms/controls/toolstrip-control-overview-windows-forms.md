---
title: "ToolStrip – přehled ovládacího prvku (Windows Forms)"
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
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45dab820072b3eb0bcc448ce32251e3ff5a3e622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrip-control-overview-windows-forms"></a><span data-ttu-id="ce505-102">ToolStrip – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ce505-102">ToolStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="ce505-103">Windows Forms <xref:System.Windows.Forms.ToolStrip> ovládací prvek a jeho přidružené třídy zadejte společná architektura pro kombinování prvky uživatelského rozhraní na panely nástrojů, stavové řádky a nabídky.</span><span class="sxs-lookup"><span data-stu-id="ce505-103">The Windows Forms <xref:System.Windows.Forms.ToolStrip> control and its associated classes provide a common framework for combining user interface elements into toolbars, status bars, and menus.</span></span> <span data-ttu-id="ce505-104"><xref:System.Windows.Forms.ToolStrip>ovládací prvky nabízí bohaté prostředí návrhu, která zahrnuje aktivace na místě a úpravy, vlastní rozložení a rafting, což je možnost panelů nástrojů sdílet vodorovné nebo svislé místa.</span><span class="sxs-lookup"><span data-stu-id="ce505-104"><xref:System.Windows.Forms.ToolStrip> controls offer a rich design-time experience that includes in-place activation and editing, custom layout, and rafting, which is the ability of toolbars to share horizontal or vertical space.</span></span>  
  
 <span data-ttu-id="ce505-105">I když <xref:System.Windows.Forms.ToolStrip> nahrazuje a přidá funkce pro ovládací prvek v předchozích verzích <xref:System.Windows.Forms.ToolBar> se zachovává kvůli zpětné kompatibilitě a budoucí použití, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="ce505-105">Although <xref:System.Windows.Forms.ToolStrip> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
## <a name="features-of-the-toolstrip-controls"></a><span data-ttu-id="ce505-106">Funkce ovládacích prvcích ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce505-106">Features of the ToolStrip Controls</span></span>  
 <span data-ttu-id="ce505-107">Použití <xref:System.Windows.Forms.ToolStrip> řídit k:</span><span class="sxs-lookup"><span data-stu-id="ce505-107">Use the <xref:System.Windows.Forms.ToolStrip> control to:</span></span>  
  
-   <span data-ttu-id="ce505-108">K dispozici uživatelské rozhraní společné napříč kontejnery.</span><span class="sxs-lookup"><span data-stu-id="ce505-108">Present a common user interface across containers.</span></span>  
  
-   <span data-ttu-id="ce505-109">Vytvořit snadno přizpůsobené, běžně zaměstnání panely nástrojů, které podporují pokročilé funkce uživatelského rozhraní a rozložení, jako je například ukotvení, raftingu, tlačítka s textem a bitové kopie, rozevíracího seznamu tlačítka a ovládací prvky, přetečení tlačítka a změny pořadí spuštění <xref:System.Windows.Forms.ToolStrip> položky.</span><span class="sxs-lookup"><span data-stu-id="ce505-109">Create easily customized, commonly employed toolbars that support advanced user interface and layout features, such as docking, rafting, buttons with text and images, drop-down buttons and controls, overflow buttons, and run-time reordering of <xref:System.Windows.Forms.ToolStrip> items.</span></span>  
  
-   <span data-ttu-id="ce505-110">Podpora přetečení a změna pořadí položek běhu.</span><span class="sxs-lookup"><span data-stu-id="ce505-110">Support overflow and run-time item reordering.</span></span> <span data-ttu-id="ce505-111">Funkci přetečení při není dostatek místa pro zobrazení je v Přesune položky do rozevírací nabídky <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ce505-111">The overflow feature moves items to a drop-down menu when there is not enough room to display them in a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
-   <span data-ttu-id="ce505-112">Podpora typické vzhled a chování operačního systému, prostřednictvím společného modelu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="ce505-112">Support the typical appearance and behavior of the operating system through a common rendering model.</span></span>  
  
-   <span data-ttu-id="ce505-113">Zpracování událostí konzistentně pro všechny kontejnery a obsažených položek, stejně jako zpracování událostí pro další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="ce505-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
-   <span data-ttu-id="ce505-114">Přetáhnout položky z jednoho <xref:System.Windows.Forms.ToolStrip> do jiné nebo uvnitř <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ce505-114">Drag items from one <xref:System.Windows.Forms.ToolStrip> to another or within a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
-   <span data-ttu-id="ce505-115">Vytvořit ovládací prvky rozevíracího seznamu a uživatelské rozhraní typ editory s pokročilé rozložení v <xref:System.Windows.Forms.ToolStripDropDown>.</span><span class="sxs-lookup"><span data-stu-id="ce505-115">Create drop-down controls and user interface type editors with advanced layouts in a <xref:System.Windows.Forms.ToolStripDropDown>.</span></span>  
  
 <span data-ttu-id="ce505-116">Použít <xref:System.Windows.Forms.ToolStripControlHost> třídu se má použít na další ovládací prvky <xref:System.Windows.Forms.ToolStrip> a získat <xref:System.Windows.Forms.ToolStrip> funkce pro ně.</span><span class="sxs-lookup"><span data-stu-id="ce505-116">Use the <xref:System.Windows.Forms.ToolStripControlHost> class to use other controls on a <xref:System.Windows.Forms.ToolStrip> and gain <xref:System.Windows.Forms.ToolStrip> functionality for them.</span></span>  
  
 <span data-ttu-id="ce505-117">Můžete rozšířit funkce a upravit vzhled a chování pomocí <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, a <xref:System.Windows.Forms.ToolStripManager> spolu s <xref:System.Windows.Forms.ToolStripRenderMode> a <xref:System.Windows.Forms.ToolStripManagerRenderMode> výčty.</span><span class="sxs-lookup"><span data-stu-id="ce505-117">You can extend the functionality and modify the appearance and behavior by using the <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, and <xref:System.Windows.Forms.ToolStripManager> along with the <xref:System.Windows.Forms.ToolStripRenderMode> and <xref:System.Windows.Forms.ToolStripManagerRenderMode> enumerations.</span></span>  
  
 <span data-ttu-id="ce505-118"><xref:System.Windows.Forms.ToolStrip> Řízení je vysoce Konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí můžete přizpůsobit vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="ce505-118">The <xref:System.Windows.Forms.ToolStrip> control is highly configurable and extensible, and it provides many properties, methods, and events to customize appearance and behavior.</span></span> <span data-ttu-id="ce505-119">Tady jsou některé pozoruhodné členy:</span><span class="sxs-lookup"><span data-stu-id="ce505-119">Below are some noteworthy members:</span></span>  
  
### <a name="important-toolstrip-members"></a><span data-ttu-id="ce505-120">Členy důležité ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce505-120">Important ToolStrip Members</span></span>  
  
|<span data-ttu-id="ce505-121">Název</span><span class="sxs-lookup"><span data-stu-id="ce505-121">Name</span></span>|<span data-ttu-id="ce505-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ce505-122">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|<span data-ttu-id="ce505-123">Získá nebo nastaví které okraje nadřazeného kontejneru <xref:System.Windows.Forms.ToolStrip> ukotven.</span><span class="sxs-lookup"><span data-stu-id="ce505-123">Gets or sets which edge of the parent container a <xref:System.Windows.Forms.ToolStrip> is docked to.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|<span data-ttu-id="ce505-124">Získá nebo nastaví hodnotu určující, zda přetahování myší a změna pořadí položek jsou zpracovávány soukromě pomocí <xref:System.Windows.Forms.ToolStrip> třídy.</span><span class="sxs-lookup"><span data-stu-id="ce505-124">Gets or sets a value indicating whether drag-and-drop and item reordering are handled privately by the <xref:System.Windows.Forms.ToolStrip> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|<span data-ttu-id="ce505-125">Získá nebo nastaví hodnotu, která určuje jak <xref:System.Windows.Forms.ToolStrip> rozložen jeho položky.</span><span class="sxs-lookup"><span data-stu-id="ce505-125">Gets or sets a value indicating how the <xref:System.Windows.Forms.ToolStrip> lays out its items.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|<span data-ttu-id="ce505-126">Získá nebo nastaví zda <xref:System.Windows.Forms.ToolStripItem> je připojen k <xref:System.Windows.Forms.ToolStrip> nebo <xref:System.Windows.Forms.ToolStripOverflowButton> nebo můžete mezi těmito dvěma float.</span><span class="sxs-lookup"><span data-stu-id="ce505-126">Gets or sets whether a <xref:System.Windows.Forms.ToolStripItem> is attached to the <xref:System.Windows.Forms.ToolStrip> or <xref:System.Windows.Forms.ToolStripOverflowButton> or can float between the two.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|<span data-ttu-id="ce505-127">Získá hodnotu, která určuje zda <xref:System.Windows.Forms.ToolStripItem> zobrazí další položky v rozevírací seznam při <xref:System.Windows.Forms.ToolStripItem> po kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="ce505-127">Gets a value indicating whether a <xref:System.Windows.Forms.ToolStripItem> displays other items in a drop-down list when the <xref:System.Windows.Forms.ToolStripItem> is clicked.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|<span data-ttu-id="ce505-128">Získá <xref:System.Windows.Forms.ToolStripItem> tlačítko pro který je přetečení <xref:System.Windows.Forms.ToolStrip> s přetečení povolena.</span><span class="sxs-lookup"><span data-stu-id="ce505-128">Gets the <xref:System.Windows.Forms.ToolStripItem> that is the overflow button for a <xref:System.Windows.Forms.ToolStrip> with overflow enabled.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|<span data-ttu-id="ce505-129">Získá nebo nastaví <xref:System.Windows.Forms.ToolStripRenderer> použít k přizpůsobení vzhledu a chování (vzhled a chování) <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ce505-129">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance and behavior (look and feel) of a <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|<span data-ttu-id="ce505-130">Získá nebo nastaví styly Malování použije <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ce505-130">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|<span data-ttu-id="ce505-131">Vyvolá, když <xref:System.Windows.Forms.ToolStrip.Renderer%2A> změny vlastností.</span><span class="sxs-lookup"><span data-stu-id="ce505-131">Raised when the <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property changes.</span></span>|  
  
 <span data-ttu-id="ce505-132"><xref:System.Windows.Forms.ToolStrip> Flexibilitu ovládacího prvku se dosáhne použitím několik tříd doprovodné.</span><span class="sxs-lookup"><span data-stu-id="ce505-132">The <xref:System.Windows.Forms.ToolStrip> control's flexibility is achieved through the use of a number of companion classes.</span></span> <span data-ttu-id="ce505-133">Tady jsou některé z nejvíc pozoruhodné:</span><span class="sxs-lookup"><span data-stu-id="ce505-133">Below are some of the most noteworthy:</span></span>  
  
### <a name="important-toolstrip-companion-classes"></a><span data-ttu-id="ce505-134">Třídy důležitého pomocníka ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce505-134">Important ToolStrip Companion Classes</span></span>  
  
|<span data-ttu-id="ce505-135">Název</span><span class="sxs-lookup"><span data-stu-id="ce505-135">Name</span></span>|<span data-ttu-id="ce505-136">Popis</span><span class="sxs-lookup"><span data-stu-id="ce505-136">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|<span data-ttu-id="ce505-137">Nahradí a přidá funkce <xref:System.Windows.Forms.MainMenu> třídy.</span><span class="sxs-lookup"><span data-stu-id="ce505-137">Replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> class.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip>|<span data-ttu-id="ce505-138">Nahradí a přidá funkce <xref:System.Windows.Forms.StatusBar> třídy.</span><span class="sxs-lookup"><span data-stu-id="ce505-138">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> class.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="ce505-139">Nahradí a přidá funkce <xref:System.Windows.Forms.ContextMenu> třídy.</span><span class="sxs-lookup"><span data-stu-id="ce505-139">Replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem>|<span data-ttu-id="ce505-140">Abstraktní základní třídu, která spravuje události a rozložení pro všechny elementy, <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, nebo <xref:System.Windows.Forms.ToolStripDropDown> může obsahovat.</span><span class="sxs-lookup"><span data-stu-id="ce505-140">Abstract base class that manages events and layout for all the elements that a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, or <xref:System.Windows.Forms.ToolStripDropDown> can contain.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="ce505-141">Poskytuje kontejner s panelem na každé straně formuláře, ve kterém mohou být uspořádány ovládací prvky různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="ce505-141">Provides a container with a panel on each side of the form in which controls can be arranged in various ways.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderer>|<span data-ttu-id="ce505-142">Zpracovává vykreslovací funkce pro <xref:System.Windows.Forms.ToolStrip> objekty.</span><span class="sxs-lookup"><span data-stu-id="ce505-142">Handles the painting functionality for <xref:System.Windows.Forms.ToolStrip> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|<span data-ttu-id="ce505-143">Poskytuje Microsoft Office – styl.</span><span class="sxs-lookup"><span data-stu-id="ce505-143">Provides Microsoft Office-style appearance.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManager>|<span data-ttu-id="ce505-144">Ovládací prvky <xref:System.Windows.Forms.ToolStrip> vykreslování a rafting a sloučení <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, a <xref:System.Windows.Forms.ToolStripMenuItem> objekty.</span><span class="sxs-lookup"><span data-stu-id="ce505-144">Controls <xref:System.Windows.Forms.ToolStrip> rendering and rafting, and the merging of <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, and <xref:System.Windows.Forms.ToolStripMenuItem> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|<span data-ttu-id="ce505-145">Určuje styl Malování (vlastní, Windows XP nebo Microsoft Office Professional) použitý pro více <xref:System.Windows.Forms.ToolStrip> objekty obsažené ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="ce505-145">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to multiple <xref:System.Windows.Forms.ToolStrip> objects contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|<span data-ttu-id="ce505-146">Určuje styl Malování (vlastní, Windows XP nebo Microsoft Office Professional) použitý pro jednu <xref:System.Windows.Forms.ToolStrip> objektů obsažených ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="ce505-146">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to one <xref:System.Windows.Forms.ToolStrip> object contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripControlHost>|<span data-ttu-id="ce505-147">Hostitelem jiných ovládacích prvků, které nejsou konkrétně <xref:System.Windows.Forms.ToolStrip> ovládací prvky, ale u kterého chcete <xref:System.Windows.Forms.ToolStrip> funkce.</span><span class="sxs-lookup"><span data-stu-id="ce505-147">Hosts other controls that are not specifically <xref:System.Windows.Forms.ToolStrip> controls but for which you want <xref:System.Windows.Forms.ToolStrip> functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|<span data-ttu-id="ce505-148">Určuje, zda <xref:System.Windows.Forms.ToolStripItem> je nastíněny v hlavním <xref:System.Windows.Forms.ToolStrip>, v oblasti přetečení <xref:System.Windows.Forms.ToolStrip>, nebo žádný z nich.</span><span class="sxs-lookup"><span data-stu-id="ce505-148">Specifies whether a <xref:System.Windows.Forms.ToolStripItem> is to be laid out on the main <xref:System.Windows.Forms.ToolStrip>, on the overflow <xref:System.Windows.Forms.ToolStrip>, or neither.</span></span>|  
  
 <span data-ttu-id="ce505-149">Další informace najdete v tématu [souhrn technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) a [architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="ce505-149">For more information, see [ToolStrip Technology Summary](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) and [ToolStrip Control Architecture](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce505-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce505-150">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
