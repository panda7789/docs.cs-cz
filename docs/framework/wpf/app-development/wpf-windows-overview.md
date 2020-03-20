---
title: Windows – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145537"
---
# <a name="wpf-windows-overview"></a>Přehled WPF Windows
Uživatelé interagují se samostatnými aplikacemi Windows Presentation Foundation (WPF) prostřednictvím oken. Primárním účelem okna je hostování obsahu, který vizualizuje data a umožňuje uživatelům pracovat s daty. Samostatné wpf aplikace poskytují vlastní okna <xref:System.Windows.Window> pomocí třídy. Toto téma <xref:System.Windows.Window> představuje před pokrývající základy vytváření a správy oken v samostatných aplikacích.  
  
> [!NOTE]
> WPF aplikace hostované v prohlížeči, včetně aplikací prohlížeče XAML (XBAPs) a volných [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránek, neposkytují vlastní okna. Místo toho jsou hostovány v oknech poskytovaných aplikací Windows Internet Explorer. Viz [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Třída okna  
 Následující obrázek znázorňuje jednotlivé části okna:  
  
 ![Snímek obrazovky, který zobrazuje prvky okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno je rozděleno do dvou oblastí: neklientská oblast a klientská oblast.  
  
 Oblast, která *není klientem* okna, je implementována wpf a zahrnuje části okna, které jsou společné pro většinu oken, včetně následujících:  
  
- Hranice.  
  
- Záhlaví.  
  
- Ikona.  
  
- Minimalizovat, maximalizovat a obnovit tlačítka.  
  
- Tlačítko Zavřít.  
  
- Nabídka Systém s položkami nabídky, které uživatelům umožňují minimalizovat, maximalizovat, obnovit, přesunout, změnit velikost a zavřít okno.  
  
 Klientská *oblast* okna je oblast v oblasti mimo klienta a vývojáři ji používají k přidání obsahu specifického pro aplikaci, jako jsou panely nabídek, panely nástrojů a ovládací prvky.  
  
 V WPF okno je zapouzdřen třídy, <xref:System.Windows.Window> které používáte k provedení následujícího:  
  
- Zobrazení okna.  
  
- Nakonfigurujte velikost, umístění a vzhled okna.  
  
- Hostitelský obsah specifický pro aplikaci.  
  
- Spravujte životnost okna.  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Implementace okna  
 Implementace typického okna se skládá z vzhledu i chování, kde *vzhled* definuje vzhled okna pro uživatele a *chování* definuje způsob, jakým okno funguje při interakci uživatelů s ním. V WPF můžete implementovat vzhled a chování okna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí kódu nebo značky.  
  
 Obecně je však vzhled okna implementován pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a jeho chování je implementováno pomocí kódu na pozadí, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Chcete-li [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] povolit, aby soubor se značkami a soubor s kódem na pozadí spolupracovaly, jsou vyžadovány následující:  
  
- Ve značkách `Window` musí prvek `x:Class` obsahovat atribut. Když je aplikace vytvořena, `x:Class` existence v souboru značek způsobí, že modul sestavení `partial` společnosti Microsoft <xref:System.Windows.Window> (MSBuild) vytvoří třídu, která je odvozena od atributu a má název, který je určen `x:Class` atributem. To vyžaduje přidání deklarace oboru názvů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XML pro `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` schéma ( ). Vygenerovaná `partial` třída `InitializeComponent` implementuje metodu, která je volána k registraci událostí a nastavení vlastností, které jsou implementovány v přirážce.  
  
- V kódu na pozadí musí `partial` být třída se stejným názvem, `x:Class` který je určen atributem <xref:System.Windows.Window>v přirážce a musí být odvozen z . To umožňuje soubor s kódem na `partial` pozadí, který má být přidružen ke třídě, která je generována pro soubor značek při sestavení aplikace (viz [Vytváření aplikace WPF).](building-a-wpf-application-wpf.md)  
  
- V kódu na <xref:System.Windows.Window> pozadí, třída musí implementovat `InitializeComponent` konstruktor, který volá metodu. `InitializeComponent`je implementována vygenerovanou `partial` třídou souboru značek pro registraci událostí a nastavení vlastností, které jsou definovány ve značkách.  
  
> [!NOTE]
> Přidáte-li nový <xref:System.Windows.Window> do projektu pomocí sady <xref:System.Windows.Window> Visual Studio, je implementována pomocí značek a kód na pozadí a zahrnuje potřebnou konfiguraci k vytvoření přidružení mezi soubory značky a kód na pozadí, jak je popsáno zde.  
  
 S touto konfigurací na místě, můžete se zaměřit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na definování vzhledu okna v značky a provádění jeho chování v kódu na pozadí. Následující příklad ukazuje okno s tlačítkem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementovaným ve značkách a obslužnou rutinou události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost tlačítka implementovanou v kódu na pozadí.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurace definice okna pro msbuild  
 Způsob implementace okna určuje, jak je nakonfigurován pro MSBuild. Pro okno, které je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] definováno pomocí značek a kódu na pozadí:  
  
- Soubory značek XAML jsou konfigurovány `Page` jako položky MSBuild.  
  
- Soubory s kódem na pozadí `Compile` jsou konfigurovány jako položky MSBuild.  
  
 To je znázorněno v následujícím souboru projektu MSBuild.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Informace o vytváření aplikací WPF naleznete [v tématu Vytváření aplikace WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Životnost okna  
 Stejně jako u všech tříd má okno životnost, která začíná při prvním vytvoření instance, po které je otevřena, aktivována a deaktivována a nakonec uzavřena.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Otevření okna  
 Chcete-li otevřít okno, nejprve vytvořte jeho instanci, která je znázorněna v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, <xref:System.Windows.Application.Startup> ke kterému dochází při vyvolání události.  
  
 Při vytvoření instance okna je odkaz na něj automaticky přidán do seznamu oken, <xref:System.Windows.Application> který <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>je spravován objektem (viz ). Kromě toho první okno, které má být vytvořena instance <xref:System.Windows.Application> je ve výchozím nastavení <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>nastavena jako hlavní okno aplikace (viz).  
  
 Okno je nakonec otevřen <xref:System.Windows.Window.Show%2A> voláním metody; výsledek je zobrazen na následujícím obrázku.  
  
 ![Okno otevřené voláním Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno, které je <xref:System.Windows.Window.Show%2A> otevřeno voláním je nemodlavé okno, což znamená, že aplikace pracuje v režimu, který umožňuje uživatelům aktivovat jiná okna ve stejné aplikaci.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>je volána k otevření oken, jako jsou dialogová okna modálně. Další informace najdete v [tématu Přehled dialogových oken.](dialog-boxes-overview.md)  
  
 Při <xref:System.Windows.Window.Show%2A> volání, okno provádí inicializační práce před je zobrazen a vytvořit infrastrukturu, která umožňuje přijímat vstup uživatele. Když je okno inicializováno, je vyvolána <xref:System.Windows.Window.SourceInitialized> událost a okno se zobrazí.  
  
 Jako zástupce <xref:System.Windows.Application.StartupUri%2A> lze nastavit, aby bylo možné určit první okno, které se otevře automaticky při spuštění aplikace.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Při spuštění aplikace je okno určené <xref:System.Windows.Application.StartupUri%2A> hodnotou otevřeno nemodálně; interně okno se otevře voláním jeho <xref:System.Windows.Window.Show%2A> metody.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Vlastnictví okna  
 Okno, které je otevřeno <xref:System.Windows.Window.Show%2A> pomocí metody nemá implicitní vztah s oknem, který jej vytvořil; Uživatelé mohou pracovat s oběma okny nezávisle na druhém, což znamená, že jedno okno může provést následující akce:  
  
- Zakryjte druhé (pokud jedno z <xref:System.Windows.Window.Topmost%2A> oken `true`nemá svou vlastnost nastavenou na).  
  
- Být minimalizovány, maximalizovány a obnoveny bez ovlivnění ostatních.  
  
 Některá okna vyžadují vztah s oknem, které je otevře. Například aplikace integrovaného vývojového prostředí (IDE) může otevřít okna vlastností a okna nástrojů, jejichž typické chování je pokrýt okno, které je vytváří. Kromě toho by tato okna měla vždy zavřít, minimalizovat, maximalizovat a obnovit ve shodě s oknem, které je vytvořilo. Takový vztah lze vytvořit tím, že jedno okno *vlastní* <xref:System.Windows.Window.Owner%2A> jiné a je dosaženo nastavením *vlastnosti vlastněného okna* s odkazem na *okno vlastníka*. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po navázání vlastnictví:  
  
- Vlastněné okno může odkazovat na okno vlastníka kontrolou hodnoty jeho <xref:System.Windows.Window.Owner%2A> vlastnosti.  
  
- Okno vlastníka můžete zjistit všechna okna, která vlastní <xref:System.Windows.Window.OwnedWindows%2A> kontrolou hodnoty jeho vlastnosti.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Zabránění aktivaci okna  
 Existují scénáře, kde by okna by neměla být aktivována při zobrazení, jako jsou například okna konverzace aplikace ve stylu messenger Internetu nebo okna oznámení e-mailové aplikace.  
  
 Pokud vaše aplikace má okno, které by neměly být <xref:System.Windows.Window.ShowActivated%2A> aktivovány při zobrazení, můžete nastavit jeho vlastnost `false` před voláním <xref:System.Windows.Window.Show%2A> metody poprvé. V důsledku toho:  
  
- Okno není aktivováno.  
  
- Událost okna <xref:System.Windows.Window.Activated> není aktivována.  
  
- Aktuálně aktivované okno zůstane aktivováno.  
  
 Okno se však aktivuje, jakmile jej uživatel aktivuje kliknutím na klientskou nebo neklientskou oblast. V tomto případě:  
  
- Okno je aktivováno.  
  
- Událost okna <xref:System.Windows.Window.Activated> je aktivována.  
  
- Dříve aktivované okno je deaktivováno.  
  
- Okno a <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> události jsou následně aktivována podle očekávání v reakci na akce uživatele.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Aktivace okna  
 Při prvním otevření se okno stane aktivním oknem <xref:System.Windows.Window.ShowActivated%2A> (pokud `false`není zobrazeno s nastavenou na ). *Aktivní okno* je okno, které právě zachytává vstup uživatele, například stisknutí kláves a kliknutí myší. Když se okno aktivuje, <xref:System.Windows.Window.Activated> vyvolá událost.  
  
> [!NOTE]
> Při prvním otevření okna <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.Window.ContentRendered> události jsou vyvolány pouze po vyvolání <xref:System.Windows.Window.Activated> události. S ohledem na tuto skutečnost může být <xref:System.Windows.Window.ContentRendered> okno skutečně považováno za otevřené, když je zvednuto.  
  
 Jakmile se okno aktivuje, může uživatel aktivovat jiné okno ve stejné aplikaci nebo aktivovat jinou aplikaci. V takovém případě se aktuálně aktivní okno deaktivuje a vyvolá <xref:System.Windows.Window.Deactivated> událost. Podobně když uživatel vybere aktuálně deaktivované okno, okno se <xref:System.Windows.Window.Activated> znovu aktivuje a je aktivováno.  
  
 Jedním z běžných důvodů pro zpracování <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> je povolit a zakázat funkce, které lze spustit pouze v případě, že je aktivní okno. Některá okna například zobrazují interaktivní obsah, který vyžaduje neustálý vstup uživatele nebo pozornost, včetně her a přehrávačů videa. Následující příklad je zjednodušený přehrávač videa, <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> který ukazuje, jak zpracovat a implementovat toto chování.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Jiné typy aplikací může stále spustit kód na pozadí při deaktivaci okna. Poštovní klient může například pokračovat v dotazování poštovního serveru, zatímco uživatel používá jiné aplikace. Aplikace, jako jsou tyto často poskytují různé nebo další chování, zatímco hlavní okno je deaktivován. Pokud jde o poštovní program, může to znamenat jak přidání nové položky pošty do složky Doručená pošta, tak přidání ikony oznámení do systémové lišty. Ikonu oznámení je třeba zobrazit pouze v případě, že okno pošty není <xref:System.Windows.Window.IsActive%2A> aktivní, což lze určit kontrolou vlastnosti.  
  
 Pokud úloha na pozadí dokončí, okno může chtít upozornit <xref:System.Windows.Window.Activate%2A> uživatele naléhavěji voláním metody. Pokud uživatel pracuje s jinou <xref:System.Windows.Window.Activate%2A> aplikací aktivovanou při volání, tlačítko hlavního panelu okna bliká. Pokud uživatel pracuje s aktuální aplikací, <xref:System.Windows.Window.Activate%2A> volání přenese okno do popředí.  
  
> [!NOTE]
> Můžete zpracovat aktivaci oboru <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> aplikace pomocí události a.  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>Zavření okna  
 Životnost okna začne končit, když jej uživatel zavře. Okno lze zavřít pomocí prvků v oblasti mimo klienta, včetně následujících:  
  
- Položka **Zavřít** v nabídce **Systém.**  
  
- Stisknutím kláves ALT+F4.  
  
- Stisknutím tlačítka **Zavřít.**  
  
 Můžete poskytnout další mechanismy do oblasti klienta zavřít okno, častější, které zahrnují následující:  
  
- **Ukončit** položku v nabídce **Soubor,** obvykle pro hlavní okna aplikace.  
  
- A **Zavřít** položku v nabídce **Soubor,** obvykle v sekundárním okně aplikace.  
  
- Tlačítko **Storno,** obvykle v modálním dialogovém okně.  
  
- Tlačítko **Zavřít,** obvykle v nemodálním dialogovém okně.  
  
 Chcete-li zavřít okno v reakci na jeden z těchto <xref:System.Windows.Window.Close%2A> vlastních mechanismů, je třeba volat metodu. Následující příklad implementuje možnost zavřít okno výběrem **exit** v nabídce **Soubor.**  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Když se okno zavře, vyvolá <xref:System.Windows.Window.Closing> dvě <xref:System.Windows.Window.Closed>události: a .  
  
 <xref:System.Windows.Window.Closing>je aktivována před zavřením okna a poskytuje mechanismus, kterým lze zabránit uzavření okna. Jedním z běžných důvodů, proč zabránit uzavření okna, je, pokud obsah okna obsahuje upravená data. V takovém případě <xref:System.Windows.Window.Closing> událost může být zpracována k určení, zda jsou data znečištěná, a pokud ano, požádat uživatele, zda pokračovat v zavírání okna bez uložení dat nebo zrušit zavření okna. Následující příklad ukazuje klíčové aspekty <xref:System.Windows.Window.Closing>zpracování .  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing> Obslužná <xref:System.ComponentModel.CancelEventArgs>rutina události `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> je předána `true` , která implementuje vlastnost, kterou jste nastavili, abyste zabránili zavření okna.  
  
 Pokud <xref:System.Windows.Window.Closing> není zpracována, nebo je zpracována, ale není zrušena, okno se zavře. Těsně předtím, než se <xref:System.Windows.Window.Closed> okno skutečně zavře, je zvednut. V tomto okamžiku nelze zabránit zavření okna.  
  
> [!NOTE]
> Aplikaci lze nakonfigurovat tak, aby se automaticky vypnula, když se zavře (viz) <xref:System.Windows.Application.MainWindow%2A>nebo poslední okno. Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Zatímco okno může být explicitně uzavřeno prostřednictvím mechanismů poskytovaných v oblastech bez klienta a klienta, okno může být také implicitně uzavřeno v důsledku chování v jiných částech aplikace nebo systému Windows, včetně následujících:  
  
- Uživatel se odhlásí nebo vypne systém Windows.  
  
- Majitel okna se zavře (viz). <xref:System.Windows.Window.Owner%2A>  
  
- Hlavní okno aplikace je <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>uzavřeno a je .  
  
- <xref:System.Windows.Application.Shutdown%2A>se nazývá.  
  
> [!NOTE]
> Po zavření nelze okno znovu otevřít.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Události životnosti okna  
 Následující obrázek znázorňuje posloupnost hlavních událostí v životnosti okna:  
  
 ![Diagram, který zobrazuje události v okně životnost.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Následující obrázek znázorňuje posloupnost hlavních událostí v pocelou<xref:System.Windows.Window.ShowActivated%2A> dobu životnosti okna, které je zobrazeno bez aktivace ( je nastaveno na `false` před zobrazením okna):  
  
 ![Diagram, který zobrazuje události v okně životnost bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Umístění okna  
 Když je okno otevřené, má umístění v rozměrech x a y vzhledem k ploše. Toto umístění lze určit <xref:System.Windows.Window.Left%2A> kontrolou <xref:System.Windows.Window.Top%2A> vlastnosti a, resp. Tyto vlastnosti můžete nastavit tak, aby se změnilo umístění okna.  
  
 Můžete také určit počáteční umístění <xref:System.Windows.Window> při prvním zjevu <xref:System.Windows.Window.WindowStartupLocation%2A> nastavením <xref:System.Windows.WindowStartupLocation> vlastnosti s jednou z následujících hodnot výčtu:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner>(výchozí)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Pokud je umístění při <xref:System.Windows.WindowStartupLocation.Manual>spuštění <xref:System.Windows.Window.Left%2A> zadáno jako a vlastnosti a <xref:System.Windows.Window.Top%2A> nebyly nastaveny, požádá systém Windows o umístění, <xref:System.Windows.Window> ve které se má zobrazit.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>Nejvyšší okna a pořadí vykreslované  
 Kromě umístění x a y má okno také umístění v dimenzi z, které určuje jeho svislou polohu vzhledem k ostatním oknům. To se označuje jako pořadí vykreslační pořadí okna a existují dva typy: normální pořadí vykreslační a nejvyšší pořadí vykresl. Umístění okna v *normálním pořadí vykreslování* je určeno tím, zda je aktuálně aktivní či nikoli. Ve výchozím nastavení je okno umístěno v normálním pořadí vykresláčů. Umístění okna v *nejvyšším pořadí vykreslování* je také určeno tím, zda je aktuálně aktivní nebo ne. Kromě toho jsou okna v nejvyšším pořadí vykreslovaného stavu vždy umístěna nad okny v normálním pořadí vykreslovaného. Okno je umístěno v nejvyšším pořadí vykreslování nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnosti na `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 V každém pořadí vykreslovaného se aktuálně aktivní okno zobrazí nad všemi ostatními okny ve stejném pořadí vykresládek.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Velikost okna  
 Kromě umístění na ploše má okno velikost, která je určena několika vlastnostmi, <xref:System.Windows.Window.SizeToContent%2A>včetně různých vlastností šířky a výšky a .  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.MaxWidth%2A> slouží ke správě rozsahu šířek, které může mít okno během své životnosti, a jsou konfigurovány tak, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Výška okna <xref:System.Windows.FrameworkElement.MinHeight%2A>je <xref:System.Windows.FrameworkElement.Height%2A>spravována aplikacemi , a <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a je konfigurována tak, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Vzhledem k tomu, že různé hodnoty šířky a hodnoty výšky každý určit rozsah, je možné, že šířka a výška okna s nastavitelnou velikostí být kdekoli v rámci zadaného rozsahu pro příslušnou dimenzi. Chcete-li zjistit jeho aktuální <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>šířku a výšku, zkontrolujte a , resp.  
  
 Pokud chcete, aby šířka a výška okna měla velikost, která odpovídá velikosti obsahu okna, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnost, která má následující hodnoty:  
  
- <xref:System.Windows.SizeToContent.Manual>. Žádný efekt (výchozí).  
  
- <xref:System.Windows.SizeToContent.Width>. Přizpůsobit šířce obsahu, což má stejný <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> účinek jako nastavení obsahu i šířky obsahu.  
  
- <xref:System.Windows.SizeToContent.Height>. Přizpůsobit výšce obsahu, která má stejný <xref:System.Windows.FrameworkElement.MinHeight%2A> účinek jako nastavení obsahu i <xref:System.Windows.FrameworkElement.MaxHeight%2A> výšky obsahu.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Přizpůsobit šířce a výšce obsahu, což má <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> stejný účinek jako nastavení obsahu <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> i výšky obsahu a nastavení obsahu i šířky obsahu.  
  
 Následující příklad ukazuje okno, které automaticky velikosti, aby se vešly jeho obsah, svisle i vodorovně, při prvním zobrazení.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Window.SizeToContent%2A> nastavit vlastnost v kódu určit, jak se změní velikost okna, aby se vešly jeho obsah .
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Pořadí priorit pro vlastnosti velikosti  
 V podstatě různé velikosti vlastnosti okna kombinovat definovat rozsah šířky a výšky pro okno s nastavitelnou velikostí. Chcete-li zajistit zachování <xref:System.Windows.Window> platného rozsahu, vyhodnocuje hodnoty vlastností velikosti pomocí následujících pořadí priorit.  
  
 **Pro výškové vlastnosti:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Pro vlastnosti šířky:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Pořadí priority můžete také určit velikost okna při maximalizaci, která je <xref:System.Windows.Window.WindowState%2A> spravována s vlastností.  
  
<a name="WindowState"></a>
## <a name="window-state"></a>Stav okna  
 Během životnosti okna s nastavitelnou platností může mít tři stavy: normální, minimalizované a maximalizované. Okno s *normálním* stavem je výchozí stav okna. Okno s tímto stavem umožňuje uživateli přesunout a změnit jeho velikost pomocí uzlu pro změny velikosti nebo ohraničení, pokud je možné změnit jeho velikost.  
  
 Okno s *minimalizovaným* stavem se sbalí <xref:System.Windows.Window.ShowInTaskbar%2A> na `true`tlačítko hlavního panelu, pokud je nastaveno na ; v opačném případě se zhroutí na nejmenší možnou velikost, kterou může být, a přemístí se do levého dolního rohu plochy. Velikost žádného typu minimalizovaného okna nelze změnit pomocí ohraničení nebo uzlu pro změna velikosti, i když minimalizované okno, které není zobrazeno na hlavním panelu, lze přetáhnout po ploše.  
  
 Okno s *maximalizovaným* stavem se rozbalí na maximální velikost, která může <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A>být, <xref:System.Windows.Window.SizeToContent%2A> což bude pouze tak velké, jako je jeho , a vlastnosti diktovat. Podobně jako minimalizované okno nelze změnit velikost maximalizovaného okna pomocí uzlu pro změna velikosti nebo přetažením ohraničení.  
  
> [!NOTE]
> Hodnoty <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti okna vždy představují hodnoty pro normální stav, i když je okno aktuálně maximalizováno nebo minimalizováno.  
  
 Stav okna lze nakonfigurovat nastavením <xref:System.Windows.Window.WindowState%2A> jeho vlastnosti, která <xref:System.Windows.WindowState> může mít jednu z následujících hodnot výčtu:  
  
- <xref:System.Windows.WindowState.Normal>(výchozí)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 Následující příklad ukazuje, jak vytvořit okno, které se při otevření zobrazí jako maximalizované.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Obecně byste měli <xref:System.Windows.Window.WindowState%2A> nastavit konfiguraci počátečního stavu okna. Po zobrazení okna s nastavitelnou změnou velikosti mohou uživatelé stisknutím tlačítek minimalizovat, maximalizovat a obnovit v záhlaví okna a změnit stav okna.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Vzhled okna  
 Vzhled klientské oblasti okna změníte přidáním obsahu specifického pro okno, například tlačítek, popisků a textových polí. Chcete-li nakonfigurovat oblast <xref:System.Windows.Window> mimo klienta, <xref:System.Windows.Window.Icon%2A> poskytuje několik vlastností, <xref:System.Windows.Window.Title%2A> které zahrnují nastavení ikony okna a nastavení jeho názvu.  
  
 Vzhled a chování ohraničení neklientské oblasti můžete také změnit konfigurací režimu změny velikosti okna, stylu okna a jeho zobrazení jako tlačítka na hlavním panelu plochy.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Změna velikosti režimu  
 V závislosti <xref:System.Windows.Window.WindowStyle%2A> na vlastnosti můžete určit, jak (a pokud) mohou uživatelé změnit velikost okna. Volba stylu okna ovlivňuje, zda uživatel může změnit velikost okna přetažením jeho ohraničení myší, zda se v oblasti mimo klienta zobrazí tlačítka **Minimalizovat**, **Maximalizovat**a **Změnit velikost,** a pokud se zobrazí, zda jsou povolena.  
  
 Můžete nakonfigurovat, jak se změní <xref:System.Windows.Window.ResizeMode%2A> velikost okna nastavením jeho <xref:System.Windows.ResizeMode> vlastnosti, což může být jedna z následujících hodnot výčtu:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize>(výchozí)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Stejně <xref:System.Windows.Window.WindowStyle%2A>jako u , je nepravděpodobné, že by se režim změny velikosti okna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] během jeho životnosti změnil, což znamená, že jej s největší pravděpodobností nastavíte ze značek.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Všimněte si, že můžete zjistit, zda je okno maximalizované, <xref:System.Windows.Window.WindowState%2A> minimalizované nebo obnovené kontrolou vlastnosti.  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Styl okna  
 Ohraničení, které je vystaveno z neklientské oblasti okna, je vhodné pro většinu aplikací. Existují však okolnosti, kdy jsou zapotřebí různé typy ohraničení nebo v závislosti na typu okna nejsou zapotřebí žádné hranice.  
  
 Chcete-li určit, jaký typ ohraničení <xref:System.Windows.Window.WindowStyle%2A> okno získá, nastavte jeho <xref:System.Windows.WindowStyle> vlastnost s jedním z následujících hodnot výčtu:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow>(výchozí)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt těchto stylů oken je znázorněn na následujícím obrázku:  
  
 ![Obrázek stylů ohraničení okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek nebo kódu; protože je nepravděpodobné, že se během životnosti okna změní, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] s největší pravděpodobností ji nakonfigurujete pomocí značek.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Neobdélníkový styl okna  
 Existují také situace, kdy <xref:System.Windows.Window.WindowStyle%2A> styly ohraničení, které vám umožní mít, nejsou dostatečné. Můžete například vytvořit aplikaci s neobdélníkovým ohraničením, jako je používá program Microsoft Windows Media Player.  
  
 Zvažte například okno bubliny řeči zobrazené na následujícím obrázku:  
  
 ![Okno bubliny řeči s nápisem Drag Me.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Tento typ okna lze vytvořit <xref:System.Windows.Window.WindowStyle%2A> nastavením <xref:System.Windows.WindowStyle.None>vlastnosti na , <xref:System.Windows.Window> a pomocí speciální podpory, která má pro průhlednost.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Tato kombinace hodnot instruuje okno k vykreslení zcela transparentní. V tomto stavu nelze použít vylepšení oblasti bez klienta (nabídka Zavřít, Minimalizovat, Maximalizovat a Obnovit a tak dále). V důsledku toho musíte poskytnout své vlastní.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Přítomnost na hlavním panelu  

Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, například tlačítko znázorněné na následujícím obrázku:

 ![Snímek obrazovky s oknem s tlačítkem na hlavním panelu](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Některé typy oken nemají tlačítko na hlavním panelu, například okna se zprávami a dialogová okna (viz [Přehled dialogových oken).](dialog-boxes-overview.md) Nastavením vlastnosti (ve <xref:System.Windows.Window.ShowInTaskbar%2A> `true` výchozím nastavení) můžete určit, zda se zobrazí tlačítko hlavního panelu okna.  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Aspekty zabezpečení  
 <xref:System.Windows.Window>vyžaduje `UnmanagedCode` oprávnění zabezpečení, které má být vytvořena instance. Pro aplikace nainstalované a spuštěné z místního počítače to spadá do sady oprávnění, která jsou aplikaci udělena.  
  
 To však spadá mimo sadu oprávnění udělených aplikacím, které jsou spouštěny z oblasti Internetu nebo místní intranetu pomocí ClickOnce. V důsledku toho uživatelé obdrží clickonce upozornění zabezpečení a bude muset zvýšit oprávnění nastavena pro aplikaci na úplný vztah důvěryhodnosti.  
  
 XBAPs navíc nemůže zobrazit okna nebo dialogová okna ve výchozím nastavení. Diskuse o aspektech zabezpečení samostatných aplikací naleznete v [tématu WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Jiné typy windows  
 <xref:System.Windows.Navigation.NavigationWindow>je okno, které je určeno k hostování splavného obsahu. Další informace naleznete v tématu [Navigační přehled](navigation-overview.md)).  
  
 Dialogová okna jsou okna, která se často používají ke shromažďování informací od uživatele k dokončení funkce. Pokud například chce uživatel otevřít soubor, zobrazí se aplikace obvykle dialogové okno **Otevřít soubor,** aby uživatel získal název souboru. Další informace naleznete v [tématu Přehled dialogových oken](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Přehled dialogových oken](dialog-boxes-overview.md)
- [Sestavení aplikace WPF](building-a-wpf-application-wpf.md)
