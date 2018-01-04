---
title: "ContextMenu – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0776e7960aa76a76422d01180af5fd6a089bc98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-overview"></a><span data-ttu-id="c7876-102">ContextMenu – přehled</span><span class="sxs-lookup"><span data-stu-id="c7876-102">ContextMenu Overview</span></span>
<span data-ttu-id="c7876-103"><xref:System.Windows.Controls.ContextMenu> Třída reprezentuje element, který zveřejňuje funkce pomocí konkrétního kontextu <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="c7876-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="c7876-104">Obvykle se uživatel zpřístupní <xref:System.Windows.Controls.ContextMenu> v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kliknutím pravým tlačítkem na tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="c7876-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="c7876-105">Toto téma představuje <xref:System.Windows.Controls.ContextMenu> elementu a obsahuje příklady použití v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kód.</span><span class="sxs-lookup"><span data-stu-id="c7876-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="c7876-106">ContextMenu – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c7876-106">ContextMenu Control</span></span>  
 <span data-ttu-id="c7876-107">A <xref:System.Windows.Controls.ContextMenu> je připojen k určitý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c7876-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="c7876-108"><xref:System.Windows.Controls.ContextMenu> Element umožňuje představovat seznam položek, které určují příkazy nebo možnosti, které jsou přidruženy ke konkrétní ovládacímu prvku, například uživatele <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="c7876-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="c7876-109">Uživatelé klikněte pravým tlačítkem na ovládací prvek zobrazí nabídku.</span><span class="sxs-lookup"><span data-stu-id="c7876-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="c7876-110">Obvykle, kliknutím <xref:System.Windows.Controls.MenuItem> otevře podnabídky nebo způsobí, že aplikaci k provedení příkazu.</span><span class="sxs-lookup"><span data-stu-id="c7876-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="c7876-111">Vytváření ContextMenus</span><span class="sxs-lookup"><span data-stu-id="c7876-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="c7876-112">Následující příklady ukazují, jak vytvořit <xref:System.Windows.Controls.ContextMenu> s dílčích.</span><span class="sxs-lookup"><span data-stu-id="c7876-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="c7876-113"><xref:System.Windows.Controls.ContextMenu> Ovládací prvky jsou připojené k ovládací prvky tlačítek.</span><span class="sxs-lookup"><span data-stu-id="c7876-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="c7876-114">Použití styly ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c7876-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="c7876-115">Pomocí ovládacího prvku <xref:System.Windows.Style>, můžete výrazně změnit vzhled a chování <xref:System.Windows.Controls.ContextMenu> bez nutnosti psaní vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7876-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="c7876-116">Kromě nastavení vizuálních vlastností, můžete taky použít stylů pro část ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c7876-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="c7876-117">Například můžete změnit chování částí ovládacího prvku pomocí vlastnosti, nebo můžete přidat do části nebo změna rozložení, <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="c7876-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="c7876-118">Následující příklady ukazují několik způsobů, jak přidat stylů pro <xref:System.Windows.Controls.ContextMenu> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c7876-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="c7876-119">V prvním příkladu definuje nazývá `SimpleSysResources`, který ukazuje, jak používat aktuální nastavení systému ve vašem stylu.</span><span class="sxs-lookup"><span data-stu-id="c7876-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="c7876-120">Příklad přiřadí <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> barev a <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A> barva <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="c7876-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="c7876-121">Následující příklad používá <xref:System.Windows.Trigger> elementu, který chcete změnit vzhled <xref:System.Windows.Controls.Menu> v reakci na události, které jsou vyvolány na <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="c7876-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="c7876-122">Když uživatel přesune myší v nabídce Vzhled <xref:System.Windows.Controls.ContextMenu> položky změny.</span><span class="sxs-lookup"><span data-stu-id="c7876-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7876-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7876-123">See Also</span></span>  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [<span data-ttu-id="c7876-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="c7876-124">ContextMenu</span></span>](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [<span data-ttu-id="c7876-125">ContextMenu – styly a šablony</span><span class="sxs-lookup"><span data-stu-id="c7876-125">ContextMenu Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [<span data-ttu-id="c7876-126">Ukázka galerie ovládacích prvků grafického subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="c7876-126">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
