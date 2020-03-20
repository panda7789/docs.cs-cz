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
# <a name="contextmenu-overview"></a>ContextMenu – přehled
Třída <xref:System.Windows.Controls.ContextMenu> představuje prvek, který zveřejňuje funkce pomocí specifické <xref:System.Windows.Controls.Menu>pro kontext . Obvykle uživatel zpřístupní <xref:System.Windows.Controls.ContextMenu> v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pravým tlačítkem myši. Toto téma <xref:System.Windows.Controls.ContextMenu> představuje prvek a poskytuje příklady, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jak jej používat v a kód.  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a>Ovládací prvek ContextMenu  
 A <xref:System.Windows.Controls.ContextMenu> je připojen ke konkrétnímu ovládacímu prvku. Tento <xref:System.Windows.Controls.ContextMenu> prvek umožňuje uživatelům prezentovat seznam položek, které určují příkazy nebo možnosti, které <xref:System.Windows.Controls.Button>jsou přidruženy k určitému ovládacímu prvku, například . Uživatelé klikněte pravým tlačítkem myši na ovládací prvek, aby se nabídka zobrazila. Obvykle klepnutím na <xref:System.Windows.Controls.MenuItem> otevře podnabídku nebo způsobí, že aplikace provést příkaz.  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a>Vytváření kontextových nabídek  
 Následující příklady ukazují, jak <xref:System.Windows.Controls.ContextMenu> vytvořit s podnabídkami. Ovládací <xref:System.Windows.Controls.ContextMenu> prvky jsou připojeny k ovládacím prvkům tlačítek.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a>Aplikování stylů na kontextovou nabídku  
 Pomocí ovládacího <xref:System.Windows.Style>prvku můžete výrazně změnit vzhled a <xref:System.Windows.Controls.ContextMenu> chování bez psaní vlastního ovládacího prvku. Kromě nastavení vizuálních vlastností můžete také aplikovat styly na části ovládacího prvku. Můžete například změnit chování částí ovládacího prvku pomocí vlastností nebo můžete přidat součásti nebo <xref:System.Windows.Controls.ContextMenu>změnit rozložení . Následující příklady ukazují několik způsobů <xref:System.Windows.Controls.ContextMenu> přidání stylů do ovládacích prvků.  
  
 První příklad definuje styl `SimpleSysResources`s názvem , který ukazuje, jak používat aktuální nastavení systému ve vašem stylu. Příklad přiřadí <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> jako <xref:System.Windows.Controls.Control.Background%2A> barvu <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> a <xref:System.Windows.Controls.Control.Foreground%2A> jako <xref:System.Windows.Controls.ContextMenu>barvu .  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 Následující příklad používá <xref:System.Windows.Trigger> prvek ke změně <xref:System.Windows.Controls.Menu> vzhledu v reakci na <xref:System.Windows.Controls.ContextMenu>události, které jsou vyvolány na . Když uživatel přesune ukazatel myši nad nabídku, změní se <xref:System.Windows.Controls.ContextMenu> vzhled položek.  
  
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
