---
title: "Přehled příkazů"
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
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1af7d9dba986c3775dc3625d1e7a874f6b26c97d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="commanding-overview"></a>Přehled příkazů
<a name="introduction"></a>Tvorba příkazů je mechanismus vstupní v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] která poskytuje vstup zpracování více sémantického úrovni, než zařízení vstup. Příklady příkazů **kopie**, **Vyjmout**, a **vložení** nalézt operace v mnoha aplikacích.  
  
 Tento přehled definuje, jaké příkazy jsou v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které třídy jsou součástí řídicího modelu a používání a vytvořit příkazy ve svých aplikacích.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Jaké jsou příkazy?](#commands_at_10000_feet)  
  
-   [Příklad jednoduchý příkaz v grafickém subsystému WPF](#simple_command)  
  
-   [Čtyři hlavní koncepty v tvorba příkazů WPF](#Four_main_Concepts)  
  
-   [Příkaz knihovny](#Command_Library)  
  
-   [Vytváření vlastních příkazů](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Jaké jsou příkazy?  
 Příkazy mají několik účely. První účelem je oddělit sémantiky a objekt, který volá příkaz z logiky, která spouští příkaz. To umožňuje více a různorodých zdrojů k vyvolání logice stejný příkaz a umožňuje logice příkaz k přizpůsobení pro různé cíle. Například úpravy operace **kopie**, **Vyjmout**, a **vložení**, které se nacházejí v mnoha aplikacích, lze vyvolat pomocí akcí jiného uživatele, pokud jsou implementovat pomocí příkazů. Aplikace může umožnit uživateli Vyjmout vybrané objekty nebo text. kliknutím tlačítko Vybrat položku v nabídce, nebo pomocí kombinace kláves, jako je například CTRL + X. Pomocí příkazů můžete vázat na stejné logiky, která každý typ akce uživatele.  
  
 Jiný účel příkazů je indikující, zda je k dispozici. Pokračujte příklad vyjmutím objektu nebo textu akce smysl pouze pokud je vybrána něco. Pokud se uživatel pokusí o vyjmout objektu nebo textu bez nutnosti nic vybrané, nic by mohlo dojít. Mnoho aplikací zakažte na tuto skutečnost oznámí uživateli, tlačítka a položky nabídky tak, že uživatel zná, zda je možné k provedení akce. Příkaz můžete určit, zda akci je možné implementací <xref:System.Windows.Input.ICommand.CanExecute%2A> metoda. Tlačítko mohou přihlásit k odběru <xref:System.Windows.Input.ICommand.CanExecuteChanged> událostí a k dispozici v případě <xref:System.Windows.Input.ICommand.CanExecute%2A> vrátí `false` nebo povolit, pokud <xref:System.Windows.Input.ICommand.CanExecute%2A> vrátí `true`.  
  
 Sémantika příkaz může být konzistentní v rámci aplikace a třídy, ale logiku akce je specifická pro konkrétní objekt reagovali na ni. Kombinace kláves CTRL + X vyvolá **Vyjmout** v textu třídy, třídy bitové kopie a webové prohlížeče, ale skutečný logiku pro provádění **Vyjmout** operaci je definována aplikace, která provádí vyjmutí. A <xref:System.Windows.Input.RoutedCommand> umožňuje klientům implementují logiku. Objekt text může vyjmout vybraný text do schránky, zatímco objekt image může vyjmout vybranou image. Když aplikace zpracovává <xref:System.Windows.Input.CommandManager.Executed> událostí, nemá přístup k cíli příkazu a moci provést vhodnou akci v závislosti na typu cílové složky.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Příklad jednoduchý příkaz v grafickém subsystému WPF  
 Nejjednodušší způsob, jak pomocí příkazu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , je použít i předdefinovanou <xref:System.Windows.Input.RoutedCommand> z jedné z knihovny tříd příkaz; používat ovládací prvek, který má nativní podpora pro zpracování příkazu; a používat ovládací prvek, který má nativní podporu pro vyvolání příkazu.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> Příkaz je jeden z předdefinovaných příkazů v <xref:System.Windows.Input.ApplicationCommands> třídy.  <xref:System.Windows.Controls.TextBox> Řízení má integrovaný logiku pro zpracování <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz.  A <xref:System.Windows.Controls.MenuItem> třída má nativní podporu pro vyvolání příkazů.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.MenuItem> tak, že když po kliknutí na bude vyvolán <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz na <xref:System.Windows.Controls.TextBox>, v případě <xref:System.Windows.Controls.TextBox> má fokus klávesnice.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Čtyři hlavní koncepty v tvorba příkazů WPF  
 Model směrované příkaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lze rozdělit do čtyř hlavní koncepty: příkaz, příkaz zdroj, cílem příkazu a vazba příkazu:  
  
-   *Příkaz* je akce, která má být proveden.  
  
-   *Příkaz zdroj* je pro objekt, který volá příkaz.  
  
-   *Cíl příkazu* je objekt, který se spouští na příkaz.  
  
-   *Příkaz vazby* je objekt, který mapuje logice příkaz k příkazu.  
  
 V předchozím příkladu <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz je příkaz, <xref:System.Windows.Controls.MenuItem> je zdrojem příkaz <xref:System.Windows.Controls.TextBox> je cílem příkazu a poskytl vazba příkazu <xref:System.Windows.Controls.TextBox> ovládací prvek.  Je vhodné poznamenat, že není vždy tento případ, <xref:System.Windows.Input.CommandBinding> poskytl ovládací prvek, který je příkaz cílové třídy.  Velmi často <xref:System.Windows.Input.CommandBinding> musí vytvořit vývojář aplikace nebo <xref:System.Windows.Input.CommandBinding> může být připojené k nadřazeným příkaz cíle.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Příkazy  
 Příkazy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou vytvořené pomocí implementace <xref:System.Windows.Input.ICommand> rozhraní.  <xref:System.Windows.Input.ICommand>poskytuje dvě metody, <xref:System.Windows.Input.ICommand.Execute%2A>, a <xref:System.Windows.Input.ICommand.CanExecute%2A>a událost, <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A>provede akce, které jsou spojeny pomocí příkazu. <xref:System.Windows.Input.ICommand.CanExecute%2A>Určuje, zda příkaz můžete spustit na aktuální příkaz cíl. <xref:System.Windows.Input.ICommand.CanExecuteChanged>je vyvolána správce příkaz, který centralizuje řídicího operace zjistí změnu v příkazu zdroji, které mohou zneplatnit příkaz, který byla vyvolána, ale ještě nebyla provedený vazba příkazu.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Implementace <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand> třídy a je hlavním cílem tohoto přehledu.  
  
 Hlavní zdroje vstupu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou myši, klávesnice, rukopisu a směrované příkazy.  Vstupy více orientovaný na zařízení používat <xref:System.Windows.RoutedEvent> oznámit objekty v stránku aplikace, která je vstupní události.  A <xref:System.Windows.Input.RoutedCommand> se neliší.  <xref:System.Windows.Input.RoutedCommand.Execute%2A> a <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody <xref:System.Windows.Input.RoutedCommand> neobsahují aplikační logiku pro příkaz, ale spíš vyvolávání událostí směrované tunelového propojení a předána prostřednictvím stromu element, dokud narazí objekt s <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> Obsahuje obslužné rutiny pro tyto události a je obslužných rutin, které k provedení příkazu.  Další informace o události směrování v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A> Metodu <xref:System.Windows.Input.RoutedCommand> vyvolá <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> události na cíli příkazu.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> Metodu <xref:System.Windows.Input.RoutedCommand> vyvolá <xref:System.Windows.Input.CommandManager.CanExecute> a <xref:System.Windows.Input.CommandManager.PreviewCanExecute> události na cíli příkazu.  Tyto události tunelu a bublin prostřednictvím stromu element dokud narazí, k objektu, který má <xref:System.Windows.Input.CommandBinding> pro tuto konkrétní příkaz.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zdroje sadu běžných směrované příkazů rozloženy několik tříd: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, a <xref:System.Windows.Documents.EditingCommands>.  Tyto třídy skládat jenom z <xref:System.Windows.Input.RoutedCommand> objekty a není implementační logika příkazu.  Implementační logika odpovídá objektu, na kterém se spouští na příkaz.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Příkaz zdroje  
 Příkaz zdroj je pro objekt, který volá příkaz.  Příklady zdrojů příkaz <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, a <xref:System.Windows.Input.KeyGesture>.  
  
 Příkaz zdroje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obecně implementovat <xref:System.Windows.Input.ICommandSource> rozhraní.  
  
 <xref:System.Windows.Input.ICommandSource>Zpřístupní vlastnosti pro tři: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, a <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A>je příkaz provést při vyvolání příkazu zdroj.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>je objekt, na které se mají spustit příkaz.  Je vhodné poznamenat, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> vlastnost na <xref:System.Windows.Input.ICommandSource> se dá použít jenom když <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand>.  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastavený na <xref:System.Windows.Input.ICommandSource> a příslušného příkazu není <xref:System.Windows.Input.RoutedCommand>, cíl příkaz je ignorováno. Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> není nastaven, element s fokus klávesnice budou cílem příkazu.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>příkaz implementuje vlastní datový typ používaný k předávání informací obslužné rutiny.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Třídy implementující <xref:System.Windows.Input.ICommandSource> jsou <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, a <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, a <xref:System.Windows.Documents.Hyperlink> vyvolání příkazu při jsou kliknutí a uvádí <xref:System.Windows.Input.InputBinding> Vyvolá příkaz při <xref:System.Windows.Input.InputGesture> spojené s se provádí.  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.MenuItem> v <xref:System.Windows.Controls.ContextMenu> jako zdroj pro příkaz <xref:System.Windows.Input.ApplicationCommands.Properties%2A> příkaz.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Obvykle bude zdroj příkaz poslouchat <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> událostí.  Tato událost informuje zdroji příkaz, který možná změnil možnost provedení příkazu na cíli aktuální příkaz.  Příkaz zdroj může dotazovat aktuální stav <xref:System.Windows.Input.RoutedCommand> pomocí <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metoda.  Příkaz zdroj můžete pak sama deaktivuje Pokud nelze provést příkaz.  Příkladem je <xref:System.Windows.Controls.MenuItem> graying samotné si při nelze provést příkaz.  
  
 <xref:System.Windows.Input.InputGesture> Lze použít jako zdroj příkaz.  Dva typy vstupní gesta v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.MouseGesture>.  Si můžete představit <xref:System.Windows.Input.KeyGesture> jako klávesové zkratky, jako je například CTRL + C.  A <xref:System.Windows.Input.KeyGesture> se skládá z <xref:System.Windows.Input.Key> a sadu <xref:System.Windows.Input.ModifierKeys>.  A <xref:System.Windows.Input.MouseGesture> se skládá z <xref:System.Windows.Input.MouseAction> a volitelná sada <xref:System.Windows.Input.ModifierKeys>.  
  
 Aby <xref:System.Windows.Input.InputGesture> tak, aby fungoval jako příkaz zdroj, musí být přidružený příkaz. Existuje několik způsobů, jak dosáhnout.  Dá se použít <xref:System.Windows.Input.InputBinding>.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.KeyBinding> mezi <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Jiný způsob, jak přiřadit <xref:System.Windows.Input.InputGesture> k <xref:System.Windows.Input.RoutedCommand> je přidání <xref:System.Windows.Input.InputGesture> k <xref:System.Windows.Input.InputGestureCollection> na <xref:System.Windows.Input.RoutedCommand>.  
  
 Následující příklad ukazuje, jak přidat <xref:System.Windows.Input.KeyGesture> k <xref:System.Windows.Input.InputGestureCollection> z <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> přidruží příkaz obslužné rutiny událostí, které implementují příkaz.  
  
 <xref:System.Windows.Input.CommandBinding> Třída obsahuje <xref:System.Windows.Input.CommandBinding.Command%2A> vlastnost, a <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, a <xref:System.Windows.Input.CommandBinding.CanExecute> události.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>obsahuje příkaz, který <xref:System.Windows.Input.CommandBinding> je bylo možné přidružit.  Obslužné rutiny událostí, které jsou připojené k <xref:System.Windows.Input.CommandBinding.PreviewExecuted> a <xref:System.Windows.Input.CommandBinding.Executed> události implementovat logiku příkaz.  Obslužné rutiny událostí připojené k <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> a <xref:System.Windows.Input.CommandBinding.CanExecute> události určit, pokud příkaz můžete spustit na aktuální příkaz cíl.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.CommandBinding> v kořenovém <xref:System.Windows.Window> aplikace.  <xref:System.Windows.Input.CommandBinding> Přidruží <xref:System.Windows.Input.ApplicationCommands.Open%2A> s <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> obslužné rutiny.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Dále <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> se vytvářejí.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Otevře <xref:System.Windows.MessageBox> který zobrazí řetězec informacemi o tom, provedení příkazu.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Nastaví <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> vlastnost `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> je připojený k určitému objektu, například kořenu <xref:System.Windows.Window> aplikace nebo ovládacího prvku.  Objekt, <xref:System.Windows.Input.CommandBinding> je připojen k definuje rozsah vazby.  Například <xref:System.Windows.Input.CommandBinding> připojen k nadřazenému prvku příkazu cíl dosažitelný z <xref:System.Windows.Input.CommandBinding.Executed> událostí, ale <xref:System.Windows.Input.CommandBinding> připojené k následníka příkazu není dosažitelný cíl.  Toto je přímým důsledkem toho, jak <xref:System.Windows.RoutedEvent> tunely a bublinách z objektu, který vyvolává událost.  
  
 V některých případech <xref:System.Windows.Input.CommandBinding> je připojené k cíli příkaz samostatně, například s <xref:System.Windows.Controls.TextBox> třídy a <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, a <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkazy. Je velmi často ale pohodlnější připojit <xref:System.Windows.Input.CommandBinding> k nadřazenému prvku příkaz cíle, jako je například hlavní <xref:System.Windows.Window> nebo objekt aplikace obzvláště pokud se stejná <xref:System.Windows.Input.CommandBinding> lze použít pro více cílů příkaz.  Jedná se o rozhodnutí, která můžete zvážit při vytváření řídicího infrastruktury.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Příkaz cíl  
 Cíl příkazu je element, na kterém je spuštěn příkaz.  S ohledem na <xref:System.Windows.Input.RoutedCommand>, cíl příkazu je element v které směrování <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandManager.CanExecute> spustí.  Uvedené jako dříve, v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> vlastnost <xref:System.Windows.Input.ICommandSource> je k dispozici jenom při <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand>.  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastavený na <xref:System.Windows.Input.ICommandSource> a příslušného příkazu není <xref:System.Windows.Input.RoutedCommand>, cíl příkaz je ignorováno.  
  
 Cíl příkazu můžete nastavit explicitně zdroj příkazu.  Pokud příkaz cíl není definován, element s fokus klávesnice se použije jako cíl příkazu.  Jednou z výhod pomocí elementu fokus klávesnice jako cíl příkazu je, že umožňuje vývojáři aplikace používaly stejný zdroj příkaz k vyvolání příkazu na více cílů bez nutnosti ke sledování cíl příkazu.  Například pokud <xref:System.Windows.Controls.MenuItem> vyvolá **vložení** příkazu v aplikaci, která má <xref:System.Windows.Controls.TextBox> řízení a <xref:System.Windows.Controls.PasswordBox> řízení, cílem může být buď <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.PasswordBox> podle toho, která ovládací prvek má fokus klávesnice.  
  
 Následující příklad ukazuje, jak explicitně nastavit cíl příkazu v značek a kódu na pozadí.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager> Funkcí souvisejících s slouží a počet příkaz.  Poskytuje sadu statické metody pro přidávání a odebírání <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, a <xref:System.Windows.Input.CommandManager.CanExecute> obslužné rutiny událostí do a z určitého prvku.  Poskytuje způsob registrace <xref:System.Windows.Input.CommandBinding> a <xref:System.Windows.Input.InputBinding> objekty do určité třídy.  <xref:System.Windows.Input.CommandManager> Poskytuje i prostředky, pomocí <xref:System.Windows.Input.CommandManager.RequerySuggested> událostí, které oznámí by měla vyvolat příkaz <xref:System.Windows.Input.ICommand.CanExecuteChanged> událostí.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> Metoda vynutí <xref:System.Windows.Input.CommandManager> zvýšit <xref:System.Windows.Input.CommandManager.RequerySuggested> událostí.  To je užitečné pro podmínky, které by měl zapnout/vypnout příkaz ale nejsou podmínky, které <xref:System.Windows.Input.CommandManager> známa.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Příkaz knihovny  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje sadu předdefinovaných příkazů.  Příkaz knihovny se skládá z následujících tříd: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>a <xref:System.Windows.Input.ComponentCommands>.  Tyto třídy poskytují příkazy, jako <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> a <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, a <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Mnoho z těchto příkazů obsahovat sadu výchozí vstupní vazby.  Například pokud určíte, že vaše aplikace zpracovává příkaz Kopírovat, automaticky získáte klávesnice vazby "CTRL + C" získáte vazby pro další vstupní zařízení, jako například [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] pera gesta a řeči informace.  
  
 Při odkazu na příkazy v různých příkaz knihoven pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], obvykle můžete vynechat název třídy třídy knihovny, která zpřístupňuje vlastnost statické příkazu. Obecně platí jsou názvy příkazů jednoznačné jako řetězce a vlastnícím typy existují zajistit logické seskupení příkazy, ale nejsou nutné pro rozlišení více tras. Například můžete zadat `Command="Cut"` místo více podrobné `Command="ApplicationCommands.Cut"`. Toto je užitečný mechanismus, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru pro příkazy (přesněji řečeno, je chování typu převaděč <xref:System.Windows.Input.ICommand>, což [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odkazy na procesor při načítání,).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Vytváření vlastních příkazů  
 Pokud se příkazy ve třídách knihovny příkaz nevyhovuje vašim potřebám, můžete vytvořit vlastní příkazy.  Existují dva způsoby vytvoření vlastního příkazu.  První je spuštění od základů a implementovat <xref:System.Windows.Input.ICommand> rozhraní.  Druhý způsob a častější přístup, je vytvoření <xref:System.Windows.Input.RoutedCommand> nebo <xref:System.Windows.Input.RoutedUICommand>.  
  
 Pro příklad vytvoření vlastní <xref:System.Windows.Input.RoutedCommand>, najdete v části [vytvořit vlastní vzorek RoutedCommand](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Implementace rozhraní ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [Postupy: přidání příkazu do MenuItem](http://msdn.microsoft.com/en-us/013d68a0-5373-4a68-bd91-5de574307370)  
 [Vytvořit vlastní RoutedCommand vzorek](http://go.microsoft.com/fwlink/?LinkID=159980)
