---
title: 'Postupy: Propojení příkazu s ovládacím prvkem s podporou příkazů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
ms.openlocfilehash: 981fecf33b60c76ecab760185db7dab4bbb254d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757245"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Postupy: Propojení příkazu s ovládacím prvkem s podporou příkazů
Následující příklad ukazuje, jak k připojení <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Control> které má integrované v podpoře pro příkaz.  Kompletní příklad, který zachytí příkazy do více zdrojů, najdete v článku [vytvořením ukázkového routedcommand – vlastní](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) vzorku.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje knihovnu běžných příkazů, které potkávají programátory aplikace pravidelně.  Třídy, které tvoří knihovnu příkazu jsou: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, a <xref:System.Windows.Documents.EditingCommands>.  
  
 Statické <xref:System.Windows.Input.RoutedCommand> objekty, které tvoří tyto třídy nezadávejte příkaz logiku.  Logika pro příkaz je přidružený příkaz s <xref:System.Windows.Input.CommandBinding>.  Některé ovládací prvky vytvořili CommandBindings pro některé příkazy.  Tento mechanismus umožňuje sémantiku příkaz zůstane stejná, zatímco se skutečná implementace může změnit.  A <xref:System.Windows.Controls.TextBox>, například zpracovává <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz jinak než ovládací prvek slouží k podpoře imagí, ale základní představu, co to znamená vložení položky zůstala stejná.  Příkaz logiky nelze zadat v příkazu, ale místo toho je nutné zadat ovládací prvek nebo aplikace.  
  
 Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít vestavěnou podporou pro některé příkazy v příkazu knihovny.  <xref:System.Windows.Controls.TextBox>, například řadu příkazů, úpravy aplikace, jako podporuje <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, a <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Vývojář aplikace nemusí provádět žádné zvláštní, chcete-li získat tyto příkazy pro práci s těmito ovládacími prvky.  Pokud <xref:System.Windows.Controls.TextBox> je cíl příkazu při spuštění příkazu bude zpracovávat pomocí příkazu <xref:System.Windows.Input.CommandBinding> , která je integrovaná do ovládacího prvku.  
  
 Následující ukazuje způsob použití <xref:System.Windows.Controls.MenuItem> jako zdroj příkaz <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz, kde <xref:System.Windows.Controls.TextBox> je cíl příkazu.  Veškerou logiku, která definuje způsob, jakým <xref:System.Windows.Controls.TextBox> provádí vkládání je integrovaná do <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
 A <xref:System.Windows.Controls.MenuItem> se vytvoří a je <xref:System.Windows.Controls.MenuItem.Command%2A> je nastavena na <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkazu.  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> Není explicitně nastavena na hodnotu <xref:System.Windows.Controls.TextBox> objektu.  Když <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> není nastavena, cíl pro příkaz je element, který má fokus klávesnice.  Pokud se nepodporuje element, který má klávesnice fokus <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz % $n nebo nelze aktuálně provést příkaz Vložit (schránky je prázdný, například) pak bude <xref:System.Windows.Controls.MenuItem> by být zobrazena šedě.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled příkazů](commanding-overview.md)
- [Propojení příkazu s ovládacím prvkem bez podpory příkazů](how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
