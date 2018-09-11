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
ms.openlocfilehash: 54fd823594fba4500f35ed1d69720a3309e54a36
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277283"
---
# <a name="contextmenu-overview"></a>ContextMenu – přehled
<xref:System.Windows.Controls.ContextMenu> Třída reprezentuje element, který zpřístupňuje funkce s použitím kontextu konkrétní <xref:System.Windows.Controls.Menu>. Obvykle uživatel poskytuje <xref:System.Windows.Controls.ContextMenu> v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kliknutím pravým tlačítkem myši na tlačítko myši. Toto téma představuje <xref:System.Windows.Controls.ContextMenu> elementu a poskytuje příklady toho, jak ho použijte ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kódu.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu – ovládací prvek  
 A <xref:System.Windows.Controls.ContextMenu> je připojen určitý ovládací prvek. <xref:System.Windows.Controls.ContextMenu> Element umožňuje být uživateli seznam položek, které určují příkazy nebo možnosti, které jsou spojeny s konkrétní ovládací prvek, například <xref:System.Windows.Controls.Button>. Uživatelé klikněte pravým tlačítkem na ovládací prvek zobrazí nabídku. Obvykle kliknutí <xref:System.Windows.Controls.MenuItem> , otevře se podnabídka nebo způsobí, že aplikace k provedení příkazu.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Vytváření ContextMenu  
 Následující příklady ukazují, jak vytvořit <xref:System.Windows.Controls.ContextMenu> s dílčích nabídek. <xref:System.Windows.Controls.ContextMenu> Ovládací prvky jsou připojeny k ovládací prvky tlačítek.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Aplikování stylů ContextMenu  
 Pomocí ovládacího prvku <xref:System.Windows.Style>, můžete výrazně změnit vzhled a chování <xref:System.Windows.Controls.ContextMenu> bez psaní vlastního ovládacího prvku. Kromě nastavení vizuální vlastnosti, můžete také použít styly k různým částem ovládacího prvku. Například můžete změnit chování části ovládacího prvku pomocí vlastnosti, nebo můžete přidat do části nebo změnit rozložení, <xref:System.Windows.Controls.ContextMenu>. Následující příklady ukazují několik způsobů, jak přidat styly <xref:System.Windows.Controls.ContextMenu> ovládacích prvků.  
  
 První příklad definuje styl zvaný `SimpleSysResources`, který ukazuje, jak používat aktuální systémová nastavení v vašemu stylu. V příkladu přiřadí <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> barvu a <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A> barvu <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 V následujícím příkladu <xref:System.Windows.Trigger> prvek, který chcete změnit vzhled <xref:System.Windows.Controls.Menu> v reakci na události, které jsou vyvolány na <xref:System.Windows.Controls.ContextMenu>. Když uživatel pohybuje ukazatelem myši přes nabídku vzhled <xref:System.Windows.Controls.ContextMenu> položky změny.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [ContextMenu – styly a šablony](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [Ukázková galerie ovládacích prvků WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
