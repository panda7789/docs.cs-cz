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
ms.openlocfilehash: 3477e6a9eda40edeadaab9cd6d3de2f016250fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186217"
---
# <a name="commanding-overview"></a>Přehled příkazů
<a name="introduction"></a>Příkazing je vstupní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mechanismus, ve kterém poskytuje zpracování vstupu na sémantické úrovni než vstup zařízení. Příklady příkazů jsou operace **Kopírování**, **Vyjmout**a **Vložit,** které se nacházejí v mnoha aplikacích.  
  
 Tento přehled definuje, jaké [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]příkazy jsou v , které třídy jsou součástí velícího modelu a jak používat a vytvářet příkazy ve vašich aplikacích.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Co jsou příkazy?](#commands_at_10000_feet)  
  
- [Jednoduchý příklad příkazu v WPF](#simple_command)  
  
- [Čtyři hlavní koncepty ve WPF Commanding](#Four_main_Concepts)  
  
- [Knihovna příkazů](#Command_Library)  
  
- [Vytváření vlastních příkazů](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>Co jsou příkazy?  
 Příkazy mají několik účelů. Prvním účelem je oddělit sémantiku a objekt, který vyvolá příkaz z logiky, která provede příkaz. To umožňuje více a různorodé zdroje vyvolat stejnou logiku příkazu a umožňuje logiku příkazu přizpůsobit pro různé cíle. Například operace úprav **Kopírovat**, **Vyjmout**a **Vložit**, které se nacházejí v mnoha aplikacích, lze vyvolat pomocí různých uživatelských akcí, pokud jsou implementovány pomocí příkazů. Aplikace může uživateli umožnit vyjmout vybrané objekty nebo text klepnutím na tlačítko, výběrem položky v nabídce nebo pomocí kombinace kláves, například CTRL+X. Pomocí příkazů můžete svázat každý typ akce uživatele se stejnou logikou.  
  
 Dalším účelem příkazů je označit, zda je k dispozici akce. Chcete-li pokračovat v příkladu vyjmutí objektu nebo textu, má akce smysl pouze v případě, že je něco vybráno. Pokud se uživatel pokusí vyjmout objekt nebo text bez výběru něčeho, nic se nestane. Chcete-li to označit uživateli, mnoho aplikací zakázat tlačítka a položky nabídky tak, aby uživatel ví, zda je možné provést akci. Příkaz může určit, zda je možné <xref:System.Windows.Input.ICommand.CanExecute%2A> akce implementací metody. Tlačítko se může <xref:System.Windows.Input.ICommand.CanExecuteChanged> přihlásit k <xref:System.Windows.Input.ICommand.CanExecute%2A> odběru `false` události a <xref:System.Windows.Input.ICommand.CanExecute%2A> `true`může být zakázáno, pokud vrátí nebo může být povoleno, pokud vrátí .  
  
 Sémantiku příkazu může být konzistentní napříč aplikacemi a třídami, ale logika akce je specifická pro konkrétní objekt, na který se jednalo. Kombinace kláves CTRL+X vyvolá příkaz **Vyjmout** v textových třídách, třídách obrázků a webových prohlížečích, ale skutečná logika pro provedení operace **Vyjmout** je definována aplikací, která provádí řez. A <xref:System.Windows.Input.RoutedCommand> umožňuje klientům implementovat logiku. Textový objekt může vyjmout vybraný text do schránky, zatímco obrazový objekt může vyjmout vybraný obraz. Když aplikace zpracovává <xref:System.Windows.Input.CommandManager.Executed> událost, má přístup k cíli příkazu a může provést příslušnou akci v závislosti na typu cíle.  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>Jednoduchý příklad příkazu v WPF  
 Nejjednodušší způsob použití příkazu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v je použít <xref:System.Windows.Input.RoutedCommand> předdefinovaný z jedné z tříd knihovny příkazů; použijte ovládací prvek, který má nativní podporu pro zpracování příkazu; a použijte ovládací prvek, který má nativní podporu pro vyvolání příkazu.  Příkaz <xref:System.Windows.Input.ApplicationCommands.Paste%2A> je jedním z předdefinovaných <xref:System.Windows.Input.ApplicationCommands> příkazů ve třídě.  Ovládací <xref:System.Windows.Controls.TextBox> prvek má vestavěnou <xref:System.Windows.Input.ApplicationCommands.Paste%2A> logiku pro zpracování příkazu.  A <xref:System.Windows.Controls.MenuItem> třída má nativní podporu pro vyvolání příkazů.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.MenuItem> nastavit tak, aby po klepnutí <xref:System.Windows.Input.ApplicationCommands.Paste%2A> vyvolá <xref:System.Windows.Controls.TextBox>příkaz na <xref:System.Windows.Controls.TextBox> , za předpokladu, že má fokus klávesnice.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>Čtyři hlavní koncepty ve WPF Commanding  
 Model směrovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příkazu v aplikaci lze rozdělit na čtyři hlavní koncepty: příkaz, zdroj příkazu, cíl příkazu a vazbu příkazu:  
  
- *Příkaz* je akce, která má být provedena.  
  
- *Zdroj příkazu* je objekt, který vyvolá příkaz.  
  
- *Cíl příkazu* je objekt, na který je příkaz prováděn.  
  
- Vazba *příkazu* je objekt, který mapuje logiku příkazu na příkaz.  
  
 V předchozím příkladu <xref:System.Windows.Input.ApplicationCommands.Paste%2A> je příkaz příkaz, <xref:System.Windows.Controls.MenuItem> je zdrojem <xref:System.Windows.Controls.TextBox> příkazu, je cílem příkazu a <xref:System.Windows.Controls.TextBox> vazba příkazu je dodávána ovládacím prvkem.  Stojí za zmínku, že není vždy <xref:System.Windows.Input.CommandBinding> případ, že je dodáván ovládacího prvku, který je cílová třída příkazu.  Poměrně <xref:System.Windows.Input.CommandBinding> často musí být vytvořen vývojář <xref:System.Windows.Input.CommandBinding> aplikace nebo může být připojen k předchůdce cíle příkazu.  
  
<a name="Commands"></a>
### <a name="commands"></a>Příkazy  
 Příkazy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jsou vytvořeny <xref:System.Windows.Input.ICommand> implementací rozhraní.  <xref:System.Windows.Input.ICommand>zveřejňuje dvě metody <xref:System.Windows.Input.ICommand.Execute%2A>, <xref:System.Windows.Input.ICommand.CanExecute%2A>a , <xref:System.Windows.Input.ICommand.CanExecuteChanged>a událost . <xref:System.Windows.Input.ICommand.Execute%2A>provede akce, které jsou přidruženy k příkazu. <xref:System.Windows.Input.ICommand.CanExecute%2A>určuje, zda lze příkaz spustit u aktuálního cíle příkazu. <xref:System.Windows.Input.ICommand.CanExecuteChanged>je aktivována, pokud správce příkazů, který centralizuje velící operace zjistí změnu ve zdroji příkazu, který může zneplatnit příkaz, který byl aktivován, ale dosud nebyl proveden vazbou příkazu.  Implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand> třída a je předmětem tohoto přehledu.  
  
 Hlavními zdroji vstupu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou příkazy myši, klávesnice, inkoustu a směrovaných příkazů.  Více vstupy orientované na <xref:System.Windows.RoutedEvent> zařízení použít k upozornění objektů na stránce aplikace, že došlo ke vstupní události.  A <xref:System.Windows.Input.RoutedCommand> se nijak neliší.  Metody <xref:System.Windows.Input.RoutedCommand.Execute%2A> <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> a a <xref:System.Windows.Input.RoutedCommand> neobsahují aplikační logiku pro příkaz, ale spíše vyvolávají směrované události, které tunelové propojení <xref:System.Windows.Input.CommandBinding>a bubliny přes strom prvku, dokud se nesetkají objekt s .  Obsahuje <xref:System.Windows.Input.CommandBinding> obslužné rutiny pro tyto události a je obslužné rutiny, které provádějí příkaz.  Další informace o směrování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]událostí v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 Metoda <xref:System.Windows.Input.RoutedCommand.Execute%2A> na <xref:System.Windows.Input.RoutedCommand> vyvolává <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> události na cíl příkazu.  Metoda <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> na <xref:System.Windows.Input.RoutedCommand> a <xref:System.Windows.Input.CommandManager.CanExecute> vyvolává <xref:System.Windows.Input.CommandManager.PreviewCanExecute> a události na cíl příkazu.  Tyto události tunelové propojení a bubliny přes strom <xref:System.Windows.Input.CommandBinding> prvku, dokud se nesetkají objekt, který má pro tento konkrétní příkaz.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dodává sadu běžných směrovaných příkazů rozložených <xref:System.Windows.Input.MediaCommands>do <xref:System.Windows.Input.ApplicationCommands> <xref:System.Windows.Input.NavigationCommands>několika <xref:System.Windows.Input.ComponentCommands>tříd: , , , a <xref:System.Windows.Documents.EditingCommands>.  Tyto třídy se <xref:System.Windows.Input.RoutedCommand> skládají pouze z objektů a nikoli z logiky implementace příkazu.  Logika implementace je odpovědnost objektu, na kterém je příkaz spouštěn.  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>Zdroje příkazů  
 Zdroj příkazu je objekt, který vyvolá příkaz.  Příklady zdrojů příkazů <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.Button>jsou <xref:System.Windows.Input.KeyGesture>, a .  
  
 Zdroje příkazů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v <xref:System.Windows.Input.ICommandSource> obecně implementovat rozhraní.  
  
 <xref:System.Windows.Input.ICommandSource>zpřístupňuje tři <xref:System.Windows.Input.ICommandSource.Command%2A> <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>vlastnosti: , , a <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A>je příkaz, který má být proveden při vyvolání zdroje příkazů.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>je objekt, na kterém chcete spustit příkaz.  Stojí za zmínku, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> že <xref:System.Windows.Input.ICommandSource> v nemovitosti <xref:System.Windows.Input.ICommand> na <xref:System.Windows.Input.RoutedCommand>je použitelná pouze v případě, že je .  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastaven <xref:System.Windows.Input.ICommandSource> na a odpovídající příkaz <xref:System.Windows.Input.RoutedCommand>není , cíl příkazu je ignorován. Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> není nastavena, prvek s fokusem klávesnice bude cílem příkazu.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>je uživatelem definovaný datový typ používaný k předání informací obslužným rutinám implementujícím příkaz.  
  
 Třídy, <xref:System.Windows.Input.ICommandSource> které <xref:System.Windows.Controls.Primitives.ButtonBase> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Documents.Hyperlink>implementují, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou , , a <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>a <xref:System.Windows.Documents.Hyperlink> vyvolat příkaz, když jsou klepnuty, a <xref:System.Windows.Input.InputBinding> <xref:System.Windows.Input.InputGesture> vyvolá příkaz při jeho přidružení k němu.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.MenuItem> použít <xref:System.Windows.Controls.ContextMenu> v a jako <xref:System.Windows.Input.ApplicationCommands.Properties%2A> zdroj příkazů pro příkaz.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Obvykle zdroj příkazu bude naslouchat <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> události.  Tato událost informuje zdroj příkazu, že schopnost příkazu provést na aktuální cíl příkazu může změnit.  Zdroj příkazů může dotaz ovat <xref:System.Windows.Input.RoutedCommand> aktuální stav <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody.  Zdroj příkazu se pak může sám zakázat, pokud příkaz nelze spustit.  Příkladem je <xref:System.Windows.Controls.MenuItem> samotné šedivění, když příkaz nelze spustit.  
  
 A <xref:System.Windows.Input.InputGesture> lze použít jako zdroj příkazů.  Dva typy vstupních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gest <xref:System.Windows.Input.KeyGesture> v <xref:System.Windows.Input.MouseGesture>jsou a .  Můžete si ji <xref:System.Windows.Input.KeyGesture> myslet jako klávesovou zkratku, například CTRL+C.  A <xref:System.Windows.Input.KeyGesture> se skládá <xref:System.Windows.Input.Key> z a <xref:System.Windows.Input.ModifierKeys>a soubor .  A <xref:System.Windows.Input.MouseGesture> se skládá <xref:System.Windows.Input.MouseAction> z a a <xref:System.Windows.Input.ModifierKeys>volitelné soubor .  
  
 Aby mohl <xref:System.Windows.Input.InputGesture> příkaz fungovat jako zdroj příkazů, musí být přidružen k příkazu. Existuje několik způsobů, jak toho dosáhnout.  Jedním ze způsobů <xref:System.Windows.Input.InputBinding>je použití .  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Input.KeyBinding> vytvořit <xref:System.Windows.Input.KeyGesture> mezi <xref:System.Windows.Input.RoutedCommand>a a .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Dalším způsobem, <xref:System.Windows.Input.InputGesture> jak <xref:System.Windows.Input.RoutedCommand> přidružit <xref:System.Windows.Input.InputGesture> a <xref:System.Windows.Input.InputGestureCollection> je <xref:System.Windows.Input.RoutedCommand>přidat na .  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Input.KeyGesture> přidat <xref:System.Windows.Input.InputGestureCollection> a <xref:System.Windows.Input.RoutedCommand>do .  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 Příkaz <xref:System.Windows.Input.CommandBinding> přidruží k obslužným rutinám událostí, které příkaz implementují.  
  
 Třída <xref:System.Windows.Input.CommandBinding> obsahuje <xref:System.Windows.Input.CommandBinding.Command%2A> vlastnost a <xref:System.Windows.Input.CommandBinding.PreviewExecuted> <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, <xref:System.Windows.Input.CommandBinding.CanExecute> a události.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>je příkaz, <xref:System.Windows.Input.CommandBinding> ke kterému je přidružen.  Obslužné rutiny událostí, které jsou připojeny <xref:System.Windows.Input.CommandBinding.PreviewExecuted> k a <xref:System.Windows.Input.CommandBinding.Executed> události implementovat logiku příkazu.  Obslužné rutiny <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> <xref:System.Windows.Input.CommandBinding.CanExecute> událostí připojené k události a určují, zda lze příkaz spustit na aktuálním cíli příkazu.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Input.CommandBinding> vytvořit <xref:System.Windows.Window> v kořenovém adresáři aplikace.  <xref:System.Windows.Input.CommandBinding> Přidruží <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandBinding.CanExecute> a obslužné rutiny.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Dále <xref:System.Windows.Input.ExecutedRoutedEventHandler> <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a a jsou vytvořeny.  Otevře <xref:System.Windows.Input.ExecutedRoutedEventHandler> se <xref:System.Windows.MessageBox> řetězec, který říká, že příkaz byl proveden.  Nastaví <xref:System.Windows.Input.CanExecuteRoutedEventHandler> <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> vlastnost `true`na .  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> je připojen k určitému objektu, jako je například kořen <xref:System.Windows.Window> aplikace nebo ovládací prvek.  Objekt, který <xref:System.Windows.Input.CommandBinding> je připojen k definuje rozsah vazby.  Například <xref:System.Windows.Input.CommandBinding> připojené k předchůdce cíle příkazu může být <xref:System.Windows.Input.CommandBinding.Executed> dosaženo událostí, <xref:System.Windows.Input.CommandBinding> ale nelze dosáhnout připojení k potomkovi cíle příkazu.  To je přímým důsledkem <xref:System.Windows.RoutedEvent> způsobu tunelů a bublin z objektu, který vyvolává událost.  
  
 V některých <xref:System.Windows.Input.CommandBinding> situacích je připojen k samotnému <xref:System.Windows.Controls.TextBox> cíli příkazu, například s třídou a <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>a <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkazy. Poměrně často však je vhodnější <xref:System.Windows.Input.CommandBinding> připojit k předchůdce cíle příkazu, <xref:System.Windows.Window> jako je například hlavní <xref:System.Windows.Input.CommandBinding> nebo aplikační objekt, zejména pokud to lze použít pro více cílů příkazu.  Jedná se o rozhodnutí o návrhu, které budete chtít zvážit při vytváření velící infrastruktury.  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>Cíl příkazu  
 Cíl příkazu je prvek, na kterém je příkaz proveden.  Pokud jde o <xref:System.Windows.Input.RoutedCommand>, cíl příkazu je prvek, <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandManager.CanExecute> při kterém směrování a začíná.  Jak již bylo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> uvedeno <xref:System.Windows.Input.ICommandSource> dříve, v <xref:System.Windows.Input.ICommand> nemovitosti <xref:System.Windows.Input.RoutedCommand>na je použitelný pouze v případě, že je .  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastaven <xref:System.Windows.Input.ICommandSource> na a odpovídající příkaz <xref:System.Windows.Input.RoutedCommand>není , cíl příkazu je ignorován.  
  
 Zdroj příkazů může explicitně nastavit cíl příkazu.  Pokud cíl příkazu není definován, prvek s fokusem klávesnice bude použit jako cíl příkazu.  Jednou z výhod použití prvku s fokusem klávesnice jako cíl příkazu je, že umožňuje vývojáři aplikace použít stejný zdroj příkazů k vyvolání příkazu na více cílů bez nutnosti sledovat cíl příkazu.  Například pokud <xref:System.Windows.Controls.MenuItem> vyvolá **příkaz Vložit** v aplikaci, <xref:System.Windows.Controls.TextBox> která <xref:System.Windows.Controls.PasswordBox> má ovládací prvek a <xref:System.Windows.Controls.TextBox> ovládací <xref:System.Windows.Controls.PasswordBox> prvek, cíl může být nebo v závislosti na tom, který ovládací prvek má fokus klávesnice.  
  
 Následující příklad ukazuje, jak explicitně nastavit cíl příkazu ve značkách a v kódu za sebou.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>Správce příkazů  
 Slouží <xref:System.Windows.Input.CommandManager> řadu funkcí souvisejících s příkazy.  Poskytuje sadu statických metod pro <xref:System.Windows.Input.CommandManager.PreviewExecuted>přidávání a odebírání , <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>a <xref:System.Windows.Input.CommandManager.CanExecute> obslužné rutiny událostí do a z určitého prvku.  Poskytuje prostředky k <xref:System.Windows.Input.CommandBinding> registraci a <xref:System.Windows.Input.InputBinding> objekty na konkrétní třídy.  Také <xref:System.Windows.Input.CommandManager> poskytuje prostředky prostřednictvím <xref:System.Windows.Input.CommandManager.RequerySuggested> události, upozornit příkaz, kdy <xref:System.Windows.Input.ICommand.CanExecuteChanged> by měl vyvolat událost.  
  
 Metoda <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> vynutí <xref:System.Windows.Input.CommandManager> vyvolat <xref:System.Windows.Input.CommandManager.RequerySuggested> událost.  To je užitečné pro podmínky, které by měly <xref:System.Windows.Input.CommandManager> zakázat nebo povolit příkaz, ale nejsou podmínky, které je vědom.  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>Knihovna příkazů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje sadu předdefinovaných příkazů.  Knihovna příkazů se skládá z <xref:System.Windows.Input.ApplicationCommands> <xref:System.Windows.Input.NavigationCommands>následujících <xref:System.Windows.Documents.EditingCommands>tříd: <xref:System.Windows.Input.ComponentCommands>, , <xref:System.Windows.Input.MediaCommands>, a .  Tyto třídy poskytují <xref:System.Windows.Input.ApplicationCommands.Cut%2A>příkazy, <xref:System.Windows.Input.MediaCommands.Stop%2A>například <xref:System.Windows.Input.MediaCommands.Pause%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> a <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>a .  
  
 Mnoho z těchto příkazů obsahuje sadu výchozívstupní vazby.  Například pokud zadáte, že vaše aplikace zpracovává příkaz kopírování, automaticky získáte vazby klávesnice "CTRL+C" Získáte také vazby pro jiná vstupní zařízení, jako jsou gesta pera tabletpc a informace o řeči.  
  
 Když odkazujete na příkazy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]různých knihovnách příkazů pomocí , můžete obvykle vynechat název třídy knihovny, která zveřejňuje vlastnost statického příkazu. Obecně platí, že názvy příkazů jsou jednoznačné jako řetězce a vlastnící typy existují poskytnout logické seskupení příkazů, ale nejsou nezbytné pro rozdvojení. Můžete například zadat `Command="Cut"` spíše než podrobnější `Command="ApplicationCommands.Cut"`. Jedná se o mechanismus pohodlí, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] který je integrován do procesoru pro příkazy <xref:System.Windows.Input.ICommand>(přesněji řečeno, jedná se o chování převaděče typu , na které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor odkazuje v době načítání).  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>Vytváření vlastních příkazů  
 Pokud příkazy ve třídách knihovny příkazů neodpovídají vašim potřebám, můžete vytvořit vlastní příkazy.  Vlastní příkaz lze vytvořit dvěma způsoby.  Prvním z nich je začít od <xref:System.Windows.Input.ICommand> základu a implementovat rozhraní.  Opačným způsobem a běžnějším přístupem je <xref:System.Windows.Input.RoutedCommand> vytvoření <xref:System.Windows.Input.RoutedUICommand>a nebo .  
  
 Příklad vytvoření vlastního objektu <xref:System.Windows.Input.RoutedCommand>naleznete v [tématu Vytvoření vlastní ukázky příkazu RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Přehled vstupu](input-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Implementace rozhraní ICommandSource](how-to-implement-icommandsource.md)
- [Postup: Přidání příkazu do položky MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Vytvoření vlastní ukázky příkazu RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
