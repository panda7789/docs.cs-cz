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
ms.openlocfilehash: b973d47711632f4c0fe56f042545598272c79d2d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124361"
---
# <a name="contextmenu-overview"></a><span data-ttu-id="045ba-102">ContextMenu – přehled</span><span class="sxs-lookup"><span data-stu-id="045ba-102">ContextMenu Overview</span></span>
<span data-ttu-id="045ba-103">Třída <xref:System.Windows.Controls.ContextMenu> představuje prvek, který zpřístupňuje funkce pomocí <xref:System.Windows.Controls.Menu>pro konkrétní kontext.</span><span class="sxs-lookup"><span data-stu-id="045ba-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="045ba-104">Uživatel obvykle zpřístupňuje <xref:System.Windows.Controls.ContextMenu> v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] tak, že klikne pravým tlačítkem myši na tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="045ba-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="045ba-105">Toto téma zavádí prvek <xref:System.Windows.Controls.ContextMenu> a poskytuje příklady, jak ho použít v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kódu.</span><span class="sxs-lookup"><span data-stu-id="045ba-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="045ba-106">Dopředné řízení</span><span class="sxs-lookup"><span data-stu-id="045ba-106">ContextMenu Control</span></span>  
 <span data-ttu-id="045ba-107"><xref:System.Windows.Controls.ContextMenu> je připojen ke konkrétnímu ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="045ba-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="045ba-108">Prvek <xref:System.Windows.Controls.ContextMenu> umožňuje uživatelům prezentovat seznam položek, které určují příkazy nebo možnosti, které jsou přidruženy ke konkrétnímu ovládacímu prvku, například <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="045ba-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="045ba-109">Kliknutím pravým tlačítkem myši na ovládací prvek zobrazíte nabídku.</span><span class="sxs-lookup"><span data-stu-id="045ba-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="045ba-110">Obvykle kliknutím na <xref:System.Windows.Controls.MenuItem> otevřete podnabídku nebo způsobí, že aplikace provede příkaz.</span><span class="sxs-lookup"><span data-stu-id="045ba-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="045ba-111">Vytváření beznabídku</span><span class="sxs-lookup"><span data-stu-id="045ba-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="045ba-112">Následující příklady ukazují, jak vytvořit <xref:System.Windows.Controls.ContextMenu> s podnabídkami.</span><span class="sxs-lookup"><span data-stu-id="045ba-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="045ba-113">Ovládací prvky <xref:System.Windows.Controls.ContextMenu> jsou připojeny k ovládacím prvkům tlačítek.</span><span class="sxs-lookup"><span data-stu-id="045ba-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="045ba-114">Aplikování stylů na nabídku</span><span class="sxs-lookup"><span data-stu-id="045ba-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="045ba-115">Pomocí <xref:System.Windows.Style>ovládacího prvku můžete významně změnit vzhled a chování <xref:System.Windows.Controls.ContextMenu> bez psaní vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="045ba-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="045ba-116">Kromě nastavení vizuálních vlastností lze také použít styly na části ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="045ba-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="045ba-117">Například můžete změnit chování částí ovládacího prvku pomocí vlastností nebo můžete přidat části do nebo změnit rozložení <xref:System.Windows.Controls.ContextMenu>a.</span><span class="sxs-lookup"><span data-stu-id="045ba-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="045ba-118">Následující příklady znázorňují několik způsobů, jak přidat styly pro ovládací prvky <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="045ba-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="045ba-119">První příklad definuje styl nazvaný `SimpleSysResources`, který ukazuje, jak použít aktuální nastavení systému ve stylu.</span><span class="sxs-lookup"><span data-stu-id="045ba-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="045ba-120">Příklad přiřadí <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako barvu <xref:System.Windows.Controls.Control.Background%2A> a <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A>ovou barvu <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="045ba-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="045ba-121">Následující příklad používá prvek <xref:System.Windows.Trigger> ke změně vzhledu <xref:System.Windows.Controls.Menu> v reakci na události, které jsou vyvolány na <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="045ba-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="045ba-122">Když uživatel přesune ukazatel myši na nabídku, vzhled <xref:System.Windows.Controls.ContextMenu>ch položek se změní.</span><span class="sxs-lookup"><span data-stu-id="045ba-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="045ba-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="045ba-123">See also</span></span>

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [<span data-ttu-id="045ba-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="045ba-124">ContextMenu</span></span>](contextmenu.md)
- [<span data-ttu-id="045ba-125">ContextMenu – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="045ba-125">ContextMenu Styles and Templates</span></span>](contextmenu-styles-and-templates.md)
- [<span data-ttu-id="045ba-126">Ukázka galerie ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="045ba-126">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
