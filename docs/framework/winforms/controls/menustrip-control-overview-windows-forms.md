---
title: MenuStrip – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733462"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="66ab6-102">MenuStrip – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="66ab6-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="66ab6-103">Nabídky pro uživatele zpřístupňují funkce, které jsou seskupeny podle společného motivu.</span><span class="sxs-lookup"><span data-stu-id="66ab6-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="66ab6-104"><xref:System.Windows.Forms.MenuStrip> Ovládací prvek byl představen ve verzi 2,0 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66ab6-104">The <xref:System.Windows.Forms.MenuStrip> control was introduced in version 2.0 of the .NET Framework.</span></span> <span data-ttu-id="66ab6-105"><xref:System.Windows.Forms.MenuStrip> Pomocí ovládacího prvku můžete snadno vytvářet nabídky, jako jsou ty, které se nacházejí v systém Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="66ab6-105">With the <xref:System.Windows.Forms.MenuStrip> control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="66ab6-106"><xref:System.Windows.Forms.MenuStrip> Ovládací prvek podporuje rozhraní MDI (Multiple Document Interface) a slučování nabídek, popisy nástrojů a přetečení.</span><span class="sxs-lookup"><span data-stu-id="66ab6-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="66ab6-107">Přidáním přístupových klíčů, klávesových zkratek, značek zaškrtnutí, obrázků a oddělovacích pruhů můžete vylepšit použitelnost a čitelnost vašich nabídek.</span><span class="sxs-lookup"><span data-stu-id="66ab6-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="66ab6-108">Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.MainMenu> ovládacímu prvku. ovládací prvek však <xref:System.Windows.Forms.MainMenu> zůstává zachován z důvodu zpětné kompatibility a budoucího použití, pokud zvolíte. <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="66ab6-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="66ab6-109">Způsoby použití ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="66ab6-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="66ab6-110"><xref:System.Windows.Forms.MenuStrip> Použijte ovládací prvek pro:</span><span class="sxs-lookup"><span data-stu-id="66ab6-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="66ab6-111">Vytvářejte snadno přizpůsobené, běžně používané nabídky, které podporují pokročilé funkce uživatelského rozhraní a rozložení, jako je například řazení textu a obrázků a zarovnání, operace přetažení, MDI, přetečení a alternativní režimy přístupu k příkazům nabídky.</span><span class="sxs-lookup"><span data-stu-id="66ab6-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="66ab6-112">Podporuje typický vzhled a chování operačního systému.</span><span class="sxs-lookup"><span data-stu-id="66ab6-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="66ab6-113">Zpracování událostí konzistentně pro všechny kontejnery a obsažené položky ve stejném způsobu, jakým se zpracovávají události pro jiné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="66ab6-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="66ab6-114">V následující tabulce jsou uvedeny některé zvláště důležité vlastnosti <xref:System.Windows.Forms.MenuStrip> a přidružené třídy.</span><span class="sxs-lookup"><span data-stu-id="66ab6-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="66ab6-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="66ab6-115">Property</span></span>|<span data-ttu-id="66ab6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="66ab6-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="66ab6-117">Získá nebo nastaví <xref:System.Windows.Forms.ToolStripMenuItem> hodnotu, která se používá k zobrazení seznamu podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="66ab6-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="66ab6-118">Získá nebo nastaví způsob, jakým jsou podřízené nabídky sloučeny s nadřazenými nabídkami v aplikacích MDI.</span><span class="sxs-lookup"><span data-stu-id="66ab6-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="66ab6-119">Získá nebo nastaví pozici sloučené položky v rámci nabídky v aplikacích MDI.</span><span class="sxs-lookup"><span data-stu-id="66ab6-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="66ab6-120">Získá nebo nastaví hodnotu označující, zda je formulář kontejner pro podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="66ab6-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="66ab6-121">Získává nebo nastavuje hodnotu, která indikuje, jestli se zobrazují popisy nástrojů <xref:System.Windows.Forms.MenuStrip>pro.</span><span class="sxs-lookup"><span data-stu-id="66ab6-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="66ab6-122">Získá nebo nastaví hodnotu označující, jestli je <xref:System.Windows.Forms.MenuStrip> podporovaná funkce přetečení.</span><span class="sxs-lookup"><span data-stu-id="66ab6-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="66ab6-123">Získá nebo nastaví klávesové zkratky spojené s <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="66ab6-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="66ab6-124">Získává nebo nastavuje hodnotu, která označuje, jestli se vedle pole <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.ToolStripMenuItem>zobrazí klávesové zkratky, které jsou přidružené k.</span><span class="sxs-lookup"><span data-stu-id="66ab6-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="66ab6-125">V následující tabulce jsou uvedeny důležité <xref:System.Windows.Forms.MenuStrip> doprovodné třídy.</span><span class="sxs-lookup"><span data-stu-id="66ab6-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="66ab6-126">Třída</span><span class="sxs-lookup"><span data-stu-id="66ab6-126">Class</span></span>|<span data-ttu-id="66ab6-127">Popis</span><span class="sxs-lookup"><span data-stu-id="66ab6-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="66ab6-128">Představuje možnost s možností volby, která se <xref:System.Windows.Forms.MenuStrip> zobrazí <xref:System.Windows.Forms.ContextMenuStrip>na nebo.</span><span class="sxs-lookup"><span data-stu-id="66ab6-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="66ab6-129">Představuje místní nabídku.</span><span class="sxs-lookup"><span data-stu-id="66ab6-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="66ab6-130">Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne na <xref:System.Windows.Forms.ToolStripDropDownButton> položku nabídky nebo na vyšší úroveň.</span><span class="sxs-lookup"><span data-stu-id="66ab6-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="66ab6-131">Poskytuje základní funkce pro ovládací prvky odvozené <xref:System.Windows.Forms.ToolStripItem> z těchto zobrazených rozevíracích položek při kliknutí.</span><span class="sxs-lookup"><span data-stu-id="66ab6-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66ab6-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66ab6-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
