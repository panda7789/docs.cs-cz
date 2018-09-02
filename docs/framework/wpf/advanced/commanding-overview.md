---
title: Přehled příkazů
ms.date: 03/30/2017
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
ms.openlocfilehash: d41613ce2488fa572fa11def06350ab1e564df6c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467961"
---
# <a name="commanding-overview"></a>Přehled příkazů
<a name="introduction"></a> Příkazů je mechanismus vstupní v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytující vstupní zpracování více sémantických úrovni, než vstupní zařízení. Příklady příkazů **kopírování**, **Vyjmout**, a **vložit** nalézt operace v mnoha aplikacích.  
  
 Tento přehled definuje, co jsou příkazy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které třídy jsou součástí řídicího modelu a jak používat a vytvořit příkazy ve svých aplikacích.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Co jsou příkazy?](#commands_at_10000_feet)  
  
-   [Příklad jednoduchého příkazu v subsystému WPF](#simple_command)  
  
-   [Čtyři hlavní koncepty v WPF příkazů](#Four_main_Concepts)  
  
-   [Knihovna příkazů](#Command_Library)  
  
-   [Vytváření vlastních příkazů](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Co jsou příkazy?  
 Příkazy mají několik účely. První slouží k oddělení sémantika a objekt, který vyvolá příkaz od logiky, který se spustí příkaz. To umožňuje více a nesourodých zdrojů, který má být vyvolán stejnou logiku příkaz který umožňuje logiky příkaz přizpůsobit pro jiné cíle. Například operace úprav **kopírování**, **Vyjmout**, a **vložit**, které se nacházejí v mnoha aplikacích lze vyvolat pomocí akcí jiného uživatele, pokud jsou implementováno s použitím příkazů. Aplikace může umožnit uživatelům vyjmout vybraných objektů nebo textu buď klikněte na tlačítko, výběrem položky v nabídce nebo pomocí kombinace kláves, jako je například CTRL + X. Pomocí příkazů můžete vázat na stejnou logiku každého typu akce uživatele.  
  
 K určení, jestli je akce k dispozici je jiný účel příkazů. Pokračujte příklad vyjmutí objektu nebo textu akce má smysl jenom při. Pokud se uživatel pokusí o vyjmutí objektu nebo textu bez nutnosti nic vybrané, co by mohlo dojít. Mnoho aplikací zakázat do značí to, tlačítka a položky v nabídce tak, že uživatel zná, zda je možné provést akci. Příkaz můžete určit, zda akci je možné díky implementaci <xref:System.Windows.Input.ICommand.CanExecute%2A> metody. Tlačítko můžete přihlásit k odběru <xref:System.Windows.Input.ICommand.CanExecuteChanged> událostí a pokud zakázat <xref:System.Windows.Input.ICommand.CanExecute%2A> vrátí `false` nebo povolit, pokud jsou <xref:System.Windows.Input.ICommand.CanExecute%2A> vrátí `true`.  
  
 Sémantika příkaz může být konzistentní vzhledem k aplikacím napříč aplikacemi a třídy, ale logic akce je specifické pro konkrétní objekt reagovali na ni. Kombinace kláves CTRL + X vyvolá **Vyjmout** v textové třídy, bitové kopie třídy a webové prohlížeče, ale skutečný logiku pro provádění **Vyjmout** operace je definován aplikací, který provádí vyjmutí. A <xref:System.Windows.Input.RoutedCommand> umožňuje klientům implementovat logiku. Objekt textu může vyjmout vybraného textu do schránky, zatímco objektu image může Vyjme vybrané bitové kopie. Když aplikace zpracovává <xref:System.Windows.Input.CommandManager.Executed> událost, má přístup k cíli příkazu a moci provést vhodnou akci v závislosti na typu cíle.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Příklad jednoduchého příkazu v subsystému WPF  
 Nejjednodušší způsob, jak pomocí příkazu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , je použít i předdefinovanou <xref:System.Windows.Input.RoutedCommand> z jednoho z knihovny třídy příkazů; použít ovládací prvek, který má nativní podporu pro zpracování příkazu; a použít ovládací prvek, který má nativní podporu pro vyvolání příkazu.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> Příkaz je jeden z předdefinovaných příkazů v <xref:System.Windows.Input.ApplicationCommands> třídy.  <xref:System.Windows.Controls.TextBox> Ovládací prvek má integrované logiku pro zpracování <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkazu.  A <xref:System.Windows.Controls.MenuItem> třída má nativní podporu pro vyvolávání příkazů.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.MenuItem> tak, aby po kliknutí se vyvolá <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz <xref:System.Windows.Controls.TextBox>, předpokládá <xref:System.Windows.Controls.TextBox> má klávesnice fokus.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Čtyři hlavní koncepty v WPF příkazů  
 Model směrování příkazu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lze rozdělit do čtyř hlavních konceptech: příkaz, příkaz zdroj, cíl příkazu a vazba příkazu:  
  
-   *Příkaz* je akce, která má být proveden.  
  
-   *Zdroj příkazu* je objekt, který vyvolá příkaz.  
  
-   *Cíl příkazu* je objekt, který se na spuštění příkazu.  
  
-   *Příkaz vazby* je objekt, který mapuje logiky příkazu pro příkaz.  
  
 V předchozím příkladu <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz je příkaz, <xref:System.Windows.Controls.MenuItem> je zdrojem příkaz <xref:System.Windows.Controls.TextBox> je cíl příkazu a poskytl vazba příkazu <xref:System.Windows.Controls.TextBox> ovládacího prvku.  Je vhodné poznamenat, že není vždy případu, který <xref:System.Windows.Input.CommandBinding> je poskytnut pomocí ovládacího prvku, který je cílovou třídu příkazu.  Poměrně často <xref:System.Windows.Input.CommandBinding> musí vytvořit vývojář aplikace, nebo <xref:System.Windows.Input.CommandBinding> může připojit k nadřazena cíli příkazu.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Příkazy  
 Příkazy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou vytvořeny pomocí implementace <xref:System.Windows.Input.ICommand> rozhraní.  <xref:System.Windows.Input.ICommand> poskytuje dvě metody <xref:System.Windows.Input.ICommand.Execute%2A>, a <xref:System.Windows.Input.ICommand.CanExecute%2A>a události, <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A> provádí akce, které jsou spojeny s příkazu. <xref:System.Windows.Input.ICommand.CanExecute%2A> Určuje, zda lze příkaz provést na aktuálním cíli příkazu. <xref:System.Windows.Input.ICommand.CanExecuteChanged> je aktivována, pokud správce příkazů, které centralizuje řídicí operace zjistí změnu ve zdroji příkaz, který může zneplatnit příkazu, která byla vyvolána, ale dosud proveden příkaz vazbou.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Provádění <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand> třídy a je na tomto přehledu.  
  
 Hlavní zdroje vstupu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se ukazatel myši, klávesnice, inkoustu a směrování příkazů.  Používat vstupy více zařízení objektově orientovaný <xref:System.Windows.RoutedEvent> oznámit objekty na stránce aplikace, že vstupní události došlo.  A <xref:System.Windows.Input.RoutedCommand> se nijak neliší.  <xref:System.Windows.Input.RoutedCommand.Execute%2A> a <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody <xref:System.Windows.Input.RoutedCommand> neobsahují aplikační logiku pro příkaz, ale místo toho vyvolat směrované události, které vytvoří tunel a předána prostřednictvím stromem prvků, dokud narazí objekt se <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> Obsahuje rutiny pro tyto události a obslužné rutiny, které k provedení příkazu.  Další informace o směrování událostí ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [směrovat Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A> Metoda <xref:System.Windows.Input.RoutedCommand> vyvolá <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> události na daném cíli příkazu.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> Metoda <xref:System.Windows.Input.RoutedCommand> vyvolá <xref:System.Windows.Input.CommandManager.CanExecute> a <xref:System.Windows.Input.CommandManager.PreviewCanExecute> události na daném cíli příkazu.  Tyto události tunelové propojení a bubliny prostřednictvím stromem prvků, dokud nebude objekt, který má narazí <xref:System.Windows.Input.CommandBinding> pro s konkrétním příkazem.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje sadu běžných příkazů směrované rozděleny mezi několik tříd: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, a <xref:System.Windows.Documents.EditingCommands>.  Tyto třídy skládat jenom z <xref:System.Windows.Input.RoutedCommand> objekty a ne implementační logika příkazu.  Implementační logika zodpovídá za objekt, na kterém se na spuštění příkazu.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Příkaz zdroje  
 Příkaz zdroj je objekt, který vyvolá příkaz.  Příklady zdrojů příkaz <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, a <xref:System.Windows.Input.KeyGesture>.  
  
 Příkaz zdroje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obecně implementovat <xref:System.Windows.Input.ICommandSource> rozhraní.  
  
 <xref:System.Windows.Input.ICommandSource> Zpřístupní vlastnosti pro tři: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, a <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A> je příkaz provedený při vyvolání příkazu zdroje.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je objekt, který se má spustit příkaz.  Je vhodné poznamenat, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> vlastnost <xref:System.Windows.Input.ICommandSource> jde použít jenom při <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand>.  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastavena na <xref:System.Windows.Input.ICommandSource> a odpovídajícího příkazu není <xref:System.Windows.Input.RoutedCommand>, cíl příkazu se ignoruje. Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> není nastaven, element s fokus klávesnice bude cíli příkazu.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> implementuje uživatelsky definovaný datový typ používaný k předávání informací do obslužné rutiny příkazu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Třídy, které implementují <xref:System.Windows.Input.ICommandSource> jsou <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, a <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, a <xref:System.Windows.Documents.Hyperlink> vyvolat příkaz při kliknutí a vlastní <xref:System.Windows.Input.InputBinding> Vyvolá příkaz při <xref:System.Windows.Input.InputGesture> přidružené pomocí provádí.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.MenuItem> v <xref:System.Windows.Controls.ContextMenu> jako zdroj pro příkaz <xref:System.Windows.Input.ApplicationCommands.Properties%2A> příkazu.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Obvykle příkaz zdroj bude naslouchat <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> událostí.  Tato událost informuje zdroj příkazu, který se mohl změnit možnost příkazu ke spuštění na aktuálním cíli příkazu.  Zdroj příkazu můžete zadávat dotazy aktuální stav <xref:System.Windows.Input.RoutedCommand> pomocí <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody.  Zdroj příkazu můžete pak sama deaktivuje Pokud nelze provést příkaz.  Příkladem je <xref:System.Windows.Controls.MenuItem> graying samotné, když nelze provést příkaz.  
  
 <xref:System.Windows.Input.InputGesture> Může sloužit jako zdroj příkazu.  Dva druhy vstupní gesta v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.MouseGesture>.  Můžete si představit <xref:System.Windows.Input.KeyGesture> jako klávesové zkratky, jako je například CTRL + C.  A <xref:System.Windows.Input.KeyGesture> se skládá z <xref:System.Windows.Input.Key> a sadu <xref:System.Windows.Input.ModifierKeys>.  A <xref:System.Windows.Input.MouseGesture> se skládá z <xref:System.Windows.Input.MouseAction> a volitelná sada <xref:System.Windows.Input.ModifierKeys>.  
  
 Aby se <xref:System.Windows.Input.InputGesture> tak, aby fungoval jako zdroj příkaz, musí být přidružený příkaz. Existuje několik způsobů, jak to provést.  Jedním ze způsobů je použít <xref:System.Windows.Input.InputBinding>.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.KeyBinding> mezi <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Dalším způsobem, jak přidružit <xref:System.Windows.Input.InputGesture> k <xref:System.Windows.Input.RoutedCommand> je přidání <xref:System.Windows.Input.InputGesture> k <xref:System.Windows.Input.InputGestureCollection> na <xref:System.Windows.Input.RoutedCommand>.  
  
 Následující příklad ukazuje, jak přidat <xref:System.Windows.Input.KeyGesture> k <xref:System.Windows.Input.InputGestureCollection> z <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> příkaz přidruží obslužné rutiny událostí, které implementují příkazu.  
  
 <xref:System.Windows.Input.CommandBinding> Obsahuje třídy <xref:System.Windows.Input.CommandBinding.Command%2A> vlastnost, a <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, a <xref:System.Windows.Input.CommandBinding.CanExecute> události.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> je příkaz, který <xref:System.Windows.Input.CommandBinding> je bylo možné přidružit.  Obslužné rutiny událostí, které jsou připojeny k <xref:System.Windows.Input.CommandBinding.PreviewExecuted> a <xref:System.Windows.Input.CommandBinding.Executed> události implementovat logiku příkazu.  Obslužné rutiny událostí připojené k <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> a <xref:System.Windows.Input.CommandBinding.CanExecute> události určit, pokud příkaz můžete spustit na aktuálním cíli příkazu.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.CommandBinding> v kořenovém adresáři <xref:System.Windows.Window> aplikace.  <xref:System.Windows.Input.CommandBinding> Přidruží <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute> obslužné rutiny.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Dále <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> jsou vytvořeny.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Otevře <xref:System.Windows.MessageBox> , který zobrazí řetězec říká byl proveden příkaz.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Nastaví <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> vlastnost `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> je připojený k určitému objektu, jako je například kořenovou <xref:System.Windows.Window> aplikace nebo ovládacího prvku.  Objekt, který <xref:System.Windows.Input.CommandBinding> je připojen k definuje rozsah vazby.  Například <xref:System.Windows.Input.CommandBinding> připojen k nadřazenému prvku příkazu cíl dosažitelný z <xref:System.Windows.Input.CommandBinding.Executed> události, ale <xref:System.Windows.Input.CommandBinding> připojené k potomkem příkazu není dostupný cílový.  Toto je v přímém důsledku tak, jak <xref:System.Windows.RoutedEvent> tunely a bubliny z objektu, která vyvolává událost.  
  
 V některých situacích <xref:System.Windows.Input.CommandBinding> je připojen k cíli příkazu, například s <xref:System.Windows.Controls.TextBox> třídy a <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, a <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkazy. Poměrně často ale je snazší připojit <xref:System.Windows.Input.CommandBinding> k nadřazena cíli příkazu, jako je hlavní <xref:System.Windows.Window> nebo objekt aplikace, zejména v případě stejné <xref:System.Windows.Input.CommandBinding> lze použít pro více cíle příkazů.  Jedná se o rozhodnutí o návrhu, které můžete zvážit při vytváření řídicího infrastruktury.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Cíl příkazu  
 Cíl příkazu je prvek, na kterém je spuštěn příkaz.  S ohledem na <xref:System.Windows.Input.RoutedCommand>, cíl příkazu je element v které směrování <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandManager.CanExecute> spustí.  Co jsou uvedené dříve v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> vlastnost <xref:System.Windows.Input.ICommandSource> jde použít jenom při <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand>.  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastavena na <xref:System.Windows.Input.ICommandSource> a odpovídajícího příkazu není <xref:System.Windows.Input.RoutedCommand>, cíl příkazu se ignoruje.  
  
 Zdroj příkazu můžete explicitně nastavit cíl příkazu.  Pokud cíl příkazu není definován, použije se element s fokus klávesnice jako cíl příkazu.  Jednou z výhod pomocí elementu fokus klávesnice jako cíl příkazu je, že umožňuje vývojáři aplikace používaly stejný zdroj příkaz pro spuštění příkazu na více cílů, aniž byste museli udržovat přehled o daném cíli příkazu.  Například pokud <xref:System.Windows.Controls.MenuItem> vyvolá **vložit** v aplikaci, která se má příkaz <xref:System.Windows.Controls.TextBox> ovládacího prvku a <xref:System.Windows.Controls.PasswordBox> ovládací prvek, cíl může být buď <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.PasswordBox> podle toho, která ovládací prvek má fokus klávesnice.  
  
 Následující příklad ukazuje, jak v kódu a v kódu explicitně nastavit cíl příkazu.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager> Slouží celou řadu příkaz související funkce.  Poskytuje sadu statické metody pro přidávání a odebírání <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, a <xref:System.Windows.Input.CommandManager.CanExecute> obslužných rutin událostí do a z konkrétní elementu.  Poskytuje prostředky k registraci <xref:System.Windows.Input.CommandBinding> a <xref:System.Windows.Input.InputBinding> objektů do určité třídy.  <xref:System.Windows.Input.CommandManager> Také poskytuje způsob, až <xref:System.Windows.Input.CommandManager.RequerySuggested> události, které oznámí by měla vyvolat příkaz <xref:System.Windows.Input.ICommand.CanExecuteChanged> událostí.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> Metoda sil <xref:System.Windows.Input.CommandManager> zvýšit <xref:System.Windows.Input.CommandManager.RequerySuggested> událostí.  To je užitečné pro podmínky, které by měl zakázat nebo povolit příkaz ale nejsou podmínky, které <xref:System.Windows.Input.CommandManager> zná.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Knihovna příkazů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje sadu předdefinovaných příkazů.  Příkaz knihovny se skládá z následujících tříd: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>a <xref:System.Windows.Input.ComponentCommands>.  Tyto třídy zadejte příkazů jako třeba <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> a <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, a <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Mnoho z těchto příkazů obsahuje sadu výchozích vstupní vazby.  Například pokud určíte, že vaše aplikace zpracovává příkaz Kopírovat, získáte automaticky klávesnice vazba "CTRL + C" získáte také vazby pro jiné vstupní zařízení, jako například [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] pera gest a řeči informace.  
  
 Při odkazu na příkazy v různých knihoven příkaz pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], obvykle můžete vynechat název třídy, který zpřístupňuje vlastnost statické třídy knihovny. Obecně jsou názvy příkazů jednoznačné jako řetězce a vlastnící typy existují na poskytují možnost logického seskupování příkazy, ale nejsou nutné pro odstraňování mnohoznačnosti. Například můžete zadat `Command="Cut"` místo podrobnější `Command="ApplicationCommands.Cut"`. To je praktické mechanismus, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru pro příkazy (přesněji řečeno, je chování typ převaděče <xref:System.Windows.Input.ICommand>, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru odkazy v okamžiku načtení).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Vytváření vlastních příkazů  
 Pokud se příkazy v příkazu tříd knihovny nevyhovuje vašim potřebám, můžete vytvořit vlastní příkazy.  Existují dva způsoby, jak vytvořit vlastní příkaz.  První je ke spuštění od základů a implementovat <xref:System.Windows.Input.ICommand> rozhraní.  Jiným způsobem a více běžným přístupem je vytvoření <xref:System.Windows.Input.RoutedCommand> nebo <xref:System.Windows.Input.RoutedUICommand>.  
  
 Příklad vytvoření vlastní <xref:System.Windows.Input.RoutedCommand>, naleznete v tématu [vytvoření vlastní routedcommand – ukázky](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Implementace rozhraní ICommandSource](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [Postupy: přidání příkazu do položku nabídky](https://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)  
 [Vytvoření vlastní routedcommand – ukázky](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
