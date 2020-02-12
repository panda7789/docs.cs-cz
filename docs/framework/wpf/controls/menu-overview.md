---
title: Přehled nabídky
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 3d5cfba0734e684349f7d73b7242f4b69089b94d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124647"
---
# <a name="menu-overview"></a>Přehled nabídky
Třída <xref:System.Windows.Controls.Menu> umožňuje organizovat prvky přidružené k příkazům a obslužným rutinám událostí v hierarchickém pořadí. Každý prvek <xref:System.Windows.Controls.Menu> obsahuje kolekci <xref:System.Windows.Controls.MenuItem> prvků.  

<a name="menu_control"></a>   
## <a name="menu-control"></a>Ovládací prvek nabídky  
 Ovládací prvek <xref:System.Windows.Controls.Menu> prezentuje seznam položek, které určují příkazy nebo možnosti pro aplikaci. Obvykle kliknutím na <xref:System.Windows.Controls.MenuItem> otevřete podnabídku nebo způsobí, že aplikace provede příkaz.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Vytváření nabídek  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> pro manipulaci s textem v <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> obsahuje <xref:System.Windows.Controls.MenuItem> objekty, které používají vlastnosti <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>a <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a události <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>a <xref:System.Windows.Controls.MenuItem.Click>.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItemy s klávesovými zkratkami  
 Klávesové zkratky jsou kombinace znaků, které lze zadat pomocí klávesnice pro vyvolání příkazů <xref:System.Windows.Controls.Menu>. Například zástupce pro **kopii** je CTRL + C. Existují dvě vlastnosti, které lze použít s klávesovými zkratkami a položkami nabídky –<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> nebo <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Následující příklad ukazuje, jak použít vlastnost <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> k přiřazení textu klávesové zkratky k ovládacím prvkům <xref:System.Windows.Controls.MenuItem>. Tím se v položce nabídky umístí jenom klávesová zkratka.  Nespojuje příkaz s <xref:System.Windows.Controls.MenuItem>. Aby se akce mohla provést, musí aplikace zpracovat vstup uživatele.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Příkaz  
 Následující příklad ukazuje, jak použít vlastnost <xref:System.Windows.Controls.MenuItem.Command%2A> k přidružení příkazů **Open** a **Save** k ovládacím prvkům <xref:System.Windows.Controls.MenuItem>. Vlastnost příkazu nepoužívá pouze k přidružení příkazu k <xref:System.Windows.Controls.MenuItem>, ale také poskytuje text speciálního gesta, který se použije jako zástupce.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 Třída <xref:System.Windows.Controls.MenuItem> má také vlastnost <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>, která určuje prvek, ve kterém se příkaz vyskytuje. Není-li <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> nastavena, bude element, který má fokus klávesnice, přijímat příkaz. Další informace o příkazech najdete v tématu [Přehled příkazů](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Styly nabídek  
 Pomocí stylu ovládacího prvku můžete významně měnit vzhled a chování <xref:System.Windows.Controls.Menu>ch ovládacích prvků bez nutnosti psát vlastní ovládací prvek. Kromě nastavení vizuálních vlastností můžete také použít <xref:System.Windows.Style> na jednotlivé části ovládacího prvku, změnit chování částí ovládacího prvku prostřednictvím vlastností nebo přidat další části nebo změnit rozložení ovládacího prvku. Následující příklady znázorňují několik způsobů, jak přidat <xref:System.Windows.Style> k ovládacímu prvku <xref:System.Windows.Controls.Menu>.  
  
 První příklad kódu definuje <xref:System.Windows.Style> s názvem `Simple`, který ukazuje, jak používat aktuální nastavení systému ve stylu. Kód přiřadí barvu `MenuHighlightBrush` jako barvu pozadí nabídky a `MenuTextBrush` jako barvu popředí nabídky. Všimněte si, že k přiřazení štětců používáte klíče prostředků.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Následující příklad používá <xref:System.Windows.Trigger> prvky, které umožňují změnit vzhled <xref:System.Windows.Controls.MenuItem> v reakci na události, ke kterým dochází na <xref:System.Windows.Controls.Menu>. Když přesunete ukazatel myši na <xref:System.Windows.Controls.Menu>, barva popředí a charakteristiky písma položek nabídky se změní.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Viz také

- [Ukázka galerie ovládacích prvků WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
