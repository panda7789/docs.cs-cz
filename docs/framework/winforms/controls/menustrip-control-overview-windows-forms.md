---
title: MenuStrip – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 7cd761697a09205294727043efc6cf73816803ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144349"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="8c042-102">MenuStrip – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8c042-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="8c042-103">Nabídky poskytují funkcionalitu uživatele tím, že se příkazy, které jsou seskupeny podle společnými tématy.</span><span class="sxs-lookup"><span data-stu-id="8c042-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="8c042-104"><xref:System.Windows.Forms.MenuStrip> Ovládací prvek je nová pro tuto verzi sady Visual Studio a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c042-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="8c042-105">Pomocí ovládacího prvku můžete snadno vytvořit nabídky například výstrahám nacházejícím se v aplikaci Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="8c042-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="8c042-106"><xref:System.Windows.Forms.MenuStrip> Ovládací prvek podporuje rozhraní více dokumentů (MDI) a slučování nabídek, popisy tlačítek a přetečení.</span><span class="sxs-lookup"><span data-stu-id="8c042-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="8c042-107">Přidáním přístupových klíčů, klávesové zkratky, značky zaškrtnutí, obrázky a oddělovacích pruhů můžete vylepšit použitelnosti a srozumitelnost vaší nabídky.</span><span class="sxs-lookup"><span data-stu-id="8c042-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="8c042-108"><xref:System.Windows.Forms.MenuStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.MainMenu> řízení; však <xref:System.Windows.Forms.MainMenu> ovládací prvek je zachován z důvodu zpětné kompatibility a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="8c042-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="8c042-109">Způsoby, jak pomocí ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="8c042-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="8c042-110">Použití <xref:System.Windows.Forms.MenuStrip> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="8c042-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
-   <span data-ttu-id="8c042-111">Vytvářejte snadno přizpůsobená, běžně proces nabídek, které podporují rozšířené uživatelské rozhraní a rozložení funkce, jako je text a obrázek řazení a zarovnání, operace přetažení myší, MDI, přetečení a alternativní způsoby přístup k příkazům nabídky.</span><span class="sxs-lookup"><span data-stu-id="8c042-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
-   <span data-ttu-id="8c042-112">Podpora typické vzhled a chování operačního systému.</span><span class="sxs-lookup"><span data-stu-id="8c042-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
-   <span data-ttu-id="8c042-113">Zpracování událostí konzistentní pro všechny kontejnery a upravovat položky, stejně jako zpracování událostí pro ostatní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="8c042-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="8c042-114">V následující tabulce jsou uvedeny některé zvlášť důležité vlastnosti <xref:System.Windows.Forms.MenuStrip> a související třídy.</span><span class="sxs-lookup"><span data-stu-id="8c042-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="8c042-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="8c042-115">Property</span></span>|<span data-ttu-id="8c042-116">Popis</span><span class="sxs-lookup"><span data-stu-id="8c042-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="8c042-117">Získá nebo nastaví <xref:System.Windows.Forms.ToolStripMenuItem> , který slouží k zobrazení seznamu podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="8c042-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="8c042-118">Získá nebo nastaví, jak slučování podřízených nabídek s nabídkami nadřazená aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="8c042-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="8c042-119">Získá nebo nastaví pozici sloučené položky v nabídce aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="8c042-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="8c042-120">Získá nebo nastaví hodnotu určující, zda je formulář jako kontejner pro podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="8c042-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="8c042-121">Získá nebo nastaví hodnotu určující, zda jsou uvedeny popisy tlačítek pro <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8c042-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="8c042-122">Získá nebo nastaví hodnotu označující, zda <xref:System.Windows.Forms.MenuStrip> podporuje přetečení funkce.</span><span class="sxs-lookup"><span data-stu-id="8c042-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="8c042-123">Získá nebo nastaví klávesových zkratek přidružené <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="8c042-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="8c042-124">Získá nebo nastaví hodnotu určující, zda klávesové zkratky, které jsou přidružené k <xref:System.Windows.Forms.ToolStripMenuItem> se zobrazí vedle položky <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="8c042-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="8c042-125">V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.MenuStrip> doprovodné třídy.</span><span class="sxs-lookup"><span data-stu-id="8c042-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="8c042-126">Třída</span><span class="sxs-lookup"><span data-stu-id="8c042-126">Class</span></span>|<span data-ttu-id="8c042-127">Popis</span><span class="sxs-lookup"><span data-stu-id="8c042-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="8c042-128">Představuje volitelnou možnost zobrazí na <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8c042-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="8c042-129">Představuje místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="8c042-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="8c042-130">Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne <xref:System.Windows.Forms.ToolStripDropDownButton> nebo vyšší úrovně položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="8c042-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="8c042-131">Poskytuje základní funkce pro ovládací prvky je odvozena z <xref:System.Windows.Forms.ToolStripItem> , který zobrazí rozevírací seznam položek při kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="8c042-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c042-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c042-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
