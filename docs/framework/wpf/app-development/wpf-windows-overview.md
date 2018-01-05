---
title: "Přehled WPF Windows"
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
caps.latest.revision: "65"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f9822c61f454f0dd166cfdad7f26798790a5f23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-windows-overview"></a>Přehled WPF Windows
Uživatelé komunikovat s [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] samostatné aplikace prostřednictvím služby windows. Primárním účelem okno je jako hostitele obsahu, který vizualizuje data a umožňuje uživatelům interakci s daty. Samostatné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace zadat své vlastní windows pomocí <xref:System.Windows.Window> třídy. Toto téma představuje <xref:System.Windows.Window> před pokrývajících základní informace o vytváření a správa systému windows v samostatné aplikace.  
  
> [!NOTE]
>  Hostované prohlížečem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a ztratit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky, neposkytují vlastní windows. Místo toho jsou hostované v systému windows poskytuje [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]. V tématu [přehled aplikace prohlížeče WPF XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>Třídy oken  
 Následující obrázek ukazuje základní části okna.  
  
 ![Okno elementy](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")  
  
 Okno je rozdělené do dvou oblastech: neklientská oblast a klientské oblasti.  
  
 *Neklientská oblast* časového období je implementováno modulem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a zahrnuje části okna, které jsou společné pro většinu windows, včetně následujících:  
  
-   Ohraničení.  
  
-   Záhlaví.  
  
-   Ikona.  
  
-   Minimalizovat, maximalizovat a obnovte tlačítka.  
  
-   Tlačítko Zavřít.  
  
-   Nabídky systému s položky nabídky, které umožňují uživatelům minimalizovat, maximalizovat, obnovení, přesunout, přizpůsobit a zavřete okno.  
  
 *Klientské oblasti* časového období je oblast v rámci časového období neklientská oblast a používají vývojáři přidání obsahu specifické pro aplikace, jako je například nabídek, panely nástrojů a ovládací prvky.  
  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], okno se zapouzdřené pomocí <xref:System.Windows.Window> třídu, která používáte k postupujte takto:  
  
-   Zobrazí okno.  
  
-   Nakonfigurujte velikost, pozice a vzhled časového období.  
  
-   Hostování obsahu specifické pro aplikaci.  
  
-   Správa životního cyklu časového období.  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>Implementace okno  
 Vzhled a chování, se skládá z implementace typické okno kde *vzhled* definuje, jak vypadá okno uživatelům a *chování* definuje způsob, jakým okno funguje jak uživatelé pracují s ním. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete implementovat vzhled a chování okno pomocí buď kódu nebo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 Obecně platí, ale vzhled okno je implementovaná pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a její chování je implementovaná pomocí kódu, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Chcete-li povolit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor značek a kódu soubor používat společně, vyžadují se následující věci:  
  
-   V kódu `Window` musí obsahovat element `x:Class` atribut. Když je aplikace vytvářena, existenci `x:Class` ve značkách souboru způsobí, že [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Window> a má název, který je zadán `x:Class` atribut. To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaraci oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Generovaný objekt `partial` třída implementuje `InitializeComponent` metoda, která se nazývá registrace události a nastavte vlastnosti, které jsou implementované v kódu.  
  
-   V kódu, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` atribut ve značce a musí být odvozeny od <xref:System.Windows.Window>. To umožňuje souboru kódu, který má být spojen s `partial` třídu, která se vygeneruje pro soubor značek, když je aplikace vytvářena (najdete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
-   V modelu code-behind <xref:System.Windows.Window> třída musí implementovat konstruktor, který volá `InitializeComponent` metoda. `InitializeComponent`je implementována ve kód je generována souboru `partial` třída registrace události a nastavte vlastnosti, které jsou definovány v kódu.  
  
> [!NOTE]
>  Když přidáte novou <xref:System.Windows.Window> do projektu s použitím [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> je implementovaná pomocí značek a kódu a zahrnuje konfiguraci potřebné k vytvoření přidružení mezi soubory značek a kódu jako popsané v tomto poli.  
  
 V této konfiguraci na místě, můžete se zaměřit na definování vzhled okna v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a implementace své chování v kódu. Následující příklad ukazuje okno s tlačítkem na implementované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a obslužné rutiny události pro tlačítka <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události, které jsou implementované v kódu.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurace definici okna pro nástroje MSBuild  
 Jak implementovat okně aplikace určuje, jak je nakonfigurována pro [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]. Časový interval, který je definován pomocí obou pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu:  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]soubory značek jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky.  
  
-   Soubory kódu jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` položky.  
  
 To je znázorněno v následujícím [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] souboru projektu.  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Informace o vytváření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, najdete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>Doba života okna  
 Okno s jakákoli třída má životnost, který začíná, když je vytvořena první instance, po jejímž uplynutí ho je otevřít, aktivovat a deaktivovat a nakonec zavřít.  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>Otevřete okno  
 Chcete-li otevřít okno, nejdřív vytvořit instance, který je znázorněn v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, která nastane při <xref:System.Windows.Application.Startup> událost se vyvolá.  
  
 Při vytváření instance časového období, odkaz na jeho se automaticky přidá do seznamu systému windows, který spravuje <xref:System.Windows.Application> objektu (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>). Kromě toho první okno chcete vytvořit instanci se ve výchozím nastavení <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).  
  
 Nakonec otevření okna voláním <xref:System.Windows.Window.Show%2A> metoda; výsledek je znázorněno na následujícím obrázku.  
  
 ![Otevřít okno otevřené voláním metody window.show](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")  
  
 Okno, ve kterém je otevřen voláním <xref:System.Windows.Window.Show%2A> je nemodálním okně, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat jiné systém windows ve stejné aplikaci.  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A>je volána modálně otevřete windows, jako je například dialogová okna. V tématu [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md) Další informace.  
  
 Když <xref:System.Windows.Window.Show%2A> je volána, okno provede práci inicializace dříve, než je zobrazen k vytvoření infrastruktury, který umožní přijímat vstup uživatele. Při inicializaci okna <xref:System.Windows.Window.SourceInitialized> událost se vyvolá, a zobrazí se okno.  
  
 Jako zástupce <xref:System.Windows.Application.StartupUri%2A> může být nastaven na zadejte první okno, která se automaticky otevře při spuštění aplikace.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Při spuštění aplikace, okno zadaný hodnotou <xref:System.Windows.Application.StartupUri%2A> je otevřen modelessly; interně otevření okna voláním jeho <xref:System.Windows.Window.Show%2A> metoda.  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>Okno vlastnictví  
 Okno, ve kterém je otevřen pomocí <xref:System.Windows.Window.Show%2A> metoda nemá relaci implicitní s okna, která ho vytvořila; mohou uživatelé komunikovat s buď okno nezávisle na druhém, což znamená, že buď okno můžete provádět následující:  
  
-   Zahrnují dalších (Pokud některý ze systému windows má jeho <xref:System.Windows.Window.Topmost%2A> vlastnost nastavena na hodnotu `true`).  
  
-   Minimalizovat, maximalizovaném okně a obnovený bez ovlivnění dalších.  
  
 Některé windows vyžadují vztah s okně, které je otevře. Například [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] aplikace může zobrazit vlastnost windows a nástroj windows, jejichž typické chování je tak, aby pokrývalo okna, která je vytvořila. Kromě toho takové windows by měla vždycky zavřete, minimalizovat, maximalizovat a obnovení v souladu s okno, které byly vytvořeny. Takové relace by bylo možné navázat tím, že jeden interval *vlastní* jiný a je dosaženo nastavením <xref:System.Windows.Window.Owner%2A> vlastnost *ve vlastnictví okno* s odkazem na *vlastníka okno*. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Po navázání vlastnictví:  
  
-   Okno Vlastní odkazovat jeho vlastníka okno zkontrolováním hodnotu jeho <xref:System.Windows.Window.Owner%2A> vlastnost.  
  
-   Okno vlastníka můžete zjistit všechny systémy windows vlastní zkontrolováním hodnotu jeho <xref:System.Windows.Window.OwnedWindows%2A> vlastnost.  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>Brání aktivaci okna  
 Existují scénáře, kde by neměl být windows aktivovat, pokud ukazuje, jako je například konverzace windows messenger-style aplikace Internet nebo windows oznámení e-mailové aplikace.  
  
 Pokud aplikace obsahuje okno, které by neměly být aktivní, pokud vidět, můžete nastavit jeho <xref:System.Windows.Window.ShowActivated%2A> vlastnost `false` před voláním <xref:System.Windows.Window.Show%2A> metoda poprvé. V důsledku:  
  
-   Okno není aktivována.  
  
-   Okně <xref:System.Windows.Window.Activated> událost není aktivována.  
  
-   Okno aktuálně aktivovaný zůstane aktivovaný.  
  
 Okno se aktivuje, ale jakmile uživatel aktivuje kliknutím na klienta nebo neklientská oblast. V tomto případě:  
  
-   Okno se aktivuje.  
  
-   Okně <xref:System.Windows.Window.Activated> událost se vyvolá.  
  
-   Okno dříve aktivovaná je deaktivována.  
  
-   Okně <xref:System.Windows.Window.Deactivated> a <xref:System.Windows.Window.Activated> události jsou vyvolány následně podle očekávání v odpovědi na akce uživatele.  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>Okno Aktivace  
 Při prvním otevření okna bude aktivní okno (Pokud se zobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavena na `false`). *Aktivní okno* je okno, které je aktuálně zachytávání vstupu uživatele, jako je například stisknutí kláves a kliknutí myší. Okno stane aktivní, vyvolá <xref:System.Windows.Window.Activated> událostí.  
  
> [!NOTE]
>  Při prvním otevření okna <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.Window.ContentRendered> události jsou vyvolány až poté, co <xref:System.Windows.Window.Activated> událost se vyvolá. Myslete na to, okno lze účinně považovat za otevřít, když <xref:System.Windows.Window.ContentRendered> je vyvolána.  
  
 Po okno stane aktivní, uživatel může aktivovat další okno ve stejné aplikaci, nebo jiná aplikace. Pokud k tomu dojde, aktuálně aktivní okno bude deaktivováno a vyvolá <xref:System.Windows.Window.Deactivated> událostí. Podobně platí, když uživatel vybere okno aktuálně deaktivované, okno zase aktivní a <xref:System.Windows.Window.Activated> je vyvolána.  
  
 Jeden běžným důvodem pro zpracování <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> se povolení a zakázání funkce, které lze spustit pouze když je aktivní okno. Například některé windows zobrazit interaktivní obsah, který vyžaduje konstantní uživatelský vstup nebo pozornost, včetně hry a přehrávačů videa. Následující příklad je zjednodušený přehrávání videa, které ukazuje, jak bude zpracováván <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> implementovat toto chování.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Jiné typy aplikací mohou stále spustit kód na pozadí při deaktivaci časového období. E-mailového klienta může například pokračovat v dotazování poštovní server, když uživatel používá jiné aplikace. Aplikace, jako je to často poskytují různé nebo další chování, zatímco je deaktivována hlavní okno. S ohledem na e-mailu program to znamená přidání nové položky e-mailu do složky Doručená pošta i přidání ikony v oznamovací do na hlavním panelu. Ikony v oznamovací potřebovat zobrazí jenom v případě okna e-mailu není aktivní, což může být určen na základě <xref:System.Windows.Window.IsActive%2A> vlastnost.  
  
 Dokončení úlohy na pozadí, okno chtít upozornit uživatele, více naléhavě voláním <xref:System.Windows.Window.Activate%2A> metoda. Pokud uživatel komunikuje s aktivaci jiné aplikace při <xref:System.Windows.Window.Activate%2A> nazývá bliká tlačítko okno na hlavním panelu. Pokud uživatel komunikuje s aktuální aplikace, volání <xref:System.Windows.Window.Activate%2A> se otevře okno na popředí.  
  
> [!NOTE]
>  Dokáže zpracovat aktivace oboru aplikace pomocí <xref:System.Windows.Application.Activated?displayProperty=nameWithType> a <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> události.  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>Zavřením okna  
 Dobu životnosti okno spustí, přejdete-li na element end při zavření ho. Okno můžete ukončit pomocí prvků v neklientská oblast, včetně následujících:  
  
-   **Zavřít** položku **systému** nabídky.  
  
-   Stisknutím ALT + F4.  
  
-   Kliknutím **Zavřít** tlačítko.  
  
 Můžete zadat další mechanismy pro klientské oblasti zavřete okno, další běžné, které zahrnují následující:  
  
-   **Ukončení** položky v **souboru** nabídky, obvykle hlavní aplikaci pro windows.  
  
-   A **Zavřít** položky v **souboru** nabídky, obvykle na okno sekundární aplikace.  
  
-   A **zrušit** tlačítko, obvykle na modální dialogové okno.  
  
-   A **Zavřít** tlačítko, obvykle v nemodálním dialogovém okně.  
  
 Zavřete okno v reakci na jednu z těchto mechanismů vlastní, je třeba volat <xref:System.Windows.Window.Close%2A> metoda. Následující příklad implementuje zavřete okno a vybrat možnost **ukončení** na **souboru** nabídky.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Zavře okno, vyvolá dvě události: <xref:System.Windows.Window.Closing> a <xref:System.Windows.Window.Closed>.  
  
 <xref:System.Windows.Window.Closing>je vyvolána před okno se zavře a poskytuje mechanismus, pomocí které okna je možné zabránit uzavření. Jeden běžným důvodem, aby se zabránilo okno uzavření je, pokud obsah okno obsahuje upravených dat. V takovém případě <xref:System.Windows.Window.Closing> události může být zpracována pro určení, zda je nekonzistentní data a pokud ano, chcete-li požádat uživatele, jestli se mají buď pokračovat zavřít okno bez uložení dat nebo zrušit okno uzavření. Následující příklad ukazuje klíčových aspektů zpracování <xref:System.Windows.Window.Closing>.  
  
 [!code-csharp[WindowClosingSnippets](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <xref:System.Windows.Window.Closing> Obslužné rutiny události je předána <xref:System.ComponentModel.CancelEventArgs>, který implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost, která můžete nastavit na hodnotu `true` zabránit zavření okna.  
  
 Pokud <xref:System.Windows.Window.Closing> nejsou zpracovávány, nebo je zpracovává, ale nebyl zrušen, okno se zavře. Těsně před okno ve skutečnosti zavře, <xref:System.Windows.Window.Closed> je vyvolána. V tomto okamžiku nelze okno zabránila uzavírací.  
  
> [!NOTE]
>  Aplikace může být nakonfigurována pro vypnutí automaticky, při zavření okna hlavní aplikace (viz <xref:System.Windows.Application.MainWindow%2A>) nebo poslední okno se zavře. Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Během časového období je možné explicitně uzavřít prostřednictvím mechanismy, které poskytuje v oblastech jiného počítače než klientského a klienta, okno lze také implicitně uzavřít v důsledku chování v dalších částí aplikace nebo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], včetně následujících:  
  
-   Uživatel odhlásí nebo ukončí [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)].  
  
-   Zavře vlastníka časového období (viz <xref:System.Windows.Window.Owner%2A>).  
  
-   Zavření okna hlavní aplikaci a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
-   <xref:System.Windows.Application.Shutdown%2A>je volána.  
  
> [!NOTE]
>  Nelze znovu otevřít okno, jakmile je uzavřený.  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>Interval životního cyklu události  
 Následující obrázek zobrazuje posloupnost hlavní událostí v průběhu životnosti časového období.  
  
 ![Doba života okna](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")  
  
 Následující obrázek zobrazuje posloupnost hlavní událostí ve životnost okno, které se zobrazí bez aktivace (<xref:System.Windows.Window.ShowActivated%2A> je nastaven na `false` předtím, než se zobrazí okno).  
  
 ![Doba života okna &#40; Window.ShowActivated & č. 61; False &#41; ] (../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>Umístění okna  
 Při otevřené okno obsahuje umístění, do x a y dimenze relativně k ploše. Toto umístění může být určen na základě <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> vlastnosti, v uvedeném pořadí. Můžete nastavit tyto vlastnosti chcete změnit umístění okna.  
  
 Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení nastavením <xref:System.Windows.Window.WindowStartupLocation%2A> vlastnost s jedním z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner>(výchozí)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Pokud při spuštění je zadán jako <xref:System.Windows.WindowStartupLocation.Manual>a <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> nebyly nastaveny vlastnosti, <xref:System.Windows.Window> požádá [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] pro umístění, do kterého se zobrazí v.  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>Nejhornější Windows a pořadí Z-Order  
 Kromě toho také s x a y umístění, okno má umístění v z dimenzi, která určuje svislé polohy s ohledem na ostatní windows. To se označuje jako okna pořadí z-order a existují dva typy: Normální pořadí vykreslování a nejhornější pořadí vykreslování. Umístění okna v *normální pořadí vykreslování* je dáno bez ohledu na jeho, jestli je aktuálně aktivní. Ve výchozím nastavení okno se nachází v normálním pořadí z-order. Umístění okna v *nejhornější pořadí vykreslování* je také určeno bez ohledu na jeho, jestli je aktuálně aktivní. Kromě toho windows v nejhornější pořadí z-order nacházejí vždy výše windows v normálním pořadí z-order. Okno se nachází v nejhornější pořadí z-order nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnost `true`.  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup2)]  
  
 V rámci každé pořadí vykreslování aktuálně aktivní okno se zobrazí nad všemi jiných windows ve stejném pořadí.  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>Velikost okna  
 Kromě nutnosti plochy umístění, okno má velikost, které je určeno několik vlastností, včetně různé vlastnosti šířky a výšky a <xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.MaxWidth%2A> se používají ke správě celou škálu šířek, které může mít během celé jeho životnosti okno a jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup2)]  
  
 Spravuje výšku okna <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.MaxHeight%2A>a jsou nakonfigurovány, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup2)]  
  
 Protože různých hodnot šířka a výška hodnoty zadejte rozsah, je možné pro šířku a výšku s možností změny velikosti okna musí být kdekoli v zadaný rozsah pro příslušné dimenze. Ke zjištění jeho aktuální šířka a výška, zkontrolujte <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A>, v uvedeném pořadí.  
  
 Pokud chcete šířku a výšku okna tak, aby měl velikost, která odpovídá velikosti okna je obsahu, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnosti, která má následující hodnoty:  
  
