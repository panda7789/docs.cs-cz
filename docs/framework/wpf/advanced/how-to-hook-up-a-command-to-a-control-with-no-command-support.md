---
title: "Postupy: Propojení příkazu s ovládacím prvkem bez podpory příkazů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f38a6f900ee2b253708da4b63bdc2f474fa3ab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Postupy: Propojení příkazu s ovládacím prvkem bez podpory příkazů
Následující příklad ukazuje, jak spojit <xref:System.Windows.Input.RoutedCommand> k <xref:System.Windows.Controls.Control> které není mít vestavěnou podporou pro příkaz.  Kompletní příklad, který zachytí až příkazů pro více zdrojů, najdete v článku [vytvořit vlastní vzorek RoutedCommand](http://go.microsoft.com/fwlink/?LinkID=159980) ukázka.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje knihovnu běžných příkazů, které pravidelně dojde programátorům aplikací.  Jsou třídy, které tvoří příkaz knihovny: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, a <xref:System.Windows.Documents.EditingCommands>.  
  
 Statické <xref:System.Windows.Input.RoutedCommand> objekty, které tvoří tyto třídy nezadávejte příkaz logiku.  Příkaz s přidružen logiku pro příkaz <xref:System.Windows.Input.CommandBinding>.  Mnoho ovládacích prvků v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít vestavěnou podporou pro některé příkazy v knihovně příkaz.  <xref:System.Windows.Controls.TextBox>, například podporuje mnoho příkazů úpravy aplikací, jako <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, a <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Vývojář aplikace nemá žádnou zvláštní získat tyto příkazy pro práci s tyto ovládací prvky.  Pokud <xref:System.Windows.Controls.TextBox> je cílem příkazu po provedení příkazu je bude zpracovávat pomocí příkazu <xref:System.Windows.Input.CommandBinding> , je integrovaná do ovládacího prvku.  
  
 Následující ukazuje způsob použití <xref:System.Windows.Controls.Button> jako zdroj pro příkaz <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz.  A <xref:System.Windows.Input.CommandBinding> se vytvoří tento partnerů zadaný <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> s <xref:System.Windows.Input.RoutedCommand>.  
  
 Nejprve je vytvořen zdroj příkazu.  A <xref:System.Windows.Controls.Button> slouží jako zdroj příkazu.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Dále <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> se vytvářejí.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Jednoduše otevře <xref:System.Windows.MessageBox> označuje, že příkaz provést.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Nastaví <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> vlastnost `true`.  Za normálních okolností může spustit obslužnou rutinu by provedl robustnější kontroluje, pokud příkaz může spustit na aktuální příkaz cíl.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Nakonec <xref:System.Windows.Input.CommandBinding> se vytvoří v kořenovém <xref:System.Windows.Window> aplikace, která přidruží obslužné rutiny události směrované na <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Viz také  
 [Tvorba příkazů – přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Propojte příkaz do ovládacího prvku s podporou příkaz](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
