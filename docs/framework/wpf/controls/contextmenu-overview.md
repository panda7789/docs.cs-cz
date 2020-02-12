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
# <a name="contextmenu-overview"></a>ContextMenu – přehled
Třída <xref:System.Windows.Controls.ContextMenu> představuje prvek, který zpřístupňuje funkce pomocí <xref:System.Windows.Controls.Menu>pro konkrétní kontext. Uživatel obvykle zpřístupňuje <xref:System.Windows.Controls.ContextMenu> v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] tak, že klikne pravým tlačítkem myši na tlačítko myši. Toto téma zavádí prvek <xref:System.Windows.Controls.ContextMenu> a poskytuje příklady, jak ho použít v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a kódu.  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>Dopředné řízení  
 <xref:System.Windows.Controls.ContextMenu> je připojen ke konkrétnímu ovládacímu prvku. Prvek <xref:System.Windows.Controls.ContextMenu> umožňuje uživatelům prezentovat seznam položek, které určují příkazy nebo možnosti, které jsou přidruženy ke konkrétnímu ovládacímu prvku, například <xref:System.Windows.Controls.Button>. Kliknutím pravým tlačítkem myši na ovládací prvek zobrazíte nabídku. Obvykle kliknutím na <xref:System.Windows.Controls.MenuItem> otevřete podnabídku nebo způsobí, že aplikace provede příkaz.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Vytváření beznabídku  
 Následující příklady ukazují, jak vytvořit <xref:System.Windows.Controls.ContextMenu> s podnabídkami. Ovládací prvky <xref:System.Windows.Controls.ContextMenu> jsou připojeny k ovládacím prvkům tlačítek.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Aplikování stylů na nabídku  
 Pomocí <xref:System.Windows.Style>ovládacího prvku můžete významně změnit vzhled a chování <xref:System.Windows.Controls.ContextMenu> bez psaní vlastního ovládacího prvku. Kromě nastavení vizuálních vlastností lze také použít styly na části ovládacího prvku. Například můžete změnit chování částí ovládacího prvku pomocí vlastností nebo můžete přidat části do nebo změnit rozložení <xref:System.Windows.Controls.ContextMenu>a. Následující příklady znázorňují několik způsobů, jak přidat styly pro ovládací prvky <xref:System.Windows.Controls.ContextMenu>.  
  
 První příklad definuje styl nazvaný `SimpleSysResources`, který ukazuje, jak použít aktuální nastavení systému ve stylu. Příklad přiřadí <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako barvu <xref:System.Windows.Controls.Control.Background%2A> a <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> jako <xref:System.Windows.Controls.Control.Foreground%2A>ovou barvu <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Následující příklad používá prvek <xref:System.Windows.Trigger> ke změně vzhledu <xref:System.Windows.Controls.Menu> v reakci na události, které jsou vyvolány na <xref:System.Windows.Controls.ContextMenu>. Když uživatel přesune ukazatel myši na nabídku, vzhled <xref:System.Windows.Controls.ContextMenu>ch položek se změní.  
  
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

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [ContextMenu](contextmenu.md)
- [ContextMenu – styly a šablony](contextmenu-styles-and-templates.md)
- [Ukázka galerie ovládacích prvků WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
