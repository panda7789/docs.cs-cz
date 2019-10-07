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
ms.openlocfilehash: 192fe629493947ffe4e0aa8ade417b7701ff95b4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004593"
---
# <a name="commanding-overview"></a>Přehled příkazů
<a name="introduction"></a>Příkazy jsou vstupním mechanismem v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], který poskytuje zpracování vstupu na sémantické úrovni než vstup zařízení. Příklady příkazů jsou operace **kopírování**, **vyjmutí**a **vložení** nalezené v mnoha aplikacích.  
  
 Tento přehled definuje, které příkazy jsou v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které třídy jsou součástí modelu příkazů a jak používat a vytvářet příkazy v aplikacích.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Co jsou příkazy?](#commands_at_10000_feet)  
  
- [Příklad jednoduchého příkazu v subsystému WPF](#simple_command)  
  
- [Tři hlavní koncepty v příkazech WPF](#Four_main_Concepts)  
  
- [Knihovna příkazů](#Command_Library)  
  
- [Vytváření vlastních příkazů](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Co jsou příkazy?  
 Příkazy mají několik účelů. Prvním účelem je oddělení sémantiky a objektu, který vyvolá příkaz z logiky, která provede příkaz. To umožňuje, aby vícenásobné a různorodé zdroje vyvolaly stejnou příkazovou logiku a bylo možné upravit příkazovou logiku pro různé cíle. Například operace úpravy **kopírování**, **vyjmutí**a **vložení**, které se nacházejí v mnoha aplikacích, lze vyvolat pomocí různých akcí uživatele, pokud jsou implementovány pomocí příkazů. Aplikace může uživateli dovolit vyjmout vybrané objekty nebo text kliknutím na tlačítko, výběrem položky v nabídce nebo pomocí kombinace kláves, například CTRL + X. Pomocí příkazů můžete vytvořit vazby každého typu akce uživatele ke stejné logice.  
  
 Dalším účelem příkazu je určit, zda je akce k dispozici. Chcete-li pokračovat v příkladu vyjmutí objektu nebo textu, akce dává smysl pouze v případě, že je vybrána položka. Pokud se uživatel pokusí Vyjmout objekt nebo text bez toho, že by vše vybralo, nic by se nestalo. Chcete-li tomuto uživateli indikovat, mnoho aplikací zakáže tlačítka a položky nabídky, aby uživatel věděl, zda je možné provést akci. Příkaz může určit, zda je možné akci provést implementací metody <xref:System.Windows.Input.ICommand.CanExecute%2A>. Tlačítko se může přihlásit k odběru události <xref:System.Windows.Input.ICommand.CanExecuteChanged> a zakázat, pokud <xref:System.Windows.Input.ICommand.CanExecute%2A> vrátí `false` nebo být povoleno, pokud <xref:System.Windows.Input.ICommand.CanExecute%2A> vrátí `true`.  
  
 Sémantika příkazu může být konzistentní napříč aplikacemi a třídami, ale logika akce je specifická pro konkrétní objekt, na kterém se jednalo. Kombinace kláves CTRL + X Vyvolá příkaz **Vyjmout** v textových třídách, třídách obrázků a webových prohlížečích, ale skutečná logika pro provedení operace **Vyjmout** je definována aplikací, která provádí vyjmutí. @No__t-0 umožňuje klientům implementovat logiku. Textový objekt může Vyjmout vybraný text do schránky, zatímco objekt obrázku může Vyjmout vybraný obrázek. Když aplikace zpracovává událost <xref:System.Windows.Input.CommandManager.Executed>, má přístup k cíli příkazu a může provést odpovídající akci v závislosti na typu cíle.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>Příklad jednoduchého příkazu v subsystému WPF  
 Nejjednodušší způsob, jak použít příkaz v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je použít předdefinovaný <xref:System.Windows.Input.RoutedCommand> z jedné z tříd knihovny příkazů; Použijte ovládací prvek, který má nativní podporu pro zpracování příkazu; a použijte ovládací prvek, který má nativní podporu pro vyvolání příkazu.  Příkaz <xref:System.Windows.Input.ApplicationCommands.Paste%2A> je jedním z předdefinovaných příkazů třídy <xref:System.Windows.Input.ApplicationCommands>.  Ovládací prvek <xref:System.Windows.Controls.TextBox> má vestavěnou logiku pro zpracování příkazu <xref:System.Windows.Input.ApplicationCommands.Paste%2A>.  A třída <xref:System.Windows.Controls.MenuItem> má nativní podporu pro vyvolání příkazů.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.MenuItem> tak, že když na ni kliknete, vyvolá příkaz <xref:System.Windows.Input.ApplicationCommands.Paste%2A> na <xref:System.Windows.Controls.TextBox> za předpokladu, že <xref:System.Windows.Controls.TextBox> má fokus klávesnice.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>Tři hlavní koncepty v příkazech WPF  
 Model směrovaného příkazu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lze rozdělit do čtyř hlavních konceptů: příkaz, zdroj příkazu, cíl příkazu a vazba příkazu:  
  
- *Příkaz* je akce, která má být provedena.  
  
- *Zdroj příkazu* je objekt, který vyvolá příkaz.  
  
- *Cíl příkazu* je objekt, na kterém je příkaz spuštěn.  
  
- *Vazba příkazu* je objekt, který mapuje logiku příkazu na příkaz.  
  
 V předchozím příkladu je příkaz <xref:System.Windows.Input.ApplicationCommands.Paste%2A> příkazem, <xref:System.Windows.Controls.MenuItem> je zdrojem příkazu, <xref:System.Windows.Controls.TextBox> je cílový příkaz a vazba příkazu je poskytována ovládacím prvkem <xref:System.Windows.Controls.TextBox>.  Je potřeba poznamenat, že není vždy v případě, že je <xref:System.Windows.Input.CommandBinding> dodán ovládacím prvkem, který je třídou cíle příkazu.  Poměrně často <xref:System.Windows.Input.CommandBinding> musí vytvořit vývojář aplikace, nebo <xref:System.Windows.Input.CommandBinding> může být připojen k předchůdci cíle příkazu.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Příkazy  
 Příkazy v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou vytvořeny implementací rozhraní <xref:System.Windows.Input.ICommand>.  <xref:System.Windows.Input.ICommand> zpřístupňuje dvě metody, <xref:System.Windows.Input.ICommand.Execute%2A> a <xref:System.Windows.Input.ICommand.CanExecute%2A> a událost, <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A> provede akce, které jsou přidruženy k příkazu. <xref:System.Windows.Input.ICommand.CanExecute%2A> určuje, zda se příkaz může spustit na aktuálním cíli příkazu. <xref:System.Windows.Input.ICommand.CanExecuteChanged> je vyvolána, pokud správce příkazů, který centralizaci operací příkazového řádku detekuje změnu ve zdroji příkazu, který by mohl znehodnotit příkaz, který byl vyvolán, ale ještě nebyl proveden vazbou příkazu.  Implementace <xref:System.Windows.Input.ICommand> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je třídou <xref:System.Windows.Input.RoutedCommand> a je zaměřuje se na tento přehled.  
  
 Hlavní zdroje vstupu v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou myš, klávesnice, rukopis a směrované příkazy.  Další vstupy zaměřené na zařízení používají <xref:System.Windows.RoutedEvent> pro upozorňování objektů na stránce aplikace, ke kterým došlo ke vstupní události.  @No__t-0 se neliší.  Metody <xref:System.Windows.Input.RoutedCommand.Execute%2A> a <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> <xref:System.Windows.Input.RoutedCommand> neobsahují aplikační logiku pro příkaz, ale místo toho vyvolávají směrované události, které se provedou tunelem a bublinou prostřednictvím stromu elementů, dokud nenaleznou objekt s <xref:System.Windows.Input.CommandBinding>.  @No__t-0 obsahuje obslužné rutiny pro tyto události a jedná se o obslužné rutiny, které provádějí příkaz.  Další informace o směrování událostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 Metoda <xref:System.Windows.Input.RoutedCommand.Execute%2A> u <xref:System.Windows.Input.RoutedCommand> vyvolává události <xref:System.Windows.Input.CommandManager.PreviewExecuted> a <xref:System.Windows.Input.CommandManager.Executed> v cíli příkazu.  Metoda <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> u <xref:System.Windows.Input.RoutedCommand> vyvolává události <xref:System.Windows.Input.CommandManager.CanExecute> a <xref:System.Windows.Input.CommandManager.PreviewCanExecute> v cíli příkazu.  Tyto události se procházejí tunelem a bublinou přes strom elementů, dokud nenaleznou objekt, který má pro tento konkrétní příkaz <xref:System.Windows.Input.CommandBinding>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dodá sadu běžných směrovaných příkazů, které jsou rozloženy mezi několik tříd: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands> a <xref:System.Windows.Documents.EditingCommands>.  Tyto třídy sestávají pouze objekty <xref:System.Windows.Input.RoutedCommand> a nikoli logika implementace příkazu.  Logika implementace je zodpovědností objektu, na kterém je příkaz spuštěn.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Zdroje příkazů  
 Zdroj příkazu je objekt, který vyvolá příkaz.  Příklady zdrojů příkazů jsou <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button> a <xref:System.Windows.Input.KeyGesture>.  
  
 Zdroje příkazů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obecně implementují rozhraní <xref:System.Windows.Input.ICommandSource>.  
  
 <xref:System.Windows.Input.ICommandSource> zpřístupňuje tři vlastnosti: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> a <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A> je příkaz, který se má provést, když je vyvolán zdroj příkazu.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> je objekt, na kterém se má příkaz Spustit.  Je třeba poznamenat, že v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vlastnost <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> v <xref:System.Windows.Input.ICommandSource> platná pouze v případě, že je <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand>.  Pokud je <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nastavená na <xref:System.Windows.Input.ICommandSource> a odpovídající příkaz není <xref:System.Windows.Input.RoutedCommand>, cíl příkazu se ignoruje. Pokud není nastavena hodnota <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, element s fokusem klávesnice bude cílem příkazu.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> je uživatelsky definovaný datový typ, který slouží k předávání informací obslužným rutinám implementující příkaz.  
  
 Třídy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které implementují <xref:System.Windows.Input.ICommandSource>, jsou <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink> a <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem> a <xref:System.Windows.Documents.Hyperlink> Vyvolá příkaz po kliknutí a <xref:System.Windows.Input.InputBinding> Vyvolá příkaz, když je proveden <xref:System.Windows.Input.InputGesture>.  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Controls.MenuItem> v <xref:System.Windows.Controls.ContextMenu> jako zdroj příkazu pro příkaz <xref:System.Windows.Input.ApplicationCommands.Properties%2A>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Zdroj příkazu obvykle naslouchá události <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged>.  Tato událost informuje zdroj příkazu, že se mohla změnit schopnost příkazu spustit na aktuálním cíli příkazu.  Zdroj příkazu může zadat dotaz na aktuální stav <xref:System.Windows.Input.RoutedCommand> pomocí metody <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>.  Zdroj příkazu se pak může vypnout, pokud příkaz nejde provést.  Příkladem je <xref:System.Windows.Controls.MenuItem> odbarvení samotného, když příkaz nelze provést.  
  
 @No__t-0 se dá použít jako zdroj příkazu.  Dva typy vstupních gest v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.MouseGesture>.  @No__t-0 si můžete představit jako klávesovou zkratku, například CTRL + C.  @No__t-0 se skládá z <xref:System.Windows.Input.Key> a sady <xref:System.Windows.Input.ModifierKeys>.  @No__t-0 se skládá z <xref:System.Windows.Input.MouseAction> a volitelné sady <xref:System.Windows.Input.ModifierKeys>.  
  
 Aby <xref:System.Windows.Input.InputGesture> fungoval jako zdroj příkazu, musí být přidružen k příkazu. Existuje několik způsobů, jak to provést.  Jedním ze způsobů je použít <xref:System.Windows.Input.InputBinding>.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.KeyBinding> mezi <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Dalším způsobem, jak přidružit <xref:System.Windows.Input.InputGesture> k <xref:System.Windows.Input.RoutedCommand>, je přidání <xref:System.Windows.Input.InputGesture> do <xref:System.Windows.Input.InputGestureCollection> na <xref:System.Windows.Input.RoutedCommand>.  
  
 Následující příklad ukazuje, jak přidat <xref:System.Windows.Input.KeyGesture> do <xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 @No__t-0 přidruží příkaz k obslužným rutinám událostí, které implementují příkaz.  
  
 Třída <xref:System.Windows.Input.CommandBinding> obsahuje vlastnost <xref:System.Windows.Input.CommandBinding.Command%2A> a události <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> a <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> je příkaz, ke kterému je přidružena <xref:System.Windows.Input.CommandBinding>.  Obslužné rutiny událostí, které jsou připojeny k událostem <xref:System.Windows.Input.CommandBinding.PreviewExecuted> a <xref:System.Windows.Input.CommandBinding.Executed> implementují příkazovou logiku.  Obslužné rutiny události připojené k událostem <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> a <xref:System.Windows.Input.CommandBinding.CanExecute> určují, zda lze příkaz provést na aktuálním cíli příkazu.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Input.CommandBinding> v kořenovém <xref:System.Windows.Window> aplikace.  @No__t-0 přidruží příkaz <xref:System.Windows.Input.ApplicationCommands.Open%2A> s obslužnými rutinami <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandBinding.CanExecute>.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 V dalším kroku se vytvoří <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.Input.CanExecuteRoutedEventHandler>.  @No__t-0 otevře <xref:System.Windows.MessageBox>, který zobrazí řetězec oznamující, že byl příkaz proveden.  Hodnota <xref:System.Windows.Input.CanExecuteRoutedEventHandler> nastaví vlastnost <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> na hodnotu `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 @No__t-0 je připojen ke konkrétnímu objektu, jako je například kořen <xref:System.Windows.Window> aplikace nebo ovládací prvek.  Objekt, ke kterému je <xref:System.Windows.Input.CommandBinding> připojen, definuje rozsah vazby.  Například <xref:System.Windows.Input.CommandBinding> připojen k předchůdci cílového příkazu je možné dosáhnout událostí <xref:System.Windows.Input.CommandBinding.Executed>, ale nelze získat <xref:System.Windows.Input.CommandBinding> připojené k následníkovi cílového příkazu.  Toto je přímá sekvence způsobu, jakým jsou tunely <xref:System.Windows.RoutedEvent> tunely a bubliny z objektu, který vyvolává událost.  
  
 V některých situacích je <xref:System.Windows.Input.CommandBinding> připojen k samotnému cíli příkazu, například s třídou <xref:System.Windows.Controls.TextBox> a příkazy <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A> a <xref:System.Windows.Input.ApplicationCommands.Paste%2A>. Poměrně často ale je pohodlnější připojit <xref:System.Windows.Input.CommandBinding> k předchůdci cíle příkazu, jako je například hlavní <xref:System.Windows.Window> nebo objekt aplikace, zejména v případě, že je možné použít stejný <xref:System.Windows.Input.CommandBinding> pro více cílů příkazu.  Jedná se o rozhodnutí o návrhu, která budete chtít vzít v úvahu při vytváření infrastruktury pro příkazy.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Cíl příkazu  
 Cíl příkazu je prvek, na kterém je příkaz spuštěn.  S ohledem na <xref:System.Windows.Input.RoutedCommand> je cílem příkazu prvek, na kterém se spouští směrování <xref:System.Windows.Input.CommandManager.Executed> a <xref:System.Windows.Input.CommandManager.CanExecute>.  Jak bylo uvedeno dříve, v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vlastnost <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> v <xref:System.Windows.Input.ICommandSource> platná pouze v případě, že je <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand>.  Pokud je <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> nastavená na <xref:System.Windows.Input.ICommandSource> a odpovídající příkaz není <xref:System.Windows.Input.RoutedCommand>, cíl příkazu se ignoruje.  
  
 Zdroj příkazu může explicitně nastavit cíl příkazu.  Pokud není definován cíl příkazu, bude element s fokusem klávesnice použit jako cíl příkazu.  Jedna z výhod použití prvku s fokusem klávesnice jako cílovým příkazem je, že umožňuje vývojářům aplikací použít stejný zdroj příkazů k vyvolání příkazu na více cílech bez nutnosti sledovat cíl příkazu.  Pokud například <xref:System.Windows.Controls.MenuItem> vyvolá příkaz **Vložit** v aplikaci, která má ovládací prvek <xref:System.Windows.Controls.TextBox> a ovládací prvek <xref:System.Windows.Controls.PasswordBox>, může být cílem buď <xref:System.Windows.Controls.TextBox>, nebo <xref:System.Windows.Controls.PasswordBox> v závislosti na tom, který ovládací prvek má fokus klávesnice.  
  
 Následující příklad ukazuje, jak explicitně nastavit cíl příkazu v kódu a v kódu na pozadí.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>Objekt CommandManager  
 @No__t-0 slouží k provádění několika funkcí souvisejících s příkazy.  Poskytuje sadu statických metod pro přidávání a odebírání obslužných rutin událostí <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute> a <xref:System.Windows.Input.CommandManager.CanExecute> do a z konkrétního prvku.  Poskytuje prostředky k registraci objektů <xref:System.Windows.Input.CommandBinding> a <xref:System.Windows.Input.InputBinding> do konkrétní třídy.  @No__t-0 také poskytuje prostředky prostřednictvím události <xref:System.Windows.Input.CommandManager.RequerySuggested> k upozornění příkazu, když by měl vyvolat událost <xref:System.Windows.Input.ICommand.CanExecuteChanged>.  
  
 Metoda <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> vynutí, aby <xref:System.Windows.Input.CommandManager> vyvolalo událost <xref:System.Windows.Input.CommandManager.RequerySuggested>.  To je užitečné pro podmínky, které by měly zakázat nebo povolit příkaz, ale nejedná se o podmínky, o kterých <xref:System.Windows.Input.CommandManager> ví.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Knihovna příkazů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje sadu předdefinovaných příkazů.  Knihovna příkazů se skládá z následujících tříd: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands> a <xref:System.Windows.Input.ComponentCommands>.  Tyto třídy poskytují příkazy, jako <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> a <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A> a <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Mnohé z těchto příkazů zahrnují sadu výchozích vstupních vazeb.  Například pokud určíte, že vaše aplikace zpracovává příkaz pro kopírování, získáte automaticky vazbu klávesnice "CTRL + C", a také získáte vazby pro jiná vstupní zařízení, jako jsou například gesta pera tabletového počítače a informace o řeči.  
  
 Když odkazujete na příkazy v různých knihovnách příkazů pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], je obvykle možné vynechat název třídy knihovny, která zveřejňuje vlastnost statického příkazu. Obecně jsou názvy příkazů jednoznačné jako řetězce a vlastnící typy existují k poskytnutí logického seskupení příkazů, ale nejsou nutné pro nejednoznačnost. Můžete například zadat `Command="Cut"` místo podrobnější `Command="ApplicationCommands.Cut"`. Toto je praktický mechanismus, který je integrovaný do procesoru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro příkazy (přesněji se jedná o chování konvertoru typu <xref:System.Windows.Input.ICommand>, které se v době načítání odkazy na procesor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Vytváření vlastních příkazů  
 Pokud příkazy v třídách knihovny příkazů nevyhovují vašim požadavkům, můžete vytvořit vlastní příkazy.  Existují dva způsoby, jak vytvořit vlastní příkaz.  První je začít od základu a implementovat rozhraní <xref:System.Windows.Input.ICommand>.  Druhým způsobem a běžnějším přístupem je vytvoření <xref:System.Windows.Input.RoutedCommand> nebo <xref:System.Windows.Input.RoutedUICommand>.  
  
 Příklad vytvoření vlastní <xref:System.Windows.Input.RoutedCommand> najdete v tématu [Vytvoření vlastní ukázky RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Přehled vstupu](input-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Implementace rozhraní ICommandSource](how-to-implement-icommandsource.md)
- [Postupy: Přidání příkazu do nabídky MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Vytvoření vlastní ukázky RoutedCommand](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
