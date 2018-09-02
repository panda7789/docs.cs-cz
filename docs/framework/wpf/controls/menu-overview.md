---
title: Přehled nabídky
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: a1074d09c195a78dcc79df0841123672b716bcfe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423109"
---
# <a name="menu-overview"></a>Přehled nabídky
<xref:System.Windows.Controls.Menu> Třída umožňuje uspořádat prvky, které jsou spojené s příkazy a obslužnými rutinami událostí v hierarchickém pořadí. Každý <xref:System.Windows.Controls.Menu> kolekce obsahuje element <xref:System.Windows.Controls.MenuItem> elementy.  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>Menu – ovládací prvek  
 <xref:System.Windows.Controls.Menu> Ovládací prvek zobrazí seznam položek, které určují možnosti pro aplikaci nebo příkazy. Obvykle kliknutí <xref:System.Windows.Controls.MenuItem> , otevře se podnabídka nebo způsobí, že aplikace k provedení příkazu.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Vytvoření nabídky  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> pro práci s textem v <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> Obsahuje <xref:System.Windows.Controls.MenuItem> objekty, které používají <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, a <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnosti a <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, a <xref:System.Windows.Controls.MenuItem.Click> události.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Vlastnost MenuItems s klávesovými zkratkami  
 Klávesové zkratky jsou určeny kombinace znaků, které mohou být zadány pomocí klávesnice, který má být vyvolán <xref:System.Windows.Controls.Menu> příkazy. Například klávesovou zkratku pro **kopírování** je kombinace kláves CTRL + C. Existují dvě vlastnosti pomocí klávesové zkratky a položky v nabídce –<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> nebo <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> vlastnost má být přiřazena text klávesové zkratky pro <xref:System.Windows.Controls.MenuItem> ovládacích prvků. To umístí pouze klávesové zkratky v položce nabídky.  Nepřiřadí příkaz <xref:System.Windows.Controls.MenuItem>. Aplikace musí zpracovat vstup uživatele k provedení akce.  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Příkaz  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.MenuItem.Command%2A> vlastnost pro přidružení **otevřít** a **Uložit** příkazů s <xref:System.Windows.Controls.MenuItem> ovládacích prvků. Nejen vlastnost příkazu přidružit příkaz s <xref:System.Windows.Controls.MenuItem>, ale také poskytuje gesta vstupní text, který má použít jako zástupce.  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> Třída má také <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> vlastnost, která určuje element, kde dochází k příkazu. Pokud <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> není nastaven, elementu, který má fokus klávesnice přijme příkaz. Další informace o příkazech najdete v tématu [přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Používání stylů pro nabídky  
 Díky používání stylů pro ovládací prvek, můžete výrazně změnit vzhled a chování <xref:System.Windows.Controls.Menu> ovládací prvky bez nutnosti psát vlastní ovládací prvek. Kromě nastavení vizuální vlastnosti, můžete také použít <xref:System.Windows.Style> na jednotlivé části ovládacího prvku, chování části ovládacího prvku pomocí vlastnosti, změnit nebo přidat další části nebo změna rozložení ovládacího prvku. Následující příklady ukazují několik způsobů, jak přidat <xref:System.Windows.Style> k <xref:System.Windows.Controls.Menu> ovládacího prvku.  
  
 První příklad kódu definuje <xref:System.Windows.Style> volá `Simple` , který ukazuje, jak používat aktuální systémová nastavení v vašemu stylu. Kód přiřadí barvu `MenuHighlightBrush` jako barva pozadí v nabídce a `MenuTextBrush` jako barva popředí v nabídce. Všimněte si, že použijete k přiřazení stopy klíče prostředku.  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Následující ukázkový používá <xref:System.Windows.Trigger> prvky, které vám umožní změnit vzhled <xref:System.Windows.Controls.MenuItem> v reakci na události, které <xref:System.Windows.Controls.Menu>. Když přesunete ukazatel myši <xref:System.Windows.Controls.Menu>, barvu popředí a vlastností písma položky nabídky, změnit.  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázková galerie ovládacích prvků WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
