---
title: 'Postupy: Propojení příkazu s ovládacím prvkem bez podpory příkazů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
ms.openlocfilehash: 66b371f4d67c1102ddf341dd4b70aac66aa41605
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352669"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Postupy: Propojení příkazu s ovládacím prvkem bez podpory příkazů
Následující příklad ukazuje, jak k připojení <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Control> které není mít vestavěnou podporou pro příkaz.  Kompletní příklad, který zachytí příkazy do více zdrojů, najdete v článku [vytvořením ukázkového routedcommand – vlastní](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) vzorku.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje knihovnu běžných příkazů, které potkávají programátory aplikace pravidelně.  Třídy, které tvoří knihovnu příkazu jsou: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, a <xref:System.Windows.Documents.EditingCommands>.  
  
 Statické <xref:System.Windows.Input.RoutedCommand> objekty, které tvoří tyto třídy nezadávejte příkaz logiku.  Logika pro příkaz je přidružený příkaz s <xref:System.Windows.Input.CommandBinding>.  Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít vestavěnou podporou pro některé příkazy v příkazu knihovny.  <xref:System.Windows.Controls.TextBox>, například řadu příkazů, úpravy aplikace, jako podporuje <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, a <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Vývojář aplikace nemusí provádět žádné zvláštní, chcete-li získat tyto příkazy pro práci s těmito ovládacími prvky.  Pokud <xref:System.Windows.Controls.TextBox> je cíl příkazu při spuštění příkazu bude zpracovávat pomocí příkazu <xref:System.Windows.Input.CommandBinding> , která je integrovaná do ovládacího prvku.  
  
 Následující znázorňuje způsob použití <xref:System.Windows.Controls.Button> jako zdroj příkaz <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz.  A <xref:System.Windows.Input.CommandBinding> vytvoření této přidruží zadaný <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> s <xref:System.Windows.Input.RoutedCommand>.  
  
 Nejprve se vytvoří zdroj příkazu.  A <xref:System.Windows.Controls.Button> slouží jako zdroj příkaz.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Dále <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> jsou vytvořeny.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Jednoduše otevře <xref:System.Windows.MessageBox> označuje, že příkaz provést.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Nastaví <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> vlastnost `true`.  Za normálních okolností může provést obslužnou rutinu by provádět robustnější kontroluje, pokud příkaz by mohl spustit na aktuálním cíli příkazu.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 A konečně <xref:System.Windows.Input.CommandBinding> se vytvoří v kořenovém adresáři <xref:System.Windows.Window> aplikace, která přidruží směrovaných událostí obslužné rutiny pro <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled příkazů](commanding-overview.md)
- [Propojení příkazu s ovládacím prvkem s podporou příkazů](how-to-hook-up-a-command-to-a-control-with-command-support.md)
