---
title: Přehled WPF Windows
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
ms.openlocfilehash: 87d5ff67a9e95c5ec5385802d09d667ee8b6e0f9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740687"
---
# <a name="wpf-windows-overview"></a>Přehled WPF Windows
Uživatelé pracují se samostatnými aplikacemi Windows Presentation Foundation (WPF) prostřednictvím systému Windows. Hlavním účelem okna je hostování obsahu, který vizualizuje data a umožňuje uživatelům pracovat s daty. Samostatné aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytují vlastní okna pomocí <xref:System.Windows.Window> třídy. Toto téma představuje <xref:System.Windows.Window> před tím, než se seznámíte se základy vytváření a správy oken v samostatných aplikacích.  
  
> [!NOTE]
> Aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostované v prohlížeči, včetně aplikací prohlížeče XAML (XBAP) a volných [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránek, neposkytují vlastní okna. Místo toho jsou hostovány ve Windows, poskytovaném aplikací Windows Internet Explorer. Viz téma [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Třída okna  
 Následující obrázek znázorňuje prvky části okna:  
  
 ![Snímek obrazovky zobrazující prvky okna](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno je rozděleno do dvou oblastí: mimo klientské a klientské oblasti.  
  
 *Neklientská oblast* okna je implementována nástrojem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a obsahuje části okna, které jsou společné pro většinu oken, včetně následujících:  
  
- Ohraničení.  
  
- Záhlaví.  
  
- Ikona.  
  
- Tlačítka minimalizovat, maximalizovat a obnovit.  
  
- Tlačítko Zavřít  
  
- Systémová nabídka s položkami nabídky, které uživatelům umožňují minimalizovat, maximalizovat, obnovit, přesunout, změnit velikost a zavřít okno.  
  
 *Klientská oblast* okna je oblast v neklientské oblasti okna, kterou vývojáři používají k přidání obsahu specifického pro aplikaci, jako jsou například panely nabídek, panely nástrojů a ovládací prvky.  
  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]je okno zapouzdřeno pomocí <xref:System.Windows.Window> třídy, kterou použijete k provedení následujících akcí:  
  
- Zobrazí okno.  
  
- Nakonfigurujte velikost, umístění a vzhled okna.  
  
- Hostování obsahu specifického pro aplikaci.  
  
- Umožňuje spravovat dobu života okna.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implementace okna  
 Implementace typického okna zahrnuje vzhled i chování, kde *vzhled* definuje, jak okno vypadá uživatelům a *chování* definuje způsob, jakým okno funguje, jak se s ním uživatelé budou pracovat. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]můžete implementovat vzhled a chování okna pomocí kódu nebo značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Obecně je však vzhled okna implementován pomocí kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a jeho chování je implementováno pomocí kódu na pozadí, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Chcete-li povolit společné fungování souboru značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a souboru s kódem na pozadí, jsou vyžadovány následující:  
  
- V kódu `Window` element musí zahrnovat atribut `x:Class`. Když je aplikace sestavena, existence `x:Class` v souboru označení způsobí, že nástroj Microsoft Build Engine (MSBuild) vytvoří třídu `partial`, která je odvozena z <xref:System.Windows.Window> a má název, který je určen atributem `x:Class`. To vyžaduje přidání deklarace oboru názvů XML pro schéma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`). Vygenerovaná `partial` třída implementuje metodu `InitializeComponent`, která je volána k zaregistrování událostí a nastavení vlastností, které jsou implementovány v označení.  
  
- V kódu na pozadí třída musí být `partial` třídy se stejným názvem, který je určen atributem `x:Class` v kódu a musí odvozovat z <xref:System.Windows.Window>. To umožňuje, aby soubor s kódem na pozadí byl přidružen ke třídě `partial`, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).  
  
- V kódu na pozadí třída <xref:System.Windows.Window> musí implementovat konstruktor, který volá metodu `InitializeComponent`. `InitializeComponent` je implementováno třídou `partial` generované souborem označení k registraci událostí a nastavení vlastností, které jsou definovány v kódu.  
  
> [!NOTE]
> Když do projektu přidáte novou <xref:System.Windows.Window> pomocí sady Visual Studio, <xref:System.Windows.Window> je implementováno pomocí kódu a kódu na pozadí a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značkami a soubory kódu na pozadí, jak je popsáno zde.  
  
 V této konfiguraci se můžete soustředit na definování vzhledu okna v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a implementaci jeho chování v kódu na pozadí. Následující příklad ukazuje okno s tlačítkem, implementované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a obslužná rutina události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost tlačítka, implementovaná v kódu na pozadí.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurace definice okna pro MSBuild  
 Způsob implementace vašeho okna určuje, jak je nakonfigurován pro nástroj MSBuild. Pro okno, které je definováno pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu na pozadí:  
  
- Soubory značek XAML jsou konfigurovány jako `Page` položky MSBuild.  
  
- Soubory kódu na pozadí jsou nakonfigurovány jako `Compile` položky MSBuild.  
  
 Tento soubor je zobrazen v následujícím souboru projektu MSBuild.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Informace o vytváření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ch aplikací naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Doba života okna  
 Stejně jako u libovolné třídy má okno životnost, která začíná při prvním vytvoření instance, po jejím otevření, aktivaci a deaktivaci a nakonec uzavření.  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Otevření okna  
 Chcete-li otevřít okno, nejprve vytvořte jeho instanci, která je znázorněna v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 V tomto příkladu je vytvořena instance `MarkupAndCodeBehindWindow` při spuštění aplikace, ke které dojde při vyvolání události <xref:System.Windows.Application.Startup>.  
  
 Po vytvoření instance okna se odkaz na něj automaticky přidá do seznamu Windows, který je spravovaný objektem <xref:System.Windows.Application> (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Kromě toho je první okno, jehož instance má být vytvořena, ve výchozím nastavení nastaveno pomocí <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Okno je nakonec otevřeno voláním metody <xref:System.Windows.Window.Show%2A>; výsledek je znázorněn na následujícím obrázku.  
  
 ![Okno otevřené voláním okna. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno, které je otevřeno voláním <xref:System.Windows.Window.Show%2A>, je nemodální okno, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat další okna ve stejné aplikaci.  
  
> [!NOTE]
> k otevření oken, jako jsou dialogová okna, se volá <xref:System.Windows.Window.ShowDialog%2A>. Další informace najdete v tématu Přehled dialogových [oken](dialog-boxes-overview.md) .  
  
 Když se zavolá <xref:System.Windows.Window.Show%2A>, okno provede inicializační práci předtím, než se zobrazí, aby se navázala infrastruktura, která mu umožní přijímat uživatelský vstup. Po inicializaci okna se vyvolá událost <xref:System.Windows.Window.SourceInitialized> a zobrazí se okno.  
  
 Jako zástupce lze nastavit <xref:System.Windows.Application.StartupUri%2A> pro určení prvního okna, které se automaticky otevře při spuštění aplikace.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Po spuštění aplikace je okno určené hodnotou <xref:System.Windows.Application.StartupUri%2A> otevřeno nemodální. interně je okno otevřeno voláním jeho metody <xref:System.Windows.Window.Show%2A>.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Vlastnictví okna  
 Okno, které je otevřeno pomocí metody <xref:System.Windows.Window.Show%2A>, neobsahuje implicitní relaci s oknem, které ho vytvořilo. Uživatelé mohou pracovat s některým z oken nezávisle na sobě, což znamená, že jedno okno může provádět následující akce:  
  
- Zakrytí druhé (Pokud má některá z oken vlastnost <xref:System.Windows.Window.Topmost%2A> nastavena na `true`).  
  
- Minimalizujte, maximalizujete a obnovíte, aniž by to ovlivnilo druhý.  
  
 Některá okna vyžadují relaci s oknem, který je otevírá. Například aplikace integrovaného vývojového prostředí (IDE) může otevřít okna vlastností a nástrojů, jejichž typické chování je pokrýt okno, které je vytvoří. Kromě toho by tato okna měla vždycky zavřít, minimalizovat, maximalizovat a obnovit ve vzájemné součinnosti s oknem, který je vytvořil. Takový vztah lze vytvořit tak, že jednu z nich navzájem nastavíte *jako jiný a* dosáhnete nastavením vlastnosti <xref:System.Windows.Window.Owner%2A> ve *vlastnictví okna* s odkazem na *okno vlastníka*. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po navázání vlastnictví:  
  
- Vlastněné okno může odkazovat na jeho vlastní okno, a to kontrolou hodnoty vlastnosti <xref:System.Windows.Window.Owner%2A>.  
  
- Okno vlastník může zjistit, že je vlastní systém Windows, a to tak, že zkontroluje hodnotu vlastnosti <xref:System.Windows.Window.OwnedWindows%2A>.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Prevence aktivace okna  
 Existují situace, kdy by systém Windows neměl být aktivovaný, pokud je zobrazený, například okna konverzace aplikace ve stylu kurýrní služby nebo okna oznámení e-mailové aplikace.  
  
 Pokud má vaše aplikace okno, které by se nemělo aktivovat, pokud je zobrazeno, můžete nastavit jeho vlastnost <xref:System.Windows.Window.ShowActivated%2A> na `false` před prvním voláním metody <xref:System.Windows.Window.Show%2A>. Jako důsledek:  
  
- Okno není aktivováno.  
  
- Událost <xref:System.Windows.Window.Activated> okna není vyvolána.  
  
- Aktuálně aktivované okno zůstane aktivované.  
  
 Okno se aktivuje, ale jakmile ho uživatel aktivuje, klikněte buď na klienta, nebo na oblast mimo klienta. V tomto případě:  
  
- Okno je aktivováno.  
  
- Vyvolá se událost <xref:System.Windows.Window.Activated> okna.  
  
- Dříve aktivované okno je deaktivováno.  
  
- Události <xref:System.Windows.Window.Deactivated> a <xref:System.Windows.Window.Activated> okna jsou následně v reakci na akce uživatele vyvolány podle očekávání.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Aktivace okna  
 Při prvním otevření okna se zobrazí okno aktivní (Pokud se nezobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavenou na `false`). *Aktivní okno* je okno, které aktuálně zachytí vstup uživatele, například tahy kláves a kliknutí myší. Když je okno aktivní, vyvolá událost <xref:System.Windows.Window.Activated>.  
  
> [!NOTE]
> Při prvním otevření okna se události <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.Window.ContentRendered> vyvolá až po vyvolání události <xref:System.Windows.Window.Activated>. V takovém případě se může okno při vyvolání <xref:System.Windows.Window.ContentRendered> považovat za otevřené.  
  
 Po aktivaci okna může uživatel aktivovat jiné okno ve stejné aplikaci nebo aktivovat jinou aplikaci. V takovém případě se aktuálně aktivní okno deaktivuje a vyvolá událost <xref:System.Windows.Window.Deactivated>. Podobně když uživatel vybere aktuálně deaktivované okno, okno se znovu aktivuje a vygeneruje se <xref:System.Windows.Window.Activated>.  
  
 Jedním z běžných důvodů, jak zpracovávat <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated>, je povolit a zakázat funkce, které se dají spustit jenom v případě, že je okno aktivní. Například některá okna zobrazují interaktivní obsah, který vyžaduje stálý vstup uživatele nebo pozornost, včetně her a přehrávačů videí. Následující příklad je zjednodušený přehrávač videa, který ukazuje, jak zpracovat <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> k implementaci tohoto chování.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Jiné typy aplikací mohou stále spouštět kód na pozadí, když dojde k deaktivaci okna. Například poštovní klient může pokračovat v dotazování poštovního serveru, zatímco uživatel používá jiné aplikace. Tyto aplikace často poskytují jiné nebo dodatečné chování při deaktivaci hlavního okna. V souvislosti s e-mailovým programem může to znamenat, že by se nová položka pošty přidala do doručené pošty a přidala se ikona oznámení do systémového zásobníku. Ikona oznámení musí být zobrazena pouze v případě, že okno pošty není aktivní, což lze určit kontrolou vlastnosti <xref:System.Windows.Window.IsActive%2A>.  
  
 Pokud se úloha na pozadí dokončí, okno může chtít uživateli upozorňovat na naléhavější voláním metody <xref:System.Windows.Window.Activate%2A>. Pokud uživatel pracuje s jinou aplikací aktivovanou, když je zavolána <xref:System.Windows.Window.Activate%2A>, tlačítko na hlavním panelu okna bude blikat. Pokud uživatel spolupracuje s aktuální aplikací, volání <xref:System.Windows.Window.Activate%2A> přepne okno do popředí.  
  
> [!NOTE]
> Aktivaci rozsahu aplikace můžete zpracovávat pomocí <xref:System.Windows.Application.Activated?displayProperty=nameWithType> a <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>ch událostí.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Zavření okna  
 Životnost okna začíná až do konce, když ho uživatel zavře. Okno lze uzavřít pomocí prvků v neklientské oblasti, včetně následujících:  
  
- Položka **Zavřít** v **systémové** nabídce  
  
- Stiskněte kombinaci kláves ALT + F4.  
  
- Stisknutí tlačítka **Zavřít** .  
  
 Do klientské oblasti můžete poskytnout další mechanismy pro zavření okna, běžnější z nich, které zahrnují následující:  
  
- Položka **Exit** v nabídce **soubor** , obvykle pro okna hlavní aplikace.  
  
- Položka **Zavřít** v nabídce **soubor** , která se obvykle nachází v sekundárním okně aplikace.  
  
- Tlačítko **Zrušit** , obvykle v modálním dialogovém okně.  
  
- Tlačítko **Zavřít** , obvykle v nemodálním dialogovém okně.  
  
 Chcete-li zavřít okno v reakci na některý z těchto vlastních mechanismů, je třeba volat metodu <xref:System.Windows.Window.Close%2A>. Následující příklad implementuje možnost Zavřít okno výběrem možnosti **konec** v nabídce **soubor** .  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Po zavření okna vyvolá dvě události: <xref:System.Windows.Window.Closing> a <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> je aktivována před zavřením okna a poskytuje mechanismus, pomocí kterého lze zabránit zavření okna. Jedním z běžných důvodů, jak zabránit zavření okna, je, pokud obsah okna obsahuje upravená data. V této situaci je možné zpracovat událost <xref:System.Windows.Window.Closing>, aby se určilo, jestli jsou data nespravovaná, a pokud ano, požádejte uživatele, aby si mohli pokračovat v zavírání okna bez uložení dat nebo zrušení zavření okna. Následující příklad ukazuje klíčové aspekty zpracování <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 Obslužná rutina události <xref:System.Windows.Window.Closing> je předána <xref:System.ComponentModel.CancelEventArgs>, která implementuje vlastnost `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>, kterou jste nastavili na `true`, aby zabránila zavření okna.  
  
 Pokud se <xref:System.Windows.Window.Closing> nezpracovává nebo se zpracovává, ale neruší se, okno se zavře. Těsně před tím, než se okno skutečně zavře, <xref:System.Windows.Window.Closed> je vyvolána. V tuto chvíli není možné zabránit zavření okna.  
  
> [!NOTE]
> Aplikaci lze nakonfigurovat tak, aby se automaticky vypnula při zavření okna hlavní aplikace (viz <xref:System.Windows.Application.MainWindow%2A>) nebo po zavření posledního okna. Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 I když může být okno explicitně uzavřeno prostřednictvím mechanismů, které jsou k dispozici v klientských a klientských oblastech, může být okno také implicitně uzavřeno v důsledku chování v jiných částech aplikace nebo Windows, včetně následujících:  
  
- Uživatel se odhlásí nebo vypne v systému Windows.  
  
- Vlastník okna se zavře (viz <xref:System.Windows.Window.Owner%2A>).  
  
- Hlavní okno aplikace je zavřené a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
- je volána <xref:System.Windows.Application.Shutdown%2A>.  
  
> [!NOTE]
> Po zavření okna nelze znovu otevřít.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Události životního cyklu okna  
 Následující ilustrace znázorňuje sekvenci hlavních událostí v době života okna:  
  
 ![Diagram, který zobrazuje události v době života okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Následující ilustrace znázorňuje sekvenci hlavních událostí v době života okna, které se zobrazuje bez aktivace (<xref:System.Windows.Window.ShowActivated%2A> je nastavené na `false` před zobrazením okna):  
  
 ![Diagram, který zobrazuje události v době života okna bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Umístění okna  
 Když je okno otevřené, má umístění v rozměrech x a y relativně k ploše. Toto umístění lze určit kontrolou vlastností <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> v uvedeném pořadí. Nastavením těchto vlastností lze změnit umístění okna.  
  
 Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení nastavením vlastnosti <xref:System.Windows.Window.WindowStartupLocation%2A> jednu z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (výchozí)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Pokud je spouštěcí umístění zadáno jako <xref:System.Windows.WindowStartupLocation.Manual>a vlastnosti <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> nebyly nastaveny, <xref:System.Windows.Window> požádá Windows o umístění, ve kterém se nachází.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>V horních oknech a pořadí Z  
 Kromě umístění x a y má okno také místo v dimenzi z, které určuje jeho svislou polohu vzhledem k ostatním systémům Windows. Toto se říká pořadí vykreslování v okně a existují dva typy: normální pořadí vykreslování a nejvyšší pořadí vykreslování. Umístění okna v *normálním pořadí z* je určeno, zda je aktuálně aktivní nebo ne. Ve výchozím nastavení je okno umístěno v normálním pořadí z. Umístění okna v *horním pořadí z* je také určeno, zda je aktuálně aktivní nebo ne. Kromě toho Windows v horním pořadí z je vždycky umístěný nad Windows v normálním pořadí z. Okno je umístěno ve vrchní části pořadí z – nastavením jeho vlastnosti <xref:System.Windows.Window.Topmost%2A> na hodnotu `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 V rámci každého pořadí z je zobrazeno aktuálně aktivní okno nad všemi ostatními okny ve stejném pořadí z.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Velikost okna  
 Kromě umístění na ploše má okno velikost, která je určena několika vlastnostmi, včetně různých vlastností šířky a výšky a <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.MaxWidth%2A> se používají ke správě rozsahu šířek, které může okno mít během své životnosti, a jsou nakonfigurovány tak, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Výška okna se spravuje <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>a <xref:System.Windows.FrameworkElement.MaxHeight%2A>a jsou nakonfigurované tak, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Vzhledem k tomu, že různé hodnoty šířky a hodnoty výšky určují rozsah, je možné, že šířka a Výška okna s možností změny velikosti budou kdekoli v zadaném rozsahu pro příslušnou dimenzi. Chcete-li zjistit aktuální šířku a výšku, zkontrolujte <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A>v uvedeném pořadí.  
  
 Pokud chcete, aby Šířka a Výška okna měla velikost, která se vejde na velikost obsahu okna, můžete použít vlastnost <xref:System.Windows.Window.SizeToContent%2A>, která má následující hodnoty:  
  
- <xref:System.Windows.SizeToContent.Manual>. Žádný efekt (výchozí).  
  
- <xref:System.Windows.SizeToContent.Width>. Přizpůsobit šířce obsahu, která má stejný efekt jako nastavení <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.  
  
- <xref:System.Windows.SizeToContent.Height>. Přizpůsobit výšce obsahu, která má stejný efekt jako nastavení <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Přizpůsobit šířce a výšce obsahu, která má stejný efekt jako nastavení <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu a nastavení <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.  
  
 Následující příklad ukazuje okno, které automaticky přizpůsobí svůj obsah, jak je to možné, vertikálně i vodorovně, pokud je zobrazeno první.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Následující příklad ukazuje, jak nastavit vlastnost <xref:System.Windows.Window.SizeToContent%2A> v kódu pro určení, jak se změní velikost okna tak, aby odpovídala jeho obsahu.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Pořadí priorit pro vlastnosti velikosti  
 V podstatě jsou různé vlastnosti velikosti okna kombinovány, aby bylo možné definovat rozsah šířky a výšky okna s možností změny velikosti. Aby bylo zajištěno zachování platného rozsahu, <xref:System.Windows.Window> vyhodnotí hodnoty vlastností velikosti pomocí následujících pořadí priorit.  
  
 **Pro vlastnosti výšky:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Pro vlastnosti šířky:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Pořadí priorit může také určit velikost okna v případě maximalizace, které je spravováno pomocí vlastnosti <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Stav okna  
 Během životnosti okna s možností změny velikosti může mít tři stavy: normální, minimalizované a maximalizované. Okno s *normálním* stavem je výchozí stav okna. Okno s tímto stavem umožňuje uživateli, aby ho přesunul a změnil jeho velikost pomocí úchytu změny velikosti nebo ohraničení, pokud jde o změnu velikosti.  
  
 Okno s *minimalizovaným* stavem se sbalí na jeho tlačítko na panelu úkolů, pokud je <xref:System.Windows.Window.ShowInTaskbar%2A> nastaveno na `true`; v opačném případě se sbalí na nejmenší možnou velikost, kterou může být, a přemístit je do levého dolního rohu plochy. Velikost minimalizovaného okna nelze měnit pomocí ohraničení nebo změny velikosti, i když minimalizované okno, které není zobrazeno na panelu úloh, lze přetáhnout na plochu.  
  
 Okno s *maximalizovaném* stavem se rozšíří na maximální velikost, která může být, což bude mít jako <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>a <xref:System.Windows.Window.SizeToContent%2A> vlastnosti diktování jenom tak velké. Podobně jako minimalizované okno nelze upravit velikost maximalizovaného okna pomocí úchytu pro změnu velikosti nebo přetažením ohraničení.  
  
> [!NOTE]
> Hodnoty <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.Height%2A>ch vlastností okna vždy reprezentují hodnoty pro normální stav, a to i v případě, že je okno momentálně maximalizováno nebo minimalizováno.  
  
 Stav okna lze nakonfigurovat nastavením jeho vlastnosti <xref:System.Windows.Window.WindowState%2A>, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:  
  
- <xref:System.Windows.WindowState.Normal> (výchozí)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 Následující příklad ukazuje, jak vytvořit okno, které se zobrazí při otevření v maximalizovaném okně.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Obecně byste měli nastavit <xref:System.Windows.Window.WindowState%2A> pro konfiguraci počátečního stavu okna. Jakmile se zobrazí okno pro změnu velikosti, uživatelé mohou změnit stav okna stisknutím tlačítek minimalizovat, maximalizovat a obnovit v záhlaví okna.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Vzhled okna  
 Můžete změnit vzhled oblasti klienta okna přidáním obsahu pro jednotlivé okno, jako jsou tlačítka, popisky a textová pole. Chcete-li nakonfigurovat neklientskou oblast, <xref:System.Windows.Window> poskytuje několik vlastností, které zahrnují <xref:System.Windows.Window.Icon%2A> k nastavení ikony okna a <xref:System.Windows.Window.Title%2A> k nastavení jeho nadpisu.  
  
 Můžete také změnit vzhled a chování ohraničení neklientské oblasti tím, že nakonfigurujete režim změny velikosti okna, styl okna a zda se zobrazí jako tlačítko na panelu úloh plochy.  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Změnit velikost režimu  
 V závislosti na vlastnosti <xref:System.Windows.Window.WindowStyle%2A> můžete určit, jak (a kdy) uživatelé mohou měnit velikost okna. Volba stylu okna ovlivňuje, zda může uživatel změnit velikost okna přetažením jeho ohraničení myší, zda se tlačítka **minimalizovat**, **maximalizovat**a **změnit velikost** zobrazují v neklientské oblasti a v případě, že se zobrazí. umožněn.  
  
 Můžete nakonfigurovat, jak se změní velikost okna nastavením jeho vlastnosti <xref:System.Windows.Window.ResizeMode%2A>, což může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (výchozí)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Stejně jako u <xref:System.Windows.Window.WindowStyle%2A>se v průběhu své životnosti režim změny velikosti okna pravděpodobně nemění. to znamená, že ho pravděpodobně nastavíte z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Všimněte si, že můžete zjistit, zda je okno maximalizováno, minimalizováno nebo obnoveno kontrolou vlastnosti <xref:System.Windows.Window.WindowState%2A>.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Styl okna  
 Ohraničení, které je vystaveno mimo klientskou oblast okna, je vhodné pro většinu aplikací. Existují však situace, kdy je třeba zadat různé typy ohraničení, nebo není nutné žádné ohraničení v závislosti na typu okna.  
  
 Chcete-li určit, jaký typ ohraničení okno získá, nastavte jeho vlastnost <xref:System.Windows.Window.WindowStyle%2A> jednu z následujících hodnot výčtu <xref:System.Windows.WindowStyle>:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (výchozí)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt těchto stylů oken je znázorněn na následujícím obrázku:  
  
 ![Ilustrace stylů ohraničení okna](./media/wpf-windows-overview/window-border-styles.png)  
  
 Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> pomocí značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo kódu; vzhledem k tomu, že se během doby platnosti okna pravděpodobně nemění, pravděpodobně ji nakonfigurujete pomocí kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl neobdélníkového okna  
 Existují také situace, kdy styly ohraničení, které <xref:System.Windows.Window.WindowStyle%2A> umožňují, nejsou dostačující. Například můžete chtít vytvořit aplikaci s neobdélníkovým ohraničením, například Microsoft Windows Media Player používá.  
  
 Představte si například okno bublinového slova, které vidíte na následujícím obrázku:  
  
 ![Okno bublinového slova, které říká, že se má přetáhnout](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Tento typ okna lze vytvořit nastavením vlastnosti <xref:System.Windows.Window.WindowStyle%2A> na <xref:System.Windows.WindowStyle.None>a pomocí speciální podpory, kterou <xref:System.Windows.Window> pro transparentnost.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Tato kombinace hodnot instruuje okno tak, aby bylo zcela transparentní. V tomto stavu nelze použít doplňky neklientských oblastí okna (tlačítka Zavřít nabídky, minimalizovat, maximalizovat a obnovit atd.). V důsledku toho je třeba zadat vlastní.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Přítomnost panelu úloh  

Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, podobně jako na následujícím obrázku:

 ![Snímek obrazovky, který zobrazuje okno s tlačítkem hlavního panelu.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Některé typy oken nemají tlačítko na hlavním panelu, například pole se zprávami a dialogová okna (viz dialogová [okna Přehled](dialog-boxes-overview.md)). Nastavením vlastnosti <xref:System.Windows.Window.ShowInTaskbar%2A> (`true` ve výchozím nastavení) můžete řídit, zda je zobrazeno tlačítko na panelu úloh okna.  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 <xref:System.Windows.Window> vyžaduje vytvoření instance `UnmanagedCode` oprávnění zabezpečení. Pro aplikace nainstalované a spouštěné z místního počítače spadá do sady oprávnění udělených aplikaci.  
  
 To však spadá mimo sadu oprávnění udělených aplikacím, které jsou spouštěny z Internetu nebo místního intranetu pomocí technologie ClickOnce. V důsledku toho se uživatelům zobrazí upozornění zabezpečení ClickOnce a bude muset zvýšit úroveň oprávnění pro aplikaci na úplný vztah důvěryhodnosti.  
  
 Aplikace XBAP navíc nemůžou ve výchozím nastavení zobrazovat okna nebo dialogová okna. Diskuzi o zabezpečení samostatných aplikací najdete v tématu [strategie zabezpečení WPF – zabezpečení platformy](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Jiné typy Windows  
 <xref:System.Windows.Navigation.NavigationWindow> je okno, které je určené k hostování obsahu naviguje. Další informace najdete v tématu [Přehled navigace](navigation-overview.md).  
  
 Dialogová okna jsou okna, která se často používají k získání informací z uživatele k dokončení funkce. Například když chce uživatel otevřít soubor, dialogové okno **otevřít soubor** se obvykle zobrazí v aplikaci k získání názvu souboru od uživatele. Další informace najdete v tématu [Přehled dialogových oken](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Přehled dialogových oken](dialog-boxes-overview.md)
- [Sestavení aplikace WPF](building-a-wpf-application-wpf.md)
