---
title: Přehled systému Windows
description: Seznamte se se základy vytváření a správy Windows pro samostatné aplikace v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: e1ad3c118fbaea8f1e23d012721f0cf3c2c50015
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622884"
---
# <a name="wpf-windows-overview"></a>Přehled WPF Windows
Uživatelé pracují se samostatnými aplikacemi Windows Presentation Foundation (WPF) prostřednictvím systému Windows. Hlavním účelem okna je hostování obsahu, který vizualizuje data a umožňuje uživatelům pracovat s daty. Samostatné aplikace WPF poskytují vlastní okna pomocí <xref:System.Windows.Window> třídy. V tomto tématu <xref:System.Windows.Window> se seznámíte se základy vytváření a správy oken v samostatných aplikacích.  
  
> [!NOTE]
> Aplikace WPF hostované v prohlížeči, včetně aplikací prohlížeče XAML (XBAP) a volných [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránek, neposkytují vlastní okna. Místo toho jsou hostovány ve Windows, poskytovaném aplikací Windows Internet Explorer. Viz téma [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Třída okna  
 Následující obrázek znázorňuje prvky části okna:  
  
 ![Snímek obrazovky zobrazující prvky okna](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno je rozděleno do dvou oblastí: mimo klientské a klientské oblasti.  
  
 *Neklientská oblast* okna je implementována pomocí WPF a zahrnuje části okna, která jsou společná pro většinu oken, včetně následujících:  
  
- Ohraničení.  
  
- Záhlaví.  
  
- Ikona.  
  
- Tlačítka minimalizovat, maximalizovat a obnovit.  
  
- Tlačítko Zavřít  
  
- Systémová nabídka s položkami nabídky, které uživatelům umožňují minimalizovat, maximalizovat, obnovit, přesunout, změnit velikost a zavřít okno.  
  
 *Klientská oblast* okna je oblast v neklientské oblasti okna, kterou vývojáři používají k přidání obsahu specifického pro aplikaci, jako jsou například panely nabídek, panely nástrojů a ovládací prvky.  
  
 V WPF je okno zapouzdřené <xref:System.Windows.Window> třídou, kterou použijete k provedení následujících akcí:  
  
- Zobrazí okno.  
  
- Nakonfigurujte velikost, umístění a vzhled okna.  
  
- Hostování obsahu specifického pro aplikaci.  
  
- Umožňuje spravovat dobu života okna.  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Implementace okna  
 Implementace typického okna zahrnuje vzhled i chování, kde *vzhled* definuje, jak okno vypadá uživatelům a *chování* definuje způsob, jakým okno funguje, jak se s ním uživatelé budou pracovat. V jazyce WPF můžete implementovat vzhled a chování okna pomocí kódu nebo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky.  
  
 Obecně se však vzhled okna implementuje pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a jeho chování je implementováno pomocí kódu na pozadí, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Chcete-li povolit spolupráci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru značek a souboru s kódem na pozadí, jsou vyžadovány následující:  
  
- V kódu `Window` musí element obsahovat `x:Class` atribut. Když je aplikace sestavena, existence `x:Class` v souboru označení způsobí, že nástroj Microsoft Build Engine (MSBuild) vytvoří `partial` třídu, která je odvozena z <xref:System.Windows.Window> a má název, který je určen `x:Class` atributem. To vyžaduje přidání deklarace oboru názvů XML pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Vygenerovaná `partial` Třída implementuje `InitializeComponent` metodu, která je volána k registraci událostí a nastavení vlastností, které jsou implementovány v označení.  
  
- V kódu na pozadí třída musí být `partial` Třída se stejným názvem, který je určen `x:Class` atributem v označení a musí odvozovat z <xref:System.Windows.Window> . To umožňuje, aby soubor s kódem na pozadí byl přidružen ke `partial` třídě, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).  
  
- V kódu na pozadí <xref:System.Windows.Window> Třída musí implementovat konstruktor, který volá `InitializeComponent` metodu. `InitializeComponent`je implementována třídou vygenerovanou souborem označení `partial` pro registraci událostí a nastavení vlastností, které jsou definovány v označení.  
  
> [!NOTE]
> Přidáte-li <xref:System.Windows.Window> do projektu nový pomocí sady Visual Studio, <xref:System.Windows.Window> je implementováno pomocí kódu a kódu na pozadí a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značkami a soubory kódu na pozadí, jak je popsáno zde.  
  
 S touto konfigurací se můžete soustředit na definování vzhledu okna v kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a implementaci jeho chování v kódu na pozadí. Následující příklad ukazuje okno s tlačítkem, implementované v kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a obslužná rutina události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Událost tlačítka, implementovaná v kódu na pozadí.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurace definice okna pro MSBuild  
 Způsob implementace vašeho okna určuje, jak je nakonfigurován pro nástroj MSBuild. Pro okno, které je definováno pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu na pozadí:  
  
- Soubory značek XAML jsou konfigurovány jako `Page` položky MSBuild.  
  
- Soubory kódu na pozadí jsou konfigurovány jako `Compile` položky nástroje MSBuild.  
  
 Tento soubor je zobrazen v následujícím souboru projektu MSBuild.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Informace o vytváření aplikací WPF naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Doba života okna  
 Stejně jako u libovolné třídy má okno životnost, která začíná při prvním vytvoření instance, po jejím otevření, aktivaci a deaktivaci a nakonec uzavření.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Otevření okna  
 Chcete-li otevřít okno, nejprve vytvořte jeho instanci, která je znázorněna v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, což nastane při <xref:System.Windows.Application.Startup> vyvolání události.  
  
 Při vytvoření instance okna je odkaz na něj automaticky přidán do seznamu oken, který je spravován <xref:System.Windows.Application> objektem (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType> ). Kromě toho první okno, které má být vytvořena instance, je ve výchozím nastavení nastaveno <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> ).  
  
 Okno je nakonec otevřeno voláním metody. <xref:System.Windows.Window.Show%2A> výsledek je znázorněn na následujícím obrázku.  
  
 ![Okno otevřené voláním okna. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno otevřené voláním <xref:System.Windows.Window.Show%2A> je nemodální okno, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat další okna ve stejné aplikaci.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>je volána pro otevření oken, například dialogová okna v modálním formátu. Další informace najdete v tématu Přehled dialogových [oken](dialog-boxes-overview.md) .  
  
 Když <xref:System.Windows.Window.Show%2A> je volána, okno provede inicializační práci předtím, než se zobrazí, aby se navázala infrastruktura, která umožňuje přijímat uživatelský vstup. Po inicializaci okna se <xref:System.Windows.Window.SourceInitialized> událost vyvolá a zobrazí se okno.  
  
 Jako zástupce <xref:System.Windows.Application.StartupUri%2A> lze nastavit, aby určovalo první okno, které se automaticky otevře při spuštění aplikace.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Po spuštění aplikace je okno určené hodnotou <xref:System.Windows.Application.StartupUri%2A> otevřeno nemodální. interně je okno otevřeno voláním jeho <xref:System.Windows.Window.Show%2A> metody.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Vlastnictví okna  
 Okno, které je otevřeno pomocí metody, nemá <xref:System.Windows.Window.Show%2A> implicitní relaci s oknem, který ho vytvořil. uživatelé mohou pracovat s některým z oken nezávisle na sobě, což znamená, že jedno okno může provést následující akce:  
  
- Zakrytí druhé (Pokud má jedna z oken <xref:System.Windows.Window.Topmost%2A> nastavenou vlastnost `true` ).  
  
- Minimalizujte, maximalizujete a obnovíte, aniž by to ovlivnilo druhý.  
  
 Některá okna vyžadují relaci s oknem, který je otevírá. Například aplikace integrovaného vývojového prostředí (IDE) může otevřít okna vlastností a nástrojů, jejichž typické chování je pokrýt okno, které je vytvoří. Kromě toho by tato okna měla vždycky zavřít, minimalizovat, maximalizovat a obnovit ve vzájemné součinnosti s oknem, který je vytvořil. Takový vztah může být vytvořen tak, že *jedno okno* naplňuje jako jiné a je dosaženo nastavením <xref:System.Windows.Window.Owner%2A> vlastnosti vlastnictví *okna* s odkazem na *okno vlastníka*. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po navázání vlastnictví:  
  
- Vlastněné okno může odkazovat na své nadřazené okno kontrolou hodnoty jeho <xref:System.Windows.Window.Owner%2A> Vlastnosti.  
  
- Okno vlastník může zjistit, že je v něm vlastní systém Windows, a to tak, že zkontroluje hodnotu jeho <xref:System.Windows.Window.OwnedWindows%2A> Vlastnosti.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Prevence aktivace okna  
 Existují situace, kdy by systém Windows neměl být aktivovaný, pokud je zobrazený, například okna konverzace aplikace ve stylu kurýrní služby nebo okna oznámení e-mailové aplikace.  
  
 Pokud má aplikace okno, které by se nemělo aktivovat, pokud je zobrazeno, můžete nastavit jeho <xref:System.Windows.Window.ShowActivated%2A> vlastnost na hodnotu `false` před <xref:System.Windows.Window.Show%2A> prvním voláním metody. Jako důsledek:  
  
- Okno není aktivováno.  
  
- Událost okna není <xref:System.Windows.Window.Activated> vyvolána.  
  
- Aktuálně aktivované okno zůstane aktivované.  
  
 Okno se aktivuje, ale jakmile ho uživatel aktivuje, klikněte buď na klienta, nebo na oblast mimo klienta. V tomto případě:  
  
- Okno je aktivováno.  
  
- <xref:System.Windows.Window.Activated>Vyvolá se událost okna.  
  
- Dříve aktivované okno je deaktivováno.  
  
- <xref:System.Windows.Window.Deactivated> <xref:System.Windows.Window.Activated> V reakci na akce uživatele jsou následně vyvolány okno a události.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Aktivace okna  
 Při prvním otevření okna se zobrazí okno aktivní (Pokud se nezobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavením na `false` ). *Aktivní okno* je okno, které aktuálně zachytí vstup uživatele, například tahy kláves a kliknutí myší. Když dojde k aktivaci okna, vyvolá <xref:System.Windows.Window.Activated> událost.  
  
> [!NOTE]
> Při prvním otevření okna se <xref:System.Windows.FrameworkElement.Loaded> události a vyvolá až <xref:System.Windows.Window.ContentRendered> po <xref:System.Windows.Window.Activated> vyvolání události. V takovém případě může být okno efektivně považováno za otevřené při <xref:System.Windows.Window.ContentRendered> vyvolání.  
  
 Po aktivaci okna může uživatel aktivovat jiné okno ve stejné aplikaci nebo aktivovat jinou aplikaci. Pokud k tomu dojde, stane se aktuálně aktivní okno deaktivováno a vyvolá <xref:System.Windows.Window.Deactivated> událost. Podobně když uživatel vybere aktuálně deaktivované okno, okno se znovu aktivuje a <xref:System.Windows.Window.Activated> vyvolá se.  
  
 Jedním z běžných důvodů, jak zpracovat a <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> Zakázat funkce, které lze spustit pouze v případě, že je okno aktivní. Například některá okna zobrazují interaktivní obsah, který vyžaduje stálý vstup uživatele nebo pozornost, včetně her a přehrávačů videí. Následující příklad je zjednodušený přehrávač videa, který ukazuje, jak zpracovat <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> implementovat toto chování.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Jiné typy aplikací mohou stále spouštět kód na pozadí, když dojde k deaktivaci okna. Například poštovní klient může pokračovat v dotazování poštovního serveru, zatímco uživatel používá jiné aplikace. Tyto aplikace často poskytují jiné nebo dodatečné chování při deaktivaci hlavního okna. V souvislosti s e-mailovým programem může to znamenat, že by se nová položka pošty přidala do doručené pošty a přidala se ikona oznámení do systémového zásobníku. Ikona oznámení musí být zobrazena pouze v případě, že okno pošty není aktivní, což lze určit kontrolou <xref:System.Windows.Window.IsActive%2A> Vlastnosti.  
  
 Pokud je úloha na pozadí dokončena, okno může chtít uživateli upozorňovat na naléhavější voláním <xref:System.Windows.Window.Activate%2A> metody. Pokud uživatel pracuje s jinou aplikací aktivovanou <xref:System.Windows.Window.Activate%2A> , když je volána, tlačítko na hlavním panelu bude blikat. Pokud uživatel spolupracuje s aktuální aplikací, volání přepne <xref:System.Windows.Window.Activate%2A> okno do popředí.  
  
> [!NOTE]
> Můžete zpracovávat aktivaci rozsahu aplikace pomocí <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> událostí a.  
  
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
  
 Chcete-li zavřít okno v reakci na některý z těchto vlastních mechanismů, je třeba zavolat <xref:System.Windows.Window.Close%2A> metodu. Následující příklad implementuje možnost Zavřít okno výběrem možnosti **konec** v nabídce **soubor** .  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Po zavření okna vyvolá dvě události: <xref:System.Windows.Window.Closing> a <xref:System.Windows.Window.Closed> .  
  
 <xref:System.Windows.Window.Closing>je aktivována před zavřením okna a poskytuje mechanismus, pomocí kterého lze zabránit zavření okna. Jedním z běžných důvodů, jak zabránit zavření okna, je, pokud obsah okna obsahuje upravená data. V takovém <xref:System.Windows.Window.Closing> případě může být událost zpracována za účelem zjištění, zda jsou data nečistá, a pokud ano, požádejte uživatele, aby buď pokračoval v zavírání okna bez uložení dat, nebo zrušení zavření okna. Následující příklad ukazuje klíčové aspekty manipulace <xref:System.Windows.Window.Closing> .  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing>Obslužná rutina události je předána a <xref:System.ComponentModel.CancelEventArgs> , která implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost, která je nastavena na, `true` aby zabránila zavření okna.  
  
 Pokud není <xref:System.Windows.Window.Closing> zpracována nebo je zpracována, ale není zrušeno, okno se zavře. Těsně před tím, než se okno skutečně zavře, <xref:System.Windows.Window.Closed> se vyvolá. V tuto chvíli není možné zabránit zavření okna.  
  
> [!NOTE]
> Aplikaci lze nakonfigurovat tak, aby se automaticky vypnula při zavření okna hlavní aplikace (viz <xref:System.Windows.Application.MainWindow%2A> ) nebo po zavření posledního okna. Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 I když může být okno explicitně uzavřeno prostřednictvím mechanismů, které jsou k dispozici v klientských a klientských oblastech, může být okno také implicitně uzavřeno v důsledku chování v jiných částech aplikace nebo Windows, včetně následujících:  
  
- Uživatel se odhlásí nebo vypne v systému Windows.  
  
- Vlastník okna se zavře (viz <xref:System.Windows.Window.Owner%2A> ).  
  
- Hlavní okno aplikace je zavřené a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose> .  
  
- <xref:System.Windows.Application.Shutdown%2A>je volána.  
  
> [!NOTE]
> Po zavření okna nelze znovu otevřít.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Události životního cyklu okna  
 Následující ilustrace znázorňuje sekvenci hlavních událostí v době života okna:  
  
 ![Diagram, který zobrazuje události v době života okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Následující ilustrace znázorňuje sekvenci hlavních událostí v době životnosti okna, které je zobrazeno bez aktivace ( <xref:System.Windows.Window.ShowActivated%2A> je nastaveno na hodnotu `false` před zobrazením okna):  
  
 ![Diagram, který zobrazuje události v době života okna bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Umístění okna  
 Když je okno otevřené, má umístění v rozměrech x a y relativně k ploše. Toto umístění lze určit kontrolou <xref:System.Windows.Window.Left%2A> vlastností a v <xref:System.Windows.Window.Top%2A> uvedeném pořadí. Nastavením těchto vlastností lze změnit umístění okna.  
  
 Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení nastavením <xref:System.Windows.Window.WindowStartupLocation%2A> vlastnosti pomocí jedné z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner>výchozí  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Pokud je počáteční umístění zadané jako <xref:System.Windows.WindowStartupLocation.Manual> a <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> vlastnosti a nejsou nastavené, <xref:System.Windows.Window> požádá Windows o umístění, ve kterém se bude zobrazovat.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>V horních oknech a pořadí Z  
 Kromě umístění x a y má okno také místo v dimenzi z, které určuje jeho svislou polohu vzhledem k ostatním systémům Windows. Toto se říká pořadí vykreslování v okně a existují dva typy: normální pořadí vykreslování a nejvyšší pořadí vykreslování. Umístění okna v *normálním pořadí z* je určeno, zda je aktuálně aktivní nebo ne. Ve výchozím nastavení je okno umístěno v normálním pořadí z. Umístění okna v *horním pořadí z* je také určeno, zda je aktuálně aktivní nebo ne. Kromě toho Windows v horním pořadí z je vždycky umístěný nad Windows v normálním pořadí z. Okno je umístěno v horní části pořadí z – nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnosti na `true` .  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 V rámci každého pořadí z je zobrazeno aktuálně aktivní okno nad všemi ostatními okny ve stejném pořadí z.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Velikost okna  
 Kromě umístění na ploše má okno velikost, která je určena několika vlastnostmi, včetně různých vlastností šířky a výšky a <xref:System.Windows.Window.SizeToContent%2A> .  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A> , a <xref:System.Windows.FrameworkElement.MaxWidth%2A> slouží ke správě rozsahu šířek, které může okno mít během své životnosti a jsou konfigurovány tak, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Výška okna je spravována pomocí <xref:System.Windows.FrameworkElement.MinHeight%2A> , <xref:System.Windows.FrameworkElement.Height%2A> , a <xref:System.Windows.FrameworkElement.MaxHeight%2A> , a je konfigurována tak, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Vzhledem k tomu, že různé hodnoty šířky a hodnoty výšky určují rozsah, je možné, že šířka a Výška okna s možností změny velikosti budou kdekoli v zadaném rozsahu pro příslušnou dimenzi. Chcete-li zjistit aktuální šířku a výšku, zkontrolujte <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> v uvedeném pořadí.  
  
 Pokud chcete, aby Šířka a Výška okna měla velikost, která se vejde na velikost obsahu okna, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnost, která má následující hodnoty:  
  
- <xref:System.Windows.SizeToContent.Manual>. Žádný efekt (výchozí).  
  
- <xref:System.Windows.SizeToContent.Width>. Přizpůsobit šířce obsahu, která má stejný efekt jako nastavení <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.  
  
- <xref:System.Windows.SizeToContent.Height>. Přizpůsobit výšce obsahu, která má stejný efekt jako nastavení obou <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. Přizpůsobit šířce a výšce obsahu, která má stejný efekt jako nastavení obou i <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu a nastavení i <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.  
  
 Následující příklad ukazuje okno, které automaticky přizpůsobí svůj obsah, jak je to možné, vertikálně i vodorovně, pokud je zobrazeno první.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Window.SizeToContent%2A> vlastnost v kódu pro určení, jak se změní velikost okna tak, aby odpovídala jeho obsahu.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Pořadí priorit pro vlastnosti velikosti  
 V podstatě jsou různé vlastnosti velikosti okna kombinovány, aby bylo možné definovat rozsah šířky a výšky okna s možností změny velikosti. Chcete-li zajistit zachování platného rozsahu, <xref:System.Windows.Window> vyhodnotí hodnoty vlastností velikosti pomocí následujících pořadí priorit.  
  
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
  
 Pořadí priorit může také určit velikost okna v případě maximalizace, které je spravováno pomocí <xref:System.Windows.Window.WindowState%2A> Vlastnosti.  
  
<a name="WindowState"></a>
## <a name="window-state"></a>Stav okna  
 Během životnosti okna s možností změny velikosti může mít tři stavy: normální, minimalizované a maximalizované. Okno s *normálním* stavem je výchozí stav okna. Okno s tímto stavem umožňuje uživateli, aby ho přesunul a změnil jeho velikost pomocí úchytu změny velikosti nebo ohraničení, pokud jde o změnu velikosti.  
  
 Okno s *minimalizovaným* stavem se sbalí na jeho tlačítko na panelu úkolů <xref:System.Windows.Window.ShowInTaskbar%2A> , pokud je nastaveno na hodnotu `true` ; v opačném případě se sbalí na nejmenší možnou velikost, která může být a přemístění do levého dolního rohu plochy. Velikost minimalizovaného okna nelze měnit pomocí ohraničení nebo změny velikosti, i když minimalizované okno, které není zobrazeno na panelu úloh, lze přetáhnout na plochu.  
  
 Okno s *maximalizovaném* stavem se zvětšuje na maximální velikost, která může být, což bude mít až velkou hodnotu, <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> a <xref:System.Windows.Window.SizeToContent%2A> vlastnosti se určí. Podobně jako minimalizované okno nelze upravit velikost maximalizovaného okna pomocí úchytu pro změnu velikosti nebo přetažením ohraničení.  
  
> [!NOTE]
> Hodnoty <xref:System.Windows.Window.Top%2A> vlastností,, a <xref:System.Windows.Window.Left%2A> v <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> okně vždy reprezentují hodnoty pro normální stav, a to i v případě, že je okno momentálně maximalizováno nebo minimalizováno.  
  
 Stav okna lze nakonfigurovat nastavením jeho <xref:System.Windows.Window.WindowState%2A> vlastnosti, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:  
  
- <xref:System.Windows.WindowState.Normal>výchozí  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 Následující příklad ukazuje, jak vytvořit okno, které se zobrazí při otevření v maximalizovaném okně.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Obecně byste měli nastavit, <xref:System.Windows.Window.WindowState%2A> aby se nakonfiguroval počáteční stav okna. Jakmile se zobrazí okno pro změnu velikosti, uživatelé mohou změnit stav okna stisknutím tlačítek minimalizovat, maximalizovat a obnovit v záhlaví okna.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Vzhled okna  
 Můžete změnit vzhled oblasti klienta okna přidáním obsahu pro jednotlivé okno, jako jsou tlačítka, popisky a textová pole. Chcete-li nakonfigurovat neklientskou oblast, <xref:System.Windows.Window> poskytuje několik vlastností, které zahrnují <xref:System.Windows.Window.Icon%2A> Nastavení ikony okna a <xref:System.Windows.Window.Title%2A> nastavení jeho názvu.  
  
 Můžete také změnit vzhled a chování ohraničení neklientské oblasti tím, že nakonfigurujete režim změny velikosti okna, styl okna a zda se zobrazí jako tlačítko na panelu úloh plochy.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Změnit velikost režimu  
 V závislosti na <xref:System.Windows.Window.WindowStyle%2A> vlastnosti můžete určit, jak (a kdy) uživatelé mohou měnit velikost okna. Volba stylu okna ovlivňuje, zda může uživatel změnit velikost okna přetažením jeho ohraničení pomocí myši, zda jsou tlačítka **minimalizovat**, **maximalizovat**a **změnit velikost** zobrazena v neklientské oblasti a v případě, že se zobrazí, zda jsou povoleny.  
  
 Můžete nakonfigurovat, jak se změní velikost okna nastavením jeho <xref:System.Windows.Window.ResizeMode%2A> vlastnosti, což může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize>výchozí  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Stejně jako v se <xref:System.Windows.Window.WindowStyle%2A> režim změny velikosti okna pravděpodobně během své životnosti nezmění, což znamená, že je pravděpodobně možné ho nastavit ze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Všimněte si, že kontrolu vlastností můžete zjistit, zda je okno maximalizováno, minimalizováno nebo obnoveno <xref:System.Windows.Window.WindowState%2A> .  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Styl okna  
 Ohraničení, které je vystaveno mimo klientskou oblast okna, je vhodné pro většinu aplikací. Existují však situace, kdy je třeba zadat různé typy ohraničení, nebo není nutné žádné ohraničení v závislosti na typu okna.  
  
 Chcete-li určit, jaký typ ohraničení okno získá, nastavte jeho <xref:System.Windows.Window.WindowStyle%2A> vlastnost pomocí jedné z následujících hodnot <xref:System.Windows.WindowStyle> výčtu:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow>výchozí  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Efekt těchto stylů oken je znázorněn na následujícím obrázku:  
  
 ![Ilustrace stylů ohraničení okna](./media/wpf-windows-overview/window-border-styles.png)  
  
 Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky nebo kódu; vzhledem k tomu, že se po celou dobu životnosti okna pravděpodobně nemění, je pravděpodobné, že ho budete konfigurovat pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl neobdélníkového okna  
 Existují také situace, kdy styly ohraničení, které umožňují, nejsou <xref:System.Windows.Window.WindowStyle%2A> dostačující. Například můžete chtít vytvořit aplikaci s neobdélníkovým ohraničením, například Microsoft Windows Media Player používá.  
  
 Představte si například okno bublinového slova, které vidíte na následujícím obrázku:  
  
 ![Okno bublinového slova, které říká, že se má přetáhnout](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Tento typ okna lze vytvořit nastavením <xref:System.Windows.Window.WindowStyle%2A> vlastnosti na <xref:System.Windows.WindowStyle.None> a pomocí speciální podpory, která <xref:System.Windows.Window> má transparentnost.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Tato kombinace hodnot instruuje okno tak, aby bylo zcela transparentní. V tomto stavu nelze použít doplňky neklientských oblastí okna (tlačítka Zavřít nabídky, minimalizovat, maximalizovat a obnovit atd.). V důsledku toho je třeba zadat vlastní.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Přítomnost panelu úloh  

Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, podobně jako na následujícím obrázku:

 ![Snímek obrazovky, který zobrazuje okno s tlačítkem hlavního panelu.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Některé typy oken nemají tlačítko na hlavním panelu, například pole se zprávami a dialogová okna (viz dialogová [okna Přehled](dialog-boxes-overview.md)). Nastavením <xref:System.Windows.Window.ShowInTaskbar%2A> vlastnosti ( `true` ve výchozím nastavení) můžete určit, zda je zobrazeno tlačítko na panelu úloh okna.  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Aspekty zabezpečení  
 <xref:System.Windows.Window>vyžaduje, `UnmanagedCode` aby se vytvořila instance oprávnění zabezpečení. Pro aplikace nainstalované a spouštěné z místního počítače spadá do sady oprávnění udělených aplikaci.  
  
 To však spadá mimo sadu oprávnění udělených aplikacím, které jsou spouštěny z Internetu nebo místního intranetu pomocí technologie ClickOnce. V důsledku toho se uživatelům zobrazí upozornění zabezpečení ClickOnce a bude muset zvýšit úroveň oprávnění pro aplikaci na úplný vztah důvěryhodnosti.  
  
 Aplikace XBAP navíc nemůžou ve výchozím nastavení zobrazovat okna nebo dialogová okna. Diskuzi o zabezpečení samostatných aplikací najdete v tématu [strategie zabezpečení WPF – zabezpečení platformy](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Jiné typy Windows  
 <xref:System.Windows.Navigation.NavigationWindow>je okno, které je navrženo pro hostování obsahu naviguje. Další informace najdete v tématu [Přehled navigace](navigation-overview.md).  
  
 Dialogová okna jsou okna, která se často používají k získání informací z uživatele k dokončení funkce. Například když chce uživatel otevřít soubor, dialogové okno **otevřít soubor** se obvykle zobrazí v aplikaci k získání názvu souboru od uživatele. Další informace najdete v tématu [Přehled dialogových oken](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Přehled dialogových oken](dialog-boxes-overview.md)
- [Sestavení aplikace WPF](building-a-wpf-application-wpf.md)
