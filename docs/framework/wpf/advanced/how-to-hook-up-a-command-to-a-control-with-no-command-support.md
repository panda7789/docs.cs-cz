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
ms.openlocfilehash: 3ae45c9a9e33a3cb53ada6e1e5430ae0f9e6c198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "71263296"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Postupy: Propojení příkazu s ovládacím prvkem bez podpory příkazů
Následující příklad ukazuje, jak připojit <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Controls.Control> k rozhraní, které nemá integrovanou podporu pro příkaz.  Úplný příklad, který zastavuje příkazy na více zdrojů, naleznete v [ukázce Sample Sample pro vytvoření vlastní RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) .  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje knihovnu běžných příkazů, které programátorům aplikací často vyskytnout.  Třídy, které tvoří knihovnu příkazů, jsou: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>a <xref:System.Windows.Documents.EditingCommands>.  
  
 Statické <xref:System.Windows.Input.RoutedCommand> objekty, které tvoří tyto třídy, neposkytují příkazovou logiku.  Logika pro příkaz je přidružena k příkazu s <xref:System.Windows.Input.CommandBinding>.  Mnoho ovládacích prvků [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v nástroji obsahuje integrovanou podporu některých příkazů v knihovně příkazů.  <xref:System.Windows.Controls.TextBox>například podporuje mnoho příkazů <xref:System.Windows.Input.ApplicationCommands.Paste%2A>pro úpravu aplikace, jako například, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>a <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Aby se tyto příkazy při práci s těmito ovládacími prvky nemusely provádět, vývojář aplikace nemusí provádět žádné zvláštní akce.  Pokud je cílem příkazu při spuštění příkazu, zpracuje příkaz <xref:System.Windows.Input.CommandBinding> pomocí ovládacího prvku, který je integrován do ovládacího prvku. <xref:System.Windows.Controls.TextBox>  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Controls.Button> jako zdroj příkazu <xref:System.Windows.Input.ApplicationCommands.Open%2A> pro příkaz.  Vytvoří <xref:System.Windows.Input.CommandBinding> se, který přidruží zadané <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> <xref:System.Windows.Input.RoutedCommand>k.  
  
 Nejprve se vytvoří zdroj příkazů.  Jako zdroj příkazu se používá. <xref:System.Windows.Controls.Button>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Dále jsou<xref:System.Windows.Input.CanExecuteRoutedEventHandler> vytvořeny a.<xref:System.Windows.Input.ExecutedRoutedEventHandler>  Jednoduše se otevře a <xref:System.Windows.MessageBox> značí, že se příkaz provedl. <xref:System.Windows.Input.ExecutedRoutedEventHandler>  Nastaví vlastnost na`true`hodnotu. <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> <xref:System.Windows.Input.CanExecuteRoutedEventHandler>  V normálním případě může obslužná rutina Execute provést robustnější kontroly, aby bylo možné zjistit, zda se příkaz v aktuálním cíli příkazu spustil.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Nakonec se vytvoří v kořenovém adresáři <xref:System.Windows.Window> aplikace, který přidruží obslužné rutiny <xref:System.Windows.Input.ApplicationCommands.Open%2A> směrovaných událostí k příkazu. <xref:System.Windows.Input.CommandBinding>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled příkazů](commanding-overview.md)
- [Propojení příkazu s ovládacím prvkem s podporou příkazů](how-to-hook-up-a-command-to-a-control-with-command-support.md)
