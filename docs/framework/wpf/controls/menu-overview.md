---
title: Přehled nabídky
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186977"
---
# <a name="menu-overview"></a>Přehled nabídky
Třída <xref:System.Windows.Controls.Menu> umožňuje uspořádat prvky přidružené k příkazům a obslužným rutinám událostí v hierarchickém pořadí. Každý <xref:System.Windows.Controls.Menu> prvek obsahuje <xref:System.Windows.Controls.MenuItem> kolekci prvků.  

<a name="menu_control"></a>
## <a name="menu-control"></a>Ovládací prvek nabídky  
 Ovládací <xref:System.Windows.Controls.Menu> prvek zobrazí seznam položek, které určují příkazy nebo možnosti pro aplikaci. Obvykle klepnutím na <xref:System.Windows.Controls.MenuItem> otevře podnabídku nebo způsobí, že aplikace provést příkaz.  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a>Vytváření nabídek  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> manipulaci s <xref:System.Windows.Controls.TextBox>textem v . Obsahuje <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.MenuItem.Command%2A>objekty, které <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>používají <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> , <xref:System.Windows.Controls.MenuItem.Checked>a <xref:System.Windows.Controls.MenuItem.Unchecked>vlastnosti a , a <xref:System.Windows.Controls.MenuItem.Click> události.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a>Položky nabídky s klávesovými zkratkami  
 Klávesové zkratky jsou kombinace znaků, které lze <xref:System.Windows.Controls.Menu> zadat pomocí klávesnice pro vyvolání příkazů. Například zástupce pro **kopírovat** je CTRL+C. S klávesovými zkratkami a položkami<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> nabídky <xref:System.Windows.Controls.MenuItem.Command%2A>lze použít dvě vlastnosti – nebo .  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a>InputGestureText  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> pomocí této vlastnosti <xref:System.Windows.Controls.MenuItem> přiřadit ovládacím prvkům text klávesové zkratky. Tím se v položce nabídky umístí pouze klávesová zkratka.  Nepřidružuje příkaz <xref:System.Windows.Controls.MenuItem>k . Aplikace musí zpracovat vstup uživatele k provedení akce.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a>Příkaz  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.MenuItem.Command%2A> použít vlastnost k přidružení příkazů <xref:System.Windows.Controls.MenuItem> **Otevřít** a **Uložit** k ovládacím prvkům. Vlastnost příkazu přidružuje <xref:System.Windows.Controls.MenuItem>nejen příkaz k příkazu , ale také dodává text vstupního gesta, který má být používán jako zástupce.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 Třída <xref:System.Windows.Controls.MenuItem> má také <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> vlastnost, která určuje prvek, kde dochází k příkazu. Pokud <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> není nastavena, prvek, který má fokus klávesnice obdrží příkaz. Další informace o příkazech naleznete v [tématu Commanding Overview](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a>Styl nabídky  
 Pomocí stylu ovládacího prvku můžete výrazně změnit <xref:System.Windows.Controls.Menu> vzhled a chování ovládacích prvků bez nutnosti psát vlastní ovládací prvek. Kromě nastavení vizuálních vlastností můžete <xref:System.Windows.Style> také použít a na jednotlivé části ovládacího prvku, změnit chování částí ovládacího prvku prostřednictvím vlastností nebo přidat další části nebo změnit rozložení ovládacího prvku. Následující příklady ukazují několik způsobů, jak přidat <xref:System.Windows.Style> do ovládacího <xref:System.Windows.Controls.Menu> prvku.  
  
 První příklad kódu definuje <xref:System.Windows.Style> `Simple` volané, které ukazuje, jak používat aktuální nastavení systému ve vašem stylu. Kód přiřadí barvu `MenuHighlightBrush` jako barvu pozadí nabídky a `MenuTextBrush` barvu popředí jako v nabídce. Všimněte si, že pomocí klíčů prostředků přiřadit stopy.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Následující ukázka <xref:System.Windows.Trigger> používá prvky, které umožňují <xref:System.Windows.Controls.MenuItem> změnit vzhled v reakci <xref:System.Windows.Controls.Menu>na události, ke kterým dochází na rozhraní . Když přesunete ukazatel <xref:System.Windows.Controls.Menu>myši , změní se barva popředí a vlastnosti písma položek nabídky.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Viz také

- [Ukázka galerie ovládacích prvků WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
