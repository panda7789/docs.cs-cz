---
title: "Přehled nabídky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ab5092b1bc9db22390a18b2c1cb1ad5725a2037
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="menu-overview"></a>Přehled nabídky
<xref:System.Windows.Controls.Menu> Třída umožňuje uspořádat prvky přidružené příkazy a obslužné rutiny událostí v hierarchickém pořadí. Každý <xref:System.Windows.Controls.Menu> element obsahuje kolekci <xref:System.Windows.Controls.MenuItem> elementy.  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>Menu – ovládací prvek  
 <xref:System.Windows.Controls.Menu> Řízení představuje seznam položek, které určují příkazy nebo možnosti pro aplikaci. Obvykle, kliknutím <xref:System.Windows.Controls.MenuItem> otevře podnabídky nebo způsobí, že aplikaci k provedení příkazu.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Vytváření nabídek  
 Následující příklad vytvoří <xref:System.Windows.Controls.Menu> pro práci s textem v <xref:System.Windows.Controls.TextBox>. <xref:System.Windows.Controls.Menu> Obsahuje <xref:System.Windows.Controls.MenuItem> objekty, které používají <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, a <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnosti a <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, a <xref:System.Windows.Controls.MenuItem.Click> události.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>Vlastnost MenuItems pomocí klávesové zkratky  
 Klávesové zkratky jsou kombinace znaků, které lze zadat pomocí klávesnice k vyvolání <xref:System.Windows.Controls.Menu> příkazy. Například na zástupce **kopie** je CTRL + C. Existují dvě vlastnosti se používat s klávesové zkratky a položky nabídky –<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> nebo <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> vlastnost přiřadit text klávesové zkratky pro <xref:System.Windows.Controls.MenuItem> ovládací prvky. To jenom umístí klávesovou zkratku položku nabídky.  Příkaz s nespojí <xref:System.Windows.Controls.MenuItem>. Aplikace musí zpracovat vstup uživatele k provedení akce.  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Příkaz  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.MenuItem.Command%2A> vlastnost pro přidružení **otevřete** a **Uložit** příkazy pomocí <xref:System.Windows.Controls.MenuItem> ovládací prvky. Ne jenom vlastnost příkazu přidružit příkaz se <xref:System.Windows.Controls.MenuItem>, ale také poskytuje vstupní gesto text, který chcete použít jako zástupce.  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> Třída také obsahuje <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> vlastnosti, která určuje elementu, kde dochází k příkazu. Pokud <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> není nastaven, elementu, který má právě fokus klávesnice přijme příkaz. Další informace o příkazech najdete v tématu [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Nabídky stylů  
 S stylů ovládacího prvku, můžete výrazně změnit vzhled a chování <xref:System.Windows.Controls.Menu> ovládacím prvkům bez nutnosti psaní vlastního ovládacího prvku. Kromě nastavení vizuálních vlastností, můžete také použít <xref:System.Windows.Style> na jednotlivé části ovládacího prvku změnit chování částí ovládacího prvku prostřednictvím vlastnosti, nebo přidání dalších částí nebo změna rozložení ovládacího prvku. Následující příklady ukazují několik způsobů, jak přidat <xref:System.Windows.Style> k <xref:System.Windows.Controls.Menu> ovládacího prvku.  
  
 V prvním příkladu kód definuje <xref:System.Windows.Style> názvem `Simple` který ukazuje, jak používat aktuální nastavení systému ve vašem stylu. Kód přiřadí barvu `MenuHighlightBrush` jako barva pozadí v nabídce a `MenuTextBrush` jako barvu popředí v nabídce. Všimněte si, můžete k přiřazení stopy použít klíčů prostředku.  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 Následující ukázkové používá <xref:System.Windows.Trigger> elementy, které vám umožní změnit vzhled <xref:System.Windows.Controls.MenuItem> v reakci na události na <xref:System.Windows.Controls.Menu>. Při přesunutí myši <xref:System.Windows.Controls.Menu>, barvu popředí a vlastnosti písma položek nabídky změnit.  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka galerie ovládacích prvků grafického subsystému WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
