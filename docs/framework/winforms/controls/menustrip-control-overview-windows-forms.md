---
title: MenuStrip – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734465"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="47a5d-102">MenuStrip – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="47a5d-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="47a5d-103">Nabídky pro uživatele zpřístupňují funkce, které jsou seskupeny podle společného motivu.</span><span class="sxs-lookup"><span data-stu-id="47a5d-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="47a5d-104"><xref:System.Windows.Forms.MenuStrip> ovládací prvek byl představen ve verzi 2,0 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47a5d-104">The <xref:System.Windows.Forms.MenuStrip> control was introduced in version 2.0 of the .NET Framework.</span></span> <span data-ttu-id="47a5d-105">Pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip> můžete snadno vytvářet nabídky, jako ty, které se nacházejí v systém Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="47a5d-105">With the <xref:System.Windows.Forms.MenuStrip> control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="47a5d-106">Ovládací prvek <xref:System.Windows.Forms.MenuStrip> podporuje slučování rozhraní více dokumentů (MDI) a nabídek, popisy tlačítek a přetečení.</span><span class="sxs-lookup"><span data-stu-id="47a5d-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="47a5d-107">Přidáním přístupových klíčů, klávesových zkratek, značek zaškrtnutí, obrázků a oddělovacích pruhů můžete vylepšit použitelnost a čitelnost vašich nabídek.</span><span class="sxs-lookup"><span data-stu-id="47a5d-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="47a5d-108">Ovládací prvek <xref:System.Windows.Forms.MenuStrip> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.MainMenu>; Nicméně ovládací prvek <xref:System.Windows.Forms.MainMenu> zůstává zachován z důvodu zpětné kompatibility a budoucího použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="47a5d-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="47a5d-109">Způsoby použití ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="47a5d-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="47a5d-110">Pomocí ovládacího prvku <xref:System.Windows.Forms.MenuStrip>:</span><span class="sxs-lookup"><span data-stu-id="47a5d-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="47a5d-111">Vytvářejte snadno přizpůsobené, běžně používané nabídky, které podporují pokročilé funkce uživatelského rozhraní a rozložení, jako je například řazení textu a obrázků a zarovnání, operace přetažení, MDI, přetečení a alternativní režimy přístupu k příkazům nabídky.</span><span class="sxs-lookup"><span data-stu-id="47a5d-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="47a5d-112">Podporuje typický vzhled a chování operačního systému.</span><span class="sxs-lookup"><span data-stu-id="47a5d-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="47a5d-113">Zpracování událostí konzistentně pro všechny kontejnery a obsažené položky ve stejném způsobu, jakým se zpracovávají události pro jiné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="47a5d-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="47a5d-114">V následující tabulce jsou uvedeny některé zvláště důležité vlastnosti <xref:System.Windows.Forms.MenuStrip> a přidružených tříd.</span><span class="sxs-lookup"><span data-stu-id="47a5d-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="47a5d-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="47a5d-115">Property</span></span>|<span data-ttu-id="47a5d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="47a5d-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="47a5d-117">Získá nebo nastaví <xref:System.Windows.Forms.ToolStripMenuItem>, která se používá k zobrazení seznamu podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="47a5d-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="47a5d-118">Získá nebo nastaví způsob, jakým jsou podřízené nabídky sloučeny s nadřazenými nabídkami v aplikacích MDI.</span><span class="sxs-lookup"><span data-stu-id="47a5d-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="47a5d-119">Získá nebo nastaví pozici sloučené položky v rámci nabídky v aplikacích MDI.</span><span class="sxs-lookup"><span data-stu-id="47a5d-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="47a5d-120">Získá nebo nastaví hodnotu označující, zda je formulář kontejner pro podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="47a5d-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="47a5d-121">Získá nebo nastaví hodnotu označující, zda jsou pro <xref:System.Windows.Forms.MenuStrip>zobrazeny popisy nástrojů.</span><span class="sxs-lookup"><span data-stu-id="47a5d-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="47a5d-122">Získává nebo nastavuje hodnotu, která označuje, jestli <xref:System.Windows.Forms.MenuStrip> podporuje přetečení funkce.</span><span class="sxs-lookup"><span data-stu-id="47a5d-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="47a5d-123">Získá nebo nastaví klávesové zkratky spojené s <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="47a5d-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="47a5d-124">Získá nebo nastaví hodnotu označující, zda jsou vedle <xref:System.Windows.Forms.ToolStripMenuItem>zobrazeny klávesové zkratky, které jsou spojeny s <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="47a5d-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="47a5d-125">Následující tabulka uvádí důležité doprovodné třídy <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="47a5d-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="47a5d-126">Třída</span><span class="sxs-lookup"><span data-stu-id="47a5d-126">Class</span></span>|<span data-ttu-id="47a5d-127">Popis</span><span class="sxs-lookup"><span data-stu-id="47a5d-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="47a5d-128">Představuje možnost, která je možné vybrat, která se zobrazuje na <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="47a5d-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="47a5d-129">Představuje místní nabídku.</span><span class="sxs-lookup"><span data-stu-id="47a5d-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="47a5d-130">Představuje ovládací prvek, který umožňuje uživateli vybrat jednu položku ze seznamu, který se zobrazí, když uživatel klikne na <xref:System.Windows.Forms.ToolStripDropDownButton> nebo na položku nabídky vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="47a5d-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="47a5d-131">Poskytuje základní funkce pro ovládací prvky odvozené od <xref:System.Windows.Forms.ToolStripItem>, které při kliknutí zobrazují rozevírací položky.</span><span class="sxs-lookup"><span data-stu-id="47a5d-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47a5d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47a5d-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
