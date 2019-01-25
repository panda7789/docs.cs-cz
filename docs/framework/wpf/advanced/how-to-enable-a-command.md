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
ms.openlocfilehash: 904d5a3404b693c383731eda01e9e43b2d5126fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622062"
---
# <a name="how-to-enable-a-command"></a>Postupy: Povolení příkazu
Následující příklad ukazuje, jak pomocí příkazů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Tento příklad ukazuje, jak přidružit <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Button>, vytvořit <xref:System.Windows.Input.CommandBinding>a vytváření obslužných rutin událostí, které implementují <xref:System.Windows.Input.RoutedCommand>.  Další informace o příkazů najdete v tématu [přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Příklad  
 První část kódu vytvoří [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], který se skládá <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.StackPanel>a vytvoří <xref:System.Windows.Input.CommandBinding> , která přidruží obslužné rutiny příkazů s <xref:System.Windows.Input.RoutedCommand>.  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A> Vlastnost <xref:System.Windows.Controls.Button> je přidružený <xref:System.Windows.Input.ApplicationCommands.Close%2A> příkazu.  
  
 <xref:System.Windows.Input.CommandBinding> Se přidá do <xref:System.Windows.Input.CommandBindingCollection> kořenové <xref:System.Windows.Window>. <xref:System.Windows.Input.CommandBinding.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> obslužné rutiny událostí jsou připojené k této vazbě a přidružené <xref:System.Windows.Input.ApplicationCommands.Close%2A> příkazu.  
  
 Bez <xref:System.Windows.Input.CommandBinding> neexistuje žádný příkaz logiku, pouze mechanismus k vyvolání příkazu.  Když <xref:System.Windows.Controls.Button> dojde ke kliknutí na, <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> je vyvoláno na daném cíli příkazu, za nímž následuje <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Tyto události procházení stromu element hledání <xref:System.Windows.Input.CommandBinding> pro s konkrétním příkazem.  Je vhodné poznamenat, protože <xref:System.Windows.RoutedEvent> tunelového propojení a bubliny prostřednictvím stromem prvků, musí věnovat pozornost tam, kde <xref:System.Windows.Input.CommandBinding> bude umístěn.   Pokud <xref:System.Windows.Input.CommandBinding> je na daném cíli příkazu nebo jiný uzel, který se nenachází na trasu na stejné úrovni <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> nebude přístupná.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 V další části kód implementuje <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> obslužných rutin událostí.  
  
 <xref:System.Windows.Input.CommandManager.Executed> Obslužná rutina zavolá metodu zavřete otevřít soubor.  <xref:System.Windows.Input.CommandBinding.CanExecute> Obslužná rutina zavolá metodu pro určení, zda je soubor otevřen.  Pokud je soubor otevřen, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> je nastavena na `true`; v opačném případě je nastavený na `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled příkazů](../../../../docs/framework/wpf/advanced/commanding-overview.md)