-   <xref:System.Windows.SizeToContent.Manual>. Žádný vliv (výchozí).  
  
-   <xref:System.Windows.SizeToContent.Width>. Na celou šířku obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.  
  
-   <xref:System.Windows.SizeToContent.Height>. Přizpůsobit na výšku obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu.  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. Přizpůsobit na obsahu šířka a výška, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu i nastavení <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.  
  
 Následující příklad ukazuje okno která automaticky velikosti podle jeho obsahu svisle i vodorovně, pokud zobrazen jako první.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup2)]  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Window.SizeToContent%2A> vlastností v kódu k určení, jak se okno změní podle jeho obsahu.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>Pořadí priorit o velikosti vlastnosti  
 V podstatě různé vlastnosti velikosti okna se kombinují a definují rozsah šířky a výšky pro okno umožňující změnu velikosti. K zajištění platný rozsah se zachová, <xref:System.Windows.Window> vyhodnotí hodnoty vlastností velikost pomocí následující objednávky priorit.  
  
 **Výška vlastnosti:**  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Šířka vlastnosti:**  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Pořadí priorit můžete také určit velikost okna, když ho je maximalizované, který je spravován pomocí <xref:System.Windows.Window.WindowState%2A> vlastnost.  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>Stav okna  
 Po dobu životnosti okno s možností změny velikosti, může mít tři stavy: Normální, minimalizovat a v maximalizovaném okně. Okno s *normální* stav je výchozí stav časového období. Okno s Tento stav umožňuje uživateli přesunout a jeho velikost na základě velikosti úchytu nebo ohraničení, pokud je s možností změny velikosti.  
  
 Okno s *minimalizovaná* stavu Hroutí k jeho tlačítko panelu úloh, pokud <xref:System.Windows.Window.ShowInTaskbar%2A> je nastaven na `true`, jinak se sbalí nejmenší možná velikost může být a přemístí samotné okraje v levém dolním rohu plochy. Ani typu minimalizovaném okně velikost lze změnit pomocí ohraničení nebo změnit velikost úchytu, i když minimalizovaném okně, které se zobrazí na hlavním panelu můžete přetáhnout kolem plochy.  
  
 Okno s *maximalizovaný* stavu zasahuje do maximální velikost může být, která bude pouze tak velké, jaká jeho <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.Window.SizeToContent%2A> tu určují vlastnosti. Maximalizovaném okně jako minimalizovaném okně, nebude možné změnit pomocí změny velikosti úchytu nebo přetažením ohraničení.  
  
