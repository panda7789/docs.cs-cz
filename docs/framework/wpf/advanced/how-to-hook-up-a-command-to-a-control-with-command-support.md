---
title: 'Postupy: Připojení příkazu k ovládacímu prvku pomocí podpory příkazů'
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
ms.openlocfilehash: 22aca20eb3f6bc2e31fb5a01ed7c153cccef0bd8
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805432"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>Postupy: Připojení příkazu k ovládacímu prvku pomocí podpory příkazů
Následující příklad ukazuje, jak spojit <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Control> které má integrovanou podporu pro příkaz.  Kompletní příklad, který zachytí až příkazů pro více zdrojů, najdete v článku [vytvořit vlastní vzorek RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) ukázka.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje knihovnu běžných příkazů, které pravidelně dojde programátorům aplikací.  Jsou třídy, které tvoří příkaz knihovny: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, a <xref:System.Windows.Documents.EditingCommands>.  
  
 Statické <xref:System.Windows.Input.RoutedCommand> objekty, které tvoří tyto třídy nezadávejte příkaz logiku.  Příkaz s přidružen logiku pro příkaz <xref:System.Windows.Input.CommandBinding>.  Některé ovládací prvky jste vytvořili v CommandBindings pro některé příkazy.  Tento mechanismus umožňuje sémantika příkaz zůstane stejná, zatímco Skutečná implementace je můžete změnit.  A <xref:System.Windows.Controls.TextBox>, například zpracovává <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz jinak než ovládacího prvku navržena k podpoře bitové kopie, ale základní představu o tom, co znamená něco vložit zůstává stejný.  Příkaz logiku nelze zadat příkaz, ale spíš musí zadat pomocí ovládacího prvku nebo v aplikaci.  
  
 Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít vestavěnou podporou pro některé příkazy v knihovně příkaz.  <xref:System.Windows.Controls.TextBox>, například podporuje mnoho příkazů úpravy aplikací, jako <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, a <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Vývojář aplikace nemá žádnou zvláštní získat tyto příkazy pro práci s tyto ovládací prvky.  Pokud <xref:System.Windows.Controls.TextBox> je cílem příkazu po provedení příkazu je bude zpracovávat pomocí příkazu <xref:System.Windows.Input.CommandBinding> , je integrovaná do ovládacího prvku.  
  
 Následující ukazuje způsob použití <xref:System.Windows.Controls.MenuItem> jako zdroj pro příkaz <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz, kde <xref:System.Windows.Controls.TextBox> je cílem příkazu.  Veškerou logiku, která definuje jak <xref:System.Windows.Controls.TextBox> provádí vložení je integrovaná do <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
 A <xref:System.Windows.Controls.MenuItem> je vytvořen a je <xref:System.Windows.Controls.MenuItem.Command%2A> je nastavena na <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz.  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> Není explicitně nastaven na <xref:System.Windows.Controls.TextBox> objektu.  Když <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> není nastavena, cíl pro příkaz je element, který má fokus klávesnice.  Pokud element, který má fokus klávesnice nepodporuje <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz nebo aktuálně nelze provést příkaz Vložit (schránky je prázdná, například) potom <xref:System.Windows.Controls.MenuItem> by být zobrazena šedě.  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Propojení příkazu s ovládacím prvkem bez podpory příkazů](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
