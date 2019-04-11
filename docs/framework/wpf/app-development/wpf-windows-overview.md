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
ms.openlocfilehash: 5acebf0f88f3147bf274818f11697b480146701a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296118"
---
# <a name="wpf-windows-overview"></a>Přehled WPF Windows
Uživatelé komunikují s samostatné aplikace Windows Presentation Foundation (WPF) prostřednictvím systému windows. Primárním účelem okna je jako hostitele obsahu, která data vizualizuje a umožňuje uživatelům interakci s daty. Samostatné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace poskytují jejich vlastní okna s použitím <xref:System.Windows.Window> třídy. Toto téma představuje <xref:System.Windows.Window> před pokrývají základní informace o vytváření a správa systému windows v samostatné aplikace.  
  
> [!NOTE]
>  Hostované v prohlížeči [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a dojde ke ztrátě [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] neposkytují stránek, vlastní systému windows. Místo toho jsou hostované v systému windows poskytuje [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]. Zobrazit [přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Třídy oken  
 Následující obrázek znázorňuje základní části okna:  
  
 ![Snímek obrazovky zobrazující prvků okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Okno je rozdělen do dvou oblastí: neklientská oblast a klientské oblasti.  
  
 *Neklientská oblast* okna je implementováno [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a obsahuje části okna, které jsou společné pro většinu windows, včetně následujících:  
  
-   Ohraničení.  
  
-   Záhlaví okna.  
  
-   Ikona.  
  
-   Minimalizovat, maximalizovat a obnovit tlačítka.  
  
-   Tlačítko pro uzavření.  
  
-   Systémové nabídky pomocí položky nabídky, které umožňují uživatelům minimalizovat, maximalizovat, obnovení, přesunutí, změna velikosti a zavření okna.  
  
 *Klientské oblasti* okna je oblast v neklientské oblasti okna a vývojáři slouží k přidání obsahu specifické pro aplikace, jako je například panel nabídek, panelů nástrojů a ovládacích prvků.  
  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], okna jsou zapouzdřena objektem <xref:System.Windows.Window> třídu, která vám postupujte takto:  
  
-   Zobrazte okno.  
  
-   Nakonfigurujte velikost, umístění a vzhled okna.  
  
-   Hostování obsahu specifické pro aplikaci.  
  
-   Správa životního cyklu okna.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implementace okna  
 Vzhled a chování, se skládá z implementace typické okno kde *vzhled* definuje, jak vypadá okno pro uživatele a *chování* definuje způsob, jakým okno funguje, jak uživatelé pracují s ním. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete implementovat vzhled a chování oken pomocí buď kódu nebo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 Obecně platí, ale vzhled okna je implementováno pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a její chování je implementováno pomocí použití modelu code-behind, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Chcete-li povolit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru označení a použití modelu code-behind soubor spolupráce, vyžadují se následující věci:  
  
-   V kódu `Window` musí obsahovat element `x:Class` atribut. Když je aplikace sestavená, existenci `x:Class` ve značkách soubor způsobí, že [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Window> a má název, který je určen `x:Class` atribut. To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarace oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Vygenerovaný `partial` implementuje třída `InitializeComponent` metodu, která je volána k registraci události a nastavit vlastnosti, které jsou implementovány v kódu.  
  
-   V modelu code-behind, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` atribut v kódu který musí být odvozen od <xref:System.Windows.Window>. To umožňuje použití modelu code-behind souboru má být spojen s `partial` třídu, která se vygeneruje pro označovacího souboru, když je aplikace sestavená (viz [sestavení aplikace WPF](building-a-wpf-application-wpf.md)).  
  
-   V modelu code-behind <xref:System.Windows.Window> třída musí implementovat konstruktor, který volá `InitializeComponent` metody. `InitializeComponent` je implementován ve značce vygenerovaný soubor `partial` třídy k registraci události a nastavte vlastnosti, které jsou definovány v kódu.  
  
> [!NOTE]
>  Když přidáte nový <xref:System.Windows.Window> do svého projektu pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> je implementováno pomocí značek a kódu a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značky a modelu code-behind soubory jako najdete tady.  
  
 S touto konfigurací na místě, můžete se soustředit na definování vzhledu okna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a provádění své chování v kódu. Následující příklad ukazuje okno s tlačítkem, implementované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a obslužnou rutinu události pro tlačítka <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události, implementovat v kódu.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurace definice okna pro MSBuild  
 Jak implementovat okno určuje, jak je nakonfigurována pro [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Pro okno, které je definováno pomocí obou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu:  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory kódu nejsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` položky.  
  
-   Soubory kódu na pozadí jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile` položky.  
  
 To je ukázáno v následujícím [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] souboru projektu.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Informace o vytváření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] naleznete v tématu [sestavení aplikace WPF](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Doba života okna  
 S všechny třídy, má okno s dobou života, která začíná, když je vytvořena první instance, po jejímž uplynutí ho je otevřen, aktivovat a deaktivovat a nakonec zavřít.  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Otevřete okno  
 Otevřete okno, nejprve vytvořte její instanci, která je znázorněn v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, které dojde při <xref:System.Windows.Application.Startup> událost se vyvolá.  
  
 Při vytváření instance časového období se na ni odkaz automaticky přidá do seznamu systému windows, která jsou spravována <xref:System.Windows.Application> objektu (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Kromě toho první okno má být vytvořena se ve výchozím nastavení <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Otevření okna je nakonec voláním <xref:System.Windows.Window.Show%2A> metoda; výsledek je znázorněno na následujícím obrázku.  
  
 ![Otevření okna voláním Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Okno, které se otevře voláním <xref:System.Windows.Window.Show%2A> je nemodálním okně, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat ostatní okna ve stejné aplikaci.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> je volána k modálně otevřít windows, jako například dialogová okna. Zobrazit [přehled dialogových oken](dialog-boxes-overview.md) Další informace.  
  
 Když <xref:System.Windows.Window.Show%2A> je volána, okno provádí inicializace předtím, než se zobrazí k vytvoření infrastruktury, které umožňuje přijímat uživatelský vstup. Při inicializaci okna <xref:System.Windows.Window.SourceInitialized> událost se vyvolá, a zobrazí se okno.  
  
 Jako zástupce <xref:System.Windows.Application.StartupUri%2A> lze nastavit k určení první okno, které se automaticky otevře při spuštění aplikace.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Při spuštění aplikace, okna zadanou hodnotou <xref:System.Windows.Application.StartupUri%2A> otevření modelessly; interně, voláním otevření okna jeho <xref:System.Windows.Window.Show%2A> metoda.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Okno vlastnictví  
 Okno, které se otevře pomocí <xref:System.Windows.Window.Show%2A> metoda nemá implicitní vztah s oknem, který byl vytvořen, mohou uživatelé komunikovat s kterékoli z těchto oken nezávisle na druhé, což znamená, že některé okno můžete dělat tyto věci:  
  
-   Na druhou (Pokud některý ze systému windows má jeho <xref:System.Windows.Window.Topmost%2A> nastavenou na `true`).  
  
-   Minimalizovat, zachovat maximalizované a obnovit, aniž by to ovlivnilo druhé.  
  
 Některé windows vyžadují vztah s oknem je otevře. Například [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] aplikace může zobrazit vlastnosti windows a okna nástrojů, jehož chování typické je zahrnují okna, která je vytvořila. Kromě toho taková okna by měl vždy zavřít, minimalizovat, maximalizovat a obnovit společně s oknem, které byly vytvořeny. Takové vztah lze navázat tak, že jedno okno *vlastní* jiného a dosáhnout tak, že nastavíte <xref:System.Windows.Window.Owner%2A> vlastnost *vlastní okno* s odkazem na *vlastníka okno*. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po navázání vlastnictví:  
  
-   Vlastní okno může odkazovat jeho nadřazenému oknu zkontrolováním hodnota jeho <xref:System.Windows.Window.Owner%2A> vlastnost.  
  
-   Okno vlastníka může zjišťovat všechna okna vlastní hodnotu zkontrolováním jeho <xref:System.Windows.Window.OwnedWindows%2A> vlastnost.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Brání aktivaci okno  
 Existují scénáře, kde by neměl systém windows aktivovat, když je vidět, jako je například konverzace windows messenger – vizuální styl internetovou aplikaci nebo windows oznámení e-mailové aplikace.  
  
 Pokud vaše aplikace má okno, které by neměly aktivovat, když je znázorněno, můžete nastavit jeho <xref:System.Windows.Window.ShowActivated%2A> vlastnost `false` před voláním <xref:System.Windows.Window.Show%2A> metoda poprvé. V důsledku:  
  
-   V okně se neaktivuje.  
  
-   V okně <xref:System.Windows.Window.Activated> není vyvolána událost.  
  
-   Aktuálně aktivovaná okno zůstane aktivovaná.  
  
 V okně se aktivuje, ale ihned poté, co uživatel aktivuje klepnutím na klienta nebo neklientská oblast. V tomto případě:  
  
-   Okno se aktivuje.  
  
-   V okně <xref:System.Windows.Window.Activated> událost se vyvolá.  
  
-   Dříve aktivovaná je deaktivováno.  
  
-   V okně <xref:System.Windows.Window.Deactivated> a <xref:System.Windows.Window.Activated> následně vyvolány události podle očekávání v reakci na akce uživatele.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Okno Aktivace  
 Při prvním otevření okna stane aktivní okno (Pokud se zobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavena na `false`). *Aktivní okno* je okno, které je aktuálně zachytávání vstupu uživatele, jako je například klávesnicí a myší. Pokud se okno stane aktivní, vyvolá <xref:System.Windows.Window.Activated> událostí.  
  
> [!NOTE]
>  Při prvním otevření okna <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.Window.ContentRendered> až poté, co jsou vyvolány události <xref:System.Windows.Window.Activated> událost se vyvolá. S myslete na to, okno lze účinně považovat za při otevření <xref:System.Windows.Window.ContentRendered> je vyvolána.  
  
 Poté, co se okno stane aktivní, uživatel může aktivovat další okno ve stejné aplikaci, nebo jiná aplikace. Pokud k tomu dojde, aktuálně aktivní okno stane deaktivováno a vyvolá <xref:System.Windows.Window.Deactivated> událostí. Podobně, když uživatel vybere aktuálně deaktivované okno, v okně opět aktivní a <xref:System.Windows.Window.Activated> je vyvolána.  
  
 Jedním z běžných důvodů pro zpracování <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> je můžete povolit nebo zakázat funkce, které lze spustit pouze když je aktivní okno. Například některé windows zobrazit interaktivní obsah, který vyžaduje vstup uživatele konstantní nebo pozornost, včetně hry a přehrávačů videa. Následující příklad je zjednodušený video přehrávač, který ukazuje, jak zpracovat <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> k implementaci tohoto chování.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Další typy aplikací může stále spuštění kódu na pozadí při deaktivaci časového období. Například poštovní klient může pokračovat v dotazování poštovní server, když uživatel používá jiné aplikace. Aplikace, jako jsou tyto často poskytují odlišných nebo dodatečných chování, zatímco je deaktivováno hlavního okna. S ohledem na program e-mailu to může znamenat přidání nové položky pošty do schránky doručených zpráv i přidání oznámení ikony na hlavním panelu systému. Ikona oznámení potřebovat zobrazí jenom při e-mailu okno není aktivní, které se dají určit pomocí kontroly <xref:System.Windows.Window.IsActive%2A> vlastnost.  
  
 Pokud se dokončí úlohu na pozadí, okno chtít upozornit uživatele, více urgentně voláním <xref:System.Windows.Window.Activate%2A> metody. Pokud uživatel pracuje s jinou aplikací aktivuje se, když <xref:System.Windows.Window.Activate%2A> nazývá bliká tlačítko na hlavním panelu okna. Pokud uživatel pracuje s aktuální aplikace, volání <xref:System.Windows.Window.Activate%2A> přinese okno na popředí.  
  
> [!NOTE]
>  Můžete zpracovat pomocí aktivace oboru aplikace <xref:System.Windows.Application.Activated?displayProperty=nameWithType> a <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> události.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Zavřením okna  
 Životnost časového období začíná už skončí, když uživatel zavře. Zavřením okna za použití prvků v neklientské oblasti, včetně následujících:  
  
-   **Zavřít** položku **systému** nabídky.  
  
-   Stisknutím klávesy ALT + F4.  
  
-   Stisknutím klávesy **Zavřít** tlačítko.  
  
 Můžete zadat další mechanismy pro klientskou oblast okna, zavřete další běžné nástroje, které zahrnují následující:  
  
-   **Ukončovací** položky v **souboru** nabídky, obvykle hlavní aplikaci pro windows.  
  
-   A **Zavřít** položky v **souboru** nabídky, obvykle na sekundární oknu.  
  
-   A **zrušit** tlačítko, obvykle na modální dialogové okno.  
  
-   A **Zavřít** tlačítko, obvykle na nemodální dialogové okno.  
  
 Zavřete okno v reakci na jednu z těchto mechanismů vlastní, musíte zavolat <xref:System.Windows.Window.Close%2A> metody. Následující příklad implementuje možnost Zavřít okno výběrem **ukončovací** na **souboru** nabídky.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Po zavření okna vyvolává dvě události: <xref:System.Windows.Window.Closing> a <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing> je aktivována před okno se zavře a poskytuje mechanismus, podle které okno jde zakázat uzavření. Jedním z běžných důvodů zabránit zavření okna je, pokud obsahu okna obsahuje upravený data. V takovém případě <xref:System.Windows.Window.Closing> události může být zpracována pro určení, zda je nekonzistentní data a pokud ano, chcete-li požádat uživatele, zda chcete pokračovat bez uložení dat zavření okna nebo zrušení zavření okna. Následující příklad ukazuje klíčové aspekty zpracování <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing> Je předána obslužné rutiny události <xref:System.ComponentModel.CancelEventArgs>, která implementuje `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost, která nastavíte na `true` zabránit okno zavřít.  
  
 Pokud <xref:System.Windows.Window.Closing> není zpracována, nebo je zpracována, ale není zrušena, okno se zavře. Těsně před plánovaným začátkem skutečně okno zavře, <xref:System.Windows.Window.Closed> je vyvolána. V tuto chvíli nelze zabránit okno zabrání v uzavření.  
  
> [!NOTE]
>  Aplikace může být nakonfigurována pro vypnutí automaticky když buď hlavního okna aplikace se zavře (viz <xref:System.Windows.Application.MainWindow%2A>) nebo poslední okno se zavře. Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Během časového období můžete explicitně ukončeno prostřednictvím mechanismů poskytnutých v oblasti neklientských a klienta, okna můžete také být implicitně uzavřen, v důsledku chování v ostatních částech aplikace nebo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], včetně následujících:  
  
-   Uživatel odhlásí nebo ukončí Windows.  
  
-   Zavření okna vlastníka (viz <xref:System.Windows.Window.Owner%2A>).  
  
-   Zavření hlavního okna aplikace a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
-   <xref:System.Windows.Application.Shutdown%2A> je volána.  
  
> [!NOTE]
>  Nelze znovu otevřít časové období, po jeho zavření.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Události doby života okno  
 Následující obrázek znázorňuje posloupnost událostí instančního objektu v životnost časového období:  
  
 ![Diagram, který zobrazuje události do okna životnost.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Následující obrázek znázorňuje posloupnost událostí instančního objektu v době životnosti okno, které se zobrazí bez aktivace (<xref:System.Windows.Window.ShowActivated%2A> je nastavena na `false` předtím, než se zobrazí v okně):  
  
 ![Diagram, který zobrazuje události do okna životnost bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Umístění okna  
 Při otevření okna má umístění v x a y dimenze vzhledem k pracovní ploše. Toto umístění se dají určit pomocí kontroly <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> vlastnosti, v uvedeném pořadí. Můžete nastavit tyto vlastnosti chcete změnit umístění okna.  
  
 Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení tak, že nastavíte <xref:System.Windows.Window.WindowStartupLocation%2A> vlastnosti s jednou z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner> (výchozí)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Pokud umístění při spuštění je zadán jako <xref:System.Windows.WindowStartupLocation.Manual>a <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> nebyly nastaveny vlastnosti, <xref:System.Windows.Window> požádá Windows se zobrazí v pro umístění.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>Nejvyšší Windows a pořadí Z-Order  
 Kromě nutnosti x a y umístění, okno má také umístění z dimenze, která určuje svislé polohy s ohledem na ostatní okna. To se označuje jako pořadí vykreslování v okně a existují dva typy: Normální pořadí vykreslování a nejvyšší pořadí vykreslování. Umístění okna *normální pořadí vykreslování* je určeno bez ohledu na to, zda je aktuálně aktivní. Ve výchozím nastavení okno se nachází v normální pořadí vykreslování. Umístění okna *nejvyšší pořadí vykreslování* je také určeno bez ohledu na to, zda je aktuálně aktivní. Kromě toho windows v nejvyšší pořadí vykreslování jsou vždy umístěné nad windows v normálním pořadí vykreslování. Okno se nachází v nejvyšší pořadí vykreslování nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnost `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 V rámci každého pořadí vykreslování aktuálně aktivní okno zobrazuje nad všemi ostatními okny ve stejném pořadí vykreslování.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Velikost okna  
 Kromě nutnosti klasické pracovní plochy umístění, okno má velikost, která je určena podle několika vlastností, včetně různé vlastnosti šířku a výšku a <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.MaxWidth%2A> se používají ke správě škálu šířek, které může mít během celé jeho životnosti okna a konfiguraci, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Spravuje výšku okna <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.MaxHeight%2A>a konfiguraci, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Protože různé hodnoty šířku a výšku hodnoty určit rozsah, je možné pro šířku a výšku umožňující změnu velikosti okna musí být kdekoli v zadaném rozsahu pro odpovídající dimenzi. Ke zjištění svou aktuální šířku a výšku, zkontrolujte <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A>v uvedeném pořadí.  
  
 Pokud chcete šířku a výšku okna mít vhodnou velikost okna velikost obsahu, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnost, která má následující hodnoty:  
  
-   <xref:System.Windows.SizeToContent.Manual>. Žádný vliv (výchozí).  
  
-   <xref:System.Windows.SizeToContent.Width>. Přizpůsobit šířce obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> šířku obsahu.  
  
-   <xref:System.Windows.SizeToContent.Height>. Přizpůsobit na výšku obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> výškou obsahu.  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. Přizpůsobit obsahu šířku a výšku, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> výškou obsahu a nastavení obě <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> šířku obsahu.  
  
 Následující příklad ukazuje okno, která automaticky velikosti podle jeho obsah svisle nebo vodorovně, při prvním zobrazení.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Window.SizeToContent%2A> vlastností v kódu k určení, jak změní velikost okna podle jeho obsahu.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Pořadí priorit pro vlastností změny velikosti  
 V podstatě kombinovat různé vlastnosti velikosti okna pro účely definování rozsahu šířky a výšky umožňující změnu velikosti okna. Aby byla zachována platný rozsah <xref:System.Windows.Window> vyhodnotí jako hodnoty vlastností velikost pomocí následujících pořadí priorit.  
  
 **Pro vlastnosti Height:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Pro vlastnosti Šířka:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Pořadí priorit můžete také určit velikost okna, když se maximalizuje, který se spravuje pomocí <xref:System.Windows.Window.WindowState%2A> vlastnost.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Stav okna  
 Po celou dobu životnosti umožňující změnu velikosti okna, může mít tři stavy: normální minimalizovány a maximalizovat. Okno s *normální* stav je výchozí stav okna. Okno s tímto stavem umožňuje uživateli umístění a velikost úchyt pro změnu nebo ohraničení, pokud je umožňující změnu velikosti.  
  
 Okno s *minimalizovány* sbalí stavu na jeho tlačítko na hlavním panelu, pokud <xref:System.Windows.Window.ShowInTaskbar%2A> je nastavena na `true`; v opačném případě Hroutí k nejmenší velikost je to možné, může být a samotné přemístí do levého dolního rohu plochy. Ani typu minimalizované okno velikost lze změnit pomocí ohraničení nebo úchyt, i když můžete kolem ploše přetáhnout minimalizované okno, které se nezobrazuje na hlavním panelu.  
  
 Okno s *maximalizované* stavu rozšíří na maximální velikost může být, který může mít pouze stejně velké jako jeho <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.Window.SizeToContent%2A> vlastnosti diktování. Například minimalizované okno maximalizované okno nelze změnit velikost úchyt pro změnu nebo přetažením ohraničení.  
  
> [!NOTE]
>  Hodnoty <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.Height%2A> i v případě, že momentálně maximalizované nebo minimalizovat okno Vlastnosti okna vždy představují hodnoty pro normální stav.  
  
 Stav okna se dá nakonfigurovat pomocí nastavení jeho <xref:System.Windows.Window.WindowState%2A> vlastnost, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:  
  
-   <xref:System.Windows.WindowState.Normal> (výchozí)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 Následující příklad ukazuje, jak vytvořit okno, které se zobrazí jako maximalizované, když se otevře.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Obecně byste měli nastavit <xref:System.Windows.Window.WindowState%2A> nakonfigurovat počáteční stav okna. Jakmile se zobrazí okno s možností změny velikosti, uživatele stiskněte minimalizovat, maximalizovat a obnovit tlačítka na záhlaví okna. Chcete-li změnit stav okna.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Okno Vzhled  
 Změna vzhledu klientské oblasti okna tak, že přidáte specifické pro okno obsah, jako jsou tlačítka a popisky, textová pole. Ke konfiguraci neklientská oblast <xref:System.Windows.Window> poskytuje několik vlastností, které zahrnují <xref:System.Windows.Window.Icon%2A> nastavit ikonu okna a <xref:System.Windows.Window.Title%2A> nastavit její název.  
  
 Můžete také změnit vzhled a chování ohraničení neklientská oblast nakonfigurováním režim změny velikosti okna, styl okna, a určuje, zda je zobrazen jako tlačítko na panelu úkolů klasické pracovní plochy.  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Změna velikosti režimu  
 V závislosti na tom <xref:System.Windows.Window.WindowStyle%2A> vlastností, můžete řídit jak (a zda) uživatelé mohou změnit výšku okna. Volba Styl okna ovlivňuje, jestli uživatel může změnit velikost okna přetažením ohraničení pomocí myši, zda **minimalizovat**, **Maximalizovat**, a **změnit velikost** tlačítka zobrazí v neklientské oblasti, a pokud se zobrazí, zda jsou povoleny.  
  
 Můžete nakonfigurovat, jak změní velikost okna tak, že nastavíte její <xref:System.Windows.Window.ResizeMode%2A> vlastnost, která může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize> (výchozí)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Stejně jako u <xref:System.Windows.Window.WindowStyle%2A>, režim změny velikosti okna je pravděpodobně nebudou měnit během celé jeho životnosti, což znamená, že budete pravděpodobně ji nastavíte z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Všimněte si, že můžete zjistit, zda je okno maximalizované, rychle minimalizovat nebo obnovit, že se podíváte <xref:System.Windows.Window.WindowState%2A> vlastnost.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Styl okna  
 Ohraničení, která je vystavena v neklientské oblasti okna je vhodný pro většinu aplikací. Existují však okolností, kde jsou potřebné různé druhy ohraničení nebo bez ohraničení nejsou vůbec potřeba v závislosti na typu okna.  
  
 Řídit, jaký typ ohraničení okna získá, nastavíte její <xref:System.Windows.Window.WindowStyle%2A> vlastnosti s jednou z následujících hodnot <xref:System.Windows.WindowStyle> výčtu:  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow> (výchozí)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Vliv tyto styly oken jsou znázorněné na následujícím obrázku:  
  
 ![Obrázek styly ohraničení okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> buď pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek nebo kódu, protože nepravděpodobné, chcete-li změnit během životního cyklu okna, bude pravděpodobně nakonfigurujete pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Styl neobdélníkových oken  
 Také existují situace, kdy styly ohraničení, které <xref:System.Windows.Window.WindowStyle%2A> umožňuje mít nestačí. Můžete například vytvořit aplikaci s neobdélníkových ohraničení, jako je [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] používá.  
  
 Představte si třeba okně bublin řeči je znázorněno na následujícím obrázku:  
  
 ![Okno bublin řeči, s upozorněním přetáhněte Me.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Tento typ okna je vytvořit tak, že nastavíte <xref:System.Windows.Window.WindowStyle%2A> vlastnost <xref:System.Windows.WindowStyle.None>a pomocí speciální podporu, která <xref:System.Windows.Window> má transparentnosti.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Tato kombinace hodnot instruuje okno k vykreslení zcela transparentní. V tomto stavu nelze použít v okně neklientská oblast vylepšení (Zavřít nabídku, tlačítka Minimalizovat, maximalizovat a obnovit a tak dále). V důsledku toho budete muset zadat vlastní.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Přítomnost hlavního panelu  

Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, podobný jako na následujícím obrázku:

 ![Snímek obrazovky zobrazující okno s tlačítkem na hlavním panelu.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Některé typy windows nemají tlačítko na hlavním panelu, jako jsou okna se zprávou a dialogová okna (viz [přehled dialogových oken](dialog-boxes-overview.md)). Můžete řídit, zda je zobrazen tlačítko na hlavním panelu okna tak, že nastavíte <xref:System.Windows.Window.ShowInTaskbar%2A> vlastnosti (`true` ve výchozím nastavení).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 <xref:System.Windows.Window> vyžaduje `UnmanagedCode` oprávnění zabezpečení, které má být vytvořena. Pro aplikace nainstalované na a spustili z místního počítače to spadá do sady oprávnění, která jsou k aplikaci.  
  
 Ale to spadá mimo sadu oprávnění udělená aplikace, které jsou spouštěny z Internetu nebo místní intranet zóny pomocí [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]. V důsledku toho uživatelé dostanou [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] upozornění zabezpečení a se potřebují k rozvoji sady oprávnění pro aplikace pro úplný vztah důvěryhodnosti.  
  
 Kromě toho [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nelze zobrazit systému windows nebo dialogová okna ve výchozím nastavení. Informace o informace o zabezpečení pro samostatné aplikace, najdete v článku [strategie zabezpečení WPF – zabezpečení platformy](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Jiné typy Windows  
 <xref:System.Windows.Navigation.NavigationWindow> je okno, které slouží k hostování navigaci obsahu. Další informace najdete v tématu [Přehled navigace](navigation-overview.md)).  
  
 Dialogová okna jsou windows, které se často používají k získání informací od uživatele k dokončení funkce. Například, pokud uživatel požaduje pro otevření souboru, **otevřít soubor** aplikací a získání názvu souboru od uživatele je obvykle zobrazí dialogové okno. Další informace najdete v tématu [přehled dialogových oken](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Přehled dialogových oken](dialog-boxes-overview.md)
- [Sestavení aplikace WPF](building-a-wpf-application-wpf.md)
