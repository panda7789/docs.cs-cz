---
title: 'Postupy: Povolení příkazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: 81ae2e46c4fdd8b46e2b72b9a1430437ebfe97b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-a-command"></a>Postupy: Povolení příkazu
Následující příklad ukazuje, jak používat tvorba příkazů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Tento příklad ukazuje, jak přidružit <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Button>, vytvoření <xref:System.Windows.Input.CommandBinding>a vytváření obslužných rutin událostí, které implementují třídu <xref:System.Windows.Input.RoutedCommand>.  Další informace o tvorba příkazů najdete v tématu [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Příklad  
 První část kód vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], který se skládá z <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.StackPanel>a vytvoří <xref:System.Windows.Input.CommandBinding> který přidruží obslužné rutiny příkazů s <xref:System.Windows.Input.RoutedCommand>.  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A> Vlastnost <xref:System.Windows.Controls.Button> přidružen <xref:System.Windows.Input.ApplicationCommands.Close%2A> příkaz.  
  
 <xref:System.Windows.Input.CommandBinding> Je přidán do <xref:System.Windows.Input.CommandBindingCollection> kořenové <xref:System.Windows.Window>. <xref:System.Windows.Input.CommandBinding.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> jsou připojené k této vazbě a přidružené obslužné rutiny událostí <xref:System.Windows.Input.ApplicationCommands.Close%2A> příkaz.  
  
 Bez <xref:System.Windows.Input.CommandBinding> neexistuje žádný příkaz logiku, pouze mechanismus pro vyvolání příkazu.  Když <xref:System.Windows.Controls.Button> po kliknutí na <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> se vyvolá při cíl příkazu následuje <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Tyto události procházení stromu element hledání <xref:System.Windows.Input.CommandBinding> pro tuto konkrétní příkaz.  Stojí za zmínku, že <xref:System.Windows.RoutedEvent> tunelové propojení a bublin prostřednictvím stromu element musí dát pozor tam, kde <xref:System.Windows.Input.CommandBinding> je.   Pokud <xref:System.Windows.Input.CommandBinding> je na stejné úrovni jako cíl příkazu nebo jiného uzlu, který se nenachází na trasa <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> nebude přístupná.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 V další části kódu implementuje <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> obslužné rutiny událostí.  
  
 <xref:System.Windows.Input.CommandManager.Executed> Události volá metodu zavřete otevření souboru.  <xref:System.Windows.Input.CommandBinding.CanExecute> Události volá metodu k určení, zda je soubor otevřený.  Pokud je soubor otevřený <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> je nastaven na `true`, jinak je nastaven na hodnotu `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)