> [!NOTE]
>  Hodnoty <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti časového období vždy představují hodnoty pro stav Normální, i když aktuálně maximalizovaný nebo minimalizovaná okna.  
  
 Stav okno se dá nakonfigurovat nastavení jeho <xref:System.Windows.Window.WindowState%2A> vlastnosti, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:  
  
-   <xref:System.Windows.WindowState.Normal>(výchozí)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 Následující příklad ukazuje, jak vytvořit okno, které se zobrazí jako maximalizovaný po jejím otevření.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup2)]  
  
 Obecně byste měli nastavit <xref:System.Windows.Window.WindowState%2A> můžete nakonfigurovat počáteční stav časového období. Jakmile se zobrazí okno s možností změny velikosti, uživatelé stiskněte minimalizovat, maximalizovat a obnovit tlačítka v záhlaví okna na změnu stavu okna.  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>Okno vzhledu  
 Změna vzhledu klientské oblasti okno přidáním okno obsahu, jako je například textová pole, tlačítka a popisky. Ke konfiguraci neklientská oblast <xref:System.Windows.Window> nabízí několik vlastností, které zahrnují <xref:System.Windows.Window.Icon%2A> nastavit ikonu časového období a <xref:System.Windows.Window.Title%2A> nastavit její název.  
  
 Také můžete změnit vzhled a chování ohraničení neklientská oblast konfigurace režim změny velikosti časového období, styl oken, a určuje, zda se zobrazí jako tlačítka na panelu úloh klientů.  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>Změnit velikost režimu  
 V závislosti na <xref:System.Windows.Window.WindowStyle%2A> vlastnost, můžete řídit způsob (a pokud) uživatelé mohou změnit velikost okna. Volba Styl okna ovlivňuje, jestli uživatel může změnit velikost okna tak, že přetáhnete jeho ohraničení pomocí myši, jestli **minimalizaci**, **Maximalizovat**, a **změnit velikost** tlačítka zobrazí na neklientská oblast, a pokud se zdá, jestli jsou povolené.  
  
 Můžete nakonfigurovat, jak se okno změní nastavením jeho <xref:System.Windows.Window.ResizeMode%2A> vlastnosti, která může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize>(výchozí)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Stejně jako u <xref:System.Windows.Window.WindowStyle%2A>, režim změny velikosti okna nepravděpodobné, chcete-li změnit během celé jeho životnosti, což znamená, že budete pravděpodobně nastavíte z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup2)]  
  
 Všimněte si, že můžete zjistit, jestli je okno maximalizované, rychle minimalizovat nebo obnovit zkontrolováním <xref:System.Windows.Window.WindowState%2A> vlastnost.  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>Styl okna  
 Ohraničení, který je zveřejněný z jiného počítače než klientského oblasti časového období je vhodná pro většinu aplikací. Existují však okolnosti, kdy je potřeba různé typy ohraničení nebo žádné ohraničení, je potřeba vůbec, v závislosti na typu časového období.  
  
 K řízení, jaké typy ohraničení okno získá, nastavíte jeho <xref:System.Windows.Window.WindowStyle%2A> vlastnost s jedním z následujících hodnot <xref:System.Windows.WindowStyle> výčtu:  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow>(výchozí)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Účinek tyto styly oken jsou zobrazené na následujícím obrázku.  
  
 ![Styly oken](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")  
  
 Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> buď pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód; protože nepravděpodobné, chcete-li změnit během časového období platnosti, budou s největší pravděpodobností nakonfigurujete pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup2)]  
  
