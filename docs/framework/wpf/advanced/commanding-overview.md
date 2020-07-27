---
title: Přehled příkazů
description: Přečtěte si o příkazech, vstupním mechanismu v Windows Presentation Foundation, který poskytuje zpracování vstupu na sémantické úrovni než vstup zařízení.
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
ms.openlocfilehash: 4f7d12fbf0de9b1546f15061ab7eb1318378bbbb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168124"
---
# <a name="commanding-overview"></a>Přehled příkazů
<a name="introduction"></a>Příkazy jsou vstupní mechanismus, ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kterém poskytuje zpracování vstupu na více sémantických úrovních než vstup zařízení. Příklady příkazů jsou operace **kopírování**, **vyjmutí**a **vložení** nalezené v mnoha aplikacích.  
  
 Tento přehled definuje, které příkazy jsou v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , které třídy jsou součástí modelu příkazů a jak používat a vytvářet příkazy v aplikacích.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Co jsou příkazy?](#commands_at_10000_feet)  
  
- [Příklad jednoduchého příkazu v subsystému WPF](#simple_command)  
  
- [Tři hlavní koncepty v příkazech WPF](#Four_main_Concepts)  
  
- [Knihovna příkazů](#Command_Library)  
  
- [Vytváření vlastních příkazů](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>Co jsou příkazy?  
 Příkazy mají několik účelů. Prvním účelem je oddělení sémantiky a objektu, který vyvolá příkaz z logiky, která provede příkaz. To umožňuje, aby vícenásobné a různorodé zdroje vyvolaly stejnou příkazovou logiku a bylo možné upravit příkazovou logiku pro různé cíle. Například operace úpravy **kopírování**, **vyjmutí**a **vložení**, které se nacházejí v mnoha aplikacích, lze vyvolat pomocí různých akcí uživatele, pokud jsou implementovány pomocí příkazů. Aplikace může uživateli dovolit vyjmout vybrané objekty nebo text kliknutím na tlačítko, výběrem položky v nabídce nebo pomocí kombinace kláves, například CTRL + X. Pomocí příkazů můžete vytvořit vazby každého typu akce uživatele ke stejné logice.  
  
 Dalším účelem příkazu je určit, zda je akce k dispozici. Chcete-li pokračovat v příkladu vyjmutí objektu nebo textu, akce dává smysl pouze v případě, že je vybrána položka. Pokud se uživatel pokusí Vyjmout objekt nebo text bez toho, že by vše vybralo, nic by se nestalo. Chcete-li tomuto uživateli indikovat, mnoho aplikací zakáže tlačítka a položky nabídky, aby uživatel věděl, zda je možné provést akci. Příkaz může určit, zda je možné akci provést implementací <xref:System.Windows.Input.ICommand.CanExecute%2A> metody. Tlačítko se může přihlásit k odběru <xref:System.Windows.Input.ICommand.CanExecuteChanged> události a při návratu vrátí <xref:System.Windows.Input.ICommand.CanExecute%2A> `false` nebo povolí jeho zakázání <xref:System.Windows.Input.ICommand.CanExecute%2A> `true` .  
  
 Sémantika příkazu může být konzistentní napříč aplikacemi a třídami, ale logika akce je specifická pro konkrétní objekt, na kterém se jednalo. Kombinace kláves CTRL + X Vyvolá příkaz **Vyjmout** v textových třídách, třídách obrázků a webových prohlížečích, ale skutečná logika pro provedení operace **Vyjmout** je definována aplikací, která provádí vyjmutí. A <xref:System.Windows.Input.RoutedCommand> umožňuje klientům implementovat logiku. Textový objekt může Vyjmout vybraný text do schránky, zatímco objekt obrázku může Vyjmout vybraný obrázek. Když aplikace <xref:System.Windows.Input.CommandManager.Executed> událost zpracuje, má přístup k cíli příkazu a může provést odpovídající akci v závislosti na typu cíle.  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>Příklad jednoduchého příkazu v subsystému WPF  
 Nejjednodušší způsob, jak použít příkaz v nástroji, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je použít předdefinovaný <xref:System.Windows.Input.RoutedCommand> z jedné z tříd knihovny příkazů; použijte ovládací prvek, který má nativní podporu pro zpracování příkazu; a použijte ovládací prvek, který má nativní podporu pro vyvolání příkazu.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A>Příkaz je jedním z předdefinovaných příkazů ve <xref:System.Windows.Input.ApplicationCommands> třídě.  <xref:System.Windows.Controls.TextBox>Ovládací prvek má vestavěnou logiku pro zpracování <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkazu.  A <xref:System.Windows.Controls.MenuItem> Třída má nativní podporu pro vyvolání příkazů.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.MenuItem> , aby při kliknutí na něj vyvolala <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkaz na <xref:System.Windows.Controls.TextBox> , za předpokladu, že <xref:System.Windows.Controls.TextBox> má fokus klávesnice.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>Tři hlavní koncepty v příkazech WPF  
 Model směrovaného příkazu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může být rozdělen do čtyř hlavních konceptů: příkaz, zdroj příkazu, cíl příkazu a vazba příkazu:  
  
- *Příkaz* je akce, která má být provedena.  
  
- *Zdroj příkazu* je objekt, který vyvolá příkaz.  
  
- *Cíl příkazu* je objekt, na kterém je příkaz spuštěn.  
  
- *Vazba příkazu* je objekt, který mapuje logiku příkazu na příkaz.  
  
 V předchozím příkladu je příkaz příkazem <xref:System.Windows.Input.ApplicationCommands.Paste%2A> , je to <xref:System.Windows.Controls.MenuItem> zdroj příkazu, <xref:System.Windows.Controls.TextBox> je cílový příkaz a vazba příkazu je poskytována <xref:System.Windows.Controls.TextBox> ovládacím prvkem.  Je potřeba poznamenat, že není vždy případ, že je <xref:System.Windows.Input.CommandBinding> dodána ovládacím prvkem, který je třídou cíle příkazu.  Poměrně často <xref:System.Windows.Input.CommandBinding> musí být vytvořen vývojářem aplikace nebo <xref:System.Windows.Input.CommandBinding> může být připojen k předchůdci cíle příkazu.  
  
<a name="Commands"></a>
### <a name="commands"></a>Příkazy  
 Příkazy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou vytvořeny implementací <xref:System.Windows.Input.ICommand> rozhraní.  <xref:System.Windows.Input.ICommand>zpřístupňuje dvě metody, <xref:System.Windows.Input.ICommand.Execute%2A> , a a <xref:System.Windows.Input.ICommand.CanExecute%2A> událost <xref:System.Windows.Input.ICommand.CanExecuteChanged> . <xref:System.Windows.Input.ICommand.Execute%2A>provede akce, které jsou přidruženy k příkazu. <xref:System.Windows.Input.ICommand.CanExecute%2A>Určuje, zda se příkaz může spustit na aktuálním cíli příkazu. <xref:System.Windows.Input.ICommand.CanExecuteChanged>je vyvolána, pokud správce příkazů, který centralizovat operace příkazového řádku, zjistí změnu ve zdroji příkazu, který může znehodnotit příkaz, který byl vyvolán, ale ještě nebyl proveden vazbou příkazu.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Implementace <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand> třídy je třída a je zaměřuje se na tento přehled.  
  
 Hlavními zdroji vstupu v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou myš, klávesnice, rukopis a směrované příkazy.  Více vstupů orientovaných na zařízení používá <xref:System.Windows.RoutedEvent> k oznamování objektů na stránce aplikace, ke které došlo ke vstupní události.  <xref:System.Windows.Input.RoutedCommand>Neexistuje žádný jiný.  <xref:System.Windows.Input.RoutedCommand.Execute%2A>Metody a <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> <xref:System.Windows.Input.RoutedCommand> neobsahují aplikační logiku pro příkaz, ale místo toho vyvolávají směrované události, které se provedou tunelem a bublinou prostřednictvím stromu elementu, dokud nenaleznou objekt s <xref:System.Windows.Input.CommandBinding> .  <xref:System.Windows.Input.CommandBinding>Obsahuje obslužné rutiny pro tyto události a jedná se o obslužné rutiny, které provádějí příkaz.  Další informace o směrování událostí v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A>Metoda na vyvolává událost <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> události v cíli příkazu.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>Metoda na <xref:System.Windows.Input.RoutedCommand> vyvolá <xref:System.Windows.Input.CommandManager.CanExecute> <xref:System.Windows.Input.CommandManager.PreviewCanExecute> události a v cíli příkazu.  Tyto události se procházejí tunelem a bublinou přes strom elementů, dokud nenaleznou objekt, který má <xref:System.Windows.Input.CommandBinding> pro tento konkrétní příkaz.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje sadu běžných směrovaných příkazů, které jsou rozloženy mezi několik tříd: <xref:System.Windows.Input.MediaCommands> , <xref:System.Windows.Input.ApplicationCommands> , <xref:System.Windows.Input.NavigationCommands> , <xref:System.Windows.Input.ComponentCommands> a <xref:System.Windows.Documents.EditingCommands> .  Tyto třídy se skládají pouze z <xref:System.Windows.Input.RoutedCommand> objektů a nikoli z logiky implementace příkazu.  Logika implementace je zodpovědností objektu, na kterém je příkaz spuštěn.  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>Zdroje příkazů  
 Zdroj příkazu je objekt, který vyvolá příkaz.  Příklady zdrojů příkazů jsou <xref:System.Windows.Controls.MenuItem> , <xref:System.Windows.Controls.Button> a <xref:System.Windows.Input.KeyGesture> .  
  
 Zdroje příkazů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zásadě implementují <xref:System.Windows.Input.ICommandSource> rozhraní.  
  
 <xref:System.Windows.Input.ICommandSource>zpřístupňuje tři vlastnosti: <xref:System.Windows.Input.ICommandSource.Command%2A> , a <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> :  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A>je příkaz, který se má provést, když je vyvolán zdroj příkazu.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>je objekt, na kterém se má příkaz Spustit.  Je třeba poznamenat, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> vlastnosti <xref:System.Windows.Input.ICommandSource> je k dispozici pouze v případě, že <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand> .  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastavené v <xref:System.Windows.Input.ICommandSource> a odpovídající příkaz není a <xref:System.Windows.Input.RoutedCommand> , cíl příkazu se ignoruje. Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> není nastaven, element s fokusem klávesnice bude cílem příkazu.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>je uživatelsky definovaný datový typ, který slouží k předávání informací obslužným rutinám implementující příkaz.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Třídy, které implementují <xref:System.Windows.Input.ICommandSource> <xref:System.Windows.Controls.Primitives.ButtonBase> , <xref:System.Windows.Controls.MenuItem> , a <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Input.InputBinding> .  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem> a <xref:System.Windows.Documents.Hyperlink> vyvolat příkaz, když se na ně klikne, a <xref:System.Windows.Input.InputBinding> Vyvolá příkaz, když se <xref:System.Windows.Input.InputGesture> provede přidružení k němu.  
  
 Následující příklad ukazuje, jak použít a <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ContextMenu> jako zdroj příkazu pro <xref:System.Windows.Input.ApplicationCommands.Properties%2A> příkaz.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Obvykle bude zdroj příkazů naslouchat <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> události.  Tato událost informuje zdroj příkazu, že se mohla změnit schopnost příkazu spustit na aktuálním cíli příkazu.  Zdroj příkazu může zadat dotaz na aktuální stav <xref:System.Windows.Input.RoutedCommand> pomocí <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> metody.  Zdroj příkazu se pak může vypnout, pokud příkaz nejde provést.  Příkladem je to, že <xref:System.Windows.Controls.MenuItem> když příkaz nelze provést, je tato šedá.  
  
 <xref:System.Windows.Input.InputGesture>Lze použít jako zdroj příkazu.  Dva typy vstupních gest v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.MouseGesture> .  Můžete si představit jako klávesovou <xref:System.Windows.Input.KeyGesture> zkratku, například CTRL + C.  A <xref:System.Windows.Input.KeyGesture> se skládá z <xref:System.Windows.Input.Key> a a sady <xref:System.Windows.Input.ModifierKeys> .  A <xref:System.Windows.Input.MouseGesture> se skládá z <xref:System.Windows.Input.MouseAction> a volitelné sady <xref:System.Windows.Input.ModifierKeys> .  
  
 Aby <xref:System.Windows.Input.InputGesture> mohl jako zdroj příkazu fungovat, musí být přidružen k příkazu. Existuje několik způsobů, jak to provést.  Jedním ze způsobů je použít <xref:System.Windows.Input.InputBinding> .  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.KeyBinding> mezi <xref:System.Windows.Input.KeyGesture> a a <xref:System.Windows.Input.RoutedCommand> .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Další způsob, jak přidružit <xref:System.Windows.Input.InputGesture> k a, <xref:System.Windows.Input.RoutedCommand> je přidat do v <xref:System.Windows.Input.InputGesture> <xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.RoutedCommand> .  
  
 Následující příklad ukazuje, jak přidat <xref:System.Windows.Input.KeyGesture> do <xref:System.Windows.Input.InputGestureCollection> a <xref:System.Windows.Input.RoutedCommand> .  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 <xref:System.Windows.Input.CommandBinding>Přidruží příkaz k obslužným rutinám událostí, které implementují příkaz.  
  
 <xref:System.Windows.Input.CommandBinding>Třída obsahuje <xref:System.Windows.Input.CommandBinding.Command%2A> <xref:System.Windows.Input.CommandBinding.PreviewExecuted> události a,, <xref:System.Windows.Input.CommandBinding.Executed> <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> a <xref:System.Windows.Input.CommandBinding.CanExecute> .  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>je příkaz, ke kterému <xref:System.Windows.Input.CommandBinding> je přidružen.  Obslužné rutiny událostí, které jsou připojeny <xref:System.Windows.Input.CommandBinding.PreviewExecuted> k <xref:System.Windows.Input.CommandBinding.Executed> událostem a implementují příkazová logika.  Obslužné rutiny události připojené k <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> <xref:System.Windows.Input.CommandBinding.CanExecute> událostem a určují, zda lze příkaz provést na aktuálním cíli příkazu.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.CommandBinding> v kořenovém adresáři <xref:System.Windows.Window> aplikace.  <xref:System.Windows.Input.CommandBinding>Přidruží <xref:System.Windows.Input.ApplicationCommands.Open%2A> příkaz k <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandBinding.CanExecute> obslužným rutinám a.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Dále <xref:System.Windows.Input.ExecutedRoutedEventHandler> jsou vytvořeny a a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> .  <xref:System.Windows.Input.ExecutedRoutedEventHandler>Otevře se <xref:System.Windows.MessageBox> , který zobrazí řetězec oznamující, že příkaz byl proveden.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler>Nastaví <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> vlastnost na hodnotu `true` .  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> je připojen ke konkrétnímu objektu, jako je například kořen <xref:System.Windows.Window> aplikace nebo ovládací prvek.  Objekt, k němuž <xref:System.Windows.Input.CommandBinding> je připojen, definuje rozsah vazby.  <xref:System.Windows.Input.CommandBinding>Událost může být například připojená k předchůdci cíle příkazu <xref:System.Windows.Input.CommandBinding.Executed> , ale <xref:System.Windows.Input.CommandBinding> není dostupná k následníkovi cílového příkazu.  Toto je přímý způsob, jakým jsou <xref:System.Windows.RoutedEvent> tunely a bubliny z objektu, který vyvolává událost.  
  
 V některých situacích <xref:System.Windows.Input.CommandBinding> je připojen k samotnému cílovému příkazu, jako je například s <xref:System.Windows.Controls.TextBox> třídou a <xref:System.Windows.Input.ApplicationCommands.Cut%2A> <xref:System.Windows.Input.ApplicationCommands.Copy%2A> příkazy, a <xref:System.Windows.Input.ApplicationCommands.Paste%2A> . Poměrně často ale je pohodlnější připojit se <xref:System.Windows.Input.CommandBinding> k předchůdci cílového příkazu, jako je například hlavní <xref:System.Windows.Window> nebo aplikační objekt, zejména pokud je <xref:System.Windows.Input.CommandBinding> možné použít pro více cílů příkazů.  Jedná se o rozhodnutí o návrhu, která budete chtít vzít v úvahu při vytváření infrastruktury pro příkazy.  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>Cíl příkazu  
 Cíl příkazu je prvek, na kterém je příkaz spuštěn.  S ohledem na <xref:System.Windows.Input.RoutedCommand> , cílový příkaz je prvek, na kterém se <xref:System.Windows.Input.CommandManager.Executed> spouští směrování a <xref:System.Windows.Input.CommandManager.CanExecute> .  Jak bylo uvedeno dříve, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> vlastnosti na <xref:System.Windows.Input.ICommandSource> je použit pouze v případě, že <xref:System.Windows.Input.ICommand> je <xref:System.Windows.Input.RoutedCommand> .  Pokud <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je nastavené v <xref:System.Windows.Input.ICommandSource> a odpovídající příkaz není a <xref:System.Windows.Input.RoutedCommand> , cíl příkazu se ignoruje.  
  
 Zdroj příkazu může explicitně nastavit cíl příkazu.  Pokud není definován cíl příkazu, bude element s fokusem klávesnice použit jako cíl příkazu.  Jedna z výhod použití prvku s fokusem klávesnice jako cílovým příkazem je, že umožňuje vývojářům aplikací použít stejný zdroj příkazů k vyvolání příkazu na více cílech bez nutnosti sledovat cíl příkazu.  Například pokud <xref:System.Windows.Controls.MenuItem> Vyvolá příkaz **vložení** v aplikaci, která má <xref:System.Windows.Controls.TextBox> ovládací prvek a <xref:System.Windows.Controls.PasswordBox> ovládací prvek, může být cílem buď <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.PasswordBox> v závislosti na tom, který ovládací prvek má fokus klávesnice.  
  
 Následující příklad ukazuje, jak explicitně nastavit cíl příkazu v kódu a v kódu na pozadí.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>Objekt CommandManager  
 <xref:System.Windows.Input.CommandManager>Slouží k provádění několika funkcí souvisejících s příkazy.  Poskytuje sadu statických metod pro přidávání a odebírání <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandManager.PreviewCanExecute> <xref:System.Windows.Input.CommandManager.CanExecute> obslužných rutin událostí,, a z konkrétního prvku.  Poskytuje prostředky pro registraci <xref:System.Windows.Input.CommandBinding> a objekty do <xref:System.Windows.Input.InputBinding> konkrétní třídy.  <xref:System.Windows.Input.CommandManager>Také poskytuje prostřednictvím události prostředek, <xref:System.Windows.Input.CommandManager.RequerySuggested> který upozorní příkaz, pokud by měl vyvolat <xref:System.Windows.Input.ICommand.CanExecuteChanged> událost.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A>Metoda vynutí <xref:System.Windows.Input.CommandManager> vyvolání <xref:System.Windows.Input.CommandManager.RequerySuggested> události.  To je užitečné pro podmínky, které by měly zakázat nebo povolit příkaz, ale nejedná se o podmínky, <xref:System.Windows.Input.CommandManager> o kterých ví.  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>Knihovna příkazů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje sadu předdefinovaných příkazů.  Knihovna příkazů se skládá z následujících tříd: <xref:System.Windows.Input.ApplicationCommands> , <xref:System.Windows.Input.NavigationCommands> , <xref:System.Windows.Input.MediaCommands> , <xref:System.Windows.Documents.EditingCommands> a <xref:System.Windows.Input.ComponentCommands> .  Tyto třídy poskytují příkazy, jako,,,, <xref:System.Windows.Input.ApplicationCommands.Cut%2A> <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A> <xref:System.Windows.Input.MediaCommands.Play%2A> <xref:System.Windows.Input.MediaCommands.Stop%2A> a <xref:System.Windows.Input.MediaCommands.Pause%2A> .  
  
 Mnohé z těchto příkazů zahrnují sadu výchozích vstupních vazeb.  Například pokud určíte, že vaše aplikace zpracovává příkaz pro kopírování, získáte automaticky vazbu klávesnice "CTRL + C", a také získáte vazby pro jiná vstupní zařízení, jako jsou například gesta pera tabletového počítače a informace o řeči.  
  
 Když odkazujete na příkazy v různých knihovnách příkazů pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , můžete obvykle vynechat název třídy knihovny, která zveřejňuje vlastnost statického příkazu. Obecně jsou názvy příkazů jednoznačné jako řetězce a vlastnící typy existují k poskytnutí logického seskupení příkazů, ale nejsou nutné pro nejednoznačnost. Například můžete zadat `Command="Cut"` místo podrobnějšího podrobnějšího `Command="ApplicationCommands.Cut"` . Toto je pohodlný mechanismus, který je integrovaný do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru pro příkazy (přesněji, jedná se o chování konvertoru typu <xref:System.Windows.Input.ICommand> , který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor odkazuje v době načítání).  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>Vytváření vlastních příkazů  
 Pokud příkazy v třídách knihovny příkazů nevyhovují vašim požadavkům, můžete vytvořit vlastní příkazy.  Existují dva způsoby, jak vytvořit vlastní příkaz.  První je začít od základu a implementovat <xref:System.Windows.Input.ICommand> rozhraní.  Druhým způsobem a běžnějším přístupem je vytvořit <xref:System.Windows.Input.RoutedCommand> nebo <xref:System.Windows.Input.RoutedUICommand> .  
  
 Příklad vytvoření vlastní najdete <xref:System.Windows.Input.RoutedCommand> v tématu [Vytvoření vlastní ukázky RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Přehled vstupu](input-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Implementace rozhraní ICommandSource](how-to-implement-icommandsource.md)
- [Postupy: Přidání příkazu do nabídky MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Vytvoření vlastní ukázky RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
