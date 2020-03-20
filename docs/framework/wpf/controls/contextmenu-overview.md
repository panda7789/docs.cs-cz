---
title: ContextMenu – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185913"
---
# <a name="contextmenu-overview"></a><span data-ttu-id="48381-102">ContextMenu – přehled</span><span class="sxs-lookup"><span data-stu-id="48381-102">ContextMenu Overview</span></span>
<span data-ttu-id="48381-103">Třída <xref:System.Windows.Controls.ContextMenu> představuje prvek, který zveřejňuje funkce pomocí specifické <xref:System.Windows.Controls.Menu>pro kontext .</span><span class="sxs-lookup"><span data-stu-id="48381-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="48381-104">Obvykle uživatel zpřístupní <xref:System.Windows.Controls.ContextMenu> v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="48381-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="48381-105">Toto téma <xref:System.Windows.Controls.ContextMenu> představuje prvek a poskytuje příklady, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jak jej používat v a kód.</span><span class="sxs-lookup"><span data-stu-id="48381-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a><span data-ttu-id="48381-106">Ovládací prvek ContextMenu</span><span class="sxs-lookup"><span data-stu-id="48381-106">ContextMenu Control</span></span>  
 <span data-ttu-id="48381-107">A <xref:System.Windows.Controls.ContextMenu> je připojen ke konkrétnímu ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="48381-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="48381-108">Tento <xref:System.Windows.Controls.ContextMenu> prvek umožňuje uživatelům prezentovat seznam položek, které určují příkazy nebo možnosti, které <xref:System.Windows.Controls.Button>jsou přidruženy k určitému ovládacímu prvku, například .</span><span class="sxs-lookup"><span data-stu-id="48381-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="48381-109">Uživatelé klikněte pravým tlačítkem myši na ovládací prvek, aby se nabídka zobrazila.</span><span class="sxs-lookup"><span data-stu-id="48381-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="48381-110">Obvykle klepnutím na <xref:System.Windows.Controls.MenuItem> otevře podnabídku nebo způsobí, že aplikace provést příkaz.</span><span class="sxs-lookup"><span data-stu-id="48381-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a><span data-ttu-id="48381-111">Vytváření kontextových nabídek</span><span class="sxs-lookup"><span data-stu-id="48381-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="48381-112">Následující příklady ukazují, jak <xref:System.Windows.Controls.ContextMenu> vytvořit s podnabídkami.</span><span class="sxs-lookup"><span data-stu-id="48381-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="48381-113">Ovládací <xref:System.Windows.Controls.ContextMenu> prvky jsou připojeny k ovládacím prvkům tlačítek.</span><span class="sxs-lookup"><span data-stu-id="48381-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="48381-114">Aplikování stylů na kontextovou nabídku</span><span class="sxs-lookup"><span data-stu-id="48381-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="48381-115">Pomocí ovládacího <xref:System.Windows.Style>prvku můžete výrazně změnit vzhled a <xref:System.Windows.Controls.ContextMenu> chování bez psaní vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="48381-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="48381-116">Kromě nastavení vizuálních vlastností můžete také aplikovat styly na části ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="48381-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="48381-117">Můžete například změnit chování částí ovládacího prvku pomocí vlastností nebo můžete přidat součásti nebo <xref:System.Windows.Controls.ContextMenu>změnit rozložení .</span><span class="sxs-lookup"><span data-stu-id="48381-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="48381-118">Následující příklady ukazují několik způsobů <xref:System.Windows.Controls.ContextMenu> přidání stylů do ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="48381-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="48381-119">První příklad definuje styl `SimpleSysResources`s názvem , který ukazuje, jak používat aktuální nastavení systému ve vašem stylu.</span><span class="sxs-lookup"><span data-stu-id="48381-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="48381-120">Příklad přiřadí <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> barvu <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> a <xref:System.Windows.Controls.Control.Foreground%2A> jako <xref:System.Windows.Controls.ContextMenu>barvu .</span><span class="sxs-lookup"><span data-stu-id="48381-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="48381-121">Následující příklad používá <xref:System.Windows.Trigger> prvek ke změně <xref:System.Windows.Controls.Menu> vzhledu v reakci na <xref:System.Windows.Controls.ContextMenu>události, které jsou vyvolány na .</span><span class="sxs-lookup"><span data-stu-id="48381-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="48381-122">Když uživatel přesune ukazatel myši nad nabídku, změní se <xref:System.Windows.Controls.ContextMenu> vzhled položek.</span><span class="sxs-lookup"><span data-stu-id="48381-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48381-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="48381-123">See also</span></span>

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [<span data-ttu-id="48381-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="48381-124">ContextMenu</span></span>](contextmenu.md)
- [<span data-ttu-id="48381-125">ContextMenu – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="48381-125">ContextMenu Styles and Templates</span></span>](contextmenu-styles-and-templates.md)
- [<span data-ttu-id="48381-126">Ukázka galerie ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="48381-126">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
