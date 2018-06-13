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
ms.openlocfilehash: e862f02e736cb8507dde5036700d751f8af0a226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552867"
---
# <a name="contextmenu-overview"></a>ContextMenu – přehled
<xref:System.Windows.Controls.ContextMenu> Třída reprezentuje element, který zveřejňuje funkce pomocí konkrétního kontextu <xref:System.Windows.Controls.Menu>. Obvykle se uživatel zpřístupní <xref:System.Windows.Controls.ContextMenu> v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kliknutím pravým tlačítkem na tlačítko myši. Toto téma představuje <xref:System.Windows.Controls.ContextMenu> elementu a obsahuje příklady použití v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kód.  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu – ovládací prvek  
 A <xref:System.Windows.Controls.ContextMenu> je připojen k určitý ovládací prvek. <xref:System.Windows.Controls.ContextMenu> Element umožňuje představovat seznam položek, které určují příkazy nebo možnosti, které jsou přidruženy ke konkrétní ovládacímu prvku, například uživatele <xref:System.Windows.Controls.Button>. Uživatelé klikněte pravým tlačítkem na ovládací prvek zobrazí nabídku. Obvykle, kliknutím <xref:System.Windows.Controls.MenuItem> otevře podnabídky nebo způsobí, že aplikaci k provedení příkazu.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Vytváření ContextMenus  
 Následující příklady ukazují, jak vytvořit <xref:System.Windows.Controls.ContextMenu> s dílčích. <xref:System.Windows.Controls.ContextMenu> Ovládací prvky jsou připojené k ovládací prvky tlačítek.  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Použití styly ContextMenu  
 Pomocí ovládacího prvku <xref:System.Windows.Style>, můžete výrazně změnit vzhled a chování <xref:System.Windows.Controls.ContextMenu> bez nutnosti psaní vlastního ovládacího prvku. Kromě nastavení vizuálních vlastností, můžete taky použít stylů pro část ovládacího prvku. Například můžete změnit chování částí ovládacího prvku pomocí vlastnosti, nebo můžete přidat do části nebo změna rozložení, <xref:System.Windows.Controls.ContextMenu>. Následující příklady ukazují několik způsobů, jak přidat stylů pro <xref:System.Windows.Controls.ContextMenu> ovládací prvky.  
  
 V prvním příkladu definuje nazývá `SimpleSysResources`, který ukazuje, jak používat aktuální nastavení systému ve vašem stylu. Příklad přiřadí <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> barev a <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A> barva <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Následující příklad používá <xref:System.Windows.Trigger> elementu, který chcete změnit vzhled <xref:System.Windows.Controls.Menu> v reakci na události, které jsou vyvolány na <xref:System.Windows.Controls.ContextMenu>. Když uživatel přesune myší v nabídce Vzhled <xref:System.Windows.Controls.ContextMenu> položky změny.  
  
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
 [Ukázka galerie ovládacích prvků grafického subsystému WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