#### <a name="non-rectangular-window-style"></a>Styl obdélníkový oken  
 Existují také situace, kdy které styly ohraničení <xref:System.Windows.Window.WindowStyle%2A> umožňuje vám tak, aby měl nestačí. Například můžete chtít vytvořit aplikaci s obdélníkový ohraničení, jako je [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] používá.  
  
 Představte si třeba okna bublin řeči vidět na následujícím obrázku.  
  
 ![Nepravoúhlý okno](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")  
  
 Tento typ okna lze vytvořit pomocí nastavení <xref:System.Windows.Window.WindowStyle%2A> vlastnost <xref:System.Windows.WindowStyle.None>a pomocí speciální podpory, který <xref:System.Windows.Window> má transparentnosti.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup2)]  
  
 Tato kombinace hodnot dá pokyn okno k vykreslení zcela transparentní. V tomto stavu nelze použít okně neklientská oblast vylepšení (Zavřít nabídky, tlačítka Minimalizovat, maximalizovat a obnovení a tak dále). V důsledku toho je třeba zadat vlastní.  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>Přítomnosti na hlavním panelu  
 Výchozí vzhled okno obsahuje tlačítko panelu úloh, stejný, jako je znázorněno na následujícím obrázku.  
  
 ![Okno s tlačítkem na hlavním panelu](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")  
  
 Některé typy windows nemáte tlačítko panelu úloh, jako je například okna zpráv a dialogových oken (viz [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)). Můžete řídit, jestli se zobrazí tlačítko panelu úloh v časovém období nastavením <xref:System.Windows.Window.ShowInTaskbar%2A> vlastnost (`true` ve výchozím nastavení).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup2)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 <xref:System.Windows.Window>vyžaduje `UnmanagedCode` oprávnění zabezpečení k vytvořit instanci. Pro aplikace v nainstalován a spuštěn z místního počítače to spadá do sadu oprávnění, kterým je uděleno oprávnění k aplikaci.  
  
 To však spadá mimo sadu oprávnění udělená aplikace, které jsou spouštěny z Internetu nebo místní intranetové zóny pomocí [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]. V důsledku toho se uživatelé dostanou [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] upozornění zabezpečení a bude nutné zvýšení oprávnění, nastavení pro aplikaci na úplný vztah důvěryhodnosti.  
  
 Kromě toho [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nelze zobrazit systému windows nebo dialogová okna ve výchozím nastavení. Podrobné informace o aspekty zabezpečení samostatné aplikace, najdete v části [strategie zabezpečení WPF - platformy zabezpečení](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>Jiné typy systému Windows  
 <xref:System.Windows.Navigation.NavigationWindow>je okno, které slouží jako hostitele obsahu navigaci. Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md)).  
  
 Dialogová okna jsou windows, které se často používá ke shromažďování informací od uživatele k dokončení funkce. Například pokud uživatel chce k otevření souboru, **otevřít soubor** obvykle zobrazí dialogové okno pomocí aplikace pro získání názvu souboru od uživatele. Další informace najdete v tématu [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Window>  
 <xref:System.Windows.MessageBox>  
 <xref:System.Windows.Navigation.NavigationWindow>  
 <xref:System.Windows.Application>  
 [Přehled dialogových oken](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)  
 [Sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
